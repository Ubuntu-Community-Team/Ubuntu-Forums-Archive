---
title: "I need help with VirtualBox OSE"
date: 2010-11-12
forum: Wine
---

### Post by TheShaggz09 on 2010-11-12
I have NO shame in admitting that I have no idea what I'm doing...all I know is I want to play MW2 online, and all I have is Ubuntu Ultimate 2.8. My step-dad told me about VirtualBoxOSE, but I don't know the first thing about how to use it. Is there anyone out there patient enough to step me through it so I can play the game I spent 60 bucks on last year? Thanks in advance.

---

### Post by Spice Weasel on 2010-11-12
Virtualbox OSE won't work with a game like Modern Warfare 2.

You should try WINE, which can be installed from the software centre.

See this link - [http://appdb.winehq.org/objectManager.php?sClass=version&iId=18348](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18348)

The winetricks they are talking about can be found here - [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by TheShaggz09 on 2010-11-12
I've tried Wine, PlayOnLinux, and Crossover Games. I followed TheLinuxWizKid's step by step on how to play, and none of these worked. They all pretty much say the same thing...IWNET_INVALIDVERSION  Even though I am using a purchased copy of the game. I've been working on this problem for 3 days now (2 without sleep). I'm obviously doing something wrong, I just can't tell what. I can get to the menu screen of MP and SP, but that's when I get either the above error, or it says I'm not connected to Steam, even though I am.

---

### Post by Sum Guy on 2010-11-12
Depending on your computer, it *might* work to use VirtualBox, but I don't know how well the graphics will function. To try it out, first create a new virtual machine by clicking New. Give it a name, pick the operating system you are going to use (Win7?), and click Next. Choose a memory size sufficient for the OS and any games/software you want to use, and click Next. Create a new virtual hard disk, making it large enough to contain the OS, your game, and some extra (it will only take up as much space as is filled if you use dynamically expanding storage, plus a bit for management). Click Finish. Next, right click the machine in the menu, and click Settings. Go to the Storage tab, click the disk in the Storage tree, and set it to either an image for the OS installer or your physical DVD drive if you have a physical disk for it. Now go to the Network tab, tick the box Enable Network Adapter, and attach the adapter to NAT (other options may also work, but this works for me). This option attaches the VM to the Internet through the host's network adapter. Now boot your VM, with your OS installer in your DVD drive if you're not using an image, and install the OS. Finally, switch the VM to your physical disk drive in settings, if you used an image, (you may have to turn off the machine), insert the game disk, install it in the VM, and see if it works.

Having another look at WINE may also work, make sure you look at the page in the database (linked by the other poster above) and check if there are any settings you missed that you need to change to get it working.

---

### Post by cwwilson721 on 2010-11-13
Or you might want to try VMWare Player, which actually has a 'working' 3d 'videocard'. It's slow, but you never know.

---

