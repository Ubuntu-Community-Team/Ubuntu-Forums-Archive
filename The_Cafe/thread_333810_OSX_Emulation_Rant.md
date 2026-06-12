---
title: "OSX Emulation Rant"
date: 2007-01-08
forum: The Cafe
---

### Post by 4KvRMU7Nnv on 2007-01-08
I feel like ranting about my attempts to get a good dock bar for ubuntu.  here we go:

First I tried kiba.  I liked it.  It was cool enough, worked perfectly, never any problems, but then I saw kxdocker.  OOOOOOOooooooOooOOOO.  So I tried it out.  EVENTUALLY, i managed to get it just to find that most of my configurations wouldn't save even with the store to thing.  Ive downloaded and gotten kxdocker working various times with varying success though none of which successful enough to make me respect the product.  I almost gave up hope when I saw Engage.  I thought it couldn't hurt to give It a try.  So i got it from the repo and installed it, configured it, found Icons.  I loved it.  It was perfect.  Then during a download and a messy desktop i switched to a new desktop to have a clean slate and low and behold...Engage wasn't there.  Engage only draws itsself onto one desktop.  I NEED ALL FOUR OF THEM!!!!!!  and so...here i find myself back at kiba dock after a long affair with seductive but toxic dock alternatives.

SO childeren let my story be a lesson to you...don't do drugs...no wait. that wasn't it.... a well.

---

### Post by macogw on 2007-01-08
sudo apt-get install -y gDesklets

There's a dock in there

---

### Post by dbbolton on 2007-01-08
i have personally had nothing but trouble with gdesklets

---

### Post by riven0 on 2007-01-08
Personally, I think the Gnome dock is good enough. But that's just me. :mrgreen:

---

### Post by spockrock on 2007-01-08
> **riven0 said:**
> Personally, I think the Gnome dock is good enough. But that's just me. :mrgreen:

umm I dunno if that is gnome dock that just looks like a transparent gnome bar with icons.  gnome dock is a project based off cairo dock.


I myself use kxdocker, I was liking kiba dock, but then it just randomly died.... I am think of just installing gnome dock and seeing how that turns out.....

---

### Post by macogw on 2007-01-08
> **dbbolton said:**
> i have personally had nothing but trouble with gdesklets

Yeah when I tried changing how the transparency works on it, I broke it.

---

### Post by hanzomon4 on 2007-01-08
If only someone could port [rklauncher]("http://home.cogeco.ca/~rklauncher/")

---

### Post by podunk on 2007-01-08
Try kooldock from the repos. Works perfectly with minimal set up, easy drag and drop. I use Kubuntu, I sort of suspect it will install a lot of KDE libs.

---

### Post by hanzomon4 on 2007-01-08
Tried it but it acted "strangely" may try it again later...........

---

### Post by darkhatter on 2007-01-08
the kcdocker in repos doesn't work for me, I tried both the edgy and Feisty

---

### Post by 4KvRMU7Nnv on 2007-01-08
Yeah, I'm using kiba now becuase I think it is the best for composite and multiple desktops.  It is also the easiest to configure.  Engage is fine except it only works with one desktop

---

### Post by macewan on 2007-01-11
check for build-essentials

sudo apt-get install build-essential

sudo apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev

wget [http://www.macewan.org/cairo-1.2.6.tar.gz](http://www.macewan.org/cairo-1.2.6.tar.gz)

tar -xzf cairo-1.2.6.tar.gz

rm cair*.gz

cd cair*

./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc

make

sudo make install

cd ../

wget [http://www.macewan.org/cairo-dock.tar.gz](http://www.macewan.org/cairo-dock.tar.gz)

sudo mv cairo-dock.tar.gz /opt

cd /opt

sudo tar -xzf cairo-dock.tar.gz

sudo rm cairo-dock*.gz

cd cairo-dock

sudo make clean

sudo make

./cairo-dock --no-glitz

credit goes to [GPH]("http://www.ubuntuforums.org/showthread.php?t=302570") of Ubuntuforums


> **d3br074 said:**
> I feel like ranting about my attempts to get a good dock bar for ubuntu.  here we go:

First I tried kiba.  I liked it.  It was cool enough, worked perfectly, never any problems, but then I saw kxdocker.  OOOOOOOooooooOooOOOO.  So I tried it out.  EVENTUALLY, i managed to get it just to find that most of my configurations wouldn't save even with the store to thing.  Ive downloaded and gotten kxdocker working various times with varying success though none of which successful enough to make me respect the product.  I almost gave up hope when I saw Engage.  I thought it couldn't hurt to give It a try.  So i got it from the repo and installed it, configured it, found Icons.  I loved it.  It was perfect.  Then during a download and a messy desktop i switched to a new desktop to have a clean slate and low and behold...Engage wasn't there.  Engage only draws itsself onto one desktop.  I NEED ALL FOUR OF THEM!!!!!!  and so...here i find myself back at kiba dock after a long affair with seductive but toxic dock alternatives.

SO childeren let my story be a lesson to you...don't do drugs...no wait. that wasn't it.... a well.

---

### Post by eitan_a on 2007-01-12
Hey, I just installed the cairo dock.  It works except none of the icons show up!

---

### Post by spockrock on 2007-01-13
> **eitan_a said:**
> Hey, I just installed the cairo dock.  It works except none of the icons show up!

only works with svgs right now.

---

### Post by eitan_a on 2007-01-13
yeah found that out...going to have to convert my pretty icons now (unless ppl are willing to upload their collection of SVG ones)

---

### Post by eitan_a on 2007-01-14
OK, just worked for about an hour and brought over a bunch of icons, so looking pretty good!

I also want to turn off autohide.  I find though, when autohide is off, a good portion of the bottom of the screen is unusable as clicking above an icon runs it.  Any idea on how to fix?

Thanks!

I'll keep looking at it tomorrow and if i find a fix I'll post.

---

