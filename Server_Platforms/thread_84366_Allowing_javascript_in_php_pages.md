---
title: "Allowing javascript in php pages?"
date: 2005-10-30
forum: Server Platforms
---

### Post by hcker2000 on 2005-10-30
I have a script in my php page and need to figure out how to get apache2 to allow it. This is the last thing I realy need to get working before the new server is done.

---

### Post by dbee on 2005-10-31
How exactly is apache 'not allowing' it ??

What's wrong ?

Apache doesn't really care whether you have javascript in your php sheets or not...

---

### Post by hcker2000 on 2005-11-06
Well this is the script that I'm having issues with.

[HTML]<script language="Javascript">
		var tickerwidth=600;
		var tickercolor="#000000";
		var fontcolor="#00FF00";
		var splitcolor="#0000FF";
		var fontsize=11;
		var visitedlink="#FF0000";
		var rollovercolor="#0000FF";
		var font="Arial";
		var speed=3;
		var sparte=4;
		var rubrik=13;
		var ticker_stop=0;
		var rollover_underline=1;
		var font_underline=0;
		var transparent=0;
		var fontbold="0";
		var tickertyp=1;
		var u_id=9314;
	</script>
	<script language="JavaScript" src="http://newsticker.shortnews.com/com/js/free/3/a.js"></script>
	<script language="JavaScript" src="http://newsticker.shortnews.com/com/js/free/3/b.js"></script>
	<ilayer  width=&{marqueewidth}; height=&{marqueeheight}; name="cmarquee01"> 
		<layer name="cmarquee02"></layer>
	</ilayer>[/HTML]

It works fine on my old mandrake server box but for some reason it isn't working when I load the same page (and code) from my new web server. Any idea's what I need to check into to get this working?

---

### Post by mpettitt on 2005-11-06
Well, it isn't going to be anything to do with just that script. Javascript is only executed on the client side, so if the server is dumping the file out, it'll work assuming the client supports it.
It could be something as simple as the PHP version changing from PHP4 to PHP5, and you having a discontinued bit of syntax in the PHP part of the page. Whatever it is, it isn't being affected by the JS.

---

### Post by hcker2000 on 2005-11-06
Well here is the whoal page so maby some one will see some thing that isn't right for php5.

[HTML]<html>
<head>
	<title>News</title>
	<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
	<link href="css/HNet.css" rel="stylesheet" type="text/css">
</head>

<body>
<div align="center">
	<script language="Javascript">
		var tickerwidth=600;
		var tickercolor="#000000";
		var fontcolor="#00FF00";
		var splitcolor="#0000FF";
		var fontsize=11;
		var visitedlink="#FF0000";
		var rollovercolor="#0000FF";
		var font="Arial";
		var speed=3;
		var sparte=4;
		var rubrik=13;
		var ticker_stop=0;
		var rollover_underline=1;
		var font_underline=0;
		var transparent=0;
		var fontbold="0";
		var tickertyp=1;
		var u_id=9314;
	</script>
	<script language="JavaScript" src="http://newsticker.shortnews.com/com/js/free/3/a.js"></script>
	<script language="JavaScript" src="http://newsticker.shortnews.com/com/js/free/3/b.js"></script>
	<ilayer  width=&{marqueewidth}; height=&{marqueeheight}; name="cmarquee01"> 
		<layer name="cmarquee02"></layer>
	</ilayer>
</div>
<hr>
<table>
	<tr>
		<td width="28%"><div align="center"><a href="News/Index.htm"><img src="Images/Interface/OldNews.gif" width="150" height="50" border="0"></a></div></td>
		<td width="28%"><div align="center"><? include("php/quote/randomquote.php"); ?></div></td>
		<td width="32%"><div align="center"><p><img src="Images/Misc/poweredby.gif" width="88" height="31"></p><p><? include("php/uptime.php"); ?></p></div></td>
	</tr>
</table>
<hr>
<p><b>News:</b></p>
<p>11/6/05</p>
<p>I will be moving shortly so news updates will probably be a little slow for a while. I will also try and let every one know
  before I take the web server down for the move. Maby I will even have the new web server up and runing by the time I get moved.</p>
</body>
</html>[/HTML]

I will also see if I can find php checker online real quick to check it.

---

### Post by JogerNaut on 2005-11-06
That whole page doesn't have any php code in it. Also, as mpettitt said before, javascript is client-sdie scripting meaning the browser is the one that runs it rather than the server.

BTW, what exactly happens when try to go to that page? Does the browser show it fine and just doesn't run the javascript part  or does it show the whole code (not show it as html)?

---

### Post by hcker2000 on 2005-11-06
When you go to that page it loads every thing but the java short news part. I could in all honesty do with out it but I would like to figure out what is up just in case I would run into the problem latter.

---

### Post by mpettitt on 2005-11-06
Change the <? to <?php for starters. The Short tags are disabled by default and have been for a while.
You might also want to scrap the <ilayer> since that isn't valid HTML

---

### Post by hcker2000 on 2005-11-06
Alright the old web server is mandrak 9.0 i think so its good and old. Also will it work with out the ilayer? 

EDIT: Is this the right syntax <?php include("php/quote/randomquote.php"); ?>

---

### Post by mpettitt on 2005-11-06
Syntax is right. Not got the faintest idea about the ilayer removal - haven't seen any ilayers for _years_! Could try replacing it with a <div> I suppose. Don't know what you are trying to do with it though, so can't be sure.

---

### Post by chris_pmf on 2005-11-06
additional you should replace
```
 language="Javascript"
```
with
```
 type="text/javascript"
```

---

### Post by JogerNaut on 2005-11-06
Ok, I tried your html on my machine and originally the script didn't work. This came as a surprise since viewing it directly (not served by the webserver) it works. I checked the java script console and it seems there were errors due to the fact that the news ticker script was encoded as iso-8859-1 and the page was being served as utf-8. This breaks the breaks the script which is why it doesn't appear. Changing my browser to use that character encoding makes the script work.

Add this 
[PHP]<?php 
header("Content-type: text/html; charset=ISO-8859-1");
?>[/PHP]
to the very beginning of the script to set the page's header to iso-8859-1.

---

### Post by hcker2000 on 2005-11-06
Tryed that I get the falowing error 

Warning: Cannot modify header information - headers already sent by (output started at /var/www/html/News.php:4) in /var/www/html/News.php on line 5

I tryed removing my <head> section and still give that error.

---

### Post by chris_pmf on 2005-11-06
Just read what JogerNaut wrote:
[QUOTE=JogerNaut]...to the **very beginning of the script** to set the page's header to iso-8859-1.[/QUOTE]

---

### Post by JogerNaut on 2005-11-06
You can't change the header if you've sent out any data. You should add it at the very top of the page.

Ex.```
<?php 
header("Content-type: text/html; charset=ISO-8859-1");
?><html>
...
...
</html>

```

You can also change the default charset by adding this line:```
AddDefaultCharset ISO-8859-1
```
 in your .htaccess file

---

### Post by hcker2000 on 2005-11-06
Thanks very much this has solved my issue. The new server is a go for launch!

---

