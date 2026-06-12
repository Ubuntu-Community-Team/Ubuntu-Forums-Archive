---
title: "First time linux user"
date: 2018-08-06
forum: Ubuntu, Linux and OS Chat
---

### Post by hohojohndo on 2018-08-06
Hey everyone! 

I must admit, this is my first time getting into Linux. Although I've known it existed for many years, I never really had the drive to learn it. I have a new laptop and I want a fresh start. I have been mucking around with Ubuntu in a virtual drive, just getting a feel for the basics, and have watched a few different videos online explaining different important points of the software and why it's a good place to start for someone looking to practice coding etc. 

I want to move to Ubuntu as my main OS, but have already had a few moments just installing from the USB boot where I think hmm, maybe I'm not ready. 

So what would ya'll do?

I'm of a mind to just dive in and learn along the way, but then there is the option of having a dual boot of windows AND Linux so that if I get really stuck at least I still have a functioning OS for daily tasks. 

Unfortunately I'm finding booting Ubuntu in virtualbox is taking far too much power for when I'm out and about..

Cheers

---

### Post by wildmanne39 on 2018-08-06
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by Quarkrad on 2018-08-07
Many people, myself included, when they were in your position decided to have their cake and eat it.  I.e. dual boot - I still do although I use ubuntu 99% of the time.  Running linux/ubuntu in virtualbox is OK for testing things out but not really as your main OS.  I would shrink your existing HD using the built-in windows app (this page will show you how [http://www.pagestart.com/win7win10tpdb10121403.html](http://www.pagestart.com/win7win10tpdb10121403.html)) and when done install ubuntu in dual boot mode.  This way you will have the full power of your laptop driving either windows or ubuntu.  There are many pages devoted to how to install ubuntu in dual boot mode including pages on this forum.  Ask questions and people will come to help you.  It is very easy to do BUT there are a few important steps you must perform so not to harm your windows environment.

---

### Post by TheFu on 2018-08-07
What you should do depends on where you need/want to be in 5 yrs. Most Unix admins don't code much.  Most coders are next to clueless about Unix administration. DBAs are a different group too.

So, what do you want to do in 5 yrs?

I'd push you do use virtualization.  Normally, people seeing poor performance have old, slow, computers AND didn't tune the hypervisor settings.  But there are some things you shouldn't expect to work well in any hypervisor without non-trivial effort.  GUI stuff - games, video editing, CAD just don't work well inside a normal, easy, virtual machine.  I'd guess that someone who learns fast and can afford the correct hardware could be ready to solve that issue using something called video PCI passthru after about a year of full-time Linux use.  It isn't something a beginner will get working. It just isn't. I don't know of any laptops that support PCI passthru.

As will all things, the more you use it, the better you become.  Nothing replaces using Linux 8+ hrs a day if you want to learn.

So, back to those questions:
a) where do you want to be in 5 yrs with your linux knowledge?
b) have you tuned virtualbox?
c) Are you willing to move to a more capable, faster, slightly harder, hypervisor?
d) What are the computer specs?  If they are low-end, somethings there isn't much that can be done. Running/posting ** inxi -Fxz** would be good.

I'm not a fan of dual-boot setups because there will be multiple OSes trying to manage the boot.  MSFT commonly assumes they are the only OS on a machine and breaks booting 1-2 times a year.  Whereas if I put Windows into a virtual machine, it can't do any harm to my real OS or disks. I control the virtual hardware provided to Windows.

---

### Post by ra7411 on 2018-08-07
I started w/ Ubuntu about 2 years ago. The only snag has been for tax software - for that I have to use Windows.

---

### Post by Carpentr on 2018-08-07
You could do a full install of Ubuntu and then install Windows in a VM if you have any critical applications (license & sufficient PC resources required). That's what I do. The only caveat to that would be if you play windows-only video games. Then, I'd say dual boot.

---

### Post by coffeefiend on 2018-08-09
I was in a similar boat. I started off test driving many different flavors as bootable USBs. Found a few I liked, narrowed down further by using VMs. Then, after using Ubuntu, and stalking this forum as a guest for a couple of weeks and seeing how helpful the smart guys and gals are here, I bought a bottom of the line HP Pavilion and loaded Ubuntu as dual boot with Win10. Then one day I decided that since the laptop was so cheap, just under $300, and since I had another laptop with Win10, I would do a full load of Ubuntu on el cheapo. Now I use it more often than my Win10 laptop.

---

### Post by recycleyourself on 2018-08-09
I agree with others that dual boot might be the way to go if you're unsure.  But the easiest way is just to do a clean install, 100% Ubuntu.  Since I've left Windows I have no regrets, and actually it's made me think about how much I was paying for stuff.  Why pay when it's free and better?  

The only anti-linux caveats I'd include are with MS office.  If you must use Word, Excel, PowerPoint at work you can convert from Libre Office or Open office.  However sometimes there are some formatting issues...especially when converting to Powerpoint.  I've had some presentations ready to go I made on Linux only to realize when I used the MS windows computer at work the formatting was completely screwed up.  That can be a pain.  My kids also complain Libre isn't as intuitive as MS Office, so if you have kids there might be some whinning.  

So the short of it is, there might be a few negatives, hopefully none to big to prevent you converting, but there are a whole lot of pros.  Go for it!

---

### Post by jcastaneda2 on 2018-08-19
> **recycleyourself said:**
> and actually it's made me think about how much I was paying for stuff

I would agree with that. I have a W10 desktop and an Ubuntu laptop. I tend to use the laptop a bit more now anyway.

---

### Post by justen_m on 2018-08-26
I dual boot. Win10 and Ubuntu. Sue me.

---

### Post by caberry9 on 2018-08-29
I just went linux all the way. The hard way from Mandriva (yuck), Debian (ooook), Gentoo (OMG that took a big piece of my life) and the settled with Ubuntu. In 99% it's idiot-proof ;-)
You just install it and that's it. There is really no challenge/fun in that ;-)

---

### Post by friedchips2 on 2018-09-12
First off welcome. Secondly. No on can tell you what is right for your needs/abilities. I still have a windows install I can boot to. I have been using linux in many forms for 16+ years! I love it and couldn't go without but some things just work easier in windows and for somethings it's the only way to get there. It is what it is. Look at my screenshot. You think I'd ever go back to windows for may main usage?? NOPE!
[ATTACH=CONFIG]281055[/ATTACH]

---

