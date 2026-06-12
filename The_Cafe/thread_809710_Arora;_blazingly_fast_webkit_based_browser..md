---
title: "Arora; blazingly fast webkit based browser."
date: 2008-05-27
forum: The Cafe
---

### Post by smbm on 2008-05-27
Hi

It's QT based but still amazingly fast on my GTK machine.

Worth a look in maybe?

[http://code.google.com/p/arora/](http://code.google.com/p/arora/)

---

### Post by Perpetual on 2008-05-27
Unfortunately it doesn't work with Yahoo! mail.  Or at least Yahoo! won't let it work.

---

### Post by ShodanjoDM on 2008-05-27
Already tried it and yes, it's fast. But since it's still in development, I'd like to see if it's still lightweight and fast after its got more features added.

---

### Post by qazwsx on 2008-05-27
7/100 in acid3 test

I compiled it in couple of minutes :) Nice

---

### Post by Speed Demon on 2008-08-11
wont work for me... has unmeetable dependencies on qts side of things in kde4

---

### Post by kernelhaxor on 2008-08-11
Is it faster than FF3?

---

### Post by KhaaL on 2009-04-01
for me its mighty faster than FF3 and FF3.1. it will definatly be my starndard webbrowser on my eeepc. I hope they will add some modularity so we can have adblock and such.

Anyone knows if there are debs for version 0.6?

---

### Post by mips on 2009-04-01
> **kernelhaxor said:**
> Is it faster than FF3?

Yip, try for yourself.

---

### Post by artir on 2009-04-01
Try epiphany with webkit compilled from svn.
It gets 100/100 on the acid test and is quite fast.

---

### Post by smartboyathome on 2009-04-01
> **artir said:**
> Try epiphany with webkit compilled from svn.
It gets 100/100 on the acid test and is quite fast.

And still doesn't have support for cookies, unlike Arora. :(

---

### Post by smbm on 2009-04-01
> **KhaaL said:**
> Anyone knows if there are debs for version 0.6?

I'm building it in my PPA at the mo. Will let you know how it goes.

---

### Post by smbm on 2009-04-01
Seems to work really well.

[https://launchpad.net/~t.vetterlein/+archive/ppa](https://launchpad.net/~t.vetterlein/+archive/ppa)

---

### Post by Skripka on 2009-04-01
> **mips said:**
> Yip, try for yourself.

Google V8 benchmark of 920...versus FF 200 or so. :D


Use it with Privoxy and you got a winner.

---

### Post by Lunx on 2009-04-01
Wonder how it'll stack up with the new Opera 10? I tried the alpha last year on my Windows machine and it absolutely flew. Now I'm a linux convert 9.64 doesn't seem as fast as the previous release, FF3 seems to be quicker than Opera, but not enough to make me change from the **[SIZE="6"][COLOR="Red"]O[/COLOR][/SIZE] **

---

### Post by Skripka on 2009-04-01
> **Lunx said:**
> Wonder how it'll stack up with the new Opera 10? I tried the alpha last year on my Windows machine and it absolutely flew. Now I'm a linux convert 9.64 doesn't seem as fast as the previous release, FF3 seems to be quicker than Opera, but not enough to make me change from the **[SIZE="6"][COLOR="Red"]O[/COLOR][/SIZE] **

Way faster than Opera on Linux, 9 or 10.  Opera for Windows is far better written than for Linux. It is also native Qt4 for 64bit-which is something Opera refuses to do....it is also far lighter.  Win.  Win.  Win.

---

### Post by steeleyuk on 2009-04-01
Anybody done a comparison between this and Midori?

Using Midori now and its got quite stable in the last few days. Still need to get Flash working with it though.

---

### Post by Skripka on 2009-04-01
> **steeleyuk said:**
> Anybody done a comparison between this and Midori?

Using Midori now and its got quite stable in the last few days. Still need to get Flash working with it though.

Flash works fine in Arora.

---

### Post by steeleyuk on 2009-04-01
Yea, Flash works fine with Webkit. Its just I haven't gotten it working with Midori yet. Using the Flash 10 64-bit rather than the one from the repo's.

---

### Post by smbm on 2009-04-01
Flash just worked for me in Arora, I'm running the 64bit version that I manually installed in Firefox.

---

### Post by Lunx on 2009-04-01
> **Skripka said:**
> Way faster than Opera on Linux, 9 or 10.  Opera for Windows is far better written than for Linux. It is also native Qt4 for 64bit-which is something Opera refuses to do....it is also far lighter.  Win.  Win.  Win.
  
 
 
 I was a huge Opera fan when I first began using it, last couple of upgrades have been pretty disappointing and now I'm finding some sites won't even load for me using it. Been trying all night to get into Launchpad, but no go. I thought it may have been an issue with the site, but just tried it with FF and had no problem. May have to swallow my pride and go back to the fox I'm thinking

---

### Post by MaindotC on 2009-04-01
> **qazwsx said:**
> 7/100 in acid3 test

I compiled it in couple of minutes :) Nice

You said 7/100 but artir said ephiphany built with webkit gets 100/100.  Is it good to get a lower or higher score out of 100?

---

### Post by steeleyuk on 2009-04-01
The higher the better.

Acid3 also should be a smooth animation as well to technically pass the test.

---

### Post by KhaaL on 2009-04-01
smbm, thanks its working real smooth! +karma for having a 64bit version too :)

steeleyuk, midori is awkwardly crashy compared to arora aswell being very feature poor. it dosent load facebook nor google documents, and i use the latter quite heavily so it was not a browser i could rely on.

---

### Post by cinna on 2009-04-01
Best on kde, too many QT dependencies with Gnome

---

### Post by steeleyuk on 2009-04-01
> steeleyuk, midori is awkwardly crashy compared to arora aswell being very feature poor. it dosent load facebook nor google documents, and i use the latter quite heavily so it was not a browser i could rely on.

It does crash for me every now and again. I don't use it very often, just usually after an update to see how its doing.

Just tried Google Docs, seems to be working OK with the latest version besides the notice which appears with a workaround.

---

### Post by adamlau on 2009-04-01
Shiretoko starts up slower but renders pages much faster than Arora on my box.

---

### Post by villainy on 2009-04-02
**EDIT:** I figured it out. I downloaded the source code from the webpage and used qmake-qt4>make and it worked :)

I'm having trouble compiling this :(

I followed this guide using the git process: [http://code.google.com/p/arora/wiki/BeginnerStepByStepInstructions](http://code.google.com/p/arora/wiki/BeginnerStepByStepInstructions)

Here is my terminal:
mike@mike-desktop:~$ cd arora
mike@mike-desktop:~/arora$ qmake-qt4
mike@mike-desktop:~/arora$ make
cd src/ && make -f Makefile 
make[1]: Entering directory `/home/mike/arora/src'
/usr/bin/lrelease -silent locale/cs_CZ.ts -qm .qm/locale/cs_CZ.qm
Usage:
    lrelease [options] project-file
    lrelease [options] ts-files [-qm qm-file]
Options:
    -help  Display this information and exit
    -nocompress
           Do not compress the .qm files
    -verbose
           Explain what is being done
    -version
           Display the version of lrelease and exit
make[1]: *** [.qm/locale/cs_CZ.qm] Error 1
make[1]: Leaving directory `/home/mike/arora/src'
make: *** [sub-src-make_default] Error 2

Any ideas on how to get this to work? Or can give me another way of compiling (I'm a complete noob at Linux). I'd love to try this out.

---

### Post by villainy on 2009-04-02
This might sound like a stupid question, but my arora doesn't look right at all. The fonts are off, and everything just looks...off. Is there something I should put into 'Style Sheet'? It just doesn't look pretty like other programs. Does this have something to do with QT?

Mine is nowhere near the looks of the screenshots on the arora page.

[http://i40.tinypic.com/11idg7k.png](http://i40.tinypic.com/11idg7k.png)

---

### Post by sertse on 2009-04-02
Arora is a "qt" app. If you're using the standard ubuntu, most of your things are follow the "gtk" theme. 

It's possible to get qt apps to theme like gtk one. The easiest way is to wait till Jaunty (Intrepid's isn't new enough) and download qt4-qtconfig, and using that set the qt look follow gtk.

It's also possible to download, compile and install qgtkstyle on top an existing install, and qtconfig....

Back to topic: I never found midori or aroa to be that fast, coming from my tweaked firefox.

---

### Post by mariuz on 2009-04-07
> **villainy said:**
> **EDIT:** I figured it out. I downloaded the source code from the webpage and used qmake-qt4>make and it worked :)

I'm having trouble compiling this :(


What version of ubuntu do you use 
is better to use an already compiled one 

if you are on intrepid or jaunty there is already one with qt 4.5
in my repository (also i have seen one above)
[http://groups.google.com/group/arora-dev/browse_thread/thread/106b6b6bf72ca64b](http://groups.google.com/group/arora-dev/browse_thread/thread/106b6b6bf72ca64b)

---

### Post by mariuz on 2009-04-07
> **villainy said:**
> This might sound like a stupid question, but my arora doesn't look right at all. The fonts are off, and everything just looks...off. Is there something I should put into 'Style Sheet'? It just doesn't look pretty like other programs. Does this have something to do with QT?

Mine is nowhere near the looks of the screenshots on the arora page.

[http://i40.tinypic.com/11idg7k.png](http://i40.tinypic.com/11idg7k.png)

you can start it with -style option (from kde)

for example i start it with oxygene
arora -style oxygene

---

