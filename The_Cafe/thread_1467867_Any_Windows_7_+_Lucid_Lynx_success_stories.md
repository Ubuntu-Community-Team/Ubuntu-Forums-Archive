---
title: "Any Windows 7 + Lucid Lynx success stories?"
date: 2010-05-01
forum: The Cafe
---

### Post by Access Excess on 2010-05-01
I have Windows 7 64bit installed on one of my hard drives. It uses two partitions, the main one and the 100MB System-reserved one.

I'm planning on installing 10.04 LTS 64bit on a third partition, as /, no swap, since I need the last primary partition for a future install of FreeBSD 8.

Has anyone done a successful install of Lucid after installing Windows 7 and managed to dual boot without a hitch afterwards? I'm reading some really nasty reports of dual boot failings. :(



Thanks in advance! :)

---

### Post by markyb73 on 2010-05-01
as long as you grabbed lucid after it was oficially released then you should have the version that fixed that bug. I run 64 bit win7 and 64 bit lucid with no problems :)If grub doesn't see windows 7 then try running sudo update-grub to see if it detects it after.
As for a swap partition i guess as long as you have plenty of RAM then you probably do not need swap depending on what you use it for. I'm sure someone can give a better answer to that.

---

### Post by RedMaster on 2010-05-01
I have on my disk installed Windows 7 Ultimate 64bit, which I don't use, but for some reason it is staying there... And 10.04 64bit on other partition... Everything works just fine! No problems with the dual boot... But you have to install Windows 7 first and then Ubuntu because as far as I remember the stupid Windows makes problems...

It's the same on my netbook. I haven't got any problems when I made a clean install of 10.04 (before I was on 9.10) and after the install the GRUB detected the Windows 7 :)

---

### Post by krishnandu.sarkar on 2010-05-01
Well....I'm using Win 7 32bit and Lucid Lynx. Just installed yesterday. Working like charm. No problem at all. Go ahed my friend.

---

### Post by KrisInfinity on 2010-05-01
I'm dual booting Windows 7 32bit with Lucid 64bit. Installation went without a hitch from the lucid rc. :)

---

### Post by Access Excess on 2010-05-01
Awesome! Thank you all for the quick replies!

I already have 7 installed and 4GB of RAM so I don't expect any problems.

Gonna go ahead and install it now. ^.^

---

### Post by RedMaster on 2010-05-01
> **Access Excess said:**
> Awesome! Thank you all for the quick replies!

I already have 7 installed and 4GB of RAM so I don't expect any problems.

Gonna go ahead and install it now. ^.^

Go for it! ^^
You will be amazed how smooth and fast the installation is! :P

---

### Post by Access Excess on 2010-05-01
I was amazed indeed! Looks great too!

And the startup time is much better. :D

---

### Post by Sporkman on 2010-05-01
> **Access Excess said:**
> ...since I need the last primary partition for a future install of FreeBSD 8.

Be careful! I had a Win 7 64 bit + Lucid 64 bit dual-boot install on my laptop which worked great. But then I installed PC-BSD 8, which I couldn't get grub to load. Turns out it messed up my disk partitions, then I messed them up even more trying to use that braindead program "testdisk".

Long story short, I ended up just nuking the whole disk & installing Lucid over the entire thing. Lost my Win 7, so I had to purchase a copy (as I never created a Win 7 recovery disk). On the bright side, though, this will enable me to run Win 7 in Virtualbox.

---

### Post by webmist09 on 2010-06-18
ok guys, I posted a query in Beginner section but since  you are all saying how great the dual boot is, can you tell me if , after you worked in Windows, you could still login on Lucid, because I can't?Windows 7 installed first, then Lucid.
Lucid was working well but I needed to go ti Windows, since which I can no longer get past the Lucid login - despite having set to log me in automatically - and it no longer recognizes my admin password.
help anyone?

---

### Post by Hman242 on 2010-06-18
I'm currently dual-booting Windows 7 64bit and Ubuntu 10.04 64bit with no trouble.

---

### Post by wilee-nilee on 2010-06-18
> **webmist09 said:**
> ok guys, I posted a query in Beginner section but since  you are all saying how great the dual boot is, can you tell me if , after you worked in Windows, you could still login on Lucid, because I can't?Windows 7 installed first, then Lucid.
Lucid was working well but I needed to go ti Windows, since which I can no longer get past the Lucid login - despite having set to log me in automatically - and it no longer recognizes my admin password.
help anyone?

To start with since you have a boot problem, start your own thread and post the script in my sig, with the code tags. This is standard procedure to start a personal thread.;) Hopefully in the process of looking at the boot we can get to the password.

I have had no problems with either problems that you describe. It might be helpful to also mention your experience with Ubuntu, in how much.

---

### Post by webmist09 on 2010-06-28
Thanks Wilee-nilee, for your reply. 
I am a beginner in forums, really, so fi**rst question is, how to start a new thread**? must be blind as cannot find it in the forums.

booted into live Lucid cd, (am in it now) and got the info you requested, so soon as I know how to post a new thread, will do so - don't know heaps about Ubuntu, which is why I originally posted in the Absolute Beginners forum - but am learning.  Have dabbled for a few years with various versions but this is the first time I have decided to be serious.

Thanks

---

### Post by wilee-nilee on 2010-06-28
> **webmist09 said:**
> Thanks Wilee-nilee, for your reply. 
I am a beginner in forums, really, so fi**rst question is, how to start a new thread**? must be blind as cannot find it in the forums.

booted into live Lucid cd, (am in it now) and got the info you requested, so soon as I know how to post a new thread, will do so - don't know heaps about Ubuntu, which is why I originally posted in the Absolute Beginners forum - but am learning.  Have dabbled for a few years with various versions but this is the first time I have decided to be serious.

Thanks

Go [here](http://ubuntuforums.org/forumdisplay.php?f=326)
Click this button mid top of page left and start your thread.
[ATTACH]161855[/ATTACH]

---

### Post by adrianlee44 on 2010-06-28
It worked completely fine in the beginning. Lucid and Win 7 were both running very smoothly.

But for some reason after I installed and played around with the VGA drivers on lucid, Windows 7 started to act weird. I was able to boot into Win 7 but it wasn't able to generate any visual effects. The Start Menu doesn't appear and all the characters/letters aren't even shown in windows/dialogs.

Anyone experience this issue?

---

### Post by wilee-nilee on 2010-06-28
> **adrianlee44 said:**
> It worked completely fine in the beginning. Lucid and Win 7 were both running very smoothly.

But for some reason after I installed and played around with the VGA drivers on lucid, Windows 7 started to act weird. I was able to boot into Win 7 but it wasn't able to generate any visual effects. The Start Menu doesn't appear and all the characters/letters aren't even shown in windows/dialogs.

Anyone experience this issue?

Lucid can only effect W7 in the boot, it makes no sense they are two different OS. If you are using a wubi install though Ubuntu is a file in W7 so you could have some corruption, but with just driver stuff this seems unlikely.

---

