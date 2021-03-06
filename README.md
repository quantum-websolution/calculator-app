# calculator-app
# 電卓を作ってみよう。

・目的
　プログラミングを触ってみたい人、始めたばかりの人
・ゴール
　足し算、引き算、掛け算、割り算、クリア、バックができる電卓

# HTMlで土台作り
```ruby:HTML
<html>
<head>
</head>
<body>
    <div class="main">
        <form name="form">
            <input class="textview" name="textview">
        </form>
        <div>
            <div>
                <button class="button" type="button" value="C" onclick="clear()">C</button>
                <button class="button" type="button" value="<" onclick="back()"><</button> 
                <button class="button" type="button" value="/" onclick="insert('/')">/</button>
                <button class="button" type="button" value="X" onclick="insert('*')">*</button>
            </div>
            <div>
                <button class="button" type="button" value="7" onclick="insert(7)">7</button>
                <button class="button" type="button" value="8" onclick="insert(8)">8</button>
                <button class="button" type="button" value="9" onclick="insert(9)">9</button>
                <button class="button" type="button" value="-" onclick="insert('-')">-</button>
            </div>
            <div>
                <button class="button" type="button" value="4" onclick="insert(4)">4</button>
                <button class="button" type="button" value="5" onclick="insert(5)">5</button>
                <button class="button" type="button" value="6" onclick="insert(6)">6</button>
                <button class="button" type="button" value="+" onclick="insert('+')">+</button>
            </div>
            <div>
                <button class="button" type="button" value="1" onclick="insert(1)">1</button>
                <button class="button" type="button" value="2" onclick="insert(2)">2</button>
                <button class="button" type="button" value="3" onclick="insert(3)">3</button>
                <button class="button equal" type="button" value="=" onclick="equal()">=</button>
            </div>
            <div>
                <button class="button" style="width: 108;" type="button" value="0" onclick="insert(0)">0</button>
                <button class="button" type="button" value="." onclick="insert('.')">.</button>
            </div>
        </div>
    </div>
</body>
</html>
```

# 書いたHTMLにCSSをあてる

```
<head>
    <style>
        button {
            width: 50px;
            height: 50px;
        }

        * {
            margin: 0;
            padding: 0;
        }

        .button {
            width: 50px;
            height: 50px;
            font-size: 25px;
            margin: 2px;
            cursor: pointer;
            background: #303AF2;
            border: 1px solid #303AF2;
            border-radius: 5px;
            color: #fffff0;
        }

        .textview {
            width: 224;
            margin: 2;
            font-size: 25;
            padding: 5;
            background: #303AF2;
            border: 1px solid #303AF2;
            border-radius: 5px;
            color: #fffff0;
        }

        .equal {
            height: 105px;
            position: absolute;
            margin-left: 6px;
        }
    </style>

</head>
```
電卓の形は完成。

# jsで処理を書いていく

```
<head>
    <script>
        function insert(num) {
            document.form.textview.value = document.form.textview.value + num;
        }
    </script>
    <style>
      中略
    </style>
</head>
```
ボタンから文字を読み取る処理

```
<head>
    <script>
        function insert(num) {
            document.form.textview.value = document.form.textview.value + num;
        }
        function equal() {
            var exp = document.form.textview.value;

            if (exp) {
                document.form.textview.value = eval(exp);
            }
        }
    </script>
    <style>
      中略
    </style>
</head>
```

equalが押された時に足算してくれる処理。
くわしくは[eval（）について](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/eval)

```
<head>
    <script>
        function insert(num) {
            document.form.textview.value = document.form.textview.value + num;
        }
        function equal() {
            var exp = document.form.textview.value;

            if (exp) {
                document.form.textview.value = eval(exp);
            }
        }
        function clear{
            document.form.textview.value = "";
        }
        function back() {
            var exp = document.form.textview.value;
            document.form.textview.value = exp.substring(0, exp.length - 1);
        }
    </script>
    <style>
      中略
    </style>
</head>
```
入力したデータを消す処理と一文字戻す処理。


これで完成です！
