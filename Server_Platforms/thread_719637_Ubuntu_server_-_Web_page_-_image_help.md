---
title: "Ubuntu server - Web page - image help"
date: 2008-03-09
forum: Server Platforms
---

### Post by Rafiki123 on 2008-03-09
I&#8217;ve been running an Ubuntu LAMP server with Jinzora and Torrentflux for some time now and just recently wanted to create a web page for my server's index page but I am having trouble getting the images to show up (to make it look not like crappy html)

I can access the image from the web (type in the external ip and the file name) and it shows up fine, but will not show up on the webpage. I gave the picture and the index.html file 644 permissions because someone told me that that may work. Is this a permissions problem? Am I missing something here? I feel like this is an easy fix but it escapes me.

If anyone could offer an insight to why it may be doing this I would be extremely happy.

---

### Post by rapiscan on 2008-03-09
If you can view the image fine, but it doesn't show up in the HTML index, my bet is that it's a problem with the HTML.  Can you provide the HTML you are using to display the image?  Also, perhaps try including a different image in your HTML, something from another server, and see if you can get that working first.

---

### Post by Rafiki123 on 2008-03-09
I created an .html file with the fillowing code:

<img src="image.jpg">
<a href="/torrentflux/index.php">Torrentflux</a>

I also tried using a image's web address and it did the same thing. Its just a blank box with the alternate written in it.

---

### Post by Oldsoldier2003 on 2008-03-09
> **Rafiki123 said:**
> I created an .html file with the fillowing code:

<img src="image.jpg">
<a href="/torrentflux/index.php">Torrentflux</a>

I also tried using a image's web address and it did the same thing. Its just a blank box with the alternate written in it.

is image.jpg in the same directory? the code you have means it has to be in the same dir as the html page

---

### Post by Rafiki123 on 2008-03-10
Yeah its in the same folder as the html file.

---

### Post by rapiscan on 2008-03-10
Are you using firefox? Do you have some sort of extension installed that might be blocking this? (For example, perhaps it thinks the image is an ad for some reason and you have adblock installed.)

---

### Post by Rafiki123 on 2008-03-10
I'm using Opera but I tried to get it to work in IE and Firefox and no luck.

I'm think it has to do with the Linux system. It&#8217;s like the server is not letting the html display images for some reason. Is retrieving and displaying an image considered a file execution?

I just don't get why I can get the html to show up anywhere on the internet but no pictures. This is driving me crazy!

Also, I tried embedding a flash animation (with it in the home folder) and no beans with that either.

Is it maybe because I created the html file while logged on as root? Would that make a difference?

---

### Post by jonabyte on 2008-03-10
not sure if this will do it, but put /> to close the img tag.

Also, I don't believe apache prevents the use of images by default.

Is this a public site that we can test the page from our end?? If so, post the address.

---

### Post by Rafiki123 on 2008-03-10
My external IP address is 65.24.146.199. When you go to this page the index.html file is loaded. I was messing around with the HTML code so it&#8217;s not exactly as I described it earlier in the thread (the image is in a folder called webcam in the home folder.) [http://65.24.146.199/webcam/poo.jpg](http://65.24.146.199/webcam/poo.jpg) this is the image that is indicated in the HTML code. The link works to the picture and you can see the picture.

Also, in the home folder there is a flash animation that I made which also does not work when embedded.  So all that shows up in the HTML file is the links and the text.

---

### Post by rapiscan on 2008-03-10
Try it with the proper <html> and <body> tags.  I don't think this is the problem, but I'm out of ideas and it's worth a shot.

---

### Post by dmizer on 2008-03-10
you need to close your image tag.

```
<img src="http://65.24.146.199/webcam/poo.jpg">[COLOR="Red"]</img>[/COLOR]
```

edit:
you've also made a typo.  it should read **src** rather than scr.
```
<img **scr**="http://65.24.146.199/webcam/poo.jpg">
<BR>
This image is in the home directory but will now work (WTF?)
</center>
<embed **scr**="deathcab.swf" width="550" height="400">
</embed>
```
so your code won't work until you change scr to src like so:
```
<img [COLOR="Red"]src[/COLOR]="http://65.24.146.199/webcam/poo.jpg">
<BR>
This image is in the home directory but will now work (WTF?)
</center>
<embed [COLOR="Red"]src[/COLOR]="deathcab.swf" width="550" height="400">
</embed>
```

---

### Post by rapiscan on 2008-03-11
You don't actually have to close your image tags for the image to render, but if you want it to be valid xhtml you can close the tag with the slash at the end of the opening tag, like so:

<img src="image.jpg" />

As dmizer said, your problem looks to be a slight case of dyslexia :).  Funny thing is, I didn't even see it when looking at your source, so I guess my dyslexia automatically fixed it.

---

### Post by jonabyte on 2008-03-11
I visited your link and this is what i got in my ff browser

The image “[http://65.24.146.199/webcam/poo.jpg”](http://65.24.146.199/webcam/poo.jpg”) cannot be displayed, because it contains errors.

---

### Post by Rafiki123 on 2008-03-11
haha omfg I can't believe I missed that. I've been working on this for like a week now. Well that should do it. I'll fix that when I get home. 

Thanks to everyone!

---

