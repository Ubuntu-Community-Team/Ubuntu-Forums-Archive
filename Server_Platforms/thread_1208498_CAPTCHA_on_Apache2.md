---
title: "CAPTCHA on Apache2?"
date: 2009-07-09
forum: Server Platforms
---

### Post by crawford.rich on 2009-07-09
Has anyone had any success getting CAPTCHA to display the image on their server.

I have Apache2 running and php5.   The CaptchaSecurityImages.php doesn't generate an image.  There must be a module that I need to install?  Any tips would be greatly appreciated.  THNX

---

### Post by Thirtysixway on 2009-07-09
Double-check that you have GD installed, that's what php uses to generate images.

---

### Post by windependence on 2009-07-09
You need to have [FONT=monospace]the [/FONT]GD and FreeType libraries loaded to run the code.

Let me make sure because you weren't clear in your post. You are running a php script which you copied or wrote yourself right?

-Tim

---

### Post by crawford.rich on 2009-07-09
Yes, it is PHP script.  I'm fairly new to php and Apache2.   

The script was written and uploaded by my web developer.  When you say GD, what exactly do you mean.  I have libgd-gd2-perl installed.
THNX

---

### Post by crawford.rich on 2009-07-09
I installed php5-gd.  Not sure how to install/config freetype.  Getting closer.

---

### Post by wojox on 2009-07-09
Here is the freetype website if you need it

[http://freshmeat.net/projects/freetype/](http://freshmeat.net/projects/freetype/)

---

### Post by Thirtysixway on 2009-07-09
> **crawford.rich said:**
> I installed php5-gd.  Not sure how to install/config freetype.  Getting closer.

This is all you should need, I believe.

sudo apt-get install php5-gd

---

### Post by windependence on 2009-07-10
> **wojox said:**
> Here is the freetype website if you need it

[http://freshmeat.net/projects/freetype/](http://freshmeat.net/projects/freetype/)

It would be better to use the package that contains the freetype library from the Ubuntu repositories.

```
sudo apt-get install freetype2
```

-Tim

---

### Post by crawford.rich on 2009-07-10
Tried to install freetye2 - got the following: 

rcrawford@rcrawford-laptop:~$ sudo apt-get install freetype2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package freetype2
rcrawford@rcrawford-laptop:~$

---

### Post by windependence on 2009-07-11
Sorry, I think they are included in the msttcorefonts package.

```
sudo apt-get install msttcorefonts
```

-Tim

---

