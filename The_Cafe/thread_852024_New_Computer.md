---
title: "New Computer"
date: 2008-07-07
forum: The Cafe
---

### Post by Nitewolf121 on 2008-07-07
I've been looking around a little bit and I'm trying to figure out how to do the initial setup of my new pc I've just ordered.  :)

When I was a lot younger, maybe 10 years ago, I used to dabble in Linux cause I had a few good friends that swore by it and gave me great support on how to do things.  I've been out of the Linux area for a long time though.  Now I want to get back in with this new pc. 

List of parts I've ordered are as follows:

Asus Rampage Formula MB Intel X48 chipset
Intel Q9550
8GB OCZ Reaper 1066
Nvidia GTX 280 + Nvidia 8800GTX (Running 3 22" Monitors)
2 x Seagate 250GB HD's in Raid0

Those are the basics.  I have copies of Windows Vistax64 and 64 bit XP and 32 bit XP.  I HAVE to run Vista and xp in dual boot for work purposes.  But for personal choice I would like to go back to Linux.  Will I be able to triple boot and run Linux?  I was looking at EasyBCD?  I think that is what it is called, saw it in the Ubuntuguide for dual booting.  Will I be able to have support for my 3 monitors?  Will my RAID0 work?

And when I build this pc once the parts arrive this week, which is the best way to install these OS's.  I'm starting my pc from scratch and want to do it right the first time.  Whether it is to install Ubuntu or Windows first.  Since I'm starting from scratch I want the install with the least amount of issues as possible to make the triple boot work.  Oh and is there a 64bit version of Ubuntu, and if so, where could I find documentation on the differences compared to 32bit?

---

### Post by aeiah on 2008-07-07
i advise installing in the order of win xp, vista, ubuntu. this is basically just due to xp being the less likely to recognise any other OS on the system. vista should be able to recognise windows xp when installing it although you may want to read up and confirm this. ubuntu should be able to see both and insert them into the grub menu. i think chainloading may be needed for vista but this should be automatic nowadays.

you shouldnt have any problems with ubuntu 64bit. it used to be the case that various things wouldnt work but i think its all been ironed out now. you should be able to get everything working. there is still no 64bit flash and i think a few restricted codecs arent 64bit either, but you can run 32bit binaries where it is necessary.

nvidia will give you the strongest chance of getting a 3 monitor set up going right now, although i cant confirm that it'll work how you want. you may not be able to get them all on the same xserver (ie, you may be able to drag between the two screens that are on the same graphics card, but not to screen number 3)

---

### Post by Nitewolf121 on 2008-07-07
As for the talk about past problems with 64bit and some apps not being for 64bit.

Is there any real benefit of me going to 64bit.  I was looking at doing that since this is the first official 64bit home pc I've built.

---

### Post by OldTimeTech on 2008-07-07
According to most things I've read here on the forums and in my tech journals...XP should be 32 bit (the why is because of drivers, applications etc), Vista 64 bit has more drivers, but not sure about applications and definitely 64 bit on HH 8.04...because Ubuntu is actually the only one that runs 64 bit without any type of glitches.

Secondly, if you type into search 3 OS setup or something like that you are likely to find a number of postings telling you how, why and why not....I have read them in the past but cannot tell you in what area of the forums....also, I've quit using anything but Ubuntu on most of the machines in my house.

Thirdly, keep in touch with the forums as you build this pc...because we're always glad to help ;)

---

### Post by wrtpeeps on 2008-07-07
> **OldTimeTech said:**
> According to most things I've read here on the forums and in my tech journals...XP should be 32 bit (the why is because of drivers, applications etc), Vista 64 bit has more drivers, but not sure about applications and definitely 64 bit on HH 8.04...[B]because Ubuntu is actually the only one that runs 64 bit without any type of glitches.
[/B]
Secondly, if you type into search 3 OS setup or something like that you are likely to find a number of postings telling you how, why and why not....I have read them in the past but cannot tell you in what area of the forums....also, I've quit using anything but Ubuntu on most of the machines in my house.

Thirdly, keep in touch with the forums as you build this pc...because we're always glad to help ;)

hmmmmmm :confused::confused:

---

### Post by mips on 2008-07-07
> **Nitewolf121 said:**
> I HAVE to run Vista and xp in dual boot for work purposes.  But for personal choice I would like to go back to Linux.

What does your work require you to do that you have to dualboot XP & Vista? Are you a developer or something? Have you considered installing XP & Vista in a virtual machine? If you don't need hardware accelrated 3D in XP or Vista then i can't see why you should not use a VM.

---

### Post by Nitewolf121 on 2008-07-07
> **mips said:**
> What does your work require you to do that you have to dualboot XP & Vista? Are you a developer or something? Have you considered installing XP & Vista in a virtual machine? If you don't need hardware accelrated 3D in XP or Vista then i can't see why you should not use a VM.

I'll be running XP for work programs and database editing.  Construction database for our offices estimating programs.  Vista I'm running because I've been asked to keep an eye on it and how it is developing and working with the programs we use at work.  So if the time comes where they need to make a switch they will be comfortable with it.  Not sure, I just do what I'm asked to do since they pay for my computer at home.  :)

---

### Post by mips on 2008-07-07
> **Nitewolf121 said:**
> I'll be running XP for work programs and database editing.  Construction database for our offices estimating programs.  Vista I'm running because I've been asked to keep an eye on it and how it is developing and working with the programs we use at work.  So if the time comes where they need to make a switch they will be comfortable with it.  Not sure, I just do what I'm asked to do since they pay for my computer at home.  :)

Sounds like you are a good candidate for VM.

---

### Post by Nitewolf121 on 2008-07-07
Now you are venturing off into an area I'm not familiar with.  I'm comfortable multi-booting if it will work.  But virtual machines I've never messed with.  Off to google I go.

---

### Post by mips on 2008-07-07
> **Nitewolf121 said:**
> Now you are venturing off into an area I'm not familiar with.  I'm comfortable multi-booting if it will work.  But virtual machines I've never messed with.  Off to google I go.

Look at VirtualBox & VMWare. Easy to set up and get going. Hell, just download virtualbox or vmware for windows and try it out for yourself.

Best way to make use of those four cores of your cpu!!! Geez, you can basically have 1core per WinOS all on a linux desktop.

---

### Post by Nitewolf121 on 2008-07-07
I looked up VirtualBox and VMWare.  This idea looks intriguing for me.  Especially with what you mentioned about how to utilize my processor with it.  

This might be a good fix for me using XP, XP is only in use at home for me to deal with work items that currently only run on XP for us.  Vista I might set up though to dual-boot with Ubuntu cause of my slight gaming addiction that no matter how old I get I still like to play.  

I could dual boot Vista 64 and Ubuntu 64.  Then use your VM suggestion for using XP since nothing I use is graphic intensive in that.  At least this way I could run Ubuntu as my main OS, boot out to Vista when I want to game.  But besides gaming, I could finally, maybe stick mainly in Linux, which was my goal when I was younger and using it.

---

### Post by mips on 2008-07-07
Do what works for you at the end of the day. Dual boot + VM in linux will work. You could even create a Vista VM for when you just need the OS but don't need to play games.

Keep in mind that at this stage only vmware has support for 64bit guest operating systems if I'm not mistaken, just incse you want to install vista64 in in a VM.

---

### Post by Nitewolf121 on 2008-07-07
Thanks for the heads up on the 64 bit, cause that is currently what I'm using in Windows.

---

