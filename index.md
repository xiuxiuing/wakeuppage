<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
</head>
<body>
<a href="wakeup://xx" style="font-size:37px">直接使用自定义协议打开(微信微博里面没反应)</a>
<br/>
<br/>
<br/>
<a href="http://yeq.moonforest.org:61593/wakeup?r=http%3A%2F%2F163.com" style="font-size:37px">使用http请求打开</a>
<div id="div1" style="font-size:27px"></div>
</body>
</html>
<script>
    function request() {//TODO 后台循环请求
        var ports = new Array(61593, 41123, 43387, 39083, 24423, 16834, 9289, 8452, 6217, 5300, 4118, 3787, 2998);
        var url = "http://yeq.moonforest.org";
        var path = "/wakeup";
        var ajax = new XMLHttpRequest();
        for (var i = 0; i < ports.length; i++) {
            var realUrl = url + ":" + ports[i] + path;
            ajax.open("GET", realUrl, true);
            ajax.onreadystatechange = function() {
                if (ajax.readyState == 4 && ajax.status == 200) {
                    var content = ajax.responseText;
                    document.getElementById("div1").innerHTML = content;
                    return;
                }
            }
        }
    }
</script>
