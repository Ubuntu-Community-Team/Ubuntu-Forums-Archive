---
title: "Can Ubuntu still not play DVDs out of the box?"
date: 2009-04-08
forum: The Cafe
---

### Post by Kazade on 2009-04-08
OK, I'm confused... I've been using Ubuntu since Breezy, and I remember back then having to jump through hoops to get DVDs to play (especially encrypted ones).

Then, I'm sure somewhere along the line this was fixed. I *thought* some automatic package installation was implemented when you try to play a DVD. I must have been mistaken.

I haven't played a DVD in my computer for a long time (years, probably since Dapper), but tonight I tried and failed. I've installed totem-xine, libdvdread3, libdvdcss2 etc. etc. I've read tutorials and Google'd like crazy, and yet I can't get it to work.

I'm going to give up. I'm totally baffled though, I though this was all sorted ages ago, am I wrong? Does every user still have to jump through hoops to play a DVD?

P.S. I'm well aware of the legal issues surrounding playing DVDs

---

### Post by swoll1980 on 2009-04-08
```
sudo apt-get install ubuntu-restricted-extras
```
if you use kubuntu then kubuntu-restricted-extras, or for xubuntu xubuntu-restricted-extras

---

### Post by gnomeuser on 2009-04-08
I think due to the legal issue surrounding this, the testing is low aside that the incentive to develop it is also low (considering the illegality of some components, it might bring legal trouble upon any company who paid for this work to be done).

Fewer lawyer that seems to be the answer

---

### Post by TBOL3 on 2009-04-08
Interesting, granted I play dvds on VLC, but when I started to play my first dvd, I got a pop up, saying to download the right codec, and it worked.  I'm sorry it's not working for you.

---

### Post by gnomeuser on 2009-04-08
btw. I think the GStreamer project has finishing DVD support up as a Google Summer of Code project proposal. Hopefully this will lead to some improvement

---

### Post by dspari1 on 2009-04-08
Yeah it's illegal for Ubuntu to do that, but if you get a "community" or "fan" distro like Mint(which is basicly Ubuntu) and Sabayon, you can get all that working out of the box.

I think if you buy Ubuntu, you get everything working out of the box because it's paid for, but I'm not sure about this one. I know that the Dell version of Ubuntu does.

---

### Post by swoll1980 on 2009-04-08
> **TBOL3 said:**
> Interesting, granted I play dvds on VLC, but when I started to play my first dvd, I got a pop up, saying to download the right codec, and it worked.  I'm sorry it's not working for you.

VLC has a disclaimer on their website about it's legality in certain countries. Ubuntu made a promise to always be freely distributable. Including DVD codecs would break that promise.

---

### Post by .Maleficus. on 2009-04-08
> **dspari1 said:**
> Yeah it's illegal for Ubuntu to do that, but if you get a "community" or "fan" distro like Mint(which is basicly Ubuntu) and Sabayon, you can get all that working out of the box.

I think if you buy Ubuntu, you get everything working out of the box because it's paid for, but I'm not sure about this one. I know that the Dell version of Ubuntu does.
...Which is technically illegal.  Mint offers various versions of the distro for just that reason.

OP:  ubuntu-restricted-extras is what you're looking for.  Having libdvdcss2 and the other various DVD packages around is never a bad idea though.

---

### Post by TBOL3 on 2009-04-08
What does that have to do with anything?  Sure, I have to download the codecs, but I have to download vlc too.  Also, I think VLC is set up in the repos, so that you can download VLC without the legally gray codecs.

Also, I just thought, how new is the dvd?  I've heard that newer dvds have a new layer of encryption on them.

---

### Post by toupeiro on 2009-04-09
I digress but, ubuntu doesn't come in a box...

---

### Post by mikewhatever on 2009-04-09
> **toupeiro said:**
> I digress but, ubuntu doesn't come in a box...

nice:lolflag:

---

### Post by JECHO on 2009-04-09
See the my blog (the entry entitled "7 things you need to do on a fresh ubuntu installation") in my signature to get all of the needed codecs for ubuntu... Its very simple now.

---

### Post by jwbrase on 2009-04-09
Swoll1980: *Great* signature!

---

### Post by hanzomon4 on 2009-04-09
> **jwbrase said:**
> Swoll1980: *Great* signature!


I know... right? 

I just can't help adding: for the rest of his short and agonizing life:

---

### Post by gnomeuser on 2009-04-09
> **dspari1 said:**
> Yeah it's illegal for Ubuntu to do that, but if you get a "community" or "fan" distro like Mint(which is basicly Ubuntu) and Sabayon, you can get all that working out of the box.

I think if you buy Ubuntu, you get everything working out of the box because it's paid for, but I'm not sure about this one. I know that the Dell version of Ubuntu does.

I meant more that since it's illegal nobody is spending the time doing the work. Managing and crowdsourcing testing of an international standard isn't light work you sit down and do over the weekend as a volunteer. Since the legal issues prevent Linux vendors from investing in making this work as well it's sadly some complicated code that is not being worked on much.

There are vendors like Dell who ship a proprietary tool to play DVDs on their OEM machines and I know Fluendo are creating a DVD player for the same use cases.

I think the issue is just going to get worse with Blu-ray, I am in honesty starting to think that the sanest approach is to create a separate attempt at standardization using Open Standards. This will be a lot of work but at some point Blu-ray will have to give way to a format that is suitable for internet broadcasting and other such requirements. I think the sane thing is to aim to win there and admit that the former are battles we have lost. We will get there eventually and it is an important goal to do so but progess is just to slow right now.

---

### Post by LowSky on 2009-04-09
It cant work from a clean install, because of legality of public use, some countries like the US, say that the proper people need to be _**PAID **_to use a codec. So to make those people happy, Ubuntu does not include the codec. If you want a free Operating System then these are things you will have to put up with


i386:
```
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```


amd64:
```

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

Reboot and it will work with VLC/Totem/Mplayer

---

### Post by swoll1980 on 2009-04-09
> **jwbrase said:**
> Swoll1980: *Great* signature!

Thanks. I forget where I heard that. I thought it was funny though.

---

### Post by gn2 on 2009-04-09
> **dspari1 said:**
> Yeah it's illegal for Ubuntu to do that ~

Only in some parts of the world, not everywhere.

Other distros provide free and non-free versions, there's no reason Ubuntu shouldn't.

---

### Post by NightwishFan on 2009-04-09
A community project for such a thing can be started. In fact I think that is what Mint Linux is.

I am mainly hoping the laws get changed eventually rather than to bother to watch movies that are so very restricted.

It is sort of funny how when talking about new restrictions on Windows with HD content and movies, they say users of Mac and Linux will not get "official access" to this content.

Well yeah us "linuxers" have unofficial access. Good day sir!

Hey does this mean Microsoft admits we exist.. :lolflag:

---

### Post by richg on 2009-04-09
I have tried Ubuntu 8.04, 8.10, 9.04 out of the box and they cannot run DVDs. I installed Mint 6 based on Ubuntu 8.10 and I can view DVDs right out of the box. Go figure. 
Don't tell me about the "easy" workarounds. They did not work for me. Other than that, Ubuntu is ok. I am sticking with Mint 6.
I joined PC World forums and some where surprised at this issue.

Rich

---

### Post by Mokoma on 2009-04-09
dont forget libdvdcss2 from synaptic ;)

---

### Post by richg on 2009-04-09
Been there, did not work. Don't need the T shirt. It was easier to install Mint 6 than to keep messing with the issue.
Change is inevitable, struggle is an option, but not for me.

Rich

---

### Post by inobe on 2009-04-09
that sort of playback is the same on any platform excluding some countries..

the first thing one does after installing any os is hunt down drivers and codecs.

[http://shop.canonical.com/index.php?cPath=19&osCsid=8a1858f599d71cf397c3a40574875873](http://shop.canonical.com/index.php?cPath=19&osCsid=8a1858f599d71cf397c3a40574875873)

---

### Post by Skripka on 2009-04-09
> **inobe said:**
> that sort of playback is the same on any platform excluding some countries..

the first thing one does after installing any os is hunt down drivers and codecs.

[http://shop.canonical.com/index.php?cPath=19&osCsid=8a1858f599d71cf397c3a40574875873](http://shop.canonical.com/index.php?cPath=19&osCsid=8a1858f599d71cf397c3a40574875873)

Also, not every distro works the same regarding codecs.  Example: When I put Arch on my box-I installed VLC along with KDE and one way or another all codecs necessary for media playback hitched dependency ride with the player packages.  No extra messing around-which was quite slick and welcome.

---

### Post by swoll1980 on 2009-04-09
> **richg said:**
> I have tried Ubuntu 8.04, 8.10, 9.04 out of the box and they cannot run DVDs. I installed Mint 6 based on Ubuntu 8.10 and I can view DVDs right out of the box. Go figure. 

Rich

Did you not read the thread? There's no "workaround" it's not "broken" this is the way it's supposed to be. Mint is illegal in many countries because of it's "easiness" using the codecs isn't a big deal, because if you bought a computer you probably paid for them, but if you were to give them to someone else it's actually a pretty serious issue.

---

### Post by inobe on 2009-04-09
> **Skripka said:**
> Also, not every distro works the same regarding codecs.  Example: When I put Arch on my box-I installed VLC along with KDE and one way or another all codecs necessary for media playback hitched dependency ride with the player packages.  No extra messing around-which was quite slick and welcome.

i had the same experience with opensuse, thanks to pacman repos.

---

### Post by zekopeko on 2009-04-09
i think that playing unencrypted DVD with menus works in jaunty.
closed standars suck :(

---

