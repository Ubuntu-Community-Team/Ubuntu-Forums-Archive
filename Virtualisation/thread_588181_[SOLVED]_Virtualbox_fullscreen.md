---
title: "[SOLVED] Virtualbox fullscreen"
date: 2007-10-23
forum: Virtualisation
---

### Post by Malice007 on 2007-10-23
I installed Virtualbox  and when I go to full screen it blows up the virtualbox window to full but the os running in it stays the same size... I am not running any desktop effect. I would just like to  
when I tell it full screen show me the whole screen just like it was not running off of Ubuntu? Is this possible?

---

### Post by Orbital75 on 2007-10-23
Humm..... that's interesting.  Are you going to full screen by using the correct command?
You do this by pressing the Right side ( Ctrl  F ) 

If thats not the issue then it sounds like a Video problem and we'll have to wait for
more responses because thats beyond my knowledge with this particular application.

---

### Post by tsgray on 2007-10-23
I had the same problem for a while. While you have you guest OS running select "install guest additions" from the devices menu. Reboot when prompted and when it comes back up host + F should take it to full screen. You may need to readjust you resolution and color depth.

---

### Post by Dr Small on 2007-10-23
I always start virtualbox on another X session, without gnome-session, so I have no bars and whatnot. Then when I open VirtualBox fullscreen, there are no bars to hinder me :D

---

### Post by bodhi.zazen on 2007-10-23
> **tsgray said:**
> I had the same problem for a while. While you have you guest OS running select "install guest additions" from the devices menu. Reboot when prompted and when it comes back up host + F should take it to full screen. You may need to readjust you resolution and color depth.

+1

---

### Post by Malice007 on 2007-10-24
Installing guest additions fix the problem thank you.

---

### Post by theblang on 2008-11-14
This fixed the problem for me as well.  Here is a link to installing the guest additions.

[http://www.robotification.com/component/content/article/8-programming/7-how-to-install-virtual-box-additions-on-ubuntu.html](http://www.robotification.com/component/content/article/8-programming/7-how-to-install-virtual-box-additions-on-ubuntu.html)

---

### Post by itisbasi on 2008-11-20
Thanks....Installing guest additions fixed the full screen issue for me too...

---

### Post by janthonywj on 2009-02-23
Solved my screen resolution problem, and also informed me about the OSE, USB issue I was about to hit. Thanks.

---

### Post by gineraso on 2009-03-24
Nice work.  Thank you.:D

---

### Post by mahendra.pardeshi on 2009-05-21
Great work !!!! ):P

---

### Post by brateni112 on 2009-07-13
> **theblang said:**
> This fixed the problem for me as well.  Here is a link to installing the guest additions.

[http://www.robotification.com/component/content/article/8-programming/7-how-to-install-virtual-box-additions-on-ubuntu.html](http://www.robotification.com/component/content/article/8-programming/7-how-to-install-virtual-box-additions-on-ubuntu.html)

Hello,
I'm new to linux, a friend of mine told me to try it out and I really like it. So I'm using MagixBox, but when I try to install guest additions - nothing happens.

I looked at hte link but could not make out what to do at the begining. I know how to write the codes. Can anyone give me a  step by step guide?

-------------------------
Pentium M 725 1.60GHz Processor, 2MB L2-Cache
  ATI Mobility RADEON 9000 AGP 4X video graphics at 32MB
  14.1-in SXGA Monitor
  60GB Ultra ATA Hard Drive, 4200RPM
  1GB RAM
  Microsoft Windows XP Pro with Service Pack 3

Thnks in advance!

---

### Post by bodhi.zazen on 2009-07-13
What is "MagixBox" ? Do you mean Virtualbox ?

Is Ubuntu your host or guest ?

---

### Post by brateni112 on 2009-07-13
> **bodhi.zazen said:**
> What is "MagixBox" ? Do you mean Virtualbox ?

Is Ubuntu your host or guest ?


Yes VirtualBox
Linux Ubuntu is my guest hosteed on windows. I can't get full screen, I did try everything mentioned above, except that text in the link.

---

### Post by bodhi.zazen on 2009-07-13
That is a very very old link, from 2007.

Shut down the guest.

For the CD, use the additions iso and reboot the guest.

If needed, mount the iso:

```
sudo mount /dev/cdrom /media/cdrom
```

Then run the installer script:

```
sudo /media/cdrom/VBoxLinuxAdditions-x86.run
```

If you are running a 64 bit guest, run the 64 bit script.

---

### Post by brateni112 on 2009-07-14
What iso do you mean in your second sentence?
I downloaded VirtualBox from their website.
Ubuntu 9.04 is on bootable CD

I understood the rest but not hte part about the iso. please explain.
P.S. My englih is exellent BUT still not my mother-language.

---

### Post by renbla on 2009-07-14
> **Dr Small said:**
> I always start virtualbox on another X session, without gnome-session, so I have no bars and whatnot. Then when I open VirtualBox fullscreen, there are no bars to hinder me :D

Hehe i never heard of this method till today. I will use this method :lolflag:

---

### Post by brateni112 on 2009-07-14
> **bodhi.zazen said:**
> That is a very very old link, from 2007.

Shut down the guest.

For the CD, use the additions iso and reboot the guest.

If needed, mount the iso:

```
sudo mount /dev/cdrom /media/cdrom
```Then run the installer script:

```
sudo /media/cdrom/VBoxLinuxAdditions-x86.run
```If you are running a 64 bit guest, run the 64 bit script.

I got it. I will try this out and let ya'll know if it worked.

---

### Post by brateni112 on 2009-07-14
> **bodhi.zazen said:**
> That is a very very old link, from 2007.

Shut down the guest.

For the CD, use the additions iso and reboot the guest.

If needed, mount the iso:

```
sudo mount /dev/cdrom /media/cdrom
```Then run the installer script:

```
sudo /media/cdrom/VBoxLinuxAdditions-x86.run
```If you are running a 64 bit guest, run the 64 bit script.


It all worked great! :p Now I will be able to test Linux couse I really like it. And this forum comunity is excellente!

WORKS GREAT!

P.S. I downloaded the addition iso from:
[http://download.virtualbox.org/virtualbox/2.2.0/VBoxGuestAdditions_2.2.0.iso](http://download.virtualbox.org/virtualbox/2.2.0/VBoxGuestAdditions_2.2.0.iso)

---

### Post by bodhi.zazen on 2009-07-14
Awesome. FYI, the additions .iso is included with VirtualBox (PUEL edition).

---

### Post by phenity on 2009-07-20
that link was very helpful. Now I know how to set this up on any other computer I want to as well.

---

### Post by pboxinator on 2009-07-27
Thanks a bunch! This really helped solve my fullscreen problem that I have been glocking over since I got my new Mac lol. I love Linux and the tiny screen on a big monitor looked really stupid. Thx =)

---

### Post by Berduchwal on 2009-07-28
I have guess additions installed on the guest Windows XP, Ubuntu 9.04 is my host.
I run in full screen CTRL + F
Still I have only small screen in the middle and max resolution I can set up in XP is 800x600.

see image attached.

---

### Post by CaptCrunch on 2009-09-21
I had this issue too when already having guest additions installed, Ctrl + F would still show a small screen despite resolution adjustments. Going to Machine > Auto-Resize Guest Display, adjusted the window to perfectly match my monitor display (at 1920 x 1051 px).

---

### Post by 2kquik on 2010-01-18
Thanks it worked! ;)

---

### Post by LordOfThePigs on 2010-01-20
> **Dr Small said:**
> I always start virtualbox on another X session, without gnome-session, so I have no bars and whatnot. Then when I open VirtualBox fullscreen, there are no bars to hinder me :D

This sounds like the perfect setup for me! How can I do that?

---

### Post by OmahaVike on 2010-02-08
> **LordOfThePigs said:**
> This sounds like the perfect setup for me! How can I do that?

I'm guessing something like this?

[https://wiki.ubuntu.com/CustomXSession]("https://wiki.ubuntu.com/CustomXSession")

---

### Post by fuzzy_hero on 2010-02-17
Hi,

This is my first time of using linux.... I'm having a similar problem of getting it to show in fullscreen. I tried out the suggestions (installing virtual box addition as instructed in this link [http://www.robotification.com/component/content/article/8-programming/7-how-to-install-virtual-box-additions-on-ubuntu.html](http://www.robotification.com/component/content/article/8-programming/7-how-to-install-virtual-box-additions-on-ubuntu.html)) mentioned but couldn't get it right.

Please can someone help me out (its my first time using linux) with this?

Thanks

---

### Post by jinmaning on 2010-06-13
i have solved this! pretty easy guys! visit my blog [http://jinnyfeb.blogspot.com/2010/06/how-to-make-ubuntu-1004-go-to-full.html]("http://jinnyfeb.blogspot.com/2010/06/how-to-make-ubuntu-1004-go-to-full.html")

---

### Post by henrx on 2013-02-04
Solved for me thank you.

---

### Post by wildmanne39 on 2013-02-05
Old thread closed.

---

