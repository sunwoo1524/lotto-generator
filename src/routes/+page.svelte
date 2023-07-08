<script>
    let picked_nums = [];
    let random_phrases = [
        "오늘은 웬지 운이 좋다.",
        "인생은 한방",
        "1등 기원!",
        "부자 되세요!",
        "오늘은 로또 사는 날",
        "개꿈도 다시 보자",
    ];

    function generateLotto() {
        let nums = [...Array(46).keys()]
        nums.splice(0, 1);
        
        let temp = [];

        for (let _ = 0; _ < 6; _++) {
            let i = parseInt(Math.random() * nums.length);
            temp.push(nums[i]);
            nums.splice(i, 1);
        }

        temp.sort(function(a, b){return a - b});

        picked_nums = [...temp];
    }

    function getBallColor(num) {
        if (num <= 10) {
            return "#FBC400";
        } else if (num <= 20) {
            return "#3975e5";
        } else if (num <= 30) {
            return "#e53939";
        } else if (num <= 40) {
            return "#3d3d3d";
        } else if (num <= 45) {
            return "#00ba0f";
        }
    }
</script>

<div class="container">
    <button on:click={generateLotto} class="generate-btn">뽑기</button>

    <div class="balls">
        {#each picked_nums as picked_num}
            <div class="ball" style="background-color: {getBallColor(picked_num)};">{picked_num}</div>
        {/each}
    </div>

    <p>{random_phrases[parseInt(Math.random() * random_phrases.length)]}</p>
</div>

<style>
    @font-face {
        font-family: 'SUITE-Regular';
        src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_2304-2@1.0/SUITE-Regular.woff2') format('woff2');
        font-weight: 400;
        font-style: normal;
    }

    :global(body) {
        margin: 0;
        font-family: "SUITE-Regular";
    }

    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding-top: 100px;
    }

    .generate-btn {
        border: 0;
        padding: 8px;
        font-size: 18px;
        border-radius: 5px;
        color: white;
        background-color: #2f4ed8;
        margin-bottom: 40px;
    }

    .balls {
        display: flex;
        margin-bottom: 50px;
    }

    .balls .ball {
        width: 50px;
        height: 50px;
        margin: 0 5px;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        color: white;
        font-size: 20px;
    }
</style>