---
title: "Without high speed internet"
date: 2007-02-01
forum: The Cafe
---

### Post by vivin_west on 2007-02-01
Well Ubuntu is certainly good for those with high speed internet. But for those whose download rates are low it is a big problem(like me). Is there a way where in I can order the Open source softwares I want.Like I make a list of sofware I want and post it this can be shipped. I dont mind paying for it shipping.

---

### Post by Mba7eth on 2007-02-01
here you go :) 
[http://www.osdisc.com]("http://www.osdisc.com/")

---

### Post by mips on 2007-02-01
Not really although there are prepackages cds for ubuntu.

In your situation you might be better of with one of the other distros that ships and entire cd/dvd set of all their stuff. Debian is one of them and the new version is bound to come out soon.

---

### Post by EmilyRose on 2007-02-01
Hey there, I'm stuck on dial-up too, so what I do to avoid tying up my phone line 24/7 is just download stuff at night (packages, updates, etc). Tisnt' like anyone's going to be calling us at 3am =)

---

### Post by Dragonbite on 2007-02-01
"Hi.. I'm Drew and I use dial-up." -- excerpt from dial-up annonymous

I'm hoping to rectify it but I am still on dial-up at this time. One trick I learned during my Gentoo days and haven't treid it yet but you may be able to get it to work is setting the system to hang up once it is done installing.

The scenario goes like this:

[LIST]
[*]Connect to the internet in the usual way
[*]Open a Terminal Window
[*]Install or at least download everything you want to install
```
apt-get install xyz
```
[*]Type the command to hang up which will execute when the installation/download is complete
```
killall pppd

[I]or something similar.. killall ppp? I'm not sure what will work. 
Practice trying to hang up after getting connected to find the code[/I]
```
[*]Check on it in the morning
[/LIST]

If you select to download only, then it will hang up quicker, otherwise it will proceed to install the program (and the time associated with that process) before hanging up.

This did become a life-saver when I foolishly downloaded KDE and almsot all componenets (~100MB)!  Ouch (and off course Gentoo compiles everything so on my 500MHz machine it took a looooooong time!)

If you manage to get it to work, please post the hang-up coding.

---

### Post by glabouni on 2007-02-01
> **vivin_west said:**
> Well Ubuntu is certainly good for those with high speed internet. But for those whose download rates are low it is a big problem(like me). Is there a way where in I can order the Open source softwares I want.Like I make a list of sofware I want and post it this can be shipped. I dont mind paying for it shipping.

you can try these:
[LinuxCD.org]("http://distrowatch.com/kokoku/linuxcdorg.php")
[OSdisc.com]("http://distrowatch.com/kokoku/osdisc.php?cgi-bin/view.cgi/index.html")

or you can ask someone you know who has high speed access to download and burn those for you, or evensomeone you don't know, many from ubuntu community would help you with that matter.

---

### Post by Adamant1988 on 2007-02-01
> **vivin_west said:**
> Well Ubuntu is certainly good for those with high speed internet. But for those whose download rates are low it is a big problem(like me). Is there a way where in I can order the Open source softwares I want.Like I make a list of sofware I want and post it this can be shipped. I dont mind paying for it shipping.

There are MANY sites where you can purchase Linux CDs for a small price. I don't know of any off-hand because I prefer to burn them, but I can also tell you that Ubuntu offers a free CD shipping program (although you do typically end up waiting for a month or more before receiving your disks).

---

