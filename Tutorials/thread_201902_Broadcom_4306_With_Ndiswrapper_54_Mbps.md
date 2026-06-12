---
title: "Broadcom 4306 With Ndiswrapper 54 Mbps"
date: 2006-06-22
forum: Tutorials
---

### Post by ubunturules on 2006-06-22
This is the easiest way to get your Broadcom 4306 wireless card working in the shortest amount of time.  I wouldn't use the firmware cutter because it only allows you to run at 11 Mbps with it.  With ndiswrapper you will get 54 Mbps if your router will allow it.

The Drivers listed below work for most broadcom 4306 wireless cards but not all of them.  If you use the drivers below and your card doesn't show up under network then you should try using the driver that came with your card or go to the manufacturer's website.

Get the 32 bit drivers from [here]("http://rapidshare.com/files/177121041/32_bit_bcmwl5.zip") or the website of the manufacturer of your wireless card.

Get the 64 bit drivers from [here]("http://rapidshare.com/files/177585227/64-bit_Broadcom_54g_Drivers.zip").  I've heard that you don't change the name .inf file to bcmwl5.inf just keep it the way it is.

Do everything in the order as it is listed.

run the following command to make sure you have a broadcom chipset wireless card.
**1.**```
lspci | grep Broadcom\ Corporation
```

**2.**```
sudo rmmod bcm43xx
```
If you get an error message saying ERROR: Module bcm43xx does not exist in /proc/modules it is ok and you can move on to the next step.

**3.**```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

**5.** You will need the Ubuntu CD to get these packages.
```
sudo apt-get install build-essential
```

**6.**
```
uname -r
```

Insert the output of the uname -r command into the following 2 commands where the numbers are at

**7.**
```
sudo apt-get install linux-headers-2.6.22-14-generic
```

Insert the output of the uname -r command into the following 2 commands where the numbers are at

**8.**
```
sudo ln -s /usr/src/linux-2.6.22-14-generic /lib/modules/2.6.22-14-generic/build
```

Download ndiswrapper
**9.**
```
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.56.tar.gz
```

Make a folder for ndiswrapper and place it in there
**10.**
```
mkdir ~/ndiswrapper
mv ndiswrapper-1.56.tar.gz ~/ndiswrapper
```

Install ndiswrapper
**11.**
```
cd ~/ndiswrapper
sudo tar -xvzf ndiswrapper-1.56.tar.gz
cd ~/ndiswrapper/ndiswrapper-1.56
make distclean
sudo make
sudo make install
```

**12** If you are running Dapper or Edgy run this command.  Some people say that compiling it works for them and some people say getting it with synaptic so I thought if you just installed both then you'll have some form of ndiswrapper working.  If you don't have a working internet connection then you can get these packages off of the Ubuntu CD.
```
sudo apt-get install ndiswrapper-utils-1.8
```

If you are running Feisty or any version higher than Feisty run this command.  You might need the Ubuntu CD to get these packages.
```
sudo apt-get install ndiswrapper-utils-1.9
```

If you can't get ndiswrapper from any of the sources above you can get it from the Ubuntu CD.

**13.**```
sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf
``` 
If you are using the 64 bit drivers run this command ```
sudo ndiswrapper -i ~/folder where driver is/netbc564.inf
```
Make sure the .sys file is in there also, without it, it won't work


**14.**```
ndiswrapper -l
```
To make sure the hardware is present


**15.**```
sudo ndiswrapper -m
```
To load ndiswrapper automatically when the wlan0 interface is used


**16.**```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

**16. B**
```
sudo gedit /etc/init.d/wirelessfix.sh
```
Paste this into that file
> #!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
Close and save that file
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
```
```
sudo update-rc.d wirelessfix.sh defaults
```

**17.**```
sudo iwconfig wlan0
```

If you are running Gutsy or any version higher than Gutsy restart your computer and skip to step 26.
**Enable the Connection**

**18.** Go to System -> Administration -> Networking

**19.** If you don't see any wlan0 connections in Networking then you should restart your computer.

**20.** Go to your eth0 connection and disable the connection.

**21.** Now go to your wlan0 connection and enable it.

**Network Manager**

If you need WPA or WEP encryption do the following:

Note: If you are running Feisty or any version higher than Feisty you can skip steps 22 through 25.

**22.**```
sudo apt-get install network-manager-gnome
```

**23.**```
sudo gedit /etc/network/interfaces
```

**24.** Comment out anything in there at the bottom that has to do with your wireless essid.  You need to also comment out anything that says eth1, eth2, or atho.  When I say comment out that means put a # in from of it. You can leave all of the eth0, wlan0, lo, inet, and auto stuff.

**25.**```
nm-applet
```

**26.** Now click on the applet that is in the top right corner and you should see all of the available connections.  Click on yours and set it up.

**SOLUIONS TO PROBLEMS**

**Problem 1**

If wlan0 isn't showing up under your network connections and you're getting invalid driver errors when you run ndiswrapper -l then:
```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```
Look for the entry for your bcm43xx device and change the NAME at the end to wlan0, example below.

# PCI device 0x14e4:0x4320 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:03:c9:70:7b:a9", NAME="wlan0"

Thanks fireant for the fix for problem 1

**Problem 2**
Totoro found a fix for the eth1 problem.  Thank You Totoro!
add ndiswrapper to /etc/modules
change eth1 -> wlan0 in the files below:
```
sudo gedit /etc/modeprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab
```

**Problem 3**
Shaton found a fix for the FATAL: Error inserting ndiswrapper problem.  Thank You Shaton!
If you get an error saying 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument 

then try this.
```
sudo apt-get install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```

If you are using Feisty then you will need to put a 9 where the 8 is.

**Problem 4**
If you get a lot of error messages talking about the icon then run this command:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

**Problem 5**
If you have to run modprobe ndiswrapper every time you reboot your computer run this command.

```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

Thanks Phifer for the fix for problem 5

I hope this helps a lot of people!

---

### Post by ubunturules on 2006-06-23
did this HOWTO help anyone?

---

### Post by thinkinvisible on 2006-06-23
Worked for me as far as activation.  However, upon reboot, none of my network interfaces are recognized in network manager.  I'm sure it was something on my end though.  Nice guide!  Thanks for posting it.

EDIT:  Upon a second reboot, wireless is up and running.

---

### Post by ubunturules on 2006-06-23
It's good to know I helped someone because I remember how it was back in the day when I couldn't get my wireless card working and I was tired of reading so many HOWTO's that didn't work.

---

### Post by xXx 0wn3d xXx on 2006-06-23
I don't think ndiswrapper works with network-manager but that it just from what I know. And as for deleting your interfaces file, how about commenting it out in case you need it/things don't work out. Nice tutorial by the way.

---

### Post by ubunturules on 2006-06-23
ndiswrapper does work with network-manager.

---

### Post by xXx 0wn3d xXx on 2006-06-23
[QUOTE=ubunturules]ndiswrapper does work with network-manager.[/QUOTE]
Ok, like I said I wasn't sure. It didn't work with my Broadcom card and ndiswrapper.

---

### Post by ubunturules on 2006-06-23
that's weird.  Did you follow this guide?  Are you sure its a broadcom card?  It does work with ndiswrapper though.

---

### Post by xXx 0wn3d xXx on 2006-06-23
[QUOTE=ubunturules]that's weird.  Did you follow this guide?  Are you sure its a broadcom card?  It does work with ndiswrapper though.[/QUOTE]
Well I'm using the bcm43xx kernel (2.6.17ck1) module on Archlinux but I tried to get it (Broadcom 4318 + ndiswrapper) to work a long time ago. About 2 months to be exact and it didn't work at all but everything it fine now.

---

### Post by ubunturules on 2006-06-23
awesome.  good to hear.

---

### Post by WADemosthenes on 2006-06-29
Didn't show up in network manager, gone an error messege on "ndiswrapper -m" it was:

WARNING: /etc/modprobe/d/blacklist line 1: ignoring bad line starting with 'bcm43xx'

That's all that I can think of.

---

### Post by elemental666 on 2006-06-30
Just got this working with a Linksys WPC54GS (bcm4306) under Xubuntu 6.06 (Fresh install).  I used the driver from linksys and renamed the inf file to match the sys file.  Went without a hitch, posting wirelessly now.

---

### Post by ubunturules on 2006-07-01
WADemosthenes: It's not "bcm43xx".  It's "blacklist bcm43xx".

---

### Post by ericesque on 2006-07-01
any time I try to connect using nm, it just sits there "connecting to *edited essid*"  then after a while it fails and I end up with no connection.  Ideas?

---

### Post by ubunturules on 2006-07-01
Make sure that you don't have anything in you /etc/network/interfaces that deals with your wireless essid.

---

### Post by ericesque on 2006-07-01
yeah that's in the guide.  I don't.

---

### Post by Quicksilver_Johny on 2006-07-02
I followed the instructions, and got it to work, but then booted in XP (to install Google Browser Sync), and when I booted Xubuntu the PCMCIA... thing, didn't load on startup. The Card came on, and was listed in ifconfig, but I couldn't connect to the network. I ran through the instructions again, still same problem. -/

Also, For some reason Ndiswrapper uses eth1 and not wlan0. /etc/modprobe.d/ndiswrapper automatically says wlan0 though, and, when kept that way, It doesn't show up in System>Administration>Networking, but when edited to eth1, it does. I'm not sure if this matters.

---

### Post by ericesque on 2006-07-02
heh.  I think I overlooked the fact that this is a 4306 tut, not broadcom in general.  I have the infamous 4318 so I suppose I shouldn't expect this to work regardless. oops.

---

### Post by benmoreassynt on 2006-07-05
This is an excellent and simple howto that will work for many of the millions of Lynksys WRT54G users (although you need to check you have a Broadcom 4306 version of the card, as some have Texas Instruments chipsets, and are quite different. See other posts and WIKIs about how to find out if you WRT54G version. if all else fails Linksys support will be able to tell you which version you have). I know other cards and laptops use the BCM 4306 chipset, but it is handy for others to know this specifically works with the Linksys card.

I'm on my third time setting up a Ubuntu laptop with a linksys card, and it is always a pain, but these instructions are the best and simplest, and easiest to understand of the lot - highly recommended.

Follow the instructions precisely, including using the suggested URL to get the driver and inf file - you do NOT need to go to the linksys website to get the driver (although that will work too, but [THIS IS IMPORTANT, AND SELDOM MENTIONED] you then need to rename the .inf file that you will find in the download to bcmwl5.inf. I THINK the file you need to rename is called lsbcmnds.inf, but don't quote me on that. That is what I did first time around 9 months ago)

If the 1st instruction (which unloads the native driver) in the list returns a 'not found' error of some sort, don't worry but complete the rest of the instructions and then restart your computer for the changes to take effect - the native driver will be prevented from loading again.

Final note - I have had no success with using the 'native' bcmxx driver that comes with Ubuntu combined with fwcutter. The ndiswrapper route for WRT54G seems much easier, and works perfectly well, if not better (it may allow faster connections as far as I can see). There's no advantage in using the included driver, as the abscence of firmware means it is still a pain to set up. Why bother with this apparently more complex route?

---

### Post by bunnicula on 2006-07-05
I followed the instructions in the first post and when I run sudo ndiswrapper -l, it says that I have an invalid driver (I took the driver off of my Windows cd) and I get an error if I try to move on to the next step. Any ideas?

---

### Post by bunnicula on 2006-07-05
I downloaded some new drivers and they appear to have installed fine. I was also able to follow the rest of the instructions without any problems. Unfortunately, my wireless connection still isn't working. The Network Manager says that it is an active wlan0 connection, wireless networks are visible from the properties screen, and the Network Monitor says that the connection is idle. But the connection still isn't working...I've tried rebooting and re-entering my WEP password a couple of times, but it still isn't working. Now what?

---

### Post by ubunturules on 2006-07-05
I have no idea sorry.  I've never heard of this problem before.

---

### Post by MarinaraOfDeath on 2006-07-05
[QUOTE=bunnicula]I downloaded some new drivers and they appear to have installed fine. I was also able to follow the rest of the instructions without any problems. Unfortunately, my wireless connection still isn't working. The Network Manager says that it is an active wlan0 connection, wireless networks are visible from the properties screen, and the Network Monitor says that the connection is idle. But the connection still isn't working...I've tried rebooting and re-entering my WEP password a couple of times, but it still isn't working. Now what?[/QUOTE]

Unfortunately you cannot use your specific windows drivers, you have to use the drivers that match both ndiswrapper and your family of wireless adapter. You may thus lose some vedor specific features but should be able to use the basic connectivity just fine. I discovered this during my epic struggle to get wireless working in Fedora 4.

---

### Post by ubunturules on 2006-07-05
Get the drivers from home.nc.rr.com/thehinnants/drivers.

---

### Post by bunnicula on 2006-07-06
I used the drivers from here: home.nc.rr.com/thehinnants/stuff/drivers

It says the drivers are active but my wireless still doesn't work...

---

### Post by noseeme on 2006-07-06
Yessss! This worked perfectly!!! Thank you!

This was the only post I found that adressed what the real problem was with my wireless setup.
I didn't realize that the whole reason the wireless wouldn't work was because Ubuntu's native broadcom wireless driver was conflicting with ndiswrapper.
The wireless device I am using is a Linksys WMP54G (version 2), which obviously uses a broadcom chip.

Thanks again for helping, I wish I had remembered that ubuntu already had a driver that I needed to blacklist!

---

### Post by bunnicula on 2006-07-06
I just realised that I didn't do this portion of the tutorial:

> 
If you need WPA or WEP encryption do the following:

Code:

sudo apt-get install network-manager-gnome


Code:

nm-applet


if you get a lot of error messages talking about the icon then run this command:

Code:

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/


Code:

sudo gedit /etc/network/interfaces


Comment out anything in there at the bottom that has to do with your wireless essid. When I say comment out that means but a # in from of it. You can leave all of the lo, inet, and auto stuff.

Now click on the applet that came up in the top right corner and you should see all of the available connections. Click on yours and set it up.


I had originally tried to do the part about the network manager, but I got some error messages. I then realised that there was already a Network Manager applet (or at least I assume that is what the computer icon in the right-hand corner is)  and so I figured that I didn't need to do that part.

I just tried to do run the last line of code, but that didn't fix anything...is there something that I am missing (or doing horribly wrong)? I can see the wireless networks nearby (including my own), so I know that the card is working...could it have something to do with the encryption?

---

### Post by ubunturules on 2006-07-06
make sure you ran:.
```
sudo gedit /etc/network/interfaces
```
if you did that, you should have no problems.  You don't have to run this command if can already see your interfaces in the nm-applet.

---

### Post by benmoreassynt on 2006-07-06
Sorry - irrelevant post. Cannot how to see to delete it.

---

### Post by foxy123 on 2006-07-07
it worked very well, so I have now 54g instead of 11g with a native driver. However, I have to do 
```
sudo modprobe ndiswrapper
```

every time after th eboot to bring the card up. 
```
sudo ndiswrapper -m
```
does not help. Any suggestions?

Please note that I have had ndiswrapper before and then I switched to the native Linux driver provided in the kernel.

---

### Post by ubunturules on 2006-07-07
Make sure you did
```
sudo rmmod bcm43xx
```

Do you have a file called /etc/modprobe.d/bcm43xx.
If you do, delete it.

then try
```
sudo ndiswrapper -m
```
```
sudo modprobe ndiswrapper
```

---

### Post by foxy123 on 2006-07-07
> **ubunturules said:**
> Make sure you did
```
sudo rmmod bcm43xx
```

Do you have a file called /etc/modprobe.d/bcm43xx.
If you do, delete it.

then try
```
sudo ndiswrapper -m
```
```
sudo modprobe ndiswrapper
```

no I do not have /etc/modprobe.d/bcm43xx :-?

---

### Post by Totoro on 2006-07-07
Hello,

Same problem here.

```
sudo ndiswrapper -m
```
write "alias wlan0 ndiswrapper" in /etc/modprobe.d/ndiswrapper

but in Network Manager, I have eth1. :-? 

I try to change eth1 -> wlan0 in /etc/network/interface. After reboot, the applet is green :mrgreen: but in configuration, it's always eth1 :evil: and I have no network...

(sorry for my bad english)

---

### Post by Totoro on 2006-07-07
I have add "ndiswrapper" in /etc/modules (not sur it's need)

change eth1 -> wlan0 in :
/etc/modeprobe.d/ndiswrapper
/etc/network/interface
/etc/iftab

and it's work ^^

---

### Post by new2linux2000 on 2006-07-07
edit - i spoke too soon. i rebooted.. i cant believe it! it works! omg.. you are my hero. everyone who posted here, you are all my heroes!

---

### Post by ubunturules on 2006-07-07
Thanks Totoro for the fix!  I will add this to the guide.

---

### Post by foxy123 on 2006-07-08
> **Totoro said:**
> I have add "ndiswrapper" in /etc/modules (not sur it's need)

change eth1 -> wlan0 in :
/etc/modeprobe.d/ndiswrapper
/etc/network/interface
/etc/iftab

and it's work ^^

thanks a lot, it helped...

---

### Post by michael1977 on 2006-07-08
Just wanted to thank you greatly for this how to.  It worked for me and now I have good wireless speed.  I originally used the firmwarecutter how to and it worked but it took any where from 2 to 5 minutes to load google.com.  So thank you thank you thank you.

"you are a god among insects"

---

### Post by ubunturules on 2006-07-08
I'm glad to hear that it helped you.  I've never tried the firmware cutter but I heard a lot of problems with slow connections.  I think eventually that will be fixed but for now ndiswrapper is the way to go.

---

### Post by RyanTMulligan on 2006-07-08
```

0000:03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Linksys WPC54G
        Flags: fast devsel, IRQ 10
        Memory at 24000000 (32-bit, non-prefetchable) [disabled] [size=8K]
        Capabilities: [40] Power Management version 2

```

I tried following the tutorial you gave but when I do ndiswrapper -l
I get...
```
root@rtmlappy:/home/rmulliga/Desktop# ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!

```

Any ideas would be a great help. UbuntuRules, what does your lspci -v say?

---

### Post by ubunturules on 2006-07-08
RyanTMulligan: Go to home.nc.rr.com/thehinnants/stuff/drivers to get the drivers or get the drivers from the linksys website.  You will need to save the .inf file as bcmwl5.inf if you get it from home.nc.rr.com/thehinnants/stuff/drivers.  If you get it from the linksys website you will need to do it on a windows box because it is a .exe file.  You could possibly do it using wine to get the drivers from the .exe but I've never tried it.   You probably used the drivers from the cd which come up as invalid driver because I had this problem a long time ago.

my lspci -v is: 
0000:01:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Linksys: Unknown device 0013
        Flags: bus master, fast devsel, latency 64, IRQ 11
        Memory at f4100000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

Hope this helps!

---

### Post by nosam on 2006-07-08
Hi, I've played with a few Linux distros but have never been able to get my Linksys WMP54G to work.  I *really* like Ubuntu and am hoping I can get it to work. I know it has Broadcom 4306 because I did: ```
lspci | grep Broadcom\ Corporation
``` in the terminal and got Broadcom 4306.  I found that command on another thread.  


I got as far as "sudo apt-get install ndiswrapper-utils" but got
```
E: couldn't find package ndiswrapper-utils
```

I'm not too good when it gets down to the nuts and bolts of linux so I know i'm probably making some noob mistake.  :rolleyes:

What did I do wrong? Thanks

---

### Post by ubunturules on 2006-07-08
That's the exact card I have so this guide should work for you.
```
sudo gedit /etc/apt/sources.list
```
enable everything, which means take all of the #'s out that are infront of the word deb.

If you don't have any special repositories then you can just copy and paste this in your sources.list which might be easier for you.

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

save the file then run.

```
sudo apt-get update
```
```
sudo apt-get install ndiswrapper-utils
```

---

### Post by nosam on 2006-07-08
Ok, did that part exactly like you said.  Went to do:
```
sudo ndiswrapper -i ~/desktop/bcmwl5.inf
```

and got

```
sudo: ndiswrapper: command not found
```

I don't know much about linux but i'm thinking that i'm incorrectly pointing it to where the .inf and .sys files are.  I have them on my desktop in ubuntu.  So would "~/desktop/bcmwl5.inf" be correct or would it be "~/home/matt/desktop/bcmwl5.inf" or what?  

Thanks alot for your help by the way.  I really appreciate it.

---

### Post by ubunturules on 2006-07-08
did the sudo apt-get install ndiswarpper-utils go fine?
another thing is Desktop needs to be capitalized.
it would be ~/Desktop/bcmwl5.inf

---

### Post by nosam on 2006-07-08
I believe there might have been text regarding some sort of error, but there was alot of text that is beyond me.  In the end it didn't actually stop me from moving on so I kept going.  I will go back and make sure to capitalize the 'd' on desktop.  Sorry.:rolleyes:

---

### Post by nosam on 2006-07-08
No luck with making sure the 'd' in Desktop was capitalized.  Any more suggestions?

---

### Post by ubunturules on 2006-07-08
try this again
```
sudo gedit /etc/apt/sources.list
```

Delete everything that is in there.
Copy and paste the following into the file.

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

save the file.

```
sudo apt-get update
```
```
sudo apt-get install ndiswrapper-utils
```

that should work.

---

### Post by nosam on 2006-07-08
I replaced everything in that file with exactly what you posted and saved the file.  Here's what I got when I did "sudo apt-get update":

```
matt@matt-desktop:~$ sudo apt-get update
Err http://us.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com' 
Err http://us.archive.ubuntu.com dapper-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com' 
Err http://us.archive.ubuntu.com dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fecth http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg
Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Some index files failed to download, the have been ignored, or old ones used instead.
```

Then I tried:

```
matt@matt-desktop:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper-utils
```

Then for the hell of it I did:

```
matt@matt-desktop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo: ndiswrapper: command not found
matt@matt-desktop:~$ sudo ndiswrapper -i ~/home/matt/Desktop/bcmwl5.inf
sudno: ndiswrapper: command not found
```

:confused:

---

### Post by ubunturules on 2006-07-08
You do have a working internet connection right?

---

### Post by nosam on 2006-07-08
Well no.  I can't run an ethernet cable to where I am in my house, hence getting the wireless to work.  You're telling me I have to be connected to the internet to be able to get my wireless connection to work?  If so, and that's kind of ridiculous, then I guess I'm going to have to take this whole thing to the basement just to set this up.  If I do so will these steps then work properly?

---

### Post by ubunturules on 2006-07-08
You need a working internet connection to get the ndiswrapper-utils.  Yes it is kinda rediculous but once you do all of the steps will run smoothly.

---

### Post by nosam on 2006-07-08
EDIT: Nevermind.  It appears to be working now.  Thanks for the help man.

---

### Post by ubunturules on 2006-07-09
No problem man.  Glad to here you got it working!

---

### Post by raalynthslair on 2006-07-09
Not to sound like a bad/cheap plug here... BUT the Fedora Core 5 DVD Iso I downloaded for my laptop has the 2.6.15... kernel and it has the drivers installed by default during the system install. It just worked out of the box on my Compaq Presario R3000. I've not yet had the chance to try the Ubuntu latest build yet (at the time the FC5 AMD64 build was more current than Ubuntu's - though Ubuntu has the same kernel and Gnome versions I use on FC5 so I expect its days (FC5 that is) are limited now. ^_^ )

Zor

---

### Post by tsb on 2006-07-09
The ndiswrapper utilities can be installed from the CD for those w/o a connection.

Anyone wanting to stick with the debian/ubuntu base can try MEPIS.  My 4306 works fine after blacklisting the native driver and changing the wireless from etho0 to wlan0 in the configuration menu.  No need for ndiswrapper either.  MEPIS 6 goes final tomorrow AFAIK.  I'm dual booting Ubuntu and MEPIS 6 now.  MEPIS is a better KDE alternative than Kubuntu IMO and Ubuntu is my favorite GNOME'd distro.

---

### Post by ubunturules on 2006-07-09
I forgot you could install stuff from the Ubuntu CD.  Thank you tsb.  I will add this to the guide.

---

### Post by nosam on 2006-07-09
Damn.  It works, *but* everytime I restart it doesn't.  After logging in I'll go to System>Administration>Networking and the wireless connection doesn't even show up as an option.  BUT if I do "sudo modprobe ndiswrapper" in the terminal then it will show up.  The weirder part is that the little network connections icon is _always_ there in the panel, but it never shows that anything is connected.  Like right now I'm on ubuntu over my wireless connection and when you left click on it it says "no network devices have been found".  I don't think it even worked when I had this thing hooked up via a hard line.  

None of this is really that big of a deal since in the end I am on the internet wirelessly.  I just wondered if you might have any ideas.  Thanks again.

---

### Post by sp0nge on 2006-07-09
Well I thought I'd give this a go, as I finally made the leap to Ubuntu just over a week ago and miss the freedom of the wireless network on my Dell Inspiron 1000. The boradcom BCM94306 is not easily supported that I can see. This is the third How To I've tried and I'm about to go buy another wireless card and give that a go. Anyone out there have any suggestions otherwise? 

I get to the point of ndiswrapper -l in the terminal then get this:
 Installed ndis drivers:
 bcmwl5 invalid driver!

---

### Post by ubunturules on 2006-07-09
No don't do that.  There is an easy fix to this.  Go to home.nc.rr.com/thehinnants/stuff/drivers and get the drivers from there.  If you use those you will have no problem.  Just make sure you save the .inf file on the website as bcmwl5.inf.  Hope this helps you.

---

### Post by foxy123 on 2006-07-09
> **nosam said:**
> Damn.  It works, *but* everytime I restart it doesn't.  After logging in I'll go to System>Administration>Networking and the wireless connection doesn't even show up as an option.  BUT if I do "sudo modprobe ndiswrapper" in the terminal then it will show up.  The weirder part is that the little network connections icon is _always_ there in the panel, but it never shows that anything is connected.  Like right now I'm on ubuntu over my wireless connection and when you left click on it it says "no network devices have been found".  I don't think it even worked when I had this thing hooked up via a hard line.  

None of this is really that big of a deal since in the end I am on the internet wirelessly.  I just wondered if you might have any ideas.  Thanks again.

add ndiswrapper in /etc/modules

---

### Post by lukem on 2006-07-09
ubunturules:
thank you very much for taking the time to put this how to together.  My motorola wn825g card now works on a dell d600.  The first time through the process i got an error that the inf file could not be copied (something about line 135) and sure enough when i finished the process it did not work.  I even got the invalid driver error mentioned above.  I deleted the driver and tried again and it worked the second time.  I got the driver from home.nc.rr.com/thehinnants/stuff/drivers.  It did not download as I expected when I clicked on it.  Rather it was opened as a text file and I just saved it from there.  

Thanks again.  If you get the time to explain what all of this is actually doing it would be a real education for those of us (me) who don't understand it all :)

Thanks
lukem

---

### Post by Ulysses on 2006-07-09
Hello

This is a very good instruction
I followed it to the letter. Or at least, I think I did.
For some reason the following has occured:
When I check for the wireless card in terminal, it is there
When I check for the wireless card using system>administration>networking, all that shows is my modem / it doesn't even show my regular network connection
On the toolbar on the upper right portion of my screen are two networking incons
One is my network connection / this is the icon that I think represents the Network Manager Applet (that's what it says when I click on 'about)
The other icon is also for the network connection / though this one says that it is wlan0 - I thought when I followed the directions that this would be the name of my wireless network?

Oh, dear. I think I've made a mistake but I don't know where to start.
Before I start rewiring my house so I have a cable outlet in every room, can someone please help with this?

RAR

---

### Post by ubunturules on 2006-07-09
Ulysses: I don't know what you should do.  Maybe reinstalling the driver would help.

do:
```
sudo ndiswrapper -e bcmwl5.inf
```
```
sudo ndiswrapper -i ~/place where driver is/bcmwl5.inf
```

a reboot might be needed.  Im not really sure.  Any body else have any ideas?

---

### Post by nosam on 2006-07-09
> **foxy123 said:**
> add ndiswrapper in /etc/modules

It won't let me save the file.

---

### Post by ubunturules on 2006-07-09
```
sudo gedit /etc/modules
```

add ndiswrapper

click the save button.

---

### Post by nosam on 2006-07-09
> **ubunturules said:**
> ```
sudo gedit /etc/modules
```

add ndiswrapper

click the save button.

It's weird, nothing happens.  But I can see and open the file in /etc, here are the contents of it if that helps: 

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
```

---

### Post by ubunturules on 2006-07-09
try:
```
sudo nano /etc/modules
```

nano is another text editor.

---

### Post by nosam on 2006-07-09
Did that.

I still have no connection upon logging into ubuntu.  But now when I go to System>Admin>Networking the wireless option *is* there.  Along with the ethernet connection, both are "active".  I have to deactivate the ethernet connection and go into properties for my wireless connection (where my ssid and wep key are already entered and are correct), hit ok, and it will activate the wireless connection.  Then I hit ok to close the "Networking" box.

I restarted and noticed when ubuntu is loading that both "Basic Networking..." and "Configuring Network Devices..." have "failed" to the right instead of "ok" like everything else.  Would this have anything to do with it?

Also, the networking icon on the panel does nothing.  It says "No network connection" when you hold the mouse over it (yet I'm writing this post).  Right-clicking on it shows "Enable networking" checked but "Connection information" is grayed out.  The icon just has the two computers with a little exclamation point in the bottom right corner.

Again, thanks for your help.

---

### Post by ubunturules on 2006-07-09
Yeah that could have something to do with it.
do a:
```
sudo gedit /etc/network/interfaces
```

put a "#" in front of anything that has to do with your wireless essid.  That might help.  You dont want to enter any information in System>Admin>Networking about your wireless essid and password because you want Network Manager to deal with it and it will cause a confliction and it won't work.

---

### Post by nosam on 2006-07-10
> **ubunturules said:**
> Yeah that could have something to do with it.
do a:
```
sudo gedit /etc/network/interfaces
```

put a "#" in front of anything that has to do with your wireless essid.  That might help.  You dont want to enter any information in System>Admin>Networking about your wireless essid and password because you want Network Manager to deal with it and it will cause a confliction and it won't work.

Ok, I'm not really sure what I did (because I already had the ssid and wep key commented out in /etc/network/interfaces) but I got the network manager applet to work.  I was able to enter in my ssid and wep key and the icon starting working with the lights etc.  After a moment it turned into the bars and said that it was connected... but firefox couldn't open any pages and gaim couldn't connect either.  I then went into System>Admin>Networking to see what was in there--in options for wireless connection everything was blank (I'm assuming because I commented out what I did in /etc/network/interfaces) and "enable this connection" was checked.  Finally, fed up, I entered in my ssid and wep key in there and I was able to get on the internet.  The network manager applet now doesn't work just like before.  I must have missed something somewhere but I have gone back and checked everything.  Here is exactly what is in my /etc/network/interfaces file as of this moment, while connected, after entering in my ssid/wep through System>Admin>Networking.

/etc/network/interfaces:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface wlan0 inet dhcp
wireless-essid 1
wireless-key "my key here"
#wireless-essid 1
#wireless-key "my key here"
#wireless-essid 1


auto eth2
iface eth2 inet dhcp

auto ath0

```

Here is /etc/modeprobe.d/ndiswrapper:

```
alias wlan0 ndiswrapper
```

/etc/iftab:

```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:07:e9:e9:99:ff arp 1
wlan0 mac 00:0c:41:12:f6:56 arp 1

```



Sorry I can't seem to get this to work right.

---

### Post by johnzilla on 2006-07-10
Hope someone can help... I've followed the instructions to the letter, and am having difficulty...

```
ndiswrapper -l
```

reports that bcmwl5 driver is present, hardware is present. (downloaded an installed from the website as directed.)

/etc/network/interfaces has the following entry:

```
auto wlan0
iface wlan0 inet dhcp
```

I've run ndiswrapper -m and confirmed that an alias has been created in /etc/modprobe.d/ndiswrapper

I applied Totoro's fixes so that all references point to wlan0, not eth1.

BUT wlan0 isn't displayed in the System->Admin->Networking app, nor does it appear in nm-applet, only eth0 and lo show up.

Anyone have any idea what I'm overlooking? (It is late and I am tired, so I'm sure the fault is my own.)

Out of frustration I even opened up my laptop to make sure I am in fact using at 4306. (I am. )

Thanks!

-John

---

### Post by ubunturules on 2006-07-10
nosam: I'm not really sure what's wrong but if you got it to work without NetworkManager then don't use NetworkManager.  Go to System>Preferences>Sessions and click on the startup tab and delete nm-applet --sm-disable.  If you wanted to get it to work with nm-applet you must comment out everything that has to do with your essid and key.  You leave all of the iface, lo, and auto stuff.

johnzilla:run: ```
sudo modprobe ndiswrapper
```You might need a reboot.  Reboot and post back what happened.

---

### Post by johnzilla on 2006-07-12
Thanks for the help, I ran that about 20 times, no dice. I went through the whole process about 6 more times, still no luck.

Having only just installed Ubuntu, I decided to do a fresh install.  Sure enough, after a fresh install, wireless set up perfectly first time.

I guess I must have broken something while I was trying to get networking up before I found this post.

---

### Post by ubunturules on 2006-07-12
Glad to here you got everything working.  It does help if you do it after a fresh install.  That's the first thing I do after a fresh install is getting wireless working.

---

### Post by devan on 2006-07-15
pardon the ignorance, but I have a broadcom 4306 (rev 3). I saw in this post ubunturules, that you had REV 2. Will these steps work with REV 3 with the same driver?

I have wifi working with the built in driver and firmware, but i would like 54mbps.

Thanks!

---

### Post by jISh on 2006-07-16
Thank ya. My Motorola card works just fine now :)

---

### Post by ubunturules on 2006-07-16
Devan: Yes it will work.

jISH: Glad to here that you got it working.

---

### Post by felixdzerzhinsky on 2006-07-17
Worked for me as well.

Thanks

---

### Post by timofthec on 2006-07-17
hi.
first off - my apologies for not reading the entirety of this thread - its very long and i'm at work (naughty me)so if this question has already bee asked and answered - sorry :-# .

anyway, i've been trying for a few days now to get my wireless network up and running without a great deal of success and am going to try yet again using this posted guide (fingers crossed)

However, there is one part that i'm not sure about which is: -
> **ubunturules said:**
> 
add "blacklist bcm43xx" to the bottom of the file.  Without the quotation marks.


what is this telling me to do? to the bottom of which file should i be adding blacklist bcm43xx to?  

oh, and do i type bcm43xx or do i replace the xx with something specific to my card?

thanx in advance :D

---

### Post by foxy123 on 2006-07-17
> **timofthec said:**
> hi.
first off - my apologies for not reading the entirety of this thread - its very long and i'm at work (naughty me)so if this question has already bee asked and answered - sorry :-# .

anyway, i've been trying for a few days now to get my wireless network up and running without a great deal of success and am going to try yet again using this posted guide (fingers crossed)

However, there is one part that i'm not sure about which is: -


what is this telling me to do? to the bottom of which file should i be adding blacklist bcm43xx to?  

oh, and do i type bcm43xx or do i replace the xx with something specific to my card?

thanx in advance :D
just open the file /etc/modprobe.d/blacklist and add
```
blacklist bcm43xx
```
to the bottom of the file. it will blacklist the native bcm43xx driver.

---

### Post by dk5151 on 2006-07-20
Everything seems to be going smoothly for me in the process until the step when I am supposed to deactivate my ethernet connection and activate my wireless. I it only lists my ethernet connection and the modem connection, but no wireless. It listed the wireless before I found this guide (didn't work, of course). I'm not sure where I may have went wrong. This has happened twice now.

---

### Post by ubunturules on 2006-07-20
do a:
```
sudo ndiswrapper -e bcmwl5
```

then a:

```
sudo ndiswrapper -i bcmwl5.inf
```

---

### Post by dk5151 on 2006-07-20
Uninstalled and reinstalled, as you suggested, and I'm still getting the same results. I did a 'ndiswrapper -l' after remove/install to make sure that it worked at each step and both steps were fine. This is now the third time I've tried and I don't understand why it's not working. The old driver is blacklisted, that's why it doesn't appear, correct? But the new driver should make it reappear, right? I'm new to Linux in general so I'm trying to make sure that I understand what I'm doing instead of typing random commands. I was trying to use the 64 bit version but I even tried reinstalling with the 32 bit, but the same results. The driver is installed in ndiswrapper, any ideas what could be in the way?

---

### Post by ubunturules on 2006-07-21
what does ndiswrapper -l give you?

---

### Post by dk5151 on 2006-07-21
It tells me that the driver and hardware are both present. I don't have it in front of me at the moment, so I can't remember the exact syntax.

*Edit: I just checked, the exact syntax is: "bcmwl5     driver present, hardware present"

During the process, when I do the 'sudo ndiswrapper -m" I don't get any input, it just goes back to the command prompt, is it supposed to tell me anything there?

---

### Post by ubunturules on 2006-07-22
No ndiswrapper -m isn't supposed to tell you anything right there.  Have you rebooted your computer?

---

### Post by Otto-C on 2006-07-22
I too have lost the wireless option on 
system > admin. >networking. Inadvertantly
deactivated it. Wireless worked great.
How do I get it back?
tia
OC

---

### Post by ubunturules on 2006-07-22
```
sudo ndiswrapper -e bcmwl5
```
which will uninstall the driver

```
sudo ndiswrapper -i bcmwl5.inf
```
which will install the driver

```
sudo modprobe ndiswrapper
```

you might need to reboot.

ps:this guide works best when doing it right after a fresh install.

---

### Post by dk5151 on 2006-07-25
> **ubunturules said:**
> No ndiswrapper -m isn't supposed to tell you anything right there.  Have you rebooted your computer?

Yes, I've rebooted. The firmware cutter method seems to be giving me better results right now, but I would really like to get ndiswrapper going so that I can use wireless G instead of B.

---

### Post by ubunturules on 2006-07-26
This method seems to work better with a fresh install.  I promise.

---

### Post by CeeDub on 2006-07-27
I'm having the exact same problem as dk5151.  I've had ubuntu for a while now, so how can I go about doing a fresh install without losing a lot of what i've done so far? Or is that possible?

---

### Post by neurotech on 2006-07-27
Okay. I've just gone through the tutorial for a second time, on a fresh install of Ubuntu 6.06, AMD64bit. My card is a Linksys WMP54G as stated by lspci:

```
0000:05:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

After 3 reboots at various stages, (all done after a "sudo modprobe ndiswrapper") my card is not appearing in Networking. The only item in the list is my ppp0 modem connection. I'm now at wit's end. I'm sure I haven't done anything wrong. I used the drivers from the recommended site, and done every step of the tutorial carefully.

Does anyone have any ideas on how I can fix this? I'm very tempted to buy a different card just so I can get wireless net access.

---

### Post by ubunturules on 2006-07-27
That's the same card I have.  Make sure you get the drivers from the home.nc.rr.com/thehinnants/stuff/drivers.  
try:
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf

That should work.

---

### Post by neurotech on 2006-07-27
> **ubunturules said:**
> That's the same card I have.  Make sure you get the drivers from the home.nc.rr.com/thehinnants/stuff/drivers.  
try:
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf

That should work.

Okay, should I use those commands literally or should I specify the path in the second command i.e. "sudo ndiswrapper -i ~/bcmwl5.inf" ?

---

### Post by ubunturules on 2006-07-27
you should specify the path in the second command.

---

### Post by punx45 on 2006-07-28
the good news is thanks to this guide i finally got a valid driver installed.

the bad news is when i "sudo modprobe ndiswrapper" i get yelled at thusly:

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/misc/ndiswrapper.ko): Invalid argument
```

i checked my .bash_history against the guide and followed all steps.   also rebooted and uninstalled and reinstalled the bcmwl5.inf.

i checked, and ~/ndiswrapper.ko does exist.

also read through this entire discussion and didnt see anything related to this error message.

---

### Post by neurotech on 2006-07-28
> **ubunturules said:**
> you should specify the path in the second command.

No luck. Any other ideas? :(

---

### Post by hw-tph on 2006-07-28
> **neurotech said:**
> Okay. I've just gone through the tutorial for a second time, on a fresh install of Ubuntu 6.06, AMD64bit.

You need to use a 64bit driver (.inf and .sys file). A 64bit ndiswrapper module cannot load a 32bit Windows driver. You can find 64bit drivers attached [here](http://ubuntuforums.org/attachment.php?attachmentid=186).

[quote=ubunturules]That's the same card I have. Make sure you get the drivers from the home.nc.rr.com/thehinnants/stuff/drivers.[/quote]

That's misleading. Those are 32bit drivers and won't be of any help to neurotech. Grab the drivers I linked to above instead.

Making a note of 64bit vs 32bit in the howto and provide links for both would probable save a lot of people a lot of time.



Håkan

---

### Post by ubunturules on 2006-07-28
punx45: make sure you run
```
sudo ndiswrapper -m
```
before you run
```
sudo modprobe ndiswrapper
```

neurotech: Read hw-tph's post.

hw-tph: you are correct about neurotech's problem.  I over read 64 bit part.

---

### Post by CeeDub on 2006-07-28
That 64-bit 32-bit thing seemed to have done something.  For one, when I installed the driver, the terminal says:
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2

Is that a good thing? I ask this because now the network manager can find the wireless spots, which it couldn't with the other driver, but it still won't connect.  It tries to, but it never does.  Any ideas on what I'm doing wrong?

---

### Post by mkw87 on 2006-07-28
I'm having trouble getting this to work as well, I'd really like to do it this way too.  My thread I started is [here](http://ubuntuforums.org/showthread.php?p=1311717#post1311717) (not to hijack, just looking for help).  Thanks.

---

### Post by ubunturules on 2006-07-28
what is your problem?

---

### Post by mkw87 on 2006-07-28
The hardware is recognized, but the internet does not work.  I honestly have no idea how to troubleshoot from here, ever step I followed gave the expected result...except for the wireless working (connecting, it appears to work but not connect?)

I followed the steps exactly, and have rebooted several times, one thing to note is that I have no entry it /etc/iftab, its blank/does not exist, not sure if thats a problem or not.

---

### Post by joypunk on 2006-07-28
You are my hero. I've been trying for over a week to get my BCM4306 adapter online with Ubuntu. Nothing has worked... this guide worked flawlessly.

---

### Post by neurotech on 2006-07-29
Thanks for that hw-tph, I'll try that when I get home. I have a good feeling about it this time!

---

### Post by mkw87 on 2006-07-29
I installed the gnome network manager, but it only lists my wired connect?  However, in sys -> admin -> networking, wlan0 is still present, any idea?

edit: Ok, I got it to show up by commenting everything in /etc/networking/interfaces out except the lo and loopback lines.  Now I entered my wep key and it tries to connect but never does...

The router sees the computer as well, but the iwconfig shows the computer working off of 2.462GHz and not the default 2.437GHz, so I changed the router, but it didnt seem to help, is there a way to change the computers signal frequency?

---

### Post by punx45 on 2006-07-29
> **ubunturules said:**
> punx45: make sure you run
```
sudo ndiswrapper -m
```
before you run
```
sudo modprobe ndiswrapper
```

i did.

---

### Post by n.arciss.us on 2006-07-29
> **ubunturules said:**
> did this HOWTO help anyone?

Thanks SO much!!!!   Now I can finally get rid of the 25ft cable snaking around my living room. (Wife will be very happy!):KS


**EDIT:** Works fine except that network manager doesn't hold the key after reboot. Could this have anything to do with running a Gnome applet in a KDE enviroment??

---

### Post by ubunturules on 2006-07-29
n.arciss.us : They are hoping to fix that problem in the next version of Network Manager.  But to that is not a problem.  That is what is supposed to happen.

---

### Post by n.arciss.us on 2006-07-29
> **ubunturules said:**
> n.arciss.us : They are hoping to fix that problem in the next version of Network Manager.  But to that is not a problem.  That is what is supposed to happen.


I kinda thought that might be the reasoning. If that's the case, then its fine with me ... I DO have wireless now!

---

### Post by neurotech on 2006-07-30
hw-tph, do I need to rename the drivers you attached to your reply or anything?

---

### Post by ubunturules on 2006-07-30
make sure they are named bcmwl5.inf and bcmwl5.sys

---

### Post by yotoad on 2006-07-31
if i have rev 02 card like yours, and my hardware and driver are present -- i can't get the card to connect (plus it's called eth1)

thanks for your help

---

### Post by yotoad on 2006-07-31
ubunturules

i followed your instruction to a T and it works!  that is, the light is on on the card and the card shows up in Network Settings

but i have a couple of questions -- after i rebooted, the wireless connection is showing up as eth1 (and active) -- when i try to edit the list of files to change eth1 to wlan0, i can't save the file because it is read-only.

and, the application at the top right corner is not showing up anything besides eth0 and lo

thanks for your help

---

### Post by punx45 on 2006-07-31
> **yotoad said:**
> ubunturules

 -- when i try to edit the list of files to change eth1 to wlan0, i can't save the file because it is read-only.



as far as editing the read only files, edit with root power such as ```
sudo gedit ~/file
```

---

### Post by yotoad on 2006-07-31
okay, so now everything is working, however when i connect to a wifi hotspot -- as i just did a second ago, i was able to connect to the router but not the internet -- for instance, this forum or google, or anything -- 
any help?

---

### Post by mkw87 on 2006-07-31
> **yotoad said:**
> okay, so now everything is working, however when i connect to a wifi hotspot -- as i just did a second ago, i was able to connect to the router but not the internet -- for instance, this forum or google, or anything -- 
any help?
Is yours named ethX or wlanX?  I have a rev 02 that I have semi-working (ie: it sees the router, the router sees it, but it won't connect).  

@ Ubunturules, does it matter that its wlanX vs ethX?  If not, any idea why it wont connect?  I have tried both with and without WEP, and it connects when using windows, so I know both work properly (router and lappy)

---

### Post by yotoad on 2006-07-31
i renamed mine to wlanX

---

### Post by ubunturules on 2006-07-31
Most people have success with wlanX

---

### Post by rlynch on 2006-07-31
man, I gotta say thanks. It took me 5+ hours of trying things out before finding this thread.


1 - Thanks for posting how to change eth1 to wlan0
2 - Thanks for posting the inf and sys driver files
3 - Thanks for taking the time and posting this tutorial. I thought without wireless my Ubuntu use will be cut short.


Thanks again!

---

### Post by Der Eisern Pinguin on 2006-07-31
Hello,

I've been using this how-to and all has gone well until I use ndiswrapper to install the driver (bcmwl5.inf). When I type
```

ndiswrapper -l
```

the output shows something along the lines of: 

```

bcmwl5 - invalid driver!
```

As per your tutorial, both the .inf and .sys files are in the same directory, /home/kenneth/4318. 

Has anyone else had this issue?

*Edit: I thought I should mention that I am using this tutorial to install the Broadcom 43**18** drivers for the Broadcom 43**18** card. I don't know if there are esential differences in the installation of the drivers for these cards that would preclude using the same process.*

---

### Post by Der Eisern Pinguin on 2006-07-31
Okay, with some fresh drivers, running 
```

ndiswrapper -l
```

yields a much more pleasing
```

Installed ndis drivers:
bcmwl5    driver present, hardware present
```

However, when I go to [FONT="Lucida Console"]System -> Administration -> Networking[/FONT], I still only see 'Ethernet connection' and 'Modem connection.' The entry for my wireless card which disappeared after killing bcm43xx is still absent.

---

### Post by rlynch on 2006-08-01
I must say I love having wireless, but right after I login, before the splash screen. I have a really long 6-7 minute pause now after doing this how-to.

Any Ideas?

---

### Post by lukeluke on 2006-08-01
Thanks a lot for this guide! Now my wireless is working perfectly! :p

---

### Post by yotoad on 2006-08-01
mine is named wlan0, but it still doesn't connect to the internet for software updates, or firefox, or anything.

it does however, connect to my windows network and i'm able to browse my closed network (not connected to the internet, just for file-sharing within my own network)

any help?  are there things i need to do to set up firefox?  or in order to download software updates?

---

### Post by yotoad on 2006-08-02
Anybody have any pointers on my comment above?

---

### Post by yotoad on 2006-08-02
Anybody have any pointers on my comment above?

---

### Post by dk5151 on 2006-08-02
I finally got my wireless to work. I used the 64-bit drivers, but I didn't rename the files. When I renamed them to match the files in the how-to it wouldn't work for me. I tried it again leaving the file names unchanged and it worked perfectly. Just thought I'd let everyone know.

---

### Post by ubunturules on 2006-08-02
dk5151: Thank you for telling us that.  I've never had to deal with the 64bit drivers so I just assumed that you needed to name them to what it is in the how-to.

---

### Post by gmanpsycho on 2006-08-03
OK I'm good up until I have to enter

```
sudo rmmod bcm43xx
```

I get
```

ERROR: Module bcm43xx does not exist in /proc/modules
```](*,) 

Not sure what's going on can anyone help me out?

All the other commands seem to work fine but I'm still not wireless yet...

---

### Post by meander on 2006-08-03
yup, worked beautifully for me
=D>

---

### Post by Epperly on 2006-08-03
[edit]nvm got it[/edit]

---

### Post by Epperly on 2006-08-03
WTF, last time I tried to do this from another guide wlan was at least under "Networking", now it's not there :(
What'd I do?

---

### Post by dk5151 on 2006-08-04
> **ubunturules said:**
> dk5151: Thank you for telling us that.  I've never had to deal with the 64bit drivers so I just assumed that you needed to name them to what it is in the how-to.

No problem, I'm just glad I got it going so that I don't have to go back to Windows haha.

---

### Post by chuckn on 2006-08-05
This is a great tutorial. It worked on my compaq presario without a hitch.
Thanks for the help.

I do have a question. I have disabled ssid broadcast on my linksys router. The only way i can connect via wireless is to enable ssid. Is there a way I can connect w/o changing ssid?

---

### Post by Epperly on 2006-08-05
wow broadcom really needs to make linux drivers, cause this is fuckin pissing me off... can't get htis shit to work on ubuntu so now Im trying SuSE in hopes of better support, and SuSE's installers sucks and takes forever...

UGGHHH I HATE THIS LAPTOP

---

### Post by ripple on 2006-08-09
> **ubunturules said:**
> did this HOWTO help anyone?

So far it has helped yes.  Please help me a bit more.  im a bnoob.  So, my main problem is that eth1 is always my wlan card,.. when it is available.  Something i did made it invisible.  now i only have eth0.  So can you help me get it back?  When I did have it.. it never worked.. i could activate it but nothing happened after that.  Also, in you final lines you posted that to solve the eth1 problem to put the Ndiswrapper into etc/??? .. what do yo mean by that.. i don't follow.. this keeps me from editing the file to change eth1 to wlan0

thanks in advance
Joeripple

---

### Post by ubunturules on 2006-08-09
for some reason a lot of people can't get wlan0 to show up under Networking.  I don't know why.  Make sure your hardware is present.
```
sudo ndiwrapper -l
```

also when I say put ndiswrapper in /etc/modules I mean do a:
```
sudo gedit /etc/modules
```
and add the word "ndiswrapper" to it without the quotations

if anyone else has any idea on why wlan0 isn't showing up under networking please tell me because that seems to be happening to a lot of people.  The only reason I can think of that, that would happen would be that you installed an invalid driver and the hardware isn't present.

---

### Post by Epperly on 2006-08-09
> **ubunturules said:**
> for some reason a lot of people can't get wlan0 to show up under Networking.  I don't know why.  Make sure your hardware is present.
```
sudo ndiwrapper -l
```

also when I say put ndiswrapper in /etc/modules I mean do a:
```
sudo gedit /etc/modules
```
and add the word "ndiswrapper" to it without the quotations

if anyone else has any idea on why wlan0 isn't showing up under networking please tell me because that seems to be happening to a lot of people.  The only reason I can think of that, that would happen would be that you installed an invalid driver and the hardware isn't present.
That's what made me give up on Linux on my laptop...

---

### Post by BGreet on 2006-08-11
Hey everyone.  So basically I had my broadcom working in Ubuntu with FWcutter initially, but it then randomly crapped out and I have no more wireless connection.  I decided I would use ndiswrapper, and everything seems to go off without a hitch (I did exactly as the tutorial said).  Ndiswrapper installs the driver, and states the driver and hardware are both present, however, the wireless light does not come on, and it appears that the hardware isn't even installed after modprobing.  Any ideas on what could be wrong?  I'm at the point where I'm seriously contemplating just going back to windows.. I really need this wireless to work for school. :/

---

### Post by ilikewhenthingswork on 2006-08-11
hw-tph ftw

thanks so much for those 64 bit drivers

everything works great now

---

### Post by em0maha on 2006-08-17
Thank you soo much.
I have tried multiple Howtos and this one is the only one that has worked so far.
Anyone with a Presario 2100, try this first.

---

### Post by WeeGraeme on 2006-08-20
I've followed this how to and it's been a help to me.  I haven't actually got wireless networking working, but as a result of following everyone's suggestions, I have got eth1 changed to wlan0.

When I was installing, everything worked except for network manager.  When I ran nm-applet the terminal seemed to freeze, and no icon appears on the top panel.

Are there any ways to tweak network manager?  I don't know what it's unhappy about.  Please type slowly if you reply because I've only been playing with Ubuntu / Linux for about 4 days.

---

### Post by uph0ria on 2006-08-20
Hey,

I was able to get my card working with the help of your tutorial, thank you.:D

---

### Post by ubunturules on 2006-08-20
WeeGraeme: These commands will help diagnose the problem.
```
sudo killall NetworkManager
```
```
sudo NetworkManager --no-daemon
```

Tell me what errors are coming up when you run this.

---

### Post by WeeGraeme on 2006-08-23
I'll have to revisit this later.  Due to needing to use the laptop again, I was forced to change back to Windows.  I'll have another look at Ubuntu at the end of semester.

Thanks to everyone who has offered suggestions.  Even without a full understanding of how to drive Ubuntu, I had already grown to like some features and I miss them already.  I've just found that I don't quite have enough time to spend to get it working properly just yet.

---

### Post by filloy on 2006-08-24
Everything worked fine, i got an IP addres, internet was working great, but suddenly, after reboot, my eth1 (the wireless) stopped working. Any idea on why ??? im back at the same point where I started, except now im more dessperated because i know it works :s

Please, someone help me !!

---

### Post by ubunturules on 2006-08-24
What is the problem?  What exactly doesn't work?  I understand the wireless in general but what do you think the problem is?

---

### Post by filloy on 2006-08-24
Intresting...
I read your post and decided to write the answer.
When analyzing what could be the problem, i found out that i installed the Automatix Bleeder, software which changed my sources.list and downloaded some software, like another version of Ndiswrapper.
And that was it, i recovered the old ndiswrapper, stopped everything and started it again, and now its working again...lets hope this one last for more than 2 hours.

In any way, thank you very much for your attention :), i am really thankfull...

Good bye

---

### Post by DW5 on 2006-08-25
Great howto.  I lost my harddrive a week ago on my hp nx9010 w/ Broadcom 4303 and had a go at fwcutter with absolutely no luck.  This worked right through. However, I was worried that I didn't have the network manager icon I had been used to.  I thought it wasn't installing right.  But when I unplugged my network cable, it popped right up.

Thanks for the hard work.

---

### Post by Paul133 on 2006-08-25
I have a Dell 1200 witha  Dell 1350 Mini-PCI or PCMCIA wireless card (Broadcom 4306 (rev03) chipset). Will your instructions work with this?

---

### Post by Paul133 on 2006-08-25
How do you save the inf file?

---

### Post by Paul133 on 2006-08-25
I figured everything out!!! Thank you so much! Now I can use Ubuntu for everything! This is the best How-To I've seen. Now, Ubuntu is perfect, almost out of the box! Thanks again, you certainly save me a lot of time looking through other How-To's! Granted, I'm not an average computer user, but the support on the forums and these guides will help to make Ubuntu more accessible to the average computer user!

---

### Post by jwhitlark on 2006-08-26
Thank you very much for your howto.  I've lots of linux experience in other areas, but never managed to get this card working.  Now every computer in my house runs ubuntu.  (All 6 of them \\:D/ )

---

### Post by erusan on 2006-08-26
I've been having this problem ever since Flight 4 (-ish), but when I try to load the ndiswrapper module, I get a segmentation fault.  It shows the driver and hardware as being present, I have the .sys file in the same directory as the .inf file, etc.  It all works fine until I do the modprobe, and then I'm stuck.

Ideas?  Help?

---

### Post by francisco tovar on 2006-08-26
hello I am new in linux, this is my first time I write, I have just instaled ubuntu 64 on a amd turion 64 (network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)).
Everything is OK except the wireless conection, 

I tried to follow your tip, but have a problem...

when I put
 *sudo modprobe ndiswrapper*

I get:


FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-amd64-gener ic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

do you know what can I do?
thank you
francisco

---

### Post by kamil on 2006-08-27
Same problem as the poster above me, invalid argument after sudo modprobe ndiswrapper :(

---

### Post by WarAngel on 2006-08-27
After following this HOWTO, I have finally been able to get network-manager to display wireless networks in the area. I am still having a problem though; network manager tries to connect to the open network ('linksys') for about a minute, and then it simply stops trying. This is driving me nuts because I am so close to connecting, yet so far away. Any ideas on how to get my laptop to connect to the network now that I can see it?

Thanks in advance!

---

### Post by erusan on 2006-08-28
Does the network have WEP or Mac address filtering enabled?

---

### Post by EvilRusk on 2006-08-31
Thanks for this guide! I had to help somebody install their wifi over the phone (lol!) and it all worked out fine. Used the guide for my Netgear WG311v3 also (ammending chipset names/drivers where necessary).

---

### Post by Paul133 on 2006-09-05
It helped me a lot. Thanks, it's the best guide I've seen; better than those using the cutter.

---

### Post by davidrose_98 on 2006-09-05
I just want to say thank you for the great instructions.  I am currently posting this on my wireless laptop with a Broadcom 4306.  

I just have on suggestion.  Either link to the wiki or go into more detail about the gnome-network-manager.  I installed this after realizing that I could not connect at home (WEP) but only on an open network.  But after installing this, i only could see my wired network card in the applet and not my wireless card.  It wasn't until I read into the wiki to comment out (put # in front of) everything in the /etc/network/interfaces file except for the stuff that has to do with lo, because this is required for the loopback adapter, as well as add "ndiswrapper" (no quotes) to /etc/modules to be loaded on boot, since this will not load without a wireless interface present, that I was able to get the network manager to detect my wireless network.

Thanks again!!

---

### Post by GlennB on 2006-09-06
Hi,

> **ubunturules said:**
> This is the easiest way to get your Broadcom 4306 wireless card working in the shortest amount of time.  I wouldn't use the firmware cutter because I've heard a lot of stories of people only being able to run at 11 Mbps with it.  With ndiswrapper you will get 54 Mbps if your router will allow it.

Do everything in order as it is listed.

This all worked fine for me, until I rebooted (I suspect restarting networking might have shown the same problems). After following the HOWTO by the book, I got wireless access straight away (Dell Inspiron 1300, Broadcom BCM 4318 ). However after the reboot, things turned pear shaped :( 

Gnome-panel crashed repeatedly, and restarting it just brought the crash back. Both the wired and wireless networking interfaces also failed completely, leaving me with no net connection. I eventually traced it to problems with the 'identity' of the wireless card. 

Removing the fix below solved the problem, but left me in the situation where network manager no longer sees any network connections, as the wireless card is now 'eth1' instead of 'wlan0'. I still have a working wireless connection, though.

> Totoro found a fix for the eth1 problem.  Thank you Totoro.
add ndiswrapper to /etc/modules
change eth1 -> wlan0 in the files below:
sudo gedit /etc/modeprobe.d/ndiswrapper
sudo gedit /etc/network/interface
sudo gedit /etc/iftab

I hope this helps a lot of people!

It certainly helped me! Thanks for the good work. Now I just need to revisit the problem with network manager, and see if I can get things changed so that the 802.11g card is seen as 'wlan0'.

If anyone can explain why replacing eth1 with wlan0 in the above three files screws my system, I'm all ears!

Thanks and regards,

Glenn.

---

### Post by ubunturules on 2006-09-06
davidrose_98: obviously you didn't read the whole guide because if you did you would of seen that's also apart of my guide.

---

### Post by GlennB on 2006-09-06
ok, I understand now why I was not able to get the network manager working. I was not aware that nm does not deal with static ip addressing, and since I have DHCP disabled here, it seems I can't use it.

However, for anyone else that has a Broadcom card and uses static ip, be aware that this guide works just fine in Dapper, provided you don't try to use network manager.

My Broadcom 4318 is now seen by Ubuntu as 'eth1' and it's working just fine.

Thanks again for a good howto.

Regards,

Glenn.

---

### Post by yani1shu on 2006-09-06
I followed the guide step by step and am getting this error message. Any help would be appreciated. I am working on a Dell Inspiron 1150 with a BCM4306 wireless card. 


sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

---

### Post by Melcar on 2006-09-07
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

That's the chip I have on my laptop.  This guide worked perfectly at the very first try.  Works even better than doing it the bcm43xx way; I can actually reconnet every time I loose signals (I used to have to reboot before with fwcutter).  Important thing is to follow the guide from begining to end step by step or you will get errors (I used to get the invalid driver error before).

---

### Post by ubunturules on 2006-09-07
yani1shu: I've had this problem before and I've seen a couple of other people saying they've had this problem.  I've searched on google and can't seem to find a fix.  Somebody said they did the following to get it fixed.
```
sudo ndiswrapper -e ndiswrapper.ko
```
```
sudo modprobe ndiswrapper
```
This not the guides fault.
I am still looking for a good fix.

---

### Post by davidrose_98 on 2006-09-07
> **ubunturules said:**
> davidrose_98: obviously you didn't read the whole guide because if you did you would of seen that's also apart of my guide.

I did read the whole guide, numerous times, and you are right, adding the ndiswrapper to /etc/modules is in there, but.... if you don't comment out the auto stuff that has to do with the wlan and the wired lan the gnome-network-manager will not display your network cards because it does not display anything that is loaded via auto in that file (at least that is what the wiki said and that is what I found when I could not get it to display on my pc).

---

### Post by Hemmer on 2006-09-08
Fantastic Guide! Cannot thank you enough for helping get this working!!! :D

---

### Post by saionjik on 2006-09-10
wow im also running a ubuntu 64, and im really mad that i've done what is said under [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)
When i do it with the 64bit drivers, i leave them alone w/o changing the names, and it seems to show hardware present and driver present, when i do "sudo ndiswrapper -l"

But everytime i follow the guild but do it with my drivers,
"
sudo rmmod bcm43xx
sudo gedit /etc/modprobe.d/blacklist
# i add "blacklist bcm43xx" to the bottom
# instead of  "sudo apt-get install ndiswrapper-utils" i put in the cd and install the ndiswrapper 1.8 from the cd on my 64 bit ubuntu

sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf
# i've noticed if i dont put my 64bit drivers close to my /home/ folder (for example "/home/(username)/PUT DRIVERS HERE") I get a line 135 error, so i put "sudo ndiswrapper -i /path to drivers/driver.inf" and terminal installs it while spitting out this code:
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2

sudo ndiswrapper -l (tells me hardware and drivers present)
sudo ndiswrapper -m
sudo modprobe ndiswrapper

I then go to System -> Administration -> Networking and all i see is modem, eth0, eth1 and my OLD eth2 which was my wireless one with the option to input a ESSID name when i click configure disapears and im like WTF!?, so i then go through all these files and change eth2 to wlan0.

"add ndiswrapper to /etc/modules
change eth1 -> wlan0 in the files below:
sudo gedit /etc/modprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab"

I dont have a passworded network so i dont do what else the tutorial says, and i've havent put # in front of the auto, Im just really mad cause i get stuck here and dont know what to do, 
to check my eth's i type "sudo iwconfig" and it pops up the eth's and wlan0 but now everything it says that no device detected or w/e it is that its not there as opposed to when i typed "sudo iwconfig" before the tutorial i followed and "eth2" showed the linksys broadcom 4603 (rev 3). So if anyone could help me thx.

I heard some ppl also used gnome network w/e but i dont know how to get that. everything i try to get offa the http archive of ubutnu instead of "apt-get" command for my 64BIT tells me that it doesnt support "lib6*YATTAYATTAYATTA*" or i386 when its not downloaded for the 64 bit. and if it does say its supported like the FWCUTTER for bcm43xx i press unpack/install and it says failed install, then i try the newer one and it says the unsupported lib6 thing.

---

### Post by ubunturules on 2006-09-10
So what's the problem?

---

### Post by hirev on 2006-09-12
I was trying this guide today and everything went smooth,except untill I got to this step

> 
Go to System -> Administration -> Networking

Go to your eth0 connection and disable the connection.

Now go to your wlan0 connection and enable it.

If you need WPA or WEP encryption do the following:

When I go to the Network settings menu, my Wireless connection disappeared from the list, I cannot continue any further with this guide because i don't have a wlan0 connection to enable.
Any help would be appreciated.

thanks in advance

---

### Post by ubunturules on 2006-09-12
Here's a little trick of the trade.  It might work and it might not work.
```
sudo ndiswrapper -e bcmwl5
```
```
sudo apt-get install ndisgtk
```
```
sudo ndisgtk
```

click Install New Driver
find the driver and click install

once it says driver present, hardware present click on Configure Network
it should work

If it doesn't work keep repeating these steps until it does.

If you don't mind I would like to here back from you to see if it works or not.  Just a little trick I picked up when I couldn't get wlan0 to show up.

---

### Post by hirev on 2006-09-12
Thak you for your feedback.
This is what i get when i try your suggestions.

```
ctr@RS-R3600:~$ sudo ndiswrapper -e bcmwl5
Password:
ctr@RS-R3600:~$ sudo apt-get install ndisgtk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndisgtk
ctr@RS-R3600:~$ sudo ndisgtk
sudo: ndisgtk: command not found
ctr@RS-R3600:~$ sudo ndisgtk
sudo: ndisgtk: command not found
ctr@RS-R3600:~$ sudo apt-get install ndisgtk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndisgtk
ctr@RS-R3600:~$ sudo ndiswrapper -i /home/ctr/bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
ctr@RS-R3600:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
```

I still can't get the Wirelss to show up in the Network settings.
any clues?
thanks

---

### Post by Epperly on 2006-09-12
> **hirev said:**
> I was trying this guide today and everything went smooth,except untill I got to this step



When I go to the Network settings menu, my Wireless connection disappeared from the list, I cannot continue any further with this guide because i don't have a wlan0 connection to enable.
Any help would be appreciated.

thanks in advance

My problem still, too.

---

### Post by Papa-san on 2006-09-12
Is it specifically wireless, or is it because wlan0 isn't the name?

I am using the same card, and I don't have wlan) either. I have eth0 and eth1. Sys > Admin > Network gives me the wireless, but it says it is eth0. I decided not to fight it, and it is running as that. If the wireless issue doesn't show at all, I'm not sure. 

The how to you are using isn't the same as the one in my signature. try those, and see if they help.

Best of luck!

---

### Post by Papa-san on 2006-09-12
> **xXx 0wn3d xXx said:**
> Well I'm using the bcm43xx kernel (2.6.17ck1) module on Archlinux but I tried to get it (Broadcom 4318 + ndiswrapper) to work a long time ago. About 2 months to be exact and it didn't work at all but everything it fine now.

I think this is specific to the 4318 cards. 4306 is a slightly different animal.
BTW, this thread helped me after my upgrade problem, but left me with the eth1 problem you addressed in your edit. I will try these things in the morning! Thanks MUCH!!!

---

### Post by hirev on 2006-09-13
> **Papa-san said:**
> Is it specifically wireless, or is it because wlan0 isn't the name?

I am using the same card, and I don't have wlan) either. I have eth0 and eth1. Sys > Admin > Network gives me the wireless, but it says it is eth0. I decided not to fight it, and it is running as that. If the wireless issue doesn't show at all, I'm not sure. 

The how to you are using isn't the same as the one in my signature. try those, and see if they help.

Best of luck!

It is the Wireless connection that is missing from the Network settings.
I have tried a couple of other guides, but I return with a bunch of errors.

Thank you!

---

### Post by Blumensaadt on 2006-09-13
:-? 
Well i've tried this "how to" since its my first time of running a linux-system.
And, err, well - it doesn't work for me. Now ALL my networkconnections i dead, even the Wire-LAN.

Obviously i can make wintendo work for me - sad but true, so i'm not sure to use linux before there's a working solution that's easy to use for people like me who doens't know how linux works.

I need the wireless connection, and ubuntu sadly don't provide this feature for my Ferrari3200.

Blumensaadt.

---

### Post by sirkamran32 on 2006-09-15
Hey everybody, i followed the HOW TO, step by step.  However, in the end, my internet is still not working.  I do not get a wlan0 interface to select and activate. I only have eth0, which doesnt work. What do I do? Everything works until, the "wlan0" is supposed to appear.  I've been troubleshooting this for hours, finally found this thread, and still not luck! I am extremely frustrated, and i just want to get linux to work, so i can switch over!!! ANY HELP IS  GREATLY APPRECIATED!! THANKS IN ADVANCE!! sigh, its late at night. bye.

---

### Post by Kulgan on 2006-09-15
Very interesting and well explained how-to! 

I got a kick when I saw it - it's exacly what I'm looking for for a desktop that I want over to ubuntu. 

Thanks so much for including that ndiswrapper-utils was on the CD - I have been to thousands of ndiswrapper how-to's and they all just say apt-get or synaptic. 

First problem I had occured when actualliy installing the driver, which is farther than I have ever gotten before :D

You said we need to have both an .inf and a .sys file. I have the .sys file from c:\WINDOWS\system32\drivers\BCMWL5.SYS, but I have no idea where the other one could be. Any ideas?

Thanks for doing a great how-to on the broadcom driver of doom, even if I'm too stupid to find the right files!

E

---

### Post by ubunturules on 2006-09-15
sirkamran32: Try what I said on the last page of this howto.  It might work.  It's a little trick I picked up back in the day.

Kulgan: I am glad you like the howto.  Go to home.nc.rr.com/thehinnants/stuff/drivers and both of them are there.
For the .inf file, copy and paste it in some form of text editor and make sure you save it as bcmwl5.inf
Make sure you have both of them in the same folder too.

---

### Post by Fully216 on 2006-09-15
I use the netbc564 (amd 64bit bcm4306 driver).  You may find it here:

[http://ubuntuforums.org/attachment.php?attachmentid=186&d=1104423377](http://ubuntuforums.org/attachment.php?attachmentid=186&d=1104423377)

You can also use the windows driver found here:

[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

Hope this helps

---

### Post by trifgabi on 2006-09-15
Hi

I'm so new i don't even know how to post a message. I have ubuntu installed on an external usb drive. it works just fine till the wireless card. I have a n inspiron 1505 with the internal wireless card on it. i tried installing the bcmwl with ndiswrapper 1.8 but unsuccesful. then i downloaded ndisgkt and installed the driver with that. it said, hardware is present. the card still doesn't want to work. the wi-fi light is on though, it always was.network controller Broadcom corporation unknown device 4311 when I type lspci

i really need some help, tired to boot windows

---

### Post by jubilee33 on 2006-09-16
Thank you for the wonderful howto.  I have never been so close to getting my wireless connection to work.  Everything well smoothly and the nm-applet (wlan0) already connected and the icon changed into bars.  100% strength, all connected but I can't load any web pages.  It seems that the router sees the laptop and the laptop sees the router but there is no actual Internet connection.  By the way, I can't use System-->Administration-->Networking to connect wlan0.  Any idea what might be wrong?  I have seen other people having the same problem but haven't seen any solution. :confused:

---

### Post by aezell on 2006-09-16
I read the entire thread and still no luck.

I followed the tutorial to the T.

"ndiswrapper -l" gives me a good response.

All of the files and folders that should be around are there.

I changed all the references of eth1 to wlan0 per Tortoro's suggestion.

The Wireless connection shows up in my Networking list.

However, when I "Activate" it, it seems to be thinking and then it will tell me that it is activated, but there is really no connection. If I close the applet and start it again, it reports the connection as deactivated.

The wired connection works fine and can be activated and deactivated at will.

Any ideas? I have checked and double-checked every step. I should mention that this is a VERY fresh install.

---

### Post by Kulgan on 2006-09-16
have you set the correct DNS servers under the DNS tab? Always worth a try double checking :D

---

### Post by aezell on 2006-09-16
Well, since the wireless device never truly activates, I doubt it's the DNS. It's also a DHCP environement meaning the router would provide that at connection time. Since the wired connection works, the DNS servers are set and working. :)

---

### Post by Kulgan on 2006-09-16
hmmm.. I had a weird issue when I was setting up my laptop, though it could be the same with whatever you are working with. I set the properties in the interface "properties" tab... DUH, -> OK -> OK, without activating it, then opened it, switched the location to the one I saved the settings to - in my case "home" - clicked activate and then did not close with OK. Just exit it with the lovely little cross. Even now that I have an internet connection working, I still have to open up the network settings, change location, etc every time I boot. The OK button seems to remove the settings. Probably won't work though as it is incredibly random.

---

### Post by ubunturules on 2006-09-17
What is in your /etc/network/interfaces?

---

### Post by aezell on 2006-09-17
I actually fixed it, but I am now on Fedora Core. The issue seemed to be related to needing a more updated version of ndiswrapper than what is available via yum. I just had to build the latest version for myself and that seemed to fix the issue.

---

### Post by ubunturules on 2006-09-17
Glad to here you got it working.

---

### Post by Brokennails on 2006-09-18
Thank you! This worked like a champ. I had tried ndiswrapper when I installed Suse 10.1 and could not get it to work.... I decided to give Ubuntu a try and am glad I did. Tons faster and I can finally use my Belkin fd57010.


Again thanks.

---

### Post by nrayever on 2006-09-19
let's see if this works

---

### Post by chuckn on 2006-09-19
This is a great forum. I am having trouble getting my wireless up and running after a fresh install.

I'm getting the following--

chuck@chuck-laptop:~$ sudo ndiswrapper -i ~/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
chuck@chuck-laptop:~$ bcmwl5.inf -e
bash: bcmwl5.inf: command not found
chuck@chuck-laptop:~$ bcmwl5 -e
bash: bcmwl5: command not found

What am i doing wrong?

Thanks

---

### Post by Brokennails on 2006-09-19
try :
ndiswrapper -e bcmwl5

That will remove the bcmwl5 inf.

I found that it is easier to do this from a fresh install... make sure ndiswrapper and gcc is installed also.

---

### Post by nrayever on 2006-09-20
holy cow!!! this howto was pretty easy, and works like a charm!! :D :D :D

---

### Post by keno on 2006-09-22
thanks for this tutorial. it is great. i was able to get my wireless up and running without a hitch, and i'm a fresh windows convert.

i do have a situation though. after fixing this from the cd boot, i have decided to go ahead with the install. now this time around i am having trouble getting this up like i did before.

i just installed ndiswrapper. my first attempt at installing the driver was met with this:

my code:
> sudo ndiswrapper -i ~/tmp/startup/bcmwl5.inf

> Installing bcmwl5
couldn't copy /home/kyle/tmp/startup/bcmwl5.inf at usr/sbin/ndiswrapper line 135

now when i try to install it somewhere else it says it is already installed. 

but when i run:

ndiswrapper -l

i get:

Installed ndis drivers:
bcmwl5 invalid driver!

i was not sure where to place the driver files....so maybe that is the issue? i am at a loss here. please help.

---

### Post by keno on 2006-09-22
nevermind. i just looked up a couple to see how to uninstall, and now i got it.

one quick question though. i have it up and running now on eth1...do i have to change it to wlan0? or is the difference purely cosmetic?

thanks...

---

### Post by seismicmike on 2006-09-22
my wireless isn't showing up as wlan0, it's showing up as eth1 and the light on the card is not on

---

### Post by ubunturules on 2006-09-22
If you have your ethernet cord plugged into your computer, unplug it, and then restart your computer.

---

### Post by azidrane on 2006-09-24
Works like a charm (with only a few differences for my system, but they are all different so what they heck)

Thanks for the guide and the link for the correct drivers. Kudo's to you!

---

### Post by azidrane on 2006-09-24
Also, make sure you enable the eth1 connection inside of network manager.
1. Disable the eth0 card
2. Select the eth1 card and then select properties
3. Click on "Enable this connection"
4. Set the "Configuration" box to "DHCP" (presuming that is what your router will be using)
5. Click on ok.
6. Select your eth1 card again and select "Activate"
7. Should be smooth sailing now!

---

### Post by Kulgan on 2006-09-25
I have an odd quirk. After I have activated the card I have to close the window with the cross rather than OK. Stumped me a little in the beginning to find out that this was the problem, but now it is indeed smooth sailing :p

---

### Post by whitegorilla on 2006-10-05
I used this method quite successfully with dapper and then something went wrong.  Not sure what, but wireless no longers works.  I did a fresh install and it just didn't work.  I get the nm applet and wireless is active in the network settings but I get no signal.  
Anyway, I decided I would give Kubuntu Edgy Eft a try (as I had not tried any Kubuntu distro's before) and I quite like it.  Now I know it's beta, but I've read on these forums that ubuntu edgy now works with this broadcom card.  What I was wondering is if anyone here has kubuntu edgy working with the 4306 card and how they did it?

Thanks

---

### Post by Kulgan on 2006-10-05
I would say that since they support it, the procedure would be similar to any old other card - I have an intel. 

presuming your wireless is under eth0 and you use dhcp with wep:

```
$ sudo nano /etc/network/interfaces 

```

edit under eth0 to look like

```

auto eth0
iface eth0 inet dhcp
wireless-essid home
wireless-key <essid, eg 123456789ABCDE. Don't use quotes.>

```

exit and save (ctrl-x -> y -> enter)

then refresh the connection 

```

$ ifdown -a
$ ifup -a

```

and you should be working. At least, that's the way it works for me :P

Let us know if you have any problems!

-K

---

### Post by whitegorilla on 2006-10-05
Thanks I'll give that a go when I get home tonight.

---

### Post by method_lam on 2006-10-05
network manager was installed, but when i type nm-applet nothing happens. 

i followed everything perfectly til the wep key part with network manager.

---

### Post by whitegorilla on 2006-10-06
> **Kulgan said:**
> I would say that since they support it, the procedure would be similar to any old other card - I have an intel. 

presuming your wireless is under eth0 and you use dhcp with wep:

```
$ sudo nano /etc/network/interfaces 

```

edit under eth0 to look like

```

auto eth0
iface eth0 inet dhcp
wireless-essid home
wireless-key A35D121C0AE4F8D33D210EEDC1

```

exit and save (ctrl-x -> y -> enter)

then refresh the connection 

```

$ ifdown -a
$ ifup -a

```

and you should be working. At least, that's the way it works for me :P

Let us know if you have any problems!

-K

Having followed the above I now see my wireless card in my network settings.  My ethernet card is enabled and the wireless card is disabled.  So I disable my ethernet card but for some reason I can't enable my wireless card.  It ticks over for a while, a green tick displays for about a second and then it returns to disabled status.  
Should I be enabling it from the Konsole?

---

### Post by Kulgan on 2006-10-06
Would say to all that the network manager is not the best thing to enable the broadcom card in. If you have installed the driver with ndiswrapper, all you should have to do is enter your information in /etc/network/interfaces and reload all interfaces. 

**whitegorilla:** did you change eth0 to the right interface for you? In many cases it's eth1. Did you have to create the file, or was it there already?

**method_lam**
 	> network manager was installed, but when i type nm-applet nothing happens.

i followed everything perfectly til the wep key part with network manager.
I take it you are on ubuntu, rather than kubuntu? I found that for the how-to, you didn't really need the last few steps unless you wanted a graphical thingy as well. I blacklisted as they do there, installed the driver with ndiswrapper, and did as I said earlier, with editing the /etc/network/interfaces file. 

If you really want to use a manager, try just using the normal "Network settings" box in System -> Administration -> Network. Just when you close it after your wireless interface has supposedly activated, don't use the "ok" button; close it just by exiting.

---

### Post by whitegorilla on 2006-10-06
> **Kulgan said:**
> 
**whitegorilla:** did you change eth0 to the right interface for you? In many cases it's eth1. Did you have to create the file, or was it there already?


Not really sure what you mean.  I'm pretty sure it was eth0 for ethernet and eth1 for wireless.  I followed the instructions at the start of this thread and then what you said earlier, so I'm not aware of creating the file :confused: 

I'm going home now so I'll be able to be more specific, hopefully!

Thanks

---

### Post by ubunturules on 2006-10-06
method_lam: run these 2 commands and tell me what you get.
```
sudo killall NetworkManager
sudo NetworkManager --no-daemon
```

---

### Post by jw824 on 2006-10-06
I am having the same issue as several other users have been having with the wireless not showing up in System>Administration>Networking. When I run ndiswrapper -l it shows the driver installed and hardware present. I don't want to do a clean install, any ideas would be greatly appricated.

---

### Post by nyinge on 2006-10-06
Edit:  Try the following after you get your "ndiswrapper -l" showing "driver present" and "hardware present."

The simplest way that has always worked for me ;) :

-Make sure your router is broadcasting SSID.
-router security (WEP/WPA etc):  OFF
   - just to make life easier for now :)

Note:  Don't forget "sudo" in front of these commands.

1) Insert the ndiswrapper module (if you havn't done so automatically at start up):
```
modprobe ndiswrapper
```

2) Searching your network:  This should display your network, including others'.
```
iwlist wlan0 scan
```

3) Replace YOUR_SSID with your own.  UPPER/lower cases matter!
```
iwconfig wlan0 essid YOUR_SSID
```

4)```
dhclient wlan0
``` to get an address from your DHCP router.

If you're lazy like me, put the following in a file:
```

sudo modprobe ndiswrapper
sudo iwconfig wlan0 essid YOUR_SSID
sudo dhclient wlan0

```
And run it as ```
sudo sh home-wifi
```
"home-wifi" being the name of the file.  See, just 3 simple lines.  :KS 

Ok, post back your results.

---

### Post by jw824 on 2006-10-07
nyinge - that worked great.... I am now going to try it with wep encryption and see if i can get that to work. 

Thanks again

Got it working with the wep too.

---

### Post by ubunturules on 2006-10-09
nm sorry

---

### Post by ubunturules on 2006-10-23
bump

---

### Post by RangerNT on 2006-10-28
> 
```
 sudo apt-get install ndiswrapper-utils
```


I do this and get the following error (after entering password):

```
Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package ndiswrapper-utils
```

Any suggestions? I'm using Ubuntu 6.10 and a newbie to Ubuntu but experienced in Unix/Linux

---

### Post by Kulgan on 2006-10-29
well, the reason that you want this package is presumably that you don't have an internet connection. By default, Ubuntu comes with certain reopsitories disabled, and you can't enable these without an internet connection. If you stick the Ubuntu CD in the comp when it's running Ubuntu, there should be a file somewhere on it called ndiswrapper-utils.deb or something. Just double-click that and it should ask you about an installation. Go along with it and ndiswrapper-utils should be installed on the system. 

-K

---

### Post by ubunturules on 2006-10-29
kulgan is right.

---

### Post by RangerNT on 2006-10-29
My ethernet card is working fine on the laptop and I'm on the Internet now replying to this post so it can't be because I don't have an Internet connection.

---

### Post by Kulgan on 2006-10-30
you could have been using windows to post this, you could have been using wired when you wanted wireless. That's normally why people want ndiswrapper, and you didn't exactly give a different reason...

-K

---

### Post by accel on 2006-10-30
I just did a fresh install of ubuntu 6.10 on my laptop and now I get this error message.
(see below)
Is this because the procedure in post 1 only works for Dapper.
How can I get my Broadcom 4306 (Linksys WPC-54G pcmcia) to do its work
in Edgy?

----------------
 ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

 sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper

 sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
-----------------

---

### Post by ubunturules on 2006-10-30
accel: This howto is for every version of Ubuntu.  I have seen your problem before and I've heard of a couple of people who get this error.  The bad thing is I haven't heard of a good fix for it.  Sorry.  Does anybody know how to fix this problem.  Do another fresh install and it should work.

---

### Post by accel on 2006-10-30
> **ubunturules said:**
>  Does anybody know how to fix this problem.  Do another fresh install and it should work.

Thanks for your reply.
I think I found a fix for my own problem in this thread :) :
[http://ubuntuforums.org/showthread.php?t=284746](http://ubuntuforums.org/showthread.php?t=284746)

As iseebluuue writes here:

He _first_ did this step: 
sudo modprobe ndiswrapper

and _then_ he did: 
sudo ndiswrapper -m

**NOT** first sudo ndiswrapper -m and then sudo modprobe ndiswrapper

ALSO make sure you download the ndiswrapper-utils v1.8 (or higher) from the repositories and do not use those located on your install CD. 

Why this works I don't know, but this does the trick for me. 

Now my Linksys WPC-54G works fine @ full speed in Edgy...

---

### Post by ubunturules on 2006-10-30
That is great.  Thanks for the fix.

---

### Post by meyrd on 2006-10-30
Thank-you..........:) 

It worked and it worked fast.

I sent you a pm with kudos as well!

Compaq r3000 with bcm4306
and it ALL works now, even my mlan with wep128.

Ubuntu is the best and the people who lurk around in this forum are the best as well!

:cool:

---

### Post by Handssolow on 2006-11-03
Eventually I managed an install of Edgy on another PC, now I need some help installing the driver for its Linksys WMP54GS with Broadcom 4306 chipset.

Initially I had a problem finding or accessing ndiswrapper on my install CD but I downloaded and used a memory stick to transfer and install ndiswrapper.
Synaptic now reports I've installed

ndiswrapper-common  installed given as 1.18-lubuntu2
ndiswrapper-source  installed given as 1.18-lubuntu2
ndiswrapper-utils   installed given as 1.1-5
ndiswrapper-utils-1.1  installed given as 1.1-5
ndiswrapper-utils-1.8  installed given as 1.18-lubuntu2

I downloaded the Linksys drivers for my ver 1.1 card. The Driver folder has
WMP54GSa.inf
bcml5a.sys  
WMP54GS.inf 
bcmwl5.sys
I transfered and copied bcmwl5.sys to the other PCs Desktop and copied and renamed WMP54GS.inf file to bcmwl5.inf.

sudo ndiswrapper -i /Desktop/bcmwl5.inf  gives the following line-

couldn't copy/Desktop/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144

I tried the sys and inf files from home.nc.rr.com/thehinnants/stuff/drivers/
but get the same error message when attempting to install this alternative bcmwl5.inf file.
Sudo ndiswrapper -l says my driver is invalid so I have to remove remove it and start again.....

Helpful suggestions appreciated.

---

### Post by Handssolow on 2006-11-03
I started to re-read these posting.
Thanks to "Ubunturules" a suggestion came that loading the graphical interface for ndiswrapper might work.

sudo apt-get install ndisgtk
sudo ndisgtk

But first I had to use my other PC to obtain it. I googled for it, downloaded and transfered it using a memory stick onto Desktop and double clicked to install. Then back to the terminal commands to input the above. I did get however, something like this as a warning-

(ndisgtk:16408): libgnomeeufs-WARNING**. Failure to open session DBUS connection:Did not receive a reply.Possible causes indicate;the remote application did not reply,the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

However over the top the graphical configuration appeared. I navigated to a folder on Desktop where bcmwl5.inf was and was able to install the driver.
sudo ndiswrapper -l reported the driver with no message of it being invalid. 
sudo iwconfig shows I've got a wlan as does the network settings program.

I've made some progress.

Why did I have to use the gui to get ndiswrapper to install bcmwl5.inf?
Is there any significance in the warning messages when I ran ndisgtk?

PS I didn't mean to add any smilies but can't remove them!!

---

### Post by Handssolow on 2006-11-03
Posting from our second PC running Ubuntu at last!!:) 

I just went into sudo /etc/network/interfaces and used the network settings gui partly because I'd forgotten our ESSID was in caps not lower case.

I've only got to sort out the ATI 9600 graphics driver, the Cannon BJ-300 printer and having a dual HD windows PC, and also installing Kubuntu. Oh happy days.

---

### Post by Kulgan on 2006-11-04
good job!

Sounds like you're having fun :D

---

### Post by motang on 2006-11-04
Thank you very much it worked beautifully and it was extremely easy to use.

---

### Post by ubunturules on 2006-11-04
I'm glad to hear that you got it to work!  Just curious...how long have you been working on it before you got to my guide?

---

### Post by Epperly on 2006-11-04
Thank you!! :D I'm so happy it's finally working!

---

### Post by javierfh on 2006-11-05
Hello Ubunturules and others,

i have a SMC2835W card and im trying to make my wireless work.
I have followed your post and well it doesnt work, it is little bit frustrating, so i hope someone can give me some help.
I have found the smc2835w v.2 wireless cardbus adapter driver multiple os and download it.
I have installed ndiswrapper and the driver...everything seemed fine and at some point i saw even the lights flashing couple of times.
These are the things i did

> 
javier@laptoplinux:~/drivers_wlan/SMC2835W$ sudo ndiswrapper -i /home/javier/drivers_wlan/SMC2835W/SMC2835W.inf
Installing smc2835w
javier@laptoplinux:~/drivers_wlan/SMC2835W$ ndiswrapper -l
Installed drivers:
smc2835w                driver installed, hardware present 
javier@laptoplinux:~/drivers_wlan/SMC2835W$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
javier@laptoplinux:~/drivers_wlan/SMC2835W$ sudo modprobe ndiswrapper


And well after that rebooted and nothing worked. 
I then followed the different things you commented in this post and well i have the icon and i can try to switch between wireless and cable network.. but only thing is that nothing happens when i select wireless and after few seconds starts the ui showing the icon moving and then says you are connected to the network(the cable)

So any idea how can i force the card to be alive?
is there anything i could do?

I know maybe you have different cards but if anyone happens to know??


Thanks in advance,

Javi

---

### Post by ubunturules on 2006-11-05
I don't really understand the question but if you have your ethernet cable still plugged in unplug it and restart your computer.

---

### Post by javierfh on 2006-11-06
> **ubunturules said:**
> I don't really understand the question but if you have your ethernet cable still plugged in unplug it and restart your computer.

That doesnt work. I have tried it already.
The problem seem to be with the card, i cant make it work.
Everything else seems to be fine. But funny thing is that same card works perfectly under windows,so card should work fine.
So is there anyway to enable the card so the lights start flashing?
The driver and everything seem to be in place..so i dont understand why still doesnt work.

Javi

---

### Post by Kulgan on 2006-11-06
someone earlier in the thread said that it worked for him to switch around the two commands after installing the driver, making it

```

javier@laptoplinux:~/drivers_wlan/SMC2835W$ sudo modprobe ndiswrapper
javier@laptoplinux:~/drivers_wlan/SMC2835W$ sudo ndiswrapper -m

```

That makes absolutely no sense, but that seemed to work. You never know...

---

### Post by javierfh on 2006-11-06
> **Kulgan said:**
> someone earlier in the thread said that it worked for him to switch around the two commands after installing the driver, making it

```

javier@laptoplinux:~/drivers_wlan/SMC2835W$ sudo modprobe ndiswrapper
javier@laptoplinux:~/drivers_wlan/SMC2835W$ sudo ndiswrapper -m

```

That makes absolutely no sense, but that seemed to work. You never know...

Hello,

well...didnt work... :D i tried...but didnt work, to be honest im desperated with that thing.

Javi

---

### Post by Kulgan on 2006-11-06
well, I really am sorry to hear that. :-k 

I have no idea either - but then I'm not excatly what you call a pro...

---

### Post by GMUDuckman on 2006-11-06
First off... thank you ubunturules and everyone else on this thread! My wireless WAS working like a charm after i did this tutorial! HOWEVER, my wireless no longer works. I'm pretty sure i know the incident that made it stop working and I'm positive I have no idea why it happened or what to do about it.  The wireless stopped working after I plugged my computer in to the internet via ethernet port at work. Ever since then I have been unable to connect to wireless again. The closest I get is the little orb at the bottom of nm-applet turns green.  Please someone help me. I know you all are whizzes! Help me out! If I don't figure this out I might have to go back to windows :-( on my laptop.

I am using ndiswrapper 1.8 (thats the only way I was able to get it working)

-Marc

---

### Post by Kulgan on 2006-11-06
tried editing /etc/network/interfaces rather than doing it from the applet?

as far as I know that should do it so long as there is a WEP involved...

---

### Post by RaYdOg on 2006-11-06
> I transfered and copied bcmwl5.sys to the other PCs Desktop and copied and renamed WMP54GS.inf file to bcmwl5.inf.

sudo ndiswrapper -i /Desktop/bcmwl5.inf gives the following line-

couldn't copy/Desktop/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144


Shouldn't that command be:
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
NOTE: The tilde before Desktop, because Desktop is in your home directory. I may be wrong, I am kinda new to Linux.

---

### Post by Kulgan on 2006-11-06
oh right, well spotted! 

/Desktop would mean that you had a folder in the top directory called Desktop... Might help](*,)

---

### Post by GMUDuckman on 2006-11-06
> **Kulgan said:**
> tried editing /etc/network/interfaces rather than doing it from the applet?

as far as I know that should do it so long as there is a WEP involved...

The networks I'm trying to connect to are not secured.... Everything was working fine until i connected VIA ethernet... then something went screwy. So i'm sad.](*,) :(

Edit: I dunno if is has anything to do with anything... when checked the version of NDISwrapper. It was 1.22... I used 1.18 to get my wireless working. But i wouldnt think getting a NEWER version of the program would mess things up...

---

### Post by ubunturules on 2006-11-06
Alright it shouldn't be that hard to diagnose the problem.

First post your /etc/network/interfaces:

```
sudo gedit /etc/network/interfaces
```

Second run these commands:

```
sudo killall NetworkManager
```

```
sudo NetworkManager --no-daemon
```

tell me what the output of those that command gives you.

---

### Post by GMUDuckman on 2006-11-06
My interfaces looks no different than it did before
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```
Then when i did you commands
```
marc@marc:~$ sudo NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <information>   wlan0: Device is fully-supported using driver 'ndiswrapper'.
NetworkManager: <information>   nm_device_init(): waiting for device's worker thread to start
NetworkManager: <information>   nm_device_init(): device's worker thread started, continuing.
NetworkManager: <information>   Now managing wireless (802.11) device 'wlan0'.
NetworkManager: <information>   Deactivating device wlan0.
NetworkManager: <information>   eth0: Device is fully-supported using driver 'natsemi'.
NetworkManager: <information>   nm_device_init(): waiting for device's worker thread to start
NetworkManager: <information>   nm_device_init(): device's worker thread started, continuing.
NetworkManager: <information>   Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <information>   Deactivating device eth0.
NetworkManager: <information>   Updating allowed wireless network lists.

```

And it just stopped there so i tried connecting to a wireless netowork
and that output was way to long to post... so i attached it... hope it works.

you might have to get rid of the bz2 ending... i had to figure out how to get past the file size limit.](*,)

---

### Post by GMUDuckman on 2006-11-07
Any ideas anyone? I've been searching and searching and nothing](*,)

---

### Post by Kulgan on 2006-11-07
is that really your whole interfaces file?

It should at least say SOMETHING about the wired connection...

---

### Post by GMUDuckman on 2006-11-07
> **Kulgan said:**
> is that really your whole interfaces file?

It should at least say SOMETHING about the wired connection...

According to everything I've read about network manager... the interfaces needs to be like that so that network-manager can take care of the card itself.
and as you can see in the beginning of the tutorial here it says

"```

sudo gedit /etc/network/interfaces
```
Comment out anything in there at the bottom that has to do with your wireless essid. When I say comment out that means but a # in from of it. You can leave all of the lo, inet, and auto stuff."

However I haven't touched the interfaces since i finished this tutorial. Like I said the only I have done to my computer since I got wireless working was:
1) Install beryl
2) Connect to an ethernet port (thats when stuff went haywire)
Thats all my interfaces had in the file to begin with..

If you think putting something in there about my network would help please tell me what to put in there. But from what I've read from your previous post you aren't much of a network-manager enthusiast. :-(

---

### Post by Kulgan on 2006-11-07
for me, all I had to do was put in:

```

auto eth1
iface eth1 inet dhcp
wireless-essid home
wireless-key <ESSID KEY>

```

I use DHCP and 128-bit WEP.

I have not found a way to get that working without WEP, when I'm in places that don't use such things, but in the manager you have to switch to "Plain Text" even if you leave it blank, so I'm guessing that it would be something like:

```

auto eth1
iface eth1 inet dhcp
wireless-essid home
wireless-key s:

```

I wouldn't go ahead and do this before someone a little more knowledgable agrees or amends it...

-K

---

### Post by GMUDuckman on 2006-11-07
See my problem is that most of the time I'm on a unsecure wireless network, but then sometimes I have to go on a secure one, then sometimes I have to connect via ethernet due to lack of wireless. So i was hoping if I got network manager working it would do all 3 for me... which it did, or so i thought. Aparently connecting via ethernet messes up wireless cards in linux? :-(

---

### Post by Kulgan on 2006-11-07
they shouldn't... 

I use the default manager for ethernet and unsecured networks, and /etc/network/interfaces + ifdown -a/ifup -a for secured wireless networks. And it all worked fine after I had set it up. Which was a little confusing. 

I must admit that the computer I am using the Broadcom 4306 on is really slow for some reason - Ubuntu doesn't like Compaq? Also, for some reason I have to restart the network after every boot - as if it doesn't save the settings. 

What I find odd is that after it connects to the network, if I close the manager box by clicking "ok", it screws up. Oh well, none of this is relevant...

---

### Post by GMUDuckman on 2006-11-07
Well i have some good news! i got my wireless working again! All I did was went int omy interfaces then i put in
```

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp
```
underneath my
```

auto lo
iface lo inet loopback
```

seems to be working again! lets see how long it lasts!:mrgreen:

TY Mr. Kulgan for giving me the idea for adding that stuff

---

### Post by Kulgan on 2006-11-07
great!

people tell me that it's this kind of thing that puts people off linux... IMO, no pop-ups is worth the "price"...

---

### Post by GMUDuckman on 2006-11-07
> **Kulgan said:**
> great!

people tell me that it's this kind of thing that puts people off linux... IMO, no pop-ups is worth the "price"...

Still doesn't make much sense that you have to download network-manager in order to have any real wireless network activity.  You'd figure they would incorporate it into ubuntu and try to make wireless as user friendly as possible since it seems wireless is the way society is moving towards now-a-days

---

### Post by ubunturules on 2006-11-07
I'm glad you were got it working! I was just about to sugest the fix you found but I'm glad you got it working yourself.

---

### Post by RaYdOg on 2006-11-07
I had some spare time the other day, and I converted this thread into a shell script. It worked on my computer, which is using a fresh install of Ubuntu 6.10 32bit, and has a Broadcom 4306 rev 3. Try using the bcmwl5.inf file in this file: [http://www.silfreed.net/download/hpzt3000cto/SP23107A.tar.gz](http://www.silfreed.net/download/hpzt3000cto/SP23107A.tar.gz)

Hope this helps...

---

### Post by GMUDuckman on 2006-11-07
So it turns out my fix only worked for my wireless network at home. I still can't connect to the wireless at school. And I know its possible because it was working before. So I have no idea what is up. This is making me sad.
Edit: I came home after class and it still connected to my home network... so I don't know what the deal is... its just making me muy sad!

---

### Post by Kulgan on 2006-11-08
does the network at your school have encryption?

@RaYdOg: Nice! That will probably help quite a few of the new people figure their way through the thread :D

---

### Post by GMUDuckman on 2006-11-08
> **Kulgan said:**
> does the network at your school have encryption?

@RaYdOg: Nice! That will probably help quite a few of the new people figure their way through the thread :D

No, How it works is its an open network however in order to get internet access through the network you have to login via your webbrowser.  Meaning when you open your webbrowser it automatically redirects you to the wireless loging page. If you don't log in you cannot use the internet. However this does not explain why I can't even connect to the network, since it is an unsecured network.  It was working before too, i was able to connect and it would take me to the login page. So I really don't know what the deal is. When I am back at school i will run the nm-applet no-daemon and send you the output.

---

### Post by ubunturules on 2006-11-08
GMUDuckman: Run it while you're trying to connect to your school network because that is the error message we're looking for.  When you run it using your home network according to you it connects fine so you won't get any error messages.

RaYdOg:  This is some good stuff.  I tried it out and it seems to have some problems.  I can't try to fix them right now because I have got to go somewhere.  It seems to start running into problems when it is trying to install ndiswrapper.  It blacklisted the driver perfectly but after that is begins to run into some problems.  If we can fix this I will defenatly post it on the guide as an alternative to getting it to work.

---

### Post by darthchaosofrspw on 2006-11-09
> **ubunturules said:**
> did this HOWTO help anyone?

Works for me!

---

### Post by ubunturules on 2006-11-09
I'm glad to hear that you got it to work!

---

### Post by Max Velocity on 2006-11-09
Hey guys got a bit of a problem, the whole install went fine until the very last line :s 

Here's what I ended up with

adam@Project-Stealth:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

Anyone know how I can solve this?
Thanks.

---

### Post by GMUDuckman on 2006-11-09
[QUOTE=ubunturules]GMUDuckman: Run it while you're trying to connect to your school network because that is the error message we're looking for.  When you run it using your home network according to you it connects fine so you won't get any error messages.
[/QUOTE]
Well i did the output but for some reason i keep getting errors when trying to upload it... so I posted it on my personal webspace.
[Here is a link to it]("http://members.cox.net/marckotwicki/Trying%20to%20Connect%20to%20GMU.bz2")

This is the out put i got when I tried to connect to the network that I cannot connect to. Maybe it has something to do with multiple access points using the same SSID? I have another friend running ubuntu and he connects fine so I dont think that explains it. Thanks for all the help by the waY!!!

---

### Post by RaYdOg on 2006-11-10
> **Max Velocity said:**
> Hey guys got a bit of a problem, the whole install went fine until the very last line :s 

Here's what I ended up with

adam@Project-Stealth:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

Anyone know how I can solve this?
Thanks.

This is usually because your ndiswrapper kernel module, and the ndiswrapper tool you just used are different versions. Get a more recent one by typing:
```
sudo apt-get install ndiswrapper-utils-1.8
```
Then try modprobe-ing again. Best of luck!

---

### Post by GMUDuckman on 2006-11-11
> **GMUDuckman said:**
> Well i did the output but for some reason i keep getting errors when trying to upload it... so I posted it on my personal webspace.
[Here is a link to it]("http://members.cox.net/marckotwicki/Trying%20to%20Connect%20to%20GMU.bz2")

This is the out put i got when I tried to connect to the network that I cannot connect to. Maybe it has something to do with multiple access points using the same SSID? I have another friend running ubuntu and he connects fine so I dont think that explains it. Thanks for all the help by the waY!!!

Any takers? LOL I've been trying to fix it but in all honesty I have no idea where to begin!](*,)

---

### Post by Kulgan on 2006-11-11
Aren't there a couple files in the original tut that you have to change the "eth0" or "eth1" to "wlan0" or something like that? It looks like there is some confusion between the two... you might want to go through and check a couple of them...

---

### Post by GMUDuckman on 2006-11-11
> **Kulgan said:**
> Aren't there a couple files in the original tut that you have to change the "eth0" or "eth1" to "wlan0" or something like that? It looks like there is some confusion between the two... you might want to go through and check a couple of them...

eth0 is my wired connection
wlan0 is my wireless connection

wlan0 used to be eth1 but I changed it in interfaces and iftab... i haven't come across any other files that need to have it changed in any threads.  The weird thing is that I can connect fine at my house (unsecured, not broadcasting SSID) but I can't connect as my university's (unsecure, broadcasting SSID).  I'm gonna try to contact the university's tech people but I don't think they will be much help...

---

### Post by n0c on 2006-11-11
Thank you *ubunturules* for the info!

I was having no luck installing my Microsoft MN-730 card with the bcmwl5.inf file. After trying many times, I used the inf file that was on the MS driver disc, following all the steps, everything worked like a charm! Took me a long time to figure it out lol.

So if you can't get your card working using bcmwl5.inf and you have your original driver disc for your wlan card, try the inf file in that disc. I am sure someone said this earlier in the thread but it's worth repeating. :)

Thanks again and ubuntu is great!

---

### Post by Kulgan on 2006-11-12
> **GMUDuckman said:**
> eth0 is my wired connection
wlan0 is my wireless connection

wlan0 used to be eth1 but I changed it in interfaces and iftab... i haven't come across any other files that need to have it changed in any threads.  The weird thing is that I can connect fine at my house (unsecured, not broadcasting SSID) but I can't connect as my university's (unsecure, broadcasting SSID).  I'm gonna try to contact the university's tech people but I don't think they will be much help...

hmm.. they might be able to point you to something - are they very M$ified?

---

### Post by rockorager on 2006-11-12
Alright I followed the tutorial, didn't work.  Reinstalled Dapper, followed tutorial, everything went fine.  wlan0 doesn't show up in Networking, I changed it all to wlan0 as is stated in the tutorial, but it doesn't seem to be working.

What should I do?

---

### Post by Kulgan on 2006-11-12
does the network itself work?

---

### Post by ubunturules on 2006-11-14
Restart your computer.

what does your sudo gedit /etc/network/interfaces have in it.
```
sudo gedit /etc/network/interfaces
```

---

### Post by Novek on 2006-11-15
so... i've followed many howto's... my light has turned on, and things seems to work... but i cant set my essid, and i cant scan for networks... 

in my iwconfig my wireless card is listed as eth1.. Does this have to be changed to wlan0 to work, or is this step just a personal option for naming? 

thanx

---

### Post by GMUDuckman on 2006-11-15
> **Novek said:**
> so... i've followed many howto's... my light has turned on, and things seems to work... but i cant set my essid, and i cant scan for networks... 

in my iwconfig my wireless card is listed as eth1.. Does this have to be changed to wlan0 to work, or is this step just a personal option for naming? 

thanx

The naming part is sposed to be optional, HOWEVER mine actually didn't work until I did this step. Now it works fine (except at my school ](*,) )

---

### Post by Kulgan on 2006-11-15
ubuntu does not automatically scan for networks. You have to either enter the information in "System -> Administration -> Networking -> *Select wireless interface* -> Properties" or use the terminal:

```

$ sudo -s
<root pass>
gedit /etc/network/interfaces
<enter correct data under the correct info>
<save>
<exit>
ifdown -a
ifup -a

```and it should be working. 

About the "correct data under correct interface", if your wireless card is listed as eth1, there should be a section that says

```

auto eth1

```

or possibly

```

auto eth1
iface eth1 inet dhcp

```

This assumes you have DHCP enabled. 

Under this section you have to enter the wireless details. 
For me, that section looks like
```

auto eth1
iface eth1 inet dhcp
wireless-essid home
wireless-key **************************

```

where *x26 is my WEP key in hex. If you mormally type your WEP in as a normal phrase, rather than hex, that line would become 

```

wireless-key s: <phrase>

```

if you use static settings, it would resemble

```

auto eth1
iface eth1 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

Hope that helps.
-K

---

### Post by Kulgan on 2006-11-15
GMUDuckman:

One way I could connect to non-secured wireless networks easily from my laptop (which does not use the Broadcom 4306 chipset) was with wifi-radar (it's in the synaptic repos), but according to some, that messes up the whole ndiswrapper stuff. I don't know if you are willing to risk starting for scratch...

---

### Post by GMUDuckman on 2006-11-15
> **Kulgan said:**
> GMUDuckman:

One way I could connect to non-secured wireless networks easily from my laptop (which does not use the Broadcom 4306 chipset) was with wifi-radar (it's in the synaptic repos), but according to some, that messes up the whole ndiswrapper stuff. I don't know if you are willing to risk starting for scratch...

Actually I figured out I am able to connect with /etc/network/interfaces, its just a pain in the butt cause I have to change it everytime I come home or go to school since this option doesn't save which network you want. I just want network manager to work for it all.  Wifi-radar was the one of the things I tried before I found this tutorial. I couldn't to get it to work. Its just really confusing why I can connect at home via network-manager but not at school. If anything I would think it would be the other way around since my home router doesn't even broadcast the SSID and GMU does.  I actually compared my output to my friend's output at school, my network-manager screws up and throws an Invalid Arguement at spots that his does not, it looks like it has something to do with wpa-supplicant that network-manager uses. So i tried changing the timeout on wpa-supplicant since my friend's was 10 seconds and mine was 5. it didn't work. I have no idea what to do haha. guess I'll just have to do it the difficult way until someone comes out with a fix!

---

### Post by Kulgan on 2006-11-15
you say you tried wifi-radar BEFORE you tried this tutorial? Well then it obviously wouldn't work if you don't have the drivers installed. I think it would be worth a try just to see if anything at all has changed.

---

### Post by GMUDuckman on 2006-11-15
Can i use both wifi radar and network manager? I still need WAP capabilities for my girlfriend's house.  Or does wifi-radar do WAP too?  If I still have to switch between the 2 then its basically the same thing I have going on now which is editing the interfaces :-(  Linux needs to work on getting wireless working better!

---

### Post by Kulgan on 2006-11-15
WAP? isn't that for mobile phones...

you can do wep with wifi-radar, but it worked best for me without. I go alot of places that might have an unsecured network, and wifi-radar is usually good for that. You should be able to use both at the same time.

---

### Post by mckatch on 2006-11-16
I have done m best to self solve this problem - this thread has given me alot of hope but alas it seems to elude me.

I am using a Belkin wireless device on my toshiba laptop. (F5D7010)

As I follow the  procedure as outlined on this thread it all starts well - the card is identified as per example (Broadcom 4306).

I downloaded the drivers from the site suggested and put them on the desktop of the machine, I work through the list to the point of having to use the ndis wrapper with the driver, till this point all is good.

On using the wrapper I get a message seeming to say its installed but saying the bcml5.sys is an invalid driver.

If I use -l it tells me:

> Installed ndis drivers:
bcw5    invalid driver!


If I try and uninstal this driver it tells me it is not installed?

I am at a loss. Any suggestions appreciated.

Machine Toshiba Satellite 1800-400
OS Ubuntu 6.1

Problem solved with a little more digging and help from another Howto - 

Found the driver I had wasn't the one I needed - popped over to the ndiswrapper site and got the driver they suggested for my card and once that was achieved and clean install later and it is up and running.

Now to secure it but thats a job for another day...

---

### Post by ubunturules on 2006-11-16
Make sure both drivers are in the same place.

run
```
sudo ndiswrapper -e bcmwl5
```

then run
```
sudo ndiswrapper -i bcmwl5.inf
```

then
```
sudo ndiswrapper -l
```

---

### Post by ubunturules on 2006-11-19
did this work for you?

---

### Post by jazzevan on 2006-11-23
okay, so.
i've used linux before, but that was with a wired, ethernet connection. 
i have a wireless network now, and i have **no** idea how to use ndiswrapper, how to figure out what kind of drivers i have, etc. 
i'm useless, basically. (:
could i have some help? i have the linksys wmp54g pci adapter, and hopefully a broadcom chipset.

evan.

---

### Post by GMUDuckman on 2006-11-24
dude, read the very first post in this thread. It walks you through it step by step.

---

### Post by Kulgan on 2006-11-24
I think I had the same card. Got it when you bought a linksys wireless g/b router?

This thread is actually discussing a how-to, so post 1 will get you most of what you need. If you have any problems, we'll be willing to help.

---

### Post by yojimbosteel on 2006-11-26
I tried your guide and got stuck at the, sudo modprobe ndiswrapper.
This is what it gave me:

usagi@tiger-lt:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

I am running edgy.

---

### Post by hdavid on 2006-11-27
This is usually because your ndiswrapper kernel module, and the ndiswrapper tool you just used are different versions. Get a more recent one by typing:
Code:

sudo apt-get install ndiswrapper-utils-1.8

Then try modprobe-ing again. Best of luck!

-----
raidog wrote this on site 27.i hope it helps.

---

### Post by Kulgan on 2006-11-27
presuming that the whole issue is lack of wireless, apt won't help much...

---

### Post by ubunturules on 2006-11-29
yojimbosteel: hdavid's fix usually works for this problem. hope it works.

---

### Post by GMUDuckman on 2006-11-29
> **Kulgan said:**
> presuming that the whole issue is lack of wireless, apt won't help much...

Well said, apt and aptitude require internet access (except if the package is on the edgy cd)  but this whole tutorial is actually fairly simple to do OFF LINE as long as you have a computer with internet access and a jump drive. Thats how I did it! :p all you gotta do is manually download the packages! BAM!

---

### Post by woopud on 2006-12-02
Well, I did everything according to the first post and got this:

woopud@woopud-laptop:~$ sudo ndiswrapper -i /woopud/80211g/bcmwl5.inf
Password:
bcmwl5 is already installed. Use -e to remove it
woopud@woopud-laptop:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
woopud@woopud-laptop:~$ 

What's wrong here ?
Bert

---

### Post by Kulgan on 2006-12-03
do you have bcmwl5.sys in the same directory? I HAS to be in a subfolder of you home dir.

---

### Post by woopud on 2006-12-03
Yes that file is in the same directory.  I have to mention that I have the 2.6.17 kernel if that matters ?

Bert

---

### Post by ubunturules on 2006-12-03
Did you use the drivers from the first post?

---

### Post by woopud on 2006-12-03
Okay, so I removed all three drivers and started over. Got the drivers from the first post and put them in a folder named "wifi" and put that in my 'home' folder named "woopud" then i did this:

woopud@woopud-laptop:~$ sudo rm -r /etc/ndiswrapper/bcmwl5
woopud@woopud-laptop:~$ sudo ndiswrapper -i ~/woopud/wifi/bcmwl5.inf
Installing bcmwl5
couldn't copy /home/woopud/woopud/wifi/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144.
woopud@woopud-laptop:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5 invalid driver!
woopud@woopud-laptop:~$

---

### Post by woopud on 2006-12-03
I see what I did wrong now, right driver is installed now but wireless won't come on and the adapter is not seen in System-Administration-Networking

---

### Post by Kulgan on 2006-12-03
edit /etc/network/interfaces to display the right information, then reload the interfaces with 

```
$ ifdown -a
$ ifup -a
```

---

### Post by woopud on 2006-12-03
Would you mind explaining a little more ?
You want me to edit the /etc/network/interfaces and add the two lines ?

The wireless light does come on now but the wireless adapter still doesn't show up.

Bert

---

### Post by Kulgan on 2006-12-03
and still no internet connection, I take it?

What I meant about the /etc/network/interfaces file is that that is the place that data concerning wireless setup is stored. 

it should be in sections, looking like:
```
auto eth1
iface eth1 inet dhcp

```

or something, a section for each interface. Don't ask me what interface it is that you need - if it doesn't appear in the network manager, then it is supposedly the one that doesn't, so if it is eth0 that appears, you should apply this to eth1 and vice versa. 

You have to edit it to suit your needs - my wireless interface is eth0, and looks like:

```
auto eth1
iface eth1 inet dhcp
wireless-essid home
wireless-key <LONG WEP KEY>
```

I have DHCP enabled with WEP protection. It is discouraged to use the plain-text format for the WEP key, but if you do, change that line to 
"wireless-key s: <WEP KEY>".

if you don't use DHCP, it is something like 

```

auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0

```

or something - that will depend on your settings. 

Then issue the other two commands in the terminal, one after the other. At some point in the second, it should slow down suddenly, and you see it sending DHCP requests (if that's what you are using, of course) on the interface to which you added the above lines. ifdown -a just means to stop all network interfaces, and ifup -a just means to put them all up again. 

presuming that things go well, you can verify the connection by typing "ifconfig" in the terminal to check the connection, and "iwconfig" to verify the wireless part of it. 

Hope that helps a wee bit

---

### Post by woopud on 2006-12-03
This is what mine looks like:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0
```

Bert

---

### Post by Kulgan on 2006-12-04
that looks about the way it should at the start. 
What is the name of the interface that appears in the network-manager thing?

---

### Post by woopud on 2006-12-04
Are you talking about the networkmanager or the thing under System>Administration>Networking ?  It only shows the wired ethernet connection and the modem and the network applet only show l0

Bert

---

### Post by crazybrit4967 on 2006-12-04
Hi everybody!

I've been using Ubuntu for a few months now, and one of the things that has kept me from using it as my primary OS is not being able to connect to the internet properly. See, I have a Microsoft MN-730 wireless card (it's a Broadcom chipset, apparently), which isn't supported by Ubuntu. I tried using bwm43xx-fwcutter for a while, but the connection was too slow and sometimes didn't work. So I decided to try using ndiswrapper - here's what I did so far:

    * Installed Ubuntu Edgy
    * Installed ndiswrapper-utils-1.8
    * sudo ndiswrapper -i (driver path)/mn-720.inf (note - I used this instead of the standard bcmwl5.inf at the suggestion of n0c on page 28 - it's the driver from the CD that came with the card).
    * sudo ndiswrapper -m
    * sudo modprobe ndiswrapper
    * sudo gedit /etc/modprobe.d/blacklist - added "blacklist bcm43xx" to the end
    * sudo gedit /etc/modeprobe.d/ndiswrapper - changed eth1 (the name of the wireless interface when I was using fwcutter) wlan0
    * gksudo gedit /etc/modules - added "ndiswrapper" to the bottom


Then I set everything up correctly in System>Administration>Networking and, surprisingly, the web still doesn't work. Anyone know what's going on? Please?

---

### Post by technodigifreak on 2006-12-04
Worked for me.  Thanks for the how-to!

---

### Post by foxy123 on 2006-12-05
> **crazybrit4967 said:**
> Hi everybody!

I've been using Ubuntu for a few months now, and one of the things that has kept me from using it as my primary OS is not being able to connect to the internet properly. See, I have a Microsoft MN-730 wireless card (it's a Broadcom chipset, apparently), which isn't supported by Ubuntu. I tried using bwm43xx-fwcutter for a while, but the connection was too slow and sometimes didn't work. So I decided to try using ndiswrapper - here's what I did so far:

    * Installed Ubuntu Edgy
    * Installed ndiswrapper-utils-1.8
    * sudo ndiswrapper -i (driver path)/mn-720.inf (note - I used this instead of the standard bcmwl5.inf at the suggestion of n0c on page 28 - it's the driver from the CD that came with the card).
    * sudo ndiswrapper -m
    * sudo modprobe ndiswrapper
    * sudo gedit /etc/modprobe.d/blacklist - added "blacklist bcm43xx" to the end
    * sudo gedit /etc/modeprobe.d/ndiswrapper - changed eth1 (the name of the wireless interface when I was using fwcutter) wlan0
    * gksudo gedit /etc/modules - added "ndiswrapper" to the bottom


Then I set everything up correctly in System>Administration>Networking and, surprisingly, the web still doesn't work. Anyone know what's going on? Please?

is the network working?

---

### Post by Kulgan on 2006-12-05
**woopud & crazybrit4967**:[INDENT]As far as I know, both of you are suffering the same problem - inconsistencies with the GUI vs. terminal. I strongly recommend the terminal method of setting up the connection, as it is permanent, and you **can see what goes wrong**.[/INDENT]




woopud:
What is the ethernet connection called (in System -> Administration -> Networking)? eth0 or eth1? 

crazybrit4967:
If you follow one of my previous posts, you will get the solution. It is the one that I posted at 10:30PM on Dec. 4. That should enable your connection. As always, ask if you encounter anything....

-K

---

### Post by crazybrit4967 on 2006-12-05
Foxy: I can'tconnect to the internet at all, if that's what you mean.

Kulgan:thanks for the tip.  For the record, I sometimes use the command line to connect (if you mean setting it up in /etc/network/interfaces and then using ifup and ifdown), and I didn't notice any inconsistencies.  I'll try it again, though, and report my findings in a bit.


Edit - I tried it again and it didn't work.  As far as inconsistencies go, there shouldn't really be any; I changed the name of my old wireless interface (eth1) to wlan0 in /etc/iftab, because that's what ndiswrapper added to the configuration file (/etc/modprobe.d/ndiswrapper, if I remember correctly) when I used ndiswrapper -m.  Also, in /etc/network/interfaces, my essid and wireless key are under wlan0 as well. What other inconsistencies could there be?

---

### Post by Kulgan on 2006-12-06
I have no idea :-k

---

### Post by Kulgan on 2006-12-06
I have no idea :-k

--
Sorry double post

---

### Post by ubunturules on 2006-12-06
crazybrit4967: Let me see your /etc/network/interfaces.
Are you trying to use network-manager?

---

### Post by trubblemaker on 2006-12-06
crazybrit4967: while your at it can you post 
```

dmesg | grep ndis
iwlist scan
iwconfig
ifconfig

```

---

### Post by crazybrit4967 on 2006-12-06
Ubunturules - no, I'm not using network-manager.  I would, but I can't get onto the web to install it.

I'll post the other stuff in a sec.

---

### Post by crazybrit4967 on 2006-12-06
Okay then:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid **********
wireless-key **********
```

```
ed@ed-desktop:~$ dmesg | grep ndis
[17179588.804000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179588.896000] ndiswrapper: driver mn720 (Microsoft,07/07/2003, 3.20.26.0) loaded
[17179588.904000] ndiswrapper: using irq 209
ed@ed-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:15:05:23:48:95
                    ESSID:"**********"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-54 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mbnew file/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

sit0      Interface doesn't support scanning.

ed@ed-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2432 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ed@ed-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:6C:5E:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9876 (9.6 KiB)  TX bytes:9876 (9.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0D:3A:6E:79:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Memory:e6000000-e6002000 
```

---

### Post by trubblemaker on 2006-12-06
> **crazybrit4967 said:**
> Okay then:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid **********
wireless-key **********
```


ok so from here we go like this:

have you connected without encryption? (remember the K.I.S.S)
your dirver is loading fine, and it's seeing the networks.
See if try to connect without encryption, 

once you can do that we know that the driver is working properly.

On an un-encrypted network.
```
sudo iconfig wlan0 essid any
sudo dhclient wlan0
```
would work like a charm.  Don't use ifup/ifdown unless you want to connect to the network in /etc/network/infterfaces 

lets say you where at a coffee shop and wanted to connect the above `dhclient` method would work via commandline.

once we know you can connect and it's not a encryption issue then we can add encryption back in and see if that's your issue.

---

### Post by crazybrit4967 on 2006-12-06
I'm not sure if I'm going to be able to do that, since I'm not exactly in charge of the wireless network in my house (meaning I can't just turn the WEP off)  One thing I noticed, though, is that when I use ifup, it only ever says DHCPDISCOVER - never DHCPREQUEST or DHCPOFFER or anything like that.


Edit - also, ifconfig keeps returning "hostname lookup failure".

---

### Post by trubblemaker on 2006-12-06
no worries just go out to a wireless cafe, where you get a free signal and see if you can connect.  (Fatport locations will be good enought to use without logging in or paying.  They're unencryted, aand good enough for the testing we need to do.)  It's alot harder when you can't  remove that hurdle. 

I would triple check the key then and then I'd learn the manual commandline way of logging in to enrypted network.  I don't think its a badly setup driver.   It looks perfect, it sees the network.  I think that the encryption is doing it's job and stopping you from logging on without a perfect setup to be honest.

---

### Post by trubblemaker on 2006-12-06
> Edit - also, ifconfig keeps returning "hostname lookup failure".

show me what you mean post the output.

---

### Post by crazybrit4967 on 2006-12-06
I'm pretty sure those were the exact words, but I'm pretty sure that's irrelevant anyway because that's ifconfig, not iwconfig.  iwconfig works fine, only I still keep just getting DHCPDISCOVER from ifup or dhclient. Any idea why that might be?

---

### Post by trubblemaker on 2006-12-06
the encryption.  I'm not down with my encryption commans but i"m pretty sure that's why your not getting connected.  man iwconfig to checkout all the commands and search the forum for howto connect I'm sure it's been posted a million times over.

---

### Post by crazybrit4967 on 2006-12-06
Actually, I just disabled WEP and it's still the same.  It seems like the problem is that it isn't sending out DHCPREQUESTS.  Anyway, though, thanks for your help so far.  I'd pretty much be completely stuck without you.

---

### Post by trubblemaker on 2006-12-06
ok so do this for me

use 'any' or the essid where i say 'any' run the following for me

```

dmesg
iwconfig
sudo iwonfig wlan0 essid any
iwconfig

```
if it assoctiates then  skip the next instruction ('ap any')
```

sudo sudo iwonfig wlan0 ap any
iwconfig
sudo dhclient wlan0
dmesg

```
just give me the last 10 lines of dmesg when poeting.

---

### Post by pdg777 on 2006-12-07
thanks but all set

---

### Post by pdg777 on 2006-12-07
this seems like the best guide I have seen but things end bad.  see the fatal error message below:

phil@nz-degrevep-2:~$ **lspci | grep Broadcom\ Corporation**
0000:09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0000:0c:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
phil@nz-degrevep-2:~$
phil@nz-degrevep-2:~$
phil@nz-degrevep-2:~$ **sudo rmmod bcm43xx**
ERROR: Module bcm43xx does not exist in /proc/modules
phil@nz-degrevep-2:~$
phil@nz-degrevep-2:~$
phil@nz-degrevep-2:~$  **sudo cat  /etc/modprobe.d/blacklist**
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

#added to get wireless working on 620
**blacklist bcm43xx.ko**



phil@nz-degrevep-2:~$
phil@nz-degrevep-2:~$
phil@nz-degrevep-2:~$ **sudo apt-get install ndiswrapper-utils**
Reading package lists... Done
Building dependency tree... Done
ndiswrapper-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 96 not upgraded.
phil@nz-degrevep-2:~$
phil@nz-degrevep-2:~$
phil@nz-degrevep-2:~$ cd downloads/
phil@nz-degrevep-2:~/downloads$ s**udo ndiswrapper -i bcmwl5.inf**
bcmwl5 is already installed. Use -e to remove it
phil@nz-degrevep-2:~/downloads$
phil@nz-degrevep-2:~/downloads$
phil@nz-degrevep-2:~/downloads$ **ndiswrapper -l**
Installed ndis drivers:
bcmwl5          driver present, hardware present
phil@nz-degrevep-2:~/downloads$
phil@nz-degrevep-2:~/downloads$
phil@nz-degrevep-2:~/downloads$ **sudo ndiswrapper -m**

modprobe config already contains alias directive

phil@nz-degrevep-2:~/downloads$
phil@nz-degrevep-2:~/downloads$ **sudo modprobe ndiswrapper**
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-27-386/misc/ndiswrapper.ko): ***Invalid module format***
phil@nz-degrevep-2:~/downloads$


Any ideas?

---

### Post by trubblemaker on 2006-12-07
the major issue usually is upgrading to dapper and getting this working,

is this a clean install?

can you please reboot and then post this:
```
 dmesg | grep ndis 
```

---

### Post by shagg1e on 2006-12-07
Hi Guys
i have a broadcom 4306 card in my ibm T23 laptop
i have done exactly as this thread says but i get 
couldn't copy bcmwl5a.inf at /usr/sbin/ndiswrapper line 135.
and if i do -l it says bcmwl5a invalid driver!

Help](*,)

---

### Post by trubblemaker on 2006-12-07
you probably didn't set the path to the driver correctly.

Here a really easy way to do it. Change into the directory with the driver, then run ndiswrapper:
```

ndiswrapper -e bcmwl5a
cd /path/to/driver
ls #should show both bcmwl5a.inf and bcmwl5a.sys 
ndiswrapper -i bcmwl5a.inf

```
above i've shown the instructions for bcmwl5a.inf, as yuou selected that driver. FYI that is the windows 95 driver, you might want to use the XP one bcmwl5.inf not bcmwl5[COLOR="Red"]a[/COLOR].inf

---

### Post by crazybrit4967 on 2006-12-07
> **trubblemaker said:**
> ok so do this for me

use 'any' or the essid where i say 'any' run the following for me

```

dmesg
iwconfig
sudo iwonfig wlan0 essid any
iwconfig

```
if it assoctiates then  skip the next instruction ('ap any')
```

sudo sudo iwonfig wlan0 ap any
iwconfig
sudo dhclient wlan0
dmesg

```
just give me the last 10 lines of dmesg when poeting.



The last ten lines were just 
```

[17180202.932000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180208.932000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180214.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180220.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180226.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180232.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180238.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180244.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180250.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180256.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180262.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180268.940000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180274.940000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180280.940000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180286.940000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180292.940000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180298.940000] ACPI: Unable to turn cooling device [dffeddec] 'on'
[17180304.940000] ACPI: Unable to turn cooling device [dffeddec] 'on'


```
But here's some stuff that I thought looked relevant:
```

[17179587.324000] ndiswrapper: using irq 209
[17179587.540000] NET: Registered protocol family 17
[17179587.900000] wlan0: vendor: ''
[17179587.900000] wlan0: ethernet device 00:0d:3a:6e:79:67 using NDIS driver mn720, 14E4:4325:1414:0004.5.conf
[17179587.900000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA

```
```

[17179732.544000] NET: Registered protocol family 10
[17179732.544000] lo: Disabled Privacy Extensions
[17179732.544000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179732.544000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179732.544000] IPv6 over IPv4 tunneling driver


```

---

### Post by fugative on 2006-12-08
I've got a HP pavilion zv5000 with built-in 802.11b. I tried the fwcutter method but wouldn't work so i went down the ndis road and it worked but when i rebooted it stopped. the driver was still installed according to ndis but no go. I uninstalled and reinstalled the driver and it worked. each time i boot this all disappears and i'm virtually back to square one. 
I want a ad-hoc connection with my shuttle xpc w/ubuntu so i can share the internet connection among others. 

help me out guys 

ps anyone know if wifi cards can be overclocked from 11mbps (that the 802.11b allows) 

the glove is down!!

---

### Post by trubblemaker on 2006-12-08
you need to use "ndiswrapper -m" so that it adds itself to "/etc/modules" or better yet manually add it in to "/etc/modules" 

ps anyone know if wifi cards can be overclocked from 11mbps (that the 802.11b allows)

You can set the speed of the rate:

"sudo iwconfig wlan0 rate 54M"
of 
"sudo iwconfig wlan0 rate 36M"

check the availible rates with 

```
sudo iwlist scan
```
it will list all the availble rates by ap

you should now that it's less reliable at higher speeds.  11M is for long distance from ap with high reliability.

---

### Post by crazybrit4967 on 2006-12-08
So, does anyone know what I should do next?  To me it seems like the card can recieve data but not send any - hence being able to scan but not send out dhcprequests.  Anyone know why that would be?

---

### Post by trubblemaker on 2006-12-08
get specific.

use:
```

sudo iconfig wlan0 essid ******
iwconfig
```
where ****** is your essid for the network. post the output. Can you associate with the ap?
if it says "ap: Not Associated" then there isn't a point to try and get an ip.  if it says a mac address "ap: a0:34:f9:ff:ff:ff" then your in business:
```
sudo dhclient wlan0
```
sometimes if you aren't specific you can't connect.  Also does your router have a mac filter on it that might be keeping you out?  ask however is the admin if that's possible.

---

### Post by crazybrit4967 on 2006-12-08
Yep, it always says not-associated when I use iwconfig.  I'll check again on the router to see if anything's keeping me out.

edit - Okay, I don't think my router is blocking my MAC address - you can set it to filter MAC addresses, but that's not turned on.  Any other ideas?

---

### Post by HeavyEddie on 2006-12-09
Everything seemed to work well until I had tod disable eth0.  I had nothing in network settings except a modem connection.

I rebooted and eth0 is there again.  I can deactivate it, but I don't have wlan0 listed.

---

### Post by crazybrit4967 on 2006-12-09
Okay, so I compiled the latest version of ndiswrapper from source, and it seems to work a bit better.  Now instead of listing signal quality as 0/100 when I do iwlist scan, it has the actual signal quality.  However, now when I do ndiswrapper-l, next to the driver it says hardware present - alternate driver (bcm43xx), even though /etc/modprobe.d/blacklist says "blacklist bcm43xx". I don't know if this matters or not, but there you go.

Anyway, I'm still having the same problem - all DHCPDISCOVER and no DHCPREQUEST.  Does anyone know why this would be?  Please?  I've wasted a whole week trying to get this working, so any help is appreciated, but I'm about ready to give up.

---

### Post by crazybrit4967 on 2006-12-09
> **HeavyEddie said:**
> Everything seemed to work well until I had tod disable eth0.  I had nothing in network settings except a modem connection.

I rebooted and eth0 is there again.  I can deactivate it, but I don't have wlan0 listed.
Did you try editing /etc/iftab so it says wlan0 instead of eth0/eth1?

---

### Post by HeavyEddie on 2006-12-09
That is what I missed!  Thanks for the help!

---

### Post by crazybrit4967 on 2006-12-09
Go you!  Now if only I could get mine to work...

---

### Post by kylebuntu on 2006-12-09
It worked! :D Thank you so much for helping me get my compaq Presario 2100 US laptop working.  You are the 5th tutorial I have tried, and it worked the first time.

Is there a way autoload/start wlan0, or do I need to type in iwconfig wlan0 essid mynetwork each time?

Thanks Again.  I am in seven heaven.

---

### Post by crazybrit4967 on 2006-12-09
> **kylebuntu said:**
> It worked! :D Thank you so much for helping me get my compaq Presario 2100 US laptop working.  You are the 5th tutorial I have tried, and it worked the first time.

Is there a way autoload/start wlan0, or do I need to type in iwconfig wlan0 essid mynetwork each time?

Thanks Again.  I am in seven heaven.Have you configured everything in /etc/network/interfaces?  If not, do that, and make sure there's a line that says "auto wlan0"

---

### Post by HeavyEddie on 2006-12-10
Well... I pushed my luck and upgraded to Edgy.  Now this is broken again.  Oi!

It simply does not appear in network settings any longer.  I did the tutorial from scratch, and get the error below when I attempt the modprobe line.

> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid arguement

---

### Post by crazybrit4967 on 2006-12-10
I got that same error message when I tried it, but I can't remember what I did.  Try removing the driver with -e and then try it again.

---

### Post by crazybrit4967 on 2006-12-11
omg omg omg, I got it to work.  Basically, I got the network working (but sloooow...) with bcm43xx-fwcutter, and then installed ndiswrapper from there and removed the files that bcm43xx-fwcutter put in my /lib/firmware directory.  As far as I know, I didn't do anything differently with ndiswrapper, although it's possible that a new version of ndiswrapper was put up since the last time I tried.  Anyway, whatever it was, it worked!

---

### Post by trubblemaker on 2006-12-12
> **HeavyEddie said:**
> Well... I pushed my luck and upgraded to Edgy.  Now this is broken again.  Oi!

It simply does not appear in network settings any longer.  I did the tutorial from scratch, and get the error below when I attempt the modprobe line.

Yeah it hates upgrades to get you fixed use the 'ndis from source' in my signature, works for upgrades because it makes you remove everything, ndiswrapper packages only seem to work for clean intall not so much for upgraded systems

---

### Post by shaton on 2006-12-13
I'm a very very new Linux user, and I have tried to configure my wireless pcmcia card usign your tutorial. 

All it works fine until I have coded: 'sudo modprobe ndiswrapper'. This command says me the next message:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

Do you know what is happening?

Thanks a lot.

---

### Post by ubunturules on 2006-12-13
can somebody please explain the reasoning behind 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

so I can put it up on the first post.  A lot of people seem to have this problem.

Thanks

---

### Post by shaton on 2006-12-14
> **ubunturules said:**
> can somebody please explain the reasoning behind 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

so I can put it up on the first post.  A lot of people seem to have this problem.

Thanks

I have found the solution for that error.

The Ubuntu Edgy 6.10 version (I'm using it) doesn't have installed the last ndiswrapper version, then it raises that error.

Solution:

```
sudo apt-get install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper 
```

With this code we get ndiswrapper in the last version and it doesn't raise the error. :) 

Now, I'm going to continue because the wlan0 doesn't appear in the networking options. ](*,)  Any idea?

---

### Post by ubunturules on 2006-12-14
Thank you shaton.  I will add it to the first post.

I added some other stuff to the first post also.  I made it a lot cleaner and easier.

ubunturules

---

### Post by woopud on 2006-12-15
Well, finaly got everything installed right, 64b bit drivers, ndiswrapper and network manager.  The wireless shows up in network manager but after typing in the SSID and the WEP key it tries to connect but it doesn't. Same thing with wifi radar, I choose the right network and hit connect but it just stops after a while of trying to connect.
Any ideas ?

Edgy mb bit on Compaq zv5466cl with BCM4306

Bert

---

### Post by woopud on 2006-12-15
> **Kulgan said:**
> **woopud & crazybrit4967**:[INDENT]As far as I know, both of you are suffering the same problem - inconsistencies with the GUI vs. terminal. I strongly recommend the terminal method of setting up the connection, as it is permanent, and you **can see what goes wrong**.[/INDENT]




woopud:
What is the ethernet connection called (in System -> Administration -> Networking)? eth0 or eth1? 

crazybrit4967:
If you follow one of my previous posts, you will get the solution. It is the one that I posted at 10:30PM on Dec. 4. That should enable your connection. As always, ask if you encounter anything....

-K


Its called eth1

Bert

---

### Post by ubunturules on 2006-12-15
woopud:  If you look under Problem 1 on the first post then it will fix your eth1 problem.

---

### Post by woopud on 2006-12-15
Okay, did the things as were posted as "problem 1" still won't work.  If i go to System -> Administration -> Networking  wireless connection shows up with my Essid name and DHCP as the Address, if I go to properties it says "enabled" but it doesn't show up in Network Manager.  I feel i'm getting really close to getting it to work...almost...

Bert

---

### Post by ubunturules on 2006-12-15
what's in your etc/network/interfaces file?
```
sudo gedit /etc/network/interfaces
```

---

### Post by woopud on 2006-12-16
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface wlan0 inet dhcp
wireless-essid DUTCH
wireless-key 95E2B7A41C04D3A1F013556644
address 192.168.0.7
netmask 255.255.255.0
gateway 192.168.0.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth1

auto eth0

```

---

### Post by ubunturules on 2006-12-16
Make it look like this.
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

If it doesn't work you can change it back but I'm thinking its going to work.

---

### Post by HeavyEddie on 2006-12-16
> **trubblemaker said:**
> Yeah it hates upgrades to get you fixed use the 'ndis from source' in my signature, works for upgrades because it makes you remove everything, ndiswrapper packages only seem to work for clean intall not so much for upgraded systems

I went back and re-installed from scratch and didn't upgrade to Edgy afterwards.  However, I would dearly love to get her to Edgy just so she can use FF2.

So, if I upgrade her to Edgy... should I download some of this information first?  When it breaks I won't have any access to the internet via her machine again.

BTW, I really appreciate all the help folks are providing in these forums.

---

### Post by woopud on 2006-12-19
> **ubunturules said:**
> Make it look like this.
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

If it doesn't work you can change it back but I'm thinking its going to work.

No, still no wireless showing up anywhere.
Any other thoughts of what i can try ?

Bert

---

### Post by woopud on 2006-12-19
Well, for some reason my wired connection don't work no more, it is enabled in System -> Administration -> Networking

Bert

---

### Post by ubunturules on 2006-12-19
change your /etc/network/interfaces file back to the way it was.

---

### Post by jkorz on 2006-12-19
I don't know if anybody is having this same problem, but just in case. When I finished up, I wanted to do it all with the command line, so I didn't install network-manager-gnome. I found that an iwlist scan would return results, but I couldn't associate. I had to run the following command to get it to connect to my AP. (I used wep, but if I remember correctly, it does the same thing without encryption)

sudo iwconfig wlan0 key open

Note: if a key was entered before this, it still remains in tact. This just changes "Security Mode" from 'restricted' to 'open'

-Joe

---

### Post by Angva on 2006-12-23
Dear forum,

Yet another Broadcom 4306/ndiswrapper issue I'm afraid. ](*,) 

I followed the how-to found here - [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) - everything went well up until this step:

> If this does not bring up the lights on the card, try ejecting it and re-inserting it.

If the system has a card that works with one of the loaded drivers, you should see the following message in the system log

wlan0: ndiswrapper ethernet device xx:xx:xx:xx:xx:xx

dmesg shows "ndiswrapper version 1.22 loaded" but I do not see "ndiswrapper ethernet device xx:xx..." The instructions say to try ejecting and re-inserting the card, but I really doubt that's the issue as the card has been working as-is in Windows for two years up until a few days ago when I wiped...

I followed that how-to closely, except I am running Edgy so I installed by doing apt-get install ndiswrapper-utils-1.8.

Here is the output of iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
         Mode:Managed  Access Point: Invalid
         RTS thr:off   Fragment thr:off
         Encryption key:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

And here is the output of iwlist scan:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.

```

My laptop is a Dell Inspiron 5160, and the wireless card model number is 1350 (physically looked at it).  lspci shows that the chipset is BCM4306 and rev 03. I tried the drivers for the following two cards found in the list - [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

> #  Laptop: Dell Inspiron 5100 Card: Wireless 1350 (802.11b/g) WLAN miniPCI Card
    * Chipset: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02) _notice this is revision 02, below is revision 03, Idon't know if it matters or not_
    * pciid: 14e4:4320
    * Driver: [http://ftp.us.dell.com/network/R90501.EXE](http://ftp.us.dell.com/network/R90501.EXE)
    * Other: This card is in the miniPCI slot of the Inspiron 5100. The driver below (R83097.exe) did not work, but this one did. To install unzip (program "unzip" works on the .exe) the exe file and use bcmwl5.inf. 

# Laptop: Dell Inspiron 5150 Card: Wireless 1350 (802.11b/g) WLAN miniPCI Card
    * Chipset: Broadcom Corporation BCM#4306 802.11b/g Wireless LAN Controller (rev 03)
    * pciid: ?
    * Driver: [ftp://ftp.us.dell.com/network/R83097.EXE](ftp://ftp.us.dell.com/network/R83097.EXE)
    * Other: This card is in the miniPCI slot of the Inspiron 5150. This driver is for US only. I think this is a Truemobile 1350. To install unzip (program "unzip" works on the .exe) the exe file and use the bcmwl5a.inf in directory AR. 

The second one seems like the best match. It has two directories, each containing bcmwl5.inf and bcmwl5a.inf. The two directories are called AR and IR. I tried all four of these .inf files. I also tried the two for the first card. I got the same results for all six cases.

As I'm sure some of you know, this is a frustrating experience. I just don't know what to do. I would greatly appreciate any advice anyone could offer.

Thank you!

---

### Post by Kulgan on 2006-12-23
you installed by doing apt-get install ndiswrapper-utils-1.8?

but doesn't that mean that you have an internet connection?

---

### Post by Angva on 2006-12-23
> **Kulgan said:**
> you installed by doing apt-get install ndiswrapper-utils-1.8?

but doesn't that mean that you have an internet connection?

Yes I have internet working (ethernet), but not the wireless adapter. Different devices...

---

### Post by Kulgan on 2006-12-23
](*,)  I forget - I only use wireless, since I move about so much... 
what does ndiswrapper -l give you?

---

### Post by trubblemaker on 2006-12-23
Sometimes your card needs to be turned on  to work, this can be done two ways

Going into your bios and see if there is a setting for it.

Turn on the card via Windows and boot back into linux

it would also be helpful if you posted:

```
 dmesg | grep ndis 
```

---

### Post by Angva on 2006-12-24
> **trubblemaker said:**
> Going into your bios and see if there is a setting for it.
This did the trick. The setting Wireless was set to Off. There was also a setting for how to toggle wireless, which was set to Fn-F2/Application. First I tried pressing Fn-F2 from the KDE, but nothing happened - system logs said this keycode wasn't recognized. Then I just set it Wireless to On and restarted... At first it still didn't work, but after setting the laptop to Hibernate mode, then starting up again later, it worked! Not quite sure why it only worked after hibernating, but it seems to consistently work now.

Thank you so much!!

---

### Post by litith on 2006-12-25
Hey guys, I, too, need some help.

Here is what I have found so far:

```
~$ dmesg | grep ndis
[4294693.155000] ndiswrapper version 1.28 loaded (preempt=yes,smp=no)
[4294693.231000] ndiswrapper: driver bcmwl5 (Linksys,07/17/2003, 3.30.15.0) loaded
[4294693.236000] ndiswrapper (NdisWriteErrorLogEntry:231): log: C000138D, count: 1, return_address: cea9ebe3
[4294693.236000] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0x103
[4294693.236000] ndiswrapper (miniport_init:269): couldn't initialize device: C0000001
[4294693.236000] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[4294693.236000] ndiswrapper (miniport_halt:326): device c8fc4260 is not initialized - not halting
[4294693.236000] ndiswrapper: device eth%d removed
[4294693.236000] ndiswrapper: probe of 0000:05:02.0 failed with error -22
[4294693.236000] usbcore: registered new driver ndiswrapper

~$ ndiswrapper -l
installed drivers:
bcmwl5          driver installed, hardware (14E4:4320) present (alternate driver: bcm43xx)

```

Looking at this, I have no idea what is going on.

As per the previous posts, I have configured (eth1->wlan0) my /etc/network/interfaces, /etc/iftab, and /etc/modprobe.d/ndiswrapper, and "ndiswrapper" is in /etc/modules.

Further, with both ifconfig and iwconfig, my wlan0/eth1 does not appear on the list at all, and it is not listed in under System->Admin->Networking, nor does the card appear in the Device Manager (the standard HAL.)

I have also checked the BIOS to make sure that the card is enabled, and it is.

I am at a complete and utter loss as to what is going wrong, though I am sure that it is just something minor that I have overlooked.

Thanks in advance!

---

### Post by Kulgan on 2006-12-25
If the driver is installed, and the hardware recognised, it should only be a matter of connecting. What does ```
dhclient essid <essid here>
``` give you?

---

### Post by litith on 2006-12-25
> **Kulgan said:**
> If the driver is installed, and the hardware recognised, it should only be a matter of connecting. What does ```
dhclient essid <essid here>
``` give you?

```
~$ sudo *(w/o sudo I got a "Permission Denied") *dhclient essid test
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
test: ERROR while getting interface flags: No such device
test: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
essid: ERROR while getting interface flags: No such device
essid: ERROR while getting interface flags:
```

---

### Post by Kulgan on 2006-12-25
Your essid is 'test'? Seems rather odd.. but anyway...

looks like the device is not started check once more the settings in /etc/network/interfaces then, try 
```
ifdown -a
```
then
```
ifup -a
```

then try the internet again. If it still doesn't work, issue 
```
dhclient essid <essid here>
```
again. 

Post all the outputs...
-K

---

### Post by litith on 2006-12-25
Heh, love my test network ;)

See, to me it sounds as though the greater computer doesn't even recognize the card and that only the ndis does.

```
~$ sudo ifdown -a
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:c0:9f:b5:42:8e
Sending on   LPF/eth0/00:c0:9f:b5:42:8e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67

~$ sudo ifup -a
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:c0:9f:b5:42:8e
Sending on   LPF/eth0/00:c0:9f:b5:42:8e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.7 -- renewal in 34044 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

~$ sudo dhclient essid test
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
test: ERROR while getting interface flags: No such device
test: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
essid: ERROR while getting interface flags: No such device
essid: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
```

---

### Post by Kulgan on 2006-12-26
The card definitely works. You got an answer to dhcp, and are bound to 192.168.1.7. Just out of curiousity, what router are you using?

As far as I can tell, you should be able to reboot, and then have internet connection. Try the ping tool (System -> Administration -> Networking tools) just to see what happens. You could also try going to your router on the network (I presume that's 192.168.1.1?)

If the rebooting doesn't change anything, try ifdown/up -a again - posting the out put, of course. Since you have set the right stuff in /etc/newtork/interfaces, the last command shouldn't be neccessary. 

-K

---

### Post by litith on 2006-12-26
Hmmm, well, I got my card working (finally: [http://www.linuxquestions.org/questions/showthread.php?t=344849)](http://www.linuxquestions.org/questions/showthread.php?t=344849)).

Well, I can do a scan (iwlist scan), and I get:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:90:4C:7E:00:10
                    ESSID:"router"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

My router is now "router," (test seemed too generic ;) ) and when I do the ifup/down -a, it still will not connect,   And when I do ```
~$ sudo dhclient router
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
router: ERROR while getting interface flags: No such device
router: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
essid: ERROR while getting interface flags: No such device
essid: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
``` it still does not work.

My router is a NetGear WGR614.   

Oh, and by the way, my eth0 is wired, hence why it was able to get the DHCP Bind.

---

### Post by trubblemaker on 2006-12-26
you need to do the following

```
sudo iwconfig wlan0 essid router
sudo dhclient wlan0
```

to get an ip, if that works then we can setup your /etc/network/interfaces file to grab your "router" essid on boot.

---

### Post by Kulgan on 2006-12-26
should you disconnect the wired ethernet when doing this? It MIGHT have some effect on things...

---

### Post by litith on 2006-12-26
> **trubblemaker said:**
> you need to do the following

```
sudo iwconfig wlan0 essid router
sudo dhclient wlan0
```

to get an ip, if that works then we can setup your /etc/network/interfaces file to grab your "router" essid on boot.

Nothing happened, here is what I got:

```
~$ sudo iwconfig wlan0 essid router
~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:90:4b:f3:a6:ac
Sending on   LPF/wlan0/00:90:4b:f3:a6:ac
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by litith on 2006-12-26
> **Kulgan said:**
> should you disconnect the wired ethernet when doing this? It MIGHT have some effect on things...

Tried it :(  and every other permutation that I could think of.

---

### Post by trubblemaker on 2006-12-26
no you don't need to remove wired connection as you specified the interface for dhcp to use.

what's the output from ```
iwconfig
```
it didn't get an offer from your router, to be honest it might be a bad name for the essid.  I don't think it's a reserved word but it might be, a simple change the myRouter or router! would be enough of a change to not have it be a reserved word.  Also please please tell me you have turned of encyption for now, atleast until we get you connnected to the router.

---

### Post by litith on 2006-12-26
Haha, yes, every single form or router security that this thing can do is disabled.   

Ok, and now I am going to get really embarssed, but happy, when I say that changing its name worked :-D   Haha, wow, some of the things I do...

---

### Post by Kulgan on 2006-12-26
:D that's great!

---

### Post by trubblemaker on 2006-12-26
stupid reserved words, Hey merry Xmas

---

### Post by litith on 2006-12-26
> **trubblemaker said:**
> stupid reserved words, Hey merry Xmas

Haha, Xmas was already here?   Wow, well, merry xmas, then.

---

### Post by trubblemaker on 2006-12-26
sorry I *swear*  I sent it before christmas..... ;)

---

### Post by Sarnix on 2006-12-29
hi,

i'm kinda going through the same stuff as Lilith and I hope one of you can help me, too.

I'm not sure what the problem is. I think the hardware works as mented, but it doesnt find any dhcp offers, where he should find my modem/router and a couple of routers in the neighborhood.
This is the output of iwconfig
```

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

this is the output of sudo dhclient wlan0
```

Listening on LPF/wlan0/00:90:96:a6:38:7d
Sending on   LPF/wlan0/00:90:96:a6:38:7d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

the output of iwlist scan
```

wlan0     No scan results

```

I really cant tell where it goes wrong in my configuration. Can of you?
Tia.

---

### Post by Kulgan on 2006-12-29
what does your /etc/network/interfaces look like? 
I know, basic, but it might have an effect...

---

### Post by Sarnix on 2006-12-29
Thanks for your reply,
When trying wifi to get to work its:
auto wlan0 instead of auto eth0

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid S4T3RF1X

auto eth0

```

---

### Post by trubblemaker on 2006-12-29
> **Sarnix said:**
> hi,
```

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

wlan0     No scan results

```



You can't see any networks (iwlist tells me) and your not associating to any networks. (iwconfig tells me).
So I kinda wonder about your ndis loading propely.
can you post the output of the following?
```

dmesg | grep ndis
ndiswrapper -l

```
That will help to pinpoint what the problem is.

---

### Post by Sarnix on 2006-12-29
dmesg | grep ndis doesnt have any output

ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

what does the lack of output mean from dmesg?

---

### Post by trubblemaker on 2006-12-29
ndiswapper isn't loading on boot, try 
```

modprobe ndiswrapper

```
then see if you get results with 
```
iwlist scan
```
on the upside ndiswrapper has a driver and can see the hardware.
if that works add "ndiswrapper" to 
```
/etc/modprobe.d
```

---

### Post by ubunturules on 2006-12-29
I just want to tell everyone in this thread thank you for all the help!  I couldn't answer all of these questions by myself and I'm glad that y'all are helping out!

ubunturules

---

### Post by Praxicoide on 2006-12-30
Hi, I followed all the steps but I don't seem to have /etc/modeprobe.d/ndiswrapper

In Networking, I don't have either eth0 or wlan0.

I had errors 1 and 2, BTW

---

### Post by Sarnix on 2006-12-30
Thx for your help trubblemaker

The problem still puzzles me. So ndiswrapper isnt loaded on boot although ndiswrapper is in /etc/modprobe.d, and the wlan0 is in /etc/iftab and /etc/modprobe.d/ndiswrapper.
Yet when i do modprobe ndiswrapper and then iwlist scan it starts scanning. Too bad that it doesnt find any dhcpoffers where it should.

I'm afraid i dont see the logic in this malfunctioning. I think i should wonder why ndiswrapper wont load on boot, because it seems configured rightly to do so.

---

### Post by trubblemaker on 2006-12-30
> **Praxicoide said:**
> Hi, I followed all the steps but I don't seem to have /etc/modeprobe.d/ndiswrapper

In Networking, I don't have either eth0 or wlan0.

I had errors 1 and 2, BTW

what do you mean errors one and two?

---

### Post by trubblemaker on 2006-12-30
> **Sarnix said:**
> Thx for your help trubblemaker

The problem still puzzles me. So ndiswrapper isnt loaded on boot although ndiswrapper is in /etc/modprobe.d, and the wlan0 is in /etc/iftab and /etc/modprobe.d/ndiswrapper.
Yet when i do modprobe ndiswrapper and then iwlist scan it starts scanning. Too bad that it doesnt find any dhcpoffers where it should..
it won't unless you specify one of the essid's that it sees., i.e.
```

sudo iwconfig wlan0 essid <fav-essid> 
sudo dhclient wlan0
iwconfig

```
try 'ndiswrapper -m' it should make things run on boot, if it doesn't post back.

> **Sarnix said:**
> 
I'm afraid i dont see the logic in this malfunctioning. I think i should wonder why ndiswrapper wont load on boot, because it seems configured rightly to do so.
yes it's configured correctly but it's not ndiswrapper that chooses to run at boot, with the above mentioned 'ndiswrapper -m' it should tell the kernel to load 'it' on boot.  small difference but really the big difference.

as always output helps me answer questions so if something doesn't work alway try and post the output of the commands back.

---

### Post by Sarnix on 2006-12-30
Thanks alot, Trubblemaker.

Posting this message wireless. :) Plus ndiswrapper is loaded on boot now.

Now moving on to wep or wpa. But that's something for tomorrow or later.

Thanks again for your help!

---

### Post by ex_tour_director on 2007-01-04
BCM4306 chipset, D-Link Router will not network 

I am trying to set up wireless connection (for my father) on an older Dell computer to a windows based wireless network. The computer has Ubuntu 6.06 installed as the operating system. It has a Belkin F5D7000 wireless card which uses the BCM4306 chipset. The router I am trying to connect to is a D-Link DI-524 with the latest firmware installed. I followed the various suggestions in the forums and used ndiswrapper and the bcmwl5.inf driver. The network is set up on a newer Dell computer running Windows XP Media Center Edition. I know that the network is set up correctly because a Dell laptop also running Window XP can connect to it. I was also able to connect to it with my own laptop.

I was able to set up a similar wireless connection on an older Gateway running Ubuntu 6.06 using the same model number Belkin card connecting to a Belkin router. The Gateway computer connected instantly to the Belkin network. In fact the the Dell computer will connect to my Belkin network so I am pretty sure that I have the card set up and the drivers installed correctly. But it will not connect to my father's D-Link network.

For some reason the wireless connection on my Gateway computer is named eth1 but the wireless connection on the Dell (that I cannot get to work with the D-Link router is called eth0). I don't know if that means anything or not. 

The following is the output from the Dell computer when I tried to connect to the D-Link network. The network I am trying to connect to is Cell 01 with an essid of “dlink”. The other network listed is my network which is located next door and I can connect to it if the weather conditions are right.  I did bring the computer over to my house to connect to my network so that I could update Ubuntu and the other programs previously.


bob@bob-desktop:~$ sudo iwlist eth0 scan
eth0 Scan completed :
Cell 01 - Address: 00:15:E9:1B:02:BA
ESSID:"dlink"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.432 GHz (Channel 5)
Quality:0/100 Signal level:-31 dBm Noise level:-256 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0
Cell 02 - Address: 00:11:50:1B:0F:29
ESSID:"al1"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.452 GHz (Channel 9)
Quality:0/100 Signal level:-70 dBm Noise level:-256 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0

bob@bob-desktop:~$ sudo iwconfig eth0 essid dlink
bob@bob-desktop:~$ sudo iwconfig eth0 key XX-XX-XX-XX-XX
bob@bob-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:11:50:18:f5:a3
Sending on LPF/eth0/00:11:50:18:f5:a3
Sending on Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.2.7
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

I am very new to Ubuntu and do not know how to do very many things so if you are able to help me please give specific and complete instructions. Thank you.

---

### Post by trubblemaker on 2007-01-04
well so far it looks like you've setup everything correctly, you can see the network, great.  But lets go back a step and make sure you can connect to the network without encryption and then will add encryption back in.  This step will help us determine if we need to further setup the wireless driver, or if we need to work more on the encryption.

---

### Post by ex_tour_director on 2007-01-04
I had turned the encryption off on the d-link router before and was not able to connect to it.  It is really crazy since I can connect to my network (Belkin router) with WEP encryption with the card but cannot connect to my father's network (D-Link router).  On my old Gateway (running Ubuntu 6.06 also) using the same card (I bought two of the exact same cards - Belkin F5D7000) I can also only connect to my Belkin network but not to my father's D-Link network. 

I appreciate you taking the time to help me to get this working.

---

### Post by trubblemaker on 2007-01-05
I love d-link as it's linux friendly we just need to figure out the specifics.
so starting with un-encrypted tell me the output from 
```

iwlist scan
iwconfig 
cat /etc/network/interfaces

```
......
er
I mean this site says that you should be using the native driver for your card... [here's the wiki you need to follow]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500")
I totally don't mind helping you work on the ndiswrapper thing but the Ralink driver is a native driver so might work better, look it over and I'll help you with either route.  Don't forget to save your settings with the D-link router, it's something I forget to do all the time.  ANd as stupid as it sounds rebooting a router is good for everyone!

---

### Post by ex_tour_director on 2007-01-05
I am sure that this card does not use the Ralink driver because it is not the version listed on the site you directed me to.  I believe that it uses the Broadcom BCM4306 chipset.  But just to make sure I called Belkin today to ask them.  The box the card came in say F5D7000 Version 2000.  When I called Belkin the tech support person said the card would not work under linux.  He was shocked when I told him that I had it working with a Belkin router. I told him I wanted to know the chipset because I was trying to find a driver on a linux site for it so I could get it to work for my dad with his d-link router. He said he had to look it up.  When he came back he said it was a Broadcom BCM9402.  I have been unable to find a listing for Broadcom BCM9402 anywhere on the web.  So it is possible that the guy a Belkin did not know what chipset it is.  Anyway, the question is where do we go from here?

---

### Post by trubblemaker on 2007-01-05
it's all good, I did see [later versions of your card ]("http://ralink.rapla.net/")using the ralink driver the (F5D7010) and (F5D7050), no big deal 

As for that rep knowing what he's talking about.... yeah I wouldn't believe a word that he said.  stay with the 4306 if you want. 

I don't believe he knew what he was talking about.

so from here:

turn of encryption, 
and post the output of the following commands
```

sudo iwlist eth0 scan
ndiswrapper -l
cat /etc/network/interfaces
dmesg | grep ndis
iwconfig 
sudo iwconfig eth0 essid dlink
iwconfig 
sudo dhclient eth0

```

---

### Post by mrojas73 on 2007-01-05
I just folled this howto to get my Linksys wireless card working.  Very nice and easy, I am running Edgy.

Thank you so much.

---

### Post by CeeDub on 2007-01-07
Well, I followed the HOW-TO word for word.  I even had to do the problem 2 fix.  However it still is not working.  I ran dmesg | grep ndis and got this:
```
ceedub@ceedub-laptop:~$ dmesg | grep ndis
[   47.294859] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   47.407780] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   47.407791] ndiswrapper (load_sys_files:215): couldn't prepare driver 'bcmwl5'
[   47.408531] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

```

Apparently the driver I used wasn't 64 bit, but I am running the 64-bit version of Ubuntu.   I started searching the same thread for a fix, but there were too many posts to go through.  Does anyone know how to fix this problem?
ps.  On the last line is says "check system log for messages from 'loadndisdriver'.  Where would I find that system log?

---

### Post by ubunturules on 2007-01-07
CeeDub: you need the 64 bit drivers. To remove the 32 bit driver you installed run this command.

```
sudo ndiswrapper -e bcmwl5
```

I'm about to go somewhere but somewhere on here around page 10 or so somebody posted the 64 bit drivers.  I'll look for them when I get back if you can't find them.

ubunturules

---

### Post by ubunturules on 2007-01-08
I added the 64 bit drivers to the front page.

ubunturules

---

### Post by blore123 on 2007-01-09
I followed the above guide and fixed my computer with just one restart absolutely perfectly.

Thanks a lot for all that help... :)

---

### Post by ubunturules on 2007-01-09
No problem man.  Glad to hear you got it working!

ubunturules

---

### Post by pbmax on 2007-01-10
I followed the same instruction listed in several places (like here) and when I get to
```
hill@widescreen:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present
phill@widescreen:~$
```

I get no "hardware present" no matter what I try.
suggestions?

---

### Post by Jammy on 2007-01-10
Hello all.

I am having trouble with step 5 on this tutorial. When I enter the command into the terminal, I get the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ndiswrapper-utils: Depends: ndiswrapper-utils-1.1 but it is not installable

```
I'm currently using Ubuntu Edgy Eft 6.10 w/ a 2.6.17-10-powerpc Kernel on an iBook G4. Any help would be appreciated. :)

---

### Post by nfoti on 2007-01-11
I need help!!! I do not post very often and can usually find all of my answers without having to. 
Background - Compaq Presario R3000 with broadcom 4306 - I used this guide to setup wireless while running dapper (no problems!)
I did a fresh install of edgy today and the guide no longer works for me. I followed all of the directions to the tee in order. The one initial mistake I made was to install ndiswrapper-utils instead of ndiswrapper-utils-1.8. 
ndiswrapper -l
netbc564                driver installed, hardware present

The big thing I cannot figure out:
sudo modprobe ndiswrapper 
when I run this the computer hangs for a minute then spits out the rather ominous:
Killed

Just the word killed - In all my messing around with ndiswrapper I have never seen this.

Anyways the output of
dmesg | grep ndis

[  483.405518] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[  483.416800] ndiswrapper (load_pe_images:573): fixing KI_USER_SHARED_DATA address in the driver
[  483.419437] ndiswrapper: driver netbc564 (,10/01/2002,3.70.17.5) loaded
[  483.425806] Modules linked in: ndiswrapper rfcomm l2cap bluetooth ipv6 powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi sbs pcc_acpi i2c_ec hotkey dev_acpi container button battery asus_acpi ac sbp2 lp af_packet pcmcia joydev tsdev evdev yenta_socket rsrc_nonstatic pcmcia_core 8139cp 8139too pcspkr parport_pc parport psmouse serio_raw mii snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer i2c_nforce2 i2c_core shpchp pci_hotplug snd soundcore snd_page_alloc ext3 jbd ide_generic ohci_hcd ohci1394 ieee1394 ehci_hcd usbcore ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan vesafb capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[  483.425893] Pid: 4636, comm: loadndisdriver- Tainted: P      2.6.17-10-generic #2
[  483.425989] Process loadndisdriver- (pid: 4636, threadinfo ffff810009d62000, task ffff810007a92730)
[  483.426035] Call Trace: <ffffffff883cd07d>{:ndiswrapper:NdisAllocateMemoryWithTag+13}
[  483.426211]        <ffffffff883c403b>{:ndiswrapper:win2lin3+17} <ffffffff883c403b>{:ndiswrapper:win2lin3+17}
[  483.426364]        <ffffffff883ccca7>{:ndiswrapper:NdisMAllocateSharedMemory+71}
[  483.426443]        <ffffffff883c406e>{:ndiswrapper:win2lin5+25} <ffffffff802cbbfe>{alternate_node_alloc+126}
[  483.426576]        <ffffffff883de407>{:ndiswrapper:miniport_init+167} <ffffffff883d8fb0>{:ndiswrapper:IoSyncForwardIrp+144}
[  483.426714]        <ffffffff883de560>{:ndiswrapper:NdisDispatchPnp+144}
[  483.426773]        <ffffffff883d7aed>{:ndiswrapper:IoInitializeIrp+45}
[  483.426840]        <ffffffff883d7bc6>{:ndiswrapper:IoAllocateIrp+134} <ffffffff883c4027>{:ndiswrapper:win2lin2+14}
[  483.426972]        <ffffffff883d71de>{:ndiswrapper:IofCallDriver+62} <ffffffff883d856f>{:ndiswrapper:IoBuildSynchronousFsdRequest+47}
[  483.427100]        <ffffffff883dc8dc>{:ndiswrapper:IoSendIrpTopDev+172}
[  483.427171]        <ffffffff883d75c5>{:ndiswrapper:IoGetAttachedDevice+293}
[  483.427244]        <ffffffff883dcb4c>{:ndiswrapper:pnp_start_device+76}
[  483.427323]        <ffffffff883dcdba>{:ndiswrapper:wrap_pnp_start_device+538}
[  483.427503]        <ffffffff8033ecf7>{__pci_register_driver+87} <ffffffff883c8a23>{:ndiswrapper:wrapper_ioctl+1155}
[  483.427782]  <3>ndiswrapper (wrapper_init:129): loadndiswrapper failed (35072); check system log for messages from 'loadndisdriver'
[  483.437605] Modules linked in: ndiswrapper rfcomm l2cap bluetooth ipv6 powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi sbs pcc_acpi i2c_ec hotkey dev_acpi container button battery asus_acpi ac sbp2 lp af_packet pcmcia joydev tsdev evdev yenta_socket rsrc_nonstatic pcmcia_core 8139cp 8139too pcspkr parport_pc parport psmouse serio_raw mii snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer i2c_nforce2 i2c_core shpchp pci_hotplug snd soundcore snd_page_alloc ext3 jbd ide_generic ohci_hcd ohci1394 ieee1394 ehci_hcd usbcore ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan vesafb capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[  483.437880]        <ffffffff8033eb18>{pci_unregister_driver+24} <ffffffff883c84a6>{:ndiswrapper:loader_exit+134}
[  483.437978]        <ffffffff883dc289>{:ndiswrapper:module_cleanup+9} <ffffffff881600fc>{:ndiswrapper:wrapper_init+252}

Any help would be greatly appreciated!! I am completely out of ideas (I removed everything having to do with ndiswrapper, reinstalled, tried different drivers) I have seen other posts recommending a compile of the newest ndiswrapper 1.29 (i think) I don't want to go through a full compile just to find out that I've been "Killed"

---

### Post by trubblemaker on 2007-01-11
hey if you ran into an issue with this script. then compiling from soure will probably save you time hunting around for the error.  check my signature for the step by step instructions probably takes 5mins, and the uninstall feature is worth it alone, as you need to remove everything and start from scratch.  I know it sounds scray compiling from source that's what i though but just read the instruction I have listed in the signature, if you don't want to do it after reading them hey, you maybe only lost a minute to reading it.

see the "ndis from source" link below

---

### Post by nfoti on 2007-01-12
I compiled ndiswrapper from source and everything is finally working again. 

Thanks for the tip!

---

### Post by djaquay on 2007-01-12
Went through the howto, worked great right away.  I'd been frustrated with using the bcm43xx driver (on my 4806 card), with getting slow and/or intermittently no connectivity; using ndiswrapper in this way worked like a charm, and I never had it connect so fast under SuSE (which I just replaced with Ubuntu, dontchano).

Anyway, thanks much,
Dave

---

### Post by ubunturules on 2007-01-14
I'm glad you got it to work djaquay!

ubunturules

---

### Post by brainiac978 on 2007-01-17
After searching this thread and some other threads, I cannot get this to work.  I have followed all suggestions in this thread, even doing a fresh install.

After I follow the procedure, the wireless network option in Network Manager disappears.  All attempts to get it to appear so far, have failed.

I have a Broadcom 4306 rev03 card.  It's on a Compaq Presario 2227us (2200 series).  Please help.  :(

---

### Post by brainiac978 on 2007-01-17
Bump Please

---

### Post by CCBalla10 on 2007-01-17
try installing Wifi-radar....go to applications>add/remove>then search for Wifi-radar....works great for me:D

---

### Post by trubblemaker on 2007-01-17
brainiac978
post me some output and I help you with this

```

lspci | grep Broad
cat /etc/modprobe.d/blacklist

ifconfig
cat /etc/network/interfaces

iwconfig 
iwlist scan

ndiswrapper -l
dmesg | grep ndis

```

sure it's alot of output, please wrap it in code blocks so it's not huge on the forum.  This will help me to diagnose your issue.

---

### Post by brainiac978 on 2007-01-18
Okay, here's what I have:
```
caroline@caroline-laptop:~$ lspci |  grep Broad
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
--------------------------------------------------------------
caroline@caroline-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:6C:B2:4A  
          inet6 addr: fe80::2c0:9fff:fe6c:b24a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:728 (728.0 b)  TX bytes:1152 (1.1 KiB)
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9592 (9.3 KiB)  TX bytes:9592 (9.3 KiB)
--------------------------------------------------------------
caroline@caroline-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

blacklist bcm43xx
--------------------------------------------------------------
caroline@caroline-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


--------------------------------------------------------------
caroline@caroline-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
--------------------------------------------------------------
caroline@caroline-laptop:~$ ndiswrapper -l
Installed drivers:
bcm5wl  invalid driver!  (this was a typo)
bcmwl5          driver installed, hardware present 
--------------------------------------------------------------
caroline@caroline-laptop:~$ dmesg | grep ndis

--------------------------------------------------------------

```
Nothing happened on the last command.

---

### Post by trubblemaker on 2007-01-18
k so ndiswrapper is loading on boot and you should remove that other driver:

remove the invalid driver:

```
sudo rm -r /etc/ndiswrapper/bcm5wl
```

try:

```
sudo modprobe ndiswrapper
iwlist scan
```

if that returns results great your back on track. I can help you with other stuff like

```
ndiswrapper -m
```
which will make ndiswrapper start on boot.

also I can show you howto configure you  /etc/network/interfaces which you didn't send me but not a big deal.

---

### Post by brainiac978 on 2007-01-18
I removed the "invalid driver" (even though it was just a typo)

```
sudo modprobe ndiswrapper
``` doesen't do anything

```
iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```
ndiswrapper -m
```modprobe config already contains alias directive


Still no luck.

---

### Post by trubblemaker on 2007-01-18
if you could please reboot and run
```
dmesg | grep ndis
```
if it turns up blank post dmesg and I'll try and give it a look through.

---

### Post by brainiac978 on 2007-01-18
```
dmesg | grep ndis
```Didn't do anything

```
dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001dee0000 (usable)
[17179569.184000]  BIOS-e820: 000000001dee0000 - 000000001deec000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001deec000 - 000000001df00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001df00000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 478MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 122592
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 118496 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 HP                                    ) @ 0x000f6560
[17179569.184000] ACPI: RSDT (v001 HP     3084     0x06040000  LTP 0x00000000) @ 0x1dee67e7
[17179569.184000] ACPI: FADT (v001 HP     3084     0x06040000 PTL  0x00000050) @ 0x1deebed2
[17179569.184000] ACPI: BOOT (v001 HP     3084     0x06040000  LTP 0x00000001) @ 0x1deebfd8
[17179569.184000] ACPI: DSDT (v001 HP     3084     0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (013ca000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1296.923 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.436000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.436000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.452000] Memory: 476264k/490368k available (1910k kernel code, 13584k reserved, 1070k data, 308k init, 0k highmem)
[17179569.452000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.532000] Calibrating delay using timer specific routine.. 2595.93 BogoMIPS (lpj=5191872)
[17179569.532000] Security Framework v1.0.0 initialized
[17179569.532000] SELinux:  Disabled at boot.
[17179569.532000] Mount-cache hash table entries: 512
[17179569.532000] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.532000] CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.532000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.532000] CPU: L2 cache: 1024K
[17179569.532000] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.532000] Checking 'hlt' instruction... OK.
[17179569.548000] SMP alternatives: switching to UP code
[17179569.548000] Freeing SMP alternatives: 16k freed
[17179569.548000] checking if image is initramfs... it is
[17179570.260000] Freeing initrd memory: 5563k freed
[17179570.260000] ACPI: Core revision 20060707
[17179570.260000] ACPI: Looking for DSDT ... not found!
[17179570.260000] ACPI: setting ELCR to 0200 (from 0c20)
[17179570.288000] CPU0: Intel(R) Celeron(R) M processor         1.30GHz stepping 06
[17179570.288000] SMP motherboard not detected.
[17179570.288000] Local APIC not detected. Using dummy APIC emulation.
[17179570.288000] Brought up 1 CPUs
[17179570.288000] migration_cost=0
[17179570.288000] NET: Registered protocol family 16
[17179570.288000] EISA bus registered
[17179570.288000] ACPI: bus type pci registered
[17179570.288000] PCI: PCI BIOS revision 2.10 entry at 0xfd9a2, last bus=2
[17179570.288000] PCI: Using configuration type 1
[17179570.288000] Setting up standard PCI resources
[17179570.308000] ACPI: Interpreter enabled
[17179570.308000] ACPI: Using PIC for interrupt routing
[17179570.308000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.308000] PCI: Probing PCI hardware (bus 00)
[17179570.312000] Boot video device is 0000:00:02.0
[17179570.312000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179570.312000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179570.312000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.312000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.312000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.312000] Please report the result to linux-kernel to fix this permanently
[17179570.312000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.316000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.316000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[17179570.316000] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[17179570.316000] ACPI: PCI Interrupt Link [LNKC] (IRQs *11)
[17179570.316000] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[17179570.320000] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[17179570.320000] ACPI: PCI Interrupt Link [LNKF] (IRQs 11) *0, disabled.
[17179570.320000] ACPI: PCI Interrupt Link [LNKG] (IRQs 11) *0, disabled.
[17179570.320000] ACPI: PCI Interrupt Link [LNKH] (IRQs *11)
[17179570.320000] ACPI: Embedded Controller [H_EC] (gpe 29) interrupt mode.
[17179570.324000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.324000] pnp: PnP ACPI init
[17179570.328000] pnp: PnP ACPI: found 7 devices
[17179570.328000] PnPBIOS: Disabled by ACPI PNP
[17179570.328000] PCI: Using ACPI for IRQ routing
[17179570.328000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.332000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.332000] PCI: Bus 3, cardbus bridge: 0000:02:05.0
[17179570.332000]   IO window: 00003400-000034ff
[17179570.332000]   IO window: 00003800-000038ff
[17179570.332000]   PREFETCH window: 30000000-31ffffff
[17179570.332000]   MEM window: 34000000-35ffffff
[17179570.332000] PCI: Bridge: 0000:00:1e.0
[17179570.332000]   IO window: 3000-3fff
[17179570.332000]   MEM window: e0200000-e02fffff
[17179570.332000]   PREFETCH window: 30000000-31ffffff
[17179570.332000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.332000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[17179570.332000] PCI: setting IRQ 11 as level-triggered
[17179570.332000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[17179570.332000] NET: Registered protocol family 2
[17179570.368000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.368000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.368000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.368000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.368000] TCP reno registered
[17179570.368000] Simple Boot Flag at 0x36 set to 0x1
[17179570.368000] audit: initializing netlink socket (disabled)
[17179570.368000] audit(1169126735.368:1): initialized
[17179570.368000] VFS: Disk quotas dquot_6.5.1
[17179570.368000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.368000] Initializing Cryptographic API
[17179570.368000] io scheduler noop registered
[17179570.368000] io scheduler anticipatory registered
[17179570.368000] io scheduler deadline registered
[17179570.368000] io scheduler cfq registered (default)
[17179570.368000] isapnp: Scanning for PnP cards...
[17179570.724000] isapnp: No Plug & Play device found
[17179570.752000] Real Time Clock Driver v1.12ac
[17179570.752000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.752000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179570.752000] PCI: setting IRQ 5 as level-triggered
[17179570.752000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179570.752000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179570.752000] mice: PS/2 mouse device common for all mice
[17179570.752000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.752000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.752000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.756000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PSM2] at 0x60,0x64 irq 1,12
[17179570.760000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.760000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.760000] EISA: Probing bus 0 at eisa.0
[17179570.760000] Cannot allocate resource for EISA slot 1
[17179570.760000] Cannot allocate resource for EISA slot 2
[17179570.760000] Cannot allocate resource for EISA slot 3
[17179570.760000] EISA: Detected 0 cards.
[17179570.764000] TCP bic registered
[17179570.764000] NET: Registered protocol family 1
[17179570.764000] NET: Registered protocol family 8
[17179570.764000] NET: Registered protocol family 20
[17179570.764000] Using IPI No-Shortcut mode
[17179570.764000] ACPI: (supports S0 S3 S4 S5)
[17179570.764000] Freeing unused kernel memory: 308k freed
[17179570.852000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.900000] Capability LSM initialized
[17179571.936000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179571.940000] ACPI: Thermal Zone [THRM] (35 C)
[17179572.280000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179572.280000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179572.280000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179572.280000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179572.280000] ICH4: chipset revision 3
[17179572.280000] ICH4: not 100% native mode: will probe irqs later
[17179572.280000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179572.284000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
[17179572.284000] Probing IDE interface ide0...
[17179572.572000] hda: HITACHI_DK23FA-40, ATA DISK drive
[17179573.244000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.248000] Probing IDE interface ide1...
[17179573.984000] hdc: PHILIPS CD-RW/DVD-ROM CDD5263, ATAPI CD/DVD-ROM drive
[17179574.656000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.660000] hda: max request size: 128KiB
[17179574.668000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179574.668000] hda: cache flushes supported
[17179574.668000]  hda: hda1 hda2 < hda5 >
[17179574.736000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179574.736000] Uniform CD-ROM driver Revision: 3.20
[17179574.972000] usbcore: registered new driver usbfs
[17179574.972000] usbcore: registered new driver hub
[17179574.972000] USB Universal Host Controller Interface driver v3.0
[17179574.972000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179574.972000] PCI: setting IRQ 10 as level-triggered
[17179574.972000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179574.972000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.972000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.972000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.972000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001820
[17179574.972000] usb usb1: configuration #1 chosen from 1 choice
[17179574.972000] hub 1-0:1.0: USB hub found
[17179574.972000] hub 1-0:1.0: 2 ports detected
[17179575.076000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179575.076000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179575.076000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.076000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.076000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179575.076000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[17179575.076000] usb usb2: configuration #1 chosen from 1 choice
[17179575.076000] hub 2-0:1.0: USB hub found
[17179575.076000] hub 2-0:1.0: 2 ports detected
[17179575.180000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179575.180000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.180000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.180000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.180000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[17179575.180000] usb usb3: configuration #1 chosen from 1 choice
[17179575.180000] hub 3-0:1.0: USB hub found
[17179575.180000] hub 3-0:1.0: 2 ports detected
[17179575.284000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[17179575.284000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[17179575.284000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.284000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.284000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179575.284000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.284000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.284000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[17179575.288000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.288000] usb usb4: configuration #1 chosen from 1 choice
[17179575.288000] hub 4-0:1.0: USB hub found
[17179575.288000] hub 4-0:1.0: 6 ports detected
[17179575.444000] Attempting manual resume
[17179575.472000] kjournald starting.  Commit interval 5 seconds
[17179575.472000] EXT3-fs: mounted filesystem with ordered data mode.
[17179587.696000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.700000] agpgart: Detected an Intel 855 Chipset.
[17179587.700000] agpgart: Detected 32636K stolen memory.
[17179587.708000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179588.000000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.004000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.068000] hw_random hardware driver 1.0.0 loaded
[17179588.244000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[17179588.276000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179588.372000] 8139too Fast Ethernet driver 0.9.27
[17179588.372000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179588.372000] eth0: RealTek RTL8139 at 0xde940000, 00:c0:9f:6c:b2:4a, IRQ 10
[17179588.372000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179588.384000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179588.472000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[17179588.472000] Yenta: CardBus bridge found at 0000:02:05.0 [103c:3084]
[17179588.472000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179588.472000] Yenta: Routing CardBus interrupts to PCI
[17179588.472000] Yenta TI: socket 0000:02:05.0, mfunc 0x01111112, devctl 0x64
[17179588.512000] ts: Compaq touchscreen protocol output
[17179588.704000] Yenta: ISA IRQ mask 0x00d8, PCI irq 11
[17179588.704000] Socket status: 30000006
[17179588.704000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179588.704000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179588.704000] cs: IO port probe 0x3000-0x3fff: clean.
[17179588.704000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179588.704000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179588.704000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179588.704000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179589.016000] intel8x0_measure_ac97_clock: measured 54111 usecs
[17179589.016000] intel8x0: clocking to 48000
[17179589.052000] cs: IO port probe 0x100-0x3af: clean.
[17179589.056000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179589.056000] cs: IO port probe 0x820-0x8ff: clean.
[17179589.056000] cs: IO port probe 0xc00-0xcf7: clean.
[17179589.056000] cs: IO port probe 0xa00-0xaff: clean.
[17179589.192000] lp: driver loaded but no devices found
[17179589.216000] Adding 1413680k swap on /dev/disk/by-uuid/9df9b6d4-f6b0-49f0-8de5-0b5a882b5e4b.  Priority:-1 extents:1 across:1413680k
[17179589.320000] EXT3 FS on hda1, internal journal
[17179590.744000] ACPI: AC Adapter [ACAD] (off-line)
[17179590.816000] ACPI: Battery Slot [BAT0] (battery present)
[17179590.836000] ACPI: Power Button (FF) [PWRF]
[17179590.836000] ACPI: Lid Switch [LID0]
[17179590.836000] ACPI: Power Button (CM) [PWRB]
[17179590.996000] ibm_acpi: ec object not found
[17179591.032000] pcc_acpi: loading...
[17179591.164000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179593.832000] [drm] Initialized drm 1.0.1 20051102
[17179593.832000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179593.836000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179593.836000] [drm] Initialized i915 1.5.0 20060119 on minor 1
[17179595.464000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179595.464000] apm: overridden by ACPI.
[17179599.080000] Bluetooth: Core ver 2.8
[17179599.080000] NET: Registered protocol family 31
[17179599.080000] Bluetooth: HCI device and connection manager initialized
[17179599.080000] Bluetooth: HCI socket layer initialized
[17179599.112000] Bluetooth: L2CAP ver 2.8
[17179599.112000] Bluetooth: L2CAP socket layer initialized
[17179599.144000] Bluetooth: RFCOMM socket layer initialized
[17179599.144000] Bluetooth: RFCOMM TTY layer initialized
[17179599.144000] Bluetooth: RFCOMM ver 1.7
[17179607.392000] NET: Registered protocol family 10
[17179607.392000] lo: Disabled Privacy Extensions
[17179607.392000] IPv6 over IPv4 tunneling driver
caroline@caroline-laptop:~$ 
```

This is the full dmesg text.

---

### Post by trubblemaker on 2007-01-18
this is wierd 'cause your card isn't detected at boot time but is later with lspci.  try and see if the native driver "sees" the card.  

in /etc/modprobe.d/blacklist comment out bcm43xx and add ndiswrapper for the test:

/etc/modprobe.d/blacklist
```
 
# blacklist bcm43xx
blacklist ndiswrapper

```

reboot  and see if their is an eth1 detected, if it's still not detected I'm pretty sure that your card has issues --> broken.

if it is detected you could try using the  native driver, check my signature

---

### Post by brainiac978 on 2007-01-18
The wireless connection now shows up.  Now I cannot use the wired connection to add the repositories.  Under Network Preferences it says "No Devices Found".  I am quickly losing what little patience I have left with this problem.  I'm just about ready to give up and go back to Windows.

---

### Post by trubblemaker on 2007-01-19
yeah I hear you with the frustrated ness if it shows up great it's being detected sounds like you need to adjust it's priority for now to use the wired connection do this:

```
sudo ifconfig eth1 down
```
 
then you should be able to use the wired connection.  

follow the instructions in my signature for the howto on the native driver.

or if this is an upgrade from dapper try "ndis from source" I have found it some instances where an upgrade was made from dapper people have issues with ndiswrapper, the generic package the 1.28 or 1.29 source seems to work out of the box.


Sorry to hear you utter the back to windows threat but I totally understand your frustration.

---

### Post by brainiac978 on 2007-01-19
It's not working.  I rebooted after that command, and still nothing.  I even tried the command with eth0 and it did not work.

---

### Post by trubblemaker on 2007-01-19
that really odd, obviously the fix is to blacklist the driver again, but this does point to some issues, can you post your dmesg when your eth1 isn't working it might help us hunt down the issue

---

### Post by brainiac978 on 2007-01-19
I would imagine the dmesg would be the same as the one I posted previously.  I don't know for sure if the eth1 has ever worked, but I do get a link light when I plug the cable in.

---

### Post by trubblemaker on 2007-01-19
no, it would have different data listed in it and may even tell you which driver's are conflicting.  dmesg that never changes it's a verbose output of your boot and running.  Hence loading different drivers like bcm43xx would change you dmesg.  your correct in 95% would be the same.  But the %5 that changed would be completely relevant material to your issue.  it might tell us that you have an IRQ issue with your two interfaces....

---

### Post by brainiac978 on 2007-01-19
Okay here is the dmesg again:

```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001dee0000 (usable)
[17179569.184000]  BIOS-e820: 000000001dee0000 - 000000001deec000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001deec000 - 000000001df00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001df00000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 478MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 122592
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 118496 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 HP                                    ) @ 0x000f6560
[17179569.184000] ACPI: RSDT (v001 HP     3084     0x06040000  LTP 0x00000000) @ 0x1dee67e7
[17179569.184000] ACPI: FADT (v001 HP     3084     0x06040000 PTL  0x00000050) @ 0x1deebed2
[17179569.184000] ACPI: BOOT (v001 HP     3084     0x06040000  LTP 0x00000001) @ 0x1deebfd8
[17179569.184000] ACPI: DSDT (v001 HP     3084     0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (013ca000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1296.923 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.436000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.436000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.452000] Memory: 476264k/490368k available (1910k kernel code, 13584k reserved, 1070k data, 308k init, 0k highmem)
[17179569.452000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.532000] Calibrating delay using timer specific routine.. 2595.93 BogoMIPS (lpj=5191872)
[17179569.532000] Security Framework v1.0.0 initialized
[17179569.532000] SELinux:  Disabled at boot.
[17179569.532000] Mount-cache hash table entries: 512
[17179569.532000] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.532000] CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.532000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.532000] CPU: L2 cache: 1024K
[17179569.532000] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.532000] Checking 'hlt' instruction... OK.
[17179569.548000] SMP alternatives: switching to UP code
[17179569.548000] Freeing SMP alternatives: 16k freed
[17179569.548000] checking if image is initramfs... it is
[17179570.260000] Freeing initrd memory: 5563k freed
[17179570.260000] ACPI: Core revision 20060707
[17179570.260000] ACPI: Looking for DSDT ... not found!
[17179570.260000] ACPI: setting ELCR to 0200 (from 0c20)
[17179570.288000] CPU0: Intel(R) Celeron(R) M processor         1.30GHz stepping 06
[17179570.288000] SMP motherboard not detected.
[17179570.288000] Local APIC not detected. Using dummy APIC emulation.
[17179570.288000] Brought up 1 CPUs
[17179570.288000] migration_cost=0
[17179570.288000] NET: Registered protocol family 16
[17179570.288000] EISA bus registered
[17179570.288000] ACPI: bus type pci registered
[17179570.288000] PCI: PCI BIOS revision 2.10 entry at 0xfd9a2, last bus=2
[17179570.288000] PCI: Using configuration type 1
[17179570.288000] Setting up standard PCI resources
[17179570.308000] ACPI: Interpreter enabled
[17179570.308000] ACPI: Using PIC for interrupt routing
[17179570.308000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.308000] PCI: Probing PCI hardware (bus 00)
[17179570.312000] Boot video device is 0000:00:02.0
[17179570.312000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179570.312000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179570.312000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.312000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.312000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.312000] Please report the result to linux-kernel to fix this permanently
[17179570.312000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.316000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.316000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[17179570.316000] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[17179570.316000] ACPI: PCI Interrupt Link [LNKC] (IRQs *11)
[17179570.316000] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[17179570.320000] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[17179570.320000] ACPI: PCI Interrupt Link [LNKF] (IRQs 11) *0, disabled.
[17179570.320000] ACPI: PCI Interrupt Link [LNKG] (IRQs 11) *0, disabled.
[17179570.320000] ACPI: PCI Interrupt Link [LNKH] (IRQs *11)
[17179570.320000] ACPI: Embedded Controller [H_EC] (gpe 29) interrupt mode.
[17179570.324000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.324000] pnp: PnP ACPI init
[17179570.328000] pnp: PnP ACPI: found 7 devices
[17179570.328000] PnPBIOS: Disabled by ACPI PNP
[17179570.328000] PCI: Using ACPI for IRQ routing
[17179570.328000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.332000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.332000] PCI: Bus 3, cardbus bridge: 0000:02:05.0
[17179570.332000]   IO window: 00003400-000034ff
[17179570.332000]   IO window: 00003800-000038ff
[17179570.332000]   PREFETCH window: 30000000-31ffffff
[17179570.332000]   MEM window: 34000000-35ffffff
[17179570.332000] PCI: Bridge: 0000:00:1e.0
[17179570.332000]   IO window: 3000-3fff
[17179570.332000]   MEM window: e0200000-e02fffff
[17179570.332000]   PREFETCH window: 30000000-31ffffff
[17179570.332000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.332000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[17179570.332000] PCI: setting IRQ 11 as level-triggered
[17179570.332000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[17179570.332000] NET: Registered protocol family 2
[17179570.368000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.368000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.368000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.368000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.368000] TCP reno registered
[17179570.368000] Simple Boot Flag at 0x36 set to 0x1
[17179570.368000] audit: initializing netlink socket (disabled)
[17179570.368000] audit(1169126735.368:1): initialized
[17179570.368000] VFS: Disk quotas dquot_6.5.1
[17179570.368000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.368000] Initializing Cryptographic API
[17179570.368000] io scheduler noop registered
[17179570.368000] io scheduler anticipatory registered
[17179570.368000] io scheduler deadline registered
[17179570.368000] io scheduler cfq registered (default)
[17179570.368000] isapnp: Scanning for PnP cards...
[17179570.724000] isapnp: No Plug & Play device found
[17179570.752000] Real Time Clock Driver v1.12ac
[17179570.752000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.752000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179570.752000] PCI: setting IRQ 5 as level-triggered
[17179570.752000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179570.752000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179570.752000] mice: PS/2 mouse device common for all mice
[17179570.752000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.752000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.752000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.756000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PSM2] at 0x60,0x64 irq 1,12
[17179570.760000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.760000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.760000] EISA: Probing bus 0 at eisa.0
[17179570.760000] Cannot allocate resource for EISA slot 1
[17179570.760000] Cannot allocate resource for EISA slot 2
[17179570.760000] Cannot allocate resource for EISA slot 3
[17179570.760000] EISA: Detected 0 cards.
[17179570.764000] TCP bic registered
[17179570.764000] NET: Registered protocol family 1
[17179570.764000] NET: Registered protocol family 8
[17179570.764000] NET: Registered protocol family 20
[17179570.764000] Using IPI No-Shortcut mode
[17179570.764000] ACPI: (supports S0 S3 S4 S5)
[17179570.764000] Freeing unused kernel memory: 308k freed
[17179570.852000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.900000] Capability LSM initialized
[17179571.936000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179571.940000] ACPI: Thermal Zone [THRM] (35 C)
[17179572.280000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179572.280000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179572.280000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179572.280000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179572.280000] ICH4: chipset revision 3
[17179572.280000] ICH4: not 100% native mode: will probe irqs later
[17179572.280000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179572.284000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
[17179572.284000] Probing IDE interface ide0...
[17179572.572000] hda: HITACHI_DK23FA-40, ATA DISK drive
[17179573.244000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.248000] Probing IDE interface ide1...
[17179573.984000] hdc: PHILIPS CD-RW/DVD-ROM CDD5263, ATAPI CD/DVD-ROM drive
[17179574.656000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.660000] hda: max request size: 128KiB
[17179574.668000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179574.668000] hda: cache flushes supported
[17179574.668000]  hda: hda1 hda2 < hda5 >
[17179574.736000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179574.736000] Uniform CD-ROM driver Revision: 3.20
[17179574.972000] usbcore: registered new driver usbfs
[17179574.972000] usbcore: registered new driver hub
[17179574.972000] USB Universal Host Controller Interface driver v3.0
[17179574.972000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179574.972000] PCI: setting IRQ 10 as level-triggered
[17179574.972000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179574.972000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.972000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.972000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.972000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001820
[17179574.972000] usb usb1: configuration #1 chosen from 1 choice
[17179574.972000] hub 1-0:1.0: USB hub found
[17179574.972000] hub 1-0:1.0: 2 ports detected
[17179575.076000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179575.076000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179575.076000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.076000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.076000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179575.076000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[17179575.076000] usb usb2: configuration #1 chosen from 1 choice
[17179575.076000] hub 2-0:1.0: USB hub found
[17179575.076000] hub 2-0:1.0: 2 ports detected
[17179575.180000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179575.180000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.180000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.180000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.180000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[17179575.180000] usb usb3: configuration #1 chosen from 1 choice
[17179575.180000] hub 3-0:1.0: USB hub found
[17179575.180000] hub 3-0:1.0: 2 ports detected
[17179575.284000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[17179575.284000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[17179575.284000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.284000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.284000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179575.284000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.284000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.284000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[17179575.288000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.288000] usb usb4: configuration #1 chosen from 1 choice
[17179575.288000] hub 4-0:1.0: USB hub found
[17179575.288000] hub 4-0:1.0: 6 ports detected
[17179575.444000] Attempting manual resume
[17179575.472000] kjournald starting.  Commit interval 5 seconds
[17179575.472000] EXT3-fs: mounted filesystem with ordered data mode.
[17179587.696000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.700000] agpgart: Detected an Intel 855 Chipset.
[17179587.700000] agpgart: Detected 32636K stolen memory.
[17179587.708000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179588.000000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.004000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.068000] hw_random hardware driver 1.0.0 loaded
[17179588.244000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[17179588.276000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179588.372000] 8139too Fast Ethernet driver 0.9.27
[17179588.372000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179588.372000] eth0: RealTek RTL8139 at 0xde940000, 00:c0:9f:6c:b2:4a, IRQ 10
[17179588.372000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179588.384000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179588.472000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[17179588.472000] Yenta: CardBus bridge found at 0000:02:05.0 [103c:3084]
[17179588.472000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179588.472000] Yenta: Routing CardBus interrupts to PCI
[17179588.472000] Yenta TI: socket 0000:02:05.0, mfunc 0x01111112, devctl 0x64
[17179588.512000] ts: Compaq touchscreen protocol output
[17179588.704000] Yenta: ISA IRQ mask 0x00d8, PCI irq 11
[17179588.704000] Socket status: 30000006
[17179588.704000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179588.704000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179588.704000] cs: IO port probe 0x3000-0x3fff: clean.
[17179588.704000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179588.704000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179588.704000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179588.704000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179589.016000] intel8x0_measure_ac97_clock: measured 54111 usecs
[17179589.016000] intel8x0: clocking to 48000
[17179589.052000] cs: IO port probe 0x100-0x3af: clean.
[17179589.056000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179589.056000] cs: IO port probe 0x820-0x8ff: clean.
[17179589.056000] cs: IO port probe 0xc00-0xcf7: clean.
[17179589.056000] cs: IO port probe 0xa00-0xaff: clean.
[17179589.192000] lp: driver loaded but no devices found
[17179589.216000] Adding 1413680k swap on /dev/disk/by-uuid/9df9b6d4-f6b0-49f0-8de5-0b5a882b5e4b.  Priority:-1 extents:1 across:1413680k
[17179589.320000] EXT3 FS on hda1, internal journal
[17179590.744000] ACPI: AC Adapter [ACAD] (off-line)
[17179590.816000] ACPI: Battery Slot [BAT0] (battery present)
[17179590.836000] ACPI: Power Button (FF) [PWRF]
[17179590.836000] ACPI: Lid Switch [LID0]
[17179590.836000] ACPI: Power Button (CM) [PWRB]
[17179590.996000] ibm_acpi: ec object not found
[17179591.032000] pcc_acpi: loading...
[17179591.164000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179593.832000] [drm] Initialized drm 1.0.1 20051102
[17179593.832000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179593.836000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179593.836000] [drm] Initialized i915 1.5.0 20060119 on minor 1
[17179595.464000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179595.464000] apm: overridden by ACPI.
[17179599.080000] Bluetooth: Core ver 2.8
[17179599.080000] NET: Registered protocol family 31
[17179599.080000] Bluetooth: HCI device and connection manager initialized
[17179599.080000] Bluetooth: HCI socket layer initialized
[17179599.112000] Bluetooth: L2CAP ver 2.8
[17179599.112000] Bluetooth: L2CAP socket layer initialized
[17179599.144000] Bluetooth: RFCOMM socket layer initialized
[17179599.144000] Bluetooth: RFCOMM TTY layer initialized
[17179599.144000] Bluetooth: RFCOMM ver 1.7
[17179607.392000] NET: Registered protocol family 10
[17179607.392000] lo: Disabled Privacy Extensions
[17179607.392000] IPv6 over IPv4 tunneling driver
caroline@caroline-laptop:~$
```

---

### Post by trubblemaker on 2007-01-20
as you dmesg says try adding "pci=routeirq" to your boot paramters in /boot/grub/menu.lst.

---

### Post by brainiac978 on 2007-01-20
Well, I would but it's too late.  I've gone back to Windows.  Thank you for all your help, I just don't have that kind of patience.  Hopefully this will help someone else.  I would like to look at Ubuntu again sometime in the future, especially if they can get full support for this card.  thanks again.

---

### Post by trubblemaker on 2007-01-20
the card is supported and it works, I use it every day.   All methods to get it running do require manual installation.  But if you look around these forums you'll find atleast 4 threads (alive and used daily) that  are dedicated to this driver.  I know I read/post to them daily.  Hope to see you in the Ubuntu world again sometime

---

### Post by jctaft on 2007-01-21
It didn't work for me.  Everything went through fine, with the same outputs you suggested, but at the end, it just didn't work.  I can't even turn my wireless card on.

any other suggestions?  

j

---

### Post by chrido64 on 2007-01-22
it seemed to work fine after the first reboot, the network manger showed a few different networks, including mine. but impossible to get an ip address!!
in the network settings my wireless connection appears as wlan0 now!

after the following reboot, network manager doesn't show the "enable wireless option any more".
and now wlan0 is again eth1(?)
so i installed wifi-radar, which shows networks, but still cannot connect to any network

any idea?

---

### Post by Helmi on 2007-01-22
i nearly got the same problem than chrido64 has. 

I alread had the same connection problem with the fwcutter version yesterday. Everything seems to be fine except the connection part. Wlan is okay - can connect without problems under windows.

---

### Post by ubunturules on 2007-01-28
did you get it working?

ubunturules

---

### Post by sephirothsigep on 2007-01-31
alright i have eth1 instead of wlan0 and i was going to fix this when i saw that it was possible under the solutions to problems section > problem 1 and then when i opened my ndiswrapper file i found it to be empty. also my interfaces file was empty as well. the only one that has anything in it is the iftab file and it contains the following: 

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:12:3f:d8:6b:44 arp 1
eth1 mac 00:90:96:bb:34:2f arp 1

Is this a problem and could this explain why my wireless will work for about 20 min and then just stops working. and i then have to disable and re enable it to work again

EDIT: well that 20 min seems to be the time that my administrative privileges are active on the connection. i have began to notice that when i lose connection i have to re-enter my password. i still have to go throuhg the same steps to get it to work

---

### Post by tim.tadh on 2007-02-01
YES! my wireless is working. thank you for posting this howto it worked the first time!

tim

---

### Post by Derspankster on 2007-02-02
Well, this has been a minor disaster, likely from my own doing. After following your tutorial **I no longer even have wireless as an option in Network Manager**. I'm sure I've screwed something up but at this point I'm not sure what. First I checked my hardware;

$ lspci | grep Broadcom\ Corporation
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I installed the driver next because I already had ndiswrapper installed. When I tried to enable the driver, I get an invalid driver message.

ndiswrapper -l

Installed drivers:
bcmwl5  invalid driver!

The driver is installed but something has gone wrong somewhere. Help! My wired connection is working fine.

---

### Post by ubunturules on 2007-02-06
go to home.nc.rr.com/thehinnants/stuff/drivers and download the set of drivers that you need.  the ones on the top are the 64 bit and the ones on the bottom are the 32 bit.

now remove the invalid driver
```
sudo ndiswrapper -e bcmwl5
```

now make sure the invalid driver is removed
```
sudo ndiswrapper -l
```

now install the driver you downloaded from the website
```
sudo ndiswrapper -i bcmwl5.inf
```

now check and see if the driver is valid and the hardware is present
```
sudo ndiswrapper -l
```

now check and see if it shows up in Network Manager.  If it doesn't then restart your computer and see if it works.

ubunturules

---

### Post by xubu_caapn on 2007-02-10
hey everyone, i was running through the tutorial smoothly and after i installed ndiswrapper through the ubuntu 6.06 live cd, i tried installing the 32bit drivers supplied through the link. this has repeatedly been my results:

```
sudo ndiswrapper -i ~/bcmwl5/bcmwl5.inf
installing bcmwl5
couldn't copy /home/brandon/bcmwl5/bcmwl5.inf at usr/sbin/ndiswrapper line 135.

```

```
sudo ndiswrapper -l
installed ndiswrapper drivers:
bcmwl5   invalid driver!
```

then i just end up uninstalling the driver

```
sudo ndiswrapper -e bcmwl5
```

after days of trying to get my wireless working this tutorial seemed pretty solid until i reached this point. i'm starting to think it's something on my end. :(

and yes, i have a broadcom 4306.
thanks for the help!

---

### Post by Detonate on 2007-02-11
I started out about 6 hours ago trying to get my broadcom wireless working.  I got ndiswrapper installed and followed all the instructions.  But it didn't work.  I was having the eth1 show as the wireless connector problem and thanks to this thread, I got it fixed.  My deepest appreciation for all the hard work some of you do to help others.
I now have wlan0 running like a scalded dog:) 

Now I just have to figure out how to get my security turned back on.
   
Floyd
Kubuntu Edgy on my desktop and laptop now.

---

### Post by Tenroh on 2007-02-11
I seem to of run into a bit of a snag.  I can atleast detect wireless networks [which is an improvement considering I thought this card was dead].  I currently have the wireless device as eth1 and tried to rename it to wlan0 [by following the steps in the problems] but with no success. /modprobe.d/ndiswrapper already had wlan0 so I went to /etc/iftab and changed eth1 to wlan0 but when I go to /etc/network/interfaces there's a listing for both a wlan0 and eth1:
 ```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0

```
If I edit it to get rid of wlan0's entry and rename eth1's to wlan0 the device still isn't renamed to wlan0, it still reads eth1 and won't activate.

The network I'm trying to connect to has no security whatsoever.  Is there a way to tell where it hangs?

Two restarts later Network Manager no longer displays wireless as an option - WTF!  It now displays this in /etc/network/interfaces and the wireless connection displays as wlan0.
```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
```

---

### Post by HotFoot on 2007-02-12
Hi,

Thanks for the guide.  I'd like some additional help, as I run into a problem at step 9 - 10.  I'm using a Linksys PCI wireless card with the Broadcom 4306 controller.  I have Edgy installed, with kernel 2.6.7-11-generic (64-bit).

Everything seems to be working fine up to step 8.  For instance, step 7 appears as:

```
scott@Scott-Desktop:~$ ndiswrapper -l
Installed drivers:
netbc564                driver installed, hardware present
```

Step 8 appears to execute normally, but when I run step 9, I get the following output.  I cannot continue the installation until this is resolved.

```
scott@Scott-Desktop:~$ sudo modprobe ndiswrapper
Password:
Killed
scott@Scott-Desktop:~$ 
Message from syslogd@Scott-Desktop at Mon Feb 12 02:04:51 2007 ...
Scott-Desktop kernel: [  387.318882] Oops: 0002 [1] SMP 

Message from syslogd@Scott-Desktop at Mon Feb 12 02:04:51 2007 ...
Scott-Desktop kernel: [  387.320263] CR2: 0000000000000000

Message from syslogd@Scott-Desktop at Mon Feb 12 02:04:51 2007 ...
Scott-Desktop kernel: [  387.321075] Oops: 0002 [2] SMP 

Message from syslogd@Scott-Desktop at Mon Feb 12 02:04:51 2007 ...
Scott-Desktop kernel: [  387.321607] CR2: 0000000000000000
```

Any help is much appreciated, as I would like to have my computer wire-free in the living room.

---

### Post by ubunturules on 2007-02-16
can anybody help him out?

ubunturules

---

### Post by trubblemaker on 2007-02-16
well if you reboot ndiswrapper will load on it's own, to check if it did load after rebooting:

```
dmesg | grep ndis
```

it's a we bit concerning that you get such errors, on a modprobe.  Are you using a custom kernel?  Have you rebooted since?  Checking dmesg right now would probably give additional information.

....

I say reboot,

check dmesg 

if all looks like it loaded

 carry on the steps from where you left off

---

### Post by HotFoot on 2007-02-16
Hi trubblemaker,

Thanks for the help.  I have rebooted my computer several times since I attempted installation of the wireless drivers (dual-boot machine and I go into WinXP regularly).  As you suggested, I checked dmesg, but there was no output.

```
scott@scott-Desktop:~$ dmesg | grep ndis
scott@scott-Desktop:~$ sudo dmesg | grep ndis
Password:
scott@scott-Desktop:~$ 
```

What does the lack of output from the command mean?

P.S. Is it possible to set up email notification of when someone responds to a thread on which you've posted?  I was just lucky to happen to check this thread shortly after your post.

---

### Post by Kulgan on 2007-02-16
> Can anyone help him out

Hm... I think you are the 1337 one on the subject here :P 

I just installed fedora core 6, and had issues with the firmware not being present, rather than the drivers (though it was for a different card), and got similar errors. Could this be something similar?

-K

---

### Post by trubblemaker on 2007-02-16
> **HotFoot said:**
> Hi trubblemaker,

Thanks for the help.  I have rebooted my computer several times since I attempted installation of the wireless drivers (dual-boot machine and I go into WinXP regularly).  As you suggested, I checked dmesg, but there was no output.

```
scott@scott-Desktop:~$ dmesg | grep ndis
 
```

this is bad, this means that ndiswrapper isn't loading at boot, it's not even setup to.

I'd strongly encourage you to actually download and install from source, that way you get a more advanced stable version of ndiswrapper, and it's tailor made for your kernel.  If you want their is a link in my signature.  Remember that things take time to make it into stable Ubuntu, so it's not actually the most update source for programs.

If you don't want to but get the same error every time you try 
```
modprobe ndiswrapper
```
reproduce the error then run dmesg and post that output.  This should give some hints as to where the issue is, likely I think it will be fixed with a source install.

> **HotFoot said:**
> 
P.S. Is it possible to set up email notification of when someone responds to a thread on which you've posted?  I was just lucky to happen to check this thread shortly after your post.
You can alter your settings by clicking on "private messages" (top right corener) and changing it so that if you post to a thread you get an "instant email"


as a final note, this tutorial is great and works really well for people, it's requires less steps than installing from source, and is great for people that want a quick method that works.  It also as a bonus continues to work after a kernel upgrade.  (Most times anyways.) 

Installing from source is more involved but is better tailored for your computer system.  It does have the draw back that you need to re-install whenever you upgrade your kernel. not an issue if you keep your install folder.

---

### Post by HotFoot on 2007-02-16
Okay, I've made some progress following trubblemaker's instructions on installing ndis from source.  I believe ndiswrapper is now functioning, and I do indeed see my wireless network connection under System>>Administration>>Networking.  However, I've had some problems...

Once everything was installed, I went into the Networking settings and disabled the ethernet connection.  Then I enabled the wireless connection and entered the ssid and wep encryption key.  Wireless was then working.  I unplugged the ethernet cable and continued browsing around online.  Then, to see if the wireless would come online during startup, I added 'ndiswrapper' to '/etc/modules' and rebooted the computer.  After restarting, I checked "dmesg | grep ndis" and it looked to be working.  I went back into Networking setup and found that my wireless was detected, but not configured....

Thinking that this may be because I use WEP encryption, I followed steps 13-16 of this thread and rebooted.  The network manager that now sits at the top-right of my screen does not detect my wireless connection, even though I can see it under the Networking setup.  If I manually enable the wireless connection and disable the wired connecting, I become unable to connect to the network/internet.  It seems that after a brief period of having wireless working, it's gone agian.  What may I have done wrong?

I played around with changing the "eth1" to "wlan0" in the files:
sudo gedit /etc/modeprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab,
but the first of these files does not exist on my computer (I presume that's because of the building ndis from source).  When this didn't work (after reboot), I changed all the "wlan0" back to "eth1".

In case it matters, the output of "dmesg | grep ndis" is below:

```
scott@Scott-Desktop:~$ dmesg | grep ndis
[   33.899837] ndiswrapper version 1.37 loaded (preempt=no,smp=yes)
[   33.988056] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   33.989052] ndiswrapper: driver netbc564 (,10/01/2002,3.70.17.5) loaded
[   33.993586] ndiswrapper: using IRQ 74
[   34.601761] usbcore: registered new driver ndiswrapper
[   34.604508] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
```
_________________________________________

A few hours later:  It seems that whatever the problem is, having booted into Windows and back to ubuntu since my last post has cleared up the problem.  The network manager icon now allows me to select my wireless network.  I wasn't able to connect using WEP encryption, so I have this disabled now.  I'm relying solely on MAC address filtering at this point, and I hope that's good enough to keep the casual threat at bay.  Thanks everyone for the help!

---

### Post by fallasteeni on 2007-02-17
Hi All,

I read a significant portion of this topic, but please forgive me if I missed anything (after all it is 46 pages long).

I followed the guide step by step, but I'm still stuck at a no-go. 

1.) I don't see wlan0 anywhere (not even after a reboot, or after unplugging the wired connection and rebooting)

2.) ndiswrapper 1.8 is installed, and so is bcmwl5 driver. ndiswrapper -l lists that the driver is installed and hardware is present.

3.) /etc/modprobe, /etc/modprobe.d and /etc/interfaces have all been updated, and there IS an alias for wlan0 in modprobe.d

4.) If i try ifconfig wlan0 I get:

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

ALSO NOTE:

lspci | grep Broadcom returns:

00.09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

ALSO NOTE:

Running Ubuntu 6.10 Edgy Eft.


HELP?

---

### Post by martinquested on 2007-02-19
This sort-of did the job for me.  I had my internal wireless card working fine on my Compaq Presario V6030US (V6000 series) until a few days ago - I think it coincided with the latest kernel update.

I had to use the trick you've added at the bottom of the post, where ndiswrapper1.18 is used instead.

I say "sort-of", because the wireless card is now working again, but the signal strength for all SSIDs is shown at 99% or 100%, which cannot be right (and I have verified elsewhere that this is not true).  It's odd; I've never seen that before.

---

### Post by mhoskins on 2007-02-19
It helped me check this installation off my list and get me off the "bad list" with my wife who now has her Sony Vaio back. You rock - Thank you!

---

### Post by ubunturules on 2007-02-20
mhoskins: awesome! glad to hear that you got it working.

---

### Post by conorfrance on 2007-02-25
Hello

I'm using ndiswrapper on my inspiron 8600 with a broadcom 4306 card, and having followed the instructions here it seems to be working (using iwconfig I get no error messages and the right MAC address for my US robotics router), but the stupid thing won't connect to the router. What am I doing wrong? Surely something simple?

Anyone have any ideas?

conor

---

### Post by martinquested on 2007-02-25
This is a really dumb-sounding answer, but after I've set everything up and got everything as it ought to be working (but isn't), often the only thing I have left to do is disconnect the power from the router for a minute or two and then reconnect it.  Sounds stupid but after messing around with the settings sometimes it gets attached to something I've since changed, and it hasn't noticed.

I admit it's a bit of a Microsoft style solution to the problem but it actually does work.  For me at least.  If only I had thought of it sooner.

No other obvious ideas based on the information you provide - provide some more info about what exactly doesn't work, what you see when you type ifconfig and so on, and I might get some better ideas...

---

### Post by ubunturules on 2007-03-01
that's what I have to do in Windows sometimes when it doesn't connect to my wireless network.  I've never had to do it under linux.  Right now I'm running Feisty and I'm still trying to get wireless working so I can see if there is anything different you have to do in Feisty or not.  I probably need to do a fresh install since I've been running it since like Herd 3 I think and they just came out with the restricted modules package and everything.  If anybody has got wireless working with ndiswrapper under Feisty please give me advice of to how you did it.  thanks

ubunturules

---

### Post by teaker1s on 2007-03-04
until I ditched feisty, for debian etch- I installed these(see screen shot)

---

### Post by ubunturules on 2007-03-04
I just installed Herd 5 today and I am pleased to say that this guide now officially works with Feisty!

---

### Post by IkimashoZ on 2007-03-07
Hello everyone.  I recently installed ubuntu, and I'm desperately trying to get ubuntu and my wireless card to work together.  My wired connection is due to be cut off any day now.

I have an Inspiron 2200 laptop with broadcom card:
> ikimashoz@MaiPasokon:~$ lspci | grep Broadcom\ Corporation
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

I followed the instructions on the first message in this thread and was fine up until the *ndiswrapper -l* command, which instead of producing the expected response of "driver present, hardware present", only gave "driver installed".

I have no wlan0 option in Connection Properties and the wireless card icon is gone in System -> Administration -> Networking.  Please help!

---

### Post by endorphinadam on 2007-03-08
I'm getting the message:  "sudo: ndiswrapper: command not found" after the command:  "sudo ndiswrapper -i ~/home/adam/Desktop/bcmwl5.inf"

any ideas?

I tried reinstalling ndiswrapper just in case and got this: "ndiswrapper-utils-1.8 is already the newest version."  I assume that means it is properly installed.

Can anyone help me free myself of this *&^%^ Ethernet cable???

---

### Post by IkimashoZ on 2007-03-08
I got mine working last night finally.

Endorphinadam: What card do you have exactly?  Do an "lspci | grep Broadcom\ Corporation" to find out.  I have a 4309, and the steps that worked for me seemed to be these:

1. I had to remove the existing ubuntu wlan drivers and blacklist them so they don't startup again on restart.

2. Then I had to get not bcmwl5.inf, but rather *bcmwl5a.inf* from windows and put it on my desktop.  Finally, when I tried to bind that file to ndiswrapper, I got the correct message when I tried the command "ndiswrapper -l".  If it works you'll see "hardware present, driver installed".  Otherwise you'll just see "driver installed".

There could have been other factors though.  I was trying a lot of different how-to's.

---

### Post by ubunturules on 2007-03-12
The drivers posted in the first post are for the Broadcom 4306 chipset but they do work with other bcm43xx cards.  I know they don't work with 4309 and I can't think of any others right now.

ubunturules

---

### Post by ubunturules on 2007-03-20
Is anybody having any problems with this guide because no one has posted in about a week.

ubunturules

---

### Post by donniebnyc on 2007-03-20
I am brand new to ubuntu.  I just installed Edgy without a hitch.  My wired connection works but the wpc54gs wireless is not.  I followed the directions but now I get this in terminal:

[INDENT]donniebnyc@donniebnyc-t40:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
donniebnyc@donniebnyc-t40:~$ sudo ndiswrapper -e home/donniebnyc/bcmwl5.inf Driver home/donniebnyc/bcmwl5.inf is not installed.Use -l to list installed drivers
donniebnyc@donniebnyc-t40:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver![/INDENT]


Any ideas?

---

### Post by ubunturules on 2007-03-20
get the drivers from the first post. they should work.

ubunturules

---

### Post by iamtherealwoody on 2007-03-20
Maybe some usefull info.  Using Feisty Herd 5, Broadcom 4306.  This does NOT work with ndiswrapper-utils-1.8-  Took me a whole day to figure that out.  Had it working absolutely  perfectly with feisty, then i messed around with the restricted drivers manager, couldnt get my resolution back, figured the easiest way was to reinstall feisty.  Long story short, use ndiswrapper-utils-1.9 
Dont know if that is already known.

Matt

---

### Post by donniebnyc on 2007-03-21
> **ubunturules said:**
> get the drivers from the first post. they should work.

ubunturules


I am using the drivers from the first post.

---

### Post by ubunturules on 2007-03-21
iamtherealwoody: thank you I will put this in the first post.

donniebnyc: are you sure you have the 4306 chipset. run the following command and post the output.

```
lspci | grep Broadcom\ Corporation
```

---

### Post by donniebnyc on 2007-03-21
donniebnyc@donniebnyc-t40:~$ lspci | grep Broadcom\ Corporation
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by benson2788 on 2007-03-21
Hello all.  I had some difficulties using this on Ubuntu AMD64 on my computer.  Using any 64-bit driver would not allow "sudo modprobe ndiswrapper" to work.  My specific card is a linksys WMP54g, running a broadcom 4306 chip.  The CPU is an athlon64 3500+ if it matters.  I didn't get any of the error messages in the first post, just odd messages, with at least one ending in [oops].  There were 4 sets of 3 lines each, one blank, one message and one ending in a word in []'s.  I apologize for not having a copy of the message, but I had to reinstall in i386 to get any internet.  Any answers would be appreciated.

---

### Post by donniebnyc on 2007-03-23
I wiped the hard drive with DBAN, reinstalled edgy, and downloaded updates.  I downloaded the driver from the first post and followed the steps as listed. Here is my terminal log:

[INDENT]donniebnyc@donniebnyc-t40:~$ lspci | grep Broadcom\ Corporation
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
donniebnyc@donniebnyc-t40:~$ sudo rmmod bcm43xx
Password:
donniebnyc@donniebnyc-t40:~$ sudo gedit /etc/modprobe.d/blacklist
{I altered the file as directed.}
donniebnyc@donniebnyc-t40:~$ sudo apt-get install ndiswrapper-utils-1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ndiswrapper-common
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.8
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 42.6kB of archives.
After unpacking 213kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main ndiswrapper-common 1.18-1ubuntu2 [13.7kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main ndiswrapper-utils-1.8 1.18-1ubuntu2 [29.0kB]
Fetched 42.6kB in 0s (64.2kB/s)            
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 107108 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.18-1ubuntu2_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.8.
Unpacking ndiswrapper-utils-1.8 (from .../ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb) ...
Setting up ndiswrapper-common (1.18-1ubuntu2) ...
Setting up ndiswrapper-utils-1.8 (1.18-1ubuntu2) ...
donniebnyc@donniebnyc-t40:~$ sudo ndiswrapper -i home/donniebnyc/bcmwl5.infInstalling bcmwl5
couldn't copy home/donniebnyc/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144.
donniebnyc@donniebnyc-t40:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
donniebnyc@donniebnyc-t40:~$ [/INDENT]

Any help will be appreciated.

---

### Post by ubunturules on 2007-03-23
did you try using the drivers that came with your cd?

ubunturules

---

### Post by psb007 on 2007-03-23
This is totally outstanding, thank you, thank you, thank you. This was by far the easiest thing to do. After 4 re-installs and numerous help pages i found this page. It total worked *with a little help from problem #1* hehe.          

Thanks Again!:guitar:

---

### Post by johanlol on 2007-03-24
The guide worked perfect. I have a network with MAC Address filtering and WPA PSK. After a week of not getting anywhere, I followed the steps in the guide and it worked in less than 15 minutes.

Johan

---

### Post by donniebnyc on 2007-03-24
> **ubunturules said:**
> did you try using the drivers that came with your cd?

ubunturules

I assumed I should uninstall before I tried a new driver and got this:

[INDENT]donniebnyc@donniebnyc-t40:~$ sudo ndiswrapper -e home/donniebnyc/bcmwl5.inf
Driver home/donniebnyc/bcmwl5.inf is not installed.Use -l to list installed drivers
donniebnyc@donniebnyc-t40:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
donniebnyc@donniebnyc-t40:~$ [/INDENT]

I'm confused.  Is it installed or not?

I downloaded the drivers from Linksys for my WPC54GS.  It's the same file, bcmwl5.sys, but with a different date and a different inf file, lsbcmnds.inf.  I have a choice of drivers for 9x and NT.  Do you know which I should use?

---

### Post by ubunturules on 2007-03-24
To remove the one you have in there right now run this
```
sudo ndiswrapper -e home/donniebnyc/bcmwl5
```

now run this to make sure you don't have anything installed
```
ndiswrapper -l
```

now install the drivers you got from the website

---

### Post by donniebnyc on 2007-03-24
donniebnyc@donniebnyc-t40:~$ sudo ndiswrapper -e home/donniebnyc/bcmwl5
Password:
Driver home/donniebnyc/bcmwl5 is not installed.Use -l to list installed drivers
donniebnyc@donniebnyc-t40:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
donniebnyc@donniebnyc-t40:~$

---

### Post by ubunturules on 2007-03-24
i see the problem

```
cd /home/donniebnyc
```
```
sudo ndiswrapper -e bcmwl5
```
```
ndiswrapper -l
```

now install the drivers you got from linksys

---

### Post by kurbacik on 2007-03-25
One of the problems I had with network-manger-gnome is that the signal strength of the wireless access points were all at 100%, which clearly doesn't help you decide which access point to use. I compiled the latest version of ndiswrapper (1.39) on my laptop (an HP zv5000 which uses a Broadcom 4306 wireless card, on Edgy i386) and now signal strength shows up correct! Awesome!

---

### Post by donniebnyc on 2007-03-26
The directory change fixed the uninstall problem, so I used it to re-install the same driver, and it worked.

[INDENT]donniebnyc@donniebnyc-t40:~$ cd /home/donniebnyc
donniebnyc@donniebnyc-t40:~$ sudo ndiswrapper -e bcmwl5
Password:
donniebnyc@donniebnyc-t40:~$ ndiswrapper -l
No drivers installed
donniebnyc@donniebnyc-t40:~$ sudo ndiswrapper -i bcmwl5.inf
Installing bcmwl5
donniebnyc@donniebnyc-t40:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present [/INDENT]

Everything from there on worked.  Thanks!!

I have another question.  I accidentally entered my WPA key, which is very long, in as the default keyring password.  I'd like to change the keyring password to something more manageable.  I can't find where to do this.  Is there a file I have to edit?

Don

---

### Post by neoncode on 2007-03-26
Worked perfectly with my Broadcom BCM4318. I had to download the drivers for my laptop model from the Acer website. (My laptop's an Acer)
I'm on Feisty and now I can connect to my WPA encrypted network with no problems.

---

### Post by HippyFoot on 2007-03-26
I seem to have a problem with this and every other tutorial I try and I can't seem to find any information on fixing it. Whenever I get to the last step and go to Networks to enable my wireless card, it is no longer recognized. Its a bummer! Any Ideas or blatantly obvious things I missed? Any help would be great! Thanks! (my card is a broadcom4306 btw)

---

### Post by wscheer on 2007-03-27
donniebnyc,

I had a problem similar to what your have.
Everytime i ran "ndiswrapper -l" I got bcmwl5 invalid driver

For me, the fix was to run all the commands where I had saved the bcmwl5.inf bcmwl5.sys files.

I saved my two files on the /home/wscheer/Desktop/
When I installed the drivers and ran the ndiswrapper commands I was in the root dir.

Try doing a
```

cd Desktop
```

Then reinstall the drivers. Thats what worked for me.

* only do "cd Desktop" if you saved those files on your desktop ;-)

---

### Post by iamtherealwoody on 2007-03-27
Nevermind, I fixed it.

---

### Post by ubunturules on 2007-03-28
donniebnyc: go to System -> Adminstration -> Keyring Manager

---

### Post by saracen on 2007-03-31
I'm on Feisty and I get the FATAL error:```
saracen@acer:~$ sudo modprobe ndiswrapper 
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```
I tried the proposed fix given in the original post but it doesn't work... :confused:

---

### Post by ubunturules on 2007-03-31
saracen: since you are using feisty im assuming you are using ndiswrapper-utils-1.9 so make sure you substitute ndiswrapper-utils-1.9 everywhere you see ndiswrapper-utils-1.8

---

### Post by ubunturules on 2007-04-01
was that the solution? i need to know so I can update the guide accordingly.

ubunturules

---

### Post by totalnub on 2007-04-04
thanks a ton for this guide, it has helped me immensely!

---

### Post by CBR900RRMan on 2007-04-05
Ive been trying this for some time and keep getting:

jordan@jordan-laptop:~/Desktop$ sudo ndiswrapper -m
modprobe config already contains alias directive

---

### Post by Laiden on 2007-04-05
I have gone through everything with success after doing your fixes for problems 1 & 2, now in, Network Settings, I have no Wireless Card!!!

I do have,
```
william@william-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 
```

I am using Edgy.

---

### Post by ubunturules on 2007-04-07
CBR900RRMan: what's in the following file?
```
sudo gedit /etc/modeprobe.d/ndiswrapper
```

Laiden: did you restart your computer?

ubunturules

---

### Post by ARich on 2007-04-09
I don't think my hardware is being detected at all.  When I run this command, here is the output.

~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed

It should say "Hardware installed", according to the guide.  I am using a PCMCIA card, that I know to be working since it works on windows.  Another helpful fact is there are two leds, one for power and one for link activity.  Neither one of these is lighting up.


Laptop Model: Pavilion Ze5300
Wireless Card: Belkin Wireless G Plus Card, Part# F5D7011

---

### Post by ubunturules on 2007-04-09
ARich: make sure you have a broadcom 4306 chipset run this command and post the output.
```
lspci | grep Broadcom\ Corporation
```
if you dont have the broadcom 4306 chipset you will need to get the right drivers for your card.

ubunturules

---

### Post by donniebnyc on 2007-04-09
> **ubunturules said:**
> donniebnyc: go to System -> Adminstration -> Keyring Manager

I changed the password on the key tab and when I reopen the keyring manager it's there, but it doesn't stick.  When I restart, it reverts to the previous password.

---

### Post by nae5 on 2007-04-09
> if you dont have the broadcom 4306 chipset you will need to get the right drivers for your card.

ubunturules
i have the BCM4309 802.11a/b/g (rev 02) .

i have tried using the driver that came with the dell inspiron 600m install cd.

winxp is  on another partition on this hd so i went to hda1 Dell/drivers/R58361/ in here are two folders Bin and TMSetup one setup.exe one setup.ini and Version.txt files 

the bin folder has only two files in it demo32.exe and setup.dbd so the drivers are in the TMSetup i found them. 

the guides say to use bcmwl5.inf through ndiswrapper  i tried that and it recognized the hardware under system admin windows wireless drivers, at least it said bcmwl5 hardware present : yes in the left box

but configuring the network doesn't work . after activating and putting in the essid w/ dhcp hexadecimal not ASCII it wont connect and then becomes unactivated...

do i need different drivers? these came w/ the cd and work on the winxp partition i must not be installing something correctly no? this was a clean install after opening repositories and reloading synaptic and then automatix2 where i installed ndiswrapper from..

 any body dealt with 4309 on dell 600m?   or any ideas?

---

### Post by eagleeyes on 2007-04-10
ok here is a question. I followed the instructions to a T and yet even on reboot i cant find any wireless network settings on my network interfaces. iwconfig doesnt show any wireless equipment. here are some of the things i did, i made sure it was the right version 1.18 ndiswrapper. my ndiswrapper -l is showing device present and software loaded. the bcmwl5 files are under ndiswrapper directory. although in my lshw it is showing my network controller as "UNCLAIMED". I have tried changing the alias to iwan0 and eth1 but neither seem to change anything. and I did make sure to blacklist the 43xx driver. any helpful hints on what i am missing? I also cant see anything with wifi radar or wireshark. I appreciate anything you guys got... oh and its the Broadcom 4306 card on an HP ze4900.

---

### Post by chuckn on 2007-04-10
Thanks for all the great help on getting the wireless working.

I am having a problem after following the instructions here. After connecting the first time, I can't connect after reboot.

Any suggestions?

Thanks,
Chuck

---

### Post by ubunturules on 2007-04-11
chuckn: let me see what's in your interfaces file

```
sudo gedit /etc/network/interfaces
```

ubunturules

---

### Post by chuckn on 2007-04-11
ubunturules, thanks for responding.

here is the output of /etc/networks

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Thanks again,
Chuck

---

### Post by Laiden on 2007-04-13
> **ubunturules said:**
> 
Laiden: did you restart your computer?

ubunturules

Yes, I have restarted.

/etc/modprobe.d/ndiswrapper
```
 alias eth1 ndiswrapper 
```

interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid bcit

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

```
:(

---

### Post by ubunturules on 2007-04-13
Laiden: change your /etc/modprobe.d/ndiswrapper to look like this:
alias wlan0 ndiswrapper

change your interfaces to look like this:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wireless-essid bcit

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by donniebnyc on 2007-04-13
> **donniebnyc said:**
> I have another question.  I accidentally entered my WPA key, which is very long, in as the default keyring password.  I'd like to change the keyring password to something more manageable.  I can't find where to do this.  Is there a file I have to edit?

Don

> **ubunturules said:**
> donniebnyc: go to System -> Adminstration -> Keyring Manager

> **donniebnyc said:**
> I changed the password on the key tab and when I reopen the keyring manager it's there, but it doesn't stick.  When I restart, it reverts to the previous password.

I found the answer here: [http://ubuntuforums.org/showthread.php?t=130192](http://ubuntuforums.org/showthread.php?t=130192)

I had to delete home/username/.gnome2/keyrings/default.keyring.  After reboot I was prompted for new default keyring password and then for WPA key.  

WARNING: It says in the above thread that you will LOSE ALL SAVED PASSWORDS when you do this.  I only had one and I knew what it was, so I was safe.  Be careful -- you've been warned.

Don

---

### Post by Laiden on 2007-04-14
> **ubunturules said:**
> Laiden: change your /etc/modprobe.d/ndiswrapper to look like this:
alias wlan0 ndiswrapper

change your interfaces to look like this:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wireless-essid bcit

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

I did that and restarted, my wireless card is still missing from Network Settings.

---

### Post by papawstone on 2007-04-14
This is frustrating!!
I followed all of the directions, everything went in fine,except I had to load the latest version of ndiswrapper and use drivers from Compaq's website otherwise, the HW was not seen.  If I click on the NM icon, the hotel's network is visable but when I click on it, it sits and spins and eventually times out. I tried to connect manually with iwconfig and dhclient reports that no DHCPoffers received. My interfaces list has all the right stuff in it and all the not needed stuff commented out just like in the previous post. Also, I reloaded so that this procedure was the very first thing I did.
Anyone have any suggestions? :confused:

---

### Post by ctimko on 2007-04-14
Need some help my friends.  My problem is simple.  After 5 days and 10 reinstallations of Ubuntu Dapper Drake, I still have one last problem.  First, this tutorial helped, to an extent.  The first major problem that I am having is this: it won't find my SSID.  My ESSID is simply: timko and I have WEP encryption.  The real problem lies in the fact that I can't get the gnome-network-manager (which I am not sure if I want to after reading some posts).  Secondly, the lights are not activating on my card.  Everything else is showing.  This is more than I got before, so thank you.  The driver that was linked works, and my manufacturer one does not.  I would like to get it working soon.  Finally nm-applet does not work for me.  I am not sure why though.  I have the lo icon, etc, but this just isn't working for me.  Any help is greatly appreciated.  Thanks in advanced.

Charles Timko

---

### Post by JoshLukas on 2007-04-14
Hello. Have some problems too. The tutorial gave me some hope, someday I finally will be able to use my wlan connection. However. On Feisty 64 bit it doesn't work and on my fresh installation of Feisty 32 bit everything seems to work, except I can't connect to my own wlan which is WPA AES secured. Mac adress filtering is off. Here is some info about my equipment and configuration. Would be nice if anyone can give me a hint what I am doing wrong.

Router: Linksys WRT54G (The old one with linux)

Router firmware: DD-WRT v23 SP2 (09/15/06) voip

WLAN-Modus: AP

WLAN-Network-Modus: only G

WLAN-Network-Name (SSID): NEXUS 

WLAN-#: 6 - 2.437 GHz 

WLAN-SSID-Broadcast: yes

ACK timing: 2000

WPA PSK: on

AES: on

Share key: *****************

Key Renewal Interval: 3600 sec

MAC filter: off

further details see attached file.



My Linksys WMP54G card is based on Broadcom 4306 chipset:

/etc/modprobe.d/ndiswrapper

```
alias wlan0 ndiswrapper
```/etc/network/interfaces

```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
# wireless-essid NEXUS


iface eth1 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
# wireless-essid NEXUS




auto eth0

auto eth1
```bcm43xx is blacklisted


installed ndiswrapper-utils-1.9 via apt-get



Greetings,

Josh
                              Capture(wl_adv.label6)

---

### Post by ctimko on 2007-04-15
I read about this other technique that installs the firmware, should i try that with the NDISWRAPPER?

---

### Post by papawstone on 2007-04-15
I just had a VERY lucky breakfast......
I was sitting in the breakfast room at the hotel eating when a guy came in complaining he couldn't get his Mac on the hotel internet. The desk clerk said their WiFi didn't like non-windows machines. Now, knowing a little bit about networking, this makes no sense to me why DHCP wouldn't work based on what OS you're running, but I'm willing to consider anything at this point. So, I went back to my room and pulled out a small wireless router I carry with me, plugged it into my Windows machine's LAN port, set up ICP on the Windows machine, ran through the How To for the umpteenth time and tried to hit my router with my Ubuntu laptop. Boom, I'm on the internet! 
So, after completely re-loading this thing 6 times yesterday, reading literally hundreds of posts trying to figure out why I can't connect, I am finally working! 
Thanks to the OP, in the end following his directions worked flawlessly!
:D :D

---

### Post by HotFoot on 2007-04-16
Well, today I got futher than ever before with my wireless card.  I'm running Fiesty on a Media Centre PC in my living room.  It's rather annoying to have an ethernet cable running from the office to there, so seeing that there has been a few advances in networking with Feisty, I thought I'd give this guide another try.

I'd say things are about 90% there for me.  The good news is that I'm able to connect to a wirless network.  I'm entering my WEP key, and I get connected to the network.  I even see the signal strength through the little network manager applet.  This is as far as I ever got with Edgy.

The problem I'm having is that very shortly after I'm connected, I get a message requiring me to enter in the WEP key again, and I can no longer get internet over the wireless.  Is this a common problem?  What might I have done wrong to end up this way?  I would really like to get my wireless working.

---

### Post by MikeB5862 on 2007-04-20
I am happy to say.. this forum RULES!.. I followed every instruction to the T, and, as a matter of fact i'm writing this reply using my Broadcom 4306 802.11g Network adapter ( of course its on a weak connection.. I'm at work (ha ha) ) .  Just wanted to let you guys know that you really know your SH... um er stuff.. :)   Thanks for your help!:)

---

### Post by donniebnyc on 2007-04-20
I was working fine under Edgy, so I got ambitious and installed Feisty.  The install went smoothly but now the wireless is dead.  I didn't save the first time, so I retyped the commands to show you the output:

[INDENT]donniebnyc@donniebnyc-t40:~$ lspci | grep Broadcom\ Corporation
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
donniebnyc@donniebnyc-t40:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
donniebnyc@donniebnyc-t40:~$ sudo gedit /etc/modprobe.d/blacklist  {I did this edit the first time.}
donniebnyc@donniebnyc-t40:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
donniebnyc@donniebnyc-t40:~$ cd /home/donniebnyc/
donniebnyc@donniebnyc-t40:~$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
donniebnyc@donniebnyc-t40:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
donniebnyc@donniebnyc-t40:~$ sudo ndiswrapper -m
module configuration already contains alias directive

donniebnyc@donniebnyc-t40:~$ sudo modprobe ndiswrapper
donniebnyc@donniebnyc-t40:~$ 
[/INDENT]

I also tried the Problem 1 solution:

sudo gedit /etc/modeprobe.d/ndiswrapper -- This file was blank.

sudo gedit /etc/network/interfaces -- I commented out the auto eth1 section.

[INDENT]auto lo
iface lo inet loopback

iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wireless-essid linksys_SES_33917
#wireless-key 

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys_SES_33917
wireless-key 

auto eth0[/INDENT]

sudo gedit /etc/iftab -- I changed eth1 to wlan0.

[INDENT]# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0d:60:af:0a:27 arp 1
wlan0 mac 00:12:17:e4:98:14 arp 1[/INDENT]

The wireless connection is not in the Network Settings, but the nm-applet shows in the taskbar for wlan0.  When I click on the nm-applet I get this error message:

"Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device"

I figured I should stop before I really screw things up.  Any ideas on how to get this working again?  Thanks.

---

### Post by donniebnyc on 2007-04-20
I decided to install Feisty from scratch.  Followed the directions and here I am online.  Thanks again for all the help.

---

### Post by elcu on 2007-04-21
> **ubunturules said:**
> 

**Enable the Connection**

**10.** Go to System -> Administration -> Networking

**11.** If you don't see any wlan0 connections in Networking then you should restart your computer.



Running Feisty here.  I've restarted several times but I don't see a wlan0 connection.  What should I do?

---

### Post by ctimko on 2007-04-21
Ok, so I am gonna do something silly and maybe a little stupid....okay maybe its really smart.  I am gonna start from scratch with Feisty Fawn.  I am gonna see if the new ndiswrapper-utils-1.9 works over the 1.8 version.

Charles

---

### Post by ubunturules on 2007-04-23
ctimko: thanks for doing that for me.  please report back just to make sure you do need ndiswapper-utils-1.9 if you're on feisty.

ubunturules

---

### Post by dlm4849 on 2007-04-23
ubunturules:

First off, thank you so much for the great guide. I would be up the creek without it. I have gotten to the point to where I know I am just *this* close to being finished, and was hoping you could lend a hand. Please keep in mind I am a new Linux user, having just switched over last night. I have got the wireless interface to come up in networking and it will detect networks. When it asks for my WPA passcode, I enter it in and it "connects," but I cannot access the internet. It shows the network and the signal strength, but I dont have an IP address. I read through the first 15 or so pages and didnt see the same issue anywhere.

Any help would be appreciated from anyone.


EDIT:

Figured out that it was a network setup issue. Everything is up and running beautifully. Thank you so much for this awesome how to guide.

---

### Post by ubunturules on 2007-04-24
dlm4849: awesome glad to hear that you got it working!

---

### Post by KingdomKid on 2007-04-25
OK...so I am the new guy on the block...had to get away from windows! 
I got a little learning curve going on here...but all is well. I did have the issue with my wireless card and fixed the issue...not knowing this would lead to, yep...I used the firmware cutter route.

Is there a way I can undo what I have done and do this method instead?
Be gentle...and as detailed as possible, I am so new at this, it aint even funny :lolflag: 

By the way...This was an incredible HOWTO post.....I hope I can still do it.

Thanks guys

---

### Post by woaizhongguo06 on 2007-04-25
I have tried unsuccessfully to install ndiswrapper and get my broadcom 4306 card working. I tried this time using your post but when I typed

sudo rmmod bcm43xx

i received the error message

ERROR: Module bcm43xx does not exist in /proc/modules

any help would be greatly appreciated

---

### Post by ubunturules on 2007-04-25
woaizhongguo06: That error message is a good error message.  It means that you have already removed it.
You can proceed with the next steps.

---

### Post by woaizhongguo06 on 2007-04-26
performed step 7. Received the error message

john@john-laptop:~$ ndiswrapper -l
bcmlw5 : invalid driver!
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
bcmwl5 : driver installed
        device (14E4:4320:103C:12F4) present (alternate driver: bcm43xx)
        device (14E4:4320) present (alternate driver: bcm43xx)

---

### Post by swoop_ubu on 2007-04-27
this is an awesome how-to. excellent job!
only one thing is missing and i think should be part of you
how-to (or the driver archive should be updated):

on 64 bit system change the name of .inf file to the
name of .sys file. from that momnet on it worked like
a charm for me.

cheers
swoop

---

### Post by woaizhongguo06 on 2007-04-27
performed step 7. Received the error message

john@john-laptop:~$ ndiswrapper -l
bcmlw5 : invalid driver!
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
bcmwl5 : driver installed
device (14E4:4320:103C:12F4) present (alternate driver: bcm43xx)
device (14E4:4320) present (alternate driver: bcm43xx)

---

### Post by Zaireeka on 2007-04-28
I just tried this on a fresh Fiesty install. Unfortunately, I'm getting the same problem seen earlier in the thread where my wireless connection dissapears from Network Settings.

As ndiswrapper didn't appear to come on the Fiesty disc I used synaptic to install it from the 6.06 disc. (I have ootb wired connection support but no access to a wired connection. Hence why I skipped the apt-get for ndiswrapper) The driver I used with ndiswrapper came on the cd with the card and works perfectly on my windows partition.

I've restarted, blacklisting worked and ndiswrapper -l displays: 

```
Installed ndis drivers:
bcmwl5           driver present, hardware present
```

Network manager currently shows only the wired connection option.

I'm kinda stuck for ideas on what to try next. Any help greatly appreciated.

---

### Post by woaizhongguo06 on 2007-04-29
Please help, I have no idea where to go from here. I am very new to Linux.

performed step 7 on the tutorial and received the error message:

john@john-laptop:~$ ndiswrapper -l
bcmlw5 : invalid driver!
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
bcmwl5 : driver installed
device (14E4:4320:103C:12F4) present (alternate driver: bcm43xx)
device (14E4:4320) present (alternate driver: bcm43xx)

---

### Post by ubunturules on 2007-04-29
woaizhongguo06: run this command 
```
sudo ndiswrapper -e bcmwl5
```
```
sudo ndiswrapper -i bcmwl5.inf
```

and then post the output of the following command
```
ndiswrapper -l
```

you might need to use a different driver

run the following command to make sure you have a broadcom 4306 card
```
lspci | grep Broadcom\ Corporation
```

If you don't have a broadcom 4306 card you will need to get the appropriate driver for that card

hope this helps

---

### Post by acm79 on 2007-04-29
@ ubunturules, thank you so much , i instaled ubuntu from the scratch and it works!!

---

### Post by woaizhongguo06 on 2007-04-29
ran those two commands here is the terminal

john@john-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper line 172.
john@john-laptop:~$ ndiswrapper -l
bcmlw5 : invalid driver!
bcmwl5 : invalid driver!


i ran the code and i do have a broadcom 4306 card

---

### Post by ubunturules on 2007-04-29
woaizhongguo06: i got a couple questions?
1. is this from a fresh install
2. did you run ```
sudo ndiswrapper -e bcmwl5
``` before running ```
sudo ndiswrapper -i bcmwl5.inf
```

---

### Post by woaizhongguo06 on 2007-04-29
What do you mean by fresh install?
I installed ubuntu edgy eft onto this computer after formatting the hard drive about a month ago. I copy and pasted the two commands that you asked about and here is the terminal

john@john-laptop:~$ sudo ndiswrapper -e bcmwl5
john@john-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper line 172.

---

### Post by ubunturules on 2007-04-29
woaizhongguo06: fresh install means you did a reinstall of edgy before you tried this howto.  for some reason you don't have a /usr/sbin/ndiswrapper file.  do a search for ndiswrapper and find out where that file so we can link it to /usr/sbin/ndiswrapper or copy it or whatever we have to do.

---

### Post by woaizhongguo06 on 2007-04-29
there are tons of files that contain ndiswrapper. 
here are the results of my search

/etc/ndiswrapper
/etc/modprobe.d/ndiswrapper
/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.17-10-generic/misc/ndiswrapper.ko
/usr/sbin/ndiswrapper-buginfo
/usr/sbin/ndiswrapper
/usr/share/doc/ndiswrapper-common
/usr/share/man/man8/ndiswrapper.8
/usr/share/man/man8/ndiswrapper.8.gz
/var/lib/dpkg/info/ndiswrapper-common.md5sums
/var/lib/dpkg/info/ndiswrapper-common.list

---

### Post by UI-Freak on 2007-04-30
This works on my laptop - thanks. BUT if I disable the wireless NIC using the switch on the laptop and later enables it using the switch, then this driver is not able to turn it "on". I have to boot Windows XP that will enable it (I can see the "wireless is on" an LED is turned on during boot of XP).

How can I enable it from Linux? It is a Acer Travelmate 290e.

---

### Post by zeddock on 2007-05-01
This is what I get:
jim@lat-lap:~$ ndiswrapper -l
bcmwl5 : driver installed

I screwed my wireless device settings I suppose. Anyway to have the system rescan so that it is seen?

Here is the output of lspci:
jim@lat-lap:~$ lspci | grep Broadcom\ Corporation
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
jim@lat-lap:~$

---

### Post by woaizhongguo06 on 2007-05-01
ubunturules:

there are tons of files that contain ndiswrapper.
here are the results of my search

/etc/ndiswrapper
/etc/modprobe.d/ndiswrapper
/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.17-10-generic/misc/ndiswrapper.ko
/usr/sbin/ndiswrapper-buginfo
/usr/sbin/ndiswrapper
/usr/share/doc/ndiswrapper-common
/usr/share/man/man8/ndiswrapper.8
/usr/share/man/man8/ndiswrapper.8.gz
/var/lib/dpkg/info/ndiswrapper-common.md5sums
/var/lib/dpkg/info/ndiswrapper-common.list

---

### Post by swoop_ubu on 2007-05-02
ubunturules:
it was nice of you to update the x64 archive with the identical filenames.

two days ago i bumped into another problem.
because the i386 software base is much broader compared to the x64
i reinstalled my laptop to ubuntu i386. i followed this how-to one  more
time and I didnt manage to make my wireless to work.

i retried several times and then i went for drivers hunting. i have gateway
7426GX laptop so i downloaded drivers from their site. the result was the same
then i tried couple of the fwcutter how-tos, but it didnt work either.
however, i learned one thing. it might lead to a dead end if you use version 4
drivers. so i turned my attention to version 3. i noticed there was an alternate
install information file. id did a bit of a renaming magic and it WORKED!!

so if you still cannot make your bcm43xx work download this file
[http://rapidshare.com/files/28972349/bmc43xx.zip.html](http://rapidshare.com/files/28972349/bmc43xx.zip.html)
and give a try to the bcmwl5a.inf (notice the "a" at the end) file.

ubunturules:
maybe you can include the alternate files in the i386 archive.

cheers
swoop

---

### Post by zeddock on 2007-05-02
> **zeddock said:**
> This is what I get:
jim@lat-lap:~$ 
bcmwl5 : driver installed

I screwed my wireless device settings I suppose. Anyway to have the system rescan so that it is seen?

Here is the output of lspci:
jim@lat-lap:~$ lspci | grep Broadcom\ Corporation
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
jim@lat-lap:~$


Why does lspci | grep Broadcom\ Corporation show my wireless card...
but this...  
ndiswrapper -l  does not say it is installed?

Please help?  Looks like I really screwed this one up. Can I get back to stable? ...or must I reinstall the OS?

Thanx.

zeddock

---

### Post by kgr132 on 2007-05-02
Awesome HOWTO. I followed the first post to the letter on a fresh install of Fiesty (due to a really bad experience updating Dapper) on my Dell Latitude D600. I used the drivers downloaded from the post. After changing eth1 to wlan0, as mentioned, I was online including WPA in under 30 minutes. Thanks a bunch.

One question remains: Will nidswrapper keep looking for the bcmwl5.inf and bcmwl5.sys files to be where they were at the time when I installed the driver in ndiswrapper? If so, how do I tell ndiswrapper that I moved the files? I had the files in my home folder (not thinking!) and I'd like to move them, but not at the expense of crashing ndiswrapper. Sorry if this was asked/answered before. I tried to read all the other posts, but with 55 pages of replies, I may have missed something.

Keith

---

### Post by zeddock on 2007-05-02
> **zeddock said:**
> Why does lspci | grep Broadcom\ Corporation show my wireless card...
but this...  
ndiswrapper -l  does not say it is installed?

Please help?  Looks like I really screwed this one up. Can I get back to stable? ...or must I reinstall the OS?

Thanx.

zeddock

Please help me find my wlan0.
...or my eth1 if it would work!

zeddock

---

### Post by ubunturules on 2007-05-02
kgr132: you can move them where every you want to.  it won't mess up anything.

zeddock: what does ndiswapper -l say?

---

### Post by KingdomKid on 2007-05-03
Ubunturules...You Rock my brother! Thanks for the HOWTO!
Being brand new to the (K)Ubuntu side of things...this was an incredible help! Thank you. And thanks to everyone for the input!

Now off to the NFTS Configuration.....I dont mean to hi-jack the thread, but could you perhaps lead me in the right direction, or any suggestions???

Thanks Guys!

---

### Post by vxd on 2007-05-03
Ok, so i'm having some troubles with this howto. My wireless interface doesn't seem to poweron...

lspci says

```
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

ndiswrapper -l says

```
bcmwl5          driver installed, hardware present
```

/etc/network/interfaces says

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

/etc/modprobe.d/ndiswrapper says
```
alias wlan0 ndiswrapper
```

I've tried diffrent firmwares, from makers webpage etc. but it does no diffrence... The device won't power up!

Appreciate all help I can get.

---

### Post by zeddock on 2007-05-03
> **ubunturules said:**
> kgr132: you can move them where every you want to.  it won't mess up anything.

zeddock: what does ndiswapper -l say?

I ended up using the guide[ here.]("http://ubuntuforums.org/showthread.php?t=340689")

But I would like to know what brought the wlan0 back into my listing of interfaces, etc.
Here is ndiswrapper -l now:
bcmwl5 : driver installed
        device (14E4:4324) present (alternate driver: bcm43xx)
jim@lat-lap:~$

Yesterday it did not show the device present!
zeddock

---

### Post by vxd on 2007-05-03
hmm, followed the same guide as the poster before me and all is good now.

ndiswrapper -l shows the same as the previous speaker... And I would also like to know why the interface didn't show up before :/

---

### Post by darthchaosofrspw on 2007-05-06
> **ubunturules said:**
> did this HOWTO help anyone?

Yeah, but there's another how-to that to me seems to work better, and it's confirmed by me to work with Dapper, Edgy, and Feisty:

1. Make a directory called "WLAN" in your home directory, and download the drivers. You will need both bcmwl5.inf and bcmwl5a.inf for the wifi to properly work.
2. Install ndiswrapper.
2. sudo rmmod bcm43xx
3. sudo gedit /etc/modprobe.d/blacklist   (add - minus the quotes - "blacklist bcm43xx" to end of file, then save)
4. cd WLAN
5. sudo ndiswrapper -i bcmwl5.inf
6. sudo ndiswrapper -i bcmwl5a.inf
7. ndiswrapper -l (The words "DRIVER PRESENT, HARDWARE PRESENT" should appear beside both bcmwl5 and bcmwl5a.
8. sudo modprobe ndiswrapper
9. sudo ndiswrapper -m

Then set up your connection manager.

---

### Post by woaizhongguo06 on 2007-05-07
Ubunturules

I really need help getting my wireless working. You told me to scan my hardrive for ndiswrapper and here are the results of my search

there are tons of files that contain ndiswrapper.
here are the results of my search

/etc/ndiswrapper
/etc/modprobe.d/ndiswrapper
/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.17-10-generic/misc/ndiswrapper.ko
/usr/sbin/ndiswrapper-buginfo
/usr/sbin/ndiswrapper
/usr/share/doc/ndiswrapper-common
/usr/share/man/man8/ndiswrapper.8
/usr/share/man/man8/ndiswrapper.8.gz
/var/lib/dpkg/info/ndiswrapper-common.md5sums
/var/lib/dpkg/info/ndiswrapper-common.list

---

### Post by ubunturules on 2007-05-07
darthchaosofrspw: that's pretty much exactly like my howto. my howto is even more detailed tha nthat.   you can't install 2 drivers so that whole installing 2 drivers thing doesn't make since.
woaizhongguo06:  can you post the error message again.

---

### Post by woaizhongguo06 on 2007-05-07
performed step 7. Received the error message

john@john-laptop:~$ ndiswrapper -l
bcmlw5 : invalid driver!
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
bcmwl5 : driver installed
device (14E4:4320:103C:12F4) present (alternate driver: bcm43xx)
device (14E4:4320) present (alternate driver: bcm43xx)

---

### Post by msinca on 2007-05-08
Hello all.  I'm another Linux/Ubuntu newbie.  I'm trying to get my wireless up and running on my Gateway 200 laptop.  I used the ndiswrapper method that I found here: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

Seemed to work because I can now see my Router when I click on Network manager in the upper right corner.  However, every time I try to connect to it, it fails.  I'm using WPA2.  If I mouseover it, it says "Waiting for Network Key for the wireless network xxxxxxxx" and then simply fails.  (obviously, i did fill in the correct network key - I checked it on another Windows laptop)

I see that some others are having similar problems: [http://ubuntuforums.org/showthread.php?t=414783](http://ubuntuforums.org/showthread.php?t=414783)

but the solution posted at the end didn't work for me (because I did install using the ndiswrapper method).  

Any suggestions of help?  Please include the code because I'm totally new to Linux and don't know my sudo from my tar ;-)

Thanks a million!
Mike

---

### Post by ubunturules on 2007-05-10
Does anybody know how I can change the title of the thread so that I can put HOWTO in front of it?

ubunturules

---

### Post by aimtrainer on 2007-05-10
hi!
I'm on a clean feisty install (my third in two hours of trying to get my wireless working)

I followed the guide step by step and couldn't find any errors or anything until I open system/admin/network and do not find a my wireless there. I ve of course tried rebootooting and some editing, Totoros fix.. but nothing helped.
in /etc/network/interfaces there is no sign of the wireless card..
tomorrow I'll follow the guide again on a fresh install again and paste every in- and output and all relevant config files.

please help me I'm close to selling that damn laptop (bought a used thinkpad x31 and thought there shouldnt be any driver related problems, but the shop I bought it from replaced the original wlan card)

thanks in advance!

---

### Post by aimtrainer on 2007-05-10
so.. I couldn't wait till tomorrow here's my console:

aimtrainer@aimtrainer:~$ lspci | grep Broadcom\ Corporation
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
aimtrainer@aimtrainer:~$ sudo rmmod bcm43xx
Password:
aimtrainer@aimtrainer:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
aimtrainer@aimtrainer:~$ sudo apt-get install ndiswrapper-utils-1.9
...
...

aimtrainer@aimtrainer:~$ sudo ndiswrapper -i /home/aimtrainer/Desktop/bcmwl5.zip_FILES/bcmwl5.inf 
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
aimtrainer@aimtrainer:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
aimtrainer@aimtrainer:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
aimtrainer@aimtrainer:~$ sudo modprobe ndiswrapper
aimtrainer@aimtrainer:~$ 

_______________________________________________________________

As far as I can see everything seems to go right but now in my networksettings there is no wlan0 or eth1 or anything. before with the linux driver it was there and under winxp it even worked, so it's not broken or something.
Btw I'm on a completely fresh feisty install on a thinkpad x31 with Broadcom wireless instead of the usual intel. But its internal). All i did before this was update availible packages as suggested by synaptic.

Here are some config files:

/ec/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2

/etc/modeprobe.d/ndiswrapper:

alias wlan0 ndiswrapper

/etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
	address 192.168.178.22
	netmask 255.255.255.0
	network 192.168.178.0
	broadcast 192.168.178.255
	gateway 192.168.178.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.178.1

/etc/iftab:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:03:c9:7c:fc:94 arp 1
eth1 mac 00:09:6b:fa:92:74 arp 1


Thanks for the guide and for the help I hope to get :)

---

### Post by ubunturules on 2007-05-10
aimtrainer: look at solution 1 at the bottom of the guide.  changeeth1 to wlan0 in all of those files.  make a back up of your /etc/interfaces file and take out all of the stuff you have under primary network interface and change it to 

auto wlan0
iface wlan0 inet dhcp

you should be able to set up the static stuff once you get it to be recognized by network manager.

ubunturules

---

### Post by aimtrainer on 2007-05-10
ok did that, but it still doesnt work. system>settings>network still only shows the normal network interface :(

aimtrainer@aimtrainer:~$ ndiswrapper -l
bcmwl5 : driver installed
device (14E4:4320) present (alternate driver: bcm43xx)

Is that how it's suppose to?
shouldn't it say "DRIVER PRESENT, HARDWARE PRESENT" ?

Everytime the same ... with notebooks 8[

---

### Post by trivix on 2007-05-10
> **aimtrainer said:**
> ok did that, but it still doesnt work. system>settings>network still only shows the normal network interface :(

aimtrainer@aimtrainer:~$ ndiswrapper -l
bcmwl5 : driver installed
device (14E4:4320) present (alternate driver: bcm43xx)

Is that how it's suppose to?
shouldn't it say "DRIVER PRESENT, HARDWARE PRESENT" ?

Everytime the same ... with notebooks 8[

Maybe alter modprobe instead of modeprobe?

---

### Post by donniebnyc on 2007-05-11
Everything was working fine, except that wireless sometimes would not reconnect after waking up from standby.  It was a minor annoyance since a reboot is very fast and fixed it .  

Yesterday it would not reconnect (even after I reset the router, my wife's windoze pc is working) so I tried connecting to a neighbor's unsecured network.  It worked, but now I can't connect to my network.  I went into network settings and unchecked roaming and selected my network from the drop down and put in the password.  I get the Configuration Interface Changing box but when it's done still no go.

I rebooted but now the keyring manager does not come up.  Wired networking is working.

I rechecked network settings and it looks good.  The nm-applet doesn't show wireless networks, only manual config.  

What do I do now?  I could re-install Feisty, it's certainly easy enough, but I want to learn to fix a problem when one arises.

---

### Post by aimtrainer on 2007-05-11
> **trivix said:**
> Maybe alter modprobe instead of modeprobe?

that was just a typo in my post

---

### Post by Zebedee18F on 2007-05-11
I am having the same problems as aimtrainer:


```
zeb@Laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
```

I have been using ndiswrapper since i started using dapper and had to do it a few times in the early days were i reinstalled alot because i couldn't help fidlding with things.

I have not come across this error yet. I checked the blacklisting and tried reinstalling ndiswrapper / drivers Anyone got any clues?

I was expecting >  "DRIVER PRESENT, HARDWARE PRESENT" ?

The wireless will connect, though it only just manages and I cannot access the net. trying to access google or use amsn and it just hangs. 

However it can access the routers admin page. 

I am using feisty after updating (full reinstall) last night. 

Thanks for any help anyone can suggest.

---

### Post by ubunturules on 2007-05-13
Zebedee18F: 
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

that is the response that ndiswrapper-utils-1.9 gives.  It is not an error.  That is what it is supposed to say.  I will fix that in my howto when I get the time.

---

### Post by Sweet Mercury on 2007-05-14
I followed this tutorial and thngs seemed to go off without a hitch, but now it seems that Ubuntu doesn't even see my wireless card; it *did* list a wireless option before the ndiswrapper install, it just didn't see or connect to my wireless network.

The lspci command still lists the wireless card, so some part of the system can see it.

I realize now there was one unkosher event in the install, the *ndiswrapper -l* command gave me no information, and it still doesn't.  Like this:

> mason@mason-laptop:~$ ndiswrapper -l
mason@mason-laptop:~$ 

Is there any way to undo what I did here, if necessary?

I'm using Feisty 7.04, and yes, I did restart the computer, as the tutorial suggested. Any help would be appreciated. I'm new to Linux, and this refusal of the OS to work with WiFi is starting to get old.

---

### Post by Bohlio on 2007-05-15
ignore this please.

---

### Post by Bohlio on 2007-05-15
sorry, Ignore that last message.

Im stuck where i try to install the driver. This is my first day on Ubuntu and i really dont know how the whole system works. any help would be appreciated.
> chad@chad-desktop:~$ sudo ndiswrapper -i /home/chad/desktop/bcmwl5.inf
installing bcmwl5 ...
couldn't open /home/chad/desktop/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.


---

### Post by zeddock on 2007-05-16
My wireless interface has disappeared also. I find I can get it back by following this guide.
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)
Keep in mind that with every kernel update, this guide must re-run.

zeddock.
PS. I think I am going to use it to get wireless interface back and then do the other Howto.

---

### Post by grayfood on 2007-05-16
thankyou this helped me solve my problem

---

### Post by Bohlio on 2007-05-16
I really need help with getting on the internet guys... Ive installed Ndiswrapper and I cant get the driver to install, all i get is... 
> chad@chad-desktop:~$ sudo ndiswrapper -i /home/chad/desktop/bcmwl5.inf
installing bcmwl5 ...
couldn't open /home/chad/desktop/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.

Im just beginning with Ubuntu and i don't really know much about how it works, Any help would be great. :)

---

### Post by bung33 on 2007-05-17
Bohlio:

Try navigating to the directory first before you attempt to install the driver...

cd /home/chad/desktop/

Then use ndiswrapper to install the driver...

sudo ndiswrapper -i bcmwl5.inf

Hope this works for you!

---

### Post by bung33 on 2007-05-17
Check out the thread below...

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

This unique approach instructs you on how to install the firmware for the wireless card. I was able to get my card working without even using ndiswrapper...

---

### Post by Prefader on 2007-05-17
Bohlio -
You need to capitalize "Desktop" - try 
```
sudo ndiswrapper -i /home/chad/Desktop/bcmwl5.inf
```
Hope that helps.

---

### Post by spesheled1 on 2007-05-17
Thanks for the info on setting up ndiswrapper.  I was finally able to get the wireless working on my laptop which I had installed both Dapper and Windows.

---

### Post by Bohlio on 2007-05-17
I just got it worked out guys, thanks.

I had messed it up earlier and had a "bcmwl5" folder in my ndiswrapper directory. I just had to remove that and try again. Im posting using Ubuntu right now :-)
Thanks for your help, Im starting to get accustomed with Ubuntu and its great so far :-)

---

### Post by Sweet Mercury on 2007-05-19
> **bung33 said:**
> Check out the thread below...

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

This unique approach instructs you on how to install the firmware for the wireless card. I was able to get my card working without even using ndiswrapper...

I saw that thread a while ago. My biggest concern with the firmware flash was that my wireless would cease to work with Windows. I am keeping windows as a secondary OS because I might need it for work/school--I have a few programs that I don't think will work with Linux (terminal emulators, etc).

---

### Post by Sweet Mercury on 2007-05-19
Also, I uninstalled the ndiswrapper using this command:

```
sudo aptitude remove ndiswrapper-common
```

and my computer *still* doesn't recognize the wireless interface, (it showed a wireless interface  before I installed the ndiswrapper).

How can I least get back to where I started before I tried this ndiswrapper thing? Do I have to reinstall the "kernel" or something like that?

---

### Post by thrashnbash on 2007-05-21
Man, this is something I had been struggling with this weekend on my D600.  Trying to get the ndiswrapper module thing installed (which, why isn't this a default with the OS?)  Reading many posts/wikis/forums, etc... all of which gave me a lot of information, but nothing laid it out like this.

I really wish I had the darn laptop in front of me right now to confirm that this would work.  Everything is laid out step by step so anyone can follow it.  I can't wait to get home and try this.  I believe finally I will have the success (thanks to this HOW TO) so I can roam with Linux & learn.

Thanks again for all the great efforts and documentation.  It really does help.

---

### Post by ubunturules on 2007-05-25
I updated the way ndiswrapper is installed. This should fix the problem people were having with their wireless card not showing up under the network settings.

ubunturules

---

### Post by zeddock on 2007-05-25
> **ubunturules said:**
> I updated the way ndiswrapper is installed. This should fix the problem people were having with their wireless card not showing up under the network settings.

ubunturules

Didn't make a difference for me. Still, after reboot, the wireless is gone from the network app.  A iwconfig shows only lo and eth0 with no wireless.

For Others:
I am going back to [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

Then I may try the firmware update listed elsewhere.  I am running a Dell Latitude D|800 4309

zeddock

---

### Post by ipina on 2007-05-26
Your advices helped me. Now, my Broadcom 4306 wireless card works correctly. Thank you very much. Best regards.

---

### Post by talkout on 2007-05-28
This might be useful. It worked for my BCM4310 UART (rev 01) .
It lists drivers for a whole lot of other Broadcom [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom?highlight=%28Broadcom%29](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom?highlight=%28Broadcom%29)

NiMaL
---
[www.talkout.tk](www.talkout.tk)

---

### Post by KingdomKid on 2007-05-28
Ubunturules, I did an update last night...It was to the 2.6.20-16-generic
When I originally setup my wireless with this howto I had, by the howto's directions #7, used 2.6.20-15-generic. All was working great.

This morning when I booted up...now my wireless won't work. Do I have to update and go through the steps again and change 2.6.20-15-generic to the new 2.6.20-16generic to resolve?

Not sure what to do here. Thanks for your help

Wanted to add...I have 2 laptops, running identical OS (Kubuntu 7.04). 
1st unit has broadcom 4306 which I installed using this howto
2nd unit has the 4318 which I used the 4318 driver and this howto to install.
All has been working great. 
I did updates mentioned above on both units last night. This morning, both units will not connect through wireless.
I have to assume it is the update that has changed something somewhere.

Thanks you for any suggestions

---

### Post by ubunturules on 2007-05-28
KingdomKid: you have to redo everything everytime you update the kernel

---

### Post by bthessel on 2007-05-28
I'm stuck, I have used this How-to  before flawlessly to get my wireless working, but today I did a fresh install of Feisty and it is not working. This is what I see in the logs during a reboot

May 28 22:33:19 brian-gateway kernel: [   25.388000] ndiswrapper (miniport_init:277): couldn't initialize device: C0000001
May 28 22:33:19 brian-gateway kernel: [   25.388000] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
May 28 22:33:19 brian-gateway kernel: [   25.388000] ndiswrapper (miniport_halt:352): device d693f400 is not initialized - not halting
May 28 22:33:19 brian-gateway kernel: [   25.388000] ndiswrapper: device eth%%d removed
May 28 22:33:19 brian-gateway kernel: [   25.388000] ndiswrapper: probe of 0000:02:09.0 failed with error -22

any help is appreciated. Thanks.

---

### Post by ajsburns on 2007-06-03
Hi,

Thanks for this - very useful. I tried out feisty with fwcutter but wanted the higher speed link naturally & stumbled across this. 

It took me two attempts to get it working though - the first time it failed to work. (I could see the wireless network & attempt to connect, but it never connected properly, though it sometimes said it was...).  I did a fresh install of feisty/7.04 in case I'd messed something up. (I'd noticed some error messages about permissions part-way through the process but had ignored them as the step seemed to complete OK). 

Second time round, I got the same errors at step #11, but the following change fixed it for me:

> 
make distclean
make
sudo make install


to:

> 
make distclean
**sudo make**
sudo make install


Followed the rest of the steps as detailed & hey presto, I have working wireless again! :D

---

### Post by ubunturules on 2007-06-04
thanks for the help man. ill fix it

ubunturules

---

### Post by mrsempai on 2007-06-05
im having the same problem as Sweet Mercury... i followed the guide and now i cant see my wireless card... is there a way to undo or redo all of this so it can work or at least be back to where it was?

---

### Post by mrsempai on 2007-06-05
ok, solved that problem by myself, now...

how can i rename my wireless card from eth0 to wlan0?? plz help :)

---

### Post by ubunturules on 2007-06-06
read problem 1 on the first post.  that should fix your problem.

ubunturules

---

### Post by giambrone on 2007-06-07
Okay, this is the second time i've used this tutorial, and has been really really helpful, HOWEVER (:o), after my second reboot (I was installing security updates) it now won't connect to my network. The little symbol comes up with the spinning blue thingy (no green lights though), but it keeps doing that until it returns to the "not connected icon". Since there are 60 pages here I am far too lazy to read through them all. Sorry guys!

Matt:KS

---

### Post by ubunturules on 2007-06-07
was one of the updates a kernel update. if it was then you will need to do the tutorial again.

ubunturules

---

### Post by ner0tic on 2007-06-11
i tried this turtorial and bcmxx-fwcutter errors out:

 sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up bcm43xx-fwcutter (006-1) ...
--17:12:06--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o.4'
Resolving boredklink.googlepages.com... 64.233.179.118
Connecting to boredklink.googlepages.com|64.233.179.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/octet-stream]

100%[====================================>] 652,866      339.74K/s             

17:12:10 (338.66 KB/s) - `wl_apsta.o.4' saved [652866/652866]

Sorry, the input file is either wrong or not supported by bcm43xx-fwcutter.
This file has an unknown MD5sum 5752f0a7d0df2e8842075bed8d6552a6.
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bcm43xx-fwcutter (006-1) ...
--17:12:11--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o.5'
Resolving boredklink.googlepages.com... 64.233.179.118
Connecting to boredklink.googlepages.com|64.233.179.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/octet-stream]

100%[====================================>] 652,866      313.15K/s             

17:12:15 (312.23 KB/s) - `wl_apsta.o.5' saved [652866/652866]

Sorry, the input file is either wrong or not supported by bcm43xx-fwcutter.
This file has an unknown MD5sum 5752f0a7d0df2e8842075bed8d6552a6.
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 bcm43xx-fwcutter

---

### Post by ubunturules on 2007-06-11
I don't know anything about bcmxx-fwcutter. I've never used it.  You might want to ask that question on a tutorial using bcmxx-fwcutter.

ubunturules

---

### Post by 00ber n00b on 2007-06-12
I still cannot get my wireless to show up after this how-to.  I realize i must be doing something wrong.  ubuntu rules, do you think you can revamp the how-to.  i believe some of the steps are not specific, as far as being on a newb level of experience.  i mean i followed the tutorial, i copied and pasted most of it.  every time i reboot i dont see my wireless connection.  thanks for any help.  if necessary, i'll go through the tutorial and post every result i get step after step.  thanks

---

### Post by ner0tic on 2007-06-13
i got mine working, but i was bouncing between tutorials so i'm not sure which i followed when, but bsically i ran the fcutter on the bcwl5.sys file and then had to got through and make sure it was looking for wlan0 and not eth1 and i was good to go

---

### Post by 00ber n00b on 2007-06-13
> **ner0tic said:**
> i got mine working, but i was bouncing between tutorials so i'm not sure which i followed when, but bsically i ran the fcutter on the bcwl5.sys file and then had to got through and make sure it was looking for wlan0 and not eth1 and i was good to go

well, its working now, by using bcmxx-fwcutter.  its extremely flaky, the wireless lights flash on and off.  I can see networks and i connect to them and i only get about 40% connection, which is not bad, but i cant surf the web.  Also, these networks are not encrypted.  I wanna try the ndiswrapper way, but i keep messing it up some how.

---

### Post by simply.jonah on 2007-06-17
I didn't realize at first that this was for the 4306.  Anyway, I got this to work flawlessly with my 4318 on Feisty Fawn.  Thank you so much!

---

### Post by Ahslan on 2007-06-22
hey...i absolutely dont know anything about ubuntu and i just installed it on my hp pavilion ze2000 laptop and i cant get the wireless to work. I know its a 4306 but it doesnt see it in the network manager applet. I dont know how to install the drivers and the other program needed to get the wireless working. Is anyone able to help me out?

---

### Post by independent8847 on 2007-06-27
i just bought that wireless card for my laptop running feisty fawn and i had a linksys one that was working fine until i dropped it so i bought this belkin one and now i cant get it working...i cant even connect to my wired network either...any help?

---

### Post by fachex on 2007-06-28
It worked for me! Thanks a lot!!! Jun 2007. Ubuntu 7.04. Toshiba Satellite. Belkin Card.

---

### Post by k4zzy on 2007-06-28
Hello. I just finished a fresh install of Xubuntu 7.04 on a HP Pavilion ZD7000. I hope it's alright that it's xubuntu, not ubuntu. :)

I followed the instructions in this thread, and got wireless working successfully. I was using the Network Manager applet (nm-applet) happily, until the next time I booted the laptop up. For some reason, I got two of the nm-applet icons in my task bar, and neither of them worked. I tried dragging the one out of there by using the "Add New Item" option, but they both disappeared. I've now figured out that nm-applet is working, but the icon is not showing up. It successfully connects to my wireless network even though the icon disappeared, which I can verify by running:

```
sudo NetworkManager --no-daemon
```

I'm starting to suspect that this is more of an issue with xfce, and not the nm-applet. When I type nm-applet into a Terminal window (something that was successful before the reboot), I get the following error:

```
~$ nm-applet
/bin/sh: /usr/bin/esd: not found
```

However, that error also appeared when I ran nm-applet successfully before. I can verify that the nm-process is running, and that I'm connected to the wireless network. I just don't see the icon anymore.

Any suggestions? Several reboots haven't solved the problem.

Thanks.

---

### Post by sargentdean on 2007-07-01
Thank you for a great tutorial. :popcorn:

I am a complete newbe to linux and could not get my wifi working before I found your tut. Now I am up and running on my laptop.

I just have one problem. Everytime I restart my computer I need to set up my wifi. I saw a fix on here somewhere, but can't find it now. Any ideas?

Again thanks,

Earl :D

---

### Post by Bill Cutler on 2007-07-01
A newbie here.  I have been reviewing posts for this problem and they have been very helpful but I have hit a stonewall.  I recently installed Dapper 6.06 and installed a Linksys PCI card WMP54GS removed from a Windows machine.  I have a working wireless network with two Windows desktops and a laptop connected.  I went the ndsiwrapper graphical route, removed (blacklisted) the installed Broadcom 43xx driver, installed the ndsiwrapper compatible driver (WMP54GS_20050406) and everything seemed to work ok thru the Graphical Driver install and Networkin install boxes.  However I have not been able to connect to the working network.  Any help would be appreciated.

Not sure this is the right thread for this, if not could you redirect me?

Thanks,
Bill Cutler

---

### Post by wil313 on 2007-07-02
Please help, I've done this ten times and it doesn't make sense, I get to step 13 and it says:

wil@wil-laptop:~/ndiswrapper/ndiswrapper-1.44$ ndiswrapper -l
bcmwl5 : invalid driver!

---

### Post by sunil12 on 2007-07-04
cant get wireless on my dell 5160. i am new to ubantu, have 1.7 on my system.
here is what i get when i go through below steps

sunil@sunil-laptop:~$ lspci | grep Broadcom\ Corporation
02:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
sunil@sunil-laptop:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules

Please help




> **ubunturules said:**
> This is the easiest way to get your Broadcom 4306 wireless card working in the shortest amount of time.  I wouldn't use the firmware cutter because it only allows you to run at 11 Mbps with it.  With ndiswrapper you will get 54 Mbps if your router will allow it.

Do everything in the order as it is listed.

Get the 32 bit drivers from [here]("http://home.nc.rr.com/thehinnants/stuff/drivers/bcmwl5.zip") or the website of the manufacturer of your wireless card.

Get the 64 bit drivers from [here]("http://home.nc.rr.com/thehinnants/stuff/drivers/64_bit_drivers.zip").  I've heard that you don't change the name .inf file to bcmwl5.inf just keep it the way it is.

run the following command to make sure you have a broadcom chipset wireless card.
**1.**```
lspci | grep Broadcom\ Corporation
```
[IMG]http://home.nc.rr.com/thehinnants/screenshots/verification.PNG[/IMG]

**2.**```
sudo rmmod bcm43xx
```

**3.**```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

[IMG]http://home.nc.rr.com/thehinnants/screenshots/blacklist.PNG[/IMG]

**5.**
```
sudo aptitude install build-essential
```

**6.**
```
uname -r
```

Insert the output of the uname -r command into the following 2 commands where the numbers are at

**7.**
```
sudo aptitude install linux-headers-2.6.17-10-generic
```

**8.**
```
sudo ln -s /usr/src/linux-2.6.17-10-generic /lib/modules/2.6.17-10-generic/build
```

Download ndiswrapper
**9.**
```
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.44.tar.gz
```

Make a folder for ndiswrapper and place it in there
**10.**
```
mkdir ~/ndiswrapper
mv ndiswrapper-1.44.tar.gz ~/ndiswrapper
```

Install ndiswrapper
**11.**
```
cd ~/ndiswrapper
sudo tar -xvzf ndiswrapper-1.44.tar.gz
cd ~/ndiswrapper/ndiswrapper-1.44
make distclean
sudo make
sudo make install
```

If you can't get ndiswrapper installed this way and you are running Dapper or Edgy run this command
```
sudo apt-get install ndiswrapper-utils-1.8
```

If you can't get ndiswrapper installed this way and you are running Feisty run this command
```
sudo apt-get install ndiswrapper-utils-1.9
```

If you can't get ndiswrapper from any of the sources above you can get it from the Ubuntu CD.

**12.**```
sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf
``` 
Make sure the .sys file is in there also, without it, it won't work

[IMG]http://home.nc.rr.com/thehinnants/screenshots/ndiswrapper_i.PNG[/IMG]

**13.**```
ndiswrapper -l
```
To make sure the hardware is present

[IMG]http://home.nc.rr.com/thehinnants/screenshots/ndiswrapper_l.PNG[/IMG]

**14.**```
sudo ndiswrapper -m
```
To load ndiswrapper automatically when the wlan0 interface is used

[IMG]http://home.nc.rr.com/thehinnants/screenshots/ndiswrapper_m.PNG[/IMG]

**15.**```
sudo modprobe ndiswrapper
```
To load the module

**Enable the Connection**

**16.** Go to System -> Administration -> Networking

**17.** If you don't see any wlan0 connections in Networking then you should restart your computer.

**18.** Go to your eth0 connection and disable the connection.
[IMG]http://home.nc.rr.com/thehinnants/screenshots/deactivate.PNG[/IMG]

**19.** Now go to your wlan0 connection and enable it.
[IMG]http://home.nc.rr.com/thehinnants/screenshots/enable.PNG[/IMG]

**Network Manager**

If you need WPA or WEP encryption do the following:

Note: If you are running Feisty you can skip steps 20 and 23.

**20.**```
sudo apt-get install network-manager-gnome
```

**21.**```
sudo gedit /etc/network/interfaces
```

**22.** Comment out anything in there at the bottom that has to do with your wireless essid.  You need to also comment out anything that says eth1, eth2, or atho.  When I say comment out that means put a # in from of it. You can leave all of the eth0, wlan0, lo, inet, and auto stuff.

**23.**```
nm-applet
```

**24.** Now click on the applet that is in the top right corner and you should see all of the available connections.  Click on yours and set it up.
[IMG]http://home.nc.rr.com/thehinnants/screenshots/nm-applet.png[/IMG]

**SOLUIONS TO PROBLEMS**

**Problem 1**
Totoro found a fix for the eth1 problem.  Thank You Totoro!
add ndiswrapper to /etc/modules
change eth1 -> wlan0 in the files below:
```
sudo gedit /etc/modeprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab
```

**Problem 2**
Shaton found a fix for the FATAL: Error inserting ndiswrapper problem.  Thank You Shaton!
If you get an error saying 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument 

then try this.
```
sudo apt-get install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```

If you are using Feisty then you will need to put a 9 where the 8 is.

**Problem 3**
If you get a lot of error messages talking about the icon then run this command:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

I hope this helps a lot of people!

---

### Post by ubunturules on 2007-07-04
sunil12: thats good you can move to step 2 now.  that command is supposed to remove it if it is in /proc/modules.  its kinda weird that it isnt in there but it should be ok.

ubunturules

---

### Post by sunil12 on 2007-07-04
[thanks for help
now i am step 13...dont know if everything is OK upto here

sunil@sunil-laptop:~$ lspci | grep Broadcom\ Corporation
02:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
sunil@sunil-laptop:~$ sudo rmmod bcm43xx
Password:
ERROR: Module bcm43xx does not exist in /proc/modules
sunil@sunil-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
sunil@sunil-laptop:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
sunil@sunil-laptop:~$ uname -r
2.6.20-16-generic
sunil@sunil-laptop:~$ sudo aptitude install linux-headers-2.6.20-16-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
sunil@sunil-laptop:~$ sudo ln -s /usr/src/linux-2.6.17-10-generic /lib/modules/2.6.20-16-generic/build
ln: creating symbolic link `/lib/modules/2.6.20-16-generic/build/linux-2.6.17-10-generic' to `/usr/src/linux-2.6.17-10-generic': File exists
sunil@sunil-laptop:~$ wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.44.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.44.tar.gz)
--14:20:34--  [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.44.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.44.tar.gz)
           => `ndiswrapper-1.44.tar.gz'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.44.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.44.tar.gz) [following]
--14:20:34--  [http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.44.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.44.tar.gz)
           => `ndiswrapper-1.44.tar.gz'
Resolving superb-east.dl.sourceforge.net... 209.160.66.130
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 195,228 (191K) [application/x-gzip]

100%[=========================================================================================================================>] 195,228      135.70K/s             

14:20:36 (135.41 KB/s) - `ndiswrapper-1.44.tar.gz' saved [195228/195228]

sunil@sunil-laptop:~$ mkdir ~/ndiswrapper
mkdir: cannot create directory `/home/sunil/ndiswrapper': File exists
sunil@sunil-laptop:~$ mv ndiswrapper-1.44.tar.gz ~/ndiswrapper
sunil@sunil-laptop:~$ cd ~/ndiswrapper
sunil@sunil-laptop:~/ndiswrapper$ sudo tar -xvzf ndiswrapper-1.44.tar.gz
ndiswrapper-1.44/
ndiswrapper-1.44/AUTHORS
ndiswrapper-1.44/ChangeLog
ndiswrapper-1.44/INSTALL
ndiswrapper-1.44/Makefile
ndiswrapper-1.44/README
ndiswrapper-1.44/ndiswrapper.spec
ndiswrapper-1.44/ndiswrapper.8
ndiswrapper-1.44/loadndisdriver.8
ndiswrapper-1.44/utils/
ndiswrapper-1.44/utils/Makefile
ndiswrapper-1.44/utils/ndiswrapper
ndiswrapper-1.44/utils/loadndisdriver.c
ndiswrapper-1.44/utils/ndiswrapper-buginfo
ndiswrapper-1.44/driver/
ndiswrapper-1.44/driver/divdi3.c
ndiswrapper-1.44/driver/hal.c
ndiswrapper-1.44/driver/iw_ndis.c
ndiswrapper-1.44/driver/iw_ndis.h
ndiswrapper-1.44/driver/loader.c
ndiswrapper-1.44/driver/loader.h
ndiswrapper-1.44/driver/longlong.h
ndiswrapper-1.44/driver/Makefile
ndiswrapper-1.44/driver/crt.c
ndiswrapper-1.44/driver/ndis.c
ndiswrapper-1.44/driver/ndis.h
ndiswrapper-1.44/driver/ndiswrapper.h
ndiswrapper-1.44/driver/ntoskernel.c
ndiswrapper-1.44/driver/ntoskernel.h
ndiswrapper-1.44/driver/ntoskernel_io.c
ndiswrapper-1.44/driver/pe_linker.c
ndiswrapper-1.44/driver/pe_linker.h
ndiswrapper-1.44/driver/pnp.c
ndiswrapper-1.44/driver/pnp.h
ndiswrapper-1.44/driver/proc.c
ndiswrapper-1.44/driver/rtl.c
ndiswrapper-1.44/driver/usb.c
ndiswrapper-1.44/driver/usb.h
ndiswrapper-1.44/driver/winnt_types.h
ndiswrapper-1.44/driver/workqueue.c
ndiswrapper-1.44/driver/wrapmem.h
ndiswrapper-1.44/driver/wrapmem.c
ndiswrapper-1.44/driver/wrapper.c
ndiswrapper-1.44/driver/wrapndis.h
ndiswrapper-1.44/driver/wrapndis.c
ndiswrapper-1.44/driver/lin2win.h
ndiswrapper-1.44/driver/win2lin_stubs.S
sunil@sunil-laptop:~/ndiswrapper$ cd ~/ndiswrapper/ndiswrapper-1.44
sunil@sunil-laptop:~/ndiswrapper/ndiswrapper-1.44$ make distclean
make -C driver clean
make[1]: Entering directory `/home/sunil/ndiswrapper/ndiswrapper-1.44/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm: cannot remove `ndiswrapper.ko': Permission denied
rm: cannot remove `ndiswrapper.o': Permission denied
rm: cannot remove `crt.o': Permission denied
rm: cannot remove `hal.o': Permission denied
rm: cannot remove `iw_ndis.o': Permission denied
rm: cannot remove `loader.o': Permission denied
rm: cannot remove `ndis.o': Permission denied
rm: cannot remove `ntoskernel.o': Permission denied
rm: cannot remove `ntoskernel_io.o': Permission denied
rm: cannot remove `pe_linker.o': Permission denied
rm: cannot remove `pnp.o': Permission denied
rm: cannot remove `proc.o': Permission denied
rm: cannot remove `rtl.o': Permission denied
rm: cannot remove `wrapmem.o': Permission denied
rm: cannot remove `wrapndis.o': Permission denied
rm: cannot remove `wrapper.o': Permission denied
rm: cannot remove `usb.o': Permission denied
rm: cannot remove `divdi3.o': Permission denied
rm: cannot remove `usb.o': Permission denied
rm: cannot remove `divdi3.o': Permission denied
rm: cannot remove `.ndiswrapper.ko.cmd': Permission denied
rm: cannot remove `.built-in.o.cmd': Permission denied
rm: cannot remove `.crt.o.cmd': Permission denied
rm: cannot remove `.divdi3.o.cmd': Permission denied
rm: cannot remove `.hal.o.cmd': Permission denied
rm: cannot remove `.iw_ndis.o.cmd': Permission denied
rm: cannot remove `.loader.o.cmd': Permission denied
rm: cannot remove `.ndis.o.cmd': Permission denied
rm: cannot remove `.ndiswrapper.mod.o.cmd': Permission denied
rm: cannot remove `.ndiswrapper.o.cmd': Permission denied
rm: cannot remove `.ntoskernel.o.cmd': Permission denied
rm: cannot remove `.ntoskernel_io.o.cmd': Permission denied
rm: cannot remove `.pe_linker.o.cmd': Permission denied
rm: cannot remove `.pnp.o.cmd': Permission denied
rm: cannot remove `.proc.o.cmd': Permission denied
rm: cannot remove `.rtl.o.cmd': Permission denied
rm: cannot remove `.usb.o.cmd': Permission denied
rm: cannot remove `.wrapmem.o.cmd': Permission denied
rm: cannot remove `.wrapndis.o.cmd': Permission denied
rm: cannot remove `.wrapper.o.cmd': Permission denied
rm: cannot remove `ndiswrapper.mod.c': Permission denied
rm: cannot remove `ndiswrapper.mod.o': Permission denied
rm: cannot remove `Module.symvers': Permission denied
make[1]: *** [clean] Error 1
make[1]: Leaving directory `/home/sunil/ndiswrapper/ndiswrapper-1.44/driver'
make: *** [clean] Error 2
sunil@sunil-laptop:~/ndiswrapper/ndiswrapper-1.44$ sudo make
make -C driver
make[1]: Entering directory `/home/sunil/ndiswrapper/ndiswrapper-1.44/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/sunil/ndiswrapper/ndiswrapper-1.44/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/sunil/ndiswrapper/ndiswrapper-1.44/driver'
make -C utils
make[1]: Entering directory `/home/sunil/ndiswrapper/ndiswrapper-1.44/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sunil/ndiswrapper/ndiswrapper-1.44/utils'
sunil@sunil-laptop:~/ndiswrapper/ndiswrapper-1.44$ sudo make install
make -C driver install
make[1]: Entering directory `/home/sunil/ndiswrapper/ndiswrapper-1.44/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/sunil/ndiswrapper/ndiswrapper-1.44/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo /lib/modules/2.6.20-16-generic/misc
/lib/modules/2.6.20-16-generic/misc
mkdir -p /lib/modules/2.6.20-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-generic/misc
/sbin/depmod -a 2.6.20-16-generic -b /
make[1]: Leaving directory `/home/sunil/ndiswrapper/ndiswrapper-1.44/driver'
make -C utils install
make[1]: Entering directory `/home/sunil/ndiswrapper/ndiswrapper-1.44/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/sunil/ndiswrapper/ndiswrapper-1.44/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
sunil@sunil-laptop:~/ndiswrapper/ndiswrapper-1.44$ ndiswrapper -l
bcmwl5 : invalid driver!
sunil@sunil-laptop:~/ndiswrapper/ndiswrapper-1.44$ 
sunil@sunil-laptop:~/ndiswrapper/ndiswrapper-1.44$ 


sunil





QUOTE=ubunturules;2962222]sunil12: thats good you can move to step 2 now.  that command is supposed to remove it if it is in /proc/modules.  its kinda weird that it isnt in there but it should be ok.

ubunturules[/QUOTE]

---

### Post by BlackOcellaris on 2007-07-08
Just wanted to say thanks for helping me out.  This guide had my card up and running very shortly on Kubuntu ;)

---

### Post by sunil12 on 2007-07-08
can some body help me please. I am still not able to get wireless working on my dell 5160.
thanks

> **ubunturules said:**
> sunil12: thats good you can move to step 2 now.  that command is supposed to remove it if it is in /proc/modules.  its kinda weird that it isnt in there but it should be ok.

ubunturules

---

### Post by oldsch00l on 2007-07-09
> **ubunturules said:**
> did this HOWTO help anyone?
I really wish I had found this weeks ago.  I have an HP laptop that I recently installed 64bit Kubuntu on.  I have been messing with the wireless on for weeks. I haven't given up but was close a few times.  I have followed several tutorials and installed countless files but nothing works.  I have ndiswrapper installed using the 32bit files from hp.  I assume that is my problem?  Can I just follow this tutorial with the correct 64bit drivers from the beginning or do I need to uninstall some of what I have done?  Linux sees the wlan and identifies it but won't allow me to enable it.
Thanks,

---

### Post by ubername on 2007-07-11
> **sargentdean said:**
> Thank you for a great tutorial. :popcorn:

I am a complete newbe to linux and could not get my wifi working before I found your tut. Now I am up and running on my laptop.

I just have one problem. Everytime I restart my computer I need to set up my wifi. I saw a fix on here somewhere, but can't find it now. Any ideas?

Again thanks,

Earl :D

Hi, same here about newbie etc. I just need to run 'sudo modprbe ndiswrapper' every time I reboot, but it would be nice to get it automatically. I have repeated step:

14.
Code:

sudo ndiswrapper -m

To load ndiswrapper automatically when the wlan0 interface is used

and get the message

'module configuration already contains alias directive'

Mind you, I'm incredibly impressed by this howto. I did not think I would be able to use my old lappy ever again so having to 'spark it up' every boot is no problem whatsoever!

---

### Post by MrMasterplan on 2007-07-12
This helped me initially. For two days I had wireless, including a few reboots. But now it doesn't work any more. The symbol next to the clock does say that the network is connected, but I cannot actually get online. Also, while it worked, I would get a little popup bubble saying that I am connected, but now I do not get this bubble, but if I hover the mouse over the symbol, I get told that it _is_ connected. (My network does have an internet connection, since when I plug in by wire, I'm online straight away).
I've tried rerunning 'sudo modprobe ndiswrapper' and 'ndiswrapper -m' like someone suggested.I'd be really grateful if someone has a solution to this.
Thanks.
Simon

---

### Post by phifer on 2007-07-12
> **ubername said:**
> Hi, same here about newbie etc. I just need to run 'sudo modprbe ndiswrapper' every time I reboot, but it would be nice to get it automatically. I have repeated step:

14.
Code:

sudo ndiswrapper -m

To load ndiswrapper automatically when the wlan0 interface is used

and get the message

'module configuration already contains alias directive'

Mind you, I'm incredibly impressed by this howto. I did not think I would be able to use my old lappy ever again so having to 'spark it up' every boot is no problem whatsoever!


```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

Should take care of you there.

ubunturules - thanks for the tutorial.

---

### Post by polygone on 2007-07-15
I am getting stuck at this point:

polygone@polygone-laptop:~/ndiswrapper/ndiswrapper-1.44$ sudo ndiswrapper -i ~/bcmwl5/bcmwl5.inf 
driver bcmwl5 is already installed
polygone@polygone-laptop:~/ndiswrapper/ndiswrapper-1.44$ ndiswrapper -l
bcmwl5 : invalid driver!
polygone@polygone-laptop:~/ndiswrapper/ndiswrapper-1.44$ sudo ndiswrapper -i ~/home/polygone/bcmwl5/bcmwl5.inf
driver bcmwl5 is already installed
polygone@polygone-laptop:~/ndiswrapper/ndiswrapper-1.44$ sudo ndiswrapper -i ~/home/polygone/bcmwl5/bcmwl5.inf
driver bcmwl5 is already installed
polygone@polygone-laptop:~/ndiswrapper/ndiswrapper-1.44$ sudo ndiswrapper -m
module configuration already contains alias directive


Is there a way to uninstall this and then continue from this point?

---

### Post by mrsock on 2007-07-18
Hey all, gotta problem here...

Laptop: Presario R3000
             Broadcom 4306 (verified) Internal Wireless with the button on the side to turn on and off.


So I followed this guide to a T and everything was going smoothly...but in the end my wireless connection option disappears. When I also use the ndiswrapper it tells me that the BCMWL5.INF file is an invalid driver. I've also tried using the BCMWL5A.INF driver and it still doesn't work (invliad driver). I have also tried the driver off the CD i got with my laptop and still no success. I have no idea where to go from here...I am a linux noob, seeing as how i just installed Ubuntu 7.04 last week and this has held me up for the entire week. lol. If anyone has any idea as to where or what might be causing this to malfunction please post back, because nothing i seem to be looking up helps.

---

### Post by ubunturules on 2007-07-18
polygone: to remove the driver run this command
```
sudo ndiswrapper -e bcmwl5
```

---

### Post by ubunturules on 2007-07-19
WE HAVE FINALLY HIT 100,000 VIEWS!!!!!!!! I have been waiting for this moment for a year! I started this guide a little over a year ago and I had no idea it was going to get this big.  One day I was just reading through a lot of guides putting a lot of things together but no guide had everything in it.  So that day I put it all together and it finally worked and at that point I had been working on trying to get my bcm43xx wireless card working.  I wanted to get it on here as fast as possible to help out as many people as possible. 100,000 views has been my goal for a while now and I'm glad that it has finally happened. This is awesome and it couldn't have happened without all of your help!  Thank you for your input and fixes that have helped turn this guide into one of the best bcm43xx guides on the internet.  I hope this guide has helped and will continue to help everyone that is trying to get there bcm43xx wireless card working.

100,000 VIEWS AND COUNTING

ubunturules

---

### Post by overdrank on 2007-07-22
works great Thanks!!!!!!!!!!!!!!!!:guitar:

---

### Post by PissedApache on 2007-07-22
Thanks for the guide! it was worth searching for :)

I had to use the 64 drivers so simply swapped the bcmwl5.inf for the 64 inf file i downloaded and voila! 

12.

sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf

---

### Post by nickajeglin on 2007-08-09
I need help. I'm a total linux newbie and have spent several hours trying to get my broadcom 4306 to work with no success. Everything in this tutorial went fine up to step 8 where I received a folder does not exist error. I continued hoping that this wouldn't be a problem. Well, before I did this, my card was showing up, labeled as eth1, now it's completely gone from network manager, and I'm stuck. Any help would be very appreciated. I also followed all the steps to get it labeled wlan0 instead of eth1.

---

### Post by Cybergod on 2007-08-17
I followed this tutorial and I'm still having problems.  I still don't have a wlan0 interface in "System" > "Administration" > "Network".  If I run the command iwconfig it doesn't even show a wlan0 interface.  My wireless was working when I used the bcm43xx-fwcutter but only with 11MB speeds and 50% signal setting right next to the router.  Any help with this issue will be greatly appreciated.

---

### Post by crjackson on 2007-08-26
I want to thank you very much for this guide.  I used it on my emachines m6809 and everything went perfect 1st time.  I havent even rebooted yet but I expect NO problems.  Thank you very much.

---

### Post by mychaelus on 2007-08-27
The first post was incredibly helpful. Also see [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper), which is the source for most of what follows.

I've had to reinstall ndiswrapper for my 4306 card so many times that I now use a batch process that takes less than a minute.

The following .deb packages have to be in your home folder:
ndiswrapper-common_1.38-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb
ndisgtk_0.6-0ubuntu3_all.deb
The .inf and .sys files that constitute the windows driver have to be  in a home folder called "drivers" for the following commands to work as is. These are the"bcmwl5.inf" and "bcmwl5.sys" files used by the 4306. Also, to work as is, your computer has to be a 386 type, i.e. not 64 bit.

The following block of commands will uninstall then reinstall ndiswrapper and activate the driver. I don't even paste the lines one by one anymore, I paste the whole block of lines all at once at the terminal prompt. (Blocks can be entered this way if a password has been entered once already in the terminal session.)

sudo modprobe -r ndiswrapper
sudo apt-get --purge remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils*.deb
sudo dpkg -i --force-depends ndisgtk_*.deb
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo ndiswrapper -i ~/drivers/bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

To make sure ndiswrapper is launched at startup, open /etc/modules (sudo gedit /etc/modules) and add the word ndiswrapper to the bottom of the list, then save and close.

Ubuntu's Network Manager gave me tons of problems, so I replaced it with  WIcd , which has been super easy to set up and use. ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/))

I hope others find this helpful. The first poster gave me my first ray of hope, which led to a solution, so many thanks and kudos to him.

---

### Post by AlfaTrion on 2007-08-27
> **rlynch said:**
> 
1 - Thanks for posting how to change eth1 to wlan0
2 - Thanks for posting the inf and sys driver files
3 - Thanks for taking the time and posting this tutorial. ^ what he said!

im only on page 13 of this 63 page post.
it works but now kwifimanager wont start unless i type it in a terminal. 
otherwise it tries to load for 20 seconds then dies. same thing when i do alt+f2. what is so diff with a terminal??

how can i fix this? I'll continue reading from page 13-63 in the mean time if the answer is already here.

Thanks again for the howto tho. 54 is better than 11!

---

### Post by ubunturules on 2007-08-28
AlfaTrion: make sure you have kwifimanager set to run at start up.

ubunturules

---

### Post by Griff on 2007-08-28
OK.  So this is really weird.  Long story short:

Install 1: no success.

Install 2: Success! ... Until I rebooted to find that wlan0 isn't listed under knetworkmanager as an option to switch to anymore.  wlan0 was however still listed as a working device.

Install 3: No success with knetworkmanger like before but I install kwifimanager and now I can view my home network!  So maybe I was ok before? The option to connect to it though is grayed out.  Maybe WEP is an issue?  Any ideas on what the heck is going on here?

Thanks for the help,
Griff

---

### Post by Griff on 2007-08-28
OK.  So I can view networks no problem now.  I just can't seem to stay connected to them.  I have a wireless router/modem that I can see fine.  If I activate the connection in Managed mode I'll be connected for a few seconds and then it's gone.  Ad-Hoc seems to be a no go.  Any ideas?

Thanks,
Griff

---

### Post by AlfaTrion on 2007-08-28
> **ubunturules said:**
> AlfaTrion: make sure you have kwifimanager set to run at start up.

ubunturules

Didn't work :(
I dragged the link into my /home/alfatrion/.kde/Autostart dir where I have beryl and tilda (which work)


EDIT
> **Griff said:**
> OK.  So I can view networks no problem now.  I just can't seem to stay connected to them.  I have a wireless router/modem that I can see fine.  If I activate the connection in Managed mode I'll be connected for a few seconds and then it's gone.  Ad-Hoc seems to be a no go.  Any ideas?

Thanks,
Griff

the not staying connected part happens to me but when i use wlassistant (wireless assistant)

---

### Post by Griff on 2007-08-28
> **AlfaTrion said:**
> i use wlassistant (wireless assistant)

That totally just fixed my problem.  I'm wireless again!  Thanks!
-Griff

---

### Post by AlfaTrion on 2007-08-28
> **Griff said:**
> That totally just fixed my problem.  I'm wireless again!  Thanks!
-Griff

wait, so what r u using now?

---

### Post by AlfaTrion on 2007-08-30
> **nyinge said:**
> 
If you're lazy like me, put the following in a file:
```

sudo modprobe ndiswrapper
sudo iwconfig wlan0 essid YOUR_SSID
sudo dhclient wlan0

```
And run it as ```
sudo sh home-wifi
```
"home-wifi" being the name of the file.  See, just 3 simple lines.  :KS 

Ok, post back your results.

when i do iwconfig and dhclient my wlan0 connects right away! no more enable/disable and waiting for 10mins! thanks nyinge!!!
:guitar: <-- you

---

### Post by crjackson on 2007-08-30
Okay, I followed this guide  and it worked perfectly 1st time right out of the gate. I then followed some other instructions to make keyring manager stop asking me to input a password everytime I reboot.  That worked.

Life was great for about 3 days.  Then for no reason I can figure, it won't connect anymore.

It shows my network (as well as others in the area), the little animated icon gives me one green ball on the notification area, and it just keeps spinning.

Finally it craps out and askes me for my WPA password again.  I input the information, and the whole process starts over again with the same result.  No connection.

It's also NOT connecting to the UNPROTECTED wireless networks it picks up.

Where do I go from here?

---

### Post by crjackson on 2007-08-30
anyone?

---

### Post by crjackson on 2007-08-31
[B][SIZE="5"]Would someone please have a stab at this, I really need assistance from a guru.

My wireless card sees networks in range but can't connect to them.  It doesn't matter if the network is unsecured or if I try to connect to my secured network.

PLEASE HELP...[/SIZE][/B]

---

### Post by AlfaTrion on 2007-09-04
im far from a guru but if you had it working, try this:

install kwifimanager
open the configuration editor window
for network name, put 'any' > apply

it might take some time to get an ip but to speed things up try going to the cosole and doing:

```
sudo ifdown wlan0
sudo ifup wlan0
```

try it again if you dont get an ip the first time

this process works for me whenever i turn on my laptop at different locations.

good luck

---

### Post by crjackson on 2007-09-05
> **AlfaTrion said:**
> im far from a guru but if you had it working, try this:

install kwifimanager
open the configuration editor window
for network name, put 'any' > apply

it might take some time to get an ip but to speed things up try going to the cosole and doing:

```
sudo ifdown wlan0
sudo ifup wlan0
```

try it again if you dont get an ip the first time

this process works for me whenever i turn on my laptop at different locations.

good luck

Thanks - I'll try that next time.  I actually got it working again after wiping my HD with another new format and reinstalled everything again.  It was a fresh install and probably not needed, but when I couldn't get any help, I started from scratch.  Thanks again...

---

### Post by Kedster on 2007-09-08
Please insert the disk labeled:
Edubuntu 7.04 _Feisty Fawn_ - Release i386 Binary-1 (20070415)
in drive /cdrom/


what do i do if that comes up

---

### Post by Kedster on 2007-09-08
kedster@spadhawk:~$ lspci | grep Broadcom\ Corporation
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
kedster@spadhawk:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules

---

### Post by Goodkimchee on 2007-09-08
Ok, I have a question here.  I get an error on the SECOND  step!  

ERROR: Module bcm43xx does not exist in /proc/modules

What am I supposed to do? 

I have Compaq Presario R3000, Athlon64 3000+, 500MB RAM, and my network controller is Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

Any and all help would be very grateful.

---

### Post by Kedster on 2007-09-08
i have the exact same prob i posted the output of step 2 above

---

### Post by ubunturules on 2007-09-09
This is not a problem.  Just procede to the next step.

That command is supposed to remove bcm43xx from that file so that error is telling you that bcm43xx isn't there which is a good thing.

---

### Post by Youkai on 2007-09-13
Thanks for the guide - managing interfaces, wireless, and ndiswrapper are a deep mystery in Linux, but the step-by-step guide got me up to speed pretty quickly.  And all the follow-up tips got me the rest of the way.

Even though the initial driver install went smoothly, actually getting my card working & keeping it working were the biggest challenges.

So I thought I'd share a few of my problems, and how I solved them:

[LIST]
[*]Wireless configuration tools could "see" wireless networks, but couldn't connect to them.

I found kwifimanager to be pretty useless.  Even when running as sudo, It would display networks, but not offer any "connect" option.  The wlassistant that AlfaTrion suggested, worked great, though - let me configure the properties, and connected to my home network.


[*]Automatically connecting to the network, without having to do anything.

By default, the wlan0 interface would be "up", but the wireless card  wouldn't connect to my home network.  I could get the network up and running myself, using various combinations of ifup/down & wlassistant.  But I was setting up a laptop for my wife to use almost exclusively at home, where it should "just work" without any effort on her part.  The way I found to make the wireless network settings "stick", and be automatically enabled, was to edit /etc/network/interfaces, and explicitly add the default network settings:
```

# Bring up the wlan0 interface during boot
auto wlan0
# The general network interface settings for a static IP
iface wlan0 inet static
  address 192.168.0.20
  netmask 255.255.255.0
  gateway 192.168.0.1
  # Wireless settings specific to my home network
  wireless-essid miko
  wireless-mode Managed
  wireless-channel 2
  wireless-ap any
  wireless-rate auto
  wireless-key c00c-69a8-fcb7-b83c-fd7b-4f46-08

```
[/LIST]

But what if I want to go to a coffee shop and connect to a different access point?  I haven't tried it yet, but I think I can just use wlassistant in those cases, to explicitly reconnect to those networks.  I'll probably need to do something about that static IP, though - maybe I'll just switch over to DHCP at home too, and avoid the issue.

Caveat: I'm still on an 802.11b (11Mbps) network, with a 128-bit WEP key, though I imagine this should still work with an 802.11g network.

---

### Post by mandeep kaur on 2007-09-24
Hi,

I have tried all the instructions given above. But I am not able to connect to our wireless network please help me out. 

Thanks

Mandeep Kaur

---

### Post by mandeep kaur on 2007-09-24
Hi,

I have tried all the instructions given on the First page of this thread. But I am not able to connect to our wireless network. Please help me out. We are using netgear WGT624v3 108 Mbps Firewall Wireless Router.

Thanks

Mandeep Kaur

---

### Post by ubunturules on 2007-09-24
post the output of the following command.
```
lspci | grep Broadcom\ Corporation
```

ubunturules

---

### Post by mandeep kaur on 2007-09-25
The output of above command

0000:02:02.0 Network controller: Broadcom Corporation BCM4306  802.11b/g Wireless Lan controller (rev 03)

thanks

Mandeep kaur

---

### Post by ubunturules on 2007-09-26
alright that's good.  now where are you having problems?

ubunturules

---

### Post by bsmonks on 2007-09-27
Dude, you rock!! I can't tell you how many of these tutorials I've followed and have been unable to get my card working. Then I found yours. <cue heavenly angels singing> I have an HP laptop (zd7000a which used to be a zd7180us) with the 4306 built in. None of the other's drivers worked. And you were the only one that offered/suggested two inf files-bcmwl5 & bcmwl5a. It was the 5a that got me up and running. 

If you're ever in San Diego, California, PM me and I'll buy you dinner!

---

### Post by mandeep kaur on 2007-09-28
Thanks for your reply,

The problem is I am not able to get wireless connection into it.
 
With Regards

Mandeep Kaur

---

### Post by bsmonks on 2007-09-28
Mandeep, do you have any security enabled on your wireless router?

---

### Post by mandeep kaur on 2007-09-30
Yes,
WEP Security is enabled

---

### Post by SimonM on 2007-09-30
I haven't read *all* of this post (sorry), I only got to page 32, but my that stage I gave up searching for my solution

Basically, the first time I used my card after the install it worked fine. The second time it didn't connect until I wired it and mess about for a bit.

I am having a problem where I have to do "something" each time before it gets an IP. It finds the network and connects, but doesn't get an IP from it :(

---

### Post by bsmonks on 2007-09-30
Mandeep, I would recommend that you first try to get connected without using security. After accessing your open router (basically proving that you can), then enable the security on the router and enter the pass-key into your laptop.

---

### Post by ferrari62589 on 2007-10-06
I followed all steps, while running ubuntu fiesty 7.04

I have a broadcom 4306 rev 3 card in a hp zv5410us laptop

I tried installing both bcmwl5 and bcmwl5a, and dmesg outputs this
```

[   25.628000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   25.700000] ndiswrapper: driver bcmwl5 (Linksys,07/17/2003, 3.30.15.0) loaded
[   25.700000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[   25.700000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNK3] -> GSI 17 (level, low) -> IRQ 21
[   25.704000] ndiswrapper (NdisWriteErrorLogEntry:231): log: C000138D, count: 1, return_address: e0d08be3
[   25.704000] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0x103
[   25.704000] ndiswrapper (miniport_init:275): couldn't initialize device: C0000001
[   25.704000] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[   25.704000] unregister_netdevice: device eth%d/d7f3a000 never was registered
[   25.704000] ndiswrapper (miniport_halt:339): device d7f3a400 is not initialized - not halting
[   25.704000] ndiswrapper: device eth%d removed
[   25.704000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[   25.704000] ndiswrapper: probe of 0000:02:02.0 failed with error -22

```
something about device could not int., **there is no wlan0 in the network manager** and when i try to press the wireless on/off button, the light does not turn on, it is always off.

any help is appreciated thanks a lot

---

### Post by ferrari62589 on 2007-10-06
Ok i solved my own problem, the problem was only the generic bcmwl5 drivers weren't compatible, but i extracted the hp ones of the site and they worked fine.

I have a hp zv5410us with a broadcom 4306 rev03, if any1 else wants the drivers for this card they are here [drivers]("http://featusa.com/bcm/")

---

### Post by ubunturules on 2007-10-10
The drivers I linked to on the first post work for most cards but I they work for all of them.  I think I will put this in the first post.  This could be why people don't find their card under network.

ubunturules

---

### Post by Count Doofus on 2007-10-21
You'll get that error @ line 174 if the case of the filename  is wrong !


had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#! 

Case Sensitive !!!!%^@#%@#$@% I hate Case Sensitive !%$#

---

### Post by Hunterkiller5150 on 2007-10-21
Hello, 
This How To helped me a while ago with getting my wireless working and thank you very much for that.  But last night I upgraded to 7.10 and now it is not working again.  I followed all the steps again, but with the updated ndiswrapper. I also enabled the firmware in the restricted device manger and that didn't work either.  I really need my wireless working and am running out of ideas on how to fix it.  I can see wireless networks but cannot connect to them.  The wireless seems to not work as soon as I go to connect to any of them.  There is WPA on the network but I know that is not the problems since I had it working before the 7.10 update.  Any help would be great!
Thanks

---

### Post by crjackson on 2007-10-21
> **Hunterkiller5150 said:**
> Hello, 
This How To helped me a while ago with getting my wireless working and thank you very much for that.  But last night I upgraded to 7.10 and now it is not working again.  I followed all the steps again, but with the updated ndiswrapper. I also enabled the firmware in the restricted device manger and that didn't work either.  I really need my wireless working and am running out of ideas on how to fix it.  I can see wireless networks but cannot connect to them.  The wireless seems to not work as soon as I go to connect to any of them.  There is WPA on the network but I know that is not the problems since I had it working before the 7.10 update.  Any help would be great!
Thanks

I'm just going to chime because I have the same problem.  The guide doesn't work under gutsy and neither does enabling the cutter thingy under restricted drivers. Any help for this would be great.  Thanks

---

### Post by sapack on 2007-10-22
> **crjackson said:**
> I'm just going to chime because I have the same problem.  The guide doesn't work under gutsy and neither does enabling the cutter thingy under restricted drivers. Any help for this would be great.  Thanks
I shall chime in as well.  Same problem.  Comaq Presario 2100 Laptop.  Broadcom card.  I have enabled the restricted drivers.  I see networks.  I just can't connect to them.  It's driving me nuts.  EDIT: I forgot to mention, this was 7.10.

---

### Post by ubunturules on 2007-10-22
I will update the guide to work with gutsy as soon as I can.  I've been real busy lately but I will have a guide that works with gutsy by the end of the week if not sooner.

---

### Post by crjackson on 2007-10-22
> **ubunturules said:**
> I will update the guide to work with gutsy as soon as I can.  I've been real busy lately but I will have a guide that works with gutsy by the end of the week if not sooner.

Thanks.  I was about to switch back to 7.04 on the lappy.

---

### Post by ubunturules on 2007-10-22
The guide now works with Gutsy Gibbon.  10/22/07

ubunturules

---

### Post by crjackson on 2007-10-22
> **ubunturules said:**
> The guide now works with Gutsy Gibbon.  10/22/07

ubunturules

Thanks, can you indicate what is different?  I currently installed ndiswrapper / tools from synaptic on the second attempt.  Do I need to remove this and comple from scratch or simply unload the current driver?

---

### Post by ubunturules on 2007-10-22
When it comes to compiling things you most likely want to start over from scratch.  Remove everything you possibly can.

---

### Post by crjackson on 2007-10-22
> **ubunturules said:**
> When it comes to compiling things you most likely want to start over from scratch.  Remove everything you possibly can.

Okay thanks, I'll do that.  What was the change that had to be made for Gutsy?

---

### Post by ubunturules on 2007-10-22
This guide is not 100% ready for Gutsy I just restarted my computer and I have no wireless connection at all.  Let me do a little bit more testing and I will for sure have a working guide in a couple of days if not tomorrow.  I'm going to do a complete reinstall and start over fresh so I will know for sure what the problems are.  Sorry crjackson.  I will try to get a working guide as soon as possbile.

ubunturules

---

### Post by crjackson on 2007-10-22
> **ubunturules said:**
> This guide is not 100% ready for Gutsy I just restarted my computer and I have no wireless connection at all.  Let me do a little bit more testing and I will for sure have a working guide in a couple of days if not tomorrow.  I'm going to do a complete reinstall and start over fresh so I will know for sure what the problems are.  Sorry crjackson.  I will try to get a working guide as soon as possbile.

ubunturules

No problem.  I just greatful for the help.  Were it not for your 1st guide I wouldn't have had wireless the 1st time around.  Using your guied for 7.04 took me less than five minutes to get wireless on a fresh install.

Thanks again...

---

### Post by ubunturules on 2007-10-22
The guide now works with Gutsy and I am for sure this time.  I found the problem.  For some reason ndiswrapper wasn't loaded into /etc/modules when I restarted but I fixed this by removing the modprobe ndiswrapper command with a command that manually puts ndiswrapper in /etc/modules.

ubunturules

---

### Post by crjackson on 2007-10-23
> **ubunturules said:**
> The guide now works with Gutsy and I am for sure this time.  I found the problem.  For some reason ndiswrapper wasn't loaded into /etc/modules when I restarted but I fixed this by removing the modprobe ndiswrapper command with a command that manually puts ndiswrapper in /etc/modules.

ubunturules

I'll work on this in a few hours.  Thanks.

---

### Post by SuperAndy on 2007-10-23
yep, that works. the modprobe command would always fail and not write the ndiswrapper module to the correct place. but that manual command works fine.

thanks a lot!

---

### Post by ubunturules on 2007-10-23
I got two question for everyone.  

1. Do ya'll think I should completly remove the modprobe ndiswrapper command and replace it with the other command or does modprobe ndiswrapper do something that the other command doesn't.

2. How do I put HOWTO: infront of the thread title.  Some people probably don't know this is a howto.

Thanks for the help.

ubunturules

---

### Post by crjackson on 2007-10-23
> **ubunturules said:**
> I got two question for everyone.  

1. Do ya'll think I should completly remove the modprobe ndiswrapper command and replace it with the other command or does modprobe ndiswrapper do something that the other command doesn't.

2. How do I put HOWTO: infront of the thread title.  Some people probably don't know this is a howto.

Thanks for the help.

ubunturules

Okay, so have a look at this and tell me what to do next please.  I'm having no luck.

[B]charles@eMachines-m6809:~$ sudo ndiswrapper -m
[sudo] password for charles:
module configuration already contains alias directive

charles@eMachines-m6809:~$ ndiswrapper -l
bcmwl564 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
charles@eMachines-m6809:~$ [/B]

---

### Post by ubunturules on 2007-10-23
actually you are having luck.

1. charles@eMachines-m6809:~$ sudo ndiswrapper -m
[sudo] password for charles:
module configuration already contains alias directive

this is ok.  it's just telling you its already contains the alias.  you must have already ran the command or something.

2. charles@eMachines-m6809:~$ ndiswrapper -l
bcmwl564 : driver installed
device (14E4:4320) present (alternate driver: bcm43xx)

this is also ok.  the correct bcmwl564 driver is installed and dont worry about the alternate driver thing.

ubunturules

---

### Post by crjackson on 2007-10-23
> **ubunturules said:**
> actually you are having luck.

1. charles@eMachines-m6809:~$ sudo ndiswrapper -m
[sudo] password for charles:
module configuration already contains alias directive

this is ok.  it's just telling you its already contains the alias.  you must have already ran the command or something.

2. charles@eMachines-m6809:~$ ndiswrapper -l
bcmwl564 : driver installed
device (14E4:4320) present (alternate driver: bcm43xx)

this is also ok.  the correct bcmwl564 driver is installed and dont worry about the alternate driver thing.

ubunturules

Then what should I do next?  It doesn't show up in the network manager.  The LED indicator on the keyboard shows it's turned off.  There is a function key that normally toggles it on/off but it's having no effect.  When it's working, it defaults to ON from boot.

I don't know what to do next.  Any suggestions?

---

### Post by ubunturules on 2007-10-24
what is the output of the first command.  you might not have the right driver for your card.

ubunturules

---

### Post by crjackson on 2007-10-24
> **ubunturules said:**
> what is the output of the first command.  you might not have the right driver for your card.
ubunturules

It's the same driver I used for 7.04 64-bit.  It worked like a charm.
[B]
charles@eMachines-m6809:~$ lspci | grep Broadcom\ Corporation
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
charles@eMachines-m6809:~$[/B]

[B]charles@eMachines-m6809:~$ ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 
charles@eMachines-m6809:~$[/B]

---

### Post by ubunturules on 2007-10-24
Well I see that you have wireless under the network settings which is very good.  You should be able to click on the network-manager applet in the top right corner.  I'm sorry what is your problem again?

ubunturules

---

### Post by gr8birdie on 2007-10-24
ubunturules......this was a great how to.....worked like a charm....nice to have people in this community that are so willing to help.....good bye MICROSOFT.....

---

### Post by gr8birdie on 2007-10-24
I had it working but had to modprobe ndiswrapper everytime I rebooted...your help was great and now my WPC54g works like a champ with WEP enabled!!!  [COLOR="Red"]**Way to go ubunturules**[/COLOR]

---

### Post by smirks on 2007-10-24
> **ubunturules said:**
> The guide now works with Gutsy and I am for sure this time.  I found the problem.  For some reason ndiswrapper wasn't loaded into /etc/modules when I restarted but I fixed this by removing the modprobe ndiswrapper command with a command that manually puts ndiswrapper in /etc/modules.

ubunturules

Try as I may I cannot get this to work in gusty.  I seem to be having several issues:

1) The wlan adapter seems to get added as eth1.  I've followed all the steps in the first post that are supposed to get it as wlan0.  This isn't that big a problem, but it may be related to #2.

2) ndiswrapper loads fine on boot, however I can't seem to join the wireless network via the Network Manager GUI.  Whenever I try I punch in the SSID and the WEP key and blue dots spin and spin and spin, but it never associates.  The ONLY way I can get it to work is to run the following from the CLI:

```
sudo iwconfig eth1 essid <SSID> key <WEP-KEY> 
``` 

I'm at a loss for what else to try.  Any ideas are appreciated.

To note, this was running feisty previously and using the fwcutter driver, however I was getting crazy packet loss and 15 second ping times to my router with the fwcutter driver in gusty.

Thanks in advance!

---

### Post by crjackson on 2007-10-24
> **ubunturules said:**
> Well I see that you have wireless under the network settings which is very good.  You should be able to click on the network-manager applet in the top right corner.  I'm sorry what is your problem again?

ubunturules

It's greyed out and not selectable.  There is no signal.  It does nothing.  The OS won't activate the card at all.  I checked the blacklist file today and found no entries relating to the old 43xx driver.

I inserted the entry and rebooted.  On reboot, the wireless LED began to flicker on/off like a neon bulb with a bad starter, and it caused the boot to stall.  Next I used the keyboard function key to TURN OFF the wireless card and the booting continued properly.  Once booted I turned on the card manually and it caused the system to stall and freeze.  I turned it off again and every(else) started to work normally.

No matter what I did manually, network manager did not detect an activated wireless device and it did not have any signal bars.

What next?

---

### Post by ubunturules on 2007-10-25
let me see what's in all of your important files

```
sudo gedit /etc/modeprobe.d/ndiswrapper
```
```
sudo gedit /etc/network/interfaces
```
```
sudo gedit /etc/iftab
```
```
sudo gedit /etc/modprobe.d/blacklist
```

ubunturules

---

### Post by crjackson on 2007-10-25
I'll do that in a bit.  I just wiped the drive and I'm reinstalling now.  The version included with Gutsy is newer than the 1.48 file in your guide.  Do you suggest I stick with the 1.48 version or try one of the newer versions?

[B]charles@emachines-m6809:~/Desktop/64_bit_drivers$ sudo ndiswrapper -i bcmwl564.inf
installing bcmwl564 ...
couldn't find SourceDisksFiles section - continuing anyway...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
charles@emachines-m6809:~/Desktop/64_bit_drivers$ ndiswrapper -l
bcmwl564 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
charles@emachines-m6809:~/Desktop/64_bit_drivers$

charles@emachines-m6809:~/Desktop/64_bit_drivers$ ndiswrapper -l
bcmwl564 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
charles@emachines-m6809:~/Desktop/64_bit_drivers$ 

charles@emachines-m6809:~/Desktop/64_bit_drivers$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 
charles@emachines-m6809:~/Desktop/64_bit_drivers$[/B]

---

### Post by ubunturules on 2007-10-25
Everything you posted looked right.  I haven't seen any problems yet.  Get back to me on those files because the problem most likely lies in them.

ubunturules

---

### Post by crjackson on 2007-10-25
sudo gedit /etc/modprobe.d/ndiswrapper
**alias wlan0 ndiswrapper**

sudo gedit /etc/network/interfaces
[B]auto lo
iface lo inet loopback[/B]

sudo gedit /etc/iftab
**_[COLOR="Red"]There is no such file or directory on my computer as far as I can tell.[/COLOR]_**

sudo gedit /etc/modprobe.d/blacklist
[B]# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx

[/B]

---

### Post by Cybergod on 2007-10-25
I'm having the same exact problem as crjackson.  I'm using the 32-bit driver though.

---

### Post by Cybergod on 2007-10-25
I got mine working, I had to download my wifi driver from my laptop manufacturers website.  The only problem I'm having now is that my wireless connection is showing up as eth1 and not wlan0.  I did follow the instructions at the beginning.  In /etc/network/interfaces, there is not eth0, eth1, or wlan0.  I don't have a /etc/iftab either.  Everything else has wlan0 in it.

---

### Post by f37u5g0d on 2007-10-25
I tried to use the how to and now my wireless card doesn't show up in network settings.  I tried running the command that it said at the end of the how to "in case your card dissappears when you reboot)  What should I do??  Also my wired connection dissappears (always has even before attempting this how to).  The only way I can get it back is if I hit the power switch on my power supply.  IDK if this is related or not.  Help please!

---

### Post by ubunturules on 2007-10-25
yeah I've got to go with cybergod on this one.  I think you might have a driver issue or something because everything your posting is exactly what you're supposed to have.

ubunturules

---

### Post by crjackson on 2007-10-25
> **ubunturules said:**
> yeah I've got to go with cybergod on this one.  I think you might have a driver issue or something because everything your posting is exactly what you're supposed to have.

ubunturules

I downloaded the driver from this howto.  As you can see from my previous posts I have a Broadcom 4306.  I downloaded and used the same driver under Feisty64 and it was flawless.

I guess I'm going back to Feisty if there's no help for this in Gutsy...

Thanks for trying.

---

### Post by crjackson on 2007-10-25
> **ubunturules said:**
> let me see what's in all of your important files

```
sudo gedit /etc/iftab
```

ubunturules

What was the deal with me NOT having this file?  Could that be the problem?

---

### Post by Cybergod on 2007-10-25
> **crjackson said:**
> What was the deal with me NOT having this file?  Could that be the problem?

I don't have this file either.  Who is the manufacturer of your laptop?  I have an HP and I went to hp.com and found the driver for my laptop.  I downloaded it and used wine to open the .exe and then I was able to use that driver.  Everything is working great now.  I would like to figure out how to get my interface changed from eth1 to wlan0.

---

### Post by crjackson on 2007-10-25
> **Cybergod said:**
> I don't have this file either.  Who is the manufacturer of your laptop?  I have an HP and I went to hp.com and found the driver for my laptop.  I downloaded it and used wine to open the .exe and then I was able to use that driver.  Everything is working great now.  I would like to figure out how to get my interface changed from eth1 to wlan0.

It's an eMachines m6809.  Pretty sure they won't have a 64-bit driver.  There was no 64-bit OS option when purchased and they don't offer much support anyway.

I can't understand why the driver would be the problem when it worked perfectly under Feisty 64-bit.  I just don't get it...

---

### Post by Cybergod on 2007-10-25
Here is a link to the eMachines website that has a driver for your wireless card.  [http://www.emachines.com/support/product_support.html?cat=Notebooks&subcat=M-Series&model=M6809]("http://www.emachines.com/support/product_support.html?cat=Notebooks&subcat=M-Series&model=M6809")

---

### Post by crjackson on 2007-10-25
> **Cybergod said:**
> Here is a link to the eMachines website that has a driver for your wireless card.  [http://www.emachines.com/support/product_support.html?cat=Notebooks&subcat=M-Series&model=M6809]("http://www.emachines.com/support/product_support.html?cat=Notebooks&subcat=M-Series&model=M6809")

I'll have a look at it when I get home, but I think it's a 32-bit driver as it says OS WinXP.  Perhaps they have been kind enough to pack a 64-bit version as well.

I still don't understand why the 64-bit driver in this how to would work perfectly under Feisty and not Gutsy...

---

### Post by crjackson on 2007-10-26
Well I downloaded their driver package but It has not bcmwl564.inf inside.  There is a 564.sys file but not the inf.

If you know where to get the inf file let me know and I'll try it.

I did reinstall gutsy twice today but no joy there.

any other suggestions?  If no one can help I guess it means I have to revert to Feisty since the posted guide/drivers work perfectly under 7.04 64-bit.

---

### Post by ubunturules on 2007-10-26
You must of downloaded the wrong thing because I went to that sight and found both the .inf and .sys file.  I will make a folder for you crjackson because for some reason I can't attach them. home.nc.rr.com/thehinnants/stuff/crjackson/drivers

hope this works

ubunturules

---

### Post by crjackson on 2007-10-26
> **ubunturules said:**
> You must of downloaded the wrong thing because I went to that sight and found both the .inf and .sys file.  I will make a folder for you crjackson because for some reason I can't attach them. home.nc.rr.com/thehinnants/stuff/crjackson/drivers

hope this works

ubunturules


Thanks I really appriciate it.  It was a HUGE download.  I actually ran it on the lappy under winXP and it works fine, but it didn't have the 64-bit inf after extracted.  Then I downloaded it to my Gutsy desktop and burned it.  I browsed the extracted files (couldn't browse the CAB files) and still no 64-bit inf's.  It must be the wrong download.

---

### Post by crjackson on 2007-10-26
Okay, I had a look and downloaded.  These files I already have.

Am I wrong in thinking that these are 32-bit and not the 64-bit.

64-bit is what I need unless I'm missing something here...

---

### Post by crjackson on 2007-10-26
Could this be the problem?  I found 2 other people who claim to have lost their wireless connection after applying this procedure to fix a problem related to slow booting and no splash screen.

[B]To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`[/B]

I did this before testing the wireless.  I don't know how to go about undooing it short of clean install.

Also, since an inf file is only a text file, wouldn't it be the same for 32/64 bit?  Since I have the 64-bit *.sys file for my card, couldn't I just rename the 32-bit *.inf file to match the 64-bit *.sys file?

---

### Post by ubunturules on 2007-10-26
yeah sorry now that I look at it I did post the wrong drivers.  yes that isn't a bad idea to just rename the .inf file and use the 64 bit .sys.  I will pos the link so you can try it out. [http://home.nc.rr.com/thehinnants/stuff/crjackson/drivers](http://home.nc.rr.com/thehinnants/stuff/crjackson/drivers)

---

### Post by Bluearrow on 2007-10-27
Yes it did finally thanks to your last comment on ndiswrapper folder allocation. I have been struggling with my Dell desktop and a broadcom 4306 for the past 4 months. You are the only post that describes what to do when some step does not work. You are clearly on top of the game. Other posts should be claned out because they are misleading folks new to ubuntu like me. I would strongly suggest to adopt your method for all toubleshooting. Thank you!

---

### Post by crjackson on 2007-10-27
> **ubunturules said:**
> yeah sorry now that I look at it I did post the wrong drivers.  yes that isn't a bad idea to just rename the .inf file and use the 64 bit .sys.  I will pos the link so you can try it out. [http://home.nc.rr.com/thehinnants/stuff/crjackson/drivers](http://home.nc.rr.com/thehinnants/stuff/crjackson/drivers)

Well, I actually got it working.  From another fresh install, I went to synaptic package manager.  I installed ndiswrapper, ndiswrapper tools, and the gtk graphical tool for ndiswrapper.

Then I used the sections from your howto to remove the 43xx module, then I blacklisted it.

I renaed the *.inf file to match the *.sys file as discussed and it loaded without problem.

Then I followed the steps to load the module but it told me it was already loaded so I guess the graphicl tool did that for me.

I did a ctrl-alt-backspace and nothing happened...
I rebooted and nothing happened...
I did a sudo depmod -a and rebooted...
Nothing happened...
I rebooted again, and on boot up my wireless indicator came on...
After the desktop loaded and I logged in, I clicked on the network manager and it saw many wireless signals in the area.

I selected mine and entered the TKIP information and BANG!  I'm in...
I was just about to give up on Gutsy.  I have learned that the ndiswrapper tools from synaptic are great for me.  No more compiling.  I just needed to get the module to load...

Thanks...

---

### Post by ubunturules on 2007-10-27
Awesome I am glad you got it to work.  the reason I put both methods of installing ndiswrapper is because some people said they had trouble getting it to work with the one in synaptic.

ubunturules

---

### Post by puppe on 2007-10-28
I tried to set up wireless by following your thread
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)
and result is that, when activating wireless (pressing the button) everything freezes for extended periods of time when trying to do anything (moving the mouse, keyword etc).

Don't know what went wrong
ndiswrapper -l gives:

    bcmwl564 : driver installed
    device (14E4:4320) present (alternate driver: bcm43xx)

which is not really what was written in the tutorial/thread but otherwise I don't know.

Any help or suggestions very appreciated.



The whole post with trying to get my wireless working are at:
[http://ubuntuforums.org/showthread.php?t=593649](http://ubuntuforums.org/showthread.php?t=593649)

thanks for any help

---

### Post by goslings on 2007-10-28
hi
really new to ubuntu
all work "out of the box" (uname -r 2.6.22-14 ) with network cable - wow 
but not so with broadcom corp BCM4306, hence the search 
I see this original post was dated 2006. 
does this all still apply to the latest downloads of ubuntu ?
Is it not corrected to pick up this hardware one year on ?
(It did detect my SGI 1600SW flat panel 1600x1048 @60 hz, unlike pclinuxos)
1st poster
goslings

---

### Post by ubunturules on 2007-10-28
This guide is update to date.  You can use this guide with Dapper, Edgy, Feisty, or Gutsy.

ubunturules

---

### Post by goslings on 2007-10-28
Is this also the case if i am using liveCD version 
can I then create a live USB version on my 2GB USB stick ?
thanks
Ian

---

### Post by ubunturules on 2007-10-30
I really don't know about that.  I think there are guides somewhere on the forums that might be able to help you with that.

ubunturules

---

### Post by f37u5g0d on 2007-10-30
So I tried to run your program and it worked (sorta).  I can use the card but it can't find any wireless networks.  But that's not the problem I'm concerned with right now.  Now when I boot my computer to ubuntu it loads the login screen and then immediately goes to a blank screen.  As if the screensaver has been running for 20 minutes and it has shut off the display.  Also the little boot loader thingy (IDK what it's really called) is gone.  The little transparent window that appears after you log in.  It shows three icons a gnome foot, a nautilus window and a third one I can't remember.  How can I get it back?  Does it have to do with sessions?  I admittedly messed with them a little bit but it didn't seem to have any effect.

---

### Post by doggscube on 2007-10-30
I'm new to ubuntu, dabbled briefly years ago in FC4 but quit due to this Broadcom chipset.  I may have a unique situation.  I have followed the tutorial with no error messages, but wlan0 doesn't show up.

ndiswrapper -l yields:
bcmwl5: driver installed
device (14E4:4320) present (alternate driver: bcm43xx)

What is unusual with my machine is that the wireless power button (physical) doesn't work all the time, and the light doesn't turn on.  Windows turns the card on automatically, so it hasn't been an issue.  

Would wlan0 show up in the network connections if the card is turned off?
Is there a way to have Ubuntu turn the card on automatically?

Edited again, the card is not showing up as wlan0 when I run lshw -C network.  I've tried 3 versions of the driver.

Thanks,
Jeff

---

### Post by tashmooclam on 2007-11-02
I have already downloaded the firmware and bcm43xx-fwcutter. I also have switched from network manager to another little app called "Wicd". 
I have the 4306 broadcom card, Dell D600. 
Is it too late for me to try out Ndiswrapper? I'm happy to give it a try. Will I be causing some damage? 
I looked at a wireless internet meter and the best speed I saw was 345kbs. 
Of course, it goes down to almost 0 and back to 13kbs, so it's not really working.

---

### Post by ubunturules on 2007-11-02
No it's not to late to use ndiswrapper.  Uninstall all of the bcm43xx stuff you downloaded and then go through the guide.  If it doesn't work you can always reinstall the bcm43xx stuff.

ubunturules

---

### Post by tashmooclam on 2007-11-02
Thanks, I may give that a try.
Off the subject, but I saw an Intel wireless card for this laptop for $49, and installation is a simple matter, just a little door on the back of the laptop. 
Sometimes I think many hours of my time searching and googling may be worth $49, if this makes the equipment work better.

---

### Post by tashmooclam on 2007-11-02
Ebay sells an Intel wireless card for $24 for my dell D600. 
Spam post apologies.

---

### Post by tashmooclam on 2007-11-03
I used synaptic package manager and removed "bcm43xx-fcutter".
I then followed the instructions at the beginning of this thread to install Ndiswrapper.
I made it to about step 10, 

kim@kim-laptop:~/ndiswrapper/ndiswrapper-1.48$ sudo make installsudo apt-get install ndiswrapper-utils-1.9
make: *** No rule to make target `installsudo'.  Stop.
kim@kim-laptop:~/ndiswrapper/ndiswrapper-1.48$ 
kim@kim-laptop:~/ndiswrapper/ndiswrapper-1.48$ sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf
sudo: ndiswrapper: command not found
kim@kim-laptop:~/ndiswrapper/ndiswrapper-1.48$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
kim@kim-laptop:~/ndiswrapper/ndiswrapper-1.48$ 
kim@kim-laptop:~/ndiswrapper/ndiswrapper-1.48$ 

I made a folder and put the ndiswrappertargz in it my home folder.
Any suggestions are welcome.

---

### Post by ubunturules on 2007-11-03
You put both commands in there at once

try
```
sudo make install
```

```
sudo apt-get install ndiswrapper-utils-1.9
```

ubunturules

---

### Post by ubunturules on 2007-11-12
did that work tashmooclam?

ubunturules

---

### Post by tibby_ on 2007-11-12
so it says to download the ndiswrapper but how am i supposed to download it if i am trying to set up my wireless ???

---

### Post by ubunturules on 2007-11-13
you can get the ndiswrapper-utils package off the Ubuntu CD.

ubunturules

---

### Post by cdorogoff on 2007-11-15
I am using a dell inspiron 5100 laptop

I just followed your guide almost perfectly on my part i think
however when i installed the bcmwl5 driver it said that is was already installed and wen did the command "ndiswrapper -l" i got the bcmwl5 : invalid driver, and i tried the 64 bit drivers and got the same result
also it says "inf: invalid driver"

Im not sure what happened because i am sure that i am using a broadcom 4306 chipset

Could someone help me please?

---

### Post by ubunturules on 2007-11-22
alright lets see what we can do.

```
sudo ndiswrapper -e bcmwl5
```
that should remove the driver now try the 64 bit driver again.

you might of forgot to uninstall the 32 bit driver before you tried the 64 bit driver

ubunturules

---

### Post by jludeman on 2007-11-23
I tried this and it worked great in Ubuntu. I've now installed Xubuntu and run fluxbox on it. I get no connection even though I'm using nm-applet.

sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

sudo ndiswrapper -m
module configuration already contains alias directive

Any ideas?

---

### Post by jludeman on 2007-11-23
Never mind. It did not come up on reboot. After a complete shutdown it did.

---

### Post by shawnerz on 2007-11-24
All,
This did not work for me.
I am running Gutsy on a Gateway MX6421 laptop with a Broadcom 4318.  I originally attempted to get wireless working on Fiesty.  It didn't work.  Wireless wasn't a pressing need, so I waited until Gutsy was released.  It still doesn't work.

My wired port works without any problems.

My access point is running 802.11 b/g with WPA2-PSK.  My ESSID is not broadcasted (is that a word?).  I use static IP addresses.

ifconfig:
eth0   Link encap:Ethernet HWaddr [MAC Address]
          inet addr:192.168.15.13  Bcast:192.168.15.255  Mask:
          255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

iwconfig:
eth0  IEEE 802.11g  ESSID: off/any
         Mode:Managed   Frequency:2.462 GHz  Access Point: Not-Associated


My laptop is dual boot and wireless works in Windows.

WiFi Radar sees the access point.  Wifi Radar says "Connected to None (IP Adress: 192.168.15.13)"

Firestarter is installed but disabled.

If I enable *both* the wired and wireless connection at the same time, Firefox cannot connect to the Internet.  The wireless interface has to be disabled in order to get a network connection on the wired port.

The Connection Properties for eth0:    [wireless port]
Status: Disconnected

The Signal Strength is at 0%.

I've rebooted (once) and powered down and powered up (once).
Still doesn't work.

Any ideas?
-Shawn

---

### Post by dshowell on 2007-12-02
WOW!! I have spent numerous hours and I have tried numerous howtos, probably over 10, to try to get my wireless working. None of them worked. I tried yours and it worked with no problems. I did one thing a little different though. I have a Dell Truemoble 1300 wireless card in my laptop. The drivers off the  Dell disk are bcmwl5.inf and bcmwl5.sys. I read a few posts on various sites and came across a post that stated that Winspire has specific drivers for the bcm94306 chipset. I ran a live version of Linspire (the free version of winspire) and copied the bcmwl5-94306 drivers to a thumbdrive. I used those drivers with your instructions and everything is working great. Once again thanks for a great post. If anyone wants those drivers let me know. I'll e-mail them to you.

---

### Post by gobbomaster on 2007-12-08
I really would like to thank you, close to throwing my laptop out of the window I found your guide and it is the first one that helped me perfectly! I'm not sure if I was the only one, but in step 16 I had to add sudo for it to work.. Again, thank you!

---

### Post by ubunturules on 2007-12-17
I'm glad I could help you out.  I like hearing success stories.

ubunturules

---

### Post by TerpEE93 on 2007-12-19
I've tried this process several times and have had no luck.  I've got a Gateway 3018 with the 4306 wireless card.  I've tried running through this process without ever loading the restricted driver, loading it first then running this process, using ndiswrapper-1.48, using ndiswrapper-1.51, etc.  I have my interface name set to wlan0 in /etc/modprobe.d/ndiswrapper and /etc/udev/rules.d/70-persistent-net.rules   There is no wlan0 (or eth1) entry in /etc/network/interfaces

Sometimes the little wireless light on my laptop comes on, sometimes not.  In any case, when I run iwconfig I see:

lo        no wireless extensions
eth0    no wireless extensions


There is no entry for wlan0.  Help!  What am I doing wrong?

---

### Post by guybers on 2007-12-20
I recently installed Ubuntu on my old e-machines M5312 and I have been extremely frustrated with trying to get my wireless card to give me a fast connection with fwcutter.  THIS WORKED LIKE A CHARM!  Anyone out there like me with an old crappy e-machines lappy, this is the way to get your wireless on.  I officially no longer hate linux, I just wish I could get the three days I spent working on it back. Thank you so much for the guide!

---

### Post by chanhdat on 2007-12-22
Sorry, SOLVED!
I am using a Dell Inspiron 9100 with Broadcom 4309: I followed this guide. And now stuck at step 24. 
Look what I got :
[IMG]http://bookofme.googlepages.com/Screenshot-1.png[/IMG]
I tried to ignore it. And then reboot.
A pop up welcomes me:
[IMG]http://bookofme.googlepages.com/Screenshot.jpg[/IMG]
Any ideas? I swear I will use all time of this Christmas holiday to make Wifi work. HIx. Help!
I can see my wireless card, Roaming mode is enable. But nothing come out. I try to disable Roaming mode, and manual configure. After filling all the blank spaces (except Gateway address ) , the result: failed. 
Another time: after adding the new connection, I wait and then see the bar graph. Thank God! But after several minutes, it won't go on ( Stuck at 0%) . Then ask me password continuously. :confused:
I want to do like this: [http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")
But I don't have a cable to connect to my modem.
I intend to do like this:[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")[this way.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")
[SIZE="7"]Help[/SIZE]

---

### Post by NoVista on 2007-12-28
I just stopped in to say thanks for a great tutorial.
It worked like a charm.

This was on a Dell Latitude D600.

---

### Post by White_Panther on 2007-12-31
thanks this worked like a charm, the only thing I had to change was the driver version from bcmwl5 to bcmwl5a, I have a dell dimension e520

---

### Post by Yellowdog428 on 2008-01-01
I am having a problem,

When I enter 
```
ndiswrapper -l
```

I get
```

bcmwl5 : invalid driver!
bcmwl5a : invalid driver!
```

any help would be great!
Cheers

---

### Post by Yellowdog428 on 2008-01-01
Sorry for the double post.

I did a clean install and now my wireless card wont turn on.  I followed the directions to a T.  Everything seemed to install just fine, but I got nothing.

When You say I need to make sure the .sys file is there am I supposed to move it to a specific directory?

Does ndiswrapper install he firmware?

I am compleatly at a loss.  

BTW I am running on a Presario 2200 if that matters with the 4306 chip.

Thanks in advance

---

### Post by ubunturules on 2008-01-02
hello,
the .sys file just needs to be with the .inf file when you run the ndiswapper -i command.  what does ndiswrapper -l give you now?

ubunturules

---

### Post by Yellowdog428 on 2008-01-02
```
bcmwl5 : driver installed 
     device (14E4:4320) present (alternate driver: bcm43xx)
```

The card wont turn on at all.  I booted into widows to make sure the card still worked (and it does) so Its not a hardware problem.

Thanks for your help
Cheers

---

### Post by Yellowdog428 on 2008-01-03
So I tried to install the bcmwl5a driver but now are both installed.  The card still does not work but both drivers are there when I enter ndiswrapper -l.

How do I remover the old driver to see if the new one works?

Anyone know where  I can find some other drivers that may work?

Thanks again guys and gals!

Cheers

---

### Post by gimmy_bond on 2008-01-03
> **ubunturules said:**
> did this HOWTO help anyone?

thanks. however It would be further helpful for us the "windows refugees'  to see these instructions, using the GNOME and Synoptics to accomplish the same.

---

### Post by fireant on 2008-01-04
> **Yellowdog428 said:**
> So I tried to install the bcmwl5a driver but now are both installed.  The card still does not work but both drivers are there when I enter ndiswrapper -l.

How do I remover the old driver to see if the new one works?

Anyone know where  I can find some other drivers that may work?

Thanks again guys and gals!

Cheers

To remove the drivers type:

sudo ndiswrapper -l <-- this will show you the drivers installed, eg bcmwl5

sudo ndiswrapper -e bcmwl5 <-- this will uninstall the driver, repeat for each driver listed under -l.

You will need to reboot for the changes to take effect:

sudo shutdown -r now


As for the card not appearing, it's a driver issue. 

There are loads of different BCM4306 card drivers from different manufacturers. Some work, some don't. 

You'll also find that some will work and be slow, whereas others will work and be fast. I tested mine on an FTP transfer and am getting over 1mb/s with Filezilla.

I used the bcm43xx drivers attached, but I have downloaded loads more from the likes of dell, linksys etc. I'm afraid it's just trial and error.

Another thing to check if you're on Gutsy is that if you have a mini pci card it may be named something like eth1, not wlan0, mine was anyway. This howto binds ndiswrapper to wlan0.

You therefore need to change this file: 

sudo gedit /etc/udev/rules.d/70-persistent-net.rules

Look for the entry for your bcm43xx device and change the NAME at the end to wlan0, example below.

# PCI device 0x14e4:0x4320 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:03:c9:70:7b:a9", NAME="wlan0"

---

### Post by Yellowdog428 on 2008-01-06
Well still no dice.

Tried a few more drivers bit after further investigation I found that my 70-persistent-net.rules file is blank.......

Is there another way of finding oyt where ndiswrapper is looking for my wireless card?

Also this tutorial sais nothing about restricted drivers being used, so I haven't enabled any...   Will that make a difference?  I know alone the restricted drivers don't work all that well, I need to be right on top of my router for it to work.  Also my card seems to turn on and off when it is using the restricted drivers.,.....   

Maybe time for another approach...

Thanks again for all your help!

Cheers

---

### Post by NoVista on 2008-01-06
Yellow, just for your reference, I had the FIRMWARE enabled under Restricted Drivers Manager, and had them enabled before I did anything mentioned on this How-To.

---

### Post by Yellowdog428 on 2008-01-07
> **fireant said:**
> To remove the drivers type:

sudo ndiswrapper -l <-- this will show you the drivers installed, eg bcmwl5

sudo ndiswrapper -e bcmwl5 <-- this will uninstall the driver, repeat for each driver listed under -l.

You will need to reboot for the changes to take effect:

sudo shutdown -r now


As for the card not appearing, it's a driver issue. 

There are loads of different BCM4306 card drivers from different manufacturers. Some work, some don't. 

You'll also find that some will work and be slow, whereas others will work and be fast. I tested mine on an FTP transfer and am getting over 1mb/s with Filezilla.

I used the bcm43xx drivers attached, but I have downloaded loads more from the likes of dell, linksys etc. I'm afraid it's just trial and error.

Another thing to check if you're on Gutsy is that if you have a mini pci card it may be named something like eth1, not wlan0, mine was anyway. This howto binds ndiswrapper to wlan0.

You therefore need to change this file: 

sudo gedit /etc/udev/rules.d/70-persistent-net.rules

Look for the entry for your bcm43xx device and change the NAME at the end to wlan0, example below.

# PCI device 0x14e4:0x4320 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:03:c9:70:7b:a9", NAME="wlan0"

Fantastic advice my friend!  

Works like a charm now.

I had to enable the restricted driver and installed your attached bcm43xx driver and installed with ndiswrapper.

Also after enabling the restricted driver my 70-persistent-net.rules file was labeling the pci device eth0.

Thanks again guys for all your great help!

Cheers

---

### Post by jeepinpete on 2008-01-07
fireant, I just wanted to thank you.  Your post (#746) was the final piece of the puzzle for me.  Now my wifi is working great!

Pete

---

### Post by ubunturules on 2008-01-08
how do i link to a specific post?
Quentin

---

### Post by khanoftartary on 2008-01-09
THANK YOU!!!!! I've been trying to get my wireless card working for weeks now, and I'm so glad that I found this. One run through, no errors, runs clean as a whistle. Who da man? You da man!

---

### Post by push_harder on 2008-01-18
Didn't work for me, when i entered the "ndiswrapper -l" command, all i got was "invalid driver for both bcmwl5 and bcmwl

I'll try again, i might have missed something.

Cheers for the nice tut though :)

---

### Post by ubunturules on 2008-01-18
push_harder: look at post 746 on page 75 that has been helping people.

ubunturules

---

### Post by Aesthetic on 2008-01-19
Finally got it working! I'm new to linux in general, but it was a lot of fun setting this one up. Drove me crazy a couple of times but wifi is up and running and i'm typing this on my project-laptop.

Thanks a lot for this guide!

I used the 64-bit drivers, had to use the fix for problem 1 and had to fiddle around with wpa-encryption, I used

echo 'ENABLED=0' | sudo tee - a /etc/default/wpasupplicant

did a reboot and filled in the wpa password and all that when the gnome network manager prompted me to do so and it connected. Did a reboot and here I am! Thanks again!

---

### Post by ubunturules on 2008-01-19
no problem man I'm glad you got it working.

ubunturules

---

### Post by Baloofalo on 2008-02-01
Be patient with me, your tutorial has me closer than I have ever been to getting this working.

I am trying to get a linksys wmp54gs working. I followed your tutorials but it will still not let me connect to either of my wireless routers. While only one of the routers has a passphrase, when i click on one of them they both ask for security.

I actually had the icon change to bars in the upper left hand corner right after going through the turorial, but it would not let me connect to any sites. I rebooted and I can still se the servers (as well as several of my neighbors, but still can not connect.

The only "odd" thing I think I am seeing is;

-l
bcmwl5 : driver installed
wmp54gs : driver installed
                device (14E4:4318) present (alternative driver: bcm43xx

Anyone have suggestions? Every step in the tutorial went without a hitch until I tried to login.

---

### Post by coggz on 2008-02-04
I am stuck, I have tried this guide and another one. I have done everything* exactly*, and yet I still have problems. I use a Dell Inspiron 1300, with Kubuntu 7.10. 

When I type ndiswrapper -l, i get this:
```
luke@luke-laptop:~/ndiswrapper/ndiswrapper-1.48$ ndiswrapper -l
bcmwl5 : invalid driver!
bcmwl5a : invalid driver!
```

i have tried both bcmwl5 and bcmwl5a, though neither work!!
Please help me, as i am totally clueless
Luke

---

### Post by starsheeep on 2008-02-06
Thank you, worked on my acer f3000, with feisty and gutsy

---

### Post by Ahslan on 2008-02-12
...my 70-persistent-net.rules file is empty and I dont know how to get this dumb wireless to work...someone said you had to enable the restricted driver and install the attached bcm43xx driver and install with ndiswrapper...how do u do that???

---

### Post by Ahslan on 2008-02-13
ugh...screw this...time to go back to xp...*sigh*...

---

### Post by rsidle on 2008-02-16
Also works for Broadcom 4309 (dell truemobile) if you have bcmwl5a.inf. For me this was on the CD that came with the wireless card. Excellent guide for general NDISWRAPPER usage! Thank you.

---

### Post by swiftfoottim on 2008-02-19
How do you enable the firmware?  I go to enable it in the restricted drivers but it will not enable.

---

### Post by swiftfoottim on 2008-02-19
Well, I have reinstalled ubuntu, then I went in and enabled the firmware.  I have tried the bcmwl5, bcmwl5a and the 43xx drivers, all show the same invalid driver.

Now I'm getting this error when I try to install a driver and it could be why I'm getting the invalid driver.

installing bcmwl5(whatever version)...
couldn't open /home/jared/desktop/bcmwl5/bcmwl5(whatever version).inf: No such file or directory at /usr/sbin/ndiswrapper - 1.9 line 181

Any ideas?  Getting crazy frustrated right now.  Dang, this is tough.

---

### Post by ubunturules on 2008-02-20
make sure you have the ".inf" at the end ofo the file.

ubunturules

---

### Post by swiftfoottim on 2008-02-20
Yeah, I've typed the .inf after it.  Ohh well, starting with a fresh install tonight...

---

### Post by ubunturules on 2008-02-27
yeah fresh installs usually fix problems.

ubunturules

---

### Post by swwjpx3 on 2008-03-01
sorry if this is already posted on one of the many pages. After doing everything in the tutorial my computer was able to find the wireless network card in my Inspiron 1150 and see the networks in the area.  However to connect to wireless connections, I had to use Synaptic Package Manager and downloaded _wifi-radar_.  now I can connect to any wireless connection that I have found so far through the WiFi Radar app.  Hope this helps

---

### Post by ubunturules on 2008-03-03
yes I have heard of that working for some people.  i might have to include that in the howto. thanks

ubunturules

---

### Post by ScarySquirrel on 2008-03-04
The sight of this thread gave me hope. Alas, I hoped in vain.  I've already tried several "howtos" on other computers, and I have yet to get one single broadcom wireless card working.  
      I've tried the Howtos.  I've tried ndiswrapper.  I've tried fwcutter.  I've tried reinstalling the OS and doing it all over in reverse order while holding a four leaf clover.
       My friends and family have described me as rather computer-literate, but this just seems beyond my ken.
       I plead for help.  I made a log of all the actions that I took to install the wireless drivers, in Step by Step format, describing all the commands I entered, actions I took, and output I received.  If anyone thinks they can help me and wants to, let them pm me.
P. S. Score one for Windows.  
I'm booting from an External Hard Disk, and Windows doesn't support that.  That's why I decided to switch to linux, so that I could.  However, it seems like I'll need to look into some way I can boot windows from my external HDD, since from the looks of it that will be easier than trying to get some infernal wireless driver to function.

P. P. S. Here's some selected from the lspci command on my computer, as well as some general system information:
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
Memory:  1010.4 MB
Processor: AMD Athlon(tm) 64 Processor 3500+

P. P. P. S. Ahslan's Post seems to describe my mood right now.

---

### Post by Aetheric on 2008-03-10
A thousand internets to you, good sir - this HowTo finally got my crappy Broadcom 4303 adapter going after two weeks of pain!

To ScarySquirrel - I found that none of the HowTos worked for me as well, no matter what I did - then I tried the 64bit drivers here and it all clicked together perfectly.

For anyone else who might have the same laptop as me:

Compaq Presario R3000
Athlon 64 3000+
Xubuntu 7.10 2.6.22-14-generic
Broadcom 4303 wireless

I just followed the HowTo exactly and used the 64bit drivers and it was grand.

Once again thanks to the OP, you're a life saver. :KS

---

### Post by ubunturules on 2008-03-17
excellent...im glad you got it to work.

ubunturules

---

### Post by ubunturules on 2008-03-30
once hardy comes out I will update the guide to fully work with it.

ubunturules

---

### Post by LinkInGuy on 2008-03-31
I tried this and I don't see Wireless connection in Network setting anymore :(
could that be due to driver mismatch?

---

### Post by ubunturules on 2008-03-31
i heard that post #746 on page 75 works with this problem.

ubunturules

---

### Post by koalix on 2008-04-03
Many thanks *ubunturules* for your tutorial. 
After several weeks of living in dispair, thanks to your tutorial I have seen the light.

:)

For other users with the same problem, this is my configuration:

Laptop: compaq nx9010
Wireless card: Broadcom 4303 (rev 02)

The trick was to use the bcmwl5a.inf driver instead of the usual bcmwl5.inf, and then apply the steps given at post #746

Thanks again *ubunturules*, Thanks to you your nickname is worthy again!

---

### Post by ubunturules on 2008-04-03
does anyone know how I can put a link directly to the post on page 75 on the guide.

ubunturules

---

### Post by Lazy-buntu on 2008-04-10
Currently I dual boot Windows Vista and Ubuntu 7.10 (Gutsy), but I'm running into a problem with my wireless.

I'm going to look through the wireless forum to see if I can find an answer to my problem, but here's my problem:

I used ndiswrapper to install my wireless driver (broadcom chip =/ ) and the good news is I can see wireless networks when I do iwlist eth1 scan.

There's a problem though: I can see the networks, but I cannot connect to them. My network has a WEP key (hex) and a broadcasted ESSID. So, in my network tools I set my ESSID, put my WEP key in, and set my IP to DCHP.

I heard ipv6 can cause problems according to the built in help topics in ubuntu--it tells you to gedit /etc/modprobe.d/aliases and change ....... pf 10 ipv6    to      ........ pf 10 off--I did this and rebooted, no go. (I did change it back since then.)

Any ideas? (BTW: I can't get a wired connection, so I haven't been able to do any  updates)

---

### Post by BradBrening on 2008-04-15
Although my card is based on the 4303 series, this guide did the trick!  Thanks ubunturules!

---

### Post by yahooshua on 2008-04-20
Worked for me. Thank you very much.
Compaq presario m2000
Gutsy Gibbon

Had a few hick-ups due to the url being changed for the ndiswrapper and having tried to figure out myself. Basically this helped.

---

### Post by promise239 on 2008-04-24
Add me to the list of lucky souls who has made this work...   I have the gateway 7426GX laptop with the Broadcom 4306 chipset (rev 03. 14e4:4320)... although the drivers that were attached in the forum were not working for me, all the information you gave with installing ndiswrapper and the other utilies has truly been a blessing.  I finally got this to work with ndiswrapper and the winxp drivers from my manufacturer's website...

also, i must extend some extra thanks explicitly to Ubuntorules!  

I'm such a happy linux newbie! LOL

---

### Post by radiophage on 2008-04-25
Trying to follow the instructions here, and tripping up when building ndiswrapper.  Here's the error I get re CFLAGS.  If you follow this post like I did, be sure to use the newer ndiswrapper for Hardy.

> make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/alan/ndiswrapper/ndiswrapper-1.48/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/alan/ndiswrapper/ndiswrapper-1.48/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/alan/ndiswrapper/ndiswrapper-1.48/driver'
make: *** [all] Error 2

Things were fine until that point.  

>>>solution:  use ndiswrapper ver 1.52 and all is well.<<<

(Running a fresh Hardy installation here with a BC 4306 card.)

Thanks

---

### Post by jc7 on 2008-04-29
Good tutorial. I ran into difficulty with my NX9010 due to the firmware. The trouble was with the firmware. I discovered this by looking through dmesg. The errors directed me to [http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy](http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy). I followed the instructions and was up and running in no time.

---

### Post by enchantedsky on 2008-05-05
Hey Ubunturules, I'm having the exact same problem as you. My Broadcom 4306 does *not* work with Hardy Heron. It detects the network card, it shows the manager on the upper right part of the screen, but it won't let me connect to any public networks :(

Edit: I got my wireless working by installing the Broadcom wireless support via Synaptic Package Manager!

---

### Post by Cybergod on 2008-05-06
> **enchantedsky said:**
> Hey Ubunturules, I'm having the exact same problem as you. My Broadcom 4306 does *not* work with Hardy Heron. It detects the network card, it shows the manager on the upper right part of the screen, but it won't let me connect to any public networks :(

Edit: I got my wireless working by installing the Broadcom wireless support via Synaptic Package Manager!

It will work if you follow Ubunturules's guide and [this]("http://ubuntuforums.org/showthread.php?t=734003") guide.  I can confirm this because I have a Broadcom 4306 and it works perfectly with ndiswrapper.

---

### Post by sapack on 2008-05-10
Add me to the list that is working now with a Broadcom 4306 and Hardy Heron.  Thanks for the fix Ubunturules.

I did do the uninstall in post 746.  That may have helped.  Didn't hurt.
Typing this from wireless now.

Broadcom sucks, but Ubunturules!!!!

---

### Post by ubunturules on 2008-05-19
glad to here someone got it to work on hardy with the guide.

---

### Post by FredKratt on 2008-05-20
I am trying to run Ubuntu 8.04 on my Pressario R3000.

This procedure did not work. I am still dead in the water.

The wireless will not turn on. I was able to get it to work with 7.04 but then I lost the panels and had to rebuild the system. So I tried rebuilding with the "latest".

Any suggestions before I reinstall again? I have the driver disks that came with the computer, would that help? 

I was hoping Linux would be better than Microsoft.

---

### Post by FredKratt on 2008-05-20
I am trying to get wireless working with 8.04. How exactly did you do it?

---

### Post by carls on 2008-05-22
> **ubunturules said:**
> This is the easiest way to get your Broadcom 4306 wireless card working in the shortest amount of time.  ...

**EDIT: This guide now works with every Ubuntu distro from Dapper to Hardy!**

Do everything in the order as it is listed.

I'm stumped at step #5:

***snip***
5. You will need the Ubuntu 7.10 CD to get these packages.
***end snip

Since I have Hardy only, should I download the 7.10 disk for this step?

TIA

Carls

Boy is this ever embarrassing - but not to ask has proven too time-consuming over the past month...

---

### Post by maraja on 2008-05-24
it was superuseful to me using a linksys wmp54gs on an old dell 700.
after having installed ubuntu 8.04 I lost my wireless connection, thanks to this post I was able to make it work again: THANK YOU SO MUCH!
:popcorn:

---

### Post by ubunturules on 2008-05-27
> **carls said:**
> I'm stumped at step #5:

***snip***
5. You will need the Ubuntu 7.10 CD to get these packages.
***end snip

Since I have Hardy only, should I download the 7.10 disk for this step?

TIA

Carls

Boy is this ever embarrassing - but not to ask has proven too time-consuming over the past month...

No, you don't need to get the 7.10 disk for this step.  You can use your hardy disk.

ubunturules

---

### Post by fisho on 2008-05-29
Hi all i have this working with the 4306 rev 2 this is the first time i have been able to get the wireless to work on the inspiron 8500 i have used fedora 7, 8, 9 so i decided to try another linux package, but i do have one issue i wont connect when encryption is on to my netgear dg834gt,

any tips for trouble shooting working this part out or the connection...

i am very happy so far with ubuntu.

---

### Post by ubunturules on 2008-05-31
what happens when you try to connect to the network when it is encrypted?

ubunturules

---

### Post by fisho on 2008-05-31
just keeps trying then gives up after a few minutes i have had it connect but no ip address then disconnects it's ok if security is off connects surf web all ok.

connects to a wireless network by defaulf in my street who has no security.i know it's not good to connect to there's but it will when it gives up on mine with security on.


i have tried changing channels on my router, static ip hide unhide ssid no go with security on.

---

### Post by wrknight on 2008-06-09
Running feisty and later gutsy, I had no problems with my Broadcom 4306 wireless card.  Unfortunately I updated to Hardy and everything fell apart.  There is no longer an "interface properties" gui in the network settings panel and there is no "enable" box to check.  Also, when I execute the command lshw -C network, it shows two wireless interfaces with different entries in each.  the latter one says "*-network DISABLED".

Anyone have any ideas on how to deconflict the wireless settings and enable the Broadcom 4306 under Hardy (kernel version 2.6.24.18)?

---

### Post by Nushizu on 2008-06-18
I followed all the steps I'm using the newest version of Ubuntu so I think I'm not getting quite abit of this...also very new to linux =\ drop me a line if you can. [email]metal.rocker89@Gmail.com[/email]

---

### Post by fisho on 2008-06-19
if other don't work try this 

[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/](http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/)

---

### Post by archeco on 2008-07-01
Hi everybody, I sure am glad that Ubuntu has this great community for mutual help!
I have just come to Ubuntu via Windows, Mac )SX, and Lindows/Linspire.  I have been trying to get my Belkin wireless card to work.  After using the synaptic package manager 
I got two green lights and the icon lets me select  my wireless network but the connection never goes through and the system reverts to wired network.
I have (twice) tried to follow the steps in this excellent post but I am stumped at step 13.  Here is what I get when I input the location of my  bcmwl5 folder:

johannes@johannes-laptop:~$ sudo ndiswrapper -i ~/home/johannes/Desktop/bcmwl5.inf
[sudo] password for johannes: 
couldn't open /home/johannes/home/johannes/Desktop/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

Sorry for my lack of skills - I've been trying hard to learn but  I do need help badly.

---

### Post by ubunturules on 2008-07-01
make sure that the bcmwl5.sys file is on the Desktop also.

ubunturules

---

### Post by archeco on 2008-07-02
> **ubunturules said:**
> make sure that the bcmwl5.sys file is on the Desktop also.

ubunturules

thanks ubunturules!
I did have that .sys file in the folder but perhaps I miscoded by listing the .inf file directly after the /Desktop directory name  without including the name of the folder before the .inf file name?
At any rate, I experimented with removing address filtering from my router and was able to use the wireless  card.  It seems unsteady though because when i switched the address filtering on, then off, then on again,I was able to retain the wireless internet access.  Perhaps I need to switch filtering off in order for my system to get on and then switch filtering on again (to maintain security) or could I code so that my system gets past the MAC filtering on my Belkin router?

Thank you so much for your prompt help - I am so happy to be able to get out of the clutches of that tyrant Microsoft!

---

### Post by jlipoth on 2008-07-12
I followed the instructions and now my computer freezes on bootup with the most recent kernel...   ...I really need some help!

update:
I found the problem - I made a mistake on step 8......  .... so I ended up reinstalling ubuntu.... ....totally my lack of attention....

---

### Post by mastahtao on 2008-07-12
In step 2 I get my first error telling me the module doesn't exist in /proc/modules. Fairly new to linux so I don't know if this is an issue but I don't get an output from step 8. I have no internet at all because both my ethernet and wireless are down after install Hardy on my Compaq r4000 so I downloaded ndiswrapper onto a flash and placed it in my ndiswrapper folder in my user folder. Then while following step 11 at "sudo make" I get a bunch of errors and warnings, almost all the same ones that I get if I try going on and doing "sudo make install" 

After that I tried step 12 both options and I get E: Couldn't find package ndiswrapper-utils-1.9. If i try to move on to step 13 I get  "sudo: ndiswrapper: command not found".

No idea what I'm doing wrong here I just don't have any experience with linux and would really appreciate any help you can give. Oh and yes I have checked to make sure I have a 4306.

---

### Post by ubunturules on 2008-07-13
Alright lets see what we can do.  The error you get from step 2 is ok.  You're not supposed to get any output from step 8.  You need to have the Ubuntu CD in the computer when you run step 12 and that's probably why you get the error.  Try all this and let me know if any of it helps.

ubunturules

---

### Post by jlipoth on 2008-07-14
This truly the is best tutorial on ndiswrapper!  I got the wireless working on my compaq r4025 laptop with drivers from the compaq website (the ones linked off the tutorial didn't work).  No more 1 mbps!  I still have one problem though - I can't get WPA so I've reverted back to WEP.  Does anyone have suggestions on getting WPA to work?

---

### Post by mastahtao on 2008-07-14
Sorry I should've mentioned that I do have the cd in while trying to do those steps. It is a burned cd however and for some reason while in a linux machine it can't auto run while in an xp machine it can. Should I burn another copy and see if that does any better? Thanks for the help in advance.

---

### Post by cuisphunt on 2008-07-17
If I have the ubuntu 7.04 disc am I going to run into problems. I have a compaq presario r3000, loaded 7.04 and upgraded to 8.04 immediately having previously read some of these threads in hopes that Hardy would be easier to get broadcam up and running.  This thread seems to show that ubunturules has nailed it but I want to make sure I don't mess something up that I can't fix. First timer with Linux after many years of disgruntled windows use.  My current situation is I find the broadcam driver but I cannot enable it.  It says restart required but nothing more happens on restart.  I got to step asking for cd, just want to make sure that this version is okay.  Thanks for any response!!

---

### Post by ubunturules on 2008-07-30
You might want to get an the 8.04 CD.  The packages you need might not be on the 7.10 CD.

ubunturules

---

### Post by RegLinUsr on 2008-08-03
I can not get past the 'build-essentials' step. After running the command 'sudo aptitude install build-essential' I receive the error 'Couldn't find any package whose name or description matched "build-essential" and it finishes with 'No packages will be installed, upgraded, or removed.' I have my CD in the drive but I do not believe that it is being accessed. The CD is listed as one of the sources in the Adept Installer. 

I can connect to the internet via my Mac but not with the Kubuntu PC at the moment w/o wireless. Thanks for any help submitted.

Kubuntu 8.04

---

### Post by williambertram on 2008-08-05
Yes!!  FINA-FREAKING-LY!!!!

THANKS!!

---

### Post by legarconblanc on 2008-08-06
I think I actually love you. Thanks. Can't believe that's the only guide that works.:guitar:

---

### Post by cuisphunt on 2008-08-18
To Ubunturules!! Thanks, the procedure worked, although I did have a couple of variations on your procedure.  The ndiswrapper 1.52 that I downloaded would not unzip.  Not sure if that was me and my newbieness with linux or the file was bad.  I kept getting a "not a zipped file" error.  Tried renaming and reloading all to no avail. I then downloaded ndiswrapper 1.53 and it installed fine.  From that point I was able to move out of the basement and into a living world again.  Thanks Ubunturules!

---

### Post by ShaxxiE on 2008-08-19
Hi

This didn't work for me - I can see my wireless connection however i cannot connect to it.  It says "Waiting for the network key for the wireless network" when i put my cursor over the WLAN sign in the top right hand corner of my screen and then after it times out, it goes back to the wired connection.

I have the Linksys WMP54G Card with the Broadcom 4306 chipset.

I have a thread going on at [http://ubuntuforums.org/showthread.php?t=893491&page=3]("http://ubuntuforums.org/showthread.php?t=893491&page=3"), would appreciate it LOADSS f you can take a look.....

thanks

Shaheen

---

### Post by lightenup on 2008-08-24
This guide worked perfectly on my HP NC6000 with Hardy 8.04 and the following internal card:

lspci output:

02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Speed and stability is much improved! Thanks!

---

### Post by ubunturules on 2008-09-01
glad it worked for you.

ubunturules

---

### Post by picto on 2008-09-05
after a few days toiling away with various other network adapters and guides, i finally fell on this one and amazingly it works. Nice one man.

edit.

using belkin F5D7001 UK version on 8.04. i failed to get my netgear WG111v3 and and wpn111 to work so if anyone can shine any light on these i would appreciate it as the belkin is old and i only get a 10% network strength.

---

### Post by FiremanEd on 2008-09-05
Another thank you!  After searching the posts for a solution, I came across this one.  Worked like a charm.

Ed

---

### Post by zeitler on 2008-09-08
Hi. Tanks for this post. It helps me a lot!...

But in the pass!

I've installed distro 8.04.1. Now, like always my Broadcom 4306 is not recogized. I was following the tutorial and I received the error after the command:
$ sudo rmmod bcm43xx
    ERROR: Module bcm43xx does not exist in /proc/modules

Before this worked fine but now it doesn't. 

Can you or anyone help me. 

Tks!

---

### Post by ubunturules on 2008-09-09
That error is fine.  Don't worry about it.

ubunturules

---

### Post by zeitler on 2008-09-11
Hi again.

I have printed this howto when I started using ubuntu and I was following it.
Now that I take a look again I saw it was a little different from the version I had. I followed the howto and it worked. Thanks and sorry for unneeded (if there is this word :) )reply.

Before I started I did the following commands:

rmmod b43
rmmod ssb

It's something that I've seen in another tutorial, probably it doesn't do anything, but it worked and that's what matters.

Thanks.

Zeitler


EDIT: Ok, 2 happy 2 soon :)

I have rebooted and now I don't have wireless and in the Administration->Network doesn't appear wlan0. 

When I do: lshw -C network in the network about wireless card it appears:
      network:1 UNCLAIMED
      product: BCM4306 802.11b/g Wireless LAN Controller
      vendor: Broadcom Corporation
      phisical id: 5
      bus info: pci@0000:02:05.0
      version: 03
      width: 32 bits
      clock: 33mhz
      capabilities: cap_list
      configuration: driver=b43-pci-bridge latency=32 module=ssb

After rmmod b43-pci-bridge and rmmod ssb: configuration: latency=32

Any ideas?

Thanks again.

---

### Post by zeitler on 2008-09-11
Hi. Finnaly I've done it.:guitar:

I found the answer to my problems in this post [http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

Thanks to all whom helped me!

Zeitler

---

### Post by ubunturules on 2008-09-21
glad you found the solution to your problem.  this guide is getting a major upgrade once 8.04 comes out so I want everybody to get ready for that because it should be great.

ubunturules

---

### Post by weboide on 2008-09-24
My wife has a Compaq Presario 2100, with Broadcom 4306 rev 02, and ubuntu 8.04.1.

I got it working, I followed the instructions, most of them actually.

I didn't install the linux headers, I compiled from source, and I didn't do the network manager part as it's already built in Hardy.
It DIDN'T work with WPA, WPA2, WEP. 

But **it DOES work** with no security after a few reboot and deactivation-reactivating the card. I'm trying to shutdown the computer and start it again and see if it still works.

---

### Post by ubunturules on 2008-09-26
weboide: try running 
```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```
that should make it where you don't have to run modprobe everytime you restart your computer.

---

### Post by ubunturules on 2008-10-09
Did that work?

ubunturules

---

### Post by amidude on 2008-10-21
I have the latest version of Ubuntu and this is my broadcom card info:

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Is this still the preferred way to get this card to work? I am trying to get it running on an HP Pavilion zd7010us.

I've tried to connect using the "Connect to other wireless network" UI and even after entering the SSID and the Key I can't get the "connect" button to gain focus....it stays greyed out.

Man you figure someone would have written a tool to fix this by now. Sorry if I sound frustrated but Ubuntu isn't letting be as "free" with my laptop as I'd like to be. I always have to plug in to a LAN because it simply will not connect to a wifi connection at all.

---

### Post by ubunturules on 2008-10-22
I haven't used the newest version of Ubuntu yet.  I haven't had time to try it.  This guide will be updated when the newest version is officially released.  This method should still work though.  I would definitely give it a try.  If not check back when intrepid comes out.

ubunturules

---

### Post by ubunturules on 2008-10-25
This guide works with Intrepid Ibex 8.10.  I just tried it and I am currently on wireless with 8.10 using this guide.  I did it in about 5 minutes.  I will update the guide so that it will be easier for people running the newest version to understand because there are some steps you can skip.

ubunturules

---

### Post by weboide on 2008-10-31
> **ubunturules said:**
> weboide: try running 
```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```
that should make it where you don't have to run modprobe everytime you restart your computer.

I didn't have to do that.

Now I'm checking if this will work on 8.10 Intrepid without installing anything (except proprietary drivers, maybe).

---

### Post by weboide on 2008-10-31
Hmm I'll have to use your tutorial again.

_Here's what I found:_
Machine: Compaq Presario 2100 with BCM4306 (rev 02)
With Intrepid 8.10, after installing proprietary drivers (fwcutter), wifi is working (didn't try any security like wep or wpa) **but is very slow** 1~2mb/s instead of 54mb/s.

It says the driver used is: NULL(info.linux.driver)

Kinda weird..

---

### Post by zeddock on 2008-11-07
Would you create a guide for 8.10 as well please?
Thanx!

zeddock

---

### Post by Altay_H on 2008-11-08
I followed the guide and now have ndiswrapper working, but still no wireless. nmapplet lists no wireless networks, and iwlist wlan0 also sees no wireless networks. I am certain, however, that I'm within range of at least 4 wireless networks.

Here's my output for ndiswrapper -l:
```

:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

```

And my output for ifconfig -a:
```

:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:70:a3:47  
          inet addr:10.24.102.203  Bcast:10.24.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:b0ff:fe70:a347/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:792309 (792.3 KB)  TX bytes:178532 (178.5 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30456 (30.4 KB)  TX bytes:30456 (30.4 KB)

pan0      Link encap:Ethernet  HWaddr b2:75:54:56:27:6d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:eb:3c:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-EB-3C-8A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

And my output for iwlist scanning:
```

~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

I'm not sure what wmaster0 or pan0 are, considering I only have one wireless card and one ethernet port. When I first installed Hardy I only had lo, eth0, and wlan0. I messed around with my wireless configuration trying to get aircrack working, and after a brief success ended up with messed up wireless settings. I decided to do a clean install of Intrepid Ibex, figuring it would leave me with just lo, eth0, and wlan0 again, but pan0 and wmaster0 are still there. Maybe they're supposed to be there, but I can't help noticing that the presence of pan0 and wmaster0 have resulted in no wireless for me. Any help is greatly appreciated.


EDIT:
My problem is solved. In case anyone else is having a similar problem, here's the solution: [http://ubuntuforums.org/showthread.php?p=6204952](http://ubuntuforums.org/showthread.php?p=6204952)

---

### Post by animeshaga on 2008-11-14
Having Issues with 
Step 12
make distclean 
and 
sudo make

I get Error 2 and Error 1 for this command.
I did "make clean" instead of "make distclean" which worked fine.
but "sudo make" still has issues

Help!
(8.10, dell 1150, clean install, no lan conenction so downloading files from one wireless laptop and transfering using external hard drive)

---

### Post by chazlarson on 2008-11-19
I'm seeing the same thing as animeshaga.

"make distclean" errors out.

"sudo make" fails with an Error 2 pointing at a problem with parameter count in a function call.

---

### Post by keineAhnung on 2008-11-20
Thanks to this forum I've got my Broadcom 4306 working on 8.10 with ndiswrapper out of the box (I got the same compilation error for the newest version of ndiswpapper as mentioned before) so I can see my router and I can connect to the Internet when I'm not using any security.
My problem starts as soon as I switch on WPA.
With all debug flags set for wpa_supplicant, I can see how my notebook tries to connect to the router, how they do a (successfull) 4-WAY-handshank and during this time, I can see with "iwconfig wlan0" the "Access Point". Then after about 5 sec it disappears and after further 5 secs it restarts ...
And now the very strange thing: after 5, sometimes 3 or 7 minutues it just connects and does not continue to write any debug-messages. As soon as this happens, I can get a DHCP-IP-address with "dhclient wlan0" and connect to the internet.
I've also tried the same game with "network-manager-kde", but it stops after two or three retries.

I've tried various options in "wpa_supplicant.conf" but without any success!
 
Has anybody any idea?

---

### Post by ubunturules on 2008-11-27
chazlarson: The parameter error isn't a big deal at all, it should still work.

---

### Post by Jeenyus on 2008-12-04
I have the Broadcom 4306 rev03 card on my HPzv6000 with ubuntu Intrepid Ibex installed.  I followed the guide the best I could but it gets confusing when the steps point out Edgy/Feisty/Draper etc., at the top of the post you mentioned that this should work with 8.10 but its kinda hard to follow.  I there anyway you could clarify the installation process for Intrepid Ibex?

Thanks much,
Jeenyus

---

### Post by ubunturules on 2008-12-05
Jeenyus: you are exactly right and I realize this is a major problem with the guide.  I get off for winter break December the 12th and one of my goals over break is to clean up the guide.  I'm sorry for the confusion.

ubunturules

---

### Post by etm124 on 2008-12-18
Sorry to bring this back up from the dead, but I followed the HOWTO, and it seems like I am ALMOST there.

I'm running Hardy.

my /etc/modprobe.d/ndiswrapper:

```
alias wlan0 ndiswrapper
```

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
address 10.0.0.199
netmask 255.255.255.0
gateway 10.0.0.1

auto eth0

```

result of ndiswrapper -l:
```

bcmwl5 : driver installed
         device(14E4:4320) present (alternate driver: ssb)

```

my card:
```
00:09.0 Network controller: Broadcom Corporation BCM 4306 802.11b/g Wireless LAN Controller (rev 02)
```

ifconfig: 
```

eth0      Link encap:Ethernet  HWaddr 00:0f:20:c9:d0:40  
          inet addr:10.0.0.150  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fec9:d040/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27048 (26.4 KB)  TX bytes:4207 (4.1 KB)
          Interrupt:10 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68993 (67.3 KB)  TX bytes:68993 (67.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:5a:3e:31  
          inet addr:10.0.0.165  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe5a:3e31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:493446 (481.8 KB)  TX bytes:7426 (7.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-5A-3E-31-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"OMGWIDEOPEN"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:90:B3:97:F0   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=123/100  Signal level=-25 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

Any help would be appreciated. Thank you!

---

### Post by tyme on 2008-12-18
can you ping outside ip addresses?

i.e., if:
```
ping ubuntu.com
```
gives you a "cannot resolve" error, feed ping the direct IP:
```
ping 91.189.94.156
```
if you get a response, then the issue seems to be DNS-related, not necessarily your wireless card/driver.

---

### Post by etm124 on 2008-12-18
tyme - 

both ping attempts are failing.

thanks for the response.

---

### Post by etm124 on 2008-12-23
any other ideas i might be able to try?

thanks guys.

---

### Post by etm124 on 2008-12-23
Actually just kinda stumbled upon the solution. I manually typed in my SSID and it connected. 

After that the card scanned and found the other networks in my office.


Thanks for your help guys.

---

### Post by ubunturules on 2008-12-26
New links have been posted for the 32 bit drivrs.  I'm going to try to locate the 64 bit drivers and post them.

---

### Post by bdougs on 2008-12-27
Okay, I feel like I'm missing something important, but I've been trying to follow these directions and a few others, but I also don't know what most of the commands actually mean. Anyway, I tried lspci | grep Broadcom\ Corporation, and I didn't get any output, and when I typed in the second line, I get ERROR: Module bcm43xx does not exist in /proc/modules.

I feel like that's not something I'm supposed to be getting. Any suggestions?

---

### Post by ubunturules on 2008-12-28
If you get the ERROR: Module bcm43xx does not exist in /proc/modules error that is ok.  I need to add this to my guide because it does confuse a lot of people.  That command removes bcm43xx from /proc/modules if you have it in there but some of the newer versions of ubuntu don't come with it in there does it doesn't have anything to remove when you run the command.

ubunturules

---

### Post by jwill113 on 2009-01-31
Well, I am super new to Linux.  Took a few Unix courses at school and I liked it, so I gave ubuntu a try.  I had this same problem of my broadcom wireless not even cutting on.  I read forum after forum.. still no luck.  What I ended up doin was hard wiring my laptop up.  The computer told me I had 243 updates, so I did them all and bam... wireless card works.  Didn't do anything, just downloaded the installs.

---

### Post by bee lauj on 2009-02-10
Ummm...
Yess I Have The Same Problem...


But Im Trying To Connect My Compaq nx9010
To At&t Router...

Is That Possible ??

Is My Driver Too Old For Wireless Connection ??


If U Need To Ask Question To Solve My Problems
Please Ask....=]]

---

### Post by ubunturules on 2009-02-11
what's your problem?

ubunturules

---

### Post by ubunturules on 2009-03-15
has anybody used this guide that used the 64 bit driver and got it to work?

ubunturules

---

### Post by LLudovic on 2009-07-13
Hello,
Please forgive me if I've missed something really obvious or if this is a daft question -I'm a Linux newbie! 
Just installed Ubuntu 9.04 on an old Dell with a Broadcom 4306 (rev 2). Been installing all the drivers, tried all the above and some other methods. The tests show my card is on, but it's greyed out in the Network Manager menu and I can't connect.
I've tried configuring new WiFi networks and unplugging the Ethernet cables, etc... but no luck so far.

Any clues?

---

### Post by Ilovecomputers on 2009-08-27
> **ubunturules said:**
> If you used my guide I would like to hear from you to know how it went and if you're having any problems.  I just updated it a little bit and I want to know if everything still works.  Please let me know.

I just worked on the guide for a little bit.  Changed a couple things to make it a little less confusing.  My website that I was using to host the drivers and pictures got shut down so now I am hosting my drivers on rapidshare.  Please note that if you are getting errors there is 5 problems fixes at the end of the guide.

This is the easiest way to get your Broadcom 4306 wireless card working in the shortest amount of time.  I wouldn't use the firmware cutter because it only allows you to run at 11 Mbps with it.  With ndiswrapper you will get 54 Mbps if your router will allow it.

This guide now works with every Ubuntu distro from Dapper to Intrepid!

The Drivers listed below work for most broadcom 4306 wireless cards but not all of them.  If you use the drivers below and your card doesn'tshow up under network then you should try using the driver that came with your card or go to the manufacturer's website.

Get the 32 bit drivers from [here]("http://rapidshare.com/files/177121041/32_bit_bcmwl5.zip") or the website of the manufacturer of your wireless card.

Get the 64 bit drivers from [here]("http://rapidshare.com/files/177585227/64-bit_Broadcom_54g_Drivers.zip").  I've heard that you don't change the name .inf file to bcmwl5.inf just keep it the way it is.

Do everything in the order as it is listed.

run the following command to make sure you have a broadcom chipset wireless card.
**1.**```
lspci | grep Broadcom\ Corporation
```

**2.**```
sudo rmmod bcm43xx
```
If you get an error message saying ERROR: Module bcm43xx does not exist in /proc/modules it is ok and you can move on to the next step.

**3.**```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

**5.** You will need the Ubuntu CD to get these packages.
```
sudo aptitude install build-essential
```

**6.**
```
uname -r
```

Insert the output of the uname -r command into the following 2 commands where the numbers are at

**7.**
```
sudo aptitude install linux-headers-2.6.22-14-generic
```

Insert the output of the uname -r command into the following 2 commands where the numbers are at

**8.**
```
sudo ln -s /usr/src/linux-2.6.22-14-generic /lib/modules/2.6.22-14-generic/build
```

Download ndiswrapper
**9.**
```
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz
```

Make a folder for ndiswrapper and place it in there
**10.**
```
mkdir ~/ndiswrapper
mv ndiswrapper-1.53.tar.gz ~/ndiswrapper
```

Install ndiswrapper
**11.**
```
cd ~/ndiswrapper
sudo tar -xvzf ndiswrapper-1.53.tar.gz
cd ~/ndiswrapper/ndiswrapper-1.53
make distclean
sudo make
sudo make install
```

**12** If you are running Dapper or Edgy run this command.  Some people say that compiling it works for them and some people say getting it with synaptic so I thought if you just installed both then you'll have some form of ndiswrapper working.  If you don't have a working internet connection then you can get these packages off of the Ubuntu CD.
```
sudo apt-get install ndiswrapper-utils-1.8
```

If you are running Feisty or any version higher than Feisty run this command.  You might need the Ubuntu CD to get these packages.
```
sudo apt-get install ndiswrapper-utils-1.9
```

If you can't get ndiswrapper from any of the sources above you can get it from the Ubuntu CD.

**13.**```
sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf
``` 
If you are using the 64 bit drivers run this command ```
sudo ndiswrapper -i ~/folder where driver is/netbc564.inf
```
Make sure the .sys file is in there also, without it, it won't work


**14.**```
ndiswrapper -l
```
To make sure the hardware is present


**15.**```
sudo ndiswrapper -m
```
To load ndiswrapper automatically when the wlan0 interface is used


**16.**```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

**16. B**
```
sudo gedit /etc/init.d/wirelessfix.sh
```
Paste this into that file

Close and save that file
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
```
```
sudo update-rc.d wirelessfix.sh defaults
```

**17.**```
sudo iwconfig wlan0
``` [/B]

If you are running Gutsy or any version higher than Gutsy you can skip to step 26.
**Enable the Connection**

**18.** Go to System -> Administration -> Networking

**19.** If you don't see any wlan0 connections in Networking then you should restart your computer.

**20.** Go to your eth0 connection and disable the connection.

**21.** Now go to your wlan0 connection and enable it.

**Network Manager**

If you need WPA or WEP encryption do the following:

Note: If you are running Feisty or any version higher than Feisty you can skip steps 22 through 25.

**22.**```
sudo apt-get install network-manager-gnome
```

**23.**```
sudo gedit /etc/network/interfaces
```

**24.** Comment out anything in there at the bottom that has to do with your wireless essid.  You need to also comment out anything that says eth1, eth2, or atho.  When I say comment out that means put a # in from of it. You can leave all of the eth0, wlan0, lo, inet, and auto stuff.

**25.**```
nm-applet
```

**26.** Now click on the applet that is in the top right corner and you should see all of the available connections.  Click on yours and set it up.

**SOLUIONS TO PROBLEMS**

**Problem 1**

If wlan0 isn't showing up under your network connections and you're getting invalid driver errors when you run ndiswrapper -l then go to post #746 on page 75.  It helped a bunch of people so maybe it will help you.  The following commands are from that post.
```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```
Look for the entry for your bcm43xx device and change the NAME at the end to wlan0, example below.

# PCI device 0x14e4:0x4320 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:03:c9:70:7b:a9", NAME="wlan0"

Thanks fireant for the fix for problem 1

**Problem 2**
Totoro found a fix for the eth1 problem.  Thank You Totoro!
add ndiswrapper to /etc/modules
change eth1 -> wlan0 in the files below:
```
sudo gedit /etc/modeprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab
```

**Problem 3**
Shaton found a fix for the FATAL: Error inserting ndiswrapper problem.  Thank You Shaton!
If you get an error saying 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument 

then try this.
```
sudo apt-get install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```

If you are using Feisty then you will need to put a 9 where the 8 is.

**Problem 4**
If you get a lot of error messages talking about the icon then run this command:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

**Problem 5**
If you have to run modprobe ndiswrapper every time you reboot your computer run this command.

```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

Thanks Phifer for the fix for problem 5

I hope this helps a lot of people!

thanks for all your effort but this is totally rocket science math to me.
where are you entering these codes? i have the same problem. i havce a dell inspiron 1150 with this card and cant get a wireless network set up. under the network (double computer icon) wireless networks is grayed out. i can only get an internet connection when i plug it in from the modem. what do i do to get wireless? i need something step by step thats easy to understand. i have ubuntu 9.04
thanks.

---

### Post by Ilovecomputers on 2009-08-27
> **ubunturules said:**
> did this HOWTO help anyone?

no i need help to set up my wireless net work. please. something user friendly.
thanks

---

### Post by LLudovic on 2009-08-28
Hi,

I solved the problem by buying a USB dongle for £6 -works now but I still can't figure out why it did not work in the first place.

I've pasted below the log of the commands you gave me.

somerton47@somerton47-laptop:~$ lspci | grep Broadcom\ Corporation
02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
somerton47@somerton47-laptop:~$ sudo rmmod bcm43xx
[sudo] password for somerton47: 
ERROR: Module bcm43xx does not exist in /proc/modules
somerton47@somerton47-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
somerton47@somerton47-laptop:~$ sudo aptitude install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
somerton47@somerton47-laptop:~$ uname -r
2.6.28-14-generic
somerton47@somerton47-laptop:~$ sudo aptitude install linux-headers-2.6.28-14-generic
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
somerton47@somerton47-laptop:~$ sudo ln -s /usr/src/linux-2.6.28-14-generic /lib/modules/2.6.28-14-generic/build
somerton47@somerton47-laptop:~$ wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz)
--2009-08-28 10:44:36--  [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://kent.dl.sourceforge.net/project/ndiswrapper/stable/1.53/ndiswrapper-1.53.tar.gz](http://kent.dl.sourceforge.net/project/ndiswrapper/stable/1.53/ndiswrapper-1.53.tar.gz) [following]
--2009-08-28 10:44:37--  [http://kent.dl.sourceforge.net/project/ndiswrapper/stable/1.53/ndiswrapper-1.53.tar.gz](http://kent.dl.sourceforge.net/project/ndiswrapper/stable/1.53/ndiswrapper-1.53.tar.gz)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198629 (194K) [application/x-gzip]
Saving to: `ndiswrapper-1.53.tar.gz'

100%[======================================>] 198,629      446K/s   in 0.4s    

2009-08-28 10:44:37 (446 KB/s) - `ndiswrapper-1.53.tar.gz' saved [198629/198629]

somerton47@somerton47-laptop:~$ mkdir ~/ndiswrapper
somerton47@somerton47-laptop:~$ mv ndiswrapper-1.53.tar.gz ~/ndiswrapper
somerton47@somerton47-laptop:~$ mkdir ~/ndiswrapper
mkdir: cannot create directory `/home/somerton47/ndiswrapper': File exists
somerton47@somerton47-laptop:~$ mv ndiswrapper-1.53.tar.gz ~/ndiswrapper
mv: cannot stat `ndiswrapper-1.53.tar.gz': No such file or directory
somerton47@somerton47-laptop:~$ cd ~/ndiswrapper
somerton47@somerton47-laptop:~/ndiswrapper$ sudo tar -xvzf ndiswrapper-1.53.tar.gz
ndiswrapper-1.53/
ndiswrapper-1.53/README
ndiswrapper-1.53/loadndisdriver.8
ndiswrapper-1.53/ndiswrapper.spec
ndiswrapper-1.53/INSTALL
ndiswrapper-1.53/ChangeLog
ndiswrapper-1.53/ndiswrapper.8
ndiswrapper-1.53/utils/
ndiswrapper-1.53/utils/ndiswrapper
ndiswrapper-1.53/utils/loadndisdriver.c
ndiswrapper-1.53/utils/ndiswrapper-buginfo
ndiswrapper-1.53/utils/Makefile
ndiswrapper-1.53/driver/
ndiswrapper-1.53/driver/mkexport.sh
ndiswrapper-1.53/driver/wrapmem.c
ndiswrapper-1.53/driver/pnp.h
ndiswrapper-1.53/driver/longlong.h
ndiswrapper-1.53/driver/rtl.c
ndiswrapper-1.53/driver/ntoskernel.c
ndiswrapper-1.53/driver/loader.h
ndiswrapper-1.53/driver/iw_ndis.c
ndiswrapper-1.53/driver/win2lin_stubs.S
ndiswrapper-1.53/driver/wrapper.c
ndiswrapper-1.53/driver/winnt_types.h
ndiswrapper-1.53/driver/wrapndis.h
ndiswrapper-1.53/driver/usb.h
ndiswrapper-1.53/driver/pe_linker.h
ndiswrapper-1.53/driver/ndis.h
ndiswrapper-1.53/driver/divdi3.c
ndiswrapper-1.53/driver/ndiswrapper.h
ndiswrapper-1.53/driver/hal.c
ndiswrapper-1.53/driver/wrapndis.c
ndiswrapper-1.53/driver/ntoskernel.h
ndiswrapper-1.53/driver/crt.c
ndiswrapper-1.53/driver/workqueue.c
ndiswrapper-1.53/driver/ntoskernel_io.c
ndiswrapper-1.53/driver/lin2win.h
ndiswrapper-1.53/driver/pnp.c
ndiswrapper-1.53/driver/loader.c
ndiswrapper-1.53/driver/ndis.c
ndiswrapper-1.53/driver/iw_ndis.h
ndiswrapper-1.53/driver/pe_linker.c
ndiswrapper-1.53/driver/wrapmem.h
ndiswrapper-1.53/driver/mkstubs.sh
ndiswrapper-1.53/driver/usb.c
ndiswrapper-1.53/driver/wrapper.h
ndiswrapper-1.53/driver/Makefile
ndiswrapper-1.53/driver/proc.c
ndiswrapper-1.53/AUTHORS
ndiswrapper-1.53/Makefile
somerton47@somerton47-laptop:~/ndiswrapper$ cd ~/ndiswrapper/ndiswrapper-1.53
somerton47@somerton47-laptop:~/ndiswrapper/ndiswrapper-1.53$ make distclean
make -C driver clean
make[1]: Entering directory `/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver'
rm -f *.o *.ko .*.cmd *.mod.c *.symvers modules.order *~ .\#*
rm -f *_exports.h win2lin_stubs.h
rm -rf .tmp_versions
make[1]: Leaving directory `/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver'
make -C utils clean
make[1]: Entering directory `/home/somerton47/ndiswrapper/ndiswrapper-1.53/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/somerton47/ndiswrapper/ndiswrapper-1.53/utils'
rm -f *~
rm -fr ndiswrapper-1.53 ndiswrapper-1.53.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver'
make[1]: *** No rule to make target `distclean'. Stop.
make[1]: Leaving directory `/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver'
make: *** [distclean] Error 2
somerton47@somerton47-laptop:~/ndiswrapper/ndiswrapper-1.53$ sudo make
make -C driver
make[1]: Entering directory `/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.28-14-generic M=/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-14-generic'
  LD      /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/built-in.o
  MKEXPORT /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/crt_exports.h
  MKEXPORT /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/hal_exports.h
  MKEXPORT /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/ndis_exports.h
  MKEXPORT /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/ntoskernel_exports.h
  MKEXPORT /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/ntoskernel_io_exports.h
  MKEXPORT /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/rtl_exports.h
  MKEXPORT /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/usb_exports.h
  CC [M]  /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/crt.o
  CC [M]  /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/hal.o
  CC [M]  /home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.o
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/somerton47/ndiswrapper/ndiswrapper-1.53/driver'
make: *** [all] Error 2
somerton47@somerton47-laptop:~/ndiswrapper/ndiswrapper-1.53$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
somerton47@somerton47-laptop:~/ndiswrapper/ndiswrapper-1.53$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4320) present (alternate driver: ssb)
somerton47@somerton47-laptop:~/ndiswrapper/ndiswrapper-1.53$ sudo ndiswrapper -mWARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

somerton47@somerton47-laptop:~/ndiswrapper/ndiswrapper-1.53$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
somerton47@somerton47-laptop:~/ndiswrapper/ndiswrapper-1.53$ sudo gedit /etc/init.d/wirelessfix.sh
somerton47@somerton47-laptop:~/ndiswrapper/ndiswrapper-1.53$ sudo gedit /etc/init.d/wirelessfix.sh
somerton47@somerton47-laptop:~/ndiswrapper/ndiswrapper-1.53$ sudo gedit /etc/init.d/wirelessfix.sh
somerton47@somerton47-laptop:~/ndiswrapper/ndiswrapper-1.53$

---

### Post by polyprotic on 2009-09-29
THANK YOU SO MUCH!!!!   I read a couple of the other posts, they did not solve my problem, however they were on the right track.   The install did not compile properly but I used the add/remove feature as a workaround.   Worked like a charm.  THANK YOU AGAIN.

:popcorn:

---

### Post by ubunturules on 2009-11-10
LLudovic: I'm glad you were able to solve your problem.

polyprotic: your welcome.  I'm glad to hear that you also got it working.  I know the feeling.

---

### Post by ubunturules on 2010-03-06
Has anyone tested this guide with the current version of Ubuntu.  I am going to wait until the new version to come out to edit my guide.

ubunturules

---

### Post by Lauti on 2010-03-07
> **ubunturules said:**
> Has anyone tested this guide with the current version of Ubuntu.  I am going to wait until the new version to come out to edit my guide.

ubunturules

Hello ubunturules,
I just tried your guide to get the following stuff running:
Ubuntu 9.10 {karmic koala} 64-bit (on an older laptop with AMD athlon 64)
but the BCM4306 802.11b/g Wireless LAN Controller is 32-bit!
I dowloaded both the drivers from your rapidshare-links and first tried to install the 64-bit driver during your installation guide.
It's not working.

After doing all this, the wireless network option doesn't show at all anymore.

Should I try the 32-bit driver?
How can I uninstall the 64-bit driver first?

Thank you!
Lauti

EDIT:
without actually knowing or understanding what I was doing, I managed to remove the 64-bit driver and installed the 32-bit version.

with
```
ndiswrapper -l
```
I get the following:
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

it seems the 32-bit driver is now the only one installed, with the 64-bit driver removed.
But what's the meaning of the warnings?

with this command
```
sudo iwconfig wlan0
```
i get this:
> wlan0     No such device

Thanks
Lauti

---

### Post by ubunturules on 2010-03-08
Hello Lauti.  Thank you for using my guide.  Let's see if we can get you working.

to get rid of the 64 bit driver run
```
ndiswrapper -e netbc564
```

restart your computer and tell me what ndiswrapper -l gives you.

I have never seen those warnings before but it could have something to do with the newer versions of Ubuntu and I haven't upgraded in a while.  I will do some research and testing to find out if those are actual problems.  They do not seem very important to me at all but I will see what I can find out.

---

### Post by Lauti on 2010-03-09
Hello ubunturules,
I meanwhile have a fresh install of karmic koala on my laptop (the "old" install was done less than a week ago).
Now I can definitely start over on a white sheet.

So my questions to start with are:
1. my install is a 64 bit version on an older HP compaq nx9105 with an AMD athlon 64, and the mentioned WLAN card is 32-bit: is this compatible?
2. which WLAN card-driver should I use? 32- or 64-bit?

THANKS
Lauti

---

### Post by ubunturules on 2010-03-09
I would probably try the 32 bit driver first and if that doesn't work try the 64 bit driver.

---

### Post by moggyman on 2010-05-22
Hi! are you updating the instructions on the first page? I got stuck not knowing if i want 32 or 64 bit driver, so i tried both!! Now I seem to have a problem on the following step:


ubuntu@ubuntu:~/ndiswrapper/ndiswrapper-1.56$ sudo ndiswrapper -i ~/folder where driver is/netbc564.inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

thanks for your help

---

### Post by Lauti on 2010-07-23
Hello again!
Hello ubunturules!

After all those months I wanted to try it again, if your guide works on my laptop, but it does not look like it's working.

```
ndiswrapper -l
```now gives me the following:
```
admin-pc@admin-pc:~$ ndiswrapper -l
bcmwl5a : driver installed
    device (14E4:4320) present (alternate driver: ssb)
```thats good, right?

BUT

with this comand:
```
sudo iwconfig wlan0
```I still get
```
admin-pc@admin-pc:~$ sudo iwconfig wlan0
wlan0     No such device
```and btw, while using the guide, after the reboot (before jumping to point #26), my laptop lost the ability to recognize the mouse!
What could be the problem here?

Thanks a lot!

---

### Post by 1point9turbo on 2010-07-25
Hey guys.  I want to get rid of Windows and use Ubuntu, I really do but I keep running into the same issue where I can not get either of 2 wireless devices to work and thusly, making me stay in windows. I do not have access to an ethernet cable so its either I get it to work or I stay in windows.

anyway, ubuntu 10.04, my aging AMD 64 desktop.  I have WMP54GS (version 2 i think) and WUSB600N version 1 (gave up on)

Has anyone had this working in 10.04?  I followed every guide I can find but most are dated and none of them worked.  Basically, installed NDISwrapper, and Ndisgk.  Downloaded the driver for the card and installed in Ndisgk. There is no change and the connections manager at the top when you click just shows "device not ready" for the wireless device.  

any help?

---

### Post by 1point9turbo on 2010-07-27
Anyone?  installed the driver in Windows Wireless Drivers.  Says "Hardware Present: Yes"

in the network connections page, nothing under the wireless tab.  Clicking on the wireless symbol at the top bar, it shows the wireless connection and then says its disconnected underneath it.

---

### Post by davidbowie on 2010-08-14
Much thanks Ubunturules!
This had been working flawlessly 'till kernel 2.6.32-24 came around. 
now i get an error in syslog after ndiswrapper interfaces ```
<info> (wlan0): deactivating device (reason 2)
supplicant_interface_acquire: assertion 'mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
<info> (wlan0): supplicant manager state: down -> idle
<info> (wlan0): device state change: 2->3 (reason 0)
b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
```Id rather not use fwcutter if possible. Any assistance appreciated.:KS

Edit: I fixed it.. It needed a fresh install of ndiswrapper utils 1.9

Edit2: nevermind problem still persists. It repeats the error twice now.. :(

---

### Post by quasidecent on 2010-08-30
Hey! I just loaded Lucid onto my HP laptop and everything works swimmingly except for this wireless modem. Broadcom 4306. I went through this entire howto and the wireless still will not work. It recognizes the hardware but does not show a wlan0 connection.

I'm lost - have only been using ubuntu for about a year.

Any idea how i can fix this?

Thanks!

Zach

EDIT: I went into the blacklist list and for some reason b43 and b43legacy were both blacklisted. I took them off the list and now I can now at least see the words "wireless networks" on the top part where I normally connect to a network. still no wlan0 in network connections.

---

### Post by ubunturules on 2010-11-27
Sorry that I haven't been on here in a while.  I haven't had time to rework the howto because I've been busy with school.

quasidecent:  Take a look at the problems part of the howto and see if that helps.  There are a couple of those that are similar to the kind of problem you are having.  If none of those work let me know and I will try to further assist you.

davidbowie:  Did a little research and a kernel upgrade seems to fix the problem.

For Everyone Else:  Please let me know if you are still having problems.  I haven't been on here in a while to check the guide and I apologize for that.  I recently installed Maverick not to long ago and haven't even tried to get the wireless card working yet because like I said I've been pretty busy.  Once I find some free time I will rewrite the guide completely.  Even I had problems trying to get it working with newer versions of Ubuntu and I just haven't taken the time to redo the guide.  Thank you for still looking at my guide and I promise I will have it updated in the near future.

---

### Post by vivsha on 2010-12-07
i'm a newbie with linux. i finally gave up on windows and installed ubuntu 10.10. my dell vostro laptop has broadcom 440X card. now the wireless internet is connect and running. however after browsing for a while the connection suddenly slows down to 11mb/s. i have fwcutter and not ndiswrapper. if i want to get ndiswrapper, should i uninstall fwcutter? can i install ndiswrapper through synaptic manager? what else do i need to do. Thanks in advance!

---

### Post by ubunturules on 2010-12-17
sudo iwconfig eth1 rate 54Mb

substitute eth1 with the name of your wireless card.

---

### Post by MattB60 on 2011-01-10
I am fairly new to Ubuntu. I have installed Ubuntu 10.10 on an old Dell Latitude X300 laptop with a Broadcom B4306 wifi adapter. 
I followed the walk through successfully and can get a 54mbps wifi connection, but only on an open (unencrypted) connection.
However I cant get it to connect to an encrypted connection - I use normally have  WAP2-PERSONAL encryption set on my router and WAP2 doesnt even appear as an option in the Ubuntu network manager.
Can you tell me how I set up the B4306 to use WAP2 - I know it will because I temporarily installed ubuntu 8.04 and made it work there using the FW34-cutter package.
any ideas appreciated.
MattB

---

### Post by ubunturules on 2011-01-19
MattB60:  try uninstalling and reinstalling network-manager and the wpa-supplicant packages

---

### Post by bcand on 2011-03-05
Ubunturules: Thank you very much for the guide.
 
I recently installed Ubuntu 10.10 Maverick Meerkat on a Dell Inspirion 8600 laptop, with a Dell TrueMobile 1300 WLAN mini-PCI wireless card made by Broadcom. I tried an untold number of instructions to get on wireless without success. I downloaded the driver bcmwl5.inf from Dell support, and could get "driver installed" and "device present" through Synaptic Package Manager, but I could not see any wireless broadcasts from my gateway or any others in my area. 
 
[LEFT]Then, I found your guide on page 1 of this thread. I uninstalled the driver, went through the steps of your guide, and it worked perfectly! The only changes I had to make were: it did not recognize the "aptitude" command in steps 5 and 7, but worked fine when I changed them to "apt-get". It was unable to install ndiswrapper-utils-1.8, but I went ahead and it installed ndiswrapper-utils-1.9 without any problem. I put the CD installation disk in where you said, but I don't think it ever activated it, but still performed the instructions just fine. I think the needed files were already on the Ubuntu files on my computer.
 
Is there anywhere on the internet where the guide is published for printout, other than just a part of this thread? When I print out this thread, some of the print is small, and I at my age, I have to get a magnifying glass and bright light to tell the difference between a - and a ~.
 
Thanks, again for sharing your guide.
                                                                                                                                                                                                                                                                     [/LEFT]

---

### Post by sfrmpton80 on 2011-03-29
if im not using the disc for install and have the usb instead what then? ty again cause i have been messing with this for 20 hours or better with all these directions that all tell you to diff things and none of them work!

---

### Post by sfrmpton80 on 2011-03-29
i tried to install it from the instructions inclused in the app and now i cant get it uninstalled to do that when i say  i cant del file ndiswrapper.ko and when i got to the directory and type rm ndiswrapper.ko it says file is protected any clue?
1`

---

### Post by jchw on 2011-05-05
I installed Ubuntu last July and have been trying to get the wifi to work ever since. I followed the advice of kontza to install firmware-b43-lpphy-installer and it worked for a few months so I know it is possible. Then I moved to a new location two weeks ago and in trying to get a connection working I followed some advice on one the forums to install the Broadcom driver in Systems Admin Additional Drivers. As soon as I did that I lost my wireless connections and have been unable to get any connection since. I have read all the threads and installed and uninstalled so many programs now I am totally lost and unable to get back to where I was a few weeks ago. Luckily I only need to use a wired connection otherwise I would have no choice but to move back to Windows. The only solution I can see is to buy a new wireless card that supports Linux but I do not know if that is feasible or the maybe the best alternative is to get a new laptop.

---

### Post by Ralph L on 2011-09-29
I am trying to install lucid on a Compaq Presario 2100 (2195US to be exact) with a Broadcom 4306 rev2 internal wireless. (Originally I tried to install Natty, but I couldn't pull down menus after the Live CD booted, so I dropped back to lucid and have it running except for wireless) I know the 4306 hw works, because I have a dual boot on the Compaq, and XP works fine with my router and the Internet. My router is set for WEP and I don't do any filtering on mac addresses. I have tried disabling WEP, but that didn't help. I also have a Dell Latitude D610 with a Broadcom 4318 that runs fine using lucid, the firmware from b43legacy. I set up Network Connections on the Compaq to be just the same as those on the Dell.

I have read many many posts in this and other forums, but still can't make it work. Also, I have found no other post, where wireless definitely worked with my exact hw. I have come the closest to having a working system by using ndiswrapper as specified on page 1 of this post.

My current status is that (using ndiswrapper) I can connect to my router using WEP. Everything works except I can't get the DHCP to work and end up with the wrong IP numbers. If I set Network Connections>Wireless>Edit>IPv4 Settings to use Automatic (DHCP), then the wireless won't lock up with my router. However, if I set IPv4 to "Link-Local only" or "Shared to other computers", it will lock up, but not have the correct IP numbers--which makes sense since DHCP wasn't set.

Here is the output from dmesg (filtered).  Note that that ndiswrapper was first registered and then deregistered, got "invalid cmd 12", and got "setting auth mode to 3 failed".  I don't know if any of these errors are meaningful or not.  Also, note that there are several b43legacy messages.  Does this indicate that I have two drivers installed simultaneously that may be battling each other?

[PHP]ralph@presario-lucid:~$ dmesg | grep 'b43\|bcm\|ssb\|ndis\|wlan'
[    1.345597] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[    1.349096] ssb: Sonics Silicon Backplane found on PCI device 0000:00:09.0
[   18.225795] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   18.266236] b43legacy-phy0: Broadcom 4306 WLAN found
[   18.288102] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   18.288128] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   18.320137] b43legacy-phy0 debug: Radio initialized
[   19.587343] usbcore: registered new interface driver ndiswrapper
[   22.319032] b43-pci-bridge 0000:00:09.0: PCI INT A disabled
[   22.485159] usbcore: deregistering interface driver ndiswrapper
[   22.748392] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   22.957749] ndiswrapper: driver bcmwl5 (Linksys,02/12/2003, 3.10.39.7) loaded
[   22.958220] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   23.818944] ndiswrapper: using IRQ 10
[   24.122553] wlan0: ethernet device 00:90:4b:44:7f:66 using NDIS driver: bcmwl5, version: 0x50000, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[   24.122717] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (C0010015)
[   24.122722] wlan0: encryption modes supported: none
[   24.125362] usbcore: registered new interface driver ndiswrapper
[   62.614539] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   66.090583] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   66.360733] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   77.156051] wlan0: no IPv6 routers present
[/PHP]

Any help would be appreciated.

Ralph

---

### Post by stevecook on 2011-10-28
> **ubunturules said:**
> I know it's been a while since I've updated the guide.  I just did a fresh install of 10.10 and I'm going to start working on the guide this week.  11/27/10

This is the easiest way to get your Broadcom 4306 wireless card working in the shortest amount of time.  I wouldn't use the firmware cutter because it only allows you to run at 11 Mbps with it.  With ndiswrapper you will get 54 Mbps if your router will allow it.

The Drivers listed below work for most broadcom 4306 wireless cards but not all of them.  If you use the drivers below and your card doesn'tshow up under network then you should try using the driver that came with your card or go to the manufacturer's website.

Get the 32 bit drivers from [here]("http://rapidshare.com/files/177121041/32_bit_bcmwl5.zip") or the website of the manufacturer of your wireless card.

Get the 64 bit drivers from [here]("http://rapidshare.com/files/177585227/64-bit_Broadcom_54g_Drivers.zip").  I've heard that you don't change the name .inf file to bcmwl5.inf just keep it the way it is.

Do everything in the order as it is listed.

run the following command to make sure you have a broadcom chipset wireless card.
**1.**```
lspci | grep Broadcom\ Corporation
```**2.**```
sudo rmmod bcm43xx
```If you get an error message saying ERROR: Module bcm43xx does not exist in /proc/modules it is ok and you can move on to the next step.

**3.**```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```**5.** You will need the Ubuntu CD to get these packages.
```
sudo apt-get install build-essential
```**6.**
```
uname -r
```Insert the output of the uname -r command into the following 2 commands where the numbers are at

**7.**
```
sudo apt-get install linux-headers-2.6.22-14-generic
```Insert the output of the uname -r command into the following 2 commands where the numbers are at

**8.**
```
sudo ln -s /usr/src/linux-2.6.22-14-generic /lib/modules/2.6.22-14-generic/build
```Download ndiswrapper
**9.**
```
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.56.tar.gz
```Make a folder for ndiswrapper and place it in there
**10.**
```
mkdir ~/ndiswrapper
mv ndiswrapper-1.56.tar.gz ~/ndiswrapper
```Install ndiswrapper
**11.**
```
cd ~/ndiswrapper
sudo tar -xvzf ndiswrapper-1.56.tar.gz
cd ~/ndiswrapper/ndiswrapper-1.56
make distclean
sudo make
sudo make install
```**12** If you are running Dapper or Edgy run this command.  Some people say that compiling it works for them and some people say getting it with synaptic so I thought if you just installed both then you'll have some form of ndiswrapper working.  If you don't have a working internet connection then you can get these packages off of the Ubuntu CD.
```
sudo apt-get install ndiswrapper-utils-1.8
```If you are running Feisty or any version higher than Feisty run this command.  You might need the Ubuntu CD to get these packages.
```
sudo apt-get install ndiswrapper-utils-1.9
```If you can't get ndiswrapper from any of the sources above you can get it from the Ubuntu CD.

**13.**```
sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf
```If you are using the 64 bit drivers run this command ```
sudo ndiswrapper -i ~/folder where driver is/netbc564.inf
```Make sure the .sys file is in there also, without it, it won't work


**14.**```
ndiswrapper -l
```To make sure the hardware is present


**15.**```
sudo ndiswrapper -m
```To load ndiswrapper automatically when the wlan0 interface is used


**16.**```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```**16. B**
```
sudo gedit /etc/init.d/wirelessfix.sh
```Paste this into that file

Close and save that file
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
``````
sudo update-rc.d wirelessfix.sh defaults
```**17.**```
sudo iwconfig wlan0
```If you are running Gutsy or any version higher than Gutsy restart your computer and skip to step 26.
**Enable the Connection**

**18.** Go to System -> Administration -> Networking

**19.** If you don't see any wlan0 connections in Networking then you should restart your computer.

**20.** Go to your eth0 connection and disable the connection.

**21.** Now go to your wlan0 connection and enable it.

**Network Manager**

If you need WPA or WEP encryption do the following:

Note: If you are running Feisty or any version higher than Feisty you can skip steps 22 through 25.

**22.**```
sudo apt-get install network-manager-gnome
```**23.**```
sudo gedit /etc/network/interfaces
```**24.** Comment out anything in there at the bottom that has to do with your wireless essid.  You need to also comment out anything that says eth1, eth2, or atho.  When I say comment out that means put a # in from of it. You can leave all of the eth0, wlan0, lo, inet, and auto stuff.

**25.**```
nm-applet
```**26.** Now click on the applet that is in the top right corner and you should see all of the available connections.  Click on yours and set it up.

**SOLUIONS TO PROBLEMS**

**Problem 1**

If wlan0 isn't showing up under your network connections and you're getting invalid driver errors when you run ndiswrapper -l then:
```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```Look for the entry for your bcm43xx device and change the NAME at the end to wlan0, example below.

# PCI device 0x14e4:0x4320 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:03:c9:70:7b:a9", NAME="wlan0"

Thanks fireant for the fix for problem 1

**Problem 2**
Totoro found a fix for the eth1 problem.  Thank You Totoro!
add ndiswrapper to /etc/modules
change eth1 -> wlan0 in the files below:
```
sudo gedit /etc/modeprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab
```**Problem 3**
Shaton found a fix for the FATAL: Error inserting ndiswrapper problem.  Thank You Shaton!
If you get an error saying 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument 

then try this.
```
sudo apt-get install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```If you are using Feisty then you will need to put a 9 where the 8 is.

**Problem 4**
If you get a lot of error messages talking about the icon then run this command:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```**Problem 5**
If you have to run modprobe ndiswrapper every time you reboot your computer run this command.

```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```Thanks Phifer for the fix for problem 5

I hope this helps a lot of people!For any person who is brand new to Ubunto, your "HOWTO" is complete gobbledegook. I say this from the perspective of knowing I am of reasonable intelliegence and so am quite capable of following complex instructions perfectly well.

In other words, your "HOWTO" has been written for people who already have a significant knowledge of this OS. 

Do you know of a "HOWTO" that actually adresses the needs of new users?

---

### Post by Ralph L on 2012-12-18
I got my Compaq Presario 2100 with Broadcom 4306 REV 2 to work unencrypted, with wep, wpa, or wp2.  And its very fast. I did a more complete write-up on this at [http://ubuntuforums.org/showthread.php?t=2095736](http://ubuntuforums.org/showthread.php?t=2095736)

---

