---
title: "WWW help"
date: 2008-07-16
forum: Server Platforms
---

### Post by ramsam on 2008-07-16
Hello guys I am new to this fourm and of course uBuntu

I installed ubuntu and have been playing around with it for couple of days..... I installed apache web server

I get the webpage and all but the .zip file that I have put up using a <a href> link will not download.

It downloads but its not the complete file ?

I am sure that I am missing some settings ?

can any one help !!!

this is how my INDEX.HTML file looks
************************************************** *
<html><body><h1>It works!</h1></body></html>


<a href="/var/www/maine.zip"<font size=15> <B> MAINE pictures </B></font></a>

************************************************** *

Any clu or help is appreciated
Thank you guys !!!

-ramsam

---

### Post by indytim on 2008-07-16
Just a wang... but might want to try:
> 
<a href="http://localhost/maine.zip"><font size=15> <B> MAINE pictures </B></font></a>



IndyTim

---

### Post by mbeach on 2008-07-16
you probably don't want to be using the absolute filepath reference like that.  Let's say your index.html file is already in /var/www/, then your link would look like:
<a href="maine.zip">Maine Pictures</a>

As you have it now, it may work in your browser on the same machine as the server, but if you were to connect from any other machine, it would not.

Once you get going, you'll likely end up with more than just pictures of Maine, so you may want to create a folder /var/www/pictures and put maine.zip in there.  Your index.html in /var/www would then point to:
<a href="pictures/maine.zip">Maine Pics</a>

A side note, and off topic, and perhaps not all that important in the grand scheme of things, but you may want to learn a little bit about css instead of starting out with the <font size=15> type tags.

A good place to start:
[http://www.w3schools.com/css/](http://www.w3schools.com/css/)

---

### Post by groshart on 2008-07-16
> **ramsam said:**
> 
this is how my INDEX.HTML file looks
************************************************** *
<html><body><h1>It works!</h1></body></html>


<a href="/var/www/maine.zip"<font size=15> <B> MAINE pictures </B></font></a>
************************************************** *


You have a lot of problems with your html. You shouldn't need to put "/var/www/" in the url if the file is in that directory. That particular directory is the default for the HTTP server. The closing </body> and </html> tags are also in the wrong place. This would be better but is still kind of ugly:

<html>
<body>
<h1>It works!</h1>
<a href="maine.zip"><font size="15"><b>MAINE pictures</b></font></a>
</body>
</html>

---

### Post by Kolipoki on 2008-07-16
Hi Ramsam,

Both mbeach and groshart are correct in their replies. I will second their suggestions. Though we are assuming here that the zip folder is actually in /var/www

However, something is puzzling me, when you say "It downloads but its not the complete file ?" What exactly do you mean? Because if you are getting a fraction of the file, then the link is not broken (thou weirdly written in html), in that case the .zip file could be corrupted and would need to be transfered again. 

My 2 cents...

---

### Post by windependence on 2008-07-16
I think he's just getting the html file when he downloads.

-Tim

---

### Post by silverglade00 on 2008-07-16
Ramsam, trying putting this:

```
<html><body>
<h1>It works!</h1>
<a href="maine.zip"<font size=15> <B> MAINE pictures </B></font></a>
</body></html>
```

It also could be an issue with the browser. Try right-click and Save Link...

---

### Post by windependence on 2008-07-16
Seriously, it would be easier just to allow directory listings. :)

-Tim

---

### Post by ReFuSeD88 on 2008-07-16
Agrees w/ tim here:popcorn:

---

### Post by q.dinar on 2008-07-16
with some css:
```
<html>
<head><style type="text/css">.upper_case {text-transform:uppercase;}</style>
</head>
<body>
<h1>It works!</h1>
<a href="maine.zip" style="font:bold 20px;"><span class="upper_case">maine</span> pictures</a>
</body>
</html>
```

2009-01-29: maybe/probably this what i said was not needed, ramsam himself could know this, i wrote this because i probably had not understand that he just used apache's default file. as i have heard one day, that file has become "it works" only on some recent apache version and so maybe i did not know that, or i did not use apache much that time.

---

### Post by ramsam on 2009-01-29
It been fixed guys. I was referring it to the wrong dir.

Thanks for the suggestions.

-ramsam

---

