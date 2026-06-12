---
title: "ubuntu diplay on oracle virtualbox"
date: 2012-01-24
forum: Virtualisation
---

### Post by rigidigital on 2012-01-24
hello, i am using ubuntu 11.10 on latest virtual box.I am having trouble with getting full screen display. it was automatically full screen with suse
so i dont know why ubuntu is not. when i go to display there are only two options 1) 1024 X 768   or 2) 800 X 600.    The 800 X 600 option makes the display even smaller.[IMG]http://i1095.photobucket.com/albums/i464/Micheal_Lynch/tue.png

---

### Post by Cheesemill on 2012-01-24
Have you installed the VirtualBox Guest Additions?

---

### Post by rigidigital on 2012-01-24
i just downloaded virtualbox 4.1.6 a few days ago. not sure what 'guest additions' you refer to are or what they do, so i guess 'no' i havent.

still suse 12 is working full screen fine in it full screen, just did it when i installed suse , no fiddling around. not that i mind fiddling if i know what to do.

as you probably guessed when i expand the virtualbox to full screen all that happens is lots of white space around the ubuntu desktop. it stays the same size.

---

### Post by Cheesemill on 2012-01-24
When the VM is running, on the VirtualBox menu click Devices > Install Guest Additions.

---

### Post by rigidigital on 2012-01-24
thx am just doing that now. ,,,,,,,,,ok greaty works beaut, much better room to manuver in gimp and all else. One thing perhaps u can help me with, im was playing with the suse virtualbox settings now "MACHINE  VIEW  DEVICES  HELP" toolbar has gone and the display has degradedm i mean stretched. how can i get the toolbar back please .:P:P

forget it.........  i needed ctrl  + C

---

### Post by LadyeLynx on 2012-01-26
New to Ubuntu/Linux and to virtual box.  Still running xp pro.... 
Do not want to update to 7 - Thought I would try ubuntu, tried to instal it along side windows did not work. So installed it on virtual box.  It runs but is verrrry slooow, lags, and is non responsive. Is there some sort of plug in or tweak I am missing to get it to run better in virtual box? 
 
Running 4.1.8 VB- latest addition- and the 32 bit version of the KDR destop version 11. 

Also is there a plug in so I can view all my drives from the desktop?

---

### Post by rigidigital on 2012-01-26
First, thx Cheesemill, that little tip got all three guest OS's running full screen without using 'Scale" which wasn't much good. I was stuck in Scale mode on one guest and didnt know what happened to the VB toolbar for awhile.

@Ladyelynx, you might be better off starting a new thread 'VirtualBox Sluggish' or some new title stating your computer specs.  I am running 3 virtual machines at once with no lag , XP, openSUSE,Ubuntu. I do have 8 gig ram on host and 3+gig AMD quad core.  for my 2 cents ram could be your problem.

---

### Post by LadyeLynx on 2012-01-26
Thank You,
Ram might indeed be the problem... just checked it ... time to clean up the computer :)

---

### Post by ixtok on 2012-01-27
I am using linux mint 12 in my HP Mini 110 netbook with 2gb ram. In run windows xp in my virtualbox with around 500mb allocated to the system. XP seems to run normally in this mode. What is very slugish in my virtual box is Ubuntu 11.10. Even Windows 7 is not too bad except I havn't figured out a good video configuration yet.

---

### Post by SeijiSensei on 2012-01-27
A Win7 VM typically requires at least 1 GB of memory to run efficiently.  On this machine I have 4 GB of memory and have allocated 2 GB to the Win7 VM I use from time to time.  An Ubuntu VM can typically get by with somewhat less, but much below 768 MB things get tight, especially if you're running a hefty desktop environment like KDE.  If you're trying to run Ubuntu in a VM where memory is at a premium, try using [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") or [Xubuntu]("http://www.xubuntu.org/") instead.

It helps if you start the VM before launching any other programs on the host. Otherwise the OS will have to swap out current programs to make room for the VM when it starts up, and everything bogs down.

I can run the Ubuntu server edition in a 512 MB VM without any performance problems, but that version has no desktop environment, just a text-mode command-line.

---

### Post by AlvitrValkyrie on 2012-01-27
> **LadyeLynx said:**
> Thank You,
Ram might indeed be the problem... just checked it ... time to clean up the computer :)

Settingd > Display > Drag the Video Memory up and check the 3D Acceleration
Settings > System > Base Memory and drag the little thingy to however much RAM you want to allow. 1GB should be enough (1024MB is = 1GB)

---

### Post by nothingspecial on 2012-01-27
*Thread moved to **Virtualization**.*

---

### Post by Rebelli0us on 2012-01-27
I have Win7 in VM with default 512MB and it runs just fine.

Guest Additions can be tricky to install.
I've tested **many** distros in VM and most will run 1024x768 or 800x600 even with Guest Additions installed. With some of the KDE distros it's a complete mystery how to install Guest Additions, lots of BS error messages like "you can't do this, only root can" and screenfulls of techno-gibberish.

---

### Post by japzone on 2012-01-27
I'd reccomend having at least 2gb RAM and Dual-Core CPU on Host PC for effective running of a Guest OS. 1gb or Less RAM with a Dual-Core CPU will only be enough to run Small-Footprint OSs like MicroXP or Lubuntu. I would never recommend running on a Single core CPU unless it's close to or higher than 2.0GHz. If you don't meet these Specs you should look into Multi-Booting your PC or buying a more powerful one. For people just wanting to give Ubuntu a Trial Run on a PC use [**WUBI**](http://www.ubuntu.com/download/ubuntu/windows-installer) to make a Temporary Install of Ubuntu on your Machine with little effort.

---

