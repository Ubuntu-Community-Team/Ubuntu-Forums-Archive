---
title: "Good-looking Linux distro for really old laptop?"
date: 2008-12-29
forum: The Cafe
---

### Post by SrEstroncio on 2008-12-29
Hello everyone.

Lately I have been reading a lot of posts regarding Crunch Bang Linux, a low-resource distro based on Ubuntu, and how it operates well low-resource computers. I've had the idea to buy really old computers and install linux on them just for the fun of it, but I am quite illiterate in Linux apart from everyday computing in my ubuntu box. So I ask, what would you install on a 1 GHz, 256MB RAM, 10GB hard drive box, and why? Bonus points for providing screenshots or an application list.

---

### Post by Rokurosv on 2008-12-29
Hmm perhaps:

[Slitaz]("http://www.slitaz.org/en/")
[TinyMe]("http://tinymelinux.com/doku.php")
[NimbleX Sub100]("http://www.nimblex.net/index.php?option=com_content&task=view&id=87&Itemid=55")
[Puppy Linux]("http://www.puppylinux.org/home")

---

### Post by Private_Ops on 2008-12-29
Crunchbang should work really well.

I use it on my laptop (albeit, it's an Athlon dual core with 1GB of ram).

Here's a shot of the stock desktop.

[http://i95.photobucket.com/albums/l121/Ops_666/2008-12-01--1228189990_1280x800_scr.png](http://i95.photobucket.com/albums/l121/Ops_666/2008-12-01--1228189990_1280x800_scr.png)

---

### Post by Warpnow on 2008-12-29
sudo apt-get install fvwm-crystal

Though, with a 1ghz processor, you should be able to run Xubuntu fine.

---

### Post by tjwoosta on 2008-12-29
well, if you have 256 mb ram i think crunchbang should work fine, as long as you stick with lightweight apps

but if i were you i would just do a base install of whatever distro you want (arch is my top pick)

i say this for two reasons..

1. you say you dont have much linux knowledge but you want to install a distro for fun  (that says to me that you are really doing it to learn, and doing a base install is the perfect way to learn)

2. doing a base install will give you the opportunity to pick and choose EVERYTHING that goes into your distro (meaning that you wont end up with a bunch of crap that you dont need, which in turn makes a very lightweight and custom tailored distro)

also i definatly recomend using lightweight browser such as epiphany rather than firefox because i have noticed with my machine that firefox uses about twice the resources as epiphany

anyways if you do decide to give archlinux a try just remember to read and follow the install guide


here are some screenshots of my arch install with fluxbox  (notice the ram usage)

---

### Post by handy on 2008-12-29
Arch is great, the docs are great, follow the [***_Beginners Guide_***]("http://wiki.archlinux.org/index.php/Beginners_Guide") to the letter & the only thing that will let you down is if you have hardware that is incompatible.  Which when using old PII's & Celerons is quite possible.  Though if you get them really cheap, which you should ($5- here) then you get good value out of them by cannibalising them for parts.

The other problem you may have with Arch is that it is compiled for the i686 architecture, so anything older than the PII & Celeron won't work. 

I really like [***_Damn Small Linux_***]("http://damnsmalllinux.org/"), DSL will work on a 486 with 16Mb of RAM!  It has great hardware detection built in, & obviously uses minimal resources.  It is 50Mb in size.  There are varieties of it as well.  I think you may find it easier than some of the others to work with.  It is a LiveCD, so you can quickly test for compatibility with it.

---

### Post by snowpine on 2008-12-30
I think CrunchBang #! is a great choice. Check out this list of #! compatible hardware: [http://crunchbanglinux.org/forums/topic/147/your-crunchbang-linux-system/](http://crunchbanglinux.org/forums/topic/147/your-crunchbang-linux-system/)

CrunchBang comes in both Full and Lite versions. #! Lite has only a few basic applications (kazehakase web browser, pcmanfm file manager, leafpad text editor, vlc media player) and is a good choice if you want to install your own apps over a slightly-more-than-minimal install. #! Full comes with a full suite of applications, with an emphasis on internet (firefox, pidgin, skype, etc) and multimedia (gimp, rhythmbox, flash, etc).

---

### Post by sujoy on 2008-12-30
give it zenwalk or do a debian stable net install and build up from there. as handy said, arch might not be suited for it

---

### Post by Spike-X on 2008-12-30
A friend bought an old laptop last week with a 600mHz CPU, 256 Mb RAM, and a 20 Gb HD. I installed Xubuntu on it and it runs quite well.

---

### Post by tjwoosta on 2008-12-30
> Arch is great, the docs are great, follow the Beginners Guide to the letter & the only thing that will let you down is if you have hardware that is incompatible. Which when using old PII's & Celerons is quite possible.

ahh...

yes thats a very good point

i almost forgot that arch was i686 optimized


if arch isnt going to be compatible with your hardware, the next base install type distro i would recomend would have to be the Debian net install, like sujoy said

---

### Post by notwen on 2008-12-30
Although somewhat dated, You may want to look into [TinyFlux]("http://pcfluxboxos.wikidot.com/tinyflux").  It's PCLinuxOS w/ FluxBox.  Here are some [screens]("http://pcfluxboxos.wikidot.com/tinyflux-screenshots") of it.  Good luck w/ whatever you decide on.  =]

---

### Post by mikjp on 2008-12-31
> **SrEstroncio said:**
>  So I ask, what would you install on a 1 GHz, 256MB RAM, 10GB hard drive box, and why? 

I use Vector Linux on a Pentium 1 GHz + 256 Mb RAM, because:
- it is lightweight
- it includes multimedia codecs
- it is based on Slackware which means its design is simple

[Screenshots](http://vectorlinux.com/screenshots) are available.

Greetings,

mikko

---

### Post by mips on 2008-12-31
You state 1GHz CPU which leads me to believe it is much newer than a PII so go with Arch Linux. Just follow the Beginners Guide on wiki.archlinux.org

---

### Post by motang on 2008-12-31
> **Private_Ops said:**
> Crunchbang should work really well.

I use it on my laptop (albeit, it's an Athlon dual core with 1GB of ram).

Here's a shot of the stock desktop.

[http://i95.photobucket.com/albums/l121/Ops_666/2008-12-01--1228189990_1280x800_scr.png](http://i95.photobucket.com/albums/l121/Ops_666/2008-12-01--1228189990_1280x800_scr.png)
Yeah I would also have to reccomend Crunchbang! Although Xubuntu should be fine with Epiphany (Gecko) as the Webkit is too buggy.

---

