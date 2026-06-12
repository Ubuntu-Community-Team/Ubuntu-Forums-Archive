---
title: "Install New Themes on Rockbox"
date: 2008-07-01
forum: The Cafe
---

### Post by geek_Man on 2008-07-01
Okay, I know how to install themes on Rockbox, but whenever I try to use them, none of the nice, fancy "Now Playing" decorations work. Like, instead of buttons, you get crappy, white bars and stuff... I think it's something to do with the wps files, but I'm not fer shurz. Themes that come pre-installed with a build work fine, but none I get online. Any ideas? Thanks!



Hopefully this is the right thread...

---

### Post by Lostincyberspace on 2008-07-01
Are the versions compatible? Are the themes complete? I also would try to find the creators and ask them if they know how to do it. I don't use it but I would if I had an Ipod.

---

### Post by |{urse on 2008-07-01
I do use it, works fine for me on zeroslackr ipod linux. installed the newer rockbox and the newer themes work too. maybe you need a different version of rockbox, I think the guy above me has your problem nailed. Try a diff version.

---

### Post by Keith Hedger on 2008-07-01
Are u using a custom build? I tried a few of them when I first tried rockbox and had loads of trouble also some themes are only for certain machines (different screen sizes etc) if u dont mind using the terminal try building from svn the instructions for this is on the rockbox website (under developers i think) i use the svn version for my old ipod photo and once the tool chain is set up its dead easy to keep rockbox upto date
I have been using rockbox exclusively for a couple of years now I think its the wasps nipples!

---

### Post by bleedingpowers on 2008-07-01
I can confirm this issue of themes only showing plain white fonts/text during playback. I have a nano 1st gen. and the rockbox release is r-17910.

I'm going to have to revert to a previous release that works with themes...Any word about which? Previously, I was using r-16558  and themes worked ok.

I will let you know which release works for me.

---

### Post by geek_Man on 2008-07-02
Thanks

---

### Post by bleedingpowers on 2008-07-02
I compiled rockbox from source, and I still can't get the themes to show a proper WPS While Playing Screen). 

Fortunately, I found out that the problem is due to a syntax change for WPS (and most of them need to be updated). 

I got this information from: [http://forums.rockbox.org/index.php?topic=17499.0]("http://forums.rockbox.org/index.php?topic=17499.0")

I guess we'll have to either modify the syntax on these themes ourselves, or wait until they get updated...There might be some themes that are compatible with the latest syntax.

Read more WPS problems here: [http://forums.rockbox.org/index.php?board=24]("http://forums.rockbox.org/index.php?board=24")

Good luck!

---

### Post by geek_Man on 2008-07-02
Sweet. Thanks for the help.

---

### Post by CompCrash on 2008-07-18
I been having the same issue and the info here help me figure out what is wrong. I'm going to try some things and see if I get it to work.

I check in later.

---

### Post by grossaffe on 2008-07-18
> **geek_Man said:**
> Okay, I know how to install themes on Rockbox, but whenever I try to use them, none of the nice, fancy "Now Playing" decorations work. Like, instead of buttons, you get crappy, white bars and stuff... I think it's something to do with the wps files, but I'm not fer shurz. Themes that come pre-installed with a build work fine, but none I get online. Any ideas? Thanks!



Hopefully this is the right thread...

they recently updated a part of the While Playing Screen, I think it was the Progress Bar.  So any theme that utilized the custom Progress Bar no longer works.  You just need to look at the documentation to see how it changed and you can fix it yourself.

edit: I made a couple of themes and already updated them for the WPS, if you use a sansa e200 (or i guess any player that has a 220 x 176 screen, right?), then you can give 'em a try.  (one of them is dedicated to a website so you may not find it interesting, but the other one is based of a popular OF theme).

crystal theme:
[IMG]http://i150.photobucket.com/albums/s109/Grossaffe/CrystalWPS.jpg[/IMG] [IMG]http://i150.photobucket.com/albums/s109/Grossaffe/CrystalMenu.jpg[/IMG]
[http://www.box.net/shared/sqh4ys6g5j](http://www.box.net/shared/sqh4ys6g5j)

Lodist theme:
[IMG]http://i150.photobucket.com/albums/s109/Grossaffe/LodistAA.jpg[/IMG] [IMG]http://i150.photobucket.com/albums/s109/Grossaffe/LodistMenu.jpg[/IMG]
[http://www.box.net/shared/tvo0o5t6cs](http://www.box.net/shared/tvo0o5t6cs)

---

