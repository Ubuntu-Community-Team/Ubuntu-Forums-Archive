---
title: "Post your console"
date: 2004-11-03
forum: The Cafe
---

### Post by cacofonix on 2004-11-03
Just wondering how everyone has set up their console. Here's what mine looks like

---

### Post by jdodson on 2004-11-03
[IMG]http://www.kennethfejer.dk/images/nintendo.jpg[/IMG] :mrgreen:

---

### Post by HungSquirrel on 2004-11-03
^ :-D


Mine's a transparent Eterm with no window borders sitting on my desktop.  You can see it in my [screenshot](http://hungsquirrel.org/images/ubuntu.jpg).

---

### Post by JsPr on 2004-11-03
Rather standard for me I believe.  :-) 
I liked jdodsons!

---

### Post by ubuntu-geek on 2004-11-03
[QUOTE=jdodson][IMG]http://www.kennethfejer.dk/images/nintendo.jpg[/IMG] :mrgreen:[/QUOTE]
 lol doesnt that bring back memories.. :)

---

### Post by jdodson on 2004-11-03
[QUOTE=ubuntu-geek]lol doesnt that bring back memories.. :)[/QUOTE]

for me it was epic.  mario brothers and legend of zelda were and still are some of the best games of all time.  so many memories, and i still own my console, play duck hunt and zelda occasionally:)

---

### Post by TravisNewman on 2004-11-03
[QUOTE=HungSquirrel]^ :-D


Mine's a transparent Eterm with no window borders sitting on my desktop.  You can see it in my [screenshot](http://hungsquirrel.org/images/ubuntu.jpg).[/QUOTE]
 What's the system monitor running on the right of your screen? I assume it's a gdesklets display. 

Is there anything you have to do to get those working? The transparency was all borked will all the desklets I tried.

---

### Post by oddabe19 on 2004-11-03
10 US bucks to the first person that manages to run Ubuntu on an NES. (original) :-P

anyway... here's mine.
```
Hit http://archive.ubuntu.com hoary/restricted Packages
Hit ftp://ftp.nerim.net unstable/main Packages
Hit http://archive.ubuntu.com hoary/restricted Release
Hit http://archive.ubuntu.com hoary/main Sources
Hit http://archive.ubuntu.com hoary/main Release
Hit http://archive.ubuntu.com hoary/restricted Sources
Hit http://archive.ubuntu.com hoary/restricted Release
Hit http://archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/universe Release
Hit http://archive.ubuntu.com hoary/universe Sources
Hit http://archive.ubuntu.com hoary/universe Release
Hit ftp://ftp.nerim.net unstable/main Release
Reading Package Lists... Done
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading Package Lists... Done
Building Dependency Tree... Done
Calculating Upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading Package Lists... Done
Building Dependency Tree... Done
 3 Nov 14:20:35 ntpdate[5457]: adjust time server 136.159.2.254 offset -0.018601 sec

Time is updated.

Yea! Your computer is now up to date. whoopie freaking do!
root@ubuntu:/home/oddabel/Desktop #

```

Just a little script i made that updates, upgrades, distupgrades, auto-cleans, and updates my clock.

---

### Post by TravisNewman on 2004-11-03
I adore this line:
```
 Yea! Your computer is now up to date. whoopie freaking do!
```

---

### Post by wallijonn on 2004-11-30
[QUOTE=HungSquirrel]Mine's a transparent Eterm with no window borders sitting on my desktop.  You can see it in my [screenshot](http://hungsquirrel.org/images/ubuntu.jpg).[/QUOTE]

I know that there must be some guys here who would love to replicate your desktop. Have you written a HOWTO?

---

### Post by zenwhen on 2004-11-30
Here's mine:

---

### Post by HungSquirrel on 2004-11-30
[QUOTE=panickedthumb]What's the system monitor running on the right of your screen? I assume it's a gdesklets display. 

Is there anything you have to do to get those working? The transparency was all borked will all the desklets I tried.[/QUOTE]
Yeah, they are all gdesklets.  They use the LT theme, and most of them can be found at /usr/share/gdesklets/ assuming you have gdesklets-data.  Their names/folders begin with LT or lt.

One exception is the temp sensor.  To get it, go [here](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=136).
To get all the temp sensors working:
```
sudo apt-get install mbmon xmbmon
sudo chmod 4755 /usr/bin/mbmon
sudo chmod 4755 /usr/bin/xmbmon
```

> I know that there must be some guys here who would love to replicate your desktop. Have you written a HOWTO?
The gdesklets, the term, or the whole thing?  :)

The term is:
```
sudo apt-get install Eterm
Eterm -f white -n DeskTerm -O -x --buttonbar false --scrollbar false
```

zenwhen, any chance you could post your cowsay file?  That's AWESOME!

---

### Post by zenwhen on 2004-11-30
Well it cames standard with debian cowsay or so it seems, but here you go. 

[http://zenhardwhere.com/files/bong.cow](http://zenhardwhere.com/files/bong.cow)

I think its pretty rocking too.

In case you meant you didn't know what cowsay itself is, here is the .deb installer. 

[http://zenhardwhere.com/files/cowsay_3.03-6_all.deb](http://zenhardwhere.com/files/cowsay_3.03-6_all.deb)

---

### Post by HungSquirrel on 2004-11-30
Ah, didn't know it was already included.  Thanks.  :)

---

### Post by adbak on 2004-11-30
[QUOTE=wallijonn]I know that there must be some guys here who would love to replicate your desktop. Have you written a HOWTO?[/QUOTE]
Almost sounds like a pick-up line.  ;)

---

### Post by jakeslife on 2004-12-23
So, uh...that's some transparent console you got there...can I uh...touch it?

No but really, I'd love to have one just like it!

---

### Post by darkoptix on 2004-12-24
[QUOTE=HungSquirrel]^ :-D


Mine's a transparent Eterm with no window borders sitting on my desktop.  You can see it in my [screenshot](http://hungsquirrel.org/images/ubuntu.jpg).[/QUOTE]

Modest Mouse is a rules!
Like how you done it.

---

### Post by jr_G-man on 2005-04-12
[img]http://members.cox.net/jrgman/images/screenshot_of_term.png[/img]

---

### Post by carlc on 2005-04-12
> sudo apt-get install Eterm
Eterm -f white -n DeskTerm -O -x --buttonbar false --scrollbar false


Thanks for the info! I added that command to start Eterm when I start Gnome and it works great. What I can not figure out is how to get it to start with a transparent window. Is that possible? I tried making it transparent and then saving user and theme settings and this works if I run Eterm after loading Gnome but for some reason, if I run Eterm as a startup program, it does not load with a transparent background.

---

### Post by poofyhairguy on 2005-04-12
[QUOTE=zenwhen]Here's mine:[/QUOTE]


I suddenly like Zenwhen more....

---

### Post by bpilgrim1979 on 2005-07-26
[QUOTE=HungSquirrel]
The term is:
```
sudo apt-get install Eterm
Eterm -f white -n DeskTerm -O -x --buttonbar false --scrollbar false
```

zenwhen, any chance you could post your cowsay file?  That's AWESOME![/QUOTE]

If I do this will it the desktop terminal start every time in Hoary?  Do I need to add it to my .bashrc?

If I install this, how do I turn off the desktop terminal if I want to?

Thanks.

---

### Post by benplaut on 2005-07-26
my metacity theme is the best EVER!  :grin: 

[img]http://img173.imageshack.us/img173/5172/screenshotbenbenhomeben0oi.png[/img]

---

### Post by benplaut on 2005-07-26
this thrad inspired me to work on it a bit, so now i'm using Xterminal (different from xterm, this is the one made for XFCE) instead of gnome-terminal

considerably faster, and same level (if not higher) of tweakability!

[img]http://img260.imageshack.us/img260/6052/screenshotterminalbenbenhomebe.png[/img]

[SIZE=1]Thanks ImageShack![/SIZE]

---

### Post by ubuntp on 2005-07-26
[IMG]http://img225.imageshack.us/img225/9482/c64term5eb.png[/IMG]

---

### Post by tomchuk on 2005-07-26
Aterm, proggy smooth font, zsh

---

### Post by NeoSNightmarE on 2005-07-27
Here's mine. It has a screenshot that someone sent me from Flight Simulator 2004. The game is boring but I love the screenshot. Check it out with the attachment. :D

---

### Post by Luggy on 2005-07-27
Here is mine: 
[[IMG]http://img242.imageshack.us/img242/8180/screenshot5tt.th.png[/IMG]](http://img242.imageshack.us/my.php?image=screenshot5tt.png)

ubuntp, that console is pretty sweet

---

