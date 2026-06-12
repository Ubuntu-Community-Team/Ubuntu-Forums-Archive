---
title: "Google Earth working"
date: 2005-12-31
forum: The Cafe
---

### Post by macewan on 2005-12-31
Just wanted to drop a note to say that I've gotten Google Earth working. Menu and nav* are all fucked looking but it does work.

[[IMG]http://www.macewan.org/wp-content/images/GoogleEarthLinuxSmall.png[/IMG]]("http://www.macewan.org/wp-content/images/GoogleEarthLinux.png")

---

### Post by somuchfortheafter on 2005-12-31
umm any links on how-to's?

---

### Post by macewan on 2005-12-31
[http://www.flexion.org/site/index.php?gadget=StaticPage&action=Page&id=10]("http://www.flexion.org/site/index.php?gadget=StaticPage&action=Page&id=10")

if you run into errors

[http://bugs.winehq.org/show_bug.cgi?id=3329](http://bugs.winehq.org/show_bug.cgi?id=3329)

---

### Post by mcmuffy on 2005-12-31
How did you get it to install? I keep stalling at en error saying the operating system is not supported even though I have set it to winxp as instructed.

EDIT : Scratch that. I found a hidden setting I missed. Works fine now except for the menus.

---

### Post by macewan on 2005-12-31
It's pretty fun - would like to get the menus and navigation system working though

---

### Post by sinbad782 on 2005-12-31
It's a shame Google haven't ported this to Linux. It seems to run perfectly well in OpenGL mode under Windows and so I'm sure it would run fine under Linux. The same can be said for NASA's WorldWind software.

---

### Post by sinbad782 on 2005-12-31
It's strange as it seemed to start up and run fine (subject to graphical errors in the menus, tables etc.) using Wine .93 but ever since Wine .94 was released it won't start and just hangs at the splash screen. I then have to manually kill the wine processes to get rid of it. 

The only other dialog I get is one asking if I would like to download and install the Mozilla ActiveX plugin - something I am rather dubious about - for all the usual reasons!

---

### Post by sapo on 2005-12-31
[QUOTE=sinbad782]It's a shame Google haven't ported this to Linux. It seems to run perfectly well in OpenGL mode under Windows and so I'm sure it would run fine under Linux. The same can be said for NASA's WorldWind software.[/QUOTE]
thats because google is becoming evil :(

---

### Post by mstlyevil on 2005-12-31
Give Google time and they will develop a Linux native version.

---

### Post by mdbarton on 2006-01-11
[QUOTE=mstlyevil]Give Google time and they will develop a Linux native version.[/QUOTE]

You could always give them some encouragement: [http://earth.google.com/support/bin/request.py?contact_type=suggestion&submit=Continue](http://earth.google.com/support/bin/request.py?contact_type=suggestion&submit=Continue)

I've managed to get Google Earth working under wine (0.95), but it isn't as good as using it on windows (navigation is missing and fonts on place labels are terrible).

Found this [https://wiki.ubuntu.com/Wine?highlight=%28wine%29](https://wiki.ubuntu.com/Wine?highlight=%28wine%29)
and this [https://wiki.ubuntu.com/GoogleEarth](https://wiki.ubuntu.com/GoogleEarth) helpful

---

### Post by emerick7 on 2006-01-12
I've been trying to follow the instructions on the wiki regarding the Google Earth install. I've installed wine and I'm able to download the DCOM98 exe, but then when I do the next step (WINEDLLOVERRIDES="ole32=n" wine DCOM98.EXE), it comes up with the error: "DCOM98 can only be installed on Windows 98. For Windows NT, please install latest service packs." What can I do to get around this?

---

### Post by jasay on 2006-01-12
I hope they do make a linux version soon.  Apparently they made a [mac version]("http://googleblog.blogspot.com/2006/01/google-earth-in-mac-world-pc-too.html").  They also claim that the mac user have given > more than a few "requests" so speak up everyone.

---

### Post by drizek on 2006-01-12
just emailed em....

---

### Post by UbuWu on 2006-01-12
[QUOTE=jasay]so speak up everyone.[/QUOTE]

Google earth? WW2D runs on linux and it can view Earth, Moon and Mars!

[http://ww2d.csoft.net/](http://ww2d.csoft.net/)

---

### Post by engla on 2006-01-19
I downloaded this one to my mac as soon as it was released.. but I really miss it on this Ubuntu desktop (pretty low-end, but what can't I do with ubuntu on it? [right-- browse the earth ])

Anyway, I noticed the mac version of Google Earth is not built with Cocoa, but is linked to libqt (included in the app package). Does this mean Google is preparing to release a Linux port and decided to save some work?

---

### Post by drizek on 2006-01-19
[QUOTE=engla]but is linked to libqt (included in the app package). Does this mean Google is preparing to release a Linux port[/QUOTE]

id say that is a very strong sign. i imagine in the future they will jus switch to qt entirely and use it for linux, windows and osx.

---

### Post by macewan on 2006-01-30
[quote=emerick7]I've been trying to follow the instructions on the wiki regarding the Google Earth install. I've installed wine and I'm able to download the DCOM98 exe, but then when I do the next step (WINEDLLOVERRIDES="ole32=n" wine DCOM98.EXE), it comes up with the error: "DCOM98 can only be installed on Windows 98. For Windows NT, please install latest service packs." What can I do to get around this?[/quote]

from command line type

winecfg

now select win98 from the drop down menu located towards the bottom of the screen.

---

### Post by sup on 2006-02-03
Hello, I followed the wiki entry about Google Earth and it was working, but then I upgraded to wine 0.9.6 and suddenly it wont start.
It gives this:
```
wine: Call from 0x7fca49b0 to unimplemented function usp10.dll.ScriptGetCMap, aborting

```
although I start it with WINEDLLOVERRIDES=\"ole32,usp10,msvcrt=n\"
aand I have got usp10.dll from windows in wine's system32 directory. Anyone here also encountered this error?

---

### Post by BLTicklemonster on 2006-02-03
Cool, thanks for the info!

---

### Post by sup on 2006-02-03
0.9.7. gives just the same result. I will probably try to reinstall everything...:-/

EDIT: I just used winecfg and set up google earth to use native windows ole32 and usp10 from there and it suddently works

---

### Post by krusbjorn on 2006-02-03
[http://www.flashearth.com/](http://www.flashearth.com/)

---

### Post by xmastree on 2006-02-05
[QUOTE=krusbjorn][http://www.flashearth.com/](http://www.flashearth.com/)[/QUOTE]
Great! I always wanted a black square in the top left corner of my browser window... :-k

---

### Post by macewan on 2006-02-05
[quote=xmastree]Great! I always wanted a black square in the top left corner of my browser window... :-k[/quote] 
same here

side note, before you can install dcom.exe you need to winecfg and set to win98.

---

### Post by krusbjorn on 2006-02-05
Heh. It worked for me. I guess you have flash installed and working?

---

### Post by xmastree on 2006-02-05
Well now you've got one! :-)
There is a menu on he left, if you click the arrow. But the contents are invisible...

I installed WW2D, it runs but it ain't google earth...

---

### Post by macewan on 2006-02-05
for those installing google earth be sure to get google earth and install with wine before adding all the extra files.

---

### Post by BLTicklemonster on 2006-02-05
A How to would be nice. I saw a link, but it says absolutely nothing about google earth. It did however have useful info concerning ther things, so I bookmarked it. Or did I miss a post somewhere along the way?


I would install ww2d, but upon looking at the page, I see where it says, "you will also need yada yada yada". Experience dictates that this will only result in utter frustration on my part. Learning to deal with the command line is one thing, but my sherlock holmes hat only comes out for certain reasons, and a program that I can't get in synaptic or terminal and have dependencies load automatically is not one of them. Nothing like spending hours tracking down why something won't install to make windows and it's 20 click installation (do you agree to the license agreement? -anyone ever say no?- Are you sure you wish to install this? -duh, no, I have no idea what I'm doing- Would you like to install this where stuff always goes? -no, I want to install it on my video card, stupid- etc etc etc) look almost palatable... don't flame me!!! I'm just making a point!

Okay, I'm done ranting, and I don't feel any better. What did I miss? 

(Bah, I might go try later when I have time, lol)

---

### Post by BLTicklemonster on 2006-02-05
New thing, or I would just edit my post...


In windows this is wierd, but not sure about in ubuntu, but bring up google earth, and search for washington dc. now once it zooms in, search for lincoln memorial, and see where it puts you. In windows, it's just east of Kungur. I had no idea that the Kunguranites even knew who Lincoln was, much less that they had a memorial to him... lol.

---

### Post by xmastree on 2006-02-05
[QUOTE=BLTicklemonster]I would install ww2d, but upon looking at the page, I see where it says, "you will also need yada yada yada".[/QUOTE]It's not that bad.
I'm running 5.04 so YMMV. I have JRE and openGL installed already.
There are two packages you need to install. download the JOGL thing (open GL driver), and run it as root from a console by typing **sudo java -jar JOGL-Inst-1.10.jar**
It should install.
Then download and unpack ww2d-0.99.87.zip which gives you a folder (where you put it) containint two other folders (earth, global), and a jar file.
Run the jar file with **java -jar WW2D.jar**

It worked fine for me, just don't click the **E** in the top right corner... That crashes mine :rolleyes:

---

### Post by BLTicklemonster on 2006-02-05
[QUOTE=xmastree]It's not that bad.
I'm running 5.04 so YMMV. I have JRE and openGL installed already.
There are two packages you need to install. download the JOGL thing (open GL driver), and run it as root from a console by typing **sudo java -jar JOGL-Inst-1.10.jar**
It should install.
Then download and unpack ww2d-0.99.87.zip which gives you a folder (where you put it) containint two other folders (earth, global), and a jar file.
Run the jar file with **java -jar WW2D.jar**

It worked fine for me, just don't click the **E** in the top right corner... That crashes mine :rolleyes:[/QUOTE]
Dude, never tell me not to click the e thing... that's gonna pester the dickens outta me.

So did you try the lincoln memorial?

---

### Post by xmastree on 2006-02-05
So, go ahead and click it... :rolleyes:

Accorting to the text (at the bottom of the screen) It's for **E**xport. Presumably exports a screenshot. What it does for me is crashes the app.. In fact, before I saw the text I thought the E was short for **E**xit.

---

### Post by xmastree on 2006-02-10
Well, I've been messing with WW2D, and Ihave to say, whilst the interface is similar to google Earth, the resolution sucks.

Compare and contrast.

Mumbai, India.

WW2D's version:
[ATTACH]6008[/ATTACH]

And now, Google maps' version:
[ATTACH]6007[/ATTACH]

However, with Google Maps you can zoom in **much** further.
Just at the top of that high-res section is that place where they tear apart old ships.

[http://maps.google.com/maps?f=q&hl=en&q=mumbai&t=k&ll=18.97232,72.851779&spn=0.003318,0.006748&t=k](http://maps.google.com/maps?f=q&hl=en&q=mumbai&t=k&ll=18.97232,72.851779&spn=0.003318,0.006748&t=k)

Ok, so google maps doesn't have the slick interface, but the detail is there...

---

