---
title: "where can I get a script for my blog, that wil advertise Firefox"
date: 2008-05-03
forum: The Cafe
---

### Post by barbedsaber on 2008-05-03
Where can I get something to add to my blog, that will check what browser the viewer is using, and if it is Internet explorer (or any non Firefox browser, /nod in direction of opera fan's), suggest that they get Firefox, and if they have firefox, inform them of there awesomeness. I have seen these before, but I don't know where to find them.

---

### Post by LaRoza on 2008-05-03
> **barbedsaber said:**
> Where can I get something to add to my blog, that will check what browser the viewer is using, and if it is Internet explorer (or any non Firefox browser, /nod in direction of opera fan's), suggest that they get Firefox, and if they have firefox, inform them of there awesomeness. I have seen these before, but I don't know where to find them.

Add this to the page:

```

<a href="http://www.opera.com" title="Best browser">Download the best browser in the world! Fast, stable, secure, and standard compliant. Available for more platforms than other browsers.</a>

```

Find the name of the browser is easy. Do you have any coding ability?

---

### Post by mr.propre on 2008-05-03
I guess the best way tot do is, is by using javascript (but you can use PHP or other sever side script as well).

On w3school you can find a small tutorial. offcource you will need tot edit a little, but its real basic.

```
<html>
<head>
<script type="text/javascript">
function detectBrowser()
{
var browser=navigator.appName;
var b_version=navigator.appVersion;
var version=parseFloat(b_version);
if ((browser=="Netscape"||browser=="Microsoft Internet Explorer")
&& (version>=4))
{
alert("Your browser is good enough!");
}
else
{
alert("It's time to upgrade your browser!");
}
}
</script>
</head>
<body onload="detectBrowser()">
</body>
</html>
```

[http://www.w3schools.com/js/js_browser.asp](http://www.w3schools.com/js/js_browser.asp)

---

### Post by barbedsaber on 2008-05-03
thanks guys, umm no coding experiance.

shouldn't there be one that I can copy and paste into the html, for n00bs like me?

---

### Post by scouser73 on 2008-05-03
Try here for Firefox promotional buttons.

[http://www.mozilla.org/products/firefox/buttons.html]("http://www.mozilla.org/products/firefox/buttons.html")

---

