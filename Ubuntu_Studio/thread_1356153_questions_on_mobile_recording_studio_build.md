---
title: "questions on mobile recording studio build"
date: 2009-12-15
forum: Ubuntu Studio
---

### Post by svtfmook on 2009-12-15
i'm building a mobile recording studio for recording live music and what not.  then some mixing and misc audio/video production at home.

i'm going to be using an asus k70 series lap top, this one actually
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220641](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220641)

and i also purchased an m-audio fast-track pro usb
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220641](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220641)

question number one, should i go with 64bit, or x86 as far as ease of configuring goes?

question number two, will i have any problems setting up the m-audio fast track with ubuntu studio?

question number three, will the hdmi output work?

i have used ubuntu for a few years, from 6.10 to 9.04, but haven't used is for about a year.  not sure how well my hardware will play with ubuntu.

---

### Post by AutoStatic on 2009-12-16
> **svtfmook said:**
> i'm building a mobile recording studio for recording live music and what not.  then some mixing and misc audio/video production at home.

i'm going to be using an asus k70 series lap top, this one actually
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220641](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220641)Looks good, any specs available on the internal soundchip/codec?

> **svtfmook said:**
> and i also purchased an m-audio fast-track pro usb
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220641](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220641)

question number one, should i go with 64bit, or x86 as far as ease of configuring goes?64bit. The notebook has 4Gb of RAM, 32bit only uses 3Gb, unless you use a PAE kernel, but as far as I know there's no RT PAE kernel so I'd go for 64bit.

> **svtfmook said:**
> question number two, will i have any problems setting up the m-audio fast track with ubuntu studio?Yes you will: [http://ubuntuforums.org/showthread.php?t=1311006](http://ubuntuforums.org/showthread.php?t=1311006)

> **svtfmook said:**
> question number three, will the hdmi output work?Depends on the internal soundchip/codec.

---

