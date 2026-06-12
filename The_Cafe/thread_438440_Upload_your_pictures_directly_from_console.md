---
title: "Upload your pictures directly from console"
date: 2007-05-09
forum: The Cafe
---

### Post by zhapoo on 2007-05-09
Hi and sorry for this type of my first post :)
I didn't know where to post this, so i thought community cafe would be the best.

I'm not sure if there is something similiar already made, but in any case.. this is a script which can be used for easy uploading of images to net.

Script info & instructions: [http://elitepicturehost.com/linux_client.php](http://elitepicturehost.com/linux_client.php)

Some people have reported problems, so if it doesen't work properly.. you'll have to use "python eph /path/to/image.jpg" or make another script which will do it for you (python /path/to/eph $1)

i was gonna post output of example usage here, but forum automatically parsed all the tags, so it wasn't good.. here's a screenshot instead

[[img]http://elitepicturehost.com/up_thumbs/tmb_48daffa9248794bdc1907637fc0ed85a.jpg[/img]](http://elitepicturehost.com/viewpic.php?code=48daffa9248794bdc1907637fc0ed85a)

Maybe there will be a GUI client as well in future, but for now it'll stay console only

Any kind of feedback is welcome :)

---

### Post by haricharan on 2007-05-09
cool..thats great...wud try when i get home....

---

### Post by zhapoo on 2007-05-09
> **haricharan said:**
> cool..thats great...wud try when i get home....

cool, post if you get any problems and we'll try to find a solution.. i'm not sure yet if this works on all distros/configurations (one of the problems i have already posted above, dont know if there are some other issues)

p.s. there is also something if some of you own a website and would like to integrate it into your site: [http://elitepicturehost.com/integrate.php](http://elitepicturehost.com/integrate.php) to let your visitors upload images on a quick way directly from your page :)

If anyone knows how to make it work on all (or most of) distros/configurations by just chmoding it to +x, please let me know, it would be really nice if something like that is possible! Thanks

---

### Post by reacocard on 2007-05-09
> **zhapoo said:**
> cool, post if you get any problems and we'll try to find a solution.. i'm not sure yet if this works on all distros/configurations (one of the problems i have already posted above, dont know if there are some other issues)

p.s. there is also something if some of you own a website and would like to integrate it into your site: [http://elitepicturehost.com/integrate.php](http://elitepicturehost.com/integrate.php) to let your visitors upload images on a quick way directly from your page :)

If anyone knows how to make it work on all (or most of) distros/configurations by just chmoding it to +x, please let me know, it would be really nice if something like that is possible! Thanks

I found the fix! It's the line endings, the site gives them in CR/LF (windows) format. If you convert it to LF (unix) format, it works perfectly.

Beautiful little tool BTW. Tested it with my avatar, very slick:

[[img]http://elitepicturehost.com/up_thumbs/tmb_b4d420069e4c9e69692af8610724bee3.jpg[/img]](http://elitepicturehost.com/viewpic.php?code=b4d420069e4c9e69692af8610724bee3)

---

### Post by zhapoo on 2007-05-09
i will upload a fixed version tommorow.. will let you know when i do it

thanks a lot!

---

### Post by zhapoo on 2007-05-10
uploaded and tested.. now it should work on much more configurations

once again.. thanks reacocard

---

