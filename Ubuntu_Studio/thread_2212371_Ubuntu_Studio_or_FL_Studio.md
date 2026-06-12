---
title: "Ubuntu Studio or FL Studio?"
date: 2014-03-20
forum: Ubuntu Studio
---

### Post by MonicaM on 2014-03-20
Hello, our Windows XP crashed and I cannot recover it, for a few complicated reasons. Anyway, my brother needs FL Studio, and I don't know anything about that program, or making music on a PC. Would the audio stuff on Ubuntu Studio help him make beats or run his instuments by chance? Would it be simple for him to use if he knows how to do music? Thanks for any replies.

---

### Post by su:bhatta on 2014-03-21
Hi, Welcome to the forums.

FL Studio, as in Fruity Loops, I am guessing. Major difference :FL Studio is one program which is used for audio generation. Ubuntu Studio is a Operating system. Ubuntu Studio comes with some inbuilt packages that are geared towards Audio, Video, Photography production and Graphic design programs.

Ubuntu Studio will come with a customized low-latency linux kernel which is more suitable for seamless audio work environment. Ubuntu Studio by default has a program called, LMMS( Linux MultiMedia Studio) which is similar to FL Studio. But there will be a learning curve to use LMMS. .
Also included is Hydrogen Drum Machine which can be used to genrate and playback drum sequence and Internet DJ Console.
Also, other program called Rosegarden is available & can be easily installed using Software-Center

Also, your brother can use FL Studio from the Ubuntu Studio installation using Wine, which gives a platform to install and use generic Windows applications.
You can see here that FL Studio has Gold rating for version 11.0 : [http://appdb.winehq.org/objectManager.php?sClass=application&iId=178](http://appdb.winehq.org/objectManager.php?sClass=application&iId=178)

You have to take a decision taking these into account and also, keep in mind you have to see the computer compatibility with Linux. 
If you give the Hardware specs of your computer it will be helpful. Read up a little in these lines(Google search)and you will be able to come to a decision.

---

### Post by jejeman on 2014-03-21
> **MonicaM said:**
> Would the audio stuff on Ubuntu Studio help him make beats or run his instuments by chance? Would it be simple for him to use if he knows how to do music?
He needs time and dedication to learn Ubuntu Studio and available software. It is not easy at all.
If he can run FL under WINE he could have a software break at least.

---

### Post by MonicaM on 2014-03-21
Thank you both. I need to make it as easy for him as possible. We'll probably end up getting Windows 8. I tried Ubuntu once and liked it though.

---

### Post by su:bhatta on 2014-03-21
You should give him a flavor by installing Ubuntu Studio in a virtual machine and see how he is taking it.... 

You never know, he might like it and go ahead..

---

### Post by MonicaM on 2014-03-21
What is a virtual machine? You know, I might end up with Ubuntu on something. See, we had 2 Pcs, and Windows got ruined on both, one's battery was going out, and none of the recovery disks are working exept one, but that was on my Dell Xps 720, which needs these dell drivers on a floppy disk to actually run the windows recovery and I have no floppy drive. So yeah, complicated, lol. My brother just bought himself another PC with no OS installed so we need to get on on there. I might play around with Ubuntu on mine after I get his fixed.

---

### Post by Frogs Hair on 2014-03-21
Here are two nice programs from the Ubuntu Software Center to give you an idea what is available .

[http://www.hydrogen-music.org/hcms/node/6](http://www.hydrogen-music.org/hcms/node/6)


[http://ardour.org/](http://ardour.org/)

---

### Post by su:bhatta on 2014-03-21
> **MonicaM said:**
> What is a virtual machine? You know, I might end up with Ubuntu on something. See, we had 2 Pcs, and Windows got ruined on both, one's battery was going out, and none of the recovery disks are working exept one, but that was on my Dell Xps 720, which needs these dell drivers on a floppy disk to actually run the windows recovery and I have no floppy drive. So yeah, complicated, lol. My brother just bought himself another PC with no OS installed so we need to get on on there. I might play around with Ubuntu on mine after I get his fixed.

From what you've told I can suggest you two options:

1) Vitual Machine: Using a program called VirtualBox (there are other such programs too) you can install a Ubuntu Studio, or for that matter many Operating systems, and see how they are run. That is you will have installed one operating system inside another, using a program. I suggest you read a little about it  by google search. [http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox)

2) Your other option is to Dual boot, Windows and Ubuntu. That is, you can choose what OS to load when the system starts. That way your brother can use FL as well as get his hands dirty with Ubuntu Studio. [http://www.makeuseof.com/tag/tired-of-windows-8-how-to-dual-boot-windows-ubuntu/](http://www.makeuseof.com/tag/tired-of-windows-8-how-to-dual-boot-windows-ubuntu/)

you go through the two links and see if you find them interesting.

Also, see Frogs Hairs links and find out how nice programs are offered in the Linux world.
And, if your Dell is old for Ubuntu (like low RAM, Graphics card), I would suggest loading Lubuntu([http://lubuntu.net/](http://lubuntu.net/)) or Xubuntu([http://xubuntu.org/](http://xubuntu.org/)) on it. 
One thing to keep in mind, there are no separate drivers required for Linux. Most drivers will come inbuilt, for some you will have to download them from required websites.

---

### Post by brianmc on 2014-03-28
> **MonicaM said:**
> [...] My brother just bought himself another PC with no OS installed so we need to get on on there. I might play around with Ubuntu on mine after I get his fixed.

Well, if he's no operating system at-all, there's nothing to lose in simply installing Ubuntu Studio and having a play with it. The next long-term support version of Ubuntu comes out next month, but I do very nicely with the 13.10 version of Ubuntu Studio; I've got it on three machines here, and it works pretty well for most basic functions I need. Admittedly, one of the boxes is pretty high-end, and being set up as a semi-pro, semi-portable, recording studio; but, as others point out, WINE (the Windows Emulator), works pretty well with Fruity Loops Studio - as well as there being a range of alternatives under Ubuntu Studio.

---

### Post by tmixshinodarap on 2014-04-10
Hello there! 

I've made some research and found how to make it work with jackd and wineASIO, (It says FLS 9 but it work on FLS 11.1)

Do every step

[http://ubuntuforums.org/showthread.php?t=1260057](http://ubuntuforums.org/showthread.php?t=1260057)

---

### Post by su:bhatta on 2014-04-11
> **tmixshinodarap said:**
> Hello there! 

I've made some research and found how to make it work with jackd and wineASIO, (It says FLS 9 but it work on FLS 11.1)

Do every step

[http://ubuntuforums.org/showthread.php?t=1260057](http://ubuntuforums.org/showthread.php?t=1260057)

Yes, Fruity Loop works with Wine & that's what all the posters in the present thread had advised the OP.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=178](http://appdb.winehq.org/objectManager.php?sClass=application&iId=178)

---

### Post by yan4 on 2014-04-28
I have found FL Studio 10 running into Wine much better than installed on Windows 7 as a Virtualbox guest.

---

### Post by yan4 on 2014-04-28
> **su:bhatta said:**
> Yes, Fruity Loop works with Wine & that's what all the posters in the present thread had advised the OP.

...however it may not work with some VSTs such as Musiclab RealGuitar, RealStrat or RealLP due to the fact that these specific VSTs won't install on Wine.

---

### Post by cub on 2014-04-30
As the alternative seemed to be Windows 8 I would say the learning curve is expected no matter if you choose to run Win8 or Ubuntu Studio. Being a linux advocate I think you/he should give Ubuntu Studio a test run as the advantages are several. Being free is one of them ...

---

### Post by Atitudes on 2014-05-02
> **cub said:**
> As the alternative seemed to be Windows 8 I would say the learning curve is expected no matter if you choose to run Win8 or Ubuntu Studio. Being a linux advocate I think you/he should give Ubuntu Studio a test run as the advantages are several. Being free is one of them ...

+1 here

Sometimes the UI is not the best of all but damn, I was amazed with plugins like ZynAddSubFx, the smoothness of Audacity (same with Ardour), Hydrogen makes some pretty good work and sincerely, Wine gets the rest!! Using CtrlJack even Reason suits like a glove and latency problems are easily solved in Ubuntu (even easier, as stated before, with Ubuntustudio). 

Therefore, I really reinforce the going for a > **cub said:**
> test run as the advantages are several. Being free is one of them ....

Cheers and GL!

p.s. By the way, I even have it on a 16Gb pen fully "pimped" and up-datable (since I finally manage to get a full install instead of the common "bootable" version thanks to the kind forum users help). And this worked in every emergency I have encountered :)

---

