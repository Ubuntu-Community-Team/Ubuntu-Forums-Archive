---
title: "HowTo: DWL-G132 in Gutsy"
date: 2007-10-20
forum: Tutorials
---

### Post by Onay on 2007-10-20
This is just a little howto I'm writing for people that have this specific usb wireless card and want to get it working in the Gutsy Gibbon release. This involves getting the ndiswrapper source and compiling it, so a few extra steps will be needed.

Things you need before you start...
[LIST=1]
[*]Gutsy Gibbon Live CD
[*]Computer with working internet (doesn't need to be the one you're installing this on)
[/LIST]

[SIZE="5"]Compile Ndiswrapper[/SIZE]
1. On the computer you have with the internet, download the ndiswrapper-1.47 source (I found that 1.48 causes lock-ups in Gutsy). Link below
[http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.47.tar.gz&980135](http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.47.tar.gz&980135)
Store that on an external usb drive and transfer to the dwl-g132 computer's **Desktop**

2. Insert the Gutsy CD into the dwl-g132 computer.

3. Open up Terminal and execute the following to get compiling tools for the source
```
sudo apt-get install build-essential
```
4. Change directory to the desktop, untar ndiswrapper, and change to the ndiswrapper directory
```
cd ~/Desktop
tar zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
```
5. Run the following commands to install ndiswrapper
```
make uninstall
make
sudo make install
```
[SIZE="5"]
Install the drivers
[/SIZE]
6. Download the following drivers on the internet computer from this link
[ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlg132_drivers_121.zip](ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlg132_drivers_121.zip)

7. Transfer these to the **desktop** of the dwl-g132 computer and unzip them there.

8. Go into the extracted directory and find the "Drivers" directory. Copy this to your desktop. You can delete the other folder if you wish, but keep the "Drivers" directory on your desktop.

9. Install the drivers by executing the following commands
```
cd ~/Desktop/Drivers
sudo ndiswrapper -i athfmwdl.inf
sudo ndiswrapper -i NetA5AGU.inf
sudo depmod -a
sudo modprobe ndiswrapper
```
10. Your little lights on the adapter should be blinking and you can now select your wireless connection in the network manager on your toolbar.

11. If everything worked, save your wlan alias...
```
sudo ndiswrapper -m
```
12. Now make it so that the ndiswrapper module is loaded with the kernel on startup...
```
sudo gedit /etc/modules
```
Add the line "ndiswrapper" (no quotes) at the end of the text file and save it.

That should be it. Let me know if I left out something

---

### Post by jacrider on 2008-02-03
Many thanks!!

I was struggling with this USB adapter.

It turns out the version of ndiswrapper made all the difference.

---

### Post by Dragothien on 2008-04-24
Hail and well met!

I am almost a complete linux noob here. At my work I've had some experience with ubuntu 7.10 and I know how to use the most basic of commands.  One of my goals has always been to learn linux, and now that I've built myself a brand new gaming computer, I have a 'non vital' spare that I can mess with all I want and use for work and school. I've always wanted to have a linux computer to really dive into the operating system, so here I am.


To get to the point. Just a few days ago I installed 7.10 and found that my usb wireless adapter (DWL G132) did not work with 7.10 out of the box. I found your awesome looking post here and tried to follow your directions. Low and behold I couldn't get it to work. I theorize this is because I was messing things up from the get go - I noticed that whenever I tried to do:

> apt-get install build-essential

It would start to do something but then ask me to insert my linux cd..even though it was already in the drive. So I ignored it and moved on and never got it to work. As I said, my theory is that this is the root of the problem.


Well moving on, as timing would have it, Ubuntu 8.04 stable was just realesed and I decided that as I'm trying to get into linux anyways I'd dive in to the newest possible stable, and I've installed the heron.

In an attempt to follow the same instructions with hope that nothing would really be any different, I very quickly found that running the apt-get install build-essential line did absolutely nothing other than to tell me that it couldn't find that package.


Soooo, I've now registered with the forum and start my first round of questions with:


Can anyone please help me get this wireless usb adapter working on Ubuntu 8.04?  Kinda sucks to not have internet when your trying to learn an operating system :D  ...Or in general..

---

### Post by Dragothien on 2008-04-25
Got it working :D

Basically the instructions are mostly the same. A couple differences I encountered though:

1) apt-get install build-essential  : Works great IF you tell linux to look in the right repositories as oppose to assuming it knows as much.

2)XXx sudo ndiswrapper -i athfmwdl.inf xXX 
      sudo ndiswrapper -i NetA5AGU.inf

Only the NetA5AGU.inf file is required. The ath--.inf file didn't exist, but didn't prove to be necessary either. 

3)I had some problem with the network accepting my key and making the connection, but after using :

>  /etc/init.d networking restart 

a few times over, all was well.

4)Network manager is decidedly misleading - But that doesn't really matter, all the power is in the command line anyways.

Just thought I'd throw up my conclusions.

---

### Post by putrid on 2008-05-27
**Dragothien**:
I did everything you said [SIZE="1"](a thousand times)[/SIZE], and the driver was installed and the [COLOR="DarkRed"]D-Link DWL-g132[/COLOR] is almost working. _[COLOR="DarkRed"]I still cant connect to a WPA or WEP protected WLAN[/COLOR]_.. If I remove the encryption, it will connect without any problems at all. But i dont want my network to stay open. When i try to connect, it only stops up and "waiting for network key" a few mins before it gives up.

Ive been trying to solve this problem for 2 days now, and are just inches away from throwing the Dlink adapter in the fire. :(

Im running a fresh install of **Ubuntu 8.4**. Im quite new to Ubuntu but ive manage to install and use it pretty much on my Laptop.

Thanks

---

### Post by Onay on 2008-05-27
> **putrid said:**
> **Dragothien**:
I did everything you said [SIZE="1"](a thousand times)[/SIZE], and the driver was installed and the [COLOR="DarkRed"]D-Link DWL-g132[/COLOR] is almost working. _[COLOR="DarkRed"]I still cant connect to a WPA or WEP protected WLAN[/COLOR]_.. If I remove the encryption, it will connect without any problems at all. But i dont want my network to stay open. When i try to connect, it only stops up and "waiting for network key" a few mins before it gives up.

Ive been trying to solve this problem for 2 days now, and are just inches away from throwing the Dlink adapter in the fire. :(

Im running a fresh install of **Ubuntu 8.4**. Im quite new to Ubuntu but ive manage to install and use it pretty much on my Laptop.

Thanks

Completely uninstall ndiswrapper-1.47
```
sudo ndiswrapper -r athfmwdl
sudo ndiswrapper -r neta5agu
cd ~/Desktop/ndiswrapper-1.47
sudo make uninstall
```


[http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=voxel&filename=ndiswrapper-1.52.tar.gz&63112128](http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=voxel&filename=ndiswrapper-1.52.tar.gz&63112128)

Download ndiswrapper-1.52 and compile that one with the same commands as above, just change the version #

Also download my "drivers" package and extract that. There will be one driver inside it: AGUx86.inf . Use that one and only that one
```
sudo ndiswrapper -i AGUx86.inf
```

That was the only way I could get gutsy to work. Hope it helps

---

### Post by Lovok on 2008-07-13
Thanks for the tutorial! My dad and I are installing the G132 on his Dell. I might as well throw up our experience in case others want a more recent testimony using Hardy Heron 8.04.
To get apt-get install build-essential to work, we had to do 

sudo apt-cdrom add
sudo apt-get install build-essential

We then used the ndiswrapper-1.53 and followed the rest of the instructions. Like Dradothien, there was no athfmwdl.inf. 
We ctrl-alt-backspace'd, set the encryption to accept 128 or 64, and voilà :)

At one point, we also did apt-get ndiswrapper, but I am not sure if that helped or not..

btw, we did a full reboot, and it stopped working :/ haven't gotten it back since :(

---

### Post by glsenaz on 2010-03-31
After much hair-pulling trying to get the internal Broadcom 4306 (Dell 1350) to work again, I followed the howto listed here and used the NetA5AGU.inf driver for my unused D-Link DWL-G132 USB wireless. Came right up in my Ubuntu 9.04 (Jaunty Jackalope). Upgrade to 9.10 (or dare I dare move to 10.4?!?) soon to come! Thanks so much, Onay and company!

-*-Bill:popcorn:

---

### Post by Briarfox on 2010-06-05
> **Dragothien said:**
> Got it working :D

Basically the instructions are mostly the same. A couple differences I encountered though:

1) apt-get install build-essential  : Works great IF you tell linux to look in the right repositories as oppose to assuming it knows as much.

2)XXx sudo ndiswrapper -i athfmwdl.inf xXX 
      sudo ndiswrapper -i NetA5AGU.inf

Only the NetA5AGU.inf file is required. The ath--.inf file didn't exist, but didn't prove to be necessary either. 

3)I had some problem with the network accepting my key and making the connection, but after using :



a few times over, all was well.

4)Network manager is decidedly misleading - But that doesn't really matter, all the power is in the command line anyways.

Just thought I'd throw up my conclusions.






Dragothien,

I new to ubuntu. How do I refresh the network. I have the same problem  w/ dlink. Wants me to reenter my network key then freezes. I tried your  "Quote" -doesn't work - error no directory. Could you explain?

Thanks
Briarfox

---

### Post by Thedude13542 on 2012-08-12
Two years later I am attempting the same thing on 12.04.
Help.

I got it to work, and it did.
Then either I chose to install the other driver that i had forgotten to do, or I restarted the system, because all of a sudden It is back to step 1, and ndiswrapper doesnt work anymore either.:confused:

---

### Post by Thedude13542 on 2012-08-12
My issue may be i never did the whole build-essentials thing, but where exactly (and how) do I refer it to what it needs?

---

