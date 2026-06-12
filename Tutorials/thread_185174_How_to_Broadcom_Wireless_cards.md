---
title: "How to: Broadcom Wireless cards"
date: 2006-05-31
forum: Tutorials
---

### Post by nickm on 2006-05-31
****In my edgy knot 2 testing I found that edgy users can stop the guide after competing stage 4 or 4b as it 'just works' with out network-manager if you fill in the SSID and set the wireless device to DHCP in the "networking" option under System > Administration****


This Should work with Apple hardware as well as PC's.

How to get a wireless card working in Ubuntu 6.06 or 6.10) with a Broadcom chipset 43xx


**This guide assumes 2 things:**
[LIST]
[*]Wired Internet access on the machine with the wireless card on it, in my case i had a 10/100 LAN card that i was using as i couldn't get wireless to work which gave me full access to internet - although it is possible to put the files required on a CD and then add that CD as a repo in synaptic on the wireless machine, how to do this is not covered here, you could even extract the firmware on a different PC and place it in the right location on a remote PC using a CD/Pen drive taking a .deb of network manager with you.
[*]A CLEAN install of dapper or edgy, most of the problems/failures in the responses to this guide have been because of unclean installs giving configuration that gets in the way of this guide and stops it from working, my dapper was installed during the Flight 5 stage and updated from there to knot 2 so its not necessary to reinstall from 6.0* or even if it has been updated from breezy but you might want to think about reinstalling if you've messed around with Ndis prior to this.
[/LIST]

**Okay so you have a wireless card that shows up in ubuntu but doesnt connect to any wireless network?**

The reason the card shows up but doesn't work is because ubuntu is only distributed with its driver (so it can recognize it) not with its firmware (so it can USE it) for legal reasons.

However you can take the firmware out of the windows drivers and put them into ubuntu and make the card work!

**Follow these steps to get your wireless card working under ubuntu dapper 6.06:**

To find out if your card has a broadcom chipset run the following command:
[CENTER]```
 lspci | grep Broadcom\ Corporation 
```[/CENTER]
If that returns a string of numbers followed by the words Broadcom Corporation and then some more numbers then your in luck!
But if not, try my guide anyway, it cant do any harm and it might work for you, its largely untested for cards other than mine and the success stories posted here so give it a go and see!

Here is my output from doing this:
[CENTER]```
lspci | grep Broadcom\ Corporation
0000:02:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```[/CENTER]

It seems that if you get the following string back: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) that this guide is VERY unlikly to work for you although it does sometimes, dont ask me why, but basically every "no" vote and "this didnt work for me" post comes from a BCM4318 user....

**Prerequisite**
    [LIST]
[*]Ubuntu dapper
[*]      A wireless card that shows up in Ubuntu
[*]      A driver installation CD (for Windows) OR a driver for your card from the internet
[*]      Access to the Ubuntu Universe Repository
[/LIST]

** 1 ) Ensure you have access to the other ubuntu repos**
follow the intructions on the second heading from this page to ensure you have the universe enabled
[https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)

** 2 ) Copy your windows driver to your desktop**

**Use this driver with preference to any other:** 
[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
if this fails, your could use any of these:
[LIST]
[*]Copy the driver from the CD that came with the Card
[*]Copy it over from your windows partition if you have access to it, it will be located here: /Windows/System32/Drivers/bcmwl5.sys
[*]Obtain it from here -[http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip)
[*]Get any driver for your card of any date from their website - use this if initially you are not successful first tome try some newer/older drivers
[/LIST]

** 3 ) Install bcm43xx-fwcutter**
Open a terminal (dont worry) and type the following:
[CENTER]```
sudo apt-get install bcm43xx-fwcutter
```[/CENTER]
It will ask for your password and may ask you to press y to install, but dont worry its really easy

**GUI Alternative:** go to *System* in the top Gnome bar then *Administration* then *Synaptic Package Manager*
From here click *Search* and search for bcm43xx-fwcutter
[CENTER][IMG]http://boredklink.googlepages.com/synapticsrearch.png[/IMG][/CENTER]
Right click on its entry in the package window, select *Mark for Installation* and then click apply
[CENTER][IMG]http://boredklink.googlepages.com/synapticselect.png[/IMG][/CENTER]

** 4 ) Extract your Cards firmware from the driver**
Open a terminal (dont worry) and type the following:
[CENTER]```
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
```[/CENTER]
This will create lots of new files in the /lib/firmware directory, this is the firmware part of the driver that will make your card work with ubuntu!
[CENTER][IMG]http://boredklink.googlepages.com/libfirmware.png[/IMG][/CENTER]

** 4B ) Extract your Cards firmware from the driver**
Just to be safe we'll put the driver in the kernel folder too
[CENTER]
```

sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o

```
[/CENTER]

you may have to repeat this step each time the kernel is updated or you may not, your results may vary.

***Note* The location and name of the .o file for this command may differ in your case,  if you really get stuck type bcm43xx-fwcutter and then hit space, find your file using the GUI and then drag and drop it into the terminal.**

** 5 ) Install Network Manager**
I find that this is the best way to manage wireless connections
[CENTER]```
sudo apt-get install network-manager-gnome
```[/CENTER]
It may ask for your password and may ask you to press y to install, but dont worry its really easy

[I]You may find that Network Manager adds itself to system > preferences > sessions >startup programs
or you may not, if you find its not inlcuded,  add[/I]
[CENTER]```
 nm-applet --sm-disable
```[/CENTER]

[I]as found here: [http://ubuntuforums.org/showpost.php?p=1082980&postcount=32](http://ubuntuforums.org/showpost.php?p=1082980&postcount=32) , Network Manager might not work for Apple users, he says that a program called wifi-radar worked for him instead so if network manager is no good for you try this program instead
This might apply for non apple users as well [/I]
[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f)

** 6 ) Bookmark this page and Reboot**
Press Ctrl + D and then click on add
[CENTER][IMG]http://boredklink.googlepages.com/bookmark.png[/IMG][/CENTER]
Then log out & reboot
Return to this page after logging back in again


** 7 ) Use your new Wireless connection**
From what i remember network manager should now show up by your clock and display your current connection, if your lucky it will show a series of bars, this means your now using your wireless connection so lucky you!
[CENTER][IMG]http://boredklink.googlepages.com/nm.png[/IMG][/CENTER]
If it doesnt, right click on it and tick "Enable Wireless" then left click on it 
 and select the wirless network of your choice.

Thanks, i hope this helps...

[B]
Issues[/B]:
----------------------------------------------------
Ensure the router you are connecting to supports 802.11 B connections
as this is what the card is now set up to use, check if your router has a "mixed"
setting rather than a G only setting which it should as G is backwards compatible with B 
----------------------------------------------------
For anyone that is having problems, try this:
[CENTER]```
modprobe bcm43xx
```[/CENTER]
and reboot
----------------------------------------------------
Information about networkmanager

[https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)
----------------------------------------------------
people seem to be having trouble getting this specific card: *Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)* working using this guide, take a look at this post for help:
[http://ubuntuforums.org/showpost.php?p=1084114&postcount=43](http://ubuntuforums.org/showpost.php?p=1084114&postcount=43)
or
[http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218) if your looking to Ndis instead
----------------------------------------------------
If you find your driver comes in a windows EXE format, typically this will just extract the drivers and can be run using Wine and then collected from your wine directory in the same places you can find them in windows
you could try renaming them to filename.zip and seeing if they open that way too.

---

### Post by markmcspadden on 2006-05-31
A little adjustment...

The command "bcm43xx-fwcutter /home/$USER/Desktop/bcmwl5.sys" creates the firmware files in the directory you are current in...it cannot be assumed that is the "Desktop".

I couldn't figure out why it wasn't creating the files, then I stumbled across them in my "~" directory (where I ran the command). Not a huge thing, but I wouldn't consider myself too much of a linux newbie and it got me.

Other than that...great work...I have wireless without the pain of the ndiswrapper manual install!!! Thanks a ton!

---

### Post by nickm on 2006-05-31
Hey, thanks, im glad i helped someone :)
out of interest what card is it?

I did put a little note about that in step 3 when i made it, i'v made it a little more prominent for other people

---

### Post by spd106 on 2006-05-31
Nice howto nickm, it deserves to be a sticky in my opinion.

Could you add a way for users to check what kind of cards are likely to work ie 

```
$lspci
0000:02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

Cheers

---

### Post by nickm on 2006-05-31
thanks spd106, i'll make an ammendment now :)

I decided people should be able to digg it too:
[http://digg.com/linux_unix/Get_your_wireless_card_working_in_Ubuntu](http://digg.com/linux_unix/Get_your_wireless_card_working_in_Ubuntu)
that way people can find it right away untill google adds it

---

### Post by nickm on 2006-06-01
[QUOTE=spd106]Nice howto nickm, it deserves to be a sticky in my opinion.

Cheers[/QUOTE]

well, if any mods want to do it, i promise to maintain it.... ;)

---

### Post by imrumpf on 2006-06-01
```
ian@ian-laptop:~/Desktop/SP32158A$ bcm43xx-fwcutter bcmwl5.sys
Sorry, the input file is either wrong or not supported by fwcutter.
I can't find the MD5sum 69f940672be0ecee5bd1e905706ba8ce :(
```

what is that supposed to mean?? :S:S

---

### Post by nickm on 2006-06-01
that means that the specific file you have isnt supported by fwcutter, it checks the firmware md5sum against a list of what it knows works and yours hasnt come up

see for yourself
```
 nickm@ubuntu:~$ bcm43xx-fwcutter -l | grep 69f9 (yours)
nickm@ubuntu:~$ bcm43xx-fwcutter -l | grep c3e (one i know works)
wl_sta.o        3.31.16.0               a/b/g  c3e663cb78b2fc299088de69fc11a9a9

```

all i can suggest is that you look for a newer/older driver on the internet for your card and try it agian with that...

---

### Post by Vaan on 2006-06-01
**Thank you!** 

Wow, thank you soo much. This was an **excellent** guide. I cannot express my gratitude enough for taking the time to make such a wonderful guide.

I spent most of my day yesterday trying to setup my wireless on my laptop following the guides on the wiki. After messing around for quite some time, I finally got it to work. However, it wasn't even working all that great (I had to constantly config the wireless each time I rebooted via terminal).

Then unfortunetly I had to reinstall my unbuntu (Dapper Drake btw) becuase of some problems I had trying to install KDE. Any how, I told myself I would reread over the wiki again today.

To my unfortunate surprise, when I went to go look in the wiki today (search broadcom) all the guides that were there yesterday now redirect to a new guide that is terrible. I almost lost it. It was there one day, and gone the next (literally).

I didn't know what to do. So I tryed my luck to search on the forums, and up came this thread, my life saver.

Not only was this explanation much faster than anything else I've read, but it actually works completely for me. I love the new network manager that I didn't even know existed. Thank you for telling us about it, works much better than the default. I can just click and switch wireless connections easily.

In my opinion, not only should this thread be made a sticky, but someone should add it to the unbuntu wiki. This will help many people and spread the word out on how to once and for all get these cards to work.

Thanks again, really appreciate it. :)

Also I noticed this thread is under the Breezy section. I'm actually using the latest version of Dapper Drake (6.06 I believe) and I notice most users are having broadcom problems with Dapper. If it could be moved somewhere to a more general place, that would be very helpful for future users I'm sure.

**Update**

Also I didn't have my driver CD at hand during this whole process. Luckily I was able to copy the driver (bcmwl5.sys) from my windows disk (under /Windows/System32/Drivers/bcmwl5.sys) and extract it that way to my unbuntu firmware directory. For future members reading this helpful I guide, I would like to add that you can grab the latest version of this driver from here -> [ bcmwl5.sys](http://sidulus.textdrive.com/bcmwl5sys.zip) (if you could add that into the guide somehow it would be great)

---

### Post by nickm on 2006-06-01
Thanks Vaan, i didnt even realise there was a dapper and breezy section, i have PMed a mod to rectify this, Thankyou!

I will also incorporate your update into the instructions an another method of obtaining the driver files.

I am testing my own modification to the guide at the moment which enables an entire step to be removed, it seems in Cutter you can specify where the files are created to, so if i specify that they are created to /lib/firmware you wont have to move them by hand! i'll give it a go and get back to you all tonight.  - **implemented**

---

### Post by Vaan on 2006-06-01
Ah that's no problem. I am now viewing this thread and happily browsing the net with my beautifully working wireless connection. 

Yet again you have managed to make this fix even simpler. :)

---

### Post by swhit on 2006-06-01
When extracting the card's firmware, I've seen this done differently by two seperate "How-To's". Which is correct?

```
sudo bcm43xx-fwcutter -w /lib/firmware /path/to/bcmwl5.sys

or

sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-23-386 /path/to/bcmwl5.sys
```

or does it not matter?

---

### Post by nickm on 2006-06-01
swhit, I put the firmware in that 2.6.15-23-386 folder and it didnt work for me,
I should think that that would lead to a problem when the kernel was updated too, but i dont know how that works...
so i think it does matter, i know my method works and i cant speak for the other method beyond  "it didnt work for me".

vaan, im glad i can help :), I think its thanks to you that this made it into the How to: catagory, which is a location that will make it much more helpfull to people, go team!

---

### Post by slooksterpsv on 2006-06-01
I promise I will figure out how to get this working for us PPC users, I'm going to try this method, and if it works for my Apple PPC Mac I'll shout it out the Windows. PPC has had the biggest issue when working with wireless. Wish us luck everyone - if I get it to work I'll write a How TO specifically for Apple Users.

---

### Post by nickm on 2006-06-01
Good Luck!! technically if it works isnt this the guide for apple users too?

---

### Post by Vaan on 2006-06-01
No problem, I'm glad I was able to lend some help.

Yesterday was my first Unbuntu experiance, and since today, it's been going very well. I love this OS. It's on a dual-boot with my WinXP Pro. I mainly installed it so I can get more familiar with linux and the terminal. Sometimes I do work via SSH (shell) on deticated linux servers, so it's extremely helpful to know how to use the terminal effectively.

Not only that, but the GNOME GUI is quite beautiful. :)

---

### Post by rjstevens3 on 2006-06-01
Does not appear to be working with my HP dv8000. I have a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) and have tried a few different drivers obtainted from the ndiswrapper wiki (I'm not using ndiswrapper, but the windows drivers for my chipset will be the same). I have also tried the drivers from this guide without success. 

The device shows up, but no essids show up when i try to configure. ifconfig shows that it is installed and should be working. 

Has anyone else ran into this problem?

-RJ

---

### Post by thecrazymonk86 on 2006-06-01
hey i got this message when moving the files into the firmware folder:

*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.*****: But this can be added in the future...

and my wireless doesnt work, i get an ip but no net and cant connect to router

---

### Post by Ziptar on 2006-06-01
Thanks for the excellent write up!! Worked like charm for me and I have been a linux user for all of 20 minutes ;)

---

### Post by crag277 on 2006-06-01
I followed a very similar guide on the wiki to try and get my Broadcom 4318 working in my Compaq V2000Z laptop.  Only differences are I'm using Kubuntu and the bcmwl5.sys file form the compaq driver site for this computer.  I thought everything was going great.  The blue light came on after the driver install and it found my wireless network.  But when I tried to connect, using Wireless Assistant in KDE it could not connect to the network.  Now, the light is still on, iwconfig correctly identifies the device, but it no longer sees any wireless networks, even though there are two very strong ones in range.  Any ideas?

I have a Turion 64, AMD64 version of Kubuntu 6.06, and 1GB RAM.

I saw another post of problems with this wireless device when the system has >1GB of RAM.  Is there any merit to that?

---

### Post by slooksterpsv on 2006-06-02
I did the same thing I've been doing before and it still works. Ubuntu just needs more support on getting these things working instead of a work-around.

---

### Post by nickm on 2006-06-02
For anyone that is having problems, try this:
```
 modprobe bcm43xx 
``` 
and reboot

---

### Post by nickm on 2006-06-02
[QUOTE=rjstevens3]

The device shows up, but no essids show up when i try to configure. ifconfig shows that it is installed and should be working. 

Has anyone else ran into this problem?[/QUOTE]

can you try this:
```
 iwconfig 
``` 
and post what you see?
------------------------------------------------------------
[QUOTE=thecrazymonk86]
hey i got this message when moving the files into the firmware folder:

*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.*****: But this can be added in the future...

and my wireless doesnt work, i get an ip but no net and cant connect to router
[/QUOTE]
hmm, i dont quite know what to make of this, i got that same error and mine works... i dont understand how you have an IP assigned to you from your router but you cant connect.. can you go to System > Administration > networking and see if your card is disabled on that menu? it should be.
Also clear out the values on the DNS tab too. hope that helps
------------------------------------------------------------
[QUOTE=crag277]
But when I tried to connect, using Wireless Assistant
[/QUOTE]
Try network manager

[QUOTE=crag277]
I saw another post of problems with this wireless device when the system has >1GB of RAM. Is there any merit to that?
[/QUOTE]

Doubtful, i dont think RAM will effect anything in that way

---

### Post by crag277 on 2006-06-02
I'm using KDE, so I installed knetworkmanager, but still no luck.  It still does not find any availible wireless networks.  However when I manually tell it to connect to my network it must see it, because the progress bar gets stuck at 28% and says something like "Configuring Device".  I'm at work now and don't remember exactly.  It stays like this for ome time, during which the wired connection doesn't work either.  Then, after some kind of timeout I assume, the blue wireless light goes off, then comes back on, and the process starts over again.  The only way to end it is to quit KNetoworkManager.

---

### Post by Swad on 2006-06-02
Good guide and all very simple compared to to some of the previous beta guides for Dapper.  That said, though, it doesn't actually work for me.  In previous guides it said you couldn't have a protected WAP (ie: encryption) enabled when trying to connect.  Is this still the case?  There's no way I'm taking down our corporate security on our WAP just for this.  This is a step backwards and uncalled for.  ndiswrapper worked great for me in Breezy, but this seems like step backwards.

Honestly, it seems like networking in general with Dapper took a step or two back... or at least does it in totally new ways.  The /etc/network/interfaces file seems to do nothing at all anymore.  Even things such as activating and deactivating interfaces through the gnome Networking GUI only half works.

I'm still going to beat on this a bit more, but I'm about to throw in the towel as things that used to work for me one way before with network suddenly doing their own thing now and I can't seem to control the setup of my networking config.  Wireless acts like it works (looking and TX/RX info on ifconfig) and the settings seem right with iwconfig, but nothing actually works.

UGH!

---

### Post by trivialpackets on 2006-06-02
A big thanks from me.  But a question.  Is there a reason this is better than ndiswrapper?  I had tried to get this going using the wiki and for whatever reason failed on RC.  I did reinstall of LTS after messing with Suse for my father in law, and this worked perfectly.  Great How To.  Now I just need a how to for getting gfxboot to work right.

---

### Post by marlobello on 2006-06-02
This is a great how-to with one major problem. You must have a network connection to get a network connection (apt-get fwcutter). Can you install this package for distro discs?

---

### Post by rjstevens3 on 2006-06-02
$iwconfig
lo...

eth1     IEEE 802.11b/g ESSID:off/any Nickname: "Broadcom 4318"
           Mode: Managed Frequency=2.437 GHz Access Point: Invalid
           Bit Rate=11 Mb/s  Tx-Power=18dBm
           RTS thr:off  Fragment thr:off
           Link Quality:0 Signal level:0 Noise level:0
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
           Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth0.....

---

### Post by unicycler on 2006-06-02
I've been fighting with this for the past two days now, but it is almost all fixed thanks to you. My only remaining problem is that now, every time I restart, I need to sudo modprobe bcm43xx. Is there any way to get this command to run during the boot process?

---

### Post by pspowell on 2006-06-02
**Thanks for a great guide!**

I had just finished setting up NetworkManager not 10 minutes before this showed up on Digg.    Sometimes, as in my case, the NetworkManager install isn't quite flawless, but I found this link which walked me thru the install.  It's on the Ubuntu wiki at :[https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)

---

### Post by bieber on 2006-06-02
Question:  Is there a way I can download the neccesary software on my computer with a wired connection, then put the files on a disk and install on the computer that isn't?  I'd very much like to save the hassle of hauling the wirelessly connected machine and its monitor out into my living room...

---

### Post by System84 on 2006-06-02
I use a 15" PowerBook G4 for work and I was able to successfully get wireless working with the above tutorial.

I did hit a slight snag however, for whatever reason I could not get connected through gnome-network-manager, kwifimanager, or anything like that, but I found a program in the repositories called Wifi-Radar and that allowed me connect with no problems.

There is hope for us Apple users!

---

### Post by jrattner on 2006-06-02
I have followed this guide verbatim for my Broadcom card ( Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Yet nothing has worked.  I'm using the drivers from the website offered in the tutorial.  Can you help me debug, or do anything to take a step in the right direction?

---

### Post by rjstevens3 on 2006-06-02
jrattner, I have the same card and have followed the guide, but i used the drivers from the HP website and then intalled them with wine, to get the correct .sys file. Still doesn't work for me.

-RJ

---

### Post by lynxus on 2006-06-02
PCMCIA Card = wpc54gs

WOW
Thank you for this post!
This needs to be sticky or posted everywhere lol!

Im sure this methoud will probably work with other devices ( As longa s they have the .sys file thingy 

Anywho
THANKS AGAIN!!
MADNESS! PERFECT WOW THANKS lol

Cheers
Graham

---

### Post by Mr Sprout on 2006-06-02
I'm unable to download the community maintained (universe) repositories, some of the files are 404ing. 

[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-powerpc/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-powerpc/Packages.gz:) 404 Not Found
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-powerpc/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-powerpc/Packages.gz:) 404 Not Found

:(

---

### Post by nickm on 2006-06-02
well its not dependant on a specific version of Ndis, as in if you use Ndis and the new version doesnt work with your card...your stuck, but this will work forever.

Also Ndis didnt work for me and this did.

---

### Post by Mr Sprout on 2006-06-02
[QUOTE=nickm]well its not dependant on a specific version of Ndis, as in if you use Ndis and the new version doesnt work with your card...your stuck, but this will work forever.

Also Ndis didnt work for me and this did.[/QUOTE]

I used wifi-radar as mentioned above and that got it working fine. Perhaps you could add it to your main post as an alternative to Network Manager.

Thanks for this tutorial though, it's been a **great** help.

---

### Post by rjstevens3 on 2006-06-02
Quote from the wiki page  > You must remove wifi-radar, as it has a driver conflict with the driver [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f) 

I'm glad you got it working, but it probably should be tested more to see why it worked.

-RJ

---

### Post by strattonbrazil on 2006-06-02
[QUOTE=markmcspadden]A little adjustment...

The command "bcm43xx-fwcutter /home/$USER/Desktop/bcmwl5.sys" creates the firmware files in the directory you are current in...it cannot be assumed that is the "Desktop".

I couldn't figure out why it wasn't creating the files, then I stumbled across them in my "~" directory (where I ran the command). Not a huge thing, but I wouldn't consider myself too much of a linux newbie and it got me.

Other than that...great work...I have wireless without the pain of the ndiswrapper manual install!!! Thanks a ton![/QUOTE]

I think you misread the command.  If you type in the command you have in your post, it will spit out the firmware in the folder you're in.  If you do the command he has,

sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/bcmwl5.sys

you can see the "-w /lib/firmware", which tells the program to put them in /lib/firmware.  So, if you do use the -w, you can assume it goes to /lib/firmware (or where ever you tell it).  If not, you can assume it they files will drop in your current directory.  Did you type it with the -w option and forget to post to the forum with it and it still put the firmware files in your current directory?  Maybe you misspelled in the /lib/firmware directory and the program just spit them out to the current directory.  

Anyways, it was a good article.

---

### Post by stromb on 2006-06-02
Hah, just my luck...seems as though everyone on this thread with a "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" card hasn't been able to get this working :( . I followed this guide to a T and though it seems as though it should be working (laptop light finally coming on and no "hanging" when configuring in the Network Manager"), I get nothing. Here is what I've done...

```
root@lappy:~# lspci | grep Broadcom\ Corporation
0000:06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

**Prerequisite**
**Ubuntu dapper** *check*
**A wireless card that shows up in Ubuntu** *check*
**A driver installation CD (for Windows) OR a driver for your card from the internet** *check* (downloaded from [http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip))
**Access to the Ubuntu Universe Repository** *check*

Did this:

```
root@lappy:~# apt-get install bcm43xx-fwcutter
```

When running:

```
root@lappy:~# bcm43xx-fwcutter -w /lib/firmware ~/Desktop/bcmwl5.sys
```

...I get:

```
*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.*****: But this can be added in the future...
```

...but it still appears to install the files into the firmware directory.

Did this:

```
root@lappy:~# apt-get install network-manager-gnome
```

And after a reboot and even trying this:

```
root@lappy:~# modprobe bcm43xx
```

...I get nothing. I've been playing around with this for hours now and am pretty much stuck. Here is some debug information (eth1 is the wlan card):

```
root@lappy:~# iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"linksys_SES_54484"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

root@lappy:~# dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:14:a5:69:d9:46
Sending on   LPF/eth1/00:14:a5:69:d9:46
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
```

I have reset ALL the router settings so there's no WEP (or any encryption at all), copied/pasted the SSID into the Network Manager and even tried statically assigning the IP address. But still nothing :( . And nothing shows up in the Gnome panel for wifi either. Has anyone gotten this specific card to work??? Any help would be GREATLY appreciated.

Thanks in advance!

---

### Post by kuriharu on 2006-06-02
Looks great, it's the first time I've had an explanation as to why my card can be seen in Ubuntu but never connect.

How do I find the firmware for an Atheros card? Any clues? My connection actually worked once but it hasn't since.

---

### Post by xXx 0wn3d xXx on 2006-06-02
This worked great with my Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) card. And to everyone who is having problems with getting this to work, try this:

> sudo gedit /etc/modprobe.d/blacklist
and add:
> blacklist ndiswrapper
to a new line.

---

### Post by samjam on 2006-06-02
I have a linksys bcm card, I had no trouble getting it to work with native bcm drivers WITHOUT encryption, but who wants to run an open network?

Here's my solution to getting it working on bootup with encryption:

Put this in a file called: /usr/local/bin/bcm43xx
> 
#! /bin/sh -x

: ${IFACE:=${1:-eth1}}

ifconfig $IFACE up
sleep 1
iwconfig $IFACE key off
sleep 3
iwconfig $IFACE essid freeden
sleep 3
iwconfig $IFACE key restricted 0000111111yourkeyinhexhere
sleep 3

and then this fragment in my /etc/network/interfaces

> 
iface eth1 inet dhcp
pre-up /usr/local/bin/bcm43xx
auto eth1

If I specify the essids and keys in my network interfaces it doesn't work
If I try to associate with the essid/AP with encryption on, it always fails, hence the script makes sure it is turned off.
So then I set the essid, wait, and then I set the key and I have to say "restricted"

A most telling message in dmesg or /var/log/messages is one like this:

Jun  2 20:56:23 localhost kernel: [4295485.996000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

the magic "link becomes ready" means essid and encryption all working fine.

---

### Post by chubsmalone on 2006-06-02
Thank God you put this out here.  I have a Motorola WN825G wireless card and these steps worked PERFECTLY!  No more ndiswrapper!!  It "just works" now.  Fantastic.

---

### Post by duelboot on 2006-06-02
nickm,

Thank you so much!  I used this on my oldest computer (a Pent II (266)) with a Motorola PCI wireless card (Broadcom chipset)...this worked perfectly!  No more ndiswrapper and no more driverloader.  

Thanks again.
duel

---

### Post by Brainfish on 2006-06-02
[QUOTE=marlobello]This is a great how-to with one major problem. You must have a network connection to get a network connection (apt-get fwcutter). Can you install this package for distro discs?[/QUOTE]

I'll second this. My only access to the internet is via my wireless connection. The guide assumes that you already have internet access to download & install fwcutter. ](*,)

---

### Post by beck24 on 2006-06-02
Well, the bad news is that I have that same:

> Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)  
card that isn't working for anyone else.  The good news is that it is working for me.  I followed the instructions as given, it gave me the same error:

>  *****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.*****: But this can be added in the future... 
as some other people.  But on reboot it's working perfectly.  Much better than in breezy using ndiswrapper and netapplet.
Thanks a bunch, I hope everyone else can get theirs going...

---

### Post by axiomata on 2006-06-02
I'd love to see a version of this guide for those like who are unable to get an ethernet  internet connection that is required for a number of steps.  Perhaps links to all the programs needed so they can be downloaded through windows or another computer as well as directions as to how to install the programs without the simple apt-get approach.

I know I'd appreciate it very much and I'm sure others may also.

---

### Post by xXx 0wn3d xXx on 2006-06-02
[QUOTE=beck24]Well, the bad news is that I have that same:

 
card that isn't working for anyone else.  The good news is that it is working for me.  I followed the instructions as given, it gave me the same error:

 
as some other people.  But on reboot it's working perfectly.  Much better than in breezy using ndiswrapper and netapplet.
Thanks a bunch, I hope everyone else can get theirs going...[/QUOTE]
That's not an error. The message is saying that most broadcom cards do not currently support microcode11 uploads. I get the same message but my wireless works.

---

### Post by K.Mandla on 2006-06-02
I'm going to hack away at this a little when I get home. I have an Inspiron 600m with the Dell 1370 (4318 chipset), and was having no luck with ndiswrapper or the wiki instructions. It might have been the drivers I downloaded from Dell's support site, though.

The funny thing is, I got the same machine to work with ndiswrapper under Breezy -- not a hitch at all. I have a feeling I'm using a different driver than what I was using in January, though. ](*,)

---

### Post by zahidism on 2006-06-02
it worked beautifully on my 600m w/ a dell wlan 1350 wireless card (BCM4306 chipset).  THANK YOU!!

---

### Post by Noahod on 2006-06-03
I just tried this on a fresh install of kubuntu dapper. I installed knetworkmanager instead of networkmanager gnome, which detected my lan card fine, but not my wireless. 

Then I tried to set up the wireless with wlassistant, and the machine found the network, but hard locked when I tried to connect to it. :-| 

Any ideas?

I did also have the 
*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in the future...

error, but my card is a bcm4306.

---

### Post by chrishack14 on 2006-06-03
I'm having problems similar to what others have been having.  After following the guide in detail, blacklisting ndiswrapper, and removing wifi-radar, I can get my card to come up, but its access point still shows up as "invalid" in iwconfig, ifconfig does not show it as "running", and it will not detect any wireless network.  I have a 4306 model.  Did anybody else with this model do anything extra and have any success?  Any ideas?  Thanks.

---

### Post by Slicedbread on 2006-06-03
After much hassle and many fresh installs I got it to work.
My laptop is a HP ZE2308WM (similar to the Compaq V2000 only with AMD and ATi).

Wireless card: 0000:05:02.0 Network controller:** Broadcom Corporation BCM4318** [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

The driver listed in the first post did not work for me, so I used the one listed in the wiki: [driver]("http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fx-msdownload&blobheadervalue2=inline%3B+filename%3DWMP54GSv1.1_20050428.exe&blobkey=id&blobtable=MungoBlobs&blobwhere=1124848568427&ssbinary=true") and it worked. It's an exe so you need to extract it and it seems to be an older driver but as long as it works...

Other things I tried that may have contributed to it working was **blacklisting ndiswrapper** like MasterChief1234 had suggested and **commenting out the interfaces** (except lo) as described in the [gnome network manager wiki]("https://wiki.ubuntu.com/NetworkManager").

Hope this helps someone. EDIT: I uploaded the actual driver that I used from the wiki. It does work with WPA by the way, although it is limited to 11MBPS (B)

---

### Post by PPower on 2006-06-03
[QUOTE=nickm]How to get a wireless card working in Ubuntu dapper(6.06) with a Broadcom chipset

**Okay so you have a wireless card that shows up in ubuntu but doesnt connect to any wireless network?**

The reason the card shows up but doesnt work is because ubuntu is distributed with its driver (so it can recognize it) but not with its firmware (so it can USE it) for legal reasons.

However you can take the firmware out of the windows drivers and put them into ubuntu and make the card work :mrgreen:
Follow these steps to get your wireless card working under ubuntu dapper 6.06:

To find out if your card has a broadcom chipset run the following command:
```
 lspci | grep Broadcom\ Corporation 
```
If that returns a string of numbers followed by the words Broadcom Corporation and then some more numbers then your in luck!
But if not, try my guide anyway, it cant do any harm and it might work for you, its largly untested for cards other than mine and the success stories posted here so give it a go and see!

Here is my output from doing this:
```
lspci | grep Broadcom\ Corporation
0000:02:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

**Prerequisite**
      Ubuntu dapper
      A wireless card that shows up in Ubuntu
      A driver installation CD (for Windows) OR a driver for your card from the internet
      Access to the Ubuntu Universe Repository

** 1) Ensure you have access to the other ubuntu repos**
follow the intructions on the second heading from this page to ensure you have the universe enabled
[https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)

** 2) Copy your windows driver to your desktop**
You have 3 options here, you can either:
Copy the driver from the CD that came with the Card
Copy it over from your windows partition if you have access to it, it will be located here: /Windows/System32/Drivers/bcmwl5.sys
Obtain the newest version of it from here - [http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip)

** 3) Install bcm43xx-fwcutter**
Open a terminal (dont worry) and type the following:
```
sudo apt-get install bcm43xx-fwcutter
```
It will ask for your password and may ask you to press y to install, but dont worry its really easy

**GUI Alternative:** go to *System* in the top Gnome bar then *Administration* then *Synaptic Package Manager*
From here click *Search* and search for bcm43xx-fwcutter
Right click on its entry in the package window, select *Mark for Installation* and then click apply

** 4) Extract your Cards firmware from the driver**
Open a terminal (dont worry) and type the following:
```
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/bcmwl5.sys
```
This will create lots of new files in the /lib/firmware directory, this is the firmware part of the driver that will make your card work with ubuntu!

***Note* The location and name of the sys file for this command may differ in your case,  if you really get stuck type bcm43xx-fwcutter and then hit space, find your file using the GUI and then drag and drop it into the terminal.**

** 5) Install Network Manager**
I find that this is the best way to manage wireless connections
```
sudo apt-get install network-manager-gnome
```
It may ask for your password and may ask you to press y to install, but dont worry its really easy

** 6) Bookmark this page and Reboot**
Press Ctrl + D and then click on add
Then log out & reboot
Return to this page after logging back in again


** 7) Use your new Wireless connection**
From what i remember network manager should now show up by your clock and display your current connection, if your lucky it will show a series of bars, this means your now using your wireless connection so lucky you!
If it doesnt, right click on it and tick "Enable Wireless" then left click on it 
 and select the wirless network of your choice.

** 8) Give me feedback**
I am happy to revise this guide if people find other ways of doing it or if you find it doesnt work for you and have a solution
I am also happy to create screenshots of each step if i can find hosting for them, i dont like imageshack etc as pictures hosted there expire
Please contact me on Boredklink+forums@gmail.com for either of these

Thanks, i hope this helps...

Thanks to markmcspadden, spd106 and Vaan for giving suggestions/correction which proved invaluable to this guide :)
A BIG thanks to Dipswitch for a second pair of eyes on this Howto and contributing some changes also :)

----------------------------------------------------
For anyone that is having problems, try this:
```
modprobe bcm43xx
```
and reboot[/QUOTE]

Nice guide. It wont work for people without a internet connection though and there is a bug in some cards that requires a extra command. Mine is one (Belkin F5D7000). Here are some ajustments:

1: Everything looks OK but no net connection?
Open a terminal and type iwconfig. Look at the wireless device (it will probably be eth1). Under access point if it says invalid then we need to fix it. To do this type:
sudo iwconfig <device> ap any
and enter your password.
Back in your network management tool disable and enable your card. Now it will work. Note you will have to repeat this every bootup.

2: Getting the firmware without a internet connection: (another method to get the firmware).

You will need another pc and a floppy or something. On the other pc browse to [http://packages.ubuntu.com](http://packages.ubuntu.com) and click Dapper. You will need to find the bcm43xx-fwcutter package. Good luck (I don't renember where it is). Stick the deb on a floppy. Now go to <wherever the special ubuntu script lists the archive> and download <the file that the script lists>. Put that on a floppy.

Back on Linux extract the file and install the fwcutter package. Then finally cut the firmware out of the <file listed in the script> and copy all the fw files to /usr/lib/firmware.

---

### Post by Noahod on 2006-06-03
[QUOTE=Slicedbread]After much hassle and many fresh installs I got it to work.
My laptop is a HP ZE2308WM (similar to the Compaq V2000 only with AMD and ATi).

Wireless card: 0000:05:02.0 Network controller:** Broadcom Corporation BCM4318** [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

The driver listed in the first post did not work for me, so I used the one listed in the wiki: [driver]("http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fx-msdownload&blobheadervalue2=inline%3B+filename%3DWMP54GSv1.1_20050428.exe&blobkey=id&blobtable=MungoBlobs&blobwhere=1124848568427&ssbinary=true") and it worked. It's an exe so you need to extract it and it seems to be an older driver but as long as it works...

Other things I tried that may have contributed to it working was **blacklisting ndiswrapper** like MasterChief1234 had suggested and **commenting out the interfaces** (except lo) as described in the [gnome network manager wiki]("https://wiki.ubuntu.com/NetworkManager").

Hope this helps someone. EDIT: I uploaded the actual driver that I used from the wiki.[/QUOTE]

This made things closer for me, networkmanager detected the network, and started to connect, although it couldn't get an ip. 

Then I ran iwconfig and the system hard locked.. I guess it's just not ready for prime time, back to ndiswrapper I go.

---

### Post by Noahod on 2006-06-03
ok, now I've loaded ndiswrapper, + the driver and I've appended it to /etc/modules

Now when I start up, it is detected by networkmanager, but it won't connect to any of the networks, it just sits there configuring the interface, then goes link is down, and stops. 

However, wlassistant works perfectly, and I can connect... But I want to use networkmanager.. any ideas?

---

### Post by n00bWillingToLearn on 2006-06-03
I would be happy to host the images on my googlepage. That is pretty much all I use my google page for, mirroring stuff. It is pretty much guarenteed to stay up (it's google) and I don't have any other use for the 100 meg.:)

---

### Post by K.Mandla on 2006-06-03
First of all, thanks for the guide. It's been helpful, although it didn't work for my 1370. 

However, I have the wireless more or less working, through ndiswrapper and the driver files listed here. ...

[ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe](ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe)

Unfortunately, that's a Windows installer program, although it really only spits out the Broadcom drivers and installation programs, into a directory you choose. Later on (like tomorrow, after I've slept :D ) I can decompress that file and strip out the .inf and .sys that I used, then post them here.

I hope that's what solved it for me. The problem is that at this point, I've whacked away at this problem so many times that I might have tweaked something completely unrelated. A fresh install is in order, for testing purposes. 

Thanks and cheers.

---

### Post by xiota on 2006-06-03
[COLOR="Gray"]Some of the comments people have typed seem like there is a way to get a list of available ESSIDs.  Is this available in Network Manager somehow, already installed with Ubuntu, or something extra that would need to be installed?  If such a feature were available, would clicking on it automatically configure wireless for connection to the selected access point?  (If that were the case, then it might be a solution to the problem I describe below.)[/COLOR]

I have a Linksys WMP54GS...  Following the steps from this thread, I got the card to work in 802.11b mode, but not in 802.11g mode.  Does anyone know how to get G mode working?

[INDENT]The card functioned properly, most of the time, in Windows 2000.  The drivers glitched or crashed occassionally, which required a reboot.

Signal strength is definitely not a problem.

I tried both the bcmwl5.sys file linked in the original instructions as well as a couple versions provided by Linksys.  The Linksys files gave an error about missing microcode, but with a comment that the missing microcode is not currently used by the drivers.[/INDENT]

I've searched these forums and elsewhere, but have not encountered anything helpful so far.  I'm about a stone's throw away from giving up and trying ndiswrapper.

Thanks for any help anyone can provide.

[COLOR="DarkRed"]Someone typed a comment elsewhere saying that G-mode seems to be not supported at the moment.  People whose cards will detect, but not connect, to a wireless network might be trying to connect to G-only networks.  So some of us may be stuck with ndiswrapper for now.[/COLOR]

---

### Post by SpackMonkeh on 2006-06-03
Has anyone got a 4303 working? I can get it to work but fail to connect to any AP's..
Chaz.

---

### Post by nickm on 2006-06-03
I'm sorry if i dont reply to you, i'v been swamped with replys, 4 pages over night, apparently the digg i made hit front page, good and bad i guess :/

[QUOTE=crag277]I'm using KDE, so I installed knetworkmanager, but still no luck.  It still does not find any availible wireless networks.  However when I manually tell it to connect to my network it must see it, because the progress bar gets stuck at 28% and says something like "Configuring Device".  I'm at work now and don't remember exactly.  It stays like this for ome time, during which the wired connection doesn't work either.  Then, after some kind of timeout I assume, the blue wireless light goes off, then comes back on, and the process starts over again.  The only way to end it is to quit KNetoworkManager.[/QUOTE]

Try wifi radar as suggested further on in this thread, see if you have any luck with that

[QUOTE=rjstevens3]$iwconfig
eth1     IEEE 802.11b/g ESSID:off/any Nickname: "Broadcom 4318"
           Mode: Managed Frequency=2.437 GHz Access Point: Invalid
           Bit Rate=11 Mb/s  Tx-Power=18dBm
           RTS thr:off  Fragment thr:off
           Link Quality:0 Signal level:0 Noise level:0
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
           Tx excessive retries:0 Invalid misc:0 Missed beacon:0
[/QUOTE]
hmm, did you try the modprobe thing?

[QUOTE=unicycler]I've been fighting with this for the past two days now, but it is almost all fixed thanks to you. My only remaining problem is that now, every time I restart, I need to sudo modprobe bcm43xx. Is there any way to get this command to run during the boot process?[/QUOTE]

Yes, modprobe bcm43xx should do it, maybe try it without sudo? thats what i did

[QUOTE=bieber]Question:  Is there a way I can download the neccesary software on my computer with a wired connection, then put the files on a disk and install on the computer that isn't?  I'd very much like to save the hassle of hauling the wirelessly connected machine and its monitor out into my living room...[/QUOTE]
Honestly, i dont know, it might be a good idea to go onto ubuntu Irc or search some more, but in any case, you'd only have to move it once and back to find out if it would work for you :)

[QUOTE=Mr Sprout]I'm unable to download the community maintained (universe) repositories, some of the files are 404ing. 

[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-powerpc/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-powerpc/Packages.gz:) 404 Not Found
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-powerpc/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-powerpc/Packages.gz:) 404 Not Found

:([/QUOTE]

Its okay, the freecontrib ones are not needed to perform this guide

[QUOTE=Mr Sprout]I used wifi-radar as mentioned above and that got it working fine. Perhaps you could add it to your main post as an alternative to Network Manager.

Thanks for this tutorial though, it's been a **great** help.[/QUOTE]

Done :)

---

### Post by SpackMonkeh on 2006-06-03
Hey, This is my card:

0000:02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)

I have got it so it detects and it can see my network however it doesnt actually connect to it and just fails.
It even promts me for my WPA-PSK key...i put it in and it doesnt connect. I've tried without encryption too.
Any ideas?
Thanks,
Chaz.

---

### Post by nickm on 2006-06-03
[QUOTE=SpackMonkeh]Hey, This is my card:

0000:02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)

I have got it so it detects and it can see my network however it doesnt actually connect to it and just fails.
It even promts me for my WPA-PSK key...i put it in and it doesnt connect. I've tried without encryption too.
Any ideas?
Thanks,
Chaz.[/QUOTE]

If your sure your putting your key in properly, there is something you have to put infront of your key to tell the router wether you wrote the key as plantext or HEX but i'v never used encryption so i dont know what it is but i found this written by jonny in another wirless post
```
8. BE CAREFUL entering your WEP key, if you're using one. You're expected to enter this in hexadecimal form; if you don't speak hex, prefix your key with s:
```

But if you've tried without encryption too then check your router settings to see if they allow 802.11B connections

people have been saying they have been having trouble with that card though :-k

---

### Post by Kawayanan on 2006-06-03
ok, I have an interesting tale :p 

First of all, I have a Compaq Presario V2401CL which has a Broadcom BCM4318.  Here is exactly what it reports:

> 0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

As soon as 6.06 came out, I first tried kubuntu.  I followed the instructions in this howto and it worked like a charm.  The only difference is I did not do the last step of installing the gnome network manager.  There was already a KDE Wireless Assistant loaded (wlassistant 0.5.5-0).  Using the wireless assistant, I see the networks and can connect without a problem.  It not automatic, it seems you have to manualy connect each time (though it does remember the settings).

After playing around for a bit, I decided that I actually wanted to gnome instead of KDE.  To keep everything clean (and since I hadn't done any other customization), I just went with a clean ubuntu install.  Once again, I followed this howto.  Everything seemed to work well.  After installing the gnome network manager and restarting, I could see the wireless networks that were available, but I cannot get any to connect.  Mine uses WEP, but I cannot get it to connect without WEP either.  As I mentioned, I can see the network.  When I enter the WEP key and settings it just sits for a long time trying to connect (when I mouse over the icon I get a bubble that says it is waiting for a network key from my wireless network).  I am sure my WEP key is correct and that I have the other correct settings (its open, not shared key).

To test this a bit and make sure something strange had not happened, I went back and did a clean install of kubuntu.  Once again, it connects easily and I have wireless access.  I did a second clean install of ubuntu and run into the same problem (see the wireless networks, but cannot connect).

I would rather used ubuntu with the gnome network manager if possible.  The KDE wireless assistant requires manual connecting and that can be a pain when moving between different locations with multiple wireless networks and wired networks.  I like the idea of the user level daemon that tries to keep you connected.  I just can't seem to get it to work though :confused: I works great for the wired network.  After trying to connect the wireless as soon as I plug in the ethernet cable it recognized it, activates it, and get an IP (DHCP).  Anyone have any ideas what wrong with the wireless?  Is this a software problem with the gnome network manager?

Thanks for the help.

Kawayanan

---

### Post by nickm on 2006-06-03
There is just network-manager as well as network-manager-gnome i dont know what that will do for Kde or another DE

---

### Post by DrkAngel on 2006-06-03
[QUOTE=unicycler]I've been fighting with this for the past two days now, but it is almost all fixed thanks to you. My only remaining problem is that now, every time I restart, I need to sudo modprobe bcm43xx. Is there any way to get this command to run during the boot process?[/QUOTE]
I added the following to my /etc/network/interfaces:

auto eth0
iface eth0 inet dhcp

This causes the wireless card to activate when Ubuntu configures the network interfaces at boot.  Of course, you'd want to change eth0 to whatever device your wireless card is configured as.  This setting is compatible with Network Manager, but may cause a delay during boot (I haven't noticed the delay with BCM43xx, but the delay was quite noticable with Ndiswrapper).  Good Luck!

-Drk^Angel-

---

### Post by nickm on 2006-06-03
[QUOTE=DrkAngel]I added the following to my /etc/network/interfaces:

auto eth0
iface eth0 inet dhcp

This causes the wireless card to activate when Ubuntu configures the network connections at boot.  Of course, you'd want to change eth0 to whatever device your wireless card is configured as.  This setting is compatible with Network Manager, but may cause a delay during boot (I haven't noticed the delay with BCM43xx, but the delay was quite noticable with Ndiswrapper).  Good Luck!

-Drk^Angel-[/QUOTE]

doesnt the BCM43xx module have to be loaded first, thats what his problem is isn't it? maybe i misunderstood.

---

### Post by jobyjoby on 2006-06-03
I am also trying to get the BCM4318 to actually connect to a wireless network after following all of the steps.  This has been a very helpful topic though!

---

### Post by DrkAngel on 2006-06-03
[QUOTE=nickm]doesnt the BCM43xx module have to be loaded first, thats what his problem is isn't it? maybe i misunderstood.[/QUOTE]
The bcm43xx module is loaded by modprobe.d, but on my system, the card isn't activated until after Network Manager loads.  I would have to modprobe bcm43xx once I logged in then  restart Network Manager to get it to recognise the wireless.  Wasn't sure if this was the same issue unicycler was having, so I thought I'd post my solution just in case it could help.

-Drk^Angel-

---

### Post by btboudreaux on 2006-06-03
Im also having trouble with bcm4318, I followed the directions exactly and still nothing. This problem is the only thing keeping me from switching over to linux on my laptop. I couldn't get it to work with any Ubuntu release.

---

### Post by nickm on 2006-06-03
> The bcm43xx module is loaded by modprobe.d, but on my system, the card isn't activated until after Network Manager loads. I would have to modprobe bcm43xx once I logged in then restart Network Manager to get it to recognise the wireless. Wasn't sure if this was the same issue unicycler was having, so I thought I'd post my solution just in case it could help.

-Drk^Angel-

Oh okay, i guess annother (but lesser) fix would be to add the instructions you have to do to the sessions program if you dont want to edit files etc

---

### Post by Slicedbread on 2006-06-03
I think the reason that a lot of people are not getting it to install despite having the exact sam cards is due to some configurations errors. Before the fresh install different methods did:

It could see wireless networks but not connect.
It would connect automatically to an unsecured network, but not obtain an ip.
It would require modprobe to start up but not do anything.
NetworkManager would not show wireless connection even though wireless was on.
ndiswrapper didnt work at all.

As far as I have found, the network interfaces file does nothing. I have them all commented out and it still works.

I would suggest if you can to do a clean install or find some way to delete the config files.

---

### Post by nickm on 2006-06-03
yes, thats right network manager does not use the traditional config files, looking at my networking through system > administration > networking shows all my netowork cards to be disabled.

If/Iw config show accurate stats but making changes by these two commands dont effect the network manager settings.

---

### Post by bieber on 2006-06-03
Is there a similar procedure I could use to get my Linksys WUSB54G working?  It does the same thing the Broadcom cards do without firmware installed, that is, showing up in Networking but not working...

---

### Post by jobyjoby on 2006-06-03
Hello again!  I fluked out and mine is working now.  This was the last/main step I followed from the guide slicedbread linked to:
> Gnome

Go to System -> Preferences -> Sessions In the Startup Programs tab, click Add type "nm-applet", click OK. log out of your gnome session, and log back in again. 
Cheers!

[QUOTE=jobyjoby]I am also trying to get the BCM4318 to actually connect to a wireless network after following all of the steps.[/QUOTE]

---

### Post by FullMetlaMonkey on 2006-06-03
Thnak you so much for posting suck a great guide! I've been trying to get my Linksys wmp54gs to work with Ubuntu for an insane amount of time!

---

### Post by nickm on 2006-06-03
AHH! i assumed NM added itself to this list, NEVER ASSUME :p i'll put a thing on my guide about that, thanks!
Great that you got it working

---

### Post by DrkAngel on 2006-06-03
Okay... I completely removed NetworkManager, and installed it again, and now I don't need the extra lines in my /etc/network/interfaces.  Must've been something I messed up in the configs way back when I first installed NetworkManager with Ndiswrapper.  Thanks.

-Drk^Angel-

---

### Post by zahidism on 2006-06-03
err...so my wireless was shifty as in it would stop working periodically...so i decided to just up and remove network manager.  now my wireless and ethernet are screwed.  any suggestions?  i didnt remove the bcm43xx fwcutter.  and i tried sudo apt-get install network-manager-gnome but w/o internet connection im convinced it wont do anything.  any ideas?

---

### Post by rjstevens3 on 2006-06-03
[QUOTE=Slicedbread]After much hassle and many fresh installs I got it to work.
My laptop is a HP ZE2308WM (similar to the Compaq V2000 only with AMD and ATi).

Wireless card: 0000:05:02.0 Network controller:** Broadcom Corporation BCM4318** [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

The driver listed in the first post did not work for me, so I used the one listed in the wiki: [driver]("http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fx-msdownload&blobheadervalue2=inline%3B+filename%3DWMP54GSv1.1_20050428.exe&blobkey=id&blobtable=MungoBlobs&blobwhere=1124848568427&ssbinary=true") and it worked. It's an exe so you need to extract it and it seems to be an older driver but as long as it works...

Other things I tried that may have contributed to it working was **blacklisting ndiswrapper** like MasterChief1234 had suggested and **commenting out the interfaces** (except lo) as described in the [gnome network manager wiki]("https://wiki.ubuntu.com/NetworkManager").

Hope this helps someone. EDIT: I uploaded the actual driver that I used from the wiki. It does work with WPA by the way, although it is limited to 11MBPS (B)[/QUOTE]

Are you running i386 or amd_64? I keep getting the feeling that i'm using the wrong firmware files for my card. 

I have a turion 64 in my laptop, but i'm running ubuntu i386. I've tried many different windows drivers without any luck. Does anyone know if the different drivers from different makers matter? (i have an HP dv8000 with wifi that only sometimes worked in windows...)

I'm going to try reloading nm_applet after setting iwconfig ap any and see if that works. Thats the only thing i haven't tried yet.

-RJ

---

### Post by n00bWillingToLearn on 2006-06-03
I followed your howto exactly on my 17'' powerbook with airport extreme and it workes!

I used the link you gave to download the drivers.


I used Network manager at first but while -Network Manager- saw only my ethernet interface, network-admin (System -> administration -> networking) connected fine since I had already manually entered the ESSID and when I installed wifi-radar ( after removing network manager ) it indeed did work and actually found more wireless networks than OSx could.:D

---

### Post by nickm on 2006-06-03
[QUOTE=zahidism]err...so my wireless was shifty as in it would stop working periodically...so i decided to just up and remove network manager.  now my wireless and ethernet are screwed.  any suggestions?  i didnt remove the bcm43xx fwcutter.  and i tried sudo apt-get install network-manager-gnome but w/o internet connection im convinced it wont do anything.  any ideas?[/QUOTE]

:-k can you still set the ethernet up using system > administration > networking?
if you can just use that with your ethernet or connect to the internet and re-do this guide to get your wireless working again

Fwcutter is only used during the guide to cut up the sys file, and seing as you already have the firmware in the right folder its no longer needed

Read one of the bullet points at the top of this guide about being offline, see if that gives you any further help.

---

### Post by nickm on 2006-06-03
[QUOTE=n00bWillingToLearn]I followed your howto exactly on my 17'' powerbook with airport extreme and it workes!

I used the link you gave to download the drivers.


I used Network manager at first but while -Network Manager- saw only my ethernet interface, network-admin (System -> administration -> networking) connected fine since I had already manually entered the ESSID and when I installed wifi-radar ( after removing network manager ) it indeed did work and actually found more wireless networks than OSx could.:D[/QUOTE]

Hey thats great n00bWillingToLearn, thanks for your offer of image hosting too, i sent you a reply if your still here.

---

### Post by Slicedbread on 2006-06-03
[QUOTE=rjstevens3]Are you running i386 or amd_64? I keep getting the feeling that i'm using the wrong firmware files for my card. 

I have a turion 64 in my laptop, but i'm running ubuntu i386. I've tried many different windows drivers without any luck. Does anyone know if the different drivers from different makers matter? (i have an HP dv8000 with wifi that only sometimes worked in windows...)

I'm going to try reloading nm_applet after setting iwconfig ap any and see if that works. Thats the only thing i haven't tried yet.

-RJ[/QUOTE]

Im using the i386 dapper 6.06, It doesnt really make sense though, because the ones  I use in windows from HP dont work nor do the ones in the main link. Each manufacturer must have modified the firmware or something like that.

---

### Post by n00bWillingToLearn on 2006-06-03
[QUOTE=nickm]Hey thats great n00bWillingToLearn, thanks for your offer of image hosting too, i sent you a reply if your still here.[/QUOTE]

I got the reply and BTW I think that this HowTo is easier / more updated to Dapper than the one in the wiki for airPort Extreme cards speifically so if others are also successfull mabe it should be updated.

[https://wiki.ubuntu.com/WifiDocs/Device/AirportExtreme](https://wiki.ubuntu.com/WifiDocs/Device/AirportExtreme)

---

### Post by Kawayanan on 2006-06-03
[QUOTE=Kawayanan]ok, I have an interesting tale :p 

First of all, I have a Compaq Presario V2401CL which has a Broadcom BCM4318.  Here is exactly what it reports:



As soon as 6.06 came out, I first tried kubuntu.  I followed the instructions in this howto and it worked like a charm.  The only difference is I did not do the last step of installing the gnome network manager.  There was already a KDE Wireless Assistant loaded (wlassistant 0.5.5-0).  Using the wireless assistant, I see the networks and can connect without a problem.  It not automatic, it seems you have to manualy connect each time (though it does remember the settings).

After playing around for a bit, I decided that I actually wanted to gnome instead of KDE.  To keep everything clean (and since I hadn't done any other customization), I just went with a clean ubuntu install.  Once again, I followed this howto.  Everything seemed to work well.  After installing the gnome network manager and restarting, I could see the wireless networks that were available, but I cannot get any to connect.  Mine uses WEP, but I cannot get it to connect without WEP either.  As I mentioned, I can see the network.  When I enter the WEP key and settings it just sits for a long time trying to connect (when I mouse over the icon I get a bubble that says it is waiting for a network key from my wireless network).  I am sure my WEP key is correct and that I have the other correct settings (its open, not shared key).

To test this a bit and make sure something strange had not happened, I went back and did a clean install of kubuntu.  Once again, it connects easily and I have wireless access.  I did a second clean install of ubuntu and run into the same problem (see the wireless networks, but cannot connect).

I would rather used ubuntu with the gnome network manager if possible.  The KDE wireless assistant requires manual connecting and that can be a pain when moving between different locations with multiple wireless networks and wired networks.  I like the idea of the user level daemon that tries to keep you connected.  I just can't seem to get it to work though :confused: I works great for the wired network.  After trying to connect the wireless as soon as I plug in the ethernet cable it recognized it, activates it, and get an IP (DHCP).  Anyone have any ideas what wrong with the wireless?  Is this a software problem with the gnome network manager?

Thanks for the help.

Kawayanan[/QUOTE]

[QUOTE=nickm]There is just network-manager as well as network-manager-gnome i dont know what that will do for Kde or another DE[/QUOTE]

I understand that.  As far as network-manager is the only daemon based "auto-connect" type of network manager available.  network-manager-gnome is only a graphical frontend for network-manager.  KDE does have a frontend called knetworkmanager.  It doens't work for me either :( 

I am back to using the more manual approach that worked.  I am back to kubuntu and am using Wireless Assistant (wlassistant).  I have to manually logon to each wireless network, but it works.  The knetworkmanager (KDE frontend to network-manager) had the same problems as under gnome - the card seems to work, network-manager is started and running, I can see the available wireless networks, but when I try to connect to any (WEP or not) it just sits and never connects.  From reading in this thread and others, it seems that there are a reasonable number of people haveing this type of problem.

I read through everything I can find about network-manager (doc's, man, web, etc.).  I am looking for a way to get something like a verbose terminal output, but can't find anything like that.  I don't know where to find any log messages for it either.  Since it seems to almost work, I would like to see what part of connecting to the network is not working.  I works great for wired, and can detect the wireless networks, it just hangs somewhere during the attempt to connect.  If anyone how to see exactly what network-manager is trying to do as it connects, let me know.  I will keep people posted on what I find.

Thanks btw for this howto :) I got me connected and close enough to network-manager working to smell it :p 

Kawayanan

---

### Post by tactus on 2006-06-03
Amazing, it looks like someone is online at last. Thanks for a very good tutorial nickm. I am new to Linux and had no problems follow it.

I have the same chipset as (you) nickm, BCM4306, but I am on a PowerBook G4 12". I tried the automatic firmware installer in one of the latest Ubuntu flight versions and went with Network Manager. It't didn't work for me back then, but I could see the available networks. So this time I just went straight for Wifi-radar instead, and lo and behold, it worked. Thanks for the Wifi-radar tip System84, that might have saved me for some headache. :)

One issue I have is that I can't see how good the signal is. All the networks shows either zero or full spike all the time (depending on app), but I asume that's driver related.

Here is a question btw: Can I use my BCM43xx and Wifi-radar on WPA networks? I usually have WPA enabled.

---

### Post by tarr2468 on 2006-06-03
I am getting so close to having this work.  I can see my netowork, but I cannot connect.  I even turned off encryption, but still no luck. Any one have any suggestions?

---

### Post by Riona on 2006-06-03
This didn't work for me. Followed the instructions. I see the network conections and the wireless connection options. However when i try to connect to my wireless router a linksys I get nothing. Tried it with no encyption and with encryption as well. My laptop a dell inspiron b130 will not connect wireless. I also set the security to mix mode and have my ssid broadcasted.
Here are a few outputs from the terminal. I have no idea what to try next. 
eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: 00:0F:B5:6F:E6:F8
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: 00:0F:B5:6F:E6:F8
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
--------------------
  lspci | grep Broadcom\ Corporation
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by ????? on 2006-06-03
This guide got my card working! But I have 2 questions:


1. Is it possible to get 802.11g working? (I prefer 54 mbps over 11 mbps)
2. Can I use WPA-PSK on this?

---

### Post by chronusdark on 2006-06-03
i agree i would like to get G support

---

### Post by Slicedbread on 2006-06-03
[QUOTE=?????]This guide got my card working! But I have 2 questions:


1. Is it possible to get 802.11g working? (I prefer 54 mbps over 11 mbps)
2. Can I use WPA-PSK on this?[/QUOTE]


You can use WPA and WPA2 (if your card supports it), I dont think G is supported with the ubuntu driver but you wont see a difference unless your transferring large files over a network or able to download files at over 1300Kbps.

---

### Post by chronusdark on 2006-06-03
i did this command 

```
iwconfig eth2 rate 54M
```

and it seems to work but i need to restart to check if networkmanager sees the change

ps replace eth2 with your wireless interface

---

### Post by MrObvious on 2006-06-03
Well the code worked chronusdark :). I've been having problems but somehow I got it to work using the alternate driver someone else pointed out I think for the 4318 chipset (try that if you have problems). Thanks to all who have worked hard to make this thread usable for others. It is much appreciated.

---

### Post by zahidism on 2006-06-03
phew, we are back online...thanks again.   this is great because I'm such a newb and i dreaded ndiswrapper since 5.10 (i broke it so i uninstalled ubuntu and went back to windows).  how do i get the following type of output within the terminal?

> eth1 IEEE 802.11b/g ESSIDff/any Nickname:"Broadcom 4318"
Mode:Managed Frequency=2.484 GHz Access Point: 00:0F:B5:6F:E6:F8
Bit Rate=11 Mb/s Tx-Power=18 dBm
RTS thrff Fragment thrff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


edit* nvm, figured it out...

---

### Post by trbloomer on 2006-06-04
Wow!

Works like a charm for me. I'm a linux noobe started with debian etch couldn't get ndiswrapper to work with my WPA setup at home. On a whim I downloaded ubuntu 6.06 LTS and found this thread and in about 10.5 secs was up and running with my Motorola 825g card. 

Now if we could get the full 54 speed with fall back and oh a working signal indicator but thats just icing on the cake for now.

Thank you.

---

### Post by piracyrocks on 2006-06-04
i have done this tutorial straight through and followed the extra stuff and i cant get my 4318 card to work with y wireless network...this is kind of troublesome...i wish to switch to linux but i will stick with m$ if i cant get wirless to work...its kind of neccessary

---

### Post by DJLC on 2006-06-04
I tried this, and now I can't really do anything. Upon boot (from both the HD AND a LiveCD), I get 3 errors. After closing them all, all I have is a dark brown/red background with a cursor - all I can do is move the cursor around.

In chronological order:
There was a problem registering the panel with the bonobo-activation server. The error code is: 3. The panel will now exit.

There was an error starting the GNOME Settings Daemon. Some things, such as sound, themes, or background settings may not work correctly. The Settings Daemon restarted too many times. The last error message was: System Exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0 GNOME will still try to restart the settings daemon the next time you log in.

Nautilus can't be used now, due to an unexpected error. (Under the Show More Details arrow is the following) Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server.

Three questions:
1) What, exactly, is the issue?
2) What did I do wrong, and is there anything I can do to correct it w/o reinstalling?
3) If I must reinstall, how can I do this if I can't boot from a LiveCD?

I'm on a Powerbook G3 Lombard. The only thing I did different was that I installed Network Manager BEFORE I installed the card firmware. My "Airport card" is a PCMCIA wireless card w/ Broadcom chipset - it was previously recognized by OS X as an AirPort card.

---

### Post by bluezdood on 2006-06-04
Ok, well this did work for me at the office since they have B and G enabled on the routers around campus.  However at home I've only got G available and hence it doesn't connect to the Netgear router I have even though it can detect the network.  Since I would rather use G anyway, how can I enable this?  The "iwconfig eth2 rate 54M" command didn't work for me.  What I get is

Error for wireless request "Set Bit Rate" (8B20) :
  SET failed on device eth1 ; Operation not permitted.

Anyone know how to fix this? ](*,)

---

### Post by Slicedbread on 2006-06-04
> **bluezdood]Ok, well this did work for me at the office since they have B and G enabled on the routers around campus.  However at home I've only got G available and hence it doesn't connect to the Netgear router I have even though it can detect the network.  Since I would rather use G anyway, how can I enable this?  The "iwconfig eth2 rate 54M" command didn't work for me.  What I get is

Error for wireless request "Set Bit Rate" (8B20) :
  SET failed on device eth1  said:**
> (*,)

Use the sudo command in front. What router do you have? It seems strange that it is able to support 54 but not 11. I doubt that will change much because as far as I can tell gnome network manager doesnt reference /etc/network/interfaces at all.

---

### Post by joergenlie on 2006-06-04
Thanks! My wireless works like a charm, but. There's one but. Is there anyway at all to get this to connect at boot up? Theres too much for my wife to modprobe and use network manager. She only uses the internet. I've tried playing with networking interfaces but still I can't get it to load at boot up.

I have a broadcom 4306 card.

Anyone with a solution to this?


Jørgen

---

### Post by Noahod on 2006-06-04
Mine finally sorted itself out. Works now with ndiswrapper and networkmanager :)

---

### Post by PPower on 2006-06-04
Can I please tell everybody this message from the people at #bcm-users:

When Ubuntu upgrade to a new kernel (and thus a new version of the bcm module) you MUST NOT use the driver supplied on this thread. It is IMPERATIVE that you use wl_apsta.o (see the wiki article or log on to #bcm-users OR run ubuntus script). This new module + driver fixes the invalid AP bug. I have sent a PM to whatshisname (the starter of this thread, sorry i forgot!) as it is a important issue.

---

### Post by PPower on 2006-06-04
[QUOTE=joergenlie]Thanks! My wireless works like a charm, but. There's one but. Is there anyway at all to get this to connect at boot up? Theres too much for my wife to modprobe and use network manager. She only uses the internet. I've tried playing with networking interfaces but still I can't get it to load at boot up.

I have a broadcom 4306 card.

Anyone with a solution to this?


Jørgen[/QUOTE]
It should as long as the bcm driver is not blacklisted. As soon as you boot up type dmesg. Do you see anything related to the bcm driver? It should say something similar to this:
[4294686.432000] bcm43xx driver

Are you using the driver on this thread. It works like a breeze for me. Disable the module and delete all the fw files out of /lib/firmware. Then fwcutter the file on the thread **unzip it first** and ignore the microcode11.fw error. Copy all files to /lib/firmware. Reboot and be on your way to networking heaven!

---

### Post by joergenlie on 2006-06-04
dmesg lists the bcm driver and I have used the driver from this thread, but still it will not connect?

And how do I disable the module?


Jørgen

---

### Post by PPower on 2006-06-04
[QUOTE=joergenlie]dmesg lists the bcm driver and I have used the driver from this thread, but still it will not connect?

And how do I disable the module?


Jørgen[/QUOTE]
You want to turn off bcm and use ndiswrapper? Simpy edit /etc/modprobe.d/interfaces and add blacklist bcm43xx and reboot your computer.

---

### Post by joergenlie on 2006-06-04
Ok. Is it better to use ndiswrapper? I get my wireless to connect and it works fine, but thats just after modprobing it and restart it in network-manager. The only problem is that it doesnt connect at boot up so I have to ifconfig up, depmod -a, update-modules and modprobe 43xx to get connection.

Jørgen

---

### Post by nickm on 2006-06-04
[QUOTE=joergenlie]Ok. Is it better to use ndiswrapper? I get my wireless to connect and it works fine, but thats just after modprobing it and restart it in network-manager. The only problem is that it doesnt connect at boot up so I have to ifconfig up, depmod -a, update-modules and modprobe 43xx to get connection.

Jørgen[/QUOTE]

Theirs a note about this in the guide about checking for nm-applett in the sessions, maybe you could add your modprobe stuff also?

---

### Post by fletch on 2006-06-04
I have the "AirForce One rev 02" broadcom card, and it took most of the tricks displayed on this page to get it working. Hibernation finally works for me in Dapper (didnt in Hoary), but powering back up my v2000, my wireless isn't working. Its active in the Network Manager panel, blue LED is glowing, but no such luck. Anybody experience this problem?

(EDIT: Wireless works fine with a simple reboot, just not coming back out of hibernation, I re-read this and figured it might confuse some people.)

Also, on a side note, how well does Ubuntu deal with PCMCIA wireless cards?? I would like to test out some of the wireless tools offered within the package database in Synaptics, such as kismet or airsnort.

I tried setting up kismet with my broadcom, but it said it only has "experimental" support with the broadcom, but speaks about the other workaround "berlios" driver I've read about back when I was working with ndiswrapper and 5.10 Ubuntu.

---

### Post by SuicideInvoice on 2006-06-04
Nickm, you are my hero.  I'm still somewhat new to Linux and I was fighting with ndiswrapper on 5.10 and after upgrading to Dapper and using your how to, my belkin 54g F5D7010 (BCM4306) finally works.

Next up is to see how well the new 'experimental' Broadcom support for Kismet works.  No high hopes there though.

Thanks again

---

### Post by grsing on 2006-06-04
THANK YOU!  I've been futzing with making wireless work on dapper for several days now (not straight, but many hours still), and this finally did it.  Awesome work.

Same chipset and all as you, so of course it should work.  Just wish I'd seen this when it was created.

---

### Post by nickm on 2006-06-04
[QUOTE=grsing]THANK YOU!  I've been futzing with making wireless work on dapper for several days now (not straight, but many hours still), and this finally did it.  Awesome work.

Same chipset and all as you, so of course it should work.  Just wish I'd seen this when it was created.[/QUOTE]

[QUOTE=SuicideInvoice]Nickm, you are my hero.  I'm still somewhat new to Linux and I was fighting with ndiswrapper on 5.10 and after upgrading to Dapper and using your how to, my belkin 54g F5D7010 (BCM4306) finally works.

Next up is to see how well the new 'experimental' Broadcom support for Kismet works.  No high hopes there though.

Thanks again[/QUOTE]

Hey i'm glad it works for both of you, iv been in both of your positions and i know how fustrating it is, and also how great it is when you can take the Ethernet wire out, hit "Home" in firefox and have google come up anyway :-D

On a side note, does anyone know what it means when your title is changed to "Spilled the beans" as mine was a few days ago?

---

### Post by ????? on 2006-06-04
I'm unsure about the beans.. I think it has to do with your post rate. And i'll try the iwconfig one I boot into Ubuntu which is right after I post this

---

### Post by nickm on 2006-06-04
beat you to it, it didnt work for me :) i think its because its editing the conf files that network manager doesnt use..so it wont have any effect, i dont know what wifi-radar uses though..

As for the title thing, i thought it maybe had something to do with this guide appearing on digg.com and getting 13,000 page views over a few hours or something "spilled the beans" "told everyone" i dunno

---

### Post by slakkie on 2006-06-04
Thanks for the HOWTO, got the wireless up pretty quick (without encryption)
.
Got it working without encryption and with encryption (WPA).
I'm using the gnome-network manager, which is described in the HOWTO. And I'm using wpasupplicant in order to get it working with WPA.

Failover from Wired to wireless isn't that good (non existent tbh)... Hopefully I will get this working somewhere this week(end).

---

### Post by drachir on 2006-06-04
I finally found the time to try this out. I Have a Compaq Presario V2000 Turion64. I have been ](*,) over this since 5.10 and thanks to :KS nickm :KS I am doing a post from a new install of 6.06 with my Broadcom 4318 up and running. 

Thanks nickm for you time and help with this. You have made lots of people very happy.

---

### Post by piracyrocks on 2006-06-04
ok drachir...did u do this tutorial straight through?...cus i did it straight through from a clean install of 6.06 and my wireless still isnt working....maybe its cus i have an athlon amd 64?...woudl that make a difference?

---

### Post by nickm on 2006-06-04
maybe piracyrocks, i dont know if there is a special 64bit driver for the card you have? are you using the X86 or 64 bit version of ubuntu?

---

### Post by piracyrocks on 2006-06-04
64 bit version

---

### Post by Cenotaph on 2006-06-04
I can't get it to work. I have the same card that is causing lots of problems.

i did everything, but i cant even check for available networks at this point. I never could get wireless to work here, but on 5.10 with ndiswrapper i could at least get it to check for available networks. what could be wrong here?

---

### Post by nickm on 2006-06-04
Okay, for everyone who couldnt get this to work PLEASE try it again with the revised instructions, i have added a new driver that is reccomended for use so go over it again before posting a "mine doesnt work" thankyou

---

### Post by Slicedbread on 2006-06-04
piracyrocks did you happen to mess with the built in network manager that gnome has? That may be your problem. 

I was doing a little experimenting when my wireless BCM4318 card was working and found that trying to configure my wireless card in and activating it would completely fudge the wireless system over. Even though I have not changed anything and disabled the cards in the built in network manager it will not detect any networks, even though the wifi light is on. This leads me to believe that there is some configuration bug in Dapper's built in network manager. 

I have the HP version of your laptop and I can tell you that a fresh install with no messing around will get it working fine.

---

### Post by Cenotaph on 2006-06-04
[QUOTE=nickm]Okay, for everyone who couldnt get this to work PLEASE try it again with the revised instructions, i have added a new driver that is reccomended for use so go over it again before posting a "mine doesnt work" thankyou[/QUOTE]
that driver worked like a charm :D

thank you :)

guess i should change my vote now hehe

---

### Post by piracyrocks on 2006-06-04
im about to re-try this whole thing..i just did a fresh install of 6.06 on my computer...here goes nothing  *crosses fingers*

---

### Post by nickm on 2006-06-04
[QUOTE=piracyrocks]im about to re-try this whole thing..i just did a fresh install of 6.06 on my computer...here goes nothing  *crosses fingers*[/QUOTE]

good luck :)

---

### Post by piracyrocks on 2006-06-04
so uh...i just did this whole thing with the new reccomended driver thing...the wl_apsta.o one...and it still doesnt work....not only can i not connect to my wireless network...but no wireless networks show up to connect to...none ever have...so im not that surprised...but im a bit dissapointed because that other guy with the same pc as me got this to work...what gives?

---

### Post by KiLLeR_WoMBaT on 2006-06-04
Sorry...wrong thread!

---

### Post by nickm on 2006-06-04
[QUOTE=KiLLeR_WoMBaT]No matter what I try...the only way to NOT get a blank screen upon login is to use VESA.  I have tried everything in this thread...both methods of installing ATI's driver and still Dapper will not get past the login screen.

If I try to use ATI or FGLRX with dpkg-reconfigure xserver-xorg, everything goes fine and upon reboot I have two drum sounds (this is how I know it won't work) and everything looks fine.  I put in the username and password...everything looks good but just the cursor and a blank (default brown) screen.  Nothing...I've let it sit for hours and nothing.  It will let me ctrl+alt+bkspc and get out to the login screen again.

I have no DRI with VESA of course either; it still says MESA.

What should I post to help diagnose this problem?  I upgraded from breezy...not a new install.[/QUOTE]

what?

---

### Post by piracyrocks on 2006-06-04
does anyone have any help for me?...i got that card that is the one people seem to have problems with and it also has been said that some got it to work...

bcm4318

---

### Post by nickm on 2006-06-04
[QUOTE=piracyrocks]so uh...i just did this whole thing with the new reccomended driver thing...the wl_apsta.o one...and it still doesnt work....not only can i not connect to my wireless network...but no wireless networks show up to connect to...none ever have...so im not that surprised...but im a bit dissapointed because that other guy with the same pc as me got this to work...what gives?[/QUOTE]

Maybe your using the 64 bit and he isnt?
 thats all i can think of, maybe ask him what driver he used, or even ask him to emal you the EXACT firmware he's using as a gzip of files that you can put in place?

---

### Post by piracyrocks on 2006-06-04
darn...i really wanna try out linux as my full-time OS ...but im thnkng of ditching it now just cus of this...i really dont want to have to do that.... :-(

---

### Post by Cenotaph on 2006-06-04
I should note that i have put the firmware into the /lib/firmware/2.6.15-23-386 folder, not the the /lib/firmware, although it shouldnt really matter.

and i'm using 32bits version.

---

### Post by nickm on 2006-06-04
[QUOTE=Cenotaph]I should note that i have put the firmware into the /lib/firmware/2.6.15-23-386 folder, not the the /lib/firmware, although it shouldnt really matter.

and i'm using 32bits version.[/QUOTE]


Really? i found the opposite :neutral:

---

### Post by piracyrocks on 2006-06-04
even though i have an athlon amd 64 bit processor...will the 32 bits version of ubuntu run on it?...cus if thats all i need to do to get this to work i will do it by all means

---

### Post by piracyrocks on 2006-06-04
whoa...i just looked at my stuff and most of my other firmware is in that folder inside firmware as well....my computer says i dont have the rights to move all the other firmware into that folder...how do i do this?...i want to try putting it in that other folder to see if it will work

do i simply just re-extract the wl_apsta.o stuff into that other folder?

---

### Post by Cenotaph on 2006-06-04
yes, it would run the 32bits version. i actually have a 64bit processor myself, but im still attached to the 32bits coz of driver issues that are somewhat usual.

you can use sudo to move the files to that other folder if you wish to try it

do something like "sudo mv /lib/firmware/bcm* /lib/firmware/(whatever the folder name is)" it should be different than mine since ur using the 64bits version

---

### Post by piracyrocks on 2006-06-04
what do i type to move them?...im new with linux

---

### Post by piracyrocks on 2006-06-04
thanks..it moved em...im gonna reboot and see what happens....if this doesnt work i will just download the 32 bit version and run that with all of this since u got it to work that way....here goes nothing *crosses fingers*

---

### Post by Cenotaph on 2006-06-04
i told ya

mv - move :)

cp - copy

sudo - lets you execute actions that need administrator privileges, you need to put your password, and this is really your pass, not the root password :)

---

### Post by nickm on 2006-06-04
[QUOTE=piracyrocks]what do i type to move them?...im new with linux[/QUOTE]
yes, do what cenotaph is suggesting OR  take a look at step 4B on the guide, i added it for you, just take note of the name of the folder you want to move them to and apply that command to your situation.

---

### Post by piracyrocks on 2006-06-04
well, it looks liek im gonna be trying the 32 bit version of ubuntu....

i just downlod the x86 one, right?

---

### Post by piracyrocks on 2006-06-04
well, it looks liek im gonna be trying the 32 bit version of ubuntu....

i just downlod the x86 one, right?

---

### Post by nickm on 2006-06-04
[QUOTE=piracyrocks]well, it looks liek im gonna be trying the 32 bit version of ubuntu....

i just downlod the x86 one, right?[/QUOTE]


i386 i think it'l be called, but yes, thats the x86 one :)

---

### Post by Cenotaph on 2006-06-04
:(

are you sure the module is loaded? do "lsmod | grep bcm" just to check if bcm43xx is there

and yes, you just have to download the 86 version and install like you did with the AMD64 version. no biggy.

---

### Post by drachir on 2006-06-04
[QUOTE=piracyrocks]well, it looks liek im gonna be trying the 32 bit version of ubuntu....

i just downlod the x86 one, right?[/QUOTE]

Sorry about the delay piracyrocks, I got caught up surfing.

I have a Turion 64 but I am using the 32bit Ubuntu. I did follow nickm's guide and I did have some hills to climb but don't worry they are worth it and I feel you will get your wireless up and running. One think I did that wasn't on the guide was I set up a dymanic ip and I have wep encryption as well.

if you post after you install the 32bit version we can help you and walk you through it. Don't give up

---

### Post by hermesrules on 2006-06-04
I've been using ndiswrapper for a very long time now, and was really thrilled to be able to use a native driver for my Broadcom 4306. It does work, it find the device, etc., however, connectivity is so choppy and slow. I had to resort back to ndiswrapper, which gives me excellent connectivity. I wonder if it is the drivers that need more work, or something in my configuration. I first set it using Flight 5 live cd, just to test it before I do it on my machine. Even though I have not done clean install (meaning I've been upgrading from Breezy), I am not certain that is the sole reason why connectivity sucks with the bcm43xx. Is it some other driver that needs to be enabled too, or is it choppy for everyone?

---

### Post by MetalMusicAddict on 2006-06-04
Ok. Everythings works great except 1 thing (theres always a catch ;)). Everytime I reboot the connection is gone. I have to go to the "Properties" of the wireless card and as soon as I do that (I dont touch a thing but look at its properties) its up and working fine. Untill a reboot. Weird.

Heres my info:
[LIST]
[*]Dell Inspiron 2200 laptop
[/LIST]
```
user@pc:~$  lspci | grep Broadcom\ Corporation
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

[LIST]
[*]Interfaces
[/LIST]
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1

iface eth0 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1



iface wlan0 inet static
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid ******** 
wireless-key ************************

auto wlan0
```

Id rather not use ndiswrapper but hey, it worked. :) Thanx.

---

### Post by crag277 on 2006-06-04
[QUOTE=drachir]Sorry about the delay piracyrocks, I got caught up surfing.

I have a Turion 64 but I am using the 32bit Ubuntu. I did follow nickm's guide and I did have some hills to climb but don't worry they are worth it and I feel you will get your wireless up and running. One think I did that wasn't on the guide was I set up a dymanic ip and I have wep encryption as well.

if you post after you install the 32bit version we can help you and walk you through it. Don't give up[/QUOTE]

Hmmm...   Looks like this is what I should do, as I have the same system.  This is a bit discouraging though.  I paid for a 64 bit processor and it would have been nice to finally use an OS that took advantage of that instruction set.  Are there any performance differences between the two?  How about power management?

---

### Post by drachir on 2006-06-04
[QUOTE=crag277]Hmmm...   Looks like this is what I should do, as I have the same system.  This is a bit discouraging though.  I paid for a 64 bit processor and it would have been nice to finally use an OS that took advantage of that instruction set.  Are there any performance differences between the two?  How about power management?[/QUOTE]

The main reason for the 64 was for the next generation of computing. There isn't to many progs out there that support 64 on any platform, we even see this in linux as well as MS, but there will be a day that the support will be there and I feel I will be ready. It does suck a bit not using the computer what it is build for but such is life. I tried the ubuntu64 but it didn't work as well as the 32 performance wise. 

Battery life is a whole lot better with 6.06. I have a 80g hdd with linux on a 20g partition and MS on a 50g partition and Backtrack on a 9g partition and a 1g swap. Ubuntu is showing me the best battery life with over 3 hours, ms gives me 2 hours and backtrack under 2 hours.

---

### Post by Cenotaph on 2006-06-04
well, i found out that actually this native broadcom driver was too unstable so i decided to use ndiswrapper and its working great :)

so my advice is: ndiswrapper plus network manager for the win :)

---

### Post by jobyjoby on 2006-06-04
[QUOTE=piracyrocks]so uh...i just did this whole thing with the new reccomended driver thing...the wl_apsta.o one...and it still doesnt work....not only can i not connect to my wireless network...but no wireless networks show up to connect to...none ever have...so im not that surprised...but im a bit dissapointed because that other guy with the same pc as me got this to work...what gives?[/QUOTE]
If you cannot see the networks with bcm4318, have you tried to blacklist ndiswapper as listed in a link at the end of the guide?  Using that was how my networks appeared, then adding nm-applet in startup programs allowed me to connect to them.

---

### Post by chrishack14 on 2006-06-04
Well, after switching back to ndiswrapper, I finally got the card to come up and discover networks properly, but it cannot use WEP encryption.  Anytime I try to connect to a WEP-enabled network, it fails to connect and a message shows up in dmesg that says:

ndiswrapper (add_wep_key:848): adding encryption key 1 failed (C0010015)

Did anyone else have this problem?  By the way, I am using the AMD64 version of Kubuntu, I have a Broadcom 4306 card, and I have tried wlassistant and wifi-radar.  Any ideas?

---

### Post by SuicideInvoice on 2006-06-04
I see now it's updated with different drivers.  It's working fine for me using the .sys file from the CD.  Even works in rfmode in Kismet.  The only thing that doesn't work right is the signal strength.  Do the newer drivers fix that?  If not, i'm staying where im at.

Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by crag277 on 2006-06-04
Different Ubuntu, same result.

It just seems like these 4318 chipsets do not want to work.

I originally tried to make it work using the 64-bit version of Kubuntu Dapper.  The very first time I scanend for networks there I saw all the availible networks, but could not connect.  Then after that first scan it was never able to find a network again.

Now after reading every post here I've installed 32-bit Ubuntu and went through the guide again, except using the driver posted by Slicedbread in post 55. [http://ubuntuforums.org/showpost.php?p=1085392&postcount=55](http://ubuntuforums.org/showpost.php?p=1085392&postcount=55)
I picked this driver because I have a Compaq V2000 with AMD and ATI, just like Slicedbread.

There were no problems or errors during the process, and after reboot network manager loaded properly, but did not immediately connect to a wireless network.  As was the problem before it did not see any networks.  I then installed WiFi Radar.  Again, no networks found, but when I manually entered the SSID for my network it showed up on the list with a full signal.  However when I tried to connect it got no farther than trying to aquire an IP address.

Hopefully someone can make these 4318s work!

Is there any way to undo this process?  I'd like to try it again using the driver specified by the author, but it's quite annoying to have to re-install the OS every time.

---

### Post by piracyrocks on 2006-06-05
i installed the 32 bit version and did the whole guide and i even blacklisted ndiswrapper and i still have no go on seeing or connecting to any wireless networks...any help would be appreciated

---

### Post by n00bWillingToLearn on 2006-06-05
[QUOTE=DJLC]I tried this, and now I can't really do anything. Upon boot (from both the HD AND a LiveCD), I get 3 errors. After closing them all, all I have is a dark brown/red background with a cursor - all I can do is move the cursor around.

In chronological order:
There was a problem registering the panel with the bonobo-activation server. The error code is: 3. The panel will now exit.

There was an error starting the GNOME Settings Daemon. Some things, such as sound, themes, or background settings may not work correctly. The Settings Daemon restarted too many times. The last error message was: System Exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0 GNOME will still try to restart the settings daemon the next time you log in.

Nautilus can't be used now, due to an unexpected error. (Under the Show More Details arrow is the following) Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server.

Three questions:
1) What, exactly, is the issue?
2) What did I do wrong, and is there anything I can do to correct it w/o reinstalling?
3) If I must reinstall, how can I do this if I can't boot from a LiveCD?

I'm on a Powerbook G3 Lombard. The only thing I did different was that I installed Network Manager BEFORE I installed the card firmware. My "Airport card" is a PCMCIA wireless card w/ Broadcom chipset - it was previously recognized by OS X as an AirPort card.[/QUOTE]

I had a similar problem when I screwed up java, but what this has to do with wireless I don't know, so this is just a hunch but try just running the java command with no arguments ie: press ctrl + alt + F1 **this will bring you to a black terminal screen to get out of it press ctrl + alt + F7** 
then type :code: java :code: and if it gives you an error like " cant find file libjvm.so" then you are having the same problem I had and I may be able to help if not then I don't know what is happening, sorry.

---

### Post by Slicedbread on 2006-06-05
[QUOTE=piracyrocks]i installed the 32 bit version and did the whole guide and i even blacklisted ndiswrapper and i still have no go on seeing or connecting to any wireless networks...any help would be appreciated[/QUOTE]

I was having the same problem. I was able to get the driver to install with the newly linked one and the Wifi light was lit but was still getting the invalid ap error. In addition, whenever i tried to scan for networks, it would not display any results. I noticed that my router's wifi light would flash when starting up but not when trying to connect so I determined it was a user setting, heres how I got it to work on my BCM 4318 chipset:

1. I removed bcm43xx-fwcutter package
2. Removed gnome network manager and network manager packages
3. Deleted all broadcom files (bcm43xx_***) in /lib/firmware
4. Commented out all connections accept lo in /etc/network/interfaces
5. Blacklisted ndiswrapper
6. Restarted
7. Followed the guide in the 1st post using the new [wl_apsta.o]("http://drinus.net/airport/wl_apsta.o") driver.

I know it seems like it should work with out having to delete the files but, I was still getting the invalid ap bug wihen I didn't delete the files. Now I dont get the microdell error or invalid ap bug. It was not also discovering the networks without commenting (#) the interfaces file. If your wifi light is not when you restart during step 6, then you know you have removed the driver and are good to start over.

---

### Post by rko618 on 2006-06-05
how is the wl_apsta.o driver better?

also if I did the guide with bcmwl5 should I go back and redo it with wl_apsta.o?  Will I see a performance boost?

---

### Post by PPower on 2006-06-05
[quote=rko618]how is the wl_apsta.o driver better?

also if I did the guide with bcmwl5 should I go back and redo it with wl_apsta.o?  Will I see a performance boost?[/quote]

According to the developers of the bcm43xx module they say this is the most up to date driver avaliable. They also they when Ubuntu upgrade to a 2.6.17+ kernel you should use this driver as it will fix the invalid ap errors (thus eliminating the need for network-manager).

---

### Post by dtlinker on 2006-06-05
I wanted to report my results with one of the "Airforce One 54g" in a Dell Inspiron B130, and Dapper in a new install.

I had already tried and failed with the native drivers, and was using ndiswrapper.

I tried blacklisting ndiswrapper, removing all bcm43xx firmware from the /lib/firmware directory and the subdirectory, and then following the instructions with the wl_apsta.o driver.

When I rebooted, I checked dmesg, and the firmware appeared to be installed, but I was unable to connect.

I then deleted all of the bcm43xx files, and re-installed using the BCMWL5.SYS file from the windows installation, rebooted, and although the driver appeared to be installed, I was still unable to connect.

Finally, I blacklisted bcm43xx, unblacklisted ndiswrapper, and rebooted, and everything works again.

Another vote saying that the Airforce One 54g driver doesn't always work!

---

### Post by Slicedbread on 2006-06-05
Did you comment out the /etc/network/interfaces file and did your wife button light up? It does seem that it is kind of touch and go with this driver but if it only depends on the wireless chipset then everyone should be able to use one solution right?

---

### Post by nickm on 2006-06-05
[QUOTE=hermesrules]I've been using ndiswrapper for a very long time now, and was really thrilled to be able to use a native driver for my Broadcom 4306. It does work, it find the device, etc., however, connectivity is so choppy and slow. I had to resort back to ndiswrapper, which gives me excellent connectivity. I wonder if it is the drivers that need more work, or something in my configuration. I first set it using Flight 5 live cd, just to test it before I do it on my machine. Even though I have not done clean install (meaning I've been upgrading from Breezy), I am not certain that is the sole reason why connectivity sucks with the bcm43xx. Is it some other driver that needs to be enabled too, or is it choppy for everyone?[/QUOTE]
 It seems fine for me on that card, it must be your configuration or building/location etc

---

### Post by stromb on 2006-06-05
[QUOTE=MasterChief1234]This worked great with my Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) card.[/QUOTE]

What system do you have? I have an HP dv5000v laptop. I've tried everything in this post and still can't get this card to work. Any other suggestions?

Thanks!

---

### Post by MetalMusicAddict on 2006-06-05
I dont need to "blacklist ndiswrapper" if I did a clean install then only used this guide right?

Is there anyone that can help with the info I posted a couple of posts above? Should I just use ndiswrapper or would it be a problem after using this guide?

---

### Post by slakkie on 2006-06-05
[QUOTE=slakkie]
Thanks for the HOWTO, got the wireless up pretty quick (without encryption).
Got it working without encryption and with encryption (WPA).
I'm using the gnome-network manager, which is described in the HOWTO. And I'm using wpasupplicant in order to get it working with WPA.

Failover from Wired to wireless isn't that good (non existent tbh)... Hopefully I will get this working somewhere this week(end).[/QUOTE]

Got my system up and running without the need of network managers.
The failover doesn't work automaticly, but its scripted so it became really easy to change from Wireless to Wired.

nickm: Don't know if you have already done this, but I created a simple install script which will do everything which is described in this HOWTO. The script can also include installing a network manager (I have disabled this for my setup).
It can also remove the installation, so you can start all over again if you want to :)

Automated install:
[http://www.euronet.nl/users/wesleys/ubuntu/installWireless.zsh](http://www.euronet.nl/users/wesleys/ubuntu/installWireless.zsh)

Switching from Wired to Wireless and vice versa:
[http://www.euronet.nl/users/wesleys/ubuntu/enableNW.zsh](http://www.euronet.nl/users/wesleys/ubuntu/enableNW.zsh)

Hope this will help some of you guys.

---

### Post by Dr Von Bon Bon on 2006-06-05
Hi,


I can't seem to install bcm43xx thingy.

Whenever I put it up in the terminal or synaptic it can't find the file. 

I think I have all the universes enabled.

---

### Post by chronusdark on 2006-06-05
ok so earlier i posted that 

```
sudo iwconfig eth1 rate 54M
```

will set my wlan into wireless G mode is there any way i can set it to do this on restart because when i reboot its back into B

if i get this figured out it should be added to the howto like a post script or something

---

### Post by charles woodward on 2006-06-05
Worked like a dream - I've been struggling to get it all to work for about two months - I could get it to work but couldn't get wep encryption to work.  Now it does using Network Manager.  

The encryption didn't work straight away, but I had read a bug that it would not work in shared mode (which the network in question used) - so I got the network to change to `open` and it worked.  XP computers (can't get the family to change) don't seem to mind if it is open, shared or what.

Anyway thanks

---

### Post by toorima on 2006-06-05
[QUOTE=chronusdark]ok so earlier i posted that 

```
sudo iwconfig eth1 rate 54M
```

will set my wlan into wireless G mode is there any way i can set it to do this on restart because when i reboot its back into B

if i get this figured out it should be added to the howto like a post script or something[/QUOTE]

Add iwconfig eth1 rate 54M to /etc/init.d/rc.local

---

### Post by rowanq on 2006-06-05
[QUOTE=charles woodward]Worked like a dream - I've been struggling to get it all to work for about two months - I could get it to work but couldn't get wep encryption to work.  Now it does using Network Manager.  

The encryption didn't work straight away, but I had read a bug that it would not work in shared mode (which the network in question used) - so I got the network to change to `open` and it worked.  XP computers (can't get the family to change) don't seem to mind if it is open, shared or what.

Anyway thanks[/QUOTE]

Right on!,
  I've been at this on and off for the last few days and I've had no success. I got every thing to install, Network Manager would show up list and my encrypted network but the connection would always fail.
 I tried various iterations of this guide (the new drivers wl_apsta.o, the drivers that came on my install cd, and the bcmwl5sys.zip download) all with the same result.
 So after reading your post I went in to my Linksys router config page and set the Authentication Type to Auto and tried again. It worked like a charm! Not only that, but I can see one other WLAN that I knew was in my neighborhood but wasn't showing up for some reason.
 Thanks for the tip Charles. And a big thanks to nickm, your guide was much needed!:D 

RowanQ

---

### Post by piracyrocks on 2006-06-05
if anyone is reading this thread that has gotten there bcm4318 to work could you please post exactly what you did to get it to work?  im at a loss here

---

### Post by axiomata on 2006-06-05
I'm having mixed results here.  I've got that famous AirForce linksys card and at first, after following this guide it worked nicely.  But now, most of the time when I reboot I get no connection.  The network manager says "connecting to my LAN" but it never fully does.  Sometimes it will default to the disabled wired connection and sometimes it will appear to connect, signal strength bars shown with 100% but it doesn't work.  Then seemingly randomly, on a later boot it will connect.

---

### Post by Slicedbread on 2006-06-05
[QUOTE=piracyrocks]if anyone is reading this thread that has gotten there bcm4318 to work could you please post exactly what you did to get it to work?  im at a loss here[/QUOTE]

If you get on AIM i can help, mine is slicedbread87.

---

### Post by PPower on 2006-06-05
For the benefit of people without internet connections on wired I have made a floppy image containing the core essencials needed to get connected to the internet plus an ODT of the guide (plus a ultra quick 4 step one). This does not include network-manager due to space limitations with all the dependencies. It also contains a 1 line script to install the firmware but I never tested it. It contains the wl_apsta.o file. The download is about 300kb and once extracted it inflates to about 660kb.

Enjoy!

What you get in the floppy:
1 copy of the guide on ODT.
1 quick install guide.
1 wl_apsta.o
1 copy of the bcm43xx-fwcutter deb
1 experimental install script for the firmware
1 readme.

This is a tar.gz containing the required files. It is not a image to dd so just copy the files to a floppy

---

### Post by chronusdark on 2006-06-05
[QUOTE=toorima]Add iwconfig eth1 rate 54M to /etc/init.d/rc.local[/QUOTE]

do i just add it to the end of the file?

---

### Post by dmarook on 2006-06-05
[QUOTE=slakkie]
nickm: Don't know if you have already done this, but I created a simple install script which will do everything which is described in this HOWTO. The script can also include installing a network manager (I have disabled this for my setup).
It can also remove the installation, so you can start all over again if you want to :)

Automated install:
[http://www.euronet.nl/users/wesleys/ubuntu/installWireless.zsh](http://www.euronet.nl/users/wesleys/ubuntu/installWireless.zsh)

Switching from Wired to Wireless and vice versa:
[http://www.euronet.nl/users/wesleys/ubuntu/enableNW.zsh](http://www.euronet.nl/users/wesleys/ubuntu/enableNW.zsh)

Hope this will help some of you guys.[/QUOTE]

Would you kindly help out a noob? How can I run the sript in UBUNTU? And what should I do to add in network manager? Thanks.

---

### Post by toorima on 2006-06-05
[QUOTE=chronusdark]do i just add it to the end of the file?[/QUOTE]

yeah and after you have a connection check with command iwconfig to see that it worked, if you don't get it to connect with 54M try with 36M, that worked for me

---

### Post by Kawayanan on 2006-06-05
[QUOTE=Slicedbread]
[QUOTE=piracyrocks]if anyone is reading this thread that has gotten there bcm4318 to work could you please post exactly what you did to get it to work?  im at a loss here[/QUOTE]

If you get on AIM i can help, mine is slicedbread87.[/QUOTE]

If you guys get do your bcm4318 to work please post what you learn.  I am still fighting with mine.  I have tried many different suggestions here with fresh installs, but have yet to get it consistantly working.  I may give ndiswrapper a try.

Kawayanan

---

### Post by piracyrocks on 2006-06-05
i havent gotten it to work yet

im going to be trying ndiswrapper pretty soon after another fresh install of 6.06

---

### Post by nickm on 2006-06-05
[QUOTE=toorima]yeah and after you have a connection check with command iwconfig to see that it worked, if you don't get it to connect with 54M try with 36M, that worked for me[/QUOTE]

Isnt the config files that iwconfig writes and reads totally unused? i think so.
so this wont make any difference to anything that uses networkmanager?

---

### Post by nickm on 2006-06-05
oops

---

### Post by slakkie on 2006-06-05
[QUOTE=dmarook]Would you kindly help out a noob? How can I run the sript in UBUNTU? And what should I do to add in network manager? Thanks.[/QUOTE]

Hi, 

I would advise u to use only the first script. You can use the second, but I saw some HOWTO's on setting up WPA with network-managers.

This is what you need to do (terminal only and non-root user):

0) mkdir ~/tmp ; cd ~/tmp
1) wget "http://www.euronet.nl/users/wesleys/ubuntu/installWireless.zsh" 
2) chmod 755 installWireless.zsh
3) get the correct dirvers, see opening post of this thread
4) Uncomment the following lines by running this:
```

perl -p -i -e 's/^  \#(RemovePackage|installNWmanager)/  $1/' installWireless.zsh
``` or do it yourself with your favorite editor:
```

  #installNWmanager
  
  #RemovePackage $NWMANAGER

```

Should look like this now:

```

  installNWmanager
  
  RemovePackage $NWMANAGER

```

Now you will be installing 'network-manager-gnome', if you want a different one, change the following line somewhere in the beginning of the script.
```

NWMANAGER=network-manager-gnome

```

5) ./installWireless install <location of driver>

You can undo all your actions by entering ./installWireless remove

You will get some examples by only running ./installWireless.

For the network manager I want to point you to this HOWTO:
[http://ubuntuforums.org/showthread.php?t=125150](http://ubuntuforums.org/showthread.php?t=125150)

As I'm doing this differently (script #2 - enableNW.zsh), I can't help you with this.

Good luck!

---

### Post by toorima on 2006-06-05
[QUOTE=nickm]Isnt the config files that iwconfig writes and reads totally unused? i think so.
so this wont make any difference to anything that uses networkmanager?[/QUOTE]

I'm not sure but when it boots with iwconfig eth1 rate 56M network manager can't connect and iwconfig shows rate 54M, when I try to connect again it connects but iwconfig shows 11M, setting it to 36M network manager connects and iwconfig shows 36M and my wireless performs better then it is when I have it at 11M so you tell me

---

### Post by piracyrocks on 2006-06-05
ok, anyone with the bcm4318 wireless card, below i will be telling you the absolute 100% gaurenteed way of getting it to work with 6.06 ubuntu:

go to this website, [http://www.beginningubuntu.com/dapper_tips.html](http://www.beginningubuntu.com/dapper_tips.html) , and follow the guide for setting up the wireless card with ndiswrapper.  (right now this website is down due to traffic hieghts but u can still get to it if u do a google search for it and view the cached version)

if your router uses a wep encryption, u have to install network manager in order to use it.  the default wireless thingy wont work with wep.

there you go, ure done...it works....oh god im so glad it worked


:-)

---

### Post by KiLLeR_WoMBaT on 2006-06-05
[QUOTE=toorima]Add iwconfig eth1 rate 54M to /etc/init.d/rc.local[/QUOTE]


Where in that file/script do I add it?  (total noob on this issue).](*,)

---

### Post by dmarook on 2006-06-05
> **slakkie]Hi, 

I would advise u to use only the first script. You can use the second, but I saw some HOWTO's on setting up WPA with network-managers.

This is what you need to do (terminal only and non-root user):

0) mkdir ~/tmp  said:**
> http://ubuntuforums.org/showthread.php?t=125150[/url]

As I'm doing this differently (script #2 - enableNW.zsh), I can't help you with this.

Good luck!

Thank you for your prompt response. I did as you instructed but get an error saying:

bash: ./installWireless.zsh: /bin/zsh: bad interpreter: No such file or directory

the driver file is on my desktop. Should I put it in a specific directory? Another thing, what would be the usual path to a file on the desktop? would it be ~/Desktop/wl_apsta.o? Thanks again.

---

### Post by toorima on 2006-06-05
[QUOTE=KiLLeR_WoMBaT]Where in that file/script do I add it?  (total noob on this issue).](*,)[/QUOTE]

Just add it at the end of the file

---

### Post by Oni-Dracula on 2006-06-05
I followed the instructions to the letter. (With the exception of a clean install).

Nothing seems to be working.... when I modprobe bcm43xx, I get module not found.

What am I doing wrong? ](*,)

---

### Post by zahidism on 2006-06-05
how do i make my bcm4306 use full power?

---

### Post by solarwind on 2006-06-06
How about if my router needs WPA-PSK authentication? Nice howto by the way, this is excellent for noobs. I should make something like this sometime. But it it were me, I would have used ndiswrapper... Whatever happned to that? Anyway, how do I get WPA-PSK support in Ubuntu Dapper? Thanks!

---

### Post by slakkie on 2006-06-06
[QUOTE=dmarook]Thank you for your prompt response. I did as you instructed but get an error saying:

bash: ./installWireless.zsh: /bin/zsh: bad interpreter: No such file or directory

the driver file is on my desktop. Should I put it in a specific directory? Another thing, what would be the usual path to a file on the desktop? would it be ~/Desktop/wl_apsta.o? Thanks again.[/QUOTE]

This could mean you don't have zsh installed, run the following command:
 sudo apt-get install zsh

And your desktop can be found at the location you mentioned: ~/Desktop

---

### Post by slakkie on 2006-06-06
[QUOTE=solarwind]How about if my router needs WPA-PSK authentication? Nice howto by the way, this is excellent for noobs. I should make something like this sometime. But it it were me, I would have used ndiswrapper... Whatever happned to that? Anyway, how do I get WPA-PSK support in Ubuntu Dapper? Thanks![/QUOTE]

I got it working with wpasupplicant:

1) Install supplicant 
2) Edit the file /etc/wpa_supplicant.conf

MIne looks like this:

```


# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

# http://www.vollink.com/gary/deb_wifi.html

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
  ssid=""
  key_mgmt=NONE
  priority=1
}

## Home WPS - TPIK
network={
  ssid="wnl.opperschaap.net"
  proto=WPA
  key_mgmt=WPA-PSK
  pairwise=TKIP
  psk='cryptedKey'
  priority=5
}


```

You can generate the network = { } section by using wpa_passphrase.
Make sure that your ESSID is the same as you want to connect to, I tried creating a key with a fake ESSID and I couldn't connect due to mismatching keys, turns out WPA used the ESSID to create the key.. 

> 
Source: [http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access)
Security in pre-shared key mode

Pre-shared key mode (PSK, also known as personal mode) is designed for home and small office networks that cannot afford the cost and complexity of an 802.1X authentication server. Each user must enter a passphrase to access the network. The passphrase may be from eight to 63 ASCII characters or 64 hexadecimal digits (256 bits). If you choose to use the ASCII characters, a hash function reduces it from 504 bits (63 characters * 8 bits/character) to 256 bits (using also the SSID). The passphrase may be stored on the user's computer at their discretion under most operating systems to avoid re-entry. The passphrase must remain stored in the Wi-Fi access point.


But enough background info, now the command you need to create your key :)

```

8:47 wesleys@nomad [/home/wesleys/bin] # wpa_passphrase wnl.opperschaap.net
# reading passphrase from stdin
TEst12345678
network={
        ssid="wnl.opperschaap.net"
        #psk="TEst12345678"
        psk=0e17eb2e34b5e7292cf0a56c0cb44c4fe40ae0dcf61130686512e40b2b926000
}

```

3) Edit the following file: /etc/default/wpasupplicant
Set the options, and set the ENABLE flag to 1

Now try running it:
```

wpa_supplicant -w -ddd -i $WLAN_INTERFACE -D wext -c /etc/wpa_supplicant.conf

```

What can help you is iwevent, this will show you events from your wireless interface, which can come in handy when debugging.

When you started up wpa_supplicant, try dhclient, or if you have defined a static IP start checking wheter you have a connection with your AP.

For more info:
[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

Which is the guide that I followed.

Good luck.

---

### Post by nickm on 2006-06-06
[QUOTE=zahidism]how do i make my bcm4306 use full power?[/QUOTE]

You cant really, but it wont effect you unless you were working with large files or had an interenet connection greater than 11mb/s.
If you want to work with large files then i suggest not using wireless at all and just go with a nice 100/1000 mb/s wired network.

---

### Post by toorima on 2006-06-06
[QUOTE=solarwind]How about if my router needs WPA-PSK authentication? Nice howto by the way, this is excellent for noobs. I should make something like this sometime. But it it were me, I would have used ndiswrapper... Whatever happned to that? Anyway, how do I get WPA-PSK support in Ubuntu Dapper? Thanks![/QUOTE]

Create /etc/default/wpasupplicant and put ENABLED=0 in it and network manager will show wpa-psk network, that was all i had to do.

---

### Post by eternalsunshine on 2006-06-06
I tried to do everything but i couldn't manage to receive wireless access from my university's ap. I don't have windows installed in my computer only dapper drake.I am using hp compaq nx9030 laptop.iwconfig eth1 gives this message:

eth1      radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Because i think i can't put the wireless light on ubuntu does not see the button...

---

### Post by tomtomgg on 2006-06-06
Cheers! Although network-manager does not report on any activity, the wireless connection works perfectly. I'm also running a Broadcom BCM4318; so you win at life.

---

### Post by dmarook on 2006-06-06
Well, got my Belkin F5D7011 Notebook wireless network card (BCM 4306 chip) going with the help of nice people like nickm (Thanks for this killer guide=D> ) , slakkie and toorima. I can now connect on startup to my home wireless network with WPA-AEP encription. A big thanks to all the posters of this thread.

I just followed the guide. The encription has been handled quite nicely by the Network-Manager without any fiddling from my part. IWCONFIG says my connection speed is 54M (Thanks toorima) though I don't know how I can test the actual speed. 

One thing I still have to sort out is that the Network-Manager cant seem to find my Router if the ESSID is not being broadcast. I am not really keen to keep broadcasting my ESSID all the time. Anyone  can advice me on this matter? Is it  a specific problem with Network-Manager?

I am only a week old in the world of UBUNTU and any Linux for that matter. So I am yet to discover all the gems hidden inside this brilliant new OS I have stumbled upon. Now that my wireless connection is 95% sorted (apart from the ESSID issue as above) I can spend some quality time with my Laptop exploring this strange new world. :D

---

### Post by maddbaron on 2006-06-06
i tried this and got this? anything i can do that doesn't involve buying an external card?

ubuntu@ubuntu:~$ lspci | grep Broadcom\ Corporation
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ubuntu@ubuntu:~$ sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  bcm43xx-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.6kB of archives.
After unpacking 102kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe bcm43xx-fwcutter 20060108-6build1 [16.6kB]
Fetched 16.6kB in 0s (28.9kB/s)
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 75854 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_20060108-6build1_i386.deb) ...
Setting up bcm43xx-fwcutter (20060108-6build1) ...

ubuntu@ubuntu:~$ sudo apt-get install network-manager-gnome
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager
The following NEW packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager network-manager-gnome
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 704kB of archives.
After unpacking 2748kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main dhcdbd 1.10-0ubuntu11 [42.8kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libnl1-pre6 1.0~pre5+svn21-2ubuntu2 [76.5kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libnm-util0 0.6.2-0ubuntu7 [116kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main network-manager 0.6.2-0ubuntu7 [228kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main network-manager-gnome 0.6.2-0ubuntu7 [241kB]
Fetched 704kB in 8s (86.0kB/s)
Selecting previously deselected package dhcdbd.
(Reading database ... 75862 files and directories currently installed.)
Unpacking dhcdbd (from .../dhcdbd_1.10-0ubuntu11_i386.deb) ...
Selecting previously deselected package libnl1-pre6.
Unpacking libnl1-pre6 (from .../libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb) ...
Selecting previously deselected package libnm-util0.
Unpacking libnm-util0 (from .../libnm-util0_0.6.2-0ubuntu7_i386.deb) ...
Selecting previously deselected package network-manager.
Unpacking network-manager (from .../network-manager_0.6.2-0ubuntu7_i386.deb) ...Selecting previously deselected package network-manager-gnome.
Unpacking network-manager-gnome (from .../network-manager-gnome_0.6.2-0ubuntu7_i386.deb) ...
Setting up dhcdbd (1.10-0ubuntu11) ...
 * Reloading system message bus config                                   [ ok ]
 * Stopping DHCP client manager...                                       [fail]
 * Starting DHCP client manager...                                       [ ok ]

Setting up libnl1-pre6 (1.0~pre5+svn21-2ubuntu2) ...

Setting up libnm-util0 (0.6.2-0ubuntu7) ...
Setting up network-manager (0.6.2-0ubuntu7) ...
 * Reloading system message bus config                                   [ ok ]
 * Stopping NetworkManager daemon                                        [ ok ]
 * Starting NetworkManager daemon                                        [ ok ]
 * Stopping NetworkManager dispatcher                                    [ ok ]
 * Starting NetworkManager dispatcher                                    [ ok ]

Setting up network-manager-gnome (0.6.2-0ubuntu7) ...
find: WARNING: Hard link count is wrong for .: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
find: WARNING: Hard link count is wrong for .: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.

---

### Post by Gurgeh on 2006-06-06
That was spot on - I really cannot express how clear and simple the instructions are - it did help that i'm using exactly the same card as you. I bow to your greatness mate.
 
Thanks again.

---

### Post by joergenlie on 2006-06-06
Now I've been playing around for two days. Still my problem is that my card will not connect at boot up, but now I have found that the only thing needed is to run 
sudo iwconfig eth0 ap any 

and 

/etc/init.d/networking restart

the wiki page about the subject suggests that I add iwconfig eth0 ap any to /network/interfaces

Still this doesnt do it. Is there anywhere else I can put these commands to make it connect at boot up? Or is there a special way or place to put them in the interfaces file?

ANother thing ,when i run iwconfig it says bitrate 11mbps, but in iwlist scan it says 54 mbps? Whats the difference?

JØrgen

---

### Post by RyanR313 on 2006-06-06
This was the easiest most straight forward instructions I have found in the linux world. OK so that may be hyperbole but WOW! It took five minutes for me to set this up and I am up and running. 
Thanks

---

### Post by nickm on 2006-06-06
not to blow my own trumpet, but i just used my guide with a fresh install of ubuntu and it works!! =D> 

:roll:

I was wondering if someone can help me though, on step 4b the user is going to have to find out what kernel they have etc, is there a command to do this, but just list the numbers so i could change it from
 sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-23-386 ~/Desktop/wl_apsta.o 
to 
 sudo bcm43xx-fwcutter -w /lib/firmware/**`command'** ~/Desktop/wl_apsta.o ?

---

### Post by PPower on 2006-06-06
[quote=nickm]not to blow my own trumpet, but i just used my guide with a fresh install of ubuntu and it works!! =D> 

:roll:

I was wondering if someone can help me though, on step 4b the user is going to have to find out what kernel they have etc, is there a command to do this, but just list the numbers so i could change it from
 sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-23-386 ~/Desktop/wl_apsta.o 
to 
 sudo bcm43xx-fwcutter -w /lib/firmware/**`command'** ~/Desktop/wl_apsta.o ?[/quote]
it would be uname -r i think but you dont need to put it in a specific folder on /lib/firmware. just dump it in /lib/firmware.

---

### Post by nickm on 2006-06-06
[QUOTE=PPower]it would be uname -r i think but you dont need to put it in a specific folder on /lib/firmware. just dump it in /lib/firmware.[/QUOTE]

well some people were finding that they had to, so i dont know if it makes a difference or not.

Thanks anyway, ill try it out :)

---

### Post by joergenlie on 2006-06-06
[QUOTE=joergenlie]Now I've been playing around for two days. Still my problem is that my card will not connect at boot up, but now I have found that the only thing needed is to run 
sudo iwconfig eth0 ap any 

and 

/etc/init.d/networking restart

the wiki page about the subject suggests that I add iwconfig eth0 ap any to /network/interfaces

Still this doesnt do it. Is there anywhere else I can put these commands to make it connect at boot up? Or is there a special way or place to put them in the interfaces file?

ANother thing ,when i run iwconfig it says bitrate 11mbps, but in iwlist scan it says 54 mbps? Whats the difference?

JØrgen[/QUOTE]

Sing HALLELUJAH!!! I went through the howto over again and now my broadcom 4306 works like silk:mrgreen: 

Thank you very much!

Jørgen

---

### Post by PPower on 2006-06-06
[quote=nickm]well some people were finding that they had to, so i dont know if it makes a difference or not.

Thanks anyway, ill try it out :)[/quote]

It works fine for me in /lib/firmware. The problem with sticking it in a kernel dir is that you have to reinstall it every time the kernel is updated. Thanks for adding the wl_apsta.o. It will come in handy when Ubuntu upgrade to 2.6.17 or later.

---

### Post by nickm on 2006-06-06
[QUOTE=PPower]It works fine for me in /lib/firmware. The problem with sticking it in a kernel dir is that you have to reinstall it every time the kernel is updated. Thanks for adding the wl_apsta.o. It will come in handy when Ubuntu upgrade to 2.6.17 or later.[/QUOTE]

its okay, im using it now and its fine with the current kernel too.

---

### Post by helfire on 2006-06-06
After i go through the guide i can see AP's and connect to them (i get an IP and  gw/dns) but i cannot get connectivity. Anyone else had this problem? I cant ping my DNS ip's or anything. I'm hopeing this is just a configuration issue. Did this on a fresh install.

---

### Post by xxrealmsxx on 2006-06-06
It works, finally!

Thanks, this thread alone made me partition a hdd for mostly linux use for the first time.

Is there a command to start the wireless nic? 

When I leave my house if I hibernate while im on wired network and I get on campus I have to restart the laptop to connect to the wireless network, any easy way around that?

---

### Post by solarwind on 2006-06-06
Yeah, this is great, but what about ndiswrapper and the bcmwl5.inf and bcmwl5.sys files? Does this method have an advantage over the ndiswrapper method?

---

### Post by TheAngryPenguin on 2006-06-06
It didn't work for me.  I have a Dell Latitude D400 with a "0000:01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)" wireless card.  I tried with the files from the first post as well as with a .sys that's known to work well with ndiswrapper.  In all cases, I've ended up with a kernel panic right as the wireless card became active.  To anyone else with this particular flavor of Broadcom, here's what I've done to get it to work (and I won't go that much into detail since most of this is documented very well elsewhere...):

1) Install ndiswrapper-utils

2) Download the [TrueMobile 1400 (BCM4309 - 802.11a+b+g)](http://ftp.us.dell.com/network/R63259.EXE) driver package from Linuxant's [site](http://www.linuxant.com/driverloader/drivers.php).

3) Rename R63259.EXE to R63259.EXE.ZIP and open with Archive Manager -- extract bcmwl5.inf and bcmwl5.sys from /TMSetup

4) Do the ndiswrapper voodoo with the file(s) above.

5) Blacklist bcm43xx

6) Add ndiswrapper to /etc/modules

7) Reboot

Now, if I could only get NetworkManager to work with ndiswrapper...

---

### Post by Kawayanan on 2006-06-06
[QUOTE=piracyrocks]ok, anyone with the bcm4318 wireless card, below i will be telling you the absolute 100% gaurenteed way of getting it to work with 6.06 ubuntu:

go to this website, [http://www.beginningubuntu.com/dapper_tips.html](http://www.beginningubuntu.com/dapper_tips.html) , and follow the guide for setting up the wireless card with ndiswrapper.  (right now this website is down due to traffic hieghts but u can still get to it if u do a google search for it and view the cached version)

if your router uses a wep encryption, u have to install network manager in order to use it.  the default wireless thingy wont work with wep.

there you go, ure done...it works....oh god im so glad it worked


:-)[/QUOTE]

Ok, after trying lots and lots of stuff (and many fresh installs) to get my bcm4318 working, ndiswrapper worked like a charm.

The website above was great (also has a bunch of other nice tips too).  The ndiswrapper install and setup was just as easy as the howto here for the bcm43xx driver, and for the 4318 at least, it works great.  As piracyrocks said, the website seems to be down (over bandwidth maybe?).  As said above, just search google for the url and use the google cache.  I would also suggest checking out the [ndiswrapper install wiki]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation").  They have some nice info if you have more questions.  They also suggest what to look for in the system logs for a sucessful install.  After installing ndiswrapper, I installed network-manager-gnome and it worked with wep on the first try (using it right now :) ).

Thanks again to everyone here for their help and suggestions, and thank you nickm for all your work on this howto.  You might think about putting something in it for 4318 owners as many seem to be having problem getting connected with the bcm43xx driver.  ndiswrapper may work better for them.

Kawayanan

---

### Post by nickdr on 2006-06-06
wow nickm i freaking love you. i tried so much to get my wireless card working in ubuntu, starting with breezy. i tried ndis-wrapper and anything else i found that sounded remotely helpful. i was actually ready to give up on linux, when i saw this link on digg.com and i decided to give it one last try.
you're a lifesaver

---

### Post by big_gie on 2006-06-06
I'm having trouble using NetworkManager. It works ok with cable, but wireless is a no-go.

I have a Dell Inspiron 8500 with a Broadcom 4306 wifi card using bcm43xx.

Attached is the log of "NetworkManager --no-daemon"

It get stock to line 141 for 60 seconds it seems, then time out with "Activation (eth1/wireless): association took too long (>60s), failing activation."

Anyone have an idea???

Thanx

---

### Post by smylie on 2006-06-07
[QUOTE=PPower]C

When Ubuntu upgrade to a new kernel (and thus a new version of the bcm module) you MUST NOT use the driver supplied on this thread. [/QUOTE]

i've had to upgrade kernel to fix acpi issues, and thus need to recompile the bcm  module. However, I can't (embarrasingly enough) find the source.
The [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) page states that it will be included in the 2.6.17 kernel, but seem to have removed the link to download the module from the page already. You can get the firmware cutter from their svn repository, but that's about it. 
The documentation merely states that you can download the module from the site.

I've patched my kernel up to 2.6.17-rc6, but although the bcm43xx files are now there in drivers/net/wireless/bcm43xx, i can't find the option to include it in menconfig.

Any one know where I can download the seperate source for this module, or how to force it to build as part of the 2.6.17 kernel?

smylie

---

### Post by crag277 on 2006-06-07
First of all, thanks to all the posts on these forums I'm posting from a wireless connection, and I have a Broadcom 4318 "AirForce One 54g".

Here's how I did it, maybe it'll help someone.  You don't even need an internet connection.

The drivers I used are attached to the message.  To follow this guide to a T downlad them and place in a folder bcm43xx on your desktop.

I've tried the procedure in this HowTo several times, on different versions of Dapper, with different drivers and it would never work.  I had to use ndiswrapper to get it working.

I'm running Ubuntu i386 Dapper, Turion 64, ATI Radeon XPRESS 200M.

1) ** Blacklist bcm43xx driver**

[INDENT][/INDENT]Open a Terminal window

[INDENT][/INDENT]Type "sudo gedit etc/modprobe.d/blacklist"

[INDENT][/INDENT]At the bottom add the lines

[INDENT][/INDENT]# get rid of the default kernel drivers

[INDENT][/INDENT]blacklist bcm43xx

2)  **Make sure network interfaces file is correct**

[INDENT][/INDENT]Type "sudo gedit /etc/network/interfaces"

[INDENT][/INDENT]Remove all comments ('#') that you see so that all devices are  [INDENT][/INDENT]handled by the default network manager.

[INDENT][/INDENT]I would reboot here and make sure the wireless light goes out

3) ** Install ndiswrapper**

[INDENT][/INDENT]Put in Ubuntu CD.  Open Synaptic Package Manager (Click [INDENT][/INDENT]System -> Administration -> Synaptic Package Manager), [INDENT][/INDENT]search for ndiswrapper-utils, and install it.
[INDENT][/INDENT]You could also type "sudo apt-get install ndiswrapper-utils

4)  **Conigure ndiswrapper**

[INDENT][/INDENT]Open termianl and navigate the folder where your drivers are.
[INDENT][/INDENT]"cd Desktop/bcm43xx"

[INDENT][/INDENT]Type "sudo ndiswrapper -i oem3.inf"
[INDENT][/INDENT]Then type "sudo ndiswrapper -m"

[INDENT][/INDENT]Type "sudo gedit /etc/modprobe.d/ndiswrapper"
[INDENT][/INDENT]Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit.  If it worked, you should be able to click the Network Manager icon in the top right.  It will probably show a disconnected ennection becuase the computer is not plugged in.  
Left click it and select eth1 from the drop down menu. 
Click Configure
Click Wireless Connection, then Properties.  Here just enter your network information.  If you're using an unprotected network you should only have to type yout SSID.

Click OK and you should now be connected!  If a green signal meter and connected network icon appear in the upper right you'll know it worked.

Hope this helps!

---

### Post by PPower on 2006-06-07
[quote=smylie]i've had to upgrade kernel to fix acpi issues, and thus need to recompile the bcm  module. However, I can't (embarrasingly enough) find the source.
The [http://bcm43xx.berlios.de/]("http://bcm43xx.berlios.de/") page states that it will be included in the 2.6.17 kernel, but seem to have removed the link to download the module from the page already. You can get the firmware cutter from their svn repository, but that's about it. 
The documentation merely states that you can download the module from the site.

I've patched my kernel up to 2.6.17-rc6, but although the bcm43xx files are now there in drivers/net/wireless/bcm43xx, i can't find the option to include it in menconfig.

Any one know where I can download the seperate source for this module, or how to force it to build as part of the 2.6.17 kernel?

smylie[/quote] 
If I believe correctly it is installed by default. Not compiling a kernel ever I dont 100% know but oh well. Ill hunt around bcm-users later when everybody is awake! (6:30 here!)

There is a guide for compiling for .15/.16 at [http://random.blackworlds.org/bcm43xx-how-to.txt](http://random.blackworlds.org/bcm43xx-how-to.txt)

---

### Post by smylie on 2006-06-07
[QUOTE=PPower]If I believe correctly it is installed by default. Not compiling a kernel ever I dont 100% know but oh well. Ill hunt around bcm-users later when everybody is awake! (6:30 here!)

There is a guide for compiling for .15/.16 at [http://random.blackworlds.org/bcm43xx-how-to.txt](http://random.blackworlds.org/bcm43xx-how-to.txt)[/QUOTE]

same problem - that documentation says to download the module source from [http://bcm43xx.berlios.de](http://bcm43xx.berlios.de), but as previously mentioned, the module source is not available on that page (that I can see).

smylie

---

### Post by veebis on 2006-06-07
Followed your **excellent** step by step, and here I am, posting from the living room (my regular spot for writing/browsing)... Thank you! Only suggestion I can think of is maybe make it clearer that the pieces (esp. the ".o" file) actually works for Apple hw. Made me a little nervous, what with all that sudo-ing and being pretty noob. Great job, and thanks again!
-Vb

---

### Post by PPower on 2006-06-07
[quote=smylie]same problem - that documentation says to download the module source from [http://bcm43xx.berlios.de]("http://bcm43xx.berlios.de"), but as previously mentioned, the module source is not available on that page (that I can see).

smylie[/quote]
The module [SIZE=2]depends on [B]PCI && IEEE80211 && IEEE80211_SOFTMAC && NET_RADIO && EXPERIMENTAL

[/B]Use **\** to find it in menuconfig. When done the bcm option will magically appear.:KS

[/SIZE]

---

### Post by rjstevens3 on 2006-06-07
[QUOTE=crag277]First of all, thanks to all the posts on these forums I'm posting from a wireless connection, and I have a Broadcom 4318 "AirForce One 54g".

Here's how I did it, maybe it'll help someone.  You don't even need an internet connection.

The drivers I used are attached to the message.  To follow this guide to a T downlad them and place in a folder bcm43xx on your desktop.

I've tried the procedure in this HowTo several times, on different versions of Dapper, with different drivers and it would never work.  I had to use ndiswrapper to get it working.

I'm running Ubuntu i386 Dapper, Turion 64, ATI Radeon XPRESS 200M.

1) ** Blacklist bcm43xx driver**

[INDENT][/INDENT]Open a Terminal window

[INDENT][/INDENT]Type "sudo gedit etc/modprobe.d/blacklist"

[INDENT][/INDENT]At the bottom add the lines

[INDENT][/INDENT]# get rid of the default kernel drivers

[INDENT][/INDENT]blacklist bcm43xx

2)  **Make sure network interfaces file is correct**

[INDENT][/INDENT]Type "sudo gedit /etc/network/interfaces"

[INDENT][/INDENT]Remove all comments ('#') that you see so that all devices are  [INDENT][/INDENT]handled by the default network manager.

[INDENT][/INDENT]I would reboot here and make sure the wireless light goes out

3) ** Install ndiswrapper**

[INDENT][/INDENT]Put in Ubuntu CD.  Open Synaptic Package Manager (Click [INDENT][/INDENT]System -> Administration -> Synaptic Package Manager), [INDENT][/INDENT]search for ndiswrapper-utils, and install it.
[INDENT][/INDENT]You could also type "sudo apt-get install ndiswrapper-utils

4)  **Conigure ndiswrapper**

[INDENT][/INDENT]Open termianl and navigate the folder where your drivers are.
[INDENT][/INDENT]"cd Desktop/bcm43xx"

[INDENT][/INDENT]Type "sudo ndiswrapper -i oem3.inf"
[INDENT][/INDENT]Then type "sudo ndiswrapper -m"

[INDENT][/INDENT]Type "sudo gedit /etc/modprobe.d/ndiswrapper"
[INDENT][/INDENT]Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit.  If it worked, you should be able to click the Network Manager icon in the top right.  It will probably show a disconnected ennection becuase the computer is not plugged in.  
Left click it and select eth1 from the drop down menu. 
Click Configure
Click Wireless Connection, then Properties.  Here just enter your network information.  If you're using an unprotected network you should only have to type yout SSID.

Click OK and you should now be connected!  If a green signal meter and connected network icon appear in the upper right you'll know it worked.

Hope this helps![/QUOTE]


When  I
```
 dmesg | grep ndiswrapper 
```

I get ndiswrapper 1.6 loaded... driver loaded... wlan0:ndiswrapper ethernet device (numbers) using driver oem3.... I changed the alias in /etc/modprobe.d/ndiswrapper, but the module still loads with wlan0 as the wireless card. Network manager doesn't show wlan0, nor does ifconfig or iwconfig. This has been my problem with ndiswrapper all along. I have used the .deb and built from source with same results. I'm using source right now.

-RJ

---

### Post by cfischer on 2006-06-07
I've read and re-read every post here - thanks, all. And I guess I should contribute - just got the wireless card working on my Dell Inspiron 5150. The secret (after two days of work) is to use ndiswrapper (disable bcm43xx and install ndiswrapper-utils)  and the drivers from dell - bcmwl5.inf and bcmwl5.sys.  The other driver (wl_apsta.o) does not bring up the link - that is handled (I guess) by the RadioState line in bcmwl5.inf - it needs to be set to 0 to turn on the card. I spent two days wondering why dmesg kept telling me that eth1: link is not ready.

see part 2 here: [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f)

---

### Post by cfischer on 2006-06-07
[QUOTE=cfischer]I've read and re-read every post here - thanks, all. And I guess I should contribute - just got the wireless card working on my Dell Inspiron 5150. The secret (after two days of work) is to use ndiswrapper (disable bcm43xx and install ndiswrapper-utils)  and the drivers from dell - bcmwl5.inf and bcmwl5.sys.  The other driver (wl_apsta.o) does not bring up the link - that is handled (I guess) by the RadioState line in bcmwl5.inf - it needs to be set to 0 to turn on the card. I spent two days wondering why dmesg kept telling me that eth1: link is not ready.

see part 2 here: [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f)[/QUOTE]

Oh, yeah ... ndiswrapper wants to name the wireless device wlan0 - and automatically does that by adding a line to /etc/modprobe.d/ndiswrapper: alias wlan0 ndiswrapper. That needs to be fixed. And then be sure the script, /etc/network/interfaces uses eth1 for the interface name - can't just pop in your old script! I added ndiswrapper to modules and blacklisted bcm43xx.

Now, on to getting my usb mouse and storage working ...

---

### Post by MarkSheely on 2006-06-07
**Thank you** so much for this guide.  I have one of the dreaded BCM4318[Air ForceOne 54g] cards that everyone has been having problems with, and a Dell B130 laptop.  I began with a clean install of Dapper (as you recommended), followed the instructions you gave, and the recommendation here:
[http://ubuntuforums.org/showpost.php?p=1084114&postcount=43](http://ubuntuforums.org/showpost.php?p=1084114&postcount=43)

Within 15 minutes, my wireless was working.  

I think the most important thing was that I went through the process immediately after installing Dapper.  I didn't have the chance to screw anything up.

---

### Post by roadkillbunny on 2006-06-07
I have a BCM4306 wireless card in my amd64 laptop. I have been using it sucessfully with ndiswrapper for some time now, but since I updated to Drapper I figured I will give the native bcm43xx driver a shot. I followed this guide to a step and am able to connect to my neighbors' unencrypted network. But when I try conneting to my WEP encrypted I get the following error in dmesg:
```

bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
ADDRCONF(NETDEV_UP): wlan0: link is not ready
SoftMAC: Open Authentication with 00:c0:49:ee:7b:78 failed, error code: 13

```

I tried using the same firmware from what I use with ndiswrapper, one that I found in bcm43xx's README, the one from this site, and one that I found on compaq's site. Anyone know what I could do to fix this?

---

### Post by ????? on 2006-06-07
[QUOTE=roadkillbunny]I have a BCM4306 wireless card in my amd64 laptop. I have been using it sucessfully with ndiswrapper for some time now, but since I updated to Drapper I figured I will give the native bcm43xx driver a shot. I followed this guide to a step and am able to connect to my neighbors' unencrypted network. But when I try conneting to my WEP encrypted I get the following error in dmesg:
```

bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
ADDRCONF(NETDEV_UP): wlan0: link is not ready
SoftMAC: Open Authentication with 00:c0:49:ee:7b:78 failed, error code: 13

```

I tried using the same firmware from what I use with ndiswrapper, one that I found in bcm43xx's README, the one from this site, and one that I found on compaq's site. Anyone know what I could do to fix this?[/QUOTE]

What comes up when you type iwconfig into terminal? Is your AP "Open" and not "shared"?

---

### Post by roadkillbunny on 2006-06-07
[QUOTE=?????]What comes up when you type iwconfig into terminal? Is your AP "Open" and not "shared"?[/QUOTE]
Right after loading the bcm43xx module:
```
wlan0     IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

After doing ifconfig wlan0 up:
```
wlan0     IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I have also tried doing "ap any" and "rate 11M" or 54M as suggested by a post with no success.

Also I am using shared mode.

---

### Post by smylie on 2006-06-08
[QUOTE=PPower]The module [SIZE=2]depends on [B]PCI && IEEE80211 && IEEE80211_SOFTMAC && NET_RADIO && EXPERIMENTAL

[/B]Use **\** to find it in menuconfig. When done the bcm option will magically appear.:KS

[/SIZE][/QUOTE]

my god man. i've been using linux since 1997 and I never knew you could hunt thru menuconfig like that! i hate to think how many hours of hunting round that would have saved me =)

i do have one more question . . . how did you find out what the dependancies on making it appear are?

thanks heaps =)

smylie

---

### Post by PPower on 2006-06-08
[quote=smylie]my god man. i've been using linux since 1997 and I never knew you could hunt thru menuconfig like that! i hate to think how many hours of hunting round that would have saved me =)

i do have one more question . . . how did you find out what the dependancies on making it appear are?

thanks heaps =)

smylie[/quote]

They are them. Thanks to the bcm team!
[SIZE=1]downloading vista public beta[/SIZE]

---

### Post by ososxe on 2006-06-08
Thanks, crag277!!
Following the steps on your ho to, it made the broadcom wireless card on my Acer Aspire 3003 works flawlessly!
Nut i have a minor correction to make on your how to. Where it says

[QUOTE=crag277]
[INDENT][/INDENT]Type "sudo gedit etc/modprobe.d/blacklist"
[/QUOTE]

Should say "sudo gedir **/**etc/modprobe.d/blacklist
A newbie like me may get troubles with this ;)

---

### Post by nickm on 2006-06-08
why is everyone reporting using NDIS Wrapper? i really hope all these people have atleast tried my guide first ](*,) 
It might be better to take NDIS questions to a thread related to their use?

---

### Post by Slicedbread on 2006-06-08
[QUOTE=nickm]why is everyone reporting using NDIS Wrapper? i really hope all these people have atleast tried my guide first ](*,) 
It might be better to take NDIS questions to a thread related to their use?[/QUOTE]

They probably tried using the bcm43xx driver but failed and the title is labled "How to: Broadcom Wireless Cards". Maybe you should include ndiswrapper instructions as an alternative, I personally found that it's more stable, as easy to install and performs better than bcm43xx driver.

---

### Post by cyberknight72 on 2006-06-08
Thanks for the great how to!  I had thought at first it had not functioned however I did not read through the how to properly and built my own problems. ](*,)   I went from a fresh install and followed the how to line line for line (same broadcom device).  Now I am up on wireless on my Compaq Pressario 2585US! Thanks a lot! =D>  One question,  under breezy, I was able to get 802.11g support with the same device using ndiswrapper however I noted that my wireless under 6.0.6 is only 802.11b.  Is this due to the way the driver functions under dapper drake?  Or is it some failure that I made? :confused:

---

### Post by nickm on 2006-06-08
[QUOTE=Slicedbread]They probably tried using the bcm43xx driver but failed and the title is labled "How to: Broadcom Wireless Cards". Maybe you should include ndiswrapper instructions as an alternative, I personally found that it's more stable, as easy to install and performs better than bcm43xx driver.[/QUOTE]

Ah Right, well its never worked for me so i cant provide instructions for how to get it working..

---

### Post by gesho on 2006-06-08
great topic, thanks to the author.

for BCM4318 users (same here, on my inspiron 600m): look like the post by Slicedbread is the best for us. 
[http://ubuntuforums.org/showpost.php?p=1085392&postcount=55](http://ubuntuforums.org/showpost.php?p=1085392&postcount=55)

here is what I did
installed bcmxx
downloaded bcmwl5 **from Slisedbread's link in above post**
blacklisted ndiswrapper
rebooted
sudo bcm43xx-fwcutter -w /lib/firmware bcmwl5.sys (got same errors here as other BCM4318 users, don't worry)
rebooted

and cheers, signal is there

---

### Post by big_gie on 2006-06-08
[QUOTE=big_gie]I'm having trouble using NetworkManager. It works ok with cable, but wireless is a no-go.

I have a Dell Inspiron 8500 with a Broadcom 4306 wifi card using bcm43xx.

Attached is the log of "NetworkManager --no-daemon"

It get stock to line 141 for 60 seconds it seems, then time out with "Activation (eth1/wireless): association took too long (>60s), failing activation."

Anyone have an idea???

Thanx[/QUOTE]

Anyone? ](*,)

---

### Post by PPower on 2006-06-08
[quote=nickm]Ah Right, well its never worked for me so i cant provide instructions for how to get it working..[/quote]

For me ndiswrapper segfaults. Oh well...

---

### Post by DW5 on 2006-06-08
Upgraded from Breezy, tried all day yesterday to get this to work following the guide.  Have an Compaq nx9010 with a Broadcom 4303. Blacklisted ndiswrapper, deleted old drivers, used the cutter, modprobed, etc.  To no avail, could see network, but dhcp failed to get an ip.  This morning, I blacklisted bcm43xx and unblacklisted ndiswrapper.  Rebooted.  It worked.  Sorry.  I really wanted this to work for me as I'd rather use a native linux driver, but I don't have time to keep trying to get it to work.

DW

---

### Post by Kawayanan on 2006-06-08
[QUOTE=nickm]why is everyone reporting using NDIS Wrapper? i really hope all these people have atleast tried my guide first ](*,) 
It might be better to take NDIS questions to a thread related to their use?[/QUOTE]

I have a 4318 and tried you guide with every permutation suggested in this thread.  Yes, they were clean installs (I think I did 5 clean installs in 2 days).  I could always see the available networks, but never connect.  I tried it with Network Manager and without (manually inputting settings).  Nothing worked.  I am guessing there are just some hardware the bcm43xx driver doesn't work well with.

Kawayanan

---

### Post by PPower on 2006-06-08
[quote=DW5]Upgraded from Breezy, tried all day yesterday to get this to work following the guide. Have an Compaq nx9010 with a Broadcom 4303. Blacklisted ndiswrapper, deleted old drivers, used the cutter, modprobed, etc. To no avail, could see network, but dhcp failed to get an ip. This morning, I blacklisted bcm43xx and unblacklisted ndiswrapper. Rebooted. It worked. Sorry. I really wanted this to work for me as I'd rather use a native linux driver, but I don't have time to keep trying to get it to work.
 
DW[/quote]
 
Is it a nx9110? That is supported but 9010 is not on the list. Please try again once Ubuntu has updated their kernels.

---

### Post by Darklance on 2006-06-08
Thanks, this how to came in handy, i was starting to think my cardbus was damaged or some how unsupported again thank you

---

### Post by medw1974 on 2006-06-08
This is interesting I successfully used this howto to get my broadcom 4306 to work automatically on boot on my dell inspiron 9100 using the 686 kernel. Network-Manager would not work for me but I didn't seem to need it.

However I have tried to replicate this now using the 686-smp kernel but the best result I can acheive is having to:

sudo iwconfig eth1 ap any
sudo dhclient eth1

on each reboot.

Any idea what the differences could be? Or how to run those 2 lines automatically at boot time?

---

### Post by nickm on 2006-06-08
[QUOTE=medw1974]
sudo iwconfig eth1 ap any
sudo dhclient eth1

on each reboot.

Any idea what the differences could be? Or how to run those 2 lines automatically at boot time?[/QUOTE]

Yes, you can add them to System > preferences > sessions > start up programs

just add each seperate command into its own entry and restart, see if that fixes it.

---

### Post by medw1974 on 2006-06-08
[QUOTE=nickm]Yes, you can add them to System > preferences > sessions > start up programs

just add each seperate command into its own entry and restart, see if that fixes it.[/QUOTE]

Thanks, I'd already tried that but it didn't do anything.

But I have an update to my earlier post - because network-manager didnt seem to work when I originally got things going on the plain 686 kernel I didn't install it on the 686-smp, but I thought I'd give it a go anyway and voila it's connected on startup.

Strangely though as per before network-manager doesnt see any connections.

---

### Post by xxrealmsxx on 2006-06-08
This method of getting the wireless networking to work for me is very inconsistent, I followed the instructions in every way but for some reason I will show 100% signal strength in network manager and the wifi light on my laptop will be on but I wont be able to browse or do anything.

However some times, like now, the wifi light is off, but network manager says 100% and it works fine.

Other than that this works great, I just wish it more consistent because I know I have signal here 24/7 in windows.

---

### Post by crag277 on 2006-06-08
[QUOTE=nickm]why is everyone reporting using NDIS Wrapper? i really hope all these people have atleast tried my guide first ](*,) 
It might be better to take NDIS questions to a thread related to their use?[/QUOTE]


Oh your guide was the first thing I tried.  It's excellet, just didn't work with my hardware.  With NDISwrapper it works perfectly with all default software and even works at full 54MBps.

---

### Post by Vogateer on 2006-06-08
I have the BCM4318 [AirForce One 54g] 802.11 g wireless LAN Controller (rev 02), so count me amongst those who can't get this working just yet. Well done on the howto, though, glad to see a lot of people having success with it. My time will come. :)

---

### Post by Cable on 2006-06-09
I've tried this, and it didn't work for me either.  The light on my card has never turned on.  My card shows up as eth0, not wlan0 like I've seen other people mention.  Is there a way to remove what I did in this guide to try this again or try other things?  Or do you have any suggestions?  Also, I noticed that your guide says this makes the card word with B.  Is there a way to get G to work?  I really need G.

My card is a WMP54G BCM4306.

---

### Post by hermesrules on 2006-06-09
I have the 4306 chipset on a Compaq Presario 2100 laptop. I've been finally able to test the bcm43xx driver, having tried several sources for the driver files. Even with the driver file I got ndiswrapper to work, I couldn't make the bcm43xx work, so I actually found a version on this thread that finally made it work. It is 3.17.100.something, if I am not wrong...

I am now using the Kubuntu 6.06 Desktop CD, so that I wouldn't have to worry about my system settings. I was able to bring the card on, but for some reason the connection is slow, and tends to drop all the time. For example, I have 10 seconds of fast internet, and then about a minute of no connectivity, then some connectivity, then no connectivity again, etc. When I issue iwconfig, there is something that caught my attention.  Where it says "Rx invalid crypt", I get a number, which is growing almost every time I use iwconfig. This was not the case with ndiswrapper.

More interestingly, the dmesg | grep bcm43xx output, following modprobe bcm43xx is as follows:
[/CODE] [4296696.067000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134 [/CODE]

Then once the connection is up, I get this from the same command:
[/CODE][4296696.067000] bcm43xx: Controller restarted
[4296906.075000] bcm43xx: MAC suspend failed
[4296907.086000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR[/CODE]

I have no idea what either of these mean. Of course, I had to do iwconfig eth1 ap any to enable the access point, and could only configure via the KDE gui, but not through sudo ifup eth1.

Lastly, my wireless light is never on. NEVER. No matter whether I use ndiswrapper, or the bcm43xx. It works fine in XP, and I use the same driver with ndiswrapper.

Any ideas why I cannot get a good connection with the bcm43xx? I'd be happy to use it, but at the current state it is very much unusable for me. It is more like a proof of concept. Any suggestions highly appreciated.

Thanks!

---

### Post by skelooth on 2006-06-09
I just want to add to the topic that it worked for me.

Turned out I had the 4318e Airforce One.... I honestly grumbled under my breath when I found out.... I followed the instructions and the wireless card was active, and it could even see the wireless network AND the windows network... but would not connect.

I added the blacklist bcm43xx entry and now it works perfect! Awesome!

---

### Post by nickm on 2006-06-09
[QUOTE=Cable]I've tried this, and it didn't work for me either.  The light on my card has never turned on.  My card shows up as eth0, not wlan0 like I've seen other people mention.  Is there a way to remove what I did in this guide to try this again or try other things?  Or do you have any suggestions?  Also, I noticed that your guide says this makes the card word with B.  Is there a way to get G to work?  I really need G.

My card is a WMP54G BCM4306.[/QUOTE]

No, i'v never got it to work with G sorry, everything people are saying about getting it to work with g dont seem to work either, i'v never understood why people need fast wirless, unless your internet is >= 11mbps you wont use it. and if you do need to move large files around quickly i dont get why people dont just use 100/1000mbps ethernet :-k

---

### Post by skelooth on 2006-06-09
mine is working with g

---

### Post by crag277 on 2006-06-09
As I posted [here]("http://ubuntuforums.org/showpost.php?p=1105667&postcount=218") I managed to get my 4318 working great using ndiswrapper in Ubuntu.  I prefer to use KDE, so after I knew it could work I installed Kubuntu 6.06 and followed the same procedure.  It worked beautifully again, until the first reboot.  Now, when the computer boots it pauses at the “Configuring Network Interfaces” step for about a minute and instead of coming on solid my wireless light flashes, as if to indicate some error.  Once KDE loads and I open up Wireless Assistant (how to auto connect in KDE anyone?) it sees my network, and I try to connect.  The first time it cannot get an IP and gives an error message.  But after that happens the wireless light on the laptop is on solid and I simply need to connect again and it works flawlessly.

I realize this is minor, but it would be nice to fix as everything else seems to be running great in Kubuntu.

---

### Post by mike4ubuntu on 2006-06-09
Yep, it finally worked for me.  Thank you very much.

I have a Lenovo 3000 Series C100

lspci | grep Broadcom\ Corporation 
0000:01:02.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)

I actually did not have to reboot.  As soon as I installed the network-manager-gnome package it just started working.  It looks like it starts a DAEMON.

Not sure I want to reboot, it might not work anymore :D

---

### Post by gomezj00 on 2006-06-09
Hi,
I just wanted to thank you for the excellent guide.  It worked perfecctly for me.  However, since I'm running Dapper with Xfce4 I don't think I can run the network manager specified in the guide.  However, that's okay for me.  Thanks again for the great guide!

---

### Post by Burke on 2006-06-09
Hi, I think I have it close to working, but it's not quite there yet.  I'm using AMD64 with a Broadcom 4318. I'm trying to make it work in ndiswrapper, and I think there's a possibility the driver I'm using is the problem. Does anyone have this working on amd64, and if so, could they supply me with the driver? 

Thanks.

---

### Post by mike4ubuntu on 2006-06-09
False Alarm!

It's actually not working.  I had the wired connection still plugged in.  The NetworkManager Applet indicates no network connection.  When I iwconfig, I see an Access Point address now, where as it used to say invalid.  Not sure why it can't get a network connection.  Oh well, back to the drawing board.:cry:

---

### Post by mhosken on 2006-06-09
Because the bcm43xx driver only claims (internally) to know anything about supporting the following cards: 4301, 4307, 4312, 4318, 4319, 4320, 4324, 4324, 4325. If you have a card that reports a code other than these, the bcm43xx driver just won't see it.

---

### Post by mannequin on 2006-06-10
Thanks, [crag277]("http://ubuntuforums.org/member.php?u=52254"). I just got my Broadcom 4311 (On a Dell Inspiron e1705) working with this method. One slight variation, though. You have to use a newer version of ndiswrapper than what Ubuntu gives you. This is normally fixed by downloading it from Sourceforge, compiling it and installing it. Then proceed as normal. :)

One quick question. How do I get it to become eth1 instead of wlan0 so that the Network Manager stops glaring at me with it's red circle with a slash through it? I did this part:
> Type "sudo gedit /etc/modprobe.d/ndiswrapper"Change the one line in that file to read "alias eth1 ndiswrapper" ... But it doesn't work, it stays as wlan0. Anyone else have this problem and fix it?

EDIT: As I've found in a place or two, simply adding 'ndiswrapper' to /etc/modules doesn't work, either. Network Manager sees that the network is there, but can't sign on to a WEP shared key protected network. Any help is much appreciated! :)

Thanks for the help!
-M.

---

### Post by arottenmind on 2006-06-10
Hey i followed this How to, and im pretty sure i have the same card as this guide,

```
arottenmind@Laptop:~$ lspci | grep Broadcom\ Corporation
0000:02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

and it did not work.. There were no errors while doing the guide, for myself..

here is a link to my theard with more info in it:
[http://ubuntuforums.org/showthread.php?p=1119926#post1119926](http://ubuntuforums.org/showthread.php?p=1119926#post1119926)

Thanks

---

### Post by Trurl on 2006-06-10
Works beautifully for me, and I'm a complete newbie. I'm using a Broadcom 4309,  a.k.a. Dell 1450 mini PCI card. Thanks!

-Trurl

---

### Post by MetalMusicAddict on 2006-06-10
[QUOTE=mannequin]One quick question. **How do I get it to become eth1 instead of wlan0** so that the Network Manager stops glaring at me with it's red circle with a slash through it? I did this part:
 ... But it doesn't work, it stays as wlan0. Anyone else have this problem and fix it?[/QUOTE]
You can change it in the **iftab** file. In a terminal:

```
sudo gedit /etc/iftab
```

---

### Post by nickm on 2006-06-10
[QUOTE=arottenmind]Hey i followed this How to, and im pretty sure i have the same card as this guide,

```
arottenmind@Laptop:~$ lspci | grep Broadcom\ Corporation
0000:02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

and it did not work.. There were no errors while doing the guide, for myself..

here is a link to my theard with more info in it:
[http://ubuntuforums.org/showthread.php?p=1119926#post1119926](http://ubuntuforums.org/showthread.php?p=1119926#post1119926)

Thanks[/QUOTE]


Did you try my guide before you found Ndis didnt work?

---

### Post by Kawayanan on 2006-06-10
[QUOTE=Burke]Hi, I think I have it close to working, but it's not quite there yet.  I'm using AMD64 with a Broadcom 4318. I'm trying to make it work in ndiswrapper, and I think there's a possibility the driver I'm using is the problem. Does anyone have this working on amd64, and if so, could they supply me with the driver? 

Thanks.[/QUOTE]

I have a Compaq with a AMD64 chip and a Broadcom4318.  I had first tried the drivers that Compaq supplied, but they did not work.  After checking the [ndiswrapper wiki]("http://http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page"), I looked for the closest thing to my laptop in the [list of known working drivers]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List").  I chose the sixth entry under "B" and it worked great.  The download was an .exe, so I used cabextract to get the files out (cabextract is available throught synaptic).  I followed the instrucions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=190177&highlight=4318"), and everything worked the first time.  I have also made a howto for stopping network manager from always asking for your keyring password found [here]("http://www.ubuntuforums.org/showthread.php?t=192281").

Hope that works for you.

Kawayanan

---

### Post by mannequin on 2006-06-10
[quote=MetalMusicAddict]You can change it in the **iftab** file. In a terminal:[/quote]
Ah, thanks. I probably should have thought of it, but I thought it would be more complicated than that for some reason. :)

Next question: It's now seeing it as eth1, but Network Manager doesn't seem to be able to connect to my wireless network with my WEP shared key. Right now, I'm using the wireless by by-passing NM (Network Manager), but I would really like to see it work. Any suggestions?

Thanks for all of the help, by the way. This rocks. :)

-M.

---

### Post by arottenmind on 2006-06-10
[QUOTE=nickm]Did you try my guide before you found Ndis didnt work?[/QUOTE]

No i did not, but i had no Ndis drivers installed..

---

### Post by nickm on 2006-06-10
[QUOTE=arottenmind]No i did not, but i had no Ndis drivers installed..[/QUOTE]


:-k  so ...wut?

---

### Post by jessica on 2006-06-10
This worked very well. Thank You.

I'm using my wireless to post this right now, on a Dell Inspiron 1150. This solution solved a problem I was having (Error SIOCGIFFLAGS: No such device) and got it all working.

That said, the gnome network app you reccomend doesn't seem to recognize my wireless (only the wired ethernet connection), but it's fine. 

THANK YOU, for getting my wireless to work.

---

### Post by arottenmind on 2006-06-10
[QUOTE=nickm]:-k  so ...wut?[/QUOTE]

What i said was i Tried your guide after i found out the ndis drivers were not working.. thats what you asked?

---

### Post by SoHoTrader on 2006-06-10
Hi All,
 
 I've a Gatware M675 Laptop and it uses BCM94306MP wireless card.  I followed the instruction as the thread mentioned using  bcm43xx drive.  The good news is that I can use my wireless connection but one thing I don't like it's using B singnal and not G.  any driver out there so I can BCM94306MP driver and install on my UBUNTU.  I love G singal....:KS 

SohoTrader

---

### Post by eightysix on 2006-06-10
For the people who got Kismet to work with their bcm43xx cards, what did you put as your source? Or better yet, perhaps a sample kismet.conf file? Thanks.

---

### Post by thevic on 2006-06-11
I followed the instructions, trying both the .o driver and the one from my windows dir.  Both lead to a strange failure of bcm43xx.  After restarting, following the login screen of Gnome, X freezes.  I'm able to kill it (alt-ctrl-backspace), but if I let it run, switching to a different terminal screen (alt-ctrl-f1), every few minutes I get the error 

bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR

I hate to be the zeebra here; no one else seems to have this problem.  Nontheless, if you have any idea what's going on, please help.

For the record, this is a clean installation of 6.0.6, and my card is Broadcom Corporation BCM4306, rev 03.

---

### Post by boakes on 2006-06-11
Well I wound up having to use ndiswrapper for mine.  Apparently dapper doesn't support broadcom 4311 chipsets yet.  Follow this link to get it working for those who own a Dell Inspiron e1705 with the 4311 broadcom wireless card.  

[http://www.ubuntuforums.org/showthread.php?t=193350&highlight=1390](http://www.ubuntuforums.org/showthread.php?t=193350&highlight=1390)

---

### Post by nickm on 2006-06-11
[QUOTE=boakes]Well I wound up having to use ndiswrapper for mine.  Apparently dapper doesn't support broadcom 4311 chipsets yet.  Follow this link to get it working for those who own a Dell Inspiron e1705 with the 4311 broadcom wireless card.  

[http://www.ubuntuforums.org/showthread.php?t=193350&highlight=1390](http://www.ubuntuforums.org/showthread.php?t=193350&highlight=1390)[/QUOTE]


Theirs a better guide in this thread, its linked to on the first page at the bottom

---

### Post by mannequin on 2006-06-11
[quote=nickm]Theirs a better guide in this thread, its linked to on the first page at the bottom[/quote] Not quite true. It doesn't explain that some situations need an updated version of ndiswrapper. The BCM4311 is one of those that NEEDS the update in order to work. The ndiswrapper-utils package in Ubuntu is just too old for these wireless cards. ](*,)

Again, for the record, I have a Dell Inspiron E1705 with a BCM4311. (Actually, it isn't labeled as such, I think the label is Intel.)

-M.

---

### Post by mannequin on 2006-06-11
[quote=boakes]Well I wound up having to use ndiswrapper for mine.  Apparently dapper doesn't support broadcom 4311 chipsets yet.  Follow this link to get it working for those who own a Dell Inspiron e1705 with the 4311 broadcom wireless card.  

[http://www.ubuntuforums.org/showthread.php?t=193350&highlight=1390]("http://www.ubuntuforums.org/showthread.php?t=193350&highlight=1390")[/quote]
Say, did you happen to try and get it to work automagically with Network Manager?

-M.

---

### Post by bdk on 2006-06-11
It took me some time to totally figure out why my wireless wasn't working. I can see that the driver was installed but I wasn't getting the option to control the wireless via the notification area at the top. What normally looks like an RJ45 plug when configuring the wired portion of the computer.

It took reading some other posts to realize that I needed to comment out all but the loopback info in /etc/network/interfaces. Once I did that and rebooted, I now had the ability to configure and attach to a WPA (installed the wpasupplicant earlier too) wireless network. Very very cool.. I tried to read back through the initial posts in this how-to to see if commenting out the non-loopback entries in the interfaces file; couldn't find any...

An interesting hardware issue is that now my dedicated wireless on/off button on my laptop now seems to flash during wireless activity. Kinda like the LEDs on a wired NIC, this LED is the activity indicator for the wireless portion. Very cool indeed. 

Hope this can help someone else out.

-bdk
(HP zd7000 using the internal Broadcom wireless card)

---

### Post by boakes on 2006-06-11
[QUOTE=mannequin]Not quite true. It doesn't explain that some situations need an updated version of ndiswrapper. The BCM4311 is one of those that NEEDS the update in order to work. The ndiswrapper-utils package in Ubuntu is just too old for these wireless cards. ](*,)

Again, for the record, I have a Dell Inspiron E1705 with a BCM4311. (Actually, it isn't labeled as such, I think the label is Intel.)

-M.[/QUOTE]Nope, I didn't try it.

---

### Post by rubliwdrahcir on 2006-06-11
nickm,

Thank you for the How-To.  I am using an Apple iBook G4 1.43GHz PPC 1.5GB RAM 100GB HD with the fabled Broadcom BCM4318 [AirForce One 54g] (rev 02) wireless networking chip.  I followed the steps using the wl_apsta.o driver file.  That file helped my cause as I was having trouble getting any of the Apple AirPort*.dmg files mounted as an hfs filesystem in order to access the driver files.

The Gnome network manager worked like a charm!  I am happy to be posting this over an encrypted wireless network.  I haven't had wireless support since I wiped OS X and installed Ubuntu Breezy back in February 2006.  It is good to be back!

Thanks again,

r

---

### Post by mannequin on 2006-06-11
[quote=boakes]Nope, I didn't try it.[/quote]
Ah well... If you ever do try to get it to work via Network Manager, and actually get it to work, PLEASE let me know. :)

-M.

---

### Post by shorty0927 on 2006-06-12
Yes! Yes! Yes! 

I now have a Powerbook G4 15" with Broadcom 4306 card, functioning wireless AND I was able to get WPA working with WPA Supplicant.  I was able to get the connection working using NetworkManager, too--I didn't have to install Wi-Fi Radar (which I had issues with about a month ago).

Thank you, nickm!  I've been trying to get wireless working on my Linux installation for two months.  Your instructions are good and easy to follow.  :)

---

### Post by frogotronic on 2006-06-12
Worked with Dell Inspiron 8100 laptop using an external PCMCIA MN720 Microsoft wireless card.  This wireless card uses the broadcom chipset.  Used 'wl_apsta.o' to extract firmware.  I am using the MN720 drivers ([www.driverguide.com](www.driverguide.com)) via the laptop wireless windows GUI (that I download using AUTOMATIX).  I used acable connection to get set up at first.

Little trouble storing the newtork password/keyring - have to sort that out.

-CH

---

### Post by Tatey on 2006-06-12
I'm using a G4 iBook with the BCM4306 (Rev3) and GNOME-Network-Manager. I'm connected to my wireless AP through WEP and completely satisfied. After the inital reboot, I had to manually reload the module (sudo modprobe bcm43xx) and everything worked. Cheers to Nickm for producing an execellent HOWTO.

---

### Post by mike4ubuntu on 2006-06-12
It's strange, it only seems to work when I have the wired port plugged in.  It does seem to respond to the wireless IP address with a ping in addition to the wired IP address.  However, if I unplug the wired lan cable, the wireless IP address doesn't ping anymore.  I'm still working on it.  Any suggestions?

eth0 is the wired port and eth1 is the wireless port.


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"**MyNet**"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:12:34:56:78:90
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:34:56:78:90
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=100/100  Signal level=-179 dBm
                    Extra: Last beacon: 4022ms ago

sit0      Interface doesn't support scanning.

---

### Post by SentientFluid on 2006-06-12
Just wanted to add a thank you and a "worked for me".  I appreciate all the work people volunteer in making all this information available. :)

And your steps worked like a charm on my 14" iBook G4 (Late 2004).  A reboot wasn't even needed where indicated.  Right after I installed the network manager I noticed a new icon in the notification area.  I clicked on it and it was already picking up my neighbours Linksys network. :)

So now I can surf to my heart's content at out local coffee shop. :)

---

### Post by ajred on 2006-06-13
Hi there .   

Ok first off, I have a bcm4306 wireless card (v03) in a hp ze4404us laptop.  I followed the steps completely.  After rebooting on the last step I see that that network manager does see my ssid so I go ahead and click wireless , then asks me for the key (using WEP)but will just not connect.  Just to make sure my key was right I restarted in windows and tested my WEP key there and all was fine.  So not really sure where to go from here,   any ideas?  Thanks

---

### Post by tehquickness on 2006-06-13
I have a dell inspiron 9100 with a BCM4306 and it did not work for me. I can scan for wireless networks but i can not connect to any of them. Network manager also does not  Recognize the card. Any ideas?

---

### Post by ????? on 2006-06-13
It stopped working.. I tried blacklisting ndiswrapper, modprobing and it "broke".

---

### Post by mike4ubuntu on 2006-06-13
Still is not working.  At least the Network Manager Applet doesn't see any networks.  However,

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13...:01
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:On
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=100/100  Signal level=-147 dBm
                    Extra: Last beacon: 36ms ago
          Cell 02 - Address: 00...:02
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:On
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=100/100  Signal level=-143 dBm
                    Extra: Last beacon: 132ms ago
          Cell 03 - Address: 00...:03
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:On
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-201 dBm
                    Extra: Last beacon: 568ms ago
          Cell 04 - Address: 00...:04
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:On
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-172 dBm
                    Extra: Last beacon: 91ms ago
          Cell 05 - Address: 00...:05
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:On
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=100/100  Signal level=-216 dBm
                    Extra: Last beacon: 6ms ago

sit0      Interface doesn't support scanning.
----
so if the scan can see, why can't the Network Manager see it?

---

### Post by gaucho on 2006-06-13
I'm at a loss... :-({|= 

I have a Dell Inspiron XPS and am using the Linksys WPC54GS V1.1 card. After following the instructions for the bcm43xx driver install everything works as long as I have no WEP encryption.

I also installed Network Manager per the instructions but it does not see my wireless at all where as the default Network Monitor does and says I am connected (all bars full green - but truly I am not connected);

Any ideas? I feel soooo close, yet... [-X

---

### Post by mike4ubuntu on 2006-06-13
I just checked [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware) and saw that my driver is supported:

Broadcom BCM43xx / Airport Extreme

$ lspci | grep Broadcom\ Corporation
0000:01:02.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)

but the NetworkManager Applet still doesn't see the networks.

---

### Post by clonist on 2006-06-13
[QUOTE=mike4ubuntu]I just checked [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware) and saw that my driver is supported:

Broadcom BCM43xx / Airport Extreme

$ lspci | grep Broadcom\ Corporation
0000:01:02.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)

but the NetworkManager Applet still doesn't see the networks.[/QUOTE]
I believe Network Manager only handles interfaces that **aren't** listed in /etc/network/interfaces. What I did was gedit /etc/network/interfaces and remove everything but the loopback reference. 

This is my /etc/network/interfaces:
auto lo
iface lo inet loopback

Edit- and I know this may sound strange, but my wireless device and networks were not detected until I removed their configuration from **Network Monitor** and restarted. Good luck! :)

---

### Post by eems01 on 2006-06-13
Worked perfectly for me using the wl_apsta.o file.  Connects at 802.11g with WPA2.
Clean dapper install on Compaq Presario R3200.  Thanks!

Update:  Chipset was BCM4306 (rev 03) and did not need to install wpasupplicant to get WPA2 to work!

---

### Post by Sepper on 2006-06-14
I just wanted to tell everyone to first check is your particular hardware is supported by the new bcm43xx kernel driver...
The list is here:
[http://openfacts.berlios.de/index-en.phtml?title=Bcm43xxDevices](http://openfacts.berlios.de/index-en.phtml?title=Bcm43xxDevices)
or here:
[http://bcm43xx.berlios.de/?go=Devices](http://bcm43xx.berlios.de/?go=Devices)
and you can get the subsystems numebr by following the instructions here:
[http://openfacts.berlios.de/index-en.phtml?title=LspciExamples](http://openfacts.berlios.de/index-en.phtml?title=LspciExamples)

My own 4318 14e4:0449 is not yet supported (on a Gateway MX7520H)

---

### Post by mike4ubuntu on 2006-06-14
Yes, I discovered too, that when I took all of the wireless settings out of the /etc/network/interfaces and only left the loopback and the wired port, the Network Manager did allow me to attempt to connect to other network.  The NM prompted me for the network name and authentication scheme.  However, it still didn't connect.  I read on one of the other threads, that it may only work with open and not shared key for WEP.  I'm going to try that to see if it works.
[http://www.ubuntuforums.org/showthread.php?t=187571](http://www.ubuntuforums.org/showthread.php?t=187571)

Also, my laptop is a Lenovo Series 3000 c100, which indicates that it's actually a broadcom 4319, but it seems to get detected as a 4318.  That may also be part of the problem.  Does anybody else have this configuration working?

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:Off/any  Nickname:"Broadcom 4318"
...

$ lspci | grep Broadcom\ Corporation
0000:01:02.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)

---

### Post by dinkumator on 2006-06-14
I have this same card, shows up as "Unknown device 4319"... but I got it to work using the wireless drivers shipped with windows (bcmwl5.sys 3.140.16.0) on it instead of the wl_apsta.o

so now i can vote that it did work =)

---

### Post by Trurl on 2006-06-14
I reinstalled ubuntu and was having problems getting the wireless working again, but eventually it worked, and I came across a few strange things that might help.

My wireless card is controlled using a combination of key-strokes. In linux, they don't appear to do anything. In windows, they toggle on/off. After being unable to get the wireless working in linux, I booted back into windows and manually turned on the card on (using the key-strokes). I also found that my wireless card was disabled in windows when the ethernet cable was plugged in. Anyway, booted back into linux and everything worked fine, although I had to right mouse the network monitor and tell it which network to choose. 

What might also help is the instruction that says something to effect of: "you can drag the '.o' file into the terminal after the commad bcm43xx-fwcutter ". I didn't do that the first time around and everything worked, but this time I did this before booting back into windows, so this may have been responsible for getting things working although I'm not sure.

Thanks again for the walkthrough and good luck to anyone still having issues.

-Trurl

---

### Post by adssse on 2006-06-14
Just finished following the guide and my BCM4306 wireless is working great. I wanted to say thanks for the guide, as I sincerely appreciate it.

---

### Post by ajred on 2006-06-14
Well after trying all different drivers for this card (bcm4306 rev3), I finally got it working with driver  sp28537 from the hp site.  WPA and WEP are both working correctly.   I also upgraded my routers (wgt624v2) firmware, not sure if that made a difference or not. Thanks for all the great posts!!   :D

---

### Post by oldgoat on 2006-06-14
nicm - yo - this was spot on - I saw this post when I was in breezy and that was the turning point in the dapper decision - Great Job!!

---

### Post by ntarun on 2006-06-15
Thank you so much,
Your guide worked for me and its extremely satisfying. 
Thanks a ton.
:)

---

### Post by kabben on 2006-06-15
i dont normally bother with registering or posting on forums. but i have to say "thank you" to the guy that brought us this. What a fantastic guide!

worked first time and not a single hic-up. For those that don't have access to the net via wired net access to begin with you can just download the fwcutter and "make" the file btw... yes some of us arnt that great with linux (just giving it another shot atm myself).

Great version of linux, by far the best of any distro ive tried and with this and automatix it was a breeze to setup.

Never will use ndiswrapper again thankgod !

Dean.

ps. Much thanks to this community and the member that posted this guide especially.

---

### Post by compwiz18 on 2006-06-15
I posted a HOWTO for Broadcom 4318 cards, the ones that *don't* work with this method.  It can be found [here]("http://ubuntuforums.org/showthread.php?p=1140976").

---

### Post by va5ja on 2006-06-15
hi there... here's my problem... i finally got network manager working, it's a great thing... i followed this instructions:

In short: Nine steps to WPA encrypted Wifi with Ubuntu Dapper Drake:

1. sudo apt-get install wpasupplicant (might already be installed)
2. sudo apt-get install network-manager-gnome
3. sudo gedit /etc/network/interfaces — Comment out everything but “lo” entries in that file
4. Create a file called /etc/default/wpasupplicant, add entry ENABLED=0
5. Reboot your system
6. Left-click the network manager icon in Gnome and select your wireless network
7. Follow the prompts for password, type, etc.
8. It will ask you to choose a password for your new “keyring”.
9. Be happy ;)

now my network manager works, my card detects available wireless networks and i can select wpa and wpa2... all perfect... but when i fill in the correct username, pass, protocols nothing happens... my iwconfig shows this:

ath0      IEEE 802.11g  ESSID:"eduroam"
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:11:5C:C7:1F:70
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry: off   RTS thr=250 B   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:292  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:109  Invalid misc:109   Missed beacon:0

is my bit rate too low? signal strength too low? how can i adjust my card properties... in windows all works great and fast to...

any ideas, thanks in advance

---

### Post by dscataglini on 2006-06-16
Thanks nickm and xXx 0wn3d xXx. 
At first I could see the card but no networks. (nickm and I have the same exact card).
I went through the steps and I had the wireless working. Then the day after it stopped working and couldn't get it to work again. 
Nothing i tried after that was working. I could see the networks but couldn't join any. Only once it looked like I was able to join one but then It dropped it.

Then I saw 0wn3d post and did the blacklist thing and voila' it works.
Thanks guys

Diego
YAN (yet another newbie)

---

### Post by meschaffe on 2006-06-16
The only way I can get online feasably at the moment is via wireless connection - any purely offline solutions? I can get online through Windows right now, so is there anything I can download and take into Ubuntu to do the entire fix offline?

---

### Post by nickm on 2006-06-16
[QUOTE=meschaffe]The only way I can get online feasably at the moment is via wireless connection - any purely offline solutions? I can get online through Windows right now, so is there anything I can download and take into Ubuntu to do the entire fix offline?[/QUOTE]
 

Yeah, its the first point in the guide, i'v never done it before so i cant tell you how to do it, but its possible that way

---

### Post by meschaffe on 2006-06-18
All I need to know is where fwcutter and netmanager are coming from and I should be able to figure out the rest.

---

### Post by georgeous on 2006-06-18
[QUOTE=nickm]If you find your driver comes in a windows EXE format, typically this will just extract the drivers and can be run using Wine and then collected from your wine directory in the same places you can find them in windows[/QUOTE]

I'm not sure if this applies to all .exe files, being a bit of a noob, but dell drivers that come in a .exe format can be extracted using 'unzip' in the terminal...

---

### Post by nickm on 2006-06-18
yeah, thats right too, or you can rename it .zip and doubleclick

i never got round to putting that in #-o

---

### Post by Viserys on 2006-06-18
Hi.

First of all, thanks for the fabulous tutorial.

However, I have a minor problem.

I followed all of the instructions as listed, and everything worked! Splendid!

I then went on to configure my computer, installing Python, MOL (I'm running an iBook G4, 1.33 GHz), etc. Later that day I went to use wireless again after rebooting, and, sadly, it failed; NetworkManager claimed that I was connected, but I couldn't do anything internet-related.

That night, on a whim, I pulled out my ethernet cord and tried wireless again. Bizarre... it was working.

So, today, I booted into Ubuntu. I tried everything, even reading this entire thread while wired. NetworkManager still thought I was connected to my network, but I couldn't use the web! I booted up WifiRader, and it said that I had a local IP and was connected as well.

What's going on? :(

I'm about to snap here, one of two things is possible:

I'll never boot into linux again (I simply can't live with wired ... my cables are too short and I have to sit on the floor :P).
I'll reinstall Dapper, try again, and pray. This can hopefully be avoided.

EDIT for clarification:

I do NOT have that supposedly evil card.
I'm using the .sys driver linked in the first post.
I've tried modprobe to no avail.
WifiRadar assures me that I have an IP, but I'm unable to connect to anything -- even my router's HTTP interface.
I can see and connect to wireless networks, just not do anything while connected.

---

### Post by JasonPN on 2006-06-19
Wow...this couldn't have been easier.  Thanks.  :)

---

### Post by traherom on 2006-06-19
[QUOTE=JasonPN]Wow...this couldn't have been easier.  Thanks.  :)[/QUOTE]My feelings exactly.

One word of warning, however: remove all ndiswrapper drivers (if you started out trying to do it that way) before attempting this.

---

### Post by meschaffe on 2006-06-21
I'm up and running now. Thanks for the guide. Hopefully it'll still hold up once I lug my computer back home.

---

### Post by pcbodger on 2006-06-21
Awesome - worked like a dream once I twigged that my RJ45 cable could reach from my office to the router and got a LAN connection :rolleyes:

---

### Post by ayanefan on 2006-06-21
Followed the instructions and worked great!   THANK YOU!   Oh, I have Rev 2 of the broadcom bcm4318.

---

### Post by Viserys on 2006-06-21
I was able to fix my issue by disabling the builtin firewall.

---

### Post by Bytewalker on 2006-06-24
i accidently removed the /lib/firmware directory lol
is my system totally screwed now or can i restore it?

---

### Post by usfour on 2006-06-25
I spent the whole evening trying to get this working for my Acer Aspire 5002 following other links and instructions.  Following yours took me 5 minutes.  Brilliant.  Thank you.  

How do you view all the available access points?

Thanks again.

---

### Post by bakreule on 2006-06-25
Thanks for the great guide!  I'm having a little trouble getting the wireless card to get recognized though:

My card (which seems like the proper one for this card):
*Broadcom Corporation BCM4306 802.1b/g Wireless (rev 03)*

'*lsmod | grep bcm*' returns this
bcm43xx
ieee80211softmac (used by: bcm43xx)
ieee80211 (used by: bcm43xx,ieee80211softmac)

I followed the instructions here and everything seems to have passed without problems. Unfortunately, upon rebooting, the Wireless Manager says "No Network Connection". The network manager that comes with Ubuntu says that wireless connection eth1 exists, and is active, and it's true that 'ifconfig' shows that eth1 is active (why eth1? why not wlan0?), but eth1 has no IP attributed, which usually means that it couldn't connect to the router. I've tried it open, and with WEP, with no success.

Have I missed something? This is really frustrating....

One last thing, this card DID work on the VectorLinux install that I had before. I then loaned the card to my girlfriend so she could use it on her Win98 box. Ever since that day, I couldn't use the card on my Vector box. It seems I'm having the same problem with my Ubuntu install....

---

### Post by Jabithew on 2006-06-25
True genius. Having spent weeks trying to get the bloody thing working, Ifollowed this and it took a quarter of an hour. And most of that was download time. Thanks!

---

### Post by usfour on 2006-06-25
[QUOTE=bakreule]...I followed the instructions here and everything seems to have passed without problems. Unfortunately, upon rebooting, the Wireless Manager says "No Network Connection". The network manager that comes with Ubuntu says that wireless connection eth1 exists, and is active, and it's true that 'ifconfig' shows that eth1 is active (why eth1? why not wlan0?), but eth1 has no IP attributed, which usually means that it couldn't connect to the router. I've tried it open, and with WEP, with no success....[/QUOTE]


I just got my wireless to work last night.  The network manager shows 'No Network Connection' but I do have a connection with my Access Point.  I do recall reading that there is a bug in the software.  Have you tried connecting with no wireless security.  ie. Broadcast SSID, no WEP/WPA, etc...   Your eth1 is active.  Give it a shot.  Unplug the ethernet cable.  Maybe it does work.   :D

---

### Post by bastupungen on 2006-06-25
What driver did you use?

If you have them can you mail me them to jonatansf(at)mail.com, or link them to me.

It would be really nice

---

### Post by bastupungen on 2006-06-25
Hello!

Thanks for the nice guide! it was really good and easy, had i nice tone! like it like it..

Though i am having a problem that wep doesn't seem to work. I used the driver you
supplied. I am using the airport express card on an ibook G4. How do i change firmware in the card? do i just remove the files that i extracted or do i have to do anything else?

When i check which card it is it says its an;
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Anyone know a good firmware for it?

---

### Post by ifrflyer on 2006-06-26
Thank you nickm- worked like a charm for me on a Dell Inspiron 5150

---

### Post by mikl on 2006-06-26
Hi there, 

I've tried your guide on a HP Pavilion zv5000 with a BCM4306 and both WPA and WPA2 AP's, but I can't connect - it finds the network, and I type in my key, and it tries to connect, but it never succeeds...
I get a lot of this on my dmesg:

[17179702.092000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179702.112000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179702.132000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179702.152000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179702.168000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179707.004000] printk: 249 messages suppressed.
[17179707.004000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179712.000000] printk: 257 messages suppressed.
[17179712.000000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179717.012000] printk: 258 messages suppressed.
[17179717.012000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179721.996000] printk: 257 messages suppressed.
[17179721.996000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179727.012000] printk: 259 messages suppressed.
[17179727.012000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179732.004000] printk: 258 messages suppressed.
[17179732.004000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179737.012000] printk: 259 messages suppressed.
[17179737.012000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90
[17179742.004000] printk: 257 messages suppressed.
[17179742.004000] SoftMAC: Open Authentication completed with 00:18:39:89:5e:90

---

### Post by usfour on 2006-06-26
[QUOTE=bastupungen]What driver did you use?

If you have them can you mail me them to jonatansf(at)mail.com, or link them to me.

It would be really nice[/QUOTE]

I followed the instructions exactly at the beginning of this thread.  I used the recommended drivers there.

---

### Post by bakreule on 2006-06-27
[QUOTE=usfour]I just got my wireless to work last night.  The network manager shows 'No Network Connection' but I do have a connection with my Access Point.  I do recall reading that there is a bug in the software.  Have you tried connecting with no wireless security.  ie. Broadcast SSID, no WEP/WPA, etc...   Your eth1 is active.  Give it a shot.  Unplug the ethernet cable.  Maybe it does work. [/QUOTE]

eth1 has no IP address attached to it, so it's not going to work. I've tried both WEP and no security, with no success; the card refuses to talk with my access point. I guess I'll just have to play with it....

---

### Post by Jhodytropical on 2006-06-27
Thank you very much. I have a Gateway 7326GZ and my Broadcom 'BCM4306' was driving me nuts to install your method helps me install it in no time.

I am now one step closer to ditch WINDOWS.

Many Thanks

---

### Post by GoldenH on 2006-06-27
I managed to get it working by

- Install bcm43xx-fwcutter with **sudo apt-get install bcm43xx-fwcutter**
- extract firmware from [http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o) with sudo **bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o**
- goto System -> Administration -> Networking and make all connections report as "Not configured" by deactivating all of them and unchecking the "enabled" button under their properties.
- activate the wireless connection (eth1 for me), goto properties, enable it, select the proper network, reboot.

then in order to make it work, i click on my network connection icon, then click configure, and then properties. it immediately loads up, and i cancel out of all the windows (pressing OK tends to break it again until I reboot)

if I don't have an ip, i run dhclient

one other interesting thing: if i do a dmesg I see this happening alot:

[17179807.388000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132

it happens in between network restarts, any idea what it means?

and the message when it finally works:
[17179817.712000] SoftMAC: Open Authentication completed with 00:09:5b:9e:48:e6
[17179817.724000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179827.816000] eth1: no IPv6 routers present


i've noticed when it doesn't work, I often have an IPv6 IP address, but not a v4 IP address, any idea why this might be?

edit: found out some more stuff, 

whenever i boot, i get an "ADDRCONF(NETDEV_UP): eth1: link is not ready" error. apparently this happens when devices are reassigned after boot. I think this makes sense, maybe the internal network cards may actually be on a USB bus? 
This usually goes away if you cancel out of the properties window  enough times. then once it says it is ready do a dhclient. you may have to do dhclient again later, as the wired connection comes back alive and wants to play, but after the second time i haven't had it come back until after I restart when I have to do this all over again.

and, apparently if i try and plug in a Lan cable (because it's alot faster), then it gives me a IRQ conflict and the Incomplete code in keymac_write() error. The only way I know of to clear the IRQ conflict is to reboot my computer. Logging off doesn't work.

Also, I have a bandwidth of about 5 kb/s. This isn't really noticeable when I am just using internet, since my server is just connected to a dialup ISP, but, it gets really slow when i try to use a virtual desktop or transfer files and it may cause the connection to drop. Very strange.

---

### Post by Kalinda on 2006-06-27
Wow! Thanks so much! NetworkManager and wireless both work great and it was so easy! Thanks for making your guide n00b-friendly :)

I have one problem, though - WEP doesn't work. I believe this is common, as a bug about it was reported. I think some more stuff is required to get WPA working, however.. so I will try it later.

Also, every time I boot now, KDEWallet attacks me with a password dialogue, even though my wireless doesn't try to automatically connect with security on. It also does it without any security (it connects by itself then, though), but it all started when I turned on WEP >><<

I'll have to look around some more; I think others have had these problems.

Thanks, though!

---

### Post by bigken on 2006-06-28
Cheers mate worked a treat with my linksys WMP54G :D

---

### Post by trl-gen on 2006-06-29
First of all thanck you for the guide it worked very well.

I've still got one problem though. For some reason Network Manager can't see my wireless connection. My wired connection is no problem for NM. Also I configured my wireles temporarily with the standard networking applet and it works that way. I still would like to use Network Manager, it's got more options and you at least know if you've got a good connection or not. Somebody got any idea what's wrong with NM???

---

### Post by usfour on 2006-06-29
[QUOTE=trl-gen]First of all thanck you for the guide it worked very well.

I've still got one problem though. For some reason Network Manager can't see my wireless connection. My wired connection is no problem for NM. Also I configured my wireles temporarily with the standard networking applet and it works that way. I still would like to use Network Manager, it's got more options and you at least know if you've got a good connection or not. Somebody got any idea what's wrong with NM???[/QUOTE]

I have the same problem with Network Manager.  If I can get that working, life would be sweet.

:D

---

### Post by RezoApio on 2006-06-29
Thanks a lot !!! It worked like a charm for me. I had the difficult version (edit: I mean by that the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)) you had mentioned but still it worked.

I had to get a new bmcwl5.sys however cos the one from the CD was not supported by the cutter. It took me some times to get it due to a difficulty to download with the firefox on this dapper version... (I will try to make it fine later).
But with the new sys file from the linksys support web site, it was ok to cut (just 2 messages about how bad it is to cut from an old driver but worded like a warning)
After that I just had to remember to rmmod the ndiswrapper, and remove the line from the /etc/modules to make it and it was ok. 
sudo ifup eth1 (from the /etc/interfaces already set up for my wep password) and I had a nice ip address from the dhcp server.

Only thing that did not work at all is this new gnome network manager but as the standard network manager is just cool with the lovely green indicator of the wifi power ;-) I will just remove it completely from my system.

Once again just cool topic. Thanks a million.
William

---

### Post by allnameswereout on 2006-06-29
Is this howto for x86 only? Maybe add that notice given Ubuntu supports more and more architectures.

I'm searching for a WiFi card which works on any architecture...

---

### Post by stanswx on 2006-06-29
This works great on my Dell Inspiron 5100 with my Dell Truemobile 1370 802.11b/g card!! I couldn't get the gnome thing to work either, it just kept looking for my ethernet connection. Thanks a bunch!!

Stan

---

### Post by boakes on 2006-06-30
[QUOTE=nickm]Theirs a better guide in this thread, its linked to on the first page at the bottom[/QUOTE]Where?  I don't see any links except for what you posted.  Sorry for taking so long to respond.

---

### Post by jeannie on 2006-06-30
Thank you for making this available.  It worked and it was easy.
=D>

---

### Post by jwest131 on 2006-07-01
Thanks worked like a charm!

---

### Post by pbeck on 2006-07-01
Great how-to! I feel like i am very close to getting mine to work. I have an emachines 6809 with the broadcom wireless chip.. i finally got the wireless light to come on after reinstalling ubuntu, but now even with the light on, it wont find any wireless networks even though i am sitting next to the router at home. iwconfig looks like this:
 lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

using the modprobe command doesnt work either.. what is that supposed to do anyways? anyways, i'm kind of a newbie, but seems like problems like these abound!

thanks!

---

### Post by ZombiekE on 2006-07-01
Thank you very much for your help =D>. I am posting this message from my laptop. I have a 4318 and I didn't even need to reboot. I am going to spend some months abroad and I needed to be able to use wireless connections. Hadn't it been for this how-to, I would have had to use Windows just for this problem.

---

### Post by The_Dewster on 2006-07-01
Worked like a charm for me on my IBM Thinkpad T21 with a Motorola WN825g card.  Thanks!

---

### Post by dirtvoyles on 2006-07-01
This worked great for me, but can anyone tell me how to get the gnome network manager GUI to start with the system at boot/xstart?

---

### Post by DaveAtFraud on 2006-07-01
I'm running into what appears to be a timing problem between bcm43xx and my WAP.  The system (HP Pavilion zv6015) is running FC4 x86_64 with the 2.6.17-2139_FC4 kernel.  Everything appears to be clean but I get:

...
ieee80211_crypt: registered algorithm 'WEP'
bcm43xx: set security called
bcm43xx:    .active_key = 0
bcm43xx:    .level = 1
bcm43xx:    .enabled = 1
bcm43xx:    .encrypt = 1
SoftMAC: Associate: Scanning for networks first.
SoftMAC: Associate: failed to initiate scan. Is device up?
bcm43xx: PHY connected
bcm43xx: Radio turned on
bcm43xx: Chip initialized
bcm43xx: DMA initialized
bcm43xx: 80211 cores initialized
bcm43xx: Keys cleared
SoftMAC: Associate: Scanning for networks first.
SoftMAC: Start scanning with channel: 1
SoftMAC: Scanning 14 channels
ADDRCONF(NETDEV_UP): eth1: link is not ready
Losing some ticks... checking if CPU frequency changed.
SoftMAC: Scanning finished
SoftMAC: Queueing Authentication Request to 00:12:17:7a:b6:f6
SoftMAC: cannot associate without being authenticated, requested authentication
SoftMAC: Queueing Authentication Request to 00:12:17:7a:b6:f6
SoftMAC: cannot associate without being authenticated, requested authentication
SoftMAC: Sent Authentication Request to 00:12:17:7a:b6:f6.
SoftMAC: Sent Authentication Request to 00:12:17:7a:b6:f6.
SoftMAC: Open Authentication with 00:12:17:7a:b6:f6 failed, error code: 13
SoftMAC: Authentication response received from 00:12:17:7a:b6:f6 but did not
request authentication.
bcm43xx: Radio turned off
bcm43xx: DMA 0x0200 (RX) max used slots: 1/64
bcm43xx: DMA 0x0260 (TX) max used slots: 0/512
bcm43xx: DMA 0x0240 (TX) max used slots: 0/512
bcm43xx: DMA 0x0220 (TX) max used slots: 2/512
bcm43xx: DMA 0x0200 (TX) max used slots: 0/512
...

That is, the driver times out waiting for an authentication response from the WAP and then complains when the response finally arrives. Is anyone else seeing anything like this?  The WAP is a D-Link with both encryption and MAC address authentication required.

Cheers,
Dave

---

### Post by JoshNCSU22 on 2006-07-02
After following the directions to add the Universe Repo I still cannot find the correct packages...

josh@ubuntu:~$ sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package bcm43xx-fwcutter

I've done a sudo apt-get update and it looks like it's grabbing the right repos...any suggestions?

---

### Post by ben s on 2006-07-02
Colour me impressed -- it worked very the first time on my 1.67GHz Powerbook G4 -- running off the CD no less!  I wanted to make sure my wireless was going to work before I committed to puting Ubuntu on the hard drive.

I'm not used to Linux related things working first time on my Powerbook.  :)

---

### Post by trevymond on 2006-07-03
hey i'm new to this whole linux-gnome world and i installed it coming from using windows my whole life and i came up with a problem when trying to install my broadcom wireless card, i followed the steps above and i came up with lots of errors along the way, am using dell inspiron 1300 notebook and ubuntu isn't recognizing my wireless card can someone please help me out i'm kind of new to this OS so can you give me a step by step a little simple so i can understand

---

### Post by cheeseman557 on 2006-07-03
I followed all the steps and at the end when I do modprobe bcm43xx, I get the following:

WARNING: Error inserting ieee80211softmac (/lib/modules/2.6.15-25-386/kernel/net/ieee80211/softmac/ieee80211softmac.ko): Operation not permitted
FATAL: Error inserting bcm43xx (/lib/modules/2.6.15-25-386/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko): Operation not permitted

I have a Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) card.  Thanks for your help.

---

### Post by Corfy on 2006-07-03
[QUOTE=TheAngryPenguin]It didn't work for me.  I have a Dell Latitude D400 with a "0000:01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)" wireless card.  I tried with the files from the first post as well as with a .sys that's known to work well with ndiswrapper.  In all cases, I've ended up with a kernel panic right as the wireless card became active.  To anyone else with this particular flavor of Broadcom, here's what I've done to get it to work (and I won't go that much into detail since most of this is documented very well elsewhere...):

1) Install ndiswrapper-utils

2) Download the [TrueMobile 1400 (BCM4309 - 802.11a+b+g)](http://ftp.us.dell.com/network/R63259.EXE) driver package from Linuxant's [site](http://www.linuxant.com/driverloader/drivers.php).

3) Rename R63259.EXE to R63259.EXE.ZIP and open with Archive Manager -- extract bcmwl5.inf and bcmwl5.sys from /TMSetup

4) Do the ndiswrapper voodoo with the file(s) above.

5) Blacklist bcm43xx

6) Add ndiswrapper to /etc/modules

7) Reboot

Now, if I could only get NetworkManager to work with ndiswrapper...[/QUOTE]


I want to thank you for this post. My Dell Latitude D600 has the exact same TrueMobile 1400 card, and I had the exact same problem with the kernel panic. Your directions got me up and running, which i have been trying to do for nearly a week now.

---

### Post by Harman Smith on 2006-07-04
Excellent guide! Having not lost the main draw of my *laptop* will makemy card to fun meauser of Ubuntu; I had tried Fedora but couldn't get my card to function. This is wonderful :D

For reference, I am a user of the *antiquated*, ahem, *older* Broadcom chipset in a Presario 2500:

```
0000:00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

No guide mentions this BCM4306 rev 02 combo specifically but Imangaed and am quite pleased with the results.

And this guide told me to turn on the Universe repositories, which no other one did*coughcough*, even thought he rest of the steps might be all well. It might not have mattered for someone more familiar and expirenced but for a n00b like me, it was a deal breaker.

Good guide, I highly recomend it for anyone expirenceing Broadcom issues.

---

### Post by chaag on 2006-07-04
Thanks much for this, I am using Ubuntu 6.06 on a Dell Latitude D600 with the Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03). This post helped me a lot. One note, the gnome network manager does not work on this set up, wifi-radar does

One warning, once you install bcm43xx-fwcutter, other instructions incate you should simply run:

[HTML]/usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh[/HTML]

However, this script appears to have an error in it. Note this for loop:

[HTML]
for i in *.fw; do
  mv -v $i /lib/firmware/$i;
done
[/HTML]

The firmware binaries end up in the wrong directory. They need to be "in" a sub directory of lib firmware, named for you current (or all) kernel. For example, here is my /lib/firmware

[HTML]
$ ls -F /lib/firmware/
2.6.15-23-386/  2.6.15-25-386/

[/HTML]

The firware binaries must be in the current release dir or both of the directories. Either move the binaries to the correct place or modify the script as follows:

[HTML]

#get the current release
rel=`uname -r`
for i in *.fw; do
        mv -v $i /lib/firmware/$rel/$i;
done

[/HTML]

Note: You will have manually move these files each time you upgrade the kernel AND, there is no guarantee that the binaries will continue to work with each new release, so it may be neccessary to aquire new firmware binaries with each new kernel.

---

### Post by krazyd on 2006-07-05
Has anyone got their broadcom chip showing correct signal strength in Network Manager?

I've tried using both the bcm43xx and ndiswrapper for my 4318 card and it's constantly on 100%.

By the way, ndiwrapper still works much better for me than bcm43xx. Way more range / router doesn't have to be as close for a good connection.

---

### Post by mannequin on 2006-07-05
[quote=krazyd]Has anyone got their broadcom chip showing correct signal strength in Network Manager?

I've tried using both the bcm43xx and ndiswrapper for my 4318 card and it's constantly on 100%.

By the way, ndiwrapper still works much better for me than bcm43xx. Way more range / router doesn't have to be as close for a good connection.[/quote] You have it working with Network Manager and ndiswrapper? Does it automatically work, or do you have to do something else? I know that you have to remove everything but lo from /etc/nework/interfaces. (That's to stop that suggestion from coming up again. :) ) Any help would be appreciated! I'd rather use WPA or WPA2 then WEP, but WEP is the only option with Network Monitor.

Thanks!
-M.

---

### Post by UeB on 2006-07-05
EDIT: sorry my mistake this msg can be deleted

---

### Post by sigmason on 2006-07-05
I have my bcm4318 based Linksys WPC54G working in Ubuntu, Kubuntu and Xubuntu.  However, I've noticed a few minor things.

Has anyone else noticed:

1. If you remove the card hot from the PCMCIA slot, although UDEV reloads it, it doesn't successfully rebuild the last WiFi association even with the proper settings in the interfaces file?  In the iwconfig screen you'll see the WiFi interface with no associated access point.

2. The rate setting doesn't work from inside interfaces...if you do 'wireless_rate 54M' it doesn't stick, but if you do 'sudo iwconfig eth1 rate 54M' it does stick.

3. Why does the interface for the wireless card alternate from wlan0 when there is no available network it is associated with...to eth1 when I'm connected to my home network...I have all my files setup for eth1...I don't have a reference to wlan0 anywhere so where is that from?

Now, I have tried the network-manager package and it helps with problem 1...in the sense I don't need to resort to terminal configuration to bring the card back.

I have also gotten past number 2 by using udev rules but that seems like overkill.

I thinking this all might be because I'm using the latest Linksys driver from the Linksys site....I'm hoping if others don't have this behavior that's all that's wrong (even though the firmware works in every other way I've tried.)

What is the suggested version of the Linksys driver to hit with the fwcutter utility?

sigmason

---

### Post by n00bWillingToLearn on 2006-07-06
[quote=JoshNCSU22]After following the directions to add the Universe Repo I still cannot find the correct packages...

josh@ubuntu:~$ sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package bcm43xx-fwcutter

I've done a sudo apt-get update and it looks like it's grabbing the right repos...any suggestions?[/quote]

Could you post your etc/apt/sources.list ?

---

### Post by JoshNCSU22 on 2006-07-06
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted



deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse
deb [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) breezy main restricted universe multiverse
deb [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) breezy-security main restricted
deb [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) breezy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse

#deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) breezy-backports main universe

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe
#deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free

---

### Post by krazyd on 2006-07-07
> **mannequin said:**
> You have it working with Network Manager and ndiswrapper? Does it automatically work, or do you have to do something else? I know that you have to remove everything but lo from /etc/nework/interfaces. (That's to stop that suggestion from coming up again. :) ) Any help would be appreciated! I'd rather use WPA or WPA2 then WEP, but WEP is the only option with Network Monitor.

Thanks!
-M.

Yes, it works well with Network Manager, all automagically once ndiswrapper is working properly!

And it isn't true that you should remove everything from /etc/network/interfaces. In fact, if I do that, Network manager can't see my wireless at all! This is what my /etc/network/interfaces looks like:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


```

eth1 is my wireless. Also, network manager also automatically worked with WPA for me. As soon as I clicked on the wireless network, it detected the WPA and asked for my password.

This is how I installed ndiswrapper, in case it helps: [http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218)
I used the windows drivers ASUS provided me with for the card.

---

### Post by da1nonlymikeo on 2006-07-09
yo man when i get to step 4 and do..... 

sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o   

 i get a reply of..

 cannot open input file  /home/mike/desktop/wl_apsta.o

 what did i do wrong??

---

### Post by rmonie on 2006-07-09
Nickm,

Thanks a million. It worked fine except that I now have a weird situation where the Network Manager refuses to acknowledge the existence of the wireless connect(which is working fine!) I am also getting a network signal bar which is vertical.

Any ideas & thanks again

Regards

RMonie

---

### Post by spidey867 on 2006-07-09
Hey, I just recently installed Ubuntu 6.06 on my Dell notebook. As far as I'm aware, it has a Truemobile 1400 in it (BCM4309 802.11a/b/g). I tried using this guide and didn't have too many problems until I rebooted at the end. Upon boot of the kernel, it gets stuck at "Loading hardware drivers..." and just sits there for a while. Since it was a fresh install, I just put the Live CD in and reinstalled 6.06. If anyone knows of what I did wrong, please help me out. 

Thanks.

---

### Post by bluppfisk on 2006-07-09
> **crag277 said:**
> I followed a very similar guide on the wiki to try and get my Broadcom 4318 working in my Compaq V2000Z laptop.  Only differences are I'm using Kubuntu and the bcmwl5.sys file form the compaq driver site for this computer.  I thought everything was going great.  The blue light came on after the driver install and it found my wireless network.  But when I tried to connect, using Wireless Assistant in KDE it could not connect to the network.  Now, the light is still on, iwconfig correctly identifies the device, but it no longer sees any wireless networks, even though there are two very strong ones in range.  Any ideas?

I have a Turion 64, AMD64 version of Kubuntu 6.06, and 1GB RAM.

I saw another post of problems with this wireless device when the system has >1GB of RAM.  Is there any merit to that?

I'm experiencing about the same problem. I have an Acer 5003 with AMD64 Ubuntu 6.06, 1Gb RAM of which 32 MB is taken by the graphics card, and a Turion 64 processor. I too can "see" wireless networks but I cannot connect to them, either via DHCP or static IP address.

Anyone else?

---

### Post by cc69 on 2006-07-10
Follow the steps (provided by Nickm)

1.Dealing with the installation of bcm43xx-fwcutter
[http://ubuntuforums.org/showthread.php?p=1071920#post1071920](http://ubuntuforums.org/showthread.php?p=1071920#post1071920)


2.The installation of the driver (provided by Vaan) found at;
[http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip)

1. sudo apt-get install bcm43xx-fwcutter

2. sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/bcmwl5sys.zip

3.I couldnt get Newtwork manager to work. Instead i used the default Network Monitor which i installed by:

a) right clicking on the grey panel at top left of the time and date in an empty portion.

b) click on "Add to Panel"

c) scroll down to System Hardware section and click on "Network Monitor"


4. Reboot


Good luck:D

---

### Post by bluppfisk on 2006-07-10
thanks a bunch, but no luck. Here's an error message I get when I use bcm43xx-fwcutter on bcmwl5.sys:

> *****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in the future...

fiddlesticks :) What's with the rebooting on UBuntu by the way? I was always told that you didn't have to reboot anything when on Linux, just the one service that required updating. Not on Ubuntu?

---

### Post by JoshNCSU22 on 2006-07-10
Guys I'm trying my best to get started with this but I cannot find a sources.list that will allow me to get bcm43xx-fwcutter or the network-manager-gnome. I've tried several different sources.list files and I was wondering if anyone had any suggestions for me... here is a copy of my sources.list:

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by McTek on 2006-07-11
:) Got it working! Need one more screen showing the selection the eth port. Mine came up eht0 and the modem was on eth1. 
Thanks and well done.

---

### Post by bluppfisk on 2006-07-11
Hmm apparently it does work now. It's just that my network monitor or any program does not report anything about my signal strength and the LED on my acer does next to nothing. So I was still thinking that wireless didn't work.

finally linux is becoming attractive. Now WMV support.

---

### Post by blackb1rd on 2006-07-11
Great howto, finally got it working (stable)! One question, is there some way to combine this solution with ethernet bonding in active/backup mode? That way a connection can continue to operate over wlan when unplugging the lan cable (and vica versa). Just as described at this Gentoo howto: [http://forums.gentoo.org/viewtopic-t-430748.html](http://forums.gentoo.org/viewtopic-t-430748.html). Already tried some bonding howto's from this forum, but the gnome network manager automatically reacts when unplugging the cable, instead of staying always connected to the wlan.

---

### Post by n00bWillingToLearn on 2006-07-11
> **JoshNCSU22 said:**
> Guys I'm trying my best to get started with this but I cannot find a sources.list that will allow me to get bcm43xx-fwcutter or the network-manager-gnome. I've tried several different sources.list files and I was wondering if anyone had any suggestions for me... here is a copy of my sources.list:

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

They may not be available for breezy, is there any reason you havn't upgraded to dapper?

---

### Post by bluppfisk on 2006-07-11
THAH! Now it stopped working _again_. I think I accidentally hit the Wireless button on the front side of my laptop when it was shutting down. And then I restarted and it's all gone again. Yes, it detects networks, no it can't connect. Yes the LED in the button sometimes flickers, no, eth1 won't become the active connection (doesn't stick).

time for me to get back to windows for a bit I guess. It's a shame because UBuntu really looked promising.

---

### Post by JoshNCSU22 on 2006-07-11
Apparently laziness...I suppose I should upgrade to dapper haha

---

### Post by JoshNCSU22 on 2006-07-11
Ok so I've updated to dapper and used apt-get to install both the bcm43xx-fwcutter and the network-manager-gnome. However when trying to complete step 4 I realize that I do not have any directories in the /lib/firmware directory. There are all the bcm43xx files but no directories? Any suggestions?? I can't really use 'sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-23-386 ~/Desktop/wl_apsta.o' because that directory doesn't exist....I tried creating one but I dunno if I used the right numbers...

---

### Post by book on 2006-07-12
Thanks to Nickm's  advice in this Howto, I finally got to see the power light on the Buffalo WLI-CB-G54S card. Presumably, the card now works as it is supposed to on my Thinkpad T23 with Ubuntu 6.06. 

At first, when the card started to function, the bars indicating signal strenth showed up on the gnome desktop panel, but only then, whereafter the netmanager seems to have lost the wlans, showing now only the wired network (not in use). Wonder why.

Anyway, thank you very much.

  - Mikael

---

### Post by mannequin on 2006-07-12
> **krazyd said:**
> Yes, it works well with Network Manager, all automagically once ndiswrapper is working properly!

And it isn't true that you should remove everything from /etc/network/interfaces. In fact, if I do that, Network manager can't see my wireless at all! This is what my /etc/network/interfaces looks like:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


``` 
eth1 is my wireless. Also, network manager also automatically worked with WPA for me. As soon as I clicked on the wireless network, it detected the WPA and asked for my password.

This is how I installed ndiswrapper, in case it helps: [http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218)
I used the windows drivers ASUS provided me with for the card.
Huh. I've tried it, and it doesn't work. :( I guess next time I pop around to my brother's house I'll try it again.

Thanks for sharing!
-M.

---

### Post by n00bWillingToLearn on 2006-07-12
> **JoshNCSU22 said:**
> Ok so I've updated to dapper and used apt-get to install both the bcm43xx-fwcutter and the network-manager-gnome. However when trying to complete step 4 I realize that I do not have any directories in the /lib/firmware directory. There are all the bcm43xx files but no directories? Any suggestions?? I can't really use 'sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-23-386 ~/Desktop/wl_apsta.o' because that directory doesn't exist....I tried creating one but I dunno if I used the right numbers...

I don't know why you don't have a diectory there, but the numbers are your current kernel version. The guide seems to suggest that that step may not be neccesary, did you try it to see if it works without that step?

---

### Post by JoshNCSU22 on 2006-07-12
Yeah I knew the numbers where my kernel version...but I don't know how exactly to get the most up to date version. Also, it says I have network-manager-gnome installed but I'm not sure how to start it...it didn't start automatically after I rebooted...

---

### Post by devillion on 2006-07-12
Wow! Thanks. This worked first try for me, with an:

HP Pavilion DV5140 Notebook/AMD Turion64/Broadcom 4318

Thanks a ton. Ubuntu rocks. I can't believe how easy this is (compared to debian i tried a few years ago).

---

### Post by sigmason on 2006-07-13
This is bad form, but I'll ask my question again.

Does any have their Broadcom chipset based card working in a manner in which it can be removed from the PCMCIA slot and does anyone have it working so that it reconnectes automatically after hibernation?

sigmason

---

### Post by n00bWillingToLearn on 2006-07-13
> **JoshNCSU22 said:**
> Yeah I knew the numbers where my kernel version...but I don't know how exactly to get the most up to date version. Also, it says I have network-manager-gnome installed but I'm not sure how to start it...it didn't start automatically after I rebooted...
To find out what kernel version you have ```
uname -r
```
I don't know about network manager, it didn't work for me so I use wifi-radar. Have you tried entering the ESSID manually and connecting with System-> Admin-> Networking to test if your connection works at all?

---

### Post by mikeeve on 2006-07-14
After 2 previous unsuccessful attempts, finally achieved success with this approach on an HP zx5000. Somewhat confusing since nm-applet doesn't show the bars for the wireless. I do have icons on the top line(panel?) for the wired and loopback interfaces. I didn't even realize the wireless was working until I unplugged the wired cable. 

The previous 2 attempts, I tried to use the window's driver that came with the laptop. Seemed logical. This time I downloaded the wl_apsta.o driver.

---

### Post by betterliving on 2006-07-15
Even this didn't work for me, sadly, though I'm dealing with a particularly odd situation... thanks anyway, though, great howto.

---

### Post by muzungu on 2006-07-15
Using a Lenovo 1000 C100 with Ubuntu Dapper and latest Linux kernel. Not only did this NOT work for me, but once I was done I couldn't log back into my graphical user desktop.

Good thing the majority of OSS also works on Windows :-(

---

### Post by n00bWillingToLearn on 2006-07-16
> **muzungu said:**
> Using a Lenovo 1000 C100 with Ubuntu Dapper and latest Linux kernel. Not only did this NOT work for me, but once I was done I couldn't log back into my graphical user desktop.

Good thing the majority of OSS also works on Windows :-(

That is verry strange and I am not quite sure how something like that could happen:confused: Anyways, what in particular is the problem with logging in? X fails to load completely, password no longer works... This thread does not get much attention so I suggest posting a new thread detailing your problem.

---

### Post by CrazyDoode on 2006-07-16
> **nickm said:**
> *updated to use a better driver*

It seems that if you get the following string back: **Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)** that this guide is VERY unlikly to work for you although it does sometimes, dont ask me why, but basically every "no" vote and "this didnt work for me" post comes from a BCM4318 user....


[SIZE="3"]I have this card on my dell inspiron 1300 and fwcutter refused to acknowledge the dell driver which worked fine under ndiswrapper. I then ran this command:
**sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh**

which installs all the latest drivers and prevents you from pulling your hair out.  aka: it worked! [/SIZE]

I used this howto:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

### Post by S.nazari on 2006-07-16
I used both the recommended file wl_ap... and the bcmwl5.sys from the link on this how to and from my cd rom for my hardware. 
I still get no luck. Here are the details of my adventure in the bcm.txt file.

---

### Post by S.nazari on 2006-07-16
> **CrazyDoode said:**
> [SIZE="3"]I have this card on my dell inspiron 1300 and fwcutter refused to acknowledge the dell driver which worked fine under ndiswrapper. I then ran this command:
**sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh**

which installs all the latest drivers and prevents you from pulling your hair out.  aka: it worked! [/SIZE]

I used this howto:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

If you did not have any internet connection how did you mange to run that command. That command without any internet connection give s no results what so ever since it has to download some files from a website and then install them. Your post is no good to people who have no internet connection on their problem computer. i.e the one with the bcm car in it.

---

### Post by stuh505 on 2006-07-17
I have followed these instructions extremely carefully twice in a row now on a brand new ubuntu install.  Both times it has damaged the system beyond repair such that it can only be booted into repair mode and all root commands fail to get rid of bcm43xx.  Be forewarned...

edit -- using hp pavilion zx5078cl, bcm4306 (rev 3), dapper drake

---

### Post by mikeeve on 2006-07-17
stuh505: Did you use the wl_apsta driver? My zx5000 worked with that driver, but not the bcm driver installed under Windows by HP. I also have built-in wireless with bcm4306, rev 3.

---

### Post by squidward_tentacles on 2006-07-19
Im using a BCM4304802-11B, 7 hours(!) of following other threads/How-to's/Docs/wikis to no avail before I found this one golden thread! Works like a charm, (after a reboot and power-cycle of the modem and router) YOUR MY HERO! 
.....now im going to try enabling WEP and see if it still works (shudders)
Anyway, Sterling How-To, Cheers!

---

### Post by Twinxor on 2006-07-19
Very helpful little walkthrough! Could you explain the differences between using the native drivers and ndiswrapper?

Update: Works great so far! Oddly, that wl_apsta.o file failed the fwcutter checksum, but the zip file you provided worked ok. (Maybe I can figure out how to extract the file the card manufacturer provides...) Also, the system log contains a bunch of these messages:

```
[17179593.092000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
```

...but as long as they have no effect, it doesn't matter.

---

### Post by PP3RKut on 2006-07-19
Thank you so so much... for some weird reason this worked for my Microsoft MN-720 Notebook adapter... which is wireless g... Anyone else who has this card... give it a try!  Thank you!!

---

### Post by Twinxor on 2006-07-19
> **PP3RKut said:**
> Thank you so so much... for some weird reason this worked for my Microsoft MN-720 Notebook adapter... which is wireless g... Anyone else who has this card... give it a try!  Thank you!!

Nothing weird about that -- Microsoft doesn't manufacture the chipset powering the wireless adapter, Broadcom does. That's why this works for Apple equipment, too.

---

### Post by PP3RKut on 2006-07-19
> **Twinxor said:**
> Nothing weird about that -- Microsoft doesn't manufacture the chipset powering the wireless adapter, Broadcom does. That's why this works for Apple equipment, too.

Yeah I saw that on the device specs.  But it is running in Wireless B mode, and it is made to run as a Wireless G card.  How does that work out?  I assume it is the same chipset that they stick in the B cards?

---

### Post by GabFromDenver on 2006-07-20
Youhou! I happen to write to you thru my brand new wireless connection. Your tutorial helped me... well sort of. I have the very difficult BCM4318 network card that so many have problems with. I struggled for a long time, going thru ndiswrapper, wpa_supplicant, ... and a lot of reading. Well, I now know more about the whole wireless thing. Anyway, here is what I did to make it work:

Pre-requisites:
 - Ubuntu Drapper
 - Lynksys Wireless G - WPC54G v3

There are 6 easy steps: 

1 - Download ubuntu script bcm43xx-fwcutter:
```
sudo apt-get install bcm43xx-fwcutter
```

2 - Now install it (this I did differently from your tutorial, but I find it more simple): 
```
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```

3 - Install indeed the greatest network manager ever:
```
sudo apt-get install network-manager-gnome
```

4 - Make sure your access point is using WPA TKIP (honestly, don't use WEP - that's an advice from a software engineer specialized in security) and choose a strong pre-shared key - you won't even have to remember it.

5 - Now the most important step that make it all work (please don't laught): go to sleep. Yep! ](*,) I hate to say it, but once I went thru your tutorial and realized it didn't work no matter how I tweaked the various settings, I remembered something I read on the net two weeks ago when I was desperately looking any info. So go head, there's nothing to do.

6 - In the morning, all fresh from a restful night, turn on your favorite OS and there you go! Have a good day my friends! :D 

	Gabriel

---

### Post by trevis on 2006-07-20
Worked perfectly on the first try.  Thanks.

---

### Post by Toady11 on 2006-07-20
Thanks! Worked great with my Inexq CR054g-009 based on the Broadcom 4306 Chipset.

---

### Post by drdeath666 on 2006-07-24
OK im not going to pretend to know what im doing... but I did this first time thru and it didnt work. (Network Manager wouldnt let me select or show up wireless at all, though it did say it was connected when I went to network connecetions)

Anyway this laptop is dual booting windows so I pulled the file out of the windows partition and placed it on the desktop.

I Tried:
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-25-386 ~/Desktop/BCMWL5.SYS

But i got a Cannot open input file error.

What am i doing wrong :confused:

---

### Post by n00bWillingToLearn on 2006-07-25
> **drdeath666 said:**
> OK im not going to pretend to know what im doing... but I did this first time thru and it didnt work. (Network Manager wouldnt let me select or show up wireless at all, though it did say it was connected when I went to network connecetions)

Anyway this laptop is dual booting windows so I pulled the file out of the windows partition and placed it on the desktop.

I Tried:
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-25-386 ~/Desktop/BCMWL5.SYS

But i got a Cannot open input file error.

What am i doing wrong :confused:

There are a few things that could be going wrong but first check to make sure the drivers are working before you mess with network-manager.To see if your card is working correctly go to a computer with working wireless ( or boot into windows ) and write down the SSID ( network name ) of the wireless connection you want to connect to. Then ( in Ubuntu ) go to System -> administration -> networking. Now select your wireless connection and go to properties. Enter the SSID and password ( if it's an open network just leave that blank ) and hit OK. If that works then you need to comment out the interfaces in /etc/network/interfaces```
sudo gedit /etc/network/interfaces
``` Then comment out ( put a # at the beggining of ) all but the first two lines ( having to do with lo )

---

### Post by mikeeve on 2006-07-25
> **drdeath666 said:**
> 

Anyway this laptop is dual booting windows so I pulled the file out of the windows partition and placed it on the desktop.



I also tried the using the driver installed with Windows. It had a missing piece, and didn't work properly. So I downloaded the driver file the author suggests, and that worked fine.

---

### Post by lupine_nickt on 2006-07-26
Don't know if this has been mentioned, but the link to the .o file no longer works! I've found another copy here:

[http://www.fedoraforum.org/forum/attachment.php?attachmentid=7759](http://www.fedoraforum.org/forum/attachment.php?attachmentid=7759)

maybe someone can update the first post?

xF,

...Nick

---

### Post by n00bWillingToLearn on 2006-07-28
> **lupine_nickt said:**
> Don't know if this has been mentioned, but the link to the .o file no longer works! I've found another copy here:

[http://www.fedoraforum.org/forum/attachment.php?attachmentid=7759](http://www.fedoraforum.org/forum/attachment.php?attachmentid=7759)

maybe someone can update the first post?

xF,

...Nick

I also made a zip file with the already extracted firmware files ( just copy them to /lib/firmware ) and put it on my web page I will keep the link up and it is more convienient to not have to deal with fwcutter. [http://trogdoor.googlepages.com/firmware.zip](http://trogdoor.googlepages.com/firmware.zip)

---

### Post by big_gie on 2006-07-28
I must say that I tryed many firmwares for my 4306 card, many of them didn't worked.

I think it would be better if their was a kind of database on firmwares and their location, maybe on the wiki? Their are so many of them, so many different versions.

For me, the bcm43xx was to unstable to use. I'm back to ndiswrapper.

---

### Post by axle on 2006-07-29
Hi, I got my wifi up and running no problem..... thanks for the guide!

Peace,
   Stu

---

### Post by nickm on 2006-07-29
> **lupine_nickt said:**
> Don't know if this has been mentioned, but the link to the .o file no longer works! I've found another copy here:

[http://www.fedoraforum.org/forum/attachment.php?attachmentid=7759](http://www.fedoraforum.org/forum/attachment.php?attachmentid=7759)

maybe someone can update the first post?

xF,

...Nick

Sorry :) its updated now, this new forum layout still confuses me.
I'l host it myself.

---

### Post by wjbaird on 2006-07-29
Wow!   Thanks.   Ndiswrapper has been a serious PITA to me for the last few months!   This looks like it'll work so much better.

---

### Post by Chii on 2006-07-30
Wow.... thank you very much for this guide!  I recently reinstalled Ubuntu to take another crack at it after giving up due to ~2-3 weeks of frustration with WPA Supplicant and Ndiswrapper, and now I am happily using my wireless card on my laptop :)  

Now I can start trying to learn other stuff on this finally! 

Thank you again :)
Chii

---

### Post by Grudgebearer on 2006-08-02
Ok, have gone through th steps listed, and my Belkin (Broadcom 4316) wireless card at least shows up now and the lights come on, but I still can't seem to pull a DHCP address, nor does the wireless icon show up on the top panel

When I run *iwconfig*, with my router set to broadcast the ESSID, WEP with a Hex key this is what I get...
```

eth1      IEEE 802.11b/g  ESSID:"SabbatMartyr"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point:00:14:BF:39:26:D5
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=184/100
          Rx invalid nwid:0  Rx invalid crypt:22  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Now, I have tried using a static IP address, and I have tried turning off WEP so that the access point is open and this is what *iwconfig* shows in both cases...
```

eth1      IEEE 802.11b/g  ESSID:"SabbatMartyr"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I am not sure where to go with troubleshooting this issue at this point.  Any insight will be much appreciated.

Thanks,

Grudge

---

### Post by Bingdinger on 2006-08-03
Worked perfectly for me, Thanks Nick.

---

### Post by evilXhwnd on 2006-08-03
worked for me too. I have a 

```

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

---

### Post by Glarbl_Blarbl on 2006-08-03
Running a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02) on a dell inspiron 5100..  Got the wireless connected, but there's some weirdness with the bit rate.  It silently accepts a "sudo iwconfig eth1 rate 54M", and a subsequent iwconfig shows 54 Mb/s - but the nm-applet still shows 11 Mb/s...

Which one should I believe?  My throughput to the ubuntu repositories is about 50Kb/s slower than it normally is on the wired connection, but since my DSL only goes at about 800K I thought that it should be the same regardless of my LAN speed...  Am I making an incorrect assumption?

EDIT:
Where would I configure the nm-applet to force a particular WLAN to run in 802.11g?  Unfortunately, the applet doesn't seem to be very well documented :( ..

---

### Post by Darth Lukan on 2006-08-03
Dude! You are the man!I'm new to Kubuntu but have been using Gentoo for a while now but decided to try a new distro for my new lapbox with wireless. Your howto had me running in about five minutes! Thank you very much! I'm sure there are a lot of people out there that use winhole that will be converting to linux, specifically ubuntu very soon.

---

### Post by nickm on 2006-08-04
> **Glarbl_Blarbl said:**
> Running a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02) on a dell inspiron 5100..  Got the wireless connected, but there's some weirdness with the bit rate.  It silently accepts a "sudo iwconfig eth1 rate 54M", and a subsequent iwconfig shows 54 Mb/s - but the nm-applet still shows 11 Mb/s...

Which one should I believe?  My throughput to the ubuntu repositories is about 50Kb/s slower than it normally is on the wired connection, but since my DSL only goes at about 800K I thought that it should be the same regardless of my LAN speed...  Am I making an incorrect assumption?

EDIT:
Where would I configure the nm-applet to force a particular WLAN to run in 802.11g?  Unfortunately, the applet doesn't seem to be very well documented :( ..

you should believe the 11mbps as i dont think your wireless now looks to iwconfig for its settings. and yes, an 802.11b connection should be sufficiant, its capable of about 4mb/s sustained transfer so aslong as your internet speed is less than 4mb you shouldn't see a slowdown.

Hope that helps :)

---

### Post by Rickshaw Driver on 2006-08-04
Ok, I have one of the AirForce one cards and it is working after this so thank you.  I do have one question though.  I downloaded the NetworkManager Applet 0.6.2 as per your instructions, but it only shows information when I am wired.  I have no choice to display the wireless information.  Can anyone give me some direction on this please?

---

### Post by vbr00t on 2006-08-05
Ok got to tell you love the tut it works Great with a little modding here and there i have the bcm4318 and i thought it wouldent work but hey i managed to get it to work with the help of your tut thank you very much.:D

---

### Post by vbr00t on 2006-08-05
Ok got to tell you love the tut it works Great with a little modding here and there i have the bcm4318 and i thought it wouldent work but hey i managed to get it to work with the help of your tut thank you very much.:D

---

### Post by Buelldozer on 2006-08-07
I have an HP Pavilion ze2000 and the original instructions (first post) worked fine...with a couple of changes.

First, I am a KDE guy so I didn't install the gnome applet, I used the KDE one (KNetwork manager) which worked fine under KDE 3.5.4 on Dapper. You have to manually install this, it doesn't come by default.

Second, I used fwcutter to extract the firmware (bcm43xx_microcode5.fw) from my *actual* Windows driver.

Third, you need to go into /etc/network/interfaces and comment out everything but the loopback (lo) adaptor. If you leave any other lines in there it will throw knetworkmanager into a tizzy and you will not be able to connect to any wireless networks. This holds true for the gm-applet as well.

Fourth, installed wpa_supplicant and rebooted.

Done! My BroadCom AirForce One Rev 02 card is now running on my Pavilion with the 686 (32 bit) kernel. I can connect to both WPA protected networks here at the office. 8)

---

### Post by yaromaster on 2006-08-07
Hi my name is Pawel and I did every thing in the tutorial. My wirless broadcom card b/g is working, I see the light. I have the good signal streanght but i cannot connect to the internet(my router is only G). Please help me. I am new to the linux.

---

### Post by Bruhthakuga on 2006-08-07
My Dear Ubuntu Friend,
	I am having trouble understanding some details of your instructions, I do understand them up to 4B.  There you said, “[COLOR="Blue"]4B ) Extract your Cards firmware from the driver
			Just to be safe we'l put the driver in the kernel folder too”[/COLOR].
Then you gave to code to enter to get that done, 

	[COLOR="Blue"]sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-25-386 **[SIZE="4"]~[/SIZE]**/Desktop/wl_apsta.o[/COLOR]

Then you said, “[COLOR="Blue"]Replace the 2.6.15-23-386 part with the most up to date folder in there, you may have to repeat this step each time the kernel is updated or you may not, your results may vary.[/COLOR]

There are only two folder in there and they are:
2.6.15-26-amd64-generic
2.6.15-23-amd64-generic,
What do I do about the symble, “ [COLOR="Blue"][SIZE="3"]**~ **[/SIZE][/COLOR]”, ?  Is that part of the command or part of file name?  

When you say, “[COLOR="Blue"]Note  The location and name of the .o file for this command may differ in your case, if you really get stuck type bcm43xx-fwcutter and then hit space, find your file using the GUI and then drag and drop it into the terminal.[/COLOR]” I don't know what you mean, what is an [COLOR="Blue"].o [/COLOR]file?  There are no file with .o as a suffix in the firmware folder.

I made a copy of the terminal showing everything I did after I finished, maybe you can see what I did wrong:[COLOR="DarkSlateGray"]

nine@nine-laptop:~$ sudo apt-get install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nine@nine-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
fwcutter can cut the firmware out of /home/nine/Desktop/wl_apsta.o
  filename :  wl_apsta.o
  version  :  3.130.20.0
  MD5      :  e08665c5c5b66beb9c3b2dd54aa80cb3

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
extracting bcm43xx_microcode11.fw ...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...
nine@nine-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-26-amd64-generic/Desktop/wl_apsta.o fwcutter 20060108

Usage: bcm43xx-fwcutter [OPTION] [driver.sys]
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -p|--postfix ".FOO"   Postfix for firmware filenames (.FOO.fw)
  -v|--version          Print fwcutter version
  -h|--help             Print this help

Example: bcm43xx-fwcutter bcmwl5.sys
         to extract the firmware blobs from bcmwl5.sys
nine@nine-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-26~/Desktop/wl_apsta.o
fwcutter 20060108

Usage: bcm43xx-fwcutter [OPTION] [driver.sys]
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -p|--postfix ".FOO"   Postfix for firmware filenames (.FOO.fw)
  -v|--version          Print fwcutter version
  -h|--help             Print this help

Example: bcm43xx-fwcutter bcmwl5.sys
         to extract the firmware blobs from bcmwl5.sys
nine@nine-laptop:~$
[/COLOR]

---

### Post by n00bWillingToLearn on 2006-08-07
> **Bruhthakuga said:**
> [COLOR=DarkSlateGray]
nine@nine-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-26-amd64-generic/Desktop/wl_apsta.o fwcutter 20060108

Usage: bcm43xx-fwcutter [OPTION] [driver.sys]
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -p|--postfix ".FOO"   Postfix for firmware filenames (.FOO.fw)
  -v|--version          Print fwcutter version
  -h|--help             Print this help

Example: bcm43xx-fwcutter bcmwl5.sys
         to extract the firmware blobs from bcmwl5.sys
nine@nine-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-26~/Desktop/wl_apsta.o
fwcutter 20060108

Usage: bcm43xx-fwcutter [OPTION] [driver.sys]
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -p|--postfix ".FOO"   Postfix for firmware filenames (.FOO.fw)
  -v|--version          Print fwcutter version
  -h|--help             Print this help

Example: bcm43xx-fwcutter bcmwl5.sys
         to extract the firmware blobs from bcmwl5.sys
nine@nine-laptop:~$
[/COLOR]

That last command shoud be ```
[COLOR=DarkSlateGray]sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-26 ~/Desktop/wl_apsta.o[/COLOR]
```[COLOR=DarkSlateGray]
It looks like you just forgot the space in between the two directories in the command and BTW ~ is short for your home directory so ~/Desktop[/COLOR] is the same as /home/yourUserName/Desktop :)

---

### Post by Bruhthakuga on 2006-08-07
n00bWillingToLearn,
     This is the results of entering the code you sugested, Is this good?  The part that say, "[COLOR="Blue"]No such file or directory[/COLOR]" is of concern to me.[COLOR="Blue"]

nine@nine-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-26 ~/Desktop/wl_apsta.o
Password:
fwcutter can cut the firmware out of /home/nine/Desktop/wl_apsta.o
  filename :  wl_apsta.o
  version  :  3.130.20.0
  MD5      :  e08665c5c5b66beb9c3b2dd54aa80cb3

extracting bcm43xx_microcode2.fw ...
/lib/firmware/2.6.15-26/bcm43xx_microcode2.fw: **No such file or directory**
nine@nine-laptop:~$
[/COLOR]

---

### Post by Bruhthakuga on 2006-08-07
In instruction 4B: ) [B]Extract your Cards firmware from the driver
Just to be safe we'l put the driver in the kernel folder too[/B]

and the code givin was: **sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-25-386 ~/Desktop/wl_apsta.o**

And in instruction  4 ) Extract your Cards firmware from the driver
Open a terminal (dont worry) and type the following:

and the code givin was: sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o

     Couldn't I just copy the file, "**bcm43xx_microcode2.fw**" from /lib/firmware folder and paste it in the /lib/firmware/2.6.15-26-amd64-generic folder?  Also if it found it once to put it into the firmware folder why wasn't it available for the 2.6.15.-26-amd64-generic folder?

OK!  OK!  I admit, I may have did something.  .  .  well stupid, I proceeded on to the instruction:  5 ) [B]Install Network Manager
I find that this is the best way to manage wireless connections[/B]
Code:

sudo apt-get install network-manager-gnome

and after that it locked up and nothing responded so I turned it off.  There I said it.  Is my notebook going to explode?  Should I take cover?

---

### Post by n00bWillingToLearn on 2006-08-07
[COLOR=Black]> **Bruhthakuga said:**
> n00bWillingToLearn,
     This is the results of entering the code you sugested, Is this good?  The part that say, "[/COLOR]> **Bruhthakuga said:**
> [COLOR=Black]No such file or directory" is of concern to me.[/COLOR][COLOR=Black]

nine@nine-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-26 ~/Desktop/wl_apsta.o
Password:
fwcutter can cut the firmware out of /home/nine/Desktop/wl_apsta.o
  filename :  wl_apsta.o
  version  :  3.130.20.0
  MD5      :  e08665c5c5b66beb9c3b2dd54aa80cb3

extracting bcm43xx_microcode2.fw ...
/lib/firmware/2.6.15-26/bcm43xx_microcode2.fw: **No such file or directory**
nine@nine-laptop:~$
[/COLOR][COLOR=Black]
My fault there, it should be [/COLOR]```
[COLOR=Black]sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-26-amd64-generic[/COLOR][COLOR=Black] ~/Desktop/wl_apsta.o[/COLOR]
```[COLOR=Black] or [/COLOR][COLOR=Black]```
[/COLOR][COLOR=Black]sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r`[/COLOR][COLOR=Black] ~/Desktop/wl_apsta.o[/COLOR][COLOR=Black]
``` Although I don't have my Ubuntu machine right now so I am not sure, that is just from memory.
[/COLOR]

---

### Post by mxa055 on 2006-08-08
Hi there,

I followed the guide exactly and everything works although I have a ```
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
(had to blacklist ndiswrapper)

The only problem is that I don't get an icon of network-manager-gnome :shock:  Any ideas why this is happening? 
Also my wireless connection is called eth1 instead of wlan0 but that is really ok with me.

Thanks for the great guide.

---

### Post by Bruhthakuga on 2006-08-08
Ubuntu Friends,
     I have been help very much by user on this thread,However, I am in need of help with the last hurdle.  I have a Compaq Presario V2570NR notebook which have a Tourion64 ML34, 1Gig of cheep Ram and the Broadcom BCM4318 ver.2 wireless network card and this is where I am at, I have successfully, so it may seem, completed all instruction up to (5), and with a squeeky clean install.  On previous attemtps I had lock-up at this code:

[COLOR="Blue"]I sudo apt-get install network-manager-gnome[/COLOR]

It wouldn't boot up successfully after it.

In a book called Linux Desktop by Davod Brickner it was sugested that I use KDE's Kwifimanager and so that is what I did.  Prehaps it should be known that at this time and to update and to download files I am and was using a Netgear WG511T card Which the KwifiManager does seem to work with.  When I enter ipconfig I get the following output:[COLOR="Blue"]

nine@nine-laptop:~$ ipconfig
bash: ipconfig: command not found
nine@nine-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"John 17:3 Taking in, not Took in"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4B:7E:7A:5B
          Bit Rate:24 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/94  Signal level=-54 dBm  Noise level=-95 dBm
          Rx invalid nwid:12  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:2   Missed beacon:0

nine@nine-laptop:~$

[/COLOR]

I actually do have a copy of everyting I done in the terminal as I save it to look back and to show other who may help me so they can see what I have done.  What should I do now?

---

### Post by gwilki5691 on 2006-08-08
Thanks for the easy to follow instructions but it seems i'm another unfortunate with a BCM4318 controller as it didn't work for me either. I was hopeful when I managed to enable the wireless hardware and scan for networks. However my wifi manager thinks there is no signal.

I have had a partial success following this post, for which I am grateful. I will check out the other posts you mention though.

Thanks again:p ,

G.

---

### Post by davers007 on 2006-08-08
My wireless card is the troublesome Linksys WPC54G and I'm using a Linksys WRT54G router on a 4 year old Toshiba Satellite 5105-S501 laptop. Here is my wireless card:

[COLOR="DarkGreen"]0000:03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]

Right out of the box, Ubuntu recognized that I had a wireless card. I followed the instructions on [http://www.ubuntuforums.org/showthread.php?t=5645](http://www.ubuntuforums.org/showthread.php?t=5645) to install the ndiswrapper. Afterwards, nothing changed.

I then followed the instructions on [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174) to update the firmware and installed network-manager-gnome. This allowed me to actually see my access point. I can see the access point now and the wireless interface is active and I can get the scan to work. However, it still won't connect to the network, even if it's unsecured. My iwconfig eth1 reads the following:

[COLOR="DarkGreen"]eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/COLOR]

My /etc/modules file reads the following:

[COLOR="DarkGreen"]lp
psmouse
sbp2
sr_mod
ndiswrapper[/COLOR]

My /etc/network/interfaces file reads the following:

[COLOR="DarkGreen"]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto ppp0
iface ppp0 inet dhcp[/COLOR]

I'm new to Linux but am frustrated that after a couple weeks I still can't get this working. Can someone point me in the right direction?

---

### Post by mangloid on 2006-08-09
I got my BCM4318 card working using the instructions in this thread.
[http://www.ubuntuforums.org/showthread.php?t=145730](http://www.ubuntuforums.org/showthread.php?t=145730)

Although the differences are; mine didnt rename to wlan0, it stayed eth0, and I manually confingured ( setting ap, channel, key, ect ) but its working!.

---

### Post by WalmartSniperLX on 2006-08-10
For some reason that lil note about the .o file is hitting me hard cuz i think im having a problem finding the right file or something rather. :confused:

---

### Post by Buelldozer on 2006-08-10
Davers007,

Go into your /etc/network/interfaces file and comment out everything after "auto lo
iface lo inet loopback"

The gnome network manager will NOT work correctly unless you do this! I'm not "good" enough to know if that is your only problem, but it sure is one of your problems at least.

Anyway, when you're done your file should look like this:

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto ppp0
#iface ppp0 inet dhcp

---

### Post by bigspottycat on 2006-08-10
Finally got my Belkin F5D7011 wireless card working once I found this thread. Never used Linux before, let alone Ubuntu, so it's good to see there is so much support for rookies like me.

I did find that this HOWTO only worked after a clean install but following the directions exactly did the job.

Many thanks.:p

---

### Post by csann on 2006-08-10
I have found out exactly how to get Wifi working if it has one of those miseable Broadcom chips in it.  R E P L A C E   I T!

That's right.  Replace the sucker.  I just received 2 brand new Intel 8200GB miniPCI cards.  I installed on my my wifes Dell Inspiron 8200.  She runs Windows.  Booted it up with the new card, installed a driver.  And it worked.  

Did the same with my Dell Inspiron 8600 under Windows.  Worked prefectly.  Both laptops reported a considerably better signal strength with the new cards.  

Then took out the Winders drive and put the Ubuntu hard drive in the Inspiron 8600.  Booted.  Turned on the Wifi.  And it worked.  Didn't even have to install anything.  Very cool.  Adios Windows.

The only problem is that I don't have any way to see the signal strength.  Something seems to be screwed up there but it is probably related to all the screwing around I had to do to try to get the evil Broadcom working.  

Anyone want to buy a Broadcom card?  Cheap.

Clark

---

### Post by WalmartSniperLX on 2006-08-10
OK GOT IT EXTRACTED BUT i did the wrong driver :( How do i remove the files in the firmware dir that i made. I wanna remove these so i can put the correct driver in. Please help :confused: !!

---

### Post by WalmartSniperLX on 2006-08-10
wow i tried both drivers and nothing worked

---

### Post by n00bWillingToLearn on 2006-08-11
> **WalmartSniperLX said:**
> OK GOT IT EXTRACTED BUT i did the wrong driver :( How do i remove the files in the firmware dir that i made. I wanna remove these so i can put the correct driver in. Please help :confused: !!
I don't have my linux machine at hand ( in for repair, using my parents machine ) so if someone could check these comands it would be great.

What you need to do is```
sudo rm /lib/firmware/*.fw
sudo rm /lib/firmware/`uname -r`/*.fw
```

---

### Post by {NmE} on 2006-08-11
Ok, your guide was ver good. It has gotten me to the point where I can at least activate my wireless card. 

~~~~~~~~~~~~~BUT~~~~~~~~~~~~~

It still will not work. :(  

When I go to the connections all I can select is eth0 (wired) and the loop back :( 

I've tried to set my wireless card as the Default gateway device in my network settings, but every time I select it all it does is freeze up for a few seconds and close, without saving the changes.. Anyone got any ideas?

---

### Post by madmanwashere on 2006-08-11
This worked for me running Dapper 6.06 and I do have: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). But it took a little luck. I have an HP laptop with a handy wireless button above the keyboard.  After following this howto, even using the wl_apsta.o driver, it didn't work. I gave up after awhile and booted xp( reqd for school :-# ) and noticed the wireless was disabled. Now, in linux the blue light showing wireless was on all the time so I didn't hit the button or mess with it, but in windows I enabled it by hitting the button and the next time I booted into linux it worked! :D  So, in linux, while it's working I hit the wireless button and it still enables/disables the wireless, but the blue light stays on, and there is no indication enabled/disabled. The only way to tell is if it works or not... So if you follow this howto and get the blue light, and it still doesn't work try hitting a hardware enable/disable button. Now off to see if I can get wpa working :p 

Thanks again for this GREAT howto!

---

### Post by bsmith1051 on 2006-08-11
this worked on my Compaq Presario 2100 (model no 2915US) with the Broadcom 4306 wi-fi.  I had to use the .sys file from the Windows driver on HP.com.

Question:  Why isn't this post a sticky in the Wireless Support forum?

Some suggestions for further improvement:
1. If your wi-fi is shown in System > Administration > Networks but says "inactive", is that a sure sign that you don't have the right driver?  Currently, the instructions don't specify anything about this, I don't think.

2. when you talk about extracting the firmware a second time (to the kernel sub-dir) you make mention of checking for the latest dir name, but I had to read the instructions a second time before I 'got' it.  I would suggest making it a separate step, i.e., open Places, browse to /lib/firmware, and identify the appropriate dir.

Thanks again!  I could *NOT* have done it without you.

---

### Post by Melcar on 2006-08-12
Excellent guide.  I have a BCM4318 (the chips that are not suppose to work with this guide).  At first it took me a while and was about to give up, until I decided to follow the guide from the beggining STEP BY STEP.  I'm posting using my laptop now:) .  The thing that really screwed me over each time was that I always skipped part 4B (the saving to the kernel part) because I thought it was not necessary due to the wording of the guide (it does say "just to be safe";) ).  Maybe I was just lucky, but it did worked for me.

Edit: By the way, I have a Compaq V2000Z laptop with a Broadcom wireless chip.

---

### Post by kograt on 2006-08-12
bcm43xx module kills the Acer 5024 WLMI when X server starts. Looks like linux dies inside bcm43xx xmit interup handler. I do not test anythink an have no lot of debuinfo but be crefull when going this guide with that hardware. Linux will hung on the next boot after graphical login prompt displays. It is possible to load it in failsafe mode and rmmod bcm43xx. After that all looks fine but the wireless. 

Linux acer 2.6.15-26-amd64-k8 #1 SMP PREEMPT Thu Aug 3 03:11:38 UTC 2006 x86_64 GNU/Linux

---

### Post by Melcar on 2006-08-13
I guess I spoke to soon.  Today I suffered the first signal drops (it would find networks but not connect).  Now it just refuses to work.  I will try going thru the setup process again.

Edit:  It seems to work most of the time but at times it just refuses to work.  Anybody find a 100% way to get Broadcom chips to work?  I love Ubuntu, but it's kinda hard to have a laptop without wireless support:( .

---

### Post by Melcar on 2006-08-13
I tried it againg today.  This time I used the bcmwl5.sys driver instead of the wl_apsta.o one.  Followed the same process as outlined in the begginig of this thread.  So far it has proven more stable (no signal drops or refusing to work).

---

### Post by ffadmraven on 2006-08-13
> **rjstevens3 said:**
> $iwconfig
lo...

eth1     IEEE 802.11b/g ESSID:off/any Nickname: "Broadcom 4318"
           Mode: Managed Frequency=2.437 GHz Access Point: Invalid
           Bit Rate=11 Mb/s  Tx-Power=18dBm
           RTS thr:off  Fragment thr:off
           Link Quality:0 Signal level:0 Noise level:0
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
           Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth0.....



rjstevens3:  the problem is where it says access point: invalid.

The quick fix for this would be to type in a terminal the folowing:

  sudo iwconfig eth1 ap any

This should then alllow the card to pick up the available access points.  I would suggest adding that line to your /etc/network/interfaces file as well that way you don't have to retype it every time you restart your networking.

Edit:
Of course if I had read the entire line of replies I might have notice the answer was already given.  Sometimes I get ahead of myself, oh well.

---

### Post by enjahova on 2006-08-13
I have a broadcom 4310

I followed these instructions and I can see all the AP around me in Network Manager just fine. It says I am connected at full strength The only problem is that I still cannot get internet access. My ip address in network tools shows a very strange IP.

What am I missing?

---

### Post by UNHOLYwoo on 2006-08-14
nickm, I think I love you. Thanks for the HOWTO, worked flawlessly.

---

### Post by toosweetnitemare on 2006-08-14
i thought i was a great post to get the cards working, yet mine still does not

0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


this is what i am working with. do you have anyideas on why it didnt work? or how to get it going? if you need any information just ask



edit: just ignor this, a few reboots fixed everything. thanks again for the great how-to

---

### Post by gholen on 2006-08-14
Thanks man, you saved my day, and my mothers!
This HOWTO was plain and simple one of the best I've read, and I've read a lot :)

Your work with this one is quite good and I love it.
Now I can save those 400 SEK that I've saved, and by something better(maybe some more RAM) :mrgreen: 

Belive me, after having to play a lot with ndiswrapper, nothing is funny anymore, and then this. It takes the fun back in computing :-D 

Thanks again!

---

### Post by Necro-File on 2006-08-15
Great HOWTO but you should add that if you use network manager, you need to comment out all the lines from /etc/network/interfaces that refer to your wireless card in order for NetworkManager to manage your connection. :D

---

### Post by kob0724 on 2006-08-17
I followed this to a T, but I can still only select wired network from the network manager. What should I do next?

---

### Post by pyxu619 on 2006-08-18
nickm, you are soooo great. I works without a glitch. I have a broadcom 54g Airforce. The only thingis that I need to use a combination of markmcspadden way and yours to extract the firmware. I moved the bcmwl5.sys and bcmwl5.inf to desktop. Then type the following code in console to extract ```
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-26-386 ~/Desktop/bcmwl5.sys
```

Cheers!!! :)

---

### Post by K.Mandla on 2006-08-20
Thanks for this. I got the wireless (a 4306) going on an HP Pavilion zv6000 with this method. 

Cheers, all! :mrgreen:

---

### Post by oldguy46 on 2006-08-20
I have a Dell XPS 140

 lspci | grep Broadcom\ Corporation
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re v 02)

Will this HowTO  work with the Broadcom BCM4401

Under System/Device Manager I found
Intel PRO/Wireless 2200 BG

thanks for any help
og46

---

### Post by gholen on 2006-08-20
Great HOWTO as I said before, but I have this strange problem.

The Wireless are working just fine for an hour os so, then it disconnects](*,) 
Anyone with the same problem? Or better yet, a workaround?

Thanks

---

### Post by spd106 on 2006-08-21
> **oldguy46 said:**
> I have a Dell XPS 140

 lspci | grep Broadcom\ Corporation
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re v 02)

Will this HowTO  work with the Broadcom BCM4401

Under System/Device Manager I found
Intel PRO/Wireless 2200 BG

thanks for any help
og46

According to the wiki [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards) your Broadcom card is supported natively. The Intel PRO/Wireless 2200 BG card should also work without problem.

---

### Post by Xirto on 2006-08-21
Thank you so much for this guide!

---

### Post by oldguy46 on 2006-08-22
Thanks for the response.  I played a little with it and it does seem to recognize the wifi card.  It is not as convenient as the Windoze interface. (ie. reporting all wifi signals with strength and info)  Would WifiRadar and/or NetworkManager work better?  I am using the System:Networking interface so far. 
I am working 95% in Ubuntu now and liking it much better than XP.
Thanks again
og46

---

### Post by mooskradio on 2006-08-23
Worked great, thanks.  I'm using the BCM4318 and it still worked fine.

I saw the warning and tried to get it working with ndiswrapper, but it wasn't working and I didn't feel like debugging, so on a whim I blacklisted ndiswrapper and used this method.

ghlen, I had a similar problem, actually - the network manager applets kept on... I don't know what, shutting off the wireless card or something (couldn't find any access points until reboot) while I was using it and occasionally even freezing the computer and forcing a hard reboot, so I use iwconfig and dhclient on the command line.  Other than that, no problems.  If you need an explanation of how to do that, just ask.

---

### Post by jaybmx on 2006-08-23
worked fine using the bcmwl5sys.zip drivers on a Dell Latitude D610 laptop...

Great thread! Thanks!

---

### Post by kob0724 on 2006-08-23
What does this mean?

*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.*****: But this can be added in the future...


I tried it the first way with wl_apsta.o and that didn't work. When i tried it with bcmwl5.sys I got this error. Whats going on?

---

### Post by peregrine on 2006-08-23
Hey guys this is the Broadcom Chipset I have 

```
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

I have a Compaq R4000 with the Amd Athalon 64. I have 1.256g of ram and the Ati Mobility Xpress 200m(and I had a easier time with this then the wireless). 

Okay I tried your tutorial. I tried the ndiswrapper part.

With the bcm43xx I got the light to come on and for the very first try it worked. Then it stopped being able to connect to any wireless connection. Which is wierd cause nothing would make it work.

So then I blacklisted bcm43xx and tried the ndiswrapper. To no avail. It would make my wireless light turn on and off untill I rebooted then it would wait a while and start over.

So then I blacklisted ndiswrapper and removed the old bcm43xx driver files from lib/firmware and tried again. I tried both the wl_apasta.o and the bcmwl5.sys they both failed. 

Right now I'm on my knees begging for a option for this stuff. Maybe I did something wrong with ndiswrapper or maybe something wrong with bcm43xx. But please somebody help me. 

If you want to pm me or just reply I would really appreciate it.

Peregrine.

---

### Post by zytsef on 2006-08-24
Using a Dell Latitude D600 with TrueMobile 1400 (bcm4309) on 6.06 here.  Every time I try to load the driver the system hard locks.  Any ideas?  Also, wondering why the version of fwcutter in the repository doesn't seem to work on a lot of the drivers mentioned in the README.

---

### Post by kekojeep on 2006-08-24
Hi people,

I am having a weird problem with my Broadcom 4306 on a HP zv5466 laptop.. I use a wireless router at home, with other laptops (still on XP, as soon as my  is ready I'll begin converting the others to Ubuntu :) ).. the router is configured with WPA, and all the other computers can use it with no problem, at 54m on XP, even I used that before switching to Ubuntu.. well, after some fight and learning I got to do all the networkmanager-fwcutter process, and got Wi-Fi working.. almost.. I can connect to my home network, but only once after some 10 trials.. and ALWAYS when I try to connect, my router hangs, then I wait for it to reboot, then I keep trying to connect, some tries after it accepts and I get connected, working 100% until I turn off and try to connect again, then it begins all again.. Not to mention the complaints of the family each time I hang the router and kill all their connections :D 


 I have tried to connect to open wireless networks on lan-houses, it even connects but doesn't navigate on any page.. then if I try to disconnect and reconnect I can't connect anymore.. it's some sort of luck, I can't see no relation between when I can't connect and the few chances I actually get connected..

My dmesg says something about 

*SoftMAC: Authentication timed out with 00:03:c9:8c:a0:62*
and
*eth1: no IPv6 routers present*

What do you need to know to be able to hekp me (dmesg, lspci)? I can't stand using these wires anymore ](*,) :) If some gentle friend would help me solve this annoyance, I would really appreciate!

[ ]'s still on ethernet for now

---

### Post by kekojeep on 2006-08-24
PS: Why is it showing up H.E.K.P when I wrote H.E.L.P ?

---

### Post by oldguy46 on 2006-08-24
Still trying to get my Dell XPS140 working on wirless.

I loaded Widi-Radar and now I can see that the computer is seeing the wrt54G and correctly noting b or g speeds.  It mentions mode=Master (what does that mean) and shows four bars signal strength.  The essid is what the router is set to. 

When I click connect, it says 'acquiring IP address' ... then 'done'.  But the address it shows when not hooked to the ethernet cable is 127.0.0.1.  I know that this is the loop back. (About all that I know :) )

When the ethernet cable is plugged in, it shows an IP of 192.168.1.103  Shoudn't I get something similar when on wireless.

I have tryed with the route set to WPA, WEP, and open.  No Joy.

Any help appreciated,
og46

---

### Post by peregrine on 2006-08-24
Okay as I said before I have a Compaq R4000 with the BCM4318 chipset and with many people it doesn't seem to work. BUT THERE IS HOPE and it comes with one action.

Okay I scoured this thread and found one simple reply that fixed my problem. 

1. Follow this guide completely (prolly using the bcmwl5.sys)
2. Restart and check if the light is on.
3. Check if you have a connection to the internet.
If you have a connection your done congradulations!(if not continue)
4. Simply press the button to turn on/off the wirless. 
5. Check if you have a connection.

You should have a connection! Congrats.

It seems the current drivers keep the light on no matter what. And I don't know why but it eluded me forever. This is perfect I'd like to change my vote from 'No' to 'Yes' but your going to have to take a mental Tally.

Thanks for the great easy to use guide.

Peregrine.

---

### Post by jseldon on 2006-08-25
EDIT:  I finally did as the poster above mentioned and tried using the wireless enable button and got it working.  Once I figure out how to automate the process I'll let everyone know.

James

---


I have a Dell Truemobile 1450 (Broadcom 4309) that just won't work.  The card shows up as a pci device, I've got firmware in there but when it goes to grab an ip it returns the following error:

ADDRCONF(NETDEV_UP) : eth1: link is not ready

This is not too surprising however since I seem to have no signal either:

eth1      IEEE 802.11b/g  ESSID: off/any  Nickname: "Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr: off   Fragment thr: off
          Encryption key: off
          Link Quality: 0  Signal level: 0  Noise level:0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0


The card is loading the firmware as it certainly is enabled but just doesn't seem to get any link to my router.  I've seen a few people with this same error and didn't see a solution, any ideas what I might be doing wrong?

Thanks.

James

---

### Post by DieMongo on 2006-08-26
This is an excellent guide, and I just want to add a note:

In the beginning two things is assumed - one is a recommended reinstall of the os. I was very close doing this, because I've tried all kindz of suggestions posted on the web regarding this problem. **[COLOR="DarkRed"]BEFORE YOU GIVE UP AND REINSTALL THE OS you should follow one of the bottom links referred in this guide, and try the two steps here below[/COLOR]** - they worked for me! (and you should know that I'm running WPA-PSK) 
Needles to say - I know - but do a backup of these two files before editing :razz:  

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f")

- the important text from this link is dumped here:

1.3. NetworkManager

As of kernel 2.6.15-20, the driver appears to play nice with NetworkManager and nm-applet. When trying this, 
[COLOR="DarkRed"]**1) make sure wpasupplicant is disabled in /etc/default/wpasupplicant**[/COLOR] and 
[COLOR="DarkRed"]**2) all lines referring to the wireless card in /etc/network/interfaces are commented out**[/COLOR].

- o -

---

### Post by kob0724 on 2006-08-26
So My wireless connection works. I'm up and running. However, the newtork manager says I have no connection. This obviously isn't true because I wouldn't be able to type this otherwise. Anyone have any ideas. Are there other network monitors I could try?

On another note, any body know a good WEP/WPA client?

---

### Post by superkikim on 2006-08-26
Hi there... An excellent howto. Thank you so much. I've lost 8 hours today trying to make my wireless work with WPA.

A note for Dell users:

I have a Dell Latitude X300 with a Truemobile 1300 (BCM4306). I first tried with the driver provided on Dell website. It failed. At boot, my system was hanging with a "blabla suspend failed"... (don't remember exactly)

I then tried NDISWRAPPER... Very difficult to install and make it work. It didn't work obviously (with the same driver).

I finally came back on this thread, and I tried with the recommended driver. IT WORKED !!! easy.... So, just tried that driver whatever you have for a manufacturer. If it is a BCM43xx chip, try it. ;)

---

### Post by Melcar on 2006-08-26
So frustrating, really.  This is the only guide that sort of works for me.  Ndiswrapper just gives me the finger each time.  I'm using the bcmwl5.sys driver (the other one does not work for me) and can get my wireless connection working on the first try.  It works until for some reason it decides to drop the signal, and if I'm lucky it will reconnect, otherwise only a reboot will get it going again (sometimes pressing the wireless key on the laptop fixes it).  After a while, it would just stop working no matter what I do to it.

---

### Post by pedwards on 2006-08-27
hey all,

im having a problem and was wondering if i could get pointed in the right direction?

i followed this guide EXACTLY and it worked perfectly.  ive been a long time ndiswrapper user, but i really wanted to be able to use network-manager.  things were great untill i rebooted from 164 updates (this guide was the first thing i did after the install cd) 
Once i rebooted network-manager cant access wireless devices.  I am still able to use my wireless card but just not with network-manager
is there some issue with network manager when it changes from the 23 to 26?

here are my specs. 
dell 1150
broadcom 4306

thanks!

---

### Post by n00bWillingToLearn on 2006-08-27
> **pedwards said:**
> hey all,

im having a problem and was wondering if i could get pointed in the right direction?

i followed this guide EXACTLY and it worked perfectly.  ive been a long time ndiswrapper user, but i really wanted to be able to use network-manager.  things were great untill i rebooted from 164 updates (this guide was the first thing i did after the install cd) 
Once i rebooted network-manager cant access wireless devices.  I am still able to use my wireless card but just not with network-manager
is there some issue with network manager when it changes from the 23 to 26?

here are my specs. 
dell 1150
broadcom 4306

thanks!

This is just a guess, but sometimes when you update some configuration files get updated also so you might want to check your /etc/network/interfaces to see if all but the lines containing 'lo' are commented out ( as others have mentioned, not having these commented out may prevent network manager from showing those interfaces ).

---

### Post by prozaconstilts on 2006-08-27
I'm having a hard time getting my Broadcom 4309 to work on my Latitude D800. I clean installed, and immediately follwed the instructions, using the recommended wl_apsta.o driver. After fwcutter installed the .fw files to /lib/firmware and /lib/firmware/2.6.15-26-386, I went to install network-manager-gnome, and my system froze.

I then restarted in recovery mode to see what was happening. I saw the loading of the bcm43xx driver with no "cannot find microcode4.fw" errors, which I saw before installing the firmware. The boot-up continued for a short time (3-5 secs) and then froze again.

I booted off the LiveCD, mounted my hard drive, and removed the .fw files. I could then boot fine.

I then attempted to use the driver that came with my drivers disk, as well as the newest driver from Dell's website, but fwcutter could not extract the .fw files from either one.

lspci output:

lspci | grep Broadcom\ Corporation
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
0000:02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)


Any help would be greatly appreciated!

---

### Post by Globe_Trekker on 2006-08-27
Worked like a charm!  Thanks!  :D

---

### Post by NightwishFreak on 2006-08-28
I followed the guide and all seemed to be going well, until i tried to connect to a network. (I'm using a broadcom 4306 airport extreme BTW). I can scanand see all available networks, but cannot connect to any. when i check my logfiles, i see this: ```
robert@robert-laptop:/var/log$ tail -f  messages
Aug 28 20:40:41 localhost kernel: [ 3034.055603] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Aug 28 20:40:41 localhost kernel: [ 3034.055612] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Aug 28 20:40:41 localhost kernel: [ 3034.055621] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Aug 28 20:40:41 localhost kernel: [ 3034.055629] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Aug 28 20:40:41 localhost kernel: [ 3034.055638] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Aug 28 20:40:41 localhost kernel: [ 3034.055647] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
Aug 28 20:40:41 localhost kernel: [ 3034.055656] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
Aug 28 20:40:41 localhost kernel: [ 3034.055665] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
Aug 28 20:40:41 localhost kernel: [ 3034.055673] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
Aug 28 20:40:41 localhost kernel: [ 3034.066685] ADDRCONF(NETDEV_UP): eth1: link is not ready
``` Is this maybe a driver problem?? any info would be appreciated.

---

### Post by rgargett on 2006-08-30
Wonderful post! Easy to follow and ultimately successful!

I almost gave up until I thought to turn on the broadcast of the SSID for my network. After that it worked just like it should.

Thanks for all your work in writing this post.

---

### Post by revdev on 2006-08-31
I have a Belkin F5D7001 PCI and this guide worked great! It took me five minutes and it worked first try. It probably would have taken less than 2 minutes if i hadn't had to download the files in XP and then boot back. Thanks so much!

---

### Post by big_gie on 2006-08-31
> **NightwishFreak said:**
> I followed the guide and all seemed to be going well, until i tried to connect to a network. (I'm using a broadcom 4306 airport extreme BTW). I can scanand see all available networks, but cannot connect to any. when i check my logfiles, i see this: ```
robert@robert-laptop:/var/log$ tail -f  messages
Aug 28 20:40:41 localhost kernel: [ 3034.055603] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Aug 28 20:40:41 localhost kernel: [ 3034.055612] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Aug 28 20:40:41 localhost kernel: [ 3034.055621] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Aug 28 20:40:41 localhost kernel: [ 3034.055629] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Aug 28 20:40:41 localhost kernel: [ 3034.055638] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Aug 28 20:40:41 localhost kernel: [ 3034.055647] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
Aug 28 20:40:41 localhost kernel: [ 3034.055656] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
Aug 28 20:40:41 localhost kernel: [ 3034.055665] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
Aug 28 20:40:41 localhost kernel: [ 3034.055673] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
Aug 28 20:40:41 localhost kernel: [ 3034.066685] ADDRCONF(NETDEV_UP): eth1: link is not ready
``` Is this maybe a driver problem?? any info would be appreciated.

bcm43xx driver is not yet finished. This is why you get those TODO warnings. They are ment for the developpers. I think (I could be wrong) this is not related to your problem.

If nothing works, I highly suggest you try another firmware. I've tryed around 10 of them, from the original Dell driver to the more general one avaible from the .o file. I was surprised to see that the driver used in windows couldn't be extracted by bcm43xx-fwcutter. You need to experiment...

For me, bcm43xx wasn't stable enough on my 4306 (can't remember the revision) card. I'm back to ndiswrapper, and can use NetworkManager without any trouble (WPA psk, no SSID broadcast).

---

### Post by Old Pink on 2006-08-31
Worked for me, thanks alot. :) 

I'm posting from my Buffalo g54 WiFi card and Ubuntu, thanks to you! :D 

Should add, if you want the WiFi to work at startup, download "Wireless Assistant" using Add/Remove, and set the preference to "close once connection is made" (or similar) 

Then, put "sudo wlassistant" in the startup list.

---

### Post by groberts1980 on 2006-09-01
I've installed bcm43xx-fwcutter, following the guide, but when I get to this point:
```
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
```

I get:
```
Cannot open input file /home/smistir/Desktop/wl_apsta.o
```

I cannot find the file wl_apsta.o in my filesystem. Its certainly not on the desktop. Is that where the command is pointing it out to be?

---

### Post by big_gie on 2006-09-01
The file "wl_apsta.o" is the file containing the firmware that need to be extracted by bcm43xx-fwcutter.

Since there is many firmware for different cards, and different versions of those firmware, you will need some experimentation : find many of those files from different locations (keep a track of where you've found them and what version it is) and try them all. Keep the one that works and seems stable.

I think it the Readme of bcm43xx-fwcutter their is some location on where to find firmware files.

---

### Post by NoTiG on 2006-09-01
i get to the point where i install networkmanager and it asks me to insert a CD. wtf . i dont have any cd's. why cant it check my resposotiroes or the internet somewhere . :/

---

### Post by compwiz18 on 2006-09-01
> **NoTiG said:**
> i get to the point where i install networkmanager and it asks me to insert a CD. wtf . i dont have any cd's. why cant it check my resposotiroes or the internet somewhere . :/
Open Synaptic, go to Settings, click Repositories, and uncheck the CDROM box.

---

### Post by Papa-san on 2006-09-01
```
john@laptop:~$ lspci | grep Broadcom\ Corporation 0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```This is the card I have.
I followed the instructions, and when I re-booted, I had a four minute lag between signin at splash and when my desktop started to load. No wireless, and my 'network settings' GUI pops open empty. (Nothing visible but a white box on a tan background.) OK... there it is, after about seven minutes of trying. Plus it doesn't show any wireless, only lo and eth0.

Do you have any instructions for fixing the damage? Or do I just go ahead and re-install again?:confused:

Edit: I think I'll just follow my sig links... lol

---

### Post by DieMongo on 2006-09-02
> **Papa-san said:**
> ```
john@laptop:~$ lspci | grep Broadcom\ Corporation 0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```This is the card I have.
I followed the instructions, and when I re-booted, I had a four minute lag between signin at splash and when my desktop started to load. No wireless, and my 'network settings' GUI pops open empty. (Nothing visible but a white box on a tan background.) OK... there it is, after about seven minutes of trying. Plus it doesn't show any wireless, only lo and eth0.

Do you have any instructions for fixing the damage? Or do I just go ahead and re-install again?:confused:

Edit: I think I'll just follow my sig links... lol

- o -

A reinstall of the OS is absolutely the last option. First you should scan all the pages to see if there's a solution to fix your problem, sometimes it's very small changes that makes it all work. I know 49 pages is a lot, but here is a link to start with - a solution that worked for me:

[http://ubuntuforums.org/showpost.php?p=1424395&postcount=468](http://ubuntuforums.org/showpost.php?p=1424395&postcount=468)

/DieMongo

---

### Post by huntz on 2006-09-03
Finally I have got the bcm4318 of my Apple iBook G4 (Mid 2005) working. I have followed all hints from this thread, but I have got success with the last ppc (K)ubuntu kernel:
- 2.6.15-26-powerpc
- extracting with fwcutter firmware from the AppleAirPort2 (from OSX) into /lib/firmware and into /lib/firmware/2.6.15-26-powerpc
- using WirelessAssistant to join my test WEP AP

The only problem is the distance from the access point: I got a working network only very close to the AP ( <= 10m/30feet ). 
Damn! ](*,) . 

I'm searching a better usable solution. :rolleyes:

---

### Post by Kaneda_help_me on 2006-09-04
it's still not working for me. i've tried like...2 million different tutorials at this point. i know i havn't provided very much info, but that's because i don't know what to provide. i followed your directions exactly and it's still not working. please provide any input that you have, it would be greatly appreciated. 

thanks.

---

### Post by nickm on 2006-09-04
updated to include Edgy Knot 2 findings

---

### Post by ibwahooka on 2006-09-04
Nickm,
Thanks for the great tutorial.  Got me up and running in no time.  This is my first time using Linux and I'm really excited.  Since I like to sit in my easy chair and surf the net I was really jazzed that I got my wireless working. Keep up the good work!

Wahooka
-Linux newbie, looking for a better thing that Windows

---

### Post by jpspyro on 2006-09-05
When i run this command:

sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r`~/Desktop/wl_apsta.o

i get:

/lib/firmware/bcm43xx_microcode2.fw/bcm43xx_microcode2.fw/: File or Folder does not exist.

---

### Post by icky on 2006-09-05
0000:06:02.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)

is a failure, i'll see what i can do :(

---

### Post by Janster on 2006-09-08
Thanks a lot. I have the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) and only went as far as step 4b and it worked perfectly. Great job.

---

### Post by ka1axy on 2006-09-08
I'm dual booting a company-issued Dell D620.  lspci says:
0000:0c:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

Everything worked according to the instructions.  Was unable to extract the firmware from the Windows .sys file, but the wl_apsta.o extraction worked as advertised.

My network showed up in the applet when rebooted, and I entered the WEP key, and connected at 11 Mb/s (it's a "g" network, so I had expected 54Mb/s,  but hey, I'm not picky)

Thank you!

Peter

---

### Post by Sh8kR on 2006-09-09
> **icky said:**
> 0000:06:02.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)

is a failure, i'll see what i can do :(


I am in the same boat did you ever get it working? I tried this and a few other walk throughs and still no luck. I have even updated my kernel to see my dual core and that did not change it. I had Kantiox on it and even recompiled the kernel but it did not see the wifi card. So I am at a loss I am going to try the "WifiDocs/Driver/bcm43xx/Dapper" and the "WifiDocs/Driver/Ndiswrapper" to see if they give any other steps but I am getting frustrated. 

Rumptz

---

### Post by tpariel on 2006-09-09
hi all,

thanks a lot for your exellent guide It worked perfectly for me and I have bad WiFi card the Broadcom BCM4318.

thanks again,
cheers Ariel

---

### Post by cemptor on 2006-09-11
> **Janster said:**
> Thanks a lot. I have the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) and only went as far as step 4b and it worked perfectly. Great job.


I wonder if you can help me. I have the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) too, and it does not connect to the router. It's a US Robotics 805417 WirelessG PCI card.

- The card is recognized by the GNOME Networking tool
- ***I can actually see the router*** on doing iwlist eth0 scan
- The interface eth0 seems to be attached to my router, if I see iwconfig


Just cannot authenticate to get an ip address. dhclient keeps giving me the message "no leases offered".

I am using wpa_supplicant, and when I run it with more debug messages, I noticed a strange thing. It seems to be trying to connect to my router but the frequency used is 0. My router's frequency is 2.437 Ghz. Is there a way to force the card to use a certain frequency?

Could that be some kind of problem? 

I've followed the instructions to the letter, except not using Network Manager. It's a clean install of 32 bit Ubuntu

1. extracted the wl_apsta.o firmware to /lib/firmware
2. modified /etc/networking/interfaces to use wpa_supplicant for eth0 (my card)
3. Set up wpa_supplicant to authenticate to my router. wpa_supplicant is known to be working (tested with ndiswrapper and another card)

The network router has a mixed mode network and any speed.

Have tried every trick in this list:

- blacklisted ndiswrapper
- modprobe bcm43xx
- turned the card off and on
- tried without any authentication
- changed rate to 11M / 36M / 54M

Help!

---

### Post by erik plaggenmars on 2006-09-12
OK, why is this not a sticky??? I bet a lot of guys would be happy with this howto.

Worked like a charm for me! :D

Thank you so much!

PS. (maybe for author to note in #1 post.)

I got the error:
"The NetworkManager Applet could not find some required resources. It cannot continue."

After i was trying to load the network manager applet. I was able to fix it with the command:
```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

Hope it helps for the guys having the same problem as me.

---

### Post by KeeNeR on 2006-09-16
Thanks nickm! It worked like a charm for a Broadcom 3411.
great guide linked on my blog.

---

### Post by brianab86 on 2006-09-16
I went through all of the steps, but the Network Manager Applet does not show a wireless connection; it is only showing the wired one.  Any advice?

---

### Post by tuxy on 2006-09-16
A very good post on Broadcom Wireless cards. It worked like a charm for me.
Great work Nickm.

---

### Post by jpeterse on 2006-09-16
Thanks for putting this update out here.
I've worked for most of a day and couldn't figure out why I could not connect to the AP.

This solution should clearly be listed in the howto post.

I had to make one change though. IfUP would not read the Interfaces file unless I moved the auto eth1 line above the definition of the interface.

I did have a complete system lock-up after running the script manually. I hope it's not a sign of instability of the driver.

Thanks for your assistance.
Jan Petersen

> **samjam said:**
> I have a linksys bcm card, I had no trouble getting it to work with native bcm drivers WITHOUT encryption, but who wants to run an open network?

Here's my solution to getting it working on bootup with encryption:

Put this in a file called: /usr/local/bin/bcm43xx


and then this fragment in my /etc/network/interfaces


If I specify the essids and keys in my network interfaces it doesn't work
If I try to associate with the essid/AP with encryption on, it always fails, hence the script makes sure it is turned off.
So then I set the essid, wait, and then I set the key and I have to say "restricted"

A most telling message in dmesg or /var/log/messages is one like this:

Jun  2 20:56:23 localhost kernel: [4295485.996000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

the magic "link becomes ready" means essid and encryption all working fine.

---

### Post by nullmind on 2006-09-17
I have the **AirForce rev 2 bcm4318** and this guide worked for me (I did black list ndiswrapper) A few things to note are:

Signal strength is invalid
The connection can flake out sometimes, happens often in public areas with a lot of signals (coffee shop)
When coming out of hibernation

Fiddling with the mod (reloading it, etc.) fixes most of these issues. Works great with my encrypted network and wpasupplicant.

---

### Post by lstomberg on 2006-09-17
Thank god there is someone out there who likes me :)... I have had alot of problems with my wireless and linux.  I have always heard of ubuntu and decided to give it a go.  Found out right away that it recognizes that I have a wireless card but it wouldn't connect.  I went online on ethernet and found your site right away.  Went through and when you said to type in the command to tell me what kind of wireless card I had I trembeled because I have the one that people say DOES NOT work :(... well i continued on and in the end everything works perfectly!  Thank you sooo much for your help i really appreciate it.

---

### Post by cyklonmetal on 2006-09-17
hi there, new to ubuntu but fooled around with mandrake and suse a few years back before i was lured back to the dark side.  anyway, my problem is how to install the bcm43xx package i downloaded from berlios.de.  i cant download using the synaptic manager cause im not conneted to the internet.  i can only connect using t-mobile hotspots so i think i have a chicken and egg problem.  i've already downloaded it using a different pc and copied the files to my desktop but cant figure out how to install it.

any help would be appreciated. thanks...

---

### Post by gtkourounis on 2006-09-17
This is an incredible post i have to say. thanx a lot, but the problem with me is that i have the cused broadcom 4318. I have tried EVERYTHING and it never works. I am not going to ask how this is going to work out for me because i know that there is no possible way for that to happen. All i want to ask is what other card should i buy? I guess i am going to have to buy a WiFi card to get WiFi on my laptop. So if you could please give me a tip on what card i should go and buy (the ones that you can insert in the WiFi card socket that every laptop has) and that would work with ubuntu, that would be more then thankfull.

Thanx in advance

PS: I have a Acer 5002WLMi

---

### Post by Andrew Borem on 2006-09-17
Okay.

Ubuntu 6.06
Dell Truemobile 1300
Broadcom 4603 (I think)

Followed the guide in the first post to the letter.  The light on my wireless card turned on like it does on windows. But it still doesn't work.  I don't UNDERSTAND.  :D  My network manager does not show a wireless signal at all.  I am three feet from my router.  So yes.

I am wired as well, so it is okay.  I have also tried setting up a static IP and junk.

Any help or suggestions would be appreciated!  Thank you!

---

### Post by tva88 on 2006-09-18
tnx u!!! :D  i have tryd to fix my WLAN al night long... this is the only guide that has workt whit my BCM4318 card.... :wink: works only whit gde, not kde... or do some1 have a smart solution to that? :-k

---

### Post by kimo818 on 2006-09-18
d

---

### Post by jorgenbear on 2006-09-18
Did all the steps, but when I type in:
[INDENT]sudo modprobe bcm4306
[/INDENT]
it gives me this error:
[INDENT]FATAL: Error inserting bcm43xx (/lib/modules/2.6.15-27-386/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
[/INDENT]

Any suggestions for what's wrong?

Jorgen

---

### Post by Andrew Borem on 2006-09-18
Hah!  All I needed to do was reboot.  I am one happy customer now. Thanks, dude!

---

### Post by pauljwells on 2006-09-19
Worked for me on an Apple Powerbook, but not with Network-Manager. I had to install wifi-radar, which works fine!

Kudos

---

### Post by samssf on 2006-09-19
Didn't work.

I had all the prereqs and have the linksys wmp64gs v1.1 broadcom 4306 chipset.

On step 4 you ask us to type "sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o"

Where is the .o file??? The file you provided for download contains a .sys, not a .o

I used the .sys file and that seemed to work for that step, but I have no idea.

Also, you said /lib/firmware. Do you mean replace the word firmware with my firmware version? Cause if so, that isnt obvious at all... especially for someone new to linux. Another post mentioned to do that.

---

### Post by jubilee33 on 2006-09-20
Ubuntu Dapper 6.06
kernel: 2.5.16-27-686-smp
Broadcom BCM4311 UART (rev01)

Thanks a lot for the howto.  It worked like a charm.  I didn't even have to use the network manager applet.  I just did System --> Administration --> Networking and the wireless connection just worked.

---

### Post by nullmind on 2006-09-20
> **cyklonmetal said:**
> hi there, new to ubuntu but fooled around with mandrake and suse a few years back before i was lured back to the dark side.  anyway, my problem is how to install the bcm43xx package i downloaded from berlios.de.  i cant download using the synaptic manager cause im not conneted to the internet.  i can only connect using t-mobile hotspots so i think i have a chicken and egg problem.  i've already downloaded it using a different pc and copied the files to my desktop but cant figure out how to install it.

any help would be appreciated. thanks...

If you downloaded the .deb then you would do something like this:

```

sudo -s
dpkg -i <name of file.deb>

```

You might even get away with just using the graphical dpkg manager when you open it from the desktop environment. If it's a tarball (.tar/.tar.gz) you will have to untar it (you can use the Archive Manager) and the read the INSTALL file inside, but chances are you will only have to do this:

```

sudo -s
./configure
make
make install

```

---

### Post by musicatplay on 2006-09-23
Excellent work!  This worked flawlessly on my Compaq Presario r4225ca!  I've struggled on many occasions to follow instructions elsewhere but you did a fantastic job of making it painless for a newbie to the linux world.  

You have brought me one step closer to getting rid of M$... :D 

Thank you,
musicatplay

---

### Post by Jahflames on 2006-09-23
thank to you my wireless is running fast than ever im a newbie to the linux world and loving it thanks alot

---

### Post by gooseneck on 2006-09-24
Thanks for such a great How To!  It got my wireless connection working right away!

---

### Post by yo2k4yo on 2006-09-24
Thanks a lot nickm, for wrting such a wonderful guide. I was about to give up and move to knoppix, but you made it easy and quick to stay in ubuntu.

0000:03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Linksys WPC54GS
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>
00: e4 14 20 43 06 00 10 00 03 00 80 02 00 40 00 00
10: 00 00 00 f6 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 81 10 00 00 37 17 20 43
30: 00 00 00 00 40 00 00 00 00 00 00 00 0b 01 00 00

---

### Post by susancragin on 2006-09-24
:( Didn't work for me. 
Acer Ferrari AMD64 Broadcom BCM4318 AirForce One 54g
bcmwl5.sys
Installs fine. PCMCIA card lights up real nice, lights flicker with activity. 
Wireless assistant recognizes my wireless and a couple of other networks within range. 
Try to activate, but nothing works. 
Susan Cragin:confused:

---

### Post by devoinregress on 2006-09-24
It worked great! I had to install WPA support.

Big problem though. Wireless is not working in Windows...
Is their any way to get WIFI working in both OS's?

---

### Post by Sokraates on 2006-09-25
> **susancragin said:**
> :( Didn't work for me. 
Acer Ferrari AMD64 Broadcom BCM4318 AirForce One 54g
bcmwl5.sys
Installs fine. PCMCIA card lights up real nice, lights flicker with activity. 
Wireless assistant recognizes my wireless and a couple of other networks within range. 
Try to activate, but nothing works. 
Susan Cragin:confused:
 
bcm4318 is a chore to setup. Try this guide, it worked for me:
 
[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)
 
 
> **devoinregress said:**
> It worked great! I had to install WPA support.
 
Big problem though. Wireless is not working in Windows...
Is their any way to get WIFI working in both OS's?
 
The last time this happened to me, the card was simply deactivated in Win. Take a look at the Systemsettings (uhm ... no, thats KDE, well you propably know what I'm talking about) under Network Connections. Also take a look at whatever other app manages the card (on a laptop usually a tool from the laptop-manufacturer). It can also be used to deactivate the card.
 
If nothing works, simply reinstall the drivers (a crazy idea: you didn't accidentally remove them, did you?). 
 
Fumbling with the card and its driver in Linux has no effect on its performance in Win or any other OS. So the reason must be with Win.

---

### Post by kikos on 2006-09-25
I followed your HOWTO but it didn't work for me with my BCM 4309.  However, after I added "ndiswrapper" to /etc/modules and rebooted, it works fine.

---

### Post by matchman on 2006-09-26
BCM 4318 in a Gateway MX6440 
  I had no luck with ndswrapper 
I kinda had luck with this guide. Everything worked great first boot. Next boot the wireless conection was no longer there and my LAN quit working. Wiconfig seen my router and all looked good.
The Network tool that is included in Ubuntu indicated all is good on both devices. 
 Bottom line is the Network tool that you are instructed to download "and use" must be the the only one controling the networks!

 auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp


#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

---

### Post by smock9 on 2006-09-28
> **ka1axy said:**
> I'm dual booting a company-issued Dell D620.  lspci says:
0000:0c:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

Everything worked according to the instructions.  Was unable to extract the firmware from the Windows .sys file, but the wl_apsta.o extraction worked as advertised.

My network showed up in the applet when rebooted, and I entered the WEP key, and connected at 11 Mb/s (it's a "g" network, so I had expected 54Mb/s,  but hey, I'm not picky)

Thank you!

Peter

I have the exact same machine with the same hardware.
I followed the HOWTO and was able to see my wireless network listed.  When I attempt to connect with my WEP key it takes a while "thinking" and then sometimes works and other times just keeps asking me for the key.  Either way in a few moments the whole system freezes.  No response from mouse or keyboard.  Yes, I locked up a linux box...  

Anybody run into this?  It seems like the described series of commands comes close to working considering it actually begins to communicate with the router.  What would cause the whole system to freeze like that?

Thanks,

Jon

---

### Post by Icoo on 2006-09-30
I have a HP NX7400 with a Broadcom 4311 chip and it didn't worked for me? I did all the steps! Help?

---

### Post by statikeffeck on 2006-09-30
Thanks for the nice guide. I have a Dell Inspiron 5100 Laptop with the bcm4306 chipset and I had to troubleshoot this for a while. I found that using Ubuntu's built-in System->Administration->Networking control panel will fudge up your wireless configuration.

I'm going to repeat & add to what another user posted which is what really helped me get this going (I can't find the original post so I forget who it was).

If you've been fiddling around trying to get it to work and you want to start over, do this:

1. Remove bcm43xx-fwcutter package (Use the Synaptics Package manager and search for bcm43, right click and remove completely, then apply).
2. Remove Network-Manager and Gnome-network-manager, again with the synaptics package manager.
3. Delete all the files that begin with bcm43 in your /lib/firmware directory, then browse in the 2.6.whatever folders under /lib/firmware and delete bcm43* files also.
```

cd /lib/firmware
sudo rm bcm43*
```
(this basically undoes the steps when your run fwcutter.)
4. At this point it might be a good idea to use the Ubuntu Software updater utility (because if you update later, you might have to repeat these steps to get wireless working again).
5. Comment out (using #) or delete all the lines in the text file: /etc/network/interfaces except the lines for loopback (lo).
```
sudo gedit /etc/network/interfaces
``` 
That will pop open an editor so you can delete the unnecessary lines and save it.
The file should only have:
```
auto lo
iface lo inet loopback
```
in it.
6. Restart the computer and you should be able to start fresh with the guide.

It works fine now, but it seems after booting up I have to manually click the network manager icon to connect to my network. I want to figure out a way that it will auto connect to a network of my preference.

---

### Post by mn_kthompson on 2006-10-02
This worked on my Dell Latitude D800 Laptop running Edgy Knot 3 with a Broadcom BCM4309.  I followed the instructions but it didn't work.  However, after I set my package manager to get updates from the Universe I downloaded a bunch of stuff and rebooted.  Then it worked.  Thanks for the great HOWTO

---

### Post by alecjw on 2006-10-03
> **mn_kthompson said:**
> This worked on my Dell Latitude D800 Laptop running Edgy Knot 3 with a Broadcom BCM4309.  I followed the instructions but it didn't work.  However, after I set my package manager to get updates from the Universe I downloaded a bunch of stuff and rebooted.  Then it worked.  Thanks for the great HOWTO

What bunch of stuff???

---

### Post by alecjw on 2006-10-03
> **samssf said:**
> Didn't work.

I had all the prereqs and have the linksys wmp64gs v1.1 broadcom 4306 chipset.

On step 4 you ask us to type "sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o"

Where is the .o file??? The file you provided for download contains a .sys, not a .o

I used the .sys file and that seemed to work for that step, but I have no idea.

Also, you said /lib/firmware. Do you mean replace the word firmware with my firmware version? Cause if so, that isnt obvious at all... especially for someone new to linux. Another post mentioned to do that.

Read the first post. There is a link to wl_apasta.o.

---

### Post by alecjw on 2006-10-03
[SIZE="7"]THANK YOU SOOOOOOOO MUCH![/SIZE]
I've got an internet connection in ubuntu now!!!

---

### Post by wanger123 on 2006-10-04
Thanks to everyone in this thread and community. I have recently been forced to switch from Linux to OSX for my main program at work so I was kinda bummed. But then I found dapper ppc version and I now dual boot with OSX. This was a huge issue not having wireless working in kubuntu. 

But NOW IT DOES!!!!!!!!!!!!!!!!!!!!!

YEE HAA!!!

thanks to all

ps I have the BCM4306 card

wanger

---

### Post by drscatris2004 on 2006-10-07
I have got Acer Aspire 5024wlmi notebook... and using edgy beta 2.6.17.10.386 kernel
try this post bcm4318 rev2 card this afternoon...
result:
Acer-acpi working good.!
Network blinking good!
Clearing network/interfaces.. network manager is good working.. but not wifi radar only editing and addinng wifi working 
Im using wpa2 tkip key but not correctly working ... only un encryptic rule is working.
cat5 cable networking not good working ip adress and gateway is not correct myway its not working.
only editing network interfaces correct static ip address and gateway then after cable network working..
general results:
few modules is good.. windows based wpa and wep is good.if is good working
but not correct ip address and gateway is bad. only manual editing..

---

### Post by Sgood1971 on 2006-10-10
Thanks, after hours and hours of trying everything else I got my Dell Inspiron E1405 with a broadcom 4311 working. Thanks again.

---

### Post by lyceum on 2006-10-11
Okay, first, thank you to everyone who worked so hard to put this thread together. I finally see the blue light of hope on my laptop. I am having few problems, & am hoping someone can help.

The card does seem to be working, but I do not see it in my network connections options. I typed in eth1 and it created a new icon, eth1, and it is WiFi, but I cannot access the net. It says the eth1 is disabled. I went to Networking and typed enabled the card by typing in my 2WIRE router and hex ID. This seemed to turn the WiFi on, but it still says disabled. I did re-start, no help there. My wife told me that the people at AT&T told her that 2WIRE would not work with Linux, but we thought they were talking about their card, not the router. If you know any thing then, HELP! PLEASE! I know nothing about networking, and though this has been a great learning tool, I have been at this for over a week now. Any help would be great. Thanks.

---

### Post by michaels on 2006-10-11
Thank you guy! Great job!

---

### Post by bfitzsimons on 2006-10-11
I am a totally frustrated newbie ...

My hardware is:
Apple iMac with 1GHz PowerPC G4 and 768 MB DDR SDRAM using dual boot: MacOSX 10.2.8 and Ubuntu 6.06 LTS;
Apple Airport Extreme Base Station using Controller Broadcom BCB4306;

I have wireless connection under the MacOS boot but not under the Ubuntu boot.  I have downloaded onto another office iMac various files and folders, burned them at slow speed to a CD, and copied to the Ubuntu desktop.  In Terminal, the following commands give the results ( -> ) noted:
$ lspci | grep Broadcom -> 0001:10:12.0 Net controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller ( rev 02)

$ ls Desktop -> bcm43xx-20060125 [this is a folder], bcm43xx-fwcutterorig [this is a folder], bcm43xx-fwcutter-005 [this is folder], bcmwls.sys [this is a file], wl_apsta.0 [this is a file]

$sudo apt-get install bcm43xx-fwcutter -> 
    Reading package lists ... Done
    Building dependency tree ... Done
    E: Couldn't find package bcm43xx-fwcutter

The above was tried with and without the Desktop/... path included - all give the same result.  I have tried other tests noted in other threads and always end up with:

$ iwconfig ->		
                    lo 	no wireless extension
		eth1	IEEE 802.11b/g  ESSID: "BEINetwork"  Nickname: "Broadcom 4306"
			Mode: Managed  Frequency=2.437 GHz  Access Point: Invalid
			Bit Rate: 1 Mb/s
			RTS thr: off  Fragment thr: off
			Link Quality:0  Signal Level:0  Noise Level:0
			Rx invalid nwid:0  Rx invalid cypt:0  Rx invalid frag:0
			Tx excessive retries:0  Invalid misc:0 Missed beacon:0
		eth0	no wireless extension
		sit0	no wireless extension

Very stupidly I ask: how do I install - step by painful step - bcm43xx-fwcutter ?

---

### Post by bfitzsimons on 2006-10-12
Follow up on my initial Post #537:

In another Thread I followed a reference to: [http://monkeyblog.org/ubuntu/install...ckage_manually](http://monkeyblog.org/ubuntu/install...ckage_manually)
and at Terminal entered the following commands with the results (->) as shown:
$ cd Desktop/bcm43xx-fwcutter-005
$ ls -> results in a list of files in that folder = bcm43xx-fwcutter.1, fwcutter.c, fwcutter.h, fwcutter_list.h, md5.c, md5.h, makefile, readme, and another folder svn which has more files in it.
$ ./configure -> no such file or directory
$ make -> command not found ... at this point, I even tried $ ./makefile -> command not found

What do I do now ... ??

---

### Post by lyceum on 2006-10-12
Updateing from above, I canot get into my home network, but I took my laptop to school and I could see the wireless rout. However, when I tried to conect to it, my card was not enabled. So it works, but is not enabled? I clicked on the enable box, but it still did not enable. Does this make sense to anyone? My laptop ended up freazing up on me. I think I am ready to open my laptop and replace the wifi with a better driver, one that is Linux compatable out of the box. ](*,)

In case anyone has any advice, I am using a 4311. Was I suppose to change the 43xx to 4311? and Netware maneger made things worse for me. I couldn't find the network until I shut it off.

---

### Post by boogyman on 2006-10-13
When I tried the
{sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o} 
I got in reply
{Sorry, the input file is either wrong or not supported by fwcutter.
I can't find the MD5sum 0a0db830f28c54f6266043b063cec272 :( }
Do you know why this is?

---

### Post by stixdannov on 2006-10-13
it seems that after following every step my wireless device has disappeared from the network settings menu.  I have no idea what to do as i'm installing linux for the first time.

---

### Post by shortstack on 2006-10-14
you are my hero. i tried everything under the sun to get my wireless working and about 70 different websites and forums. i love you. \\:D/

---

### Post by sbentzen on 2006-10-15
ok, just wondering, does this guide work for airport extreme, cause  i am running an ibook g4, and would like to dual boot, though i really wonder if this works, i have a wep network aswell.

---

### Post by dan828 on 2006-10-17
OK, after trying everything under the sun, since I first tried Hoary, I finally got it working with your method on my HP ZD7000 running Edgy now.  Kudos to you.

---

### Post by jrz on 2006-10-17
> **boogyman said:**
> When I tried the
{sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o} 
I got in reply
{Sorry, the input file is either wrong or not supported by fwcutter.
I can't find the MD5sum 0a0db830f28c54f6266043b063cec272 :( }
Do you know why this is?

A friend and I spent the day trying to get his wireless working and encountered the same thing. What we seem to have found was that by re-downloading the file several times we encountered the same error 3 times, each time displaying a different MD5sum, which led me to believe the file was being corrupted in transit and on the 4th try it was OK. So you may have to do the same thing, download the file again and use it and notice if it fails, does it display a different MD5sum, and if so you have just received another corrupted copy and must download again until you get a good copy. We were using Firefox to download with and I don't believe it checks what it downloads to assure the file is not corrupt.

---

### Post by jrz on 2006-10-17
Using a Compaq Presario V3042AU, AMD64 X2, Ubuntu 6.06 LTS i386 version freshly installed, and a Broadcom BCM4311 wireless, we followed the instructions carefully and still are unable to use the wireless.

My first question is, should we remove anything prior to trying a new approach, and if so what is the correct procedure as we would not like to leave many useless files around that may cause future concerns.

Second, although we read somewhere in the numerous posts that it is "IMPERATIVE that you use wl_apsta.o", I am wondering if it may be worth trying the Windows drivers I downloaded from Compaqs website and opened on a Windows system? And if so would we use just the bcmwl5.sys file alone which is included in the folder created by the Compaq download or are other files from that folder necessary as well?

Primarily we do not wish to proceed further until we are certain that we are not leaving files scattered that may cause conflicts when attempting other procedures. 

Last question, What commands should we use to display that the wireless is installed properly and all settings are correct? Should we be able to set an IP address unique from the one we set for the wired connection, or does it use the same IP address to connect to the router?

The 'How to' is very useful, but an addition telling what to do when something doesn't work might be helpful also as once something is installed I'm not sure how to remove it, and if it doesn't work it would appear that what was installed should not be left.

Thanks

---

### Post by cherokee on 2006-10-17
> **jrz said:**
> Using a Compaq Presario V3042AU, AMD64 X2, Ubuntu 6.06 LTS i386 version freshly installed, and a Broadcom BCM4311 wireless, we followed the instructions carefully and still are unable to use the wireless.

My first question is, should we remove anything prior to trying a new approach, and if so what is the correct procedure as we would not like to leave many useless files around that may cause future concerns.

Second, although we read somewhere in the numerous posts that it is "IMPERATIVE that you use wl_apsta.o", I am wondering if it may be worth trying the Windows drivers I downloaded from Compaqs website and opened on a Windows system? And if so would we use just the bcmwl5.sys file alone which is included in the folder created by the Compaq download or are other files from that folder necessary as well?

Primarily we do not wish to proceed further until we are certain that we are not leaving files scattered that may cause conflicts when attempting other procedures. 

Last question, What commands should we use to display that the wireless is installed properly and all settings are correct? Should we be able to set an IP address unique from the one we set for the wired connection, or does it use the same IP address to connect to the router?

The 'How to' is very useful, but an addition telling what to do when something doesn't work might be helpful also as once something is installed I'm not sure how to remove it, and if it doesn't work it would appear that what was installed should not be left.

Thanks
I had the broadcom 4318 rev 02

The way it is working I have to type sudo modprobe on reboot and log in.

Thanks for the work that was put in this card. I belive it will work out of the box soon

---

### Post by jrz on 2006-10-18
We had tried using modprobe as well and it didn't change any thing, so we are looking to trying some other solution, but wish to clean up every thing we have done so far first.

---

### Post by lyceum on 2006-10-18
I am also using 4311, if you get yours working, please let me know how. It sounds like I have followed the same steps as you, and my card will not configure. I can see wireless networks, but I can't use them. Thank you!

I do have to say, don't install netware manager. It messed things up even more for me.

---

### Post by motrennoc on 2006-10-18
Hi,
Great How to. It worked like a charm. That is up until a couple of days ago.
The (Broadcom) Dell true mobile 1300 miniPCI was working very well. It took some time to get WEP working  but I finally did. 

Then the wireless network tick under the network connection disappeared and it no longer "senses" the wireless connections avaiable. In  network setting the Wireless connection says The network connection eth1 is active and it has the right network name and WEP key.

I tried removing (via synaptic) nm-applet and then reinstalling. But this did not help. I've tried "resetting" the DSL and wireless router. I've tried deactivating and reactivating the wireless connection as well as redoing the WEP key. I've turned the WEP protection off and it still doesn't "sense" the wireless net. I've tried to turn on/off the wireless card but there's no indication of it turning on off with fn-F2. I've run iwconfig and this is the output:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"home"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Anyone have any ideas?

---

### Post by jrz on 2006-10-19
Something that I feel might be helpful to those of us new to Linux, would be a list of commands and their functions which relate to wireless. Not knowing exactly what to do first, second and so on, it would be nice to have a list telling what commands could be used to provide information as to whether or not the card is recognized by the system, and then a list of commands that would display information telling that everything is installed completely and properly. Additionally, when packages are installed and don't work, it would be nice to know if they should be removed and how to do that properly. I'm sometimes hesitant to try something for fear of being unable to recover if it should cause the system not to boot. We were not provided with any means of re-installing the system as it came pre-loaded with Ubuntu 6.06 LTS and would have to ship it some distance to get it re-installed. Sorry for such a big request, but if I were more certain of how to recover from mistakes I, and probably many others, would be willing to take risks. A major cause of reluctance to try Linux is often pointed out to be the learning curve, and from what I have seen, it is not due to the unavailability of information, but instead the huge abundance of information which can quickly overwhelm someone who is new to Linux. We have spent many hours googling for info and have found so much, and often so many different paths of solving the same problem that we don't know which to follow and what we should do when we find a solution doesn't solve our problem. And I must add that I want very much to eliminate my dependency on MS Windows so we are trying very hard to learn all we can about Linux.

Thanks to those who have offered suggestions to date, and we will keep plugging along until we resolve all our problems with your kind assistance.

Joe (Northern Thailand)

---

### Post by jrz on 2006-10-19
An afterthought question:

Are there 2 methods of installing a wireless LAN card in Ubuntu?
From what all I have been reading it appears that one method is a Linux method and the other uses something called ndiswrapper which if I understand properly, is a program which acts as a go between allowing Linux systems to communicate with a Windows driver. I therefore assume that using ndiswrapper should be a second choice solution to be used when all else fails?
An email to Broadcom led me to believe that they only produce the chip used in the wireless card and someone else produces the card and therefore they provide no direct end user support. Compaq, the producer of the notebook we are using recommends Windows OS, and should you wish to purchase a notebook to run Linux, suggest you purchase a particular model which they provide with a Linux (SUSE) OS installed. I did not notice any other name on the card to indicate who manufactures it so I don't know who else to email with questions.

---

### Post by mobo on 2006-10-19
Good Job Nick =D>

---

### Post by motrennoc on 2006-10-20
Great How to!
Thanks:D

---

### Post by Bob Mikok on 2006-10-20
Wow, this worked like a charm for me. I got tired of windows and jumped right into Linux without ever looking back. I have a Buffalo Air Station WL12-PCI-G54S PCI Adapter (which has broadcom chipset). Thank you for creating this thread!!! Now I can kick some more butt with my 26 dbi grid dish with 1w booster! :-D

---

### Post by lyceum on 2006-10-20
I am impressed you got as far as you did. When I called Compact, they not only did not know what Linux was, they also thought that hardware was (I'm not kidding) really complex software. 

Yes there are more than one ways to set things up. I have not been able to make either way work, but I can't use ndswrapper as my laptop was sold with no disks, and I could not find the driver at Broadcom's page. I really didn't know as much then, so I am going to look again if I can't get things to work with this method. At this point I am waiting for 6.10 to come out to try again.

> **jrz said:**
> An afterthought question:

Are there 2 methods of installing a wireless LAN card in Ubuntu?
From what all I have been reading it appears that one method is a Linux method and the other uses something called ndiswrapper which if I understand properly, is a program which acts as a go between allowing Linux systems to communicate with a Windows driver. I therefore assume that using ndiswrapper should be a second choice solution to be used when all else fails?
An email to Broadcom led me to believe that they only produce the chip used in the wireless card and someone else produces the card and therefore they provide no direct end user support. Compaq, the producer of the notebook we are using recommends Windows OS, and should you wish to purchase a notebook to run Linux, suggest you purchase a particular model which they provide with a Linux (SUSE) OS installed. I did not notice any other name on the card to indicate who manufactures it so I don't know who else to email with questions.

---

### Post by bicchi on 2006-10-21
I am having problems with the BCM4309 on a Dell Latitude D600 using the method listed here. I get to see my wireless network with the gnome network manager but when i try to connect to it, it just hangs for a long time and goes back to the wired connection. Gnome network manager displays the message: Waiting for Network Key for the wireless network 'Bicchi'. 

I am running a linksys WRT54GL router with the DD-WRT firmware. Yes, it works from windows.
I have my router set as: 
Security Mode: WPA2 Pre-Shared Key Mixed
WPA Algorithms: TKIP+AES
 
When i run "sudo iwlist eth1 scan" i get:
```

eth1      Scan completed :
          Cell 01 - Address: ** MAC ADDRESS GOES HERE **
                    ESSID:"Bicchi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-27 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 200ms ago

```

Running the command: "sudo dhclient eth1" gives the following:
```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/** MAC ADDRESS GOES HERE **
Sending on   LPF/eth1/** MAC ADDRESS GOES HERE **
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Any advice on how to fix this?

---

### Post by motrennoc on 2006-10-21
bicchi,
That sounds exactly like the problem I'm having. (Dell inspiron 8500) Did yours work briefly then disappear. The first time I thought it was something I did so I reinstalled everything. Ran through this how to and it worked for about 2 days then the "enable wireless" disappeared and I get the same "waiting for network wireless key" message. If you get this figured out please post it here and I'll do the same.

---

### Post by bicchi on 2006-10-21
> **motrennoc said:**
> bicchi,
That sounds exactly like the problem I'm having. (Dell inspiron 8500) Did yours work briefly then disappear. The first time I thought it was something I did so I reinstalled everything. Ran through this how to and it worked for about 2 days then the "enable wireless" disappeared and I get the same "waiting for network wireless key" message. If you get this figured out please post it here and I'll do the same.
In my case it happens to be a fresh install of Edgy RC from this week and wireless has never worked for me on Edgy. I might try to download Dapper to see if its an issue with Edgy. 

I have spent 2 days trying to figure this wireless problem. Hopefully Edgy+1 will do a better job and the driver in the kernel be more mature. I am not sure where I read it but it does seem that for some earlier version of kernel 2.6.17 this card was working. After an Ubuntu upgrade some people claimed that the card was unable to connect to the wireless networks. 

I think that the mayor issue in my case is that I can not optain an IP address from the wireless router. It seems to detect the wireless router but it times out when it tries to stablish the protocol.

---

### Post by motrennoc on 2006-10-22
Bicchi,
I figured it out!
So, I finally figured out why my wireless network "disappeared" from network manager.

I found this in _Ubuntu Hacks_ by Jonathan Oxer, Kyle Rankin and Bill Childers.

In Hack #42
"NetworkManager cannot manage any cards that have entries in */etc/network/interfaces*. If you've added your network card to that file, make sure you remove it before you start working with Network manager."

I removed this from the /etc/network/interfaces file

"auto eth1
iface eth1 inet dhcp
wireless-essid home"

It worked like a charm, well almost, I'm still struggling with the WEP encryption. But, the wireless networks available are listed by network manager and the "enable wireless" selection is back.

---

### Post by jrz on 2006-10-22
This is becoming very frustrating, I'm beginning to believe there is no one answer to the same problem and not sure what to do. We've tried several different procedures to try and get our wireless working, and I'm still not even sure that the card is recognized by the system. The wired LAN works, and it appears there is an entry for a modem, but I see no evidence of a wireless other than opening the cover where the card is plugged in. 
If someone here has a Compaq Presario V3042AU or any 3000 series notebook and has successfully got the wireless to work we would appreciate it they would provide instructions as to what proceedures they used. I have spent days searching and reading and then trying different suggestions and none have produced any results we can view.
We really wish to stick with Linux, but it is much more difficult than Windows to get things working properly. We have a working system, but have numerous things that we would like to make easier to use, and currently the wireless is keeping us from making progress on the other items. Any help would be greatly appreciated, or should we be asking questions in another Forum??
Getting the wireless to work would be a great confidence builder.
Thanks

---

### Post by serlex on 2006-10-22
not big deal but, network manager doesnt show up for me!

i installed it and it shows up on startup programs too, but no manager by the clock, any ideas?

---

### Post by crimesaucer on 2006-10-22
Thanks for your guide.

---

### Post by Synikk on 2006-10-23
These instructions worked perfectly with my BCM4306 in my Dell Inspiron 5100 on 6.06. Thanks!

---

### Post by raz33th on 2006-10-23
> **jrz said:**
> 
If someone here has a Compaq Presario V3042AU or any 3000 series notebook and has successfully got the wireless to work we would appreciate it they would provide instructions as to what proceedures they used. I have spent days searching and reading and then trying different suggestions and none have produced any results we can view.


Hey.. 

I have a Compaq Presario V3029AU (AMD Turion X2). I hit this thread after installing Ubuntu Dapper (amd64) with my wired internet, followed the steps and after the reboot it worked. (I doubt whether Windows will have a smoother insallation than this. kudos nickm. a great how to.. great work bro. ty.

---

### Post by vagayan on 2006-10-23
Excellent guide. I am new to Ubuntu (but not to Linux in general) and finding this forum a great source of information.

This procedure worked for me (I have a wireless Linksys PCI Adapter WMP54GS which uses Broadcom 4306 chipset. After installing the drivers, the eth1 interface would come alive and I could scan the network, but it would not connect to my network. I was fighting with it for a couple of days. I am using WEP and my router (Linksys WRT54GS) had its Authentication Type set to Shared Key. When I changed it to Auto (I am still only allowing encrypted connections, but simply changed the Authentication Type) it started working. I verified it twice, if I change the Authentication Type back to Shared Key, Gnome Network Manager wasn't able to connect to my router. Well, it is working now, but I wonder if anyone has an explanation. My other box (Windows 2000) and a wireless laptop (IBM ThinkPad T42 with Windows XP) had no issues connecting to my network with the Shared Key setting on my router, but Ubuntu wouldn't.

---

### Post by hangfire on 2006-10-24
Thanks for the guide, but regretfully I must report that it not only does not work for me, it causes Ubuntu to hang soon after startup.

I reinstalled clean and immediately did this HowTo before running any updates or doing any customizations- literally the first thing I did after the machine booted up on the fresh install- same thing.

Here is a lspci:

```

0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
0000:02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)

```

Here's some log messages, unfortunately the kernel fault stack dump didn't log anywhere (that I could find).

```

messages:Oct 23 21:11:09 irad-lt kernel: [4294689.875000] eth1: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:aa:74:df
messages:Oct 23 21:11:09 irad-lt kernel: [4294692.756000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1608
messages:Oct 23 21:11:09 irad-lt kernel: [4294692.756000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1611
messages:Oct 23 21:11:09 irad-lt kernel: [4294692.757000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1651
messages:Oct 23 21:11:09 irad-lt kernel: [4294692.766000] bcm43xx: TODO: Incomplete code in bcm43xx_phy_inita() at drivers/net/wireless/bcm43xx/bcm43xx_phy.c:577
messages:Oct 23 21:11:09 irad-lt kernel: [4294692.766000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1608
messages:Oct 23 21:11:09 irad-lt kernel: [4294692.766000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1611
messages:Oct 23 21:11:09 irad-lt kernel: [4294692.766000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1651
messages:Oct 23 21:11:09 irad-lt kernel: [4294692.766000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_set_txpower_a() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1802
messages:Oct 23 21:11:09 irad-lt kernel: [4294692.776000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
messages:Oct 23 21:11:09 irad-lt kernel: [4294692.776000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
messages:Oct 24 13:03:35 irad-lt kernel: [4294689.306000] bcm43xx driver
messages:Oct 24 13:03:35 irad-lt kernel: [4294689.775000] eth1: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:aa:74:df
messages:Oct 24 13:03:35 irad-lt kernel: [4294691.320000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1608
messages:Oct 24 13:03:35 irad-lt kernel: [4294691.320000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1611
messages:Oct 24 13:03:35 irad-lt kernel: [4294691.320000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1651
messages:Oct 24 13:03:35 irad-lt kernel: [4294691.329000] bcm43xx: TODO: Incomplete code in bcm43xx_phy_inita() at drivers/net/wireless/bcm43xx/bcm43xx_phy.c:577
messages:Oct 24 13:03:35 irad-lt kernel: [4294691.329000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1608
messages:Oct 24 13:03:35 irad-lt kernel: [4294691.329000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1611
messages:Oct 24 13:03:35 irad-lt kernel: [4294691.329000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1651
messages:Oct 24 13:03:35 irad-lt kernel: [4294691.329000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_set_txpower_a() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1802
messages:Oct 24 13:03:35 irad-lt kernel: [4294691.340000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
messages:Oct 24 13:03:35 irad-lt kernel: [4294691.340000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
messages:Oct 24 19:06:13 irad-lt kernel: [4294689.190000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:aa:74:df
messages:Oct 24 19:06:13 irad-lt kernel: [4294689.361000] bcm43xx driver
messages:Oct 24 17:04:52 irad-lt kernel: [17179594.148000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:aa:74:df
messages:Oct 24 17:04:52 irad-lt kernel: [17179594.380000] bcm43xx driver
syslog:Oct 24 17:04:52 irad-lt kernel: [17179594.148000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:aa:74:df
syslog:Oct 24 17:04:52 irad-lt kernel: [17179594.380000] bcm43xx driver
syslog:Oct 24 17:04:52 irad-lt kernel: [17179595.672000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
syslog:Oct 24 17:04:52 irad-lt kernel: [17179595.672000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294689.673000] bcm43xx driver
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294689.875000] eth1: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:aa:74:df
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294692.756000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1608
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294692.756000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1611
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294692.757000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1651
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294692.766000] bcm43xx: TODO: Incomplete code in bcm43xx_phy_inita() at drivers/net/wireless/bcm43xx/bcm43xx_phy.c:577
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294692.766000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1608
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294692.766000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1611
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294692.766000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1651
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294692.766000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_set_txpower_a() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1802
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294692.776000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
syslog.0:Oct 23 21:11:09 irad-lt kernel: [4294692.776000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294689.306000] bcm43xx driver
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294689.775000] eth1: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:aa:74:df
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294691.320000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1608
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294691.320000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1611
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294691.320000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1651
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294691.329000] bcm43xx: TODO: Incomplete code in bcm43xx_phy_inita() at drivers/net/wireless/bcm43xx/bcm43xx_phy.c:577
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294691.329000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1608
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294691.329000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1611
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294691.329000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_selectchannel() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1651
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294691.329000] bcm43xx: TODO: Incomplete code in bcm43xx_radio_set_txpower_a() at drivers/net/wireless/bcm43xx/bcm43xx_radio.c:1802
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294691.340000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
syslog.0:Oct 24 13:03:35 irad-lt kernel: [4294691.340000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
syslog.0:Oct 24 19:06:13 irad-lt kernel: [4294689.190000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:aa:74:df
syslog.0:Oct 24 19:06:13 irad-lt kernel: [4294689.361000] bcm43xx driver
syslog.0:Oct 24 19:06:13 irad-lt kernel: [4294691.153000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
syslog.0:Oct 24 19:06:13 irad-lt kernel: [4294691.157000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
syslog.0:Oct 24 19:06:21 irad-lt firmware_helper[4745]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
syslog.0:Oct 24 19:06:21 irad-lt kernel: [4294717.084000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
syslog.0:Oct 24 19:06:24 irad-lt NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'bcm43xx'.
syslog.0:Oct 24 19:06:24 irad-lt firmware_helper[5001]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
syslog.0:Oct 24 19:06:24 irad-lt kernel: [4294719.970000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
syslog.0:Oct 24 15:06:55 irad-lt firmware_helper[5186]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
syslog.0:Oct 24 15:06:55 irad-lt kernel: [4294750.797000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
syslog.0:Oct 24 15:07:17 irad-lt firmware_helper[5211]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
syslog.0:Oct 24 15:07:17 irad-lt kernel: [4294773.627000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
syslog.0:Oct 24 15:07:40 irad-lt firmware_helper[5247]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
syslog.0:Oct 24 15:07:40 irad-lt kernel: [4294796.477000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.

```

---

### Post by ZombiekE on 2006-10-25
It worked for me in Dapper. However now I need to use wifi without the X server and I can't configure it. I tried to retry the step that the guide recommends when one updates the Kernel (I suppose it was updated with Edgy Eft). However it doesn't work... in the command there is some `uname -r` that doesn't work. Is it supposed to be something else? If I delete that part of the command it gets better, but still I can't go online.

How can I configure/activate/use my Broadcom in Edge Efty without X? :(

Please help.

---

### Post by henkstubbe on 2006-10-25
Thanks, that worked with Edgy on a Dell Latitude D600 laptop!

In Dapper ndiswrapper did the work without problems. However, after upgrading to Edgy I ran into problems.

With ndiswrapper I got this error: FATAL: Could not open &#8216;/lib/modules/2.6.15-27-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko&#8217;: No such file or directory

Then I followed this howto, but no wireless networks were recognized after the reboot.

I had to clean up /etc/network/interfaces first. 

So I uncommented all interfaces (in my case only wlan0), except lo and eth0. The result:

```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet dhcp

# wireless
# iface wlan0 inet dhcp
# wireless-eddid <myessid>
# wireless-key <mykey>

```

Then I did
```

sudo /etc/init.d/networking restart

```
and voila, I was able to connect to my wireless connection.

---

### Post by tech2k5 on 2006-10-25
> **xiota said:**
> [COLOR="Gray"]Some of the comments people have typed seem like there is a way to get a list of available ESSIDs.  Is this available in Network Manager somehow, already installed with Ubuntu, or something extra that would need to be installed?  If such a feature were available, would clicking on it automatically configure wireless for connection to the selected access point?  (If that were the case, then it might be a solution to the problem I describe below.)[/COLOR]

I have a Linksys WMP54GS...  Following the steps from this thread, I got the card to work in 802.11b mode, but not in 802.11g mode.  Does anyone know how to get G mode working?

[INDENT]The card functioned properly, most of the time, in Windows 2000.  The drivers glitched or crashed occassionally, which required a reboot.

Signal strength is definitely not a problem.

I tried both the bcmwl5.sys file linked in the original instructions as well as a couple versions provided by Linksys.  The Linksys files gave an error about missing microcode, but with a comment that the missing microcode is not currently used by the drivers.[/INDENT]

I've searched these forums and elsewhere, but have not encountered anything helpful so far.  I'm about a stone's throw away from giving up and trying ndiswrapper.

Thanks for any help anyone can provide.

[COLOR="DarkRed"]Someone typed a comment elsewhere saying that G-mode seems to be not supported at the moment.  People whose cards will detect, but not connect, to a wireless network might be trying to connect to G-only networks.  So some of us may be stuck with ndiswrapper for now.[/COLOR]


How did you get your WMP54GS to work under Ubuntu? Are you running 6.06 LTS Drapper? I cant get this card to work under drapper, I would be just happy if I can run it in 802.11 b mode :-(

[http://ubuntuforums.org/showthread.php?p=1663001#post1663001](http://ubuntuforums.org/showthread.php?p=1663001#post1663001)

---

### Post by ZombiekE on 2006-10-25
Ok, I've solved this... it seems Ubuntu needs "sudo modprobe bcm43xx" every time it starts.

---

### Post by lyceum on 2006-10-25
For those with 4311, I re-installed edgy & tried ndiswrapper (yes I know I did not need to and it was dumb, but I was willing to try anything at that point) and my WiFi was gone. Edgy could no longer find it. Do not try that page. If you can't get this to work, I would recomend you get a new card.

---

### Post by llimllib on 2006-10-26
So, it kind of works for me. I can connect and use the internet at first (edgy eft, same card as you) but the connection zonks out every 2 minutes or so. Sometimes for 10 seconds, sometimes for 10 minutes.

It makes the system unusable.

Anybody have any suggestions?

---

### Post by LinLenLap on 2006-10-27
I just did a clean install of Edgy on a Lenovo 3000 c100. Under 6.06 lspci showed me having a broadcom 4318 or 4311...I can't recall which. Now it shows up as a Broadcom dell 1420 or something like that. Very odd.

Anyway, this guide works better than ever for me!

From a clean install I installed fwcutter, then dowloaded the wlapsto.o file, then copied the firmware to lib/firmware and the kernel directory. Then rebooted. I then booted up, entered my password, and Bam!

I mean, I'm using WAP-PSK and no problems. Amazing. I'd vote again, but apparently it remembers me having success with this under dapper.

Best,

LLL

---

### Post by baluchi on 2006-10-27
Hello everyone,

I have a PC with Linksys WMP54G PCI card and a laptop with a Linksys WPC54G PCMCIA card. They both use the Broadcom 4306 chipset.

Following the tutorial on Ubuntu 6.06, they both worked fine using the **wl_apsta.o** driver provided, however [COLOR="Red"]after updating[/COLOR] Ubuntu (**apt-get upgrade**), they both stopped working.

My router used the WEP 128bit encryption.

On my PC (Gnome), I had to redo the whole tutorial plus the following to get it to work:
```
sudo modprobe bcm43xx
```

On my laptop (server mode - ie terminal only) I had to edit **/etc/network/interfaces** manually to look like this:
```
auto lo
iface lo inet loopback

iface eth0 inet static
        wireless-essid <myessid>
        address 192.168.2.21
        netmask 255.255.255.0
        gateway 192.168.2.1
        wireless-key <mykey>
auto eth0
```
For DHCP, it can just look like this:
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0
```

However, after the upgrade, I started getting this error message ([COLOR="MediumTurquoise"]James[/COLOR], are you listenning? ;)):
```
ADDRCONF(NETDEV_UP) : eth0: link is not ready
```
So I had to enter:
```
sudo iwconfig eth0 ap any
```
every time I boot.

Instead of re-typing these commands on every boot, I edited the **/etc/rc.local** to include the commands (without sudo) before the line where it says **exit 0**.

In both cases, I also added:
```
iwconfig eth0 rate 54M
```
to the same file so that the higher speed is used.

I hope this helps some, but I recommend anyone posting his problem to include the outputs of:
[B]sudo iwconfig
sudo iwconfig
sudo iwlist scan
cat /etc/network/interfaces[/B]
plus any error message he encounters if related to his problem.

Thank you everyone for your help. :)

---

### Post by ZombiekE on 2006-10-27
I have a Broadcom 4318 in Edgy Eft. I need to write "sudo modprobe bcm43xx" every time I start Ubuntu. After a few hours of use (sometimes not many), I have to do it again, but sometimes when I re-do it it doesn't work unless I reboot the laptop. What can I do?

Is anybody else having this issue?

---

### Post by benbruscella on 2006-10-29
With Edgy, my wireless connection seems to go down after a while.

Then, when I try to reboot, I get:

bcm43xx: Controller RESET (Tx Timeout)

And this means I cannot shutdown/reboot without a power down.

Anyone else seeing this?


```

benb@zigzag:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:24:0A:34:F5
                    ESSID:"home"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-71 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 348ms ago
          Cell 02 - Address: 00:14:6C:D0:27:38
                    ESSID:"MAGGIE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-30 dBm  
                    Extra: Last beacon: 4ms ago

sit0      Interface doesn't support scanning.

```

```

benb@zigzag:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

---

### Post by OneSeventeen on 2006-10-30
I tried the original instructions to a T, then when that didn't work, I tried using the wireless drivers I used in the past to get it to work with Dapper.

Still no luck with Edgy.

Here's the requested output:```
oneseventeen@tigershark:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Calvary"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

oneseventeen@tigershark:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

oneseventeen@tigershark:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

iface eth1 inet dhcp
wireless-essid Calvary
wireless-key s:

auto eth1
```

Any tips?  Or should I go the ndiswrapper route, or possibly downgrade to Dapper?

This is my business laptop and I can't believe I was so eager to upgrade that I didn't give it time and check into the potential issues... I just remember using fwcutter to get wireless working in dapper and it was so easy. :(

---

### Post by OneSeventeen on 2006-10-30
I followed [these instructions](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper) and just like this thread mentioned, I installed the fwcutter script, but after extracting the firmware from the file linked to in this thread, and the file I used last time to get it to work with ndiswrapper, I wound up just running the fwcutter script:
```
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```
I had to plug into a wired network for it to download the .so file and extract the firmware for me.

My wireless adapter still didn't work, so I manually edited the interfaces file to tell the interface to operate at 11M```
wireless-rate 11M
```

I disabled all wireless networking whether that be from network-manager-gnome or network configuration, then rebooted, and it still didn't work.

So, I wound up just manually typing in ```
sudo iwconfig eth1 essid Calvary
``` and it actually connected!

If there are any config files or command line argument results I can attach here to help anyone else with the issue, just ask and I'll post it.

(I'm now setting up a webserver on my laptop for development purposes over the now-working wireless!!!  only 2 minutes remaining :D )

---

### Post by ag65151 on 2006-10-30
Worked like a champ on my HP pavilion ze5500. I came over to Ubuntu from FC. I was tired of banging my head against a brick wall to get my hw working. Thank you for this how-to.

---

### Post by Tiede on 2006-10-30
I followed this to get my broadcom 4318 card to work in dapper (and it worked purrrfectly). Now that I've upgraded to edgy, I'm noticing some odd behaviors: sometimes, it works, well... But then out of the blue, it stops...
And reboot as I may, it still doesn't work... Then after a while, everything works fine again... Is someone else noticing this?

P.S: I did try (many times to no avail ```
sudo rmmod bcm43xx
sudo modprobe bcm43xx
```

---

### Post by Sokraates on 2006-10-31
So I take, that ubuntu's default driver work for you. That's strange, since the bcm4318 is not supported (at least not rev2). You get the exact typeof your chip  by typing "lspci" in a console. At least on my HP nx6110 it would only work with ndiswrapper.

You might also want to take a look at [this]("http://www.ubuntuforums.org/showthread.php?t=197102") thread and maybe try the script, though in my case I needed to install both ndiwrapper-utils1.1 and ndiwrapper-utils1.8. The script also produces a nice log-file.

The steps performed by the script are explained [here]("http://www.ubuntuforums.org/showthread.php?t=285809"), if you prefer to do everything manually (it won't hurt for troubleshooting).

---

### Post by Sparticuz on 2006-10-31
I'm having an interesting problem. I've got everything installed right (using ndiswrapper, the firmware thing didn't work). It's detecting my card, the 4311, and it's even getting an IP address from the router, but it's not getting on the internet. I have done this on multiple different AP's too, but still no internet. I do have to type my ESSID in, it's not scanning in network config, or network manager, but it is in wifi-radar.

---

### Post by 4KvRMU7Nnv on 2006-10-31
AHHHHHH!!! WTH!?!?  I have done this exact procedure like 8 times after I proceded to kill ubuntu each time.  I was doing it this time and it doesn't work?!!!?!??!?  Now it says that my driver is old?
wtf?! it never was before! in fact i have installed it earlier today before i killed linux again and it worked! WTF! sigh...ill instll ubuntu again......but it takes like 30 minutes!!!!!!! GGRRRRRRRRR.

---

### Post by blackest_knight on 2006-11-01
Hi 
I just installed Edgy EFT and I have an HP Compaq NX6110 which has the BroadCom BCM4318 Version2 Chipset. 

It's working fine and it was very quick and easy to install, no NDISWrapper needed but you do need to have had it working in Dapper natively.

So you need to backup some things from Dapper before you install Edgy. 

Edgy has a file for broadcom chipsets ending in .Ko  this is the operating systems side of the Driver, this will not work because it needs the cards firmware (from the manufacturer to talk to) 

basically the driver is in two halves one half provided by the os is the .ko file the other half is provided by the wireless card manufacturer in 
Dapper you used BcmCutter to cut the windows driver into bits

well Edgy needs those bits. 
/lib/firmware/ has the bits you need inside that folder is bits of wireless  driver and a number of folders (your linux kernel and supporting files live in them) ignore the folders just get those individual files out of there on your dapper install and put them somewhere safe. 
install edgy and then put those files back into edgys /lib/firmware/
and reboot.

heres an easy way 
open two terminals and
**sudo nautilus** 
in each of them 

that will bring up two file browser windows with root access 
navigate to your saved firmware  folder and to your edgy firmware folder 
copy the files from savedfolder to edgy lib/firmware/ folder 

ok reboot 
now open a terminal window 
type 
$**iwconfig** 
you should get 

lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Myrouter"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:11:50:45:85:35   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr: off   Fragment thr: off
          Link Quality=56/100  Signal level=-51 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

good 
now lets get a lease 

$ [B]sudo dhclient
[/B]
Password:
There is already a pid file /var/run/dhclient.pid with pid 4848
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit ,,,

Listening on LPF/eth0/ mac address
Sending on   LPF/eth0/ mac address
Listening on LPF/eth1/ forum thinks 
Sending on   LPF/eth1/ mac addresses are smileys
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.x.1
bound to 192.168.x.2 -- renewal in 985072504 seconds.
$ 

bingo connected not done anything else except come on here and tell you how i did it.

I created some files on my laptop they might be useful if you put them in your lib/firmware folder I think they are ok

I use an open access point with mac address filtering you probably want more security than that.

I don't know why but I find when changing access points it is difficult to associate with a new access point, however if i boot windows and get a lease then rebooting into ubuntu there is no problem at all. (I don't have any evidence other than this seems to work)

---

### Post by blackest_knight on 2006-11-01
I've been playing with the data rates for the wireless card 
sudo iwconfig eth1 rate 24M auto
 works for me with no losses 
sudo iwconfig eth1 rate 54M auto
and there are lots of losses 

sudo iwconfig eth1 rate 48M auto

seemed ok but the internet seemed slow 
there are a number of parameters you can try with iwconfig
but it looks like 18DBm is the maximum you can set the txpower 
(you can lower it)

anyone able to do iwconfig on dapper and see what things are set to?

---

### Post by zds on 2006-11-01
Worked for me on my Compaq V2000Z AMD64 Turion with Broadcom 4318 using additional instructions at 

[http://ubuntuforums.org/showpost.php...4&postcount=43](http://ubuntuforums.org/showpost.php...4&postcount=43)

Thanks!

---

### Post by rossjamesparker on 2006-11-03
Looks like a good howto. Unfortunately this is not so much help for me though.... my cheapy conexant wireless card doesn't show in Ubuntu :( I guess it's down to the computer shop for me.

---

### Post by eems01 on 2006-11-04
> **benbruscella said:**
> With Edgy, my wireless connection seems to go down after a while.

Then, when I try to reboot, I get:

bcm43xx: Controller RESET (Tx Timeout)

And this means I cannot shutdown/reboot without a power down.

Anyone else seeing this?


```

benb@zigzag:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:24:0A:34:F5
                    ESSID:"home"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-71 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 348ms ago
          Cell 02 - Address: 00:14:6C:D0:27:38
                    ESSID:"MAGGIE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-30 dBm  
                    Extra: Last beacon: 4ms ago

sit0      Interface doesn't support scanning.

```

```

benb@zigzag:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Also seeing this issue on a dapper to edgy upgrade.  Never a problem on dapper.  I think edgy was ok for a few days after upgrading and then the past two days I have started seeing this.  I've run all the updates since upgrade and maybe somehow they have made this issue?

---

### Post by eems01 on 2006-11-04
> **benbruscella said:**
> With Edgy, my wireless connection seems to go down after a while.

Then, when I try to reboot, I get:

bcm43xx: Controller RESET (Tx Timeout)

And this means I cannot shutdown/reboot without a power down.

Anyone else seeing this?


```

benb@zigzag:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:24:0A:34:F5
                    ESSID:"home"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-71 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 348ms ago
          Cell 02 - Address: 00:14:6C:D0:27:38
                    ESSID:"MAGGIE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-30 dBm  
                    Extra: Last beacon: 4ms ago

sit0      Interface doesn't support scanning.

```

```

benb@zigzag:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
 
Believe I just fixed this issue by re-extracting the firmware to _both_ the /lib/firmware directory and the /lib/firmware/2.6.17-10-386 
directory.  Logs so far have not shown this error again.

Edit: It died again.

---

### Post by neversfelde on 2006-11-06
Thank you for this fantastic howto. I think it has worked for me. The wlan interface (it's a broadcom with 4311 chipset) seems to work. I can scan for networks and I get a dhcp or static connection to my wlan network. Even WPA is really working.

The only problem is that I can't see any websites in my browsers. Ping, apt-get update is no problem, but kopete is also not working with wlan.
Might this be a problem with the broadcom driver?

Thanks for reading.

---

### Post by jon_herr on 2006-11-07
I'm seeing your problem with Edgy...

"bcm43xx: Controller RESET (TX timeout)"

When it happens my keyboard is frozen - my mouse works - but sometimes the only way to shutdown or reboot is a hard reset.

Menus respond but don't do anything.

I'm trying a different kernel.

Jon

---

### Post by neversfelde on 2006-11-08
I'm using the Generic-Kernel, but I also tried some tests with the i386. The same problem.

---

### Post by jon_herr on 2006-11-08
My problem continues...

I've read something about this being a Kernel issue in Red Hat when some people switched to SMP version of Kernel.

I'm not using a SMP version as far as I know...  just whatever was installed by Edgy.  This is a single core Athlon 64.

Jon

---

### Post by greensmoke on 2006-11-09
Thank you nickm!!!  I've been trying to get this card to work for days!  Got a Motorola wn825g pc card and could NOT get it to work even with all the various other walkthroughs I tried and the reinstalls of the ubuntu edgy alternate cd when the walkthroughs screwed up my system.  I had basically given up, since I had no way to connect to the internet besides this wireless card as I have only a phone line jack in my laptop...that's it.  I have usb ports on a pc card but they wouldn't let the usb2ethernet adapter work, so I was pretty much screwed.  I was downloading the ndiswrapper util on a usb drive at an internet cafe and transferring it to ubuntu and back and forth and back and forth with everything to try to get it to work.  My time was almost up at the cafe but I happened to run into your walkthrough.  I saved it on the usb, and since it's two in the morning, I ran back to my place, gave it a try, and said..."If it doesn't work, I'm going back to windoze..."   so I type in my router's address and IT WORKS!!  

Thanks nickm, this deserves to be put in a more prominent area as it is a major solution for a lot of people.

greenxmoke

---

### Post by neversfelde on 2006-11-09
> 
 I'm not using a SMP version as far as I know... just whatever was installed by Edgy.

I`ve tried with an smp Kernel and without. Now I`m using ndiswrapper at the moment, but I'm trying for the future.

---

### Post by jon_herr on 2006-11-09
Can you use WPA encryption with ndiswrapper?

That's the whole reason I'm using 'network manager'...

---

### Post by neversfelde on 2006-11-09
With ndiswrapper everything, even WPA encryption, works fine.

---

### Post by sakko on 2006-11-09
Hey guys,

Just wanted to thank blackest_knight, and everyone else on this forum for the immense amount of info here.

blackest_knight had posted a zip file with the firmware for my card with instructions to put it in the /lib/firmware folder, which, after doing, my "sudo dhclient eth1" command fired up my wifi card no problem!

Before I was getting something like SSCIOFFLAGS: No file or directory found

After adding the firmware files I get:

> Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:a5:48:d5:7c
Sending on   LPF/eth1/00:14:a5:48:d5:7c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Just FYI I am not currently near an AP so that's why it didn't find one. But my Wifi light is ON for the first time and I am sure it will work when I get home! If nothing else I am one HUGE step closer... thank you thank you thank you!

---

### Post by tommy1987 on 2006-11-10
worked excellently, thank you so much! I even had the dreaded: 

Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller (rev 02)

Thanks again,

---

### Post by ZombiekE on 2006-11-10
> **Tiede said:**
> I followed this to get my broadcom 4318 card to work in dapper (and it worked purrrfectly). Now that I've upgraded to edgy, I'm noticing some odd behaviors: sometimes, it works, well... But then out of the blue, it stops...
And reboot as I may, it still doesn't work... Then after a while, everything works fine again... Is someone else noticing this?

P.S: I did try (many times to no avail ```
sudo rmmod bcm43xx
sudo modprobe bcm43xx
```
I think we have the same issue with our Broadcom cards.

---

### Post by Tiede on 2006-11-10
Is yours still doing it? Mine is showing improvement: it always connects though every once in a while it drops and I have to fire up wifi-radar to reconnect...

---

### Post by pastorjay on 2006-11-10
Guys, I am putting this in as many threads about the broadcomm as I can.  The new nvidia drivers cause some kind of comflict with the broadcom wireless cards.  Not sure what happens, but as soon as I unloaded the nvidia drivers, and went with the default drivers the wireless function all of a sudden is working perfectly, and not droppiing out anymore.  Just a heads up!  And here is hoping that nvidia can fix this real quick, as you cannot use any 3d functions of the card, which means no Beryl and the sorts.

---

### Post by Sparticuz on 2006-11-11
I've got the firmware installed and almost working...I can see all the networks in wifi-radar, but I can't get an IP from any of them.](*,)

---

### Post by eems01 on 2006-11-11
> **jon_herr said:**
> I'm seeing your problem with Edgy...

"bcm43xx: Controller RESET (TX timeout)"

When it happens my keyboard is frozen - my mouse works - but sometimes the only way to shutdown or reboot is a hard reset.

Menus respond but don't do anything.

I'm trying a different kernel.

Jon

This morning I installed the 7 avahi updates which mentioned fixing a crash.  I figured this may solve this problem.  Instead, network manager will not connect anymore after entering the key passphrase.  The first light goes green and then a wireless connection screen pops up.  After entering the correct credentials in and accepting network manager just stops.

Edit: A few reboots later keyring prompted for password and network manager connected successfully. Lets see if things eventually crash again?

---

### Post by PartisanEntity on 2006-11-11
Hi, I have followed this tutorial but no luck, although the network manager shows up at start up, the only option I have is to enable networking (it does not say wireless networking).

My card is an Asus card with a bcm4306 chip.

---

### Post by dread0 on 2006-11-11
I have exactly the configuration mentioned in the HOW TO.  I followed the steps exactly but when rebooting the the boot hangs and only recovers when I delete the extracted firmware from the kernel.  nothing seems to work with broadcom and wireless and linux.

---

### Post by hoegaandit on 2006-11-12
Thanks for the help, it took me a couple of days to get this working. I have a Broadcom 4306 and it works most of the time, but sometimes it just drops the connection. I try doing

modprobe bcm43xx 

but that only works sometimes. A reboot seems to fix it most of the time.
Anyone know how to fix this?

---

### Post by greensmoke on 2006-11-13
do the modrobe bcm43xx command and then reboot.  It should work after that.  Recheck your essid and wep also.  Reset your internet connection (router/modem) too as that seems to have helped a few times.  It's just a bit tricky.

---

### Post by Novek on 2006-11-15
Thanks very much for this howto... tried many ndis howto's and didn'y have high ekspects for this nativ driver thing... but now i'm connected:D

---

### Post by deevus on 2006-11-16
Omg it works finally!! Ive been trying for so long but to no avail with dapper and now edgy, but now it works!

Im using Broadcom 4306 on Apple g4 Powerbook. Did as instructed up to step 4b then entered SSID and enabled DHCP, and voila!

---

### Post by homerj742 on 2006-11-19
man this WAS working for me, and no suddenly I cannot see any of my wireless networks in "wifi-radar".

I haven't changed anything.

I followed this guide, however I am using Xubuntu on my laptop. and Wifi-Radar as my wireless application. 

The card I'm using is a Linksys WPC54GS.

Any Ideas as to why this would suddnely stop working???

---

### Post by bilange on 2006-11-19
This howto helped me enable my BCM4318 card. At the time of writing this, I didnt try the card in a real wireless network so I dont know if I will get the "I dont get an IP" bug, but lets cross fingers ;)

**Machine:** Acer Aspire 5044 ("5040 series"), using added-in Broadcom 4318, listed by lspci as "*06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)*"

Used original poster's [wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o) to extract the firmware, and copied it twice, in /lib/firmware AND /lib/firmware/**kernel_version**.

Added "bcm43xx" in /etc/modules, and also added ndiswrapper in /etc/modprobe.d/blacklist so it wouldnt conflict.

---

### Post by g33k on 2006-11-19
WOW....3 days of struggling, but it works now.  Glad I found this post.  THANK!

---

### Post by pastorjay on 2006-11-19
> **homerj742 said:**
> man this WAS working for me, and no suddenly I cannot see any of my wireless networks in "wifi-radar".

I haven't changed anything.

I followed this guide, however I am using Xubuntu on my laptop. and Wifi-Radar as my wireless application. 

The card I'm using is a Linksys WPC54GS.

Any Ideas as to why this would suddnely stop working???

Did you happen to update Nvidia drivers?  There is a known issue with the new Nvidia drivers and the broadcomm chip having IRQ problems.

PJ

---

### Post by Tiede on 2006-11-20
Here is the summary of my problems with the bcm43xx driver... (At least I have to say it's working... ;) )
Card is working intermittently. Also observed, the bcm43xx driver will only connect when a network's signal is "very good" i.e 5 full bars. Otherwise, connection stalls and never connects.
Output of lspci | grep Broadcom:
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Tried Ndiswrapper. Did not seem to work... Installed wrong??? - I do not wanna have to install it again > I could try with automatix, but I wanna see if the native will work instead, since I do not wanna have to reinstall Ndiswrapper after every upgrade...

Is anyone else having those issues

---

### Post by stuh84 on 2006-11-20
Took a while of messing around but finally got it working. Using a 4318 Airforce One type wireless, had given up with NDISWrapper because of the inability to get an IP Address, no matter what I tried.

Had quite a few problems with this one too, was about to give up. It would see the AP, and got an IP Address, but no luck getting anything else. I commented out the Wireless in /etc/network/interfaces and Network-Manager finally took over, went slightly dodgy and froze at first, gave it one more try, and it worked fine, I now have the little blue bars. This means I'll actually start using Ubuntu on this laptop now (not deleting XP by a long shot, but finally I have an alternative).

Thanks for this guide, its great.

---

### Post by homerj742 on 2006-11-20
I'm going to try editing my network interfaces file first!(as I don't believe my old sony laptop has Nvidia components in it) Thank you for the response Pastorjay

---

### Post by svenforum on 2006-11-20
(Sorry for the bad English - Working on it)

I once had a succes using ndiswrapper, but after reboot it failed to work.
The solution posted here also worked, but again after reboot it failed to connect to an AP. 

I solved it by creating two scripts.
The vital one looks like this:
> 
bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o

I run this one each time I have to shutdown or reboot.

The other script looks like this:
> 
iwconfig eth1 essid "blablabla"
iwlist eth1 scan > scan.log
grep Cell scan.log
grep ESSID scan.log
iwconfig eth1 mode Managed
iwconfig eth1 essid "blablabla"
iwconfig eth1 key restricted s:password
iwconfig eth1 essid "blablabla"
iwconfig eth1 | tail -n 9
dhclient eth1

This one is run to connect to my Wlan at home.

This works, but it ain't pretty.
Does someone see a more beautiful solution?

If not, is there a way to execute a script automatically at startup and shutdown, so I don't have to do it manually all the time?

Thanks in advance.
Sven

My specs:
Dual boot Windows XP / Ubuntu 6.06
Edgy 
Linux flaptop 2.6.15-27-386
0000:02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
Actually it's a RavoTek card.

---

### Post by svenforum on 2006-11-20
The first script isn't necessary.
In the second script (called getwlan), I added a line above the rest:
> kill `pgrep dhcl`
(BTW: I run the scripts as root, forgot to mention it)

The procedure is as follows:
Eject the card & insert the card
./getwlan
> 
Listening on LPF/eth1/00:90:96:af:f9:8a
Sending on   LPF/eth1/00:90:96:af:f9:8a
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67

(It will not get past DHCPREQUEST.)
Repeat procedure and it works!
> 
Listening on LPF/eth1/00:90:96:af:f9:8a
Sending on   LPF/eth1/00:90:96:af:f9:8a
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.123.254
bound to 192.168.123.153 -- renewal in 3459667 seconds.


It's always after the second try that it works. How come, I wonder. Does somebody has an idea?

Thanks in advance,
Sven

---

### Post by helmerizer on 2006-11-21
Hello everyone.

I have been trying out a couple of different How To:s in order to get my BCM4306 802.11b/g Wireless to work. At first I installed Ndiswrapper and dled and installed the proper driver for my card in terminal: 
```

sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
```

And then:

```
:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

```
After this I proceeded according to the recipe and encountered something weird:
```

sudo modprobe ndiswrapper
Password:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument 
```
I didn't know if that was important or not so I rebooted and opened Network Settings to configure the new wlan0 connection, only to find that it wasn't there. I could only find the same old eth1 (my wired connection is eth0) as before, which isn't working.
I did the same thing all over again with the graphical Ndisgtk, with the exact same result. Since then I have tried a few other (quite similar) methods, but to no avail.
It seems to me that the driver is in place but something keeps the kernel from loading it because it behaves like I haven't changed a thing.
I would be most grateful if anyone could shed some light on this.

I run a compaq nx6110 (dual boot winXP / Ubuntu 6.10)

---

### Post by thomastheobscure on 2006-11-24
> **nickm said:**
> ****In my edgy knot 2 testing I found that edgy users can stop the guide after competing stage 4 or 4b as it 'just works' with out network-manager if you fill in the SSID and set the wireless device to DHCP in the "networking" option under System > Administration****


This Should work with Apple hardware as well as PC's.

How to get a wireless card working in Ubuntu 6.06 or 6.10) with a Broadcom chipset 43xx


**This guide assumes 2 things:**
[LIST]
[*]Wired Internet access on the machine with the wireless card on it, in my case i had a 10/100 LAN card that i was using as i couldn't get wireless to work which gave me full access to internet - although it is possible to put the files required on a CD and then add that CD as a repo in synaptic on the wireless machine, how to do this is not covered here, you could even extract the firmware on a different PC and place it in the right location on a remote PC using a CD/Pen drive taking a .deb of network manager with you.
[*]A CLEAN install of dapper or edgy, most of the problems/failures in the responses to this guide have been because of unclean installs giving configuration that gets in the way of this guide and stops it from working, my dapper was installed during the Flight 5 stage and updated from there to knot 2 so its not necessary to reinstall from 6.0* or even if it has been updated from breezy but you might want to think about reinstalling if you've messed around with Ndis prior to this.
[/LIST]

**Okay so you have a wireless card that shows up in ubuntu but doesnt connect to any wireless network?**

The reason the card shows up but doesn't work is because ubuntu is only distributed with its driver (so it can recognize it) not with its firmware (so it can USE it) for legal reasons.

However you can take the firmware out of the windows drivers and put them into ubuntu and make the card work!

**Follow these steps to get your wireless card working under ubuntu dapper 6.06:**

To find out if your card has a broadcom chipset run the following command:
[CENTER]```
 lspci | grep Broadcom\ Corporation 
```[/CENTER]
If that returns a string of numbers followed by the words Broadcom Corporation and then some more numbers then your in luck!
But if not, try my guide anyway, it cant do any harm and it might work for you, its largely untested for cards other than mine and the success stories posted here so give it a go and see!

Here is my output from doing this:
[CENTER]```
lspci | grep Broadcom\ Corporation
0000:02:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```[/CENTER]

It seems that if you get the following string back: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) that this guide is VERY unlikly to work for you although it does sometimes, dont ask me why, but basically every "no" vote and "this didnt work for me" post comes from a BCM4318 user....

**Prerequisite**
    [LIST]
[*]Ubuntu dapper
[*]      A wireless card that shows up in Ubuntu
[*]      A driver installation CD (for Windows) OR a driver for your card from the internet
[*]      Access to the Ubuntu Universe Repository
[/LIST]

** 1 ) Ensure you have access to the other ubuntu repos**
follow the intructions on the second heading from this page to ensure you have the universe enabled
[https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)

** 2 ) Copy your windows driver to your desktop**

**Use this driver with preference to any other:** 
[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
if this fails, your could use any of these:
[LIST]
[*]Copy the driver from the CD that came with the Card
[*]Copy it over from your windows partition if you have access to it, it will be located here: /Windows/System32/Drivers/bcmwl5.sys
[*]Obtain it from here -[http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip)
[*]Get any driver for your card of any date from their website - use this if initially you are not successful first tome try some newer/older drivers
[/LIST]

** 3 ) Install bcm43xx-fwcutter**
Open a terminal (dont worry) and type the following:
[CENTER]```
sudo apt-get install bcm43xx-fwcutter
```[/CENTER]
It will ask for your password and may ask you to press y to install, but dont worry its really easy

**GUI Alternative:** go to *System* in the top Gnome bar then *Administration* then *Synaptic Package Manager*
From here click *Search* and search for bcm43xx-fwcutter
[CENTER][IMG]http://boredklink.googlepages.com/synapticsrearch.png[/IMG][/CENTER]
Right click on its entry in the package window, select *Mark for Installation* and then click apply
[CENTER][IMG]http://boredklink.googlepages.com/synapticselect.png[/IMG][/CENTER]

** 4 ) Extract your Cards firmware from the driver**
Open a terminal (dont worry) and type the following:
[CENTER]```
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
```[/CENTER]
This will create lots of new files in the /lib/firmware directory, this is the firmware part of the driver that will make your card work with ubuntu!
[CENTER][IMG]http://boredklink.googlepages.com/libfirmware.png[/IMG][/CENTER]

** 4B ) Extract your Cards firmware from the driver**
Just to be safe we'll put the driver in the kernel folder too
[CENTER]
```

sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o

```
[/CENTER]

you may have to repeat this step each time the kernel is updated or you may not, your results may vary.

***Note* The location and name of the .o file for this command may differ in your case,  if you really get stuck type bcm43xx-fwcutter and then hit space, find your file using the GUI and then drag and drop it into the terminal.**

** 5 ) Install Network Manager**
I find that this is the best way to manage wireless connections
[CENTER]```
sudo apt-get install network-manager-gnome
```[/CENTER]
It may ask for your password and may ask you to press y to install, but dont worry its really easy

[I]You may find that Network Manager adds itself to system > preferences > sessions >startup programs
or you may not, if you find its not inlcuded,  add[/I]
[CENTER]```
 nm-applet --sm-disable
```[/CENTER]

[I]as found here: [http://ubuntuforums.org/showpost.php?p=1082980&postcount=32](http://ubuntuforums.org/showpost.php?p=1082980&postcount=32) , Network Manager might not work for Apple users, he says that a program called wifi-radar worked for him instead so if network manager is no good for you try this program instead
This might apply for non apple users as well [/I]
[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f)

** 6 ) Bookmark this page and Reboot**
Press Ctrl + D and then click on add
[CENTER][IMG]http://boredklink.googlepages.com/bookmark.png[/IMG][/CENTER]
Then log out & reboot
Return to this page after logging back in again


** 7 ) Use your new Wireless connection**
From what i remember network manager should now show up by your clock and display your current connection, if your lucky it will show a series of bars, this means your now using your wireless connection so lucky you!
[CENTER][IMG]http://boredklink.googlepages.com/nm.png[/IMG][/CENTER]
If it doesnt, right click on it and tick "Enable Wireless" then left click on it 
 and select the wirless network of your choice.

Thanks, i hope this helps...

[B]
Issues[/B]:
----------------------------------------------------
Ensure the router you are connecting to supports 802.11 B connections
as this is what the card is now set up to use, check if your router has a "mixed"
setting rather than a G only setting which it should as G is backwards compatible with B 
----------------------------------------------------
For anyone that is having problems, try this:
[CENTER]```
modprobe bcm43xx
```[/CENTER]
and reboot
----------------------------------------------------
Information about networkmanager

[https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)
----------------------------------------------------
people seem to be having trouble getting this specific card: *Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)* working using this guide, take a look at this post for help:
[http://ubuntuforums.org/showpost.php?p=1084114&postcount=43](http://ubuntuforums.org/showpost.php?p=1084114&postcount=43)
or
[http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218) if your looking to Ndis instead
----------------------------------------------------
If you find your driver comes in a windows EXE format, typically this will just extract the drivers and can be run using Wine and then collected from your wine directory in the same places you can find them in windows
you could try renaming them to filename.zip and seeing if they open that way too.

Thanks for putting together this brilliant guide. I'm a complete newbie to ubuntu, and none of the ndiswrapper stuff worked for me. Your wireless setup method worked like a charm.

Cheers, mate.

---

### Post by woopud on 2006-11-24
Will this work for a AMD64 laptop with the Broadcom 4603 and Ubuntu 6.10 ?

Bert

---

### Post by PPower on 2006-11-27
It depends... Do you mean 4306?
 
Never heard of a 4603, but that probably wouldnt be supported anyway. The 4306 is the most supported one at the moment.
 
Nickm: If your still alive (which I hope you are), I have cracked a few more problems related to this driver. No offence or anything, but the guide has got a little bloated as of late, so I might rewrite it.

---

### Post by dsapoki on 2006-11-28
worked perfectly on my asus a6k-Q023H with Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
thank you

---

### Post by kryton9 on 2006-11-29
Thanks for this walkthrough. I am totally new to linux and ubuntu. I am having problems I can't figure out. I have spent the last 4 days trying to get it to work about 5 hours each day at least. I figured the only way to learn how some of this stuff works.

I tried every walkthrough out there all the ndiswrapper one to the fwcutter ones as this one and did clean reinstalls of ubuntu edgy 32bit each time in between.

I have a Gateway 7422gx with the broadcom 4306 wireless, this walkthrough is the only one where I got the light to come on for the wireless at least, but I can't see any wired networks with network manager. I even disabled all security on my linsys router and enabled it to broadcast. 
When I do sudo /sbin/ifconfig -s
I get this:
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR   TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1500 0      1546      0      0      0     1522      0      0      0 BMRU
lo    16436 0         2      0      0      0        2      0      0      0 LRU
wlan0  1500 0         0      0      0      0      182      0      0      0 BMU

eth0 is my hard wired connection I use when the wireless never works. I do disable it and reboot with the wireless enabled and never can get it to work. My notebook does not have a switch for the wireless, so the fwcutter helped in getting it to turn on as I do get the led lighting up that it is active. 

Any guidance will really help. I feel I am close, but this last day just going in circles and decided to ask for help.

---

### Post by PPower on 2006-11-29
Hmm... Can't help you there, don't use edgy myself (then again, im a Fedora user now).
 
May I suggest you check dmesg for any errors, and let us know whats in ifconfig and iwconfig (no switches).

---

### Post by kryton9 on 2006-11-30
Thanks, I think I am just going to wait till the next release of Ubuntu to come out. I saw the talk on Google video about Fiesty Fawn, it sounds like these sort of problems will be taken care of by then. 

Being new to linux from XP, too much work to make things that work easily in windows. 

I think Ubuntu is really close to being a real alternative to Windows. I just tried Suse 10.2 RC1 today and couldn't get it to see my ati 3d card, even after I installed the linux drivers from Ati. I will see if I can get the wireless working just to see if it does. If not, I will give Fedora a shot.

If I fail in all, I will just put XP back on till the next releases then. It is fun seeing all of these OS's. It will be nice to have a real alternative that just works.

---

### Post by PPower on 2006-12-02
In all honesty, Fedora is nice, but as for your ubuntu problem:
 
The only thing I have any chance of reccomending to you for now is Dapper, but that has problems with it too (losing the AP mac address, one of the reasons I went to use Fedora).
 
Then again... ndiswrapper segfaulted for me on ubuntu.
 
*goes back to playing with compiz*

---

### Post by cyberslayer on 2006-12-04
My system locked up after I completed step 5 in your guide and I had to power everything off because I couldn't reboot.  I can still boot linux (from my hard drive) and my wireless light comes on now (it didn't before) but I can't log on because my mouse and keyboard do not work (I never had any problems with them before).  I was running Ubuntu 6.10 with a Broadcom AirforceOne BCM4318 (I know you said it probably wouldn't work but I thought I'd try it) I am running off of a live CD right now.  How can I get my mouse and keyboard working again short of a reinstall?  I don't care if the wireless card works as long as my mouse and keyboard work again.  ](*,) 

Thanks

---

### Post by cyberslayer on 2006-12-04
Ok I figure out how to fix it.  It seems that the wireless driver was interfering with the mouse and keyboard drivers somehow.  So anyway I fixed it by booting off the live CD and removing the files for the wireless driver from /lib/firmware (after mounting the hard drive).  I have my mouse and keyboard back now but of course my wireless still doesn't work.

---

### Post by mrSlush50 on 2006-12-05
so i got my card working on the second try.  but like an idiot I went and deleted the applet from my panel, and no matter what I do I can't seem to get it back.  I even completly uninstalled network manager, but it still won't pot back up, and when I try to create a new one, I can't seem to get it to work.

can anyone help?

---

### Post by Tiede on 2006-12-05
Your post can have two meanings, so  I have put both things here to account for the ambiguity
First, if you just needed an icon that shows network status:
right click on the panel, select add,  and then choose the icon you want from the list...
If this is not what you meant, i.e you need the network-manager applet that let you select the wireless profile you need, then do the following:
in a terminal, type
```
sudo nm-applet
```

---

### Post by mrSlush50 on 2006-12-05
well the icon isn't on the list, that's the problem.  I'll try to other one though thank you.

EDIT:  right, that didn't work at all.  infact, when I type in sudo nm-applet something weird happens... nothing at all.  it doesn't ask me for my password or anything.  the cursor just drops down to the next line.  I can type whatever I want into this line, and when I hit enter nothing will happen again.  I have to close down, then open up a new terminal in order to do anything at all.

Let me be as specific as I can about my original problem.  The little icon on the panel which apears next to the network monitor is gone.  it's gone because I right clicked on it, then clicked "remove from panel" assuming I could get it back by right clicking on the panel and choosing network manager from the menu.  but network manager isn't on the menu, and when I tried to create a custom application launcher, I was unable to find the right executable in order to do so.  I uninstalled, then reinstalled network manager, then restarted my system, but nothing changed.

---

### Post by Tiede on 2006-12-06
try, in sequence:```
sudo -s -H
apt-get remove --purge network-manager network-manager-gnome
apt-get install network-manager-gnome
nm-applet
```and get back to us.

---

### Post by dalemed on 2006-12-06
It worked!!!  After 2 days of messing around with everything but ndiswrapper, I came across your post.  It worked the first time through.  Thank you very much!!!

I should mention that I'm working with the old Network Monitor, not with the NetworkManager Applet.

I made this mod to a eMachine M5312.

---

### Post by trubblemaker on 2006-12-06
nickm, you the man, I'm going to add your forum to the wiki so people can ask questions, you wrote a great howto,  [wiki for Broadcom]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy").

ps

if anyone feels like updating the wiki with the pretty pictures your the man!

---

### Post by trubblemaker on 2006-12-06
Any one know if the native driver can handle being a ap --> (master mode?)

---

### Post by Jbweld on 2006-12-06
IN TERMINAL Program...
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome
sudo apt-get
sudo apt-get install wpasupplicant
--------------------------------------------------------------------------
sudo gedit /etc/network/interfaces
# Comment out everything other than “lo” entries in that file and save the file 
USE # to comment out!
((Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
Sudo Gedit /etc/default wpasupplicant))) add ENABLE=0 into it and save file.
-----------------------------------------------------------------------------
sudo touch /etc/default/wpasupplicant
YEAH RE_Boot
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
Then set it all up with wpa/network names etc..and your done.

---

### Post by mrSlush50 on 2006-12-07
the first part goes ok, and them I get this:

root@LAPPY-5000:/home/keith# nm-applet

(nm-applet:5464): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


???  did i type that wrong?  was nm-applet supposed to go on the line above?

---

### Post by mrSlush50 on 2006-12-08
well I've tried everything. (that I know to try)  I have completely removed all traces of the install (firmware, drivers, network manager... everything)  then restarted, then did the install again.  still nothing.  I have no way of gaining access to the network manager interface.  when it is installed on my computer, it runs, (I know this because I still get error messages from it) but because I can't run the nm-applet, I can't set a network up.  

Is there a way to run the network manager, or the network manager applet (are these the same thing?) without it being installed on a panel?  is there a way to install the applet on a panel without uninstalling and reinstalling network-manager-gnome? (since this doesn't work anyway.)

---

### Post by trubblemaker on 2006-12-08
so this [post didn't help?]("http://ubuntuforums.org/showpost.php?p=1851604&postcount=635")
there are other ways of getting an ip address.

I assume your interface is wlan0 but could be eth1

you can use:

```
sudo iwlist scan
```

find an ap you like, get it's essid:
```

sudo iwconfig wlan0 essid <fav-essid>
sudo dhclient wlan0
```

or **if** your /etc/network/interfaces is setup correctly:

```
sudo ifup wlan0
sudo ifdown wlan0
```

gui is nice but commandline is better for troubleshooting

---

### Post by mrSlush50 on 2006-12-08
when i run a scan in the command line I don't find anything.  when the applet functioned it found all the networks I find when running windows.  hence the need to get the applet back.  this is what I get when I scan:

lo        Interface doesn't support scanning.

eth1      No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

I *know* there is a network because I have xp up and running wirelessly on the computer next to mine right now.  

bottom line, I'm brand new at this and in GUI, things work (when the GUI is there) in command line things don't work.  (I know this is because I don't know how to make them work and not because they won't, but frankly knowing I don't know something doesn't get me any closer to knowing it.)

EDIT:  Got it. 

thanks for all the help everybody.

---

### Post by trubblemaker on 2006-12-09
I totally get where your coming from.  FYI, if you can't get the wireless networks listed with "iwlist scan" you won't be able to get them running with the gui either.  why don't you post 

```
dmesg | grep bcm
```

I think  it might help point to your issue.


also the last couple lines of ```
dmesg 
```would also help diagnose your issue.

---

### Post by jjesena on 2006-12-09
YES! I finally got it working. Gesho is right, but I think what really did it for me was commenting out everything in the  /etc/network/interfaces file except 'lo'. I have the DELL D810 laptop with a 4318 Broadcom.

A few things to keep in mind: the 'wifi' light needs to be on. Ony my laptop I'd have to press the 'Fn' + 'F2' keys (this also toggles the bluetooth light). When the light is on, try connecting. When that doesn't work, reboot and try connecting again. It worked for me on the second try.

The only problem now is that I only get 11Mb/s, not 54Mb/s in bandwidth. It could be because of the driver, I don't know. And I don't feel like spending another 4 hours trying to get that working. But if anyone else has, please post!

> **gesho said:**
> great topic, thanks to the author.

for BCM4318 users (same here, on my inspiron 600m): look like the post by Slicedbread is the best for us. 
[http://ubuntuforums.org/showpost.php?p=1085392&postcount=55](http://ubuntuforums.org/showpost.php?p=1085392&postcount=55)

here is what I did
installed bcmxx
downloaded bcmwl5 **from Slisedbread's link in above post**
blacklisted ndiswrapper
rebooted
sudo bcm43xx-fwcutter -w /lib/firmware bcmwl5.sys (got same errors here as other BCM4318 users, don't worry)
rebooted

and cheers, signal is there

---

### Post by sargetech on 2006-12-09
much kudos to nick m, thanks loads my friend for the help with microsoft mn-730 wireless card after following your instructs the card worked ok,period,that's all folks,
in fact I'm writing this with the wireless card in full effect
thanks for helping a spanking new nubbie crispy fried chicken dude!!!
thank you,thank you,thank you...

Live Long and Prosper!!!

sargetech,
[email]sargetech@gmail.com[/email]

---

### Post by advoss on 2006-12-10
Your guide was quite helpful in getting the BCM4306 (rev 3) thats built into the compaq nx9110 (the german version thoes letter are used for others aswell).  However it didnt quite work.  NetworkManager wouldnt work but I could use Wifi-Radar to get connected but I couldnt figure out how to connect to protected networks with that. On further searching on the forums I found there is a repository that will do the firmware stuff:

> **Nicks Spleen said:**
> 
## BCM43XX Firmware Repo
deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego bcm43xx


I added it to /etc/apt/sources.list  then installed bcm43xx-firmware rebooted [removed WiFi-Radar, installed NetworkManager] and then NetworkManager is work.

It sometimes takes a couple attempts to connect but I havent had it be unable to yet.

Thank You very much.


___
To thoes people who dont have wireless showing up in network manager:

I had the same problem, it was because i had already tried to configure the card.
I looked at the NetworkManager page in the [Ubuntu Wiki]("https://help.ubuntu.com/community/WifiDocs/NetworkManager") and found that you cant do that.  I followed the instructions:

> the harder way, is to backup and then edit the /etc/network/interfaces file to remove the configuration of these devices (except for lo which is needed for the loopback interface). You will have to save the file and reboot for the changes to take effect (or don't reboot and run /etc/init.d/networking restart instead).

and then wireless appeared in NetworkManager

---

### Post by nukedathlonman on 2006-12-11
I've followed the guide and this works perfectly on my laptop (Acer Aspire 5002WLMi with Kubuntu "Edgy" AMD64 Desktop installed).

I know from reading most people use ndiswrapper to get the wireless working on these laptops, but ndiswrapper simply wouldn't work at all.  No issues installing the proper 64-bit windows drivers, it load in no issues, and shen detected the card properly - but ndiswrapper kept on puking when I tried to load it.  I know it's been suggested that the bcm43xx driver won't work on this particular laptop, I found this driver works perfectly - even the radio enable/disable button works as it should.

Now I have configured up wpa_supplicant so that I can connect to my wireless network (I'm using WPA2-PSK), but I can't seem to get this to auto-connect when in range of my home network, let alone any other wireless network.  The only way I can connect to wireless networks is to do it manuly everytime.

Any idea's on how to get my wireless auto-connecting?

---

### Post by nukedathlonman on 2006-12-11
Never mind, got it all figured out. :-)

---

### Post by jsherman75212 on 2006-12-11
After spending at least 60 hours looking for info to help resolve the wlan issue, I finally found a page that stated that there were issues with the kernel. I followed the directions for compiling the 2.6.19 kernel and rebooted. I removed anything to do with ndiswrapper and loaded the native bcm43xx module. Voila! I am posting this on an HP zv6000 with AMD64 3500+ over the wireless lan. Note - I had already used fwcutter to cut the firmware and I have no clue if this may have made a difference on the new kernel. But 2.6.19 just works with the wireless device although the light ONLY comes on when it is transmitting or receiving.

---

### Post by Tiede on 2006-12-13
That's the way the light works now. I know, it pisses me off too sometimes; especially when I need to quickly check if my wlan card is on or off. I guess they thought we might need to monitor network activity more often...

---

### Post by jd4x4 on 2006-12-17
newbie user here... Thanks! It worked on IBM A20m laptop under XUbuntu 6.10 with Linksys card (BCM4306 Rev 03), but with the following notes:
I had installed Wireless Asistant prior, and after step 4a no luck. Then, after 4b & no luck I installed Network Manager. NM didn't see wireless card because I realized that it wasn't activated so I activated it (using System menu, Network). Still no luck so I rebooted.

Couldn't find NM again (hmm.. newbie!?) so I used Wireless Assistant & this time all worked fine.

I think NM said that it installed under Internet, but since my XUbuntu doesn't have that as a menu option... well, who knows where it is! I'll find it eventually I guess!

---

### Post by BrianH on 2006-12-18
Is it true that this will not allow me to connect 802.11g 54Mbps???

I got this working last night on my BCM4306 Rev 02 and it works great except that I need it to work at 54Mbps.  I'm trying to transfer HD video from another local machine (wired to the router) and 11Mbps is out of the question.

How can I get 54g speeds?  Will the Ndiswrapper method work for this?  I was hoping I could make it simple.  Anyone have any success?

---

### Post by damnhappy on 2006-12-18
Hi, 
I got everything working great! This guide was a great help. 
One thing is I need to have my IP set to a static address. Is there a way to configure my card's IP? 
Thanks!

---

### Post by Clydesdale on 2006-12-20
Awesome!!!  It worked the first time on my Fujitsu P5010 laptop!  I'm using it right now!!!

I followed the first directions exactly, using the wl_apsta.o driver method.

WOW!!!  I was about to go back to Windows XP but now have my screen recolution, Palm Pilot interface, and wireless Internet access so I'll stay with Ubuntu Linux.  Way to go Ubuntu.  I gave up on getting Red Hat Enterprise Linux 4 to work on my laptop.  Ubuntu was FAR easier to get going.  Not easy but I, a beginner, was able to do it.

---

### Post by woopud on 2006-12-20
nickm, thank you so much !!
I've been trying to get my 64 bit Edgy on my Laptop to work with the build in Broadcom 4306 for a month now, re-installing 64 bit Edgy, trying x86 Edgy, trying 64 bit dapper and followed the Ndiswrapper guide but got messed up every time.  Followed your guide and I got it working in 10 minutes !!

Bert

---

### Post by mukherjee.siddhartha on 2006-12-22
Hi,
I have this
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

And the bcmwl5.sys worked perfect.
Thanks to all :mrgreen:

---

### Post by xpan on 2006-12-24
It didn't work on me.

I use an Acer 3023WLMi laptop with broadcom's 4318 wireless chipset. NDiswrapper didn't work either. The problem is that the button that turns on the antenna does not work (neither it works on windows but at lest broadcom provides a small .exe file that turns on the antenna and the wifi led starts to blink)

this is my output, if means anything to you:


The lines printed out while installing fw-cutter are not in english so I removed them. The following comments are mine
.. 
downloading and installing fw-cutter 
..seems ok
..However I get a message that the following libraries
[I]imlib11 tcltls docker sox imlib-base tk8.4 php5-cli libhtml-lint-perl
php5-common weblint-perl ndiswrapper-utils-1.1
[/I]
are not needed and I can use apt-get autoremove to remove them
..
The non-english part ends here, The following section is copy-pasted as is.

> 
xpan@xpan-laptop:~$ sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
--19:51:14-- [http://svit.epfl.ch/stuff/wl_apsta.o](http://svit.epfl.ch/stuff/wl_apsta.o)
=> `wl_apsta.o'
looking for svit.epfl.ch... 128.178.192.9
Connecting to svit.epfl.ch|128.178.192.9|:80... connected.
(http seems ok)... 200 OK
length: 652866 (638K) [text/plain]

100%[====================================>] 652866 74.21K/s ETA 00:00

19:51:23 (73.81 KB/s) - `wl_apsta.o' saved [652866/652866]

bcm43xx-fwcutter can cut the firmware out of wl_apsta.o

filename : wl_apsta.o
version : 3.130.20.0
MD5 : e08665c5c5b66beb9c3b2dd54aa80cb3

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
extracting bcm43xx_microcode11.fw ...
*****: Sorry, it's not possible to extract "bcm43xx_microcode13.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in the future...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...
xpan@xpan-laptop:~$ sudo modprobe bcm43xx
xpan@xpan-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID: off/any Nickname:"Broadcom 4318"
Mode: Managed Frequency=2.484 GHz Access Point: Invalid
Bit Rate=1 Mb/s Tx-Power=19 dBm
RTS thr: off Fragment thr: off
Link Quality: 0 Signal level:0 Noise level:0
Rx invalid nwid: 0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries: 0 Invalid misc: 0 Missed beacon:0

sit0 no wireless extensions.

xpan@xpan-laptop:~$ sudo iwconfig eth1 ap any
xpan@xpan-laptop:~$ sudo iwconfig eth1 rate 54M
xpan@xpan-laptop:~$ sudo gedit /etc/network/interfaces 


I also tried to run nm-appler but it does not recognize any wired or wireless device. Maybe because Edgy uses its own network manager interface. Edgy's network manager interface recognizes both my devices (wired and wireless) but although the wireless device is recognized and enabled the wifi led does not blink. This means that the radio is off.

any ideas?

---

### Post by woopud on 2006-12-24
> **woopud said:**
> nickm, thank you so much !!
I've been trying to get my 64 bit Edgy on my Laptop to work with the build in Broadcom 4306 for a month now, re-installing 64 bit Edgy, trying x86 Edgy, trying 64 bit dapper and followed the Ndiswrapper guide but got messed up every time.  Followed your guide and I got it working in 10 minutes !!

Bert

Well, it worked for about four days then it quit working.  The wireless shows up under System -> Administration -> Networking and is enabled but under Network Manager it only shows Wired Connection.   Any ideas ?

Bert

---

### Post by Dustin88 on 2006-12-24
@woopud-

If you have configured the wireless settings in Networking at all, it will not show up in Network Manager. Make sure you uncheck the box for the wireless connection that says 'Enable this connection' and then restart your system. Now it should show up in Network Manager.

@xpan-

The above may apply to you.

@BrianH-

As far as I can tell it will only work at 11Mbps. The ndiswrapper method, however, will allow you to connect at 54Mbps. You can find out how to do it here: [http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/](http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/) . If you're using Ubuntu 6.10 (Edgy) be sure to replace the line that has "sudo apt-get install ndiswrapper-utils" with "sudo apt-get install ndiswrapper-utils-1.8" otherwise it won't work.

Hope this helps you all,
Dustin

---

### Post by trubblemaker on 2006-12-24
> **xpan said:**
> 
 Edgy's network manager interface recognizes both my devices (wired and wireless) but although the wireless device is recognized and enabled the wifi led does not blink. This means that the radio is off.

any ideas?

You can turn on your wireless in bios or in windows then try and use it.

---

### Post by xpan on 2006-12-25
> **trubblemaker said:**
> You can turn on your wireless in bios or in windows then try and use it.

thanks, I tried but when I logoff from windows the radio is disabled. 

in Bios I couldn't find the option.

I will send a mail to Acer support. Have I got any chances to receive an answer?

Does my output look normal?

---

### Post by trubblemaker on 2006-12-26
yes most looks normal except for you setting the rate to 54M which at this point doesn't work.  But that was mention in a previous post.  Just good to reiterate it.  It works reliably at 11M, bit faster at 22M, and unstable but faster at 36M.  I wouldn't recommend at all using 54M and the bcm43xx driver.  (for that speed use ndiswrapper)

to see if the card is working use 

```
iwlist scan
```

this is a simple test to see what the card can see. 

I didn't really see much output from you. (read the post but nothing out of the ordinary there) 

/etc/network/interfaces must be empty ( except for lo enteries) for nm-appler to recognive your device

if you used the Network Manager to configure your wirless card, /etc/network/interfaces will have entries in it.

if you previously attempted to use ndiswrapper, it may be causing a conflict with the current bcm43xx driver.  If you have not blacklisted ndiswrapper please consider doing it as both ndiswrapper and bcm43xx should not be loaded at the same time.

to blacklist ndiswrapper at "blacklist ndiswrapper" to :

```
sudo gedit /etc/modprobe.d/blacklist
```

hope this helps

please remember to post iwlist scan.

---

### Post by SeaSky on 2006-12-27
If you have ever updated the broadcom driver under windows many of these how to's will not work. Why? Because the OEM drivers also update your firmware on your handy dandy broadcom chipset, it will still say you have 4318 or 4319 or whatever, and you do, but it's been "updated" After sending over 300 correspondances to HP about this and threatening legal action they finally did add the words "and firmware" on their driver downloads pages.

 If you updated your driver under windows with a driver from HP then it also 'updated' your firmware...

---

### Post by trubblemaker on 2006-12-27
SeaSky thanks for the update, but isn't the firmware loaded on boot hence us cutting it out, so it can be loaded?  are you saying that we shouldn't cut out the firmware from new downloads?  Or are you saying that new drivers need new firmware?

---

### Post by itsjustasensation on 2006-12-30
This HowTo worked for me.

This is a note Lenovo 3000 C100 laptop users trying to get their wireless working. I'm running Ubuntu 6.06 Dapper


```
lspci | grep Broadcom\ CorporationI


```


Gives me this:

Code:
```

0000:01:02.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02) 


```

note the end part that says (rev 02) - so its a rev 02 device but not specifically the AirForce One 54g referred to above.

I didn't have to do anything extraneous, only what nickm posted in the original.

I did, however, have to unplug my network cable and reboot to use the wirless. This means that, at this stage, I can only use either the wireless OR wired. If I want to change to wired I have to plug the cable back in and reboot. No amount of deactivating / activating or whatnot in System > Administration > Networking seems to be able to do this for me.

I also edit iftab

```

sudo gedit /etc/iftab 


```

so it says wlan0 instead of eth1


---

You might be wondering why I would want to use wired when I now have my wireless working? 

To my knowledge wireless network cards use similar transmittions technology as mobile phones, and I don't particularly fancy the idea of having a low powered microwave transceiver sitting on my testicles (or so close to my partners ovaries), hence I have a 30meter network cable and only rarely use the wireless.

Thanks nickm, that is really simple compaired with the other 2 processes I tried.

Good job.

Adam

---

### Post by boersmaa on 2006-12-30
After I did this, in network-tools, when I checked, I did not get the IPv4 protocol in my eth1, only IPv6.
My wired eth0, and when I plug in a Cisco airnet card, they get both, IPv6 and IPv4 protocol.
I have no need for IPv6.

I also have a wifi0 card listed in my network-tools, it has no protocol but it shows interface statistics!

Anybody can shine some light on this?

HP DV8120 Turion ML37, Broadcom Airforce G, Ubuntu Edgy.
It has 2 drives so I installed Edgy on both with the same result!

Everything else works perfect on the laptop.

Andy

---

### Post by trubblemaker on 2006-12-31
> **itsjustasensation said:**
> No amount of deactivating / activating or whatnot in System > Administration > Networking seems to be able to do this for me.


I suspect it's the bind order of the nic's, I'm not being snotty but I don't use the gui.  the command line process to change from wireless back to wired connection (assuming /etc/network/interfaces file is correctly configured)

[code]
sudo ifdown wlan0
sudo ifup eth0
[code]
that should do all the necessary work to switch back to a wired connection.  I hope this helps if you don't get a new ip that usable post the output from the commands and I'll try and help you figure out what's up.

rebooting isn't usually necessary in linux.  it usually works, but isn't usually required.  there's another command to invoke restarting your networking module in linux but I have it written down on a computer I don't have access to at the moment.  if the above commands don't work I'll post that solution tomorrow.

---

### Post by cbm_redux on 2006-12-31
I couldn't get anything to work with EdgyEft. Well, that's not entirely true. I hand wireless access for about 15 minutes using ndiswrapper. That promptly disappeared and proved irretrievable when I rebooted.

So, I did a fresh install of Dapper and followed the instructions in this how-to. Again, I had wireless access for a few minutes, and now it's gone. The nm-applet shows my wireless network and that of a neighbor. However, when I attempt to connect it takes an inordinate amount of time to establish a connection. When the "circling connection icon" finally shows two green lights, there is no signal, 0%. The one time that I actually had internet access, immediately after installation, it was at 100%. Also, I'm not sure if this is significant, the signal is quite strong under WinXP. 

I've managed to connect using wifi-radar by creating a an entirely new wifi network with a different ssid and no security. Of course, this isn't a suitable solution. At this point I haven't a clue what to try next. Any ideas anyone? ](*,)

* the poll should have a choice for "not exactly."


Edit: Well I've got wifi working reliably if not perfectly. For reasons about which I won't even hazard a guess, I can connect on the first time, every time, if I use the nm-applet choice "create new wireless network" then launch wifi-radar. If I don't launch wifi-radar, then nm-applet will connect but the signal strength will be a 0% and I won't be assigned an IP address. With wifi-radar running (I don't connect with it, I just have it running so that I can see which, if any, IP address assigned) the connection and appropriate IP initiate straight away.

---

### Post by Stephen47 on 2007-01-01
I read in another thread that the fw-cutter method doesn't work with the 1390 on the E1505. Is this true?

---

### Post by laharrin on 2007-01-02
This worked for me with a BCM4318 AirForce One (rev02) using bcmwl5.sys.  I believe the key was in following the steps on a fresh install *before* applying any updates.  I tried earlier after applying updates to a fresh install and had no luck.  I was very glad to see the green Wi-Fi indicator on a Dell Inspiron 6000 alight this time!  Thanks very much for the concise how-to.

*Update*:  The card continues to work after applying the updates.

---

### Post by Slodeine on 2007-01-02
I've been endlessly tweaking my settings for the past two days without success.  I use a Linksys WPC54G v1.2 PC card, and I've tried both ndiswrapper and the native drivers.  Most recently, I reinstalled Edgy and followed this HOWTO word for word.  I'm still having the same problem, what others have described as "kernel panic."  Everytime I attempt to modify the card's settings through the built-in Network utility, I experience this kernel panic.  *dhclient* also causes a hard crash.

I'm completely new to Linux and Ubuntu, so I don't really know what to do about this.  Will changing kernels solve the problem?  Is changing kernels difficult?  Do I have to go to a newer kernel or an older kernel?  What might the side-effects be?

---

### Post by taco_truck on 2007-01-02
This guide worked perfect for me!!

All i had to do was install gnome network manager and it worked!

---

### Post by katu on 2007-01-02
Worked perfectly. I had a moment of crisis right after restart, cause it didn't see anything, but now it works perfectly (on an AMD 64 bit system ;>).

---

### Post by trubblemaker on 2007-01-02
cbm_redux check out last 20 posts on this thread as I think I've already answered this question. 

please post the output of these commands:
```

sudo iwlist scan
iwconfig
cat /etc/network/interfaces

```

---

### Post by trubblemaker on 2007-01-02
the kernel panic may be due to the not blacklisting  ndiswrapper or bcm43xx  whichever you have installed you must blacklist the other
if you have bcm43xx installed 

add "blacklist ndiswrapper" to /etc/modprobe.d/blacklist

don't for get to use sudo as you'll need permission to edit that file

if you have ndiswrapper installed

add "blacklist bcm43xx" to /etc/modprobe.d/blacklist

---

### Post by mallama on 2007-01-02
First off i would like to say thank you so much for this walk though! It worked like a charm. I am writing this post on my new wireless connection under ubuntu!!! The only thing that i have to say. Keep in mind this may be a rare problem. My wireless wouldn't connect until i set a static ip. Then it would connect and i couldn't surf till i set a DNS server. Weird huh but never the less everything is working great. Thanks so much for this TUT great work!!

---

### Post by Stephen47 on 2007-01-03
> **Stephen47 said:**
> I read in another thread that the fw-cutter method doesn't work with the 1390 on the E1505. Is this true?

bump

---

### Post by shams on 2007-01-03
Laharrin, I have the same card.  

questions:
1. [QUOTE]****In my edgy knot 2 testing I found that edgy users can stop the guide after competing stage 4 or 4b as it 'just works' with out network-manager if you fill in the SSID and set the wireless device to DHCP in the "networking" option under System > Administration****[QUOTE]

how do I find the SSID to fill in?  

you use edgy or dapper?

---

### Post by trubblemaker on 2007-01-03
```
sudo iwlist scan 
``` will give you a list of essid's to use

---

### Post by Stephen47 on 2007-01-03
> **Stephen47 said:**
> I read in another thread that the fw-cutter method doesn't work with the 1390 on the E1505. Is this true?

bump well is it?

---

### Post by Slodeine on 2007-01-03
Thanks for the suggestion, Trubble, but I followed the procedure on a completely clean install of Edgy Eft.  I've blacklisted ndiswrapper just in case, but it hasn't solved my kernel panic problem.

Any other suggestions?

---

### Post by jeanomobono on 2007-01-04
Works perfect in a Compaq Presario V3115LA!!!!

Thanks!!!!

---

### Post by trubblemaker on 2007-01-04
> **Stephen47 said:**
> bump well is it?

only one way to find out try it, I don't believe everything I read, and half of what's posted.  Most people are trying to help out but don't have all the info.  To really know the answer I say try it out yourself.  I'll help troubleshoot it if you want.

---

### Post by trubblemaker on 2007-01-04
Slodeine, most likely you have two driver's trying to access the same piece of hardware,  and that is what is 'causing your kernel panic.  Atleast that is what happened with me, bcm43xx and ndiswarapper.   I don't have your driver, and don't know what's natively supported for it, but that might be something to look into.  Basically if you did a fresh install, did you try for wireless support before installing anything?  Did you immediately install a wireless driver? Was the wireless card detected in the installation process?  Can you think of any other drivers that you might have installed?

hope this helps, keep me posted.

---

### Post by mallama on 2007-01-04
OK i have HP dv5222 laptop with a broadcom wireless card. I finally got this card to work with this nice TuT after many failed attempts with NdisWrapper. The only problem i have now is the wireless will stop working after about an hour of use. It will still say it is connected but will not receive any more data. I see it sending but not receiving thanks again for all the help.

Cheers

---

### Post by Slodeine on 2007-01-04
Actually, Trubble, Ubuntu recognized the wireless card immediately after the clean install.  Does that indicate the presence of a native driver for the card?  And could that driver be causing the conflict?  I suppose I'd need to blacklist that driver as well; does anybody know where to find it?

However, that doesn't explain the kernel panic, because I experience the kernel panic even before I followed this tutorial and right off the clean install, literally before I had done anything to the OS.

---

### Post by trubblemaker on 2007-01-04
if you the wireless card is detected off the bat then their is no need to start installing drivers.  If you  experienced kernel panic before installing the driver then your likely isn't related to the driver.  you should start a new thread with your posted dmesg, and a meaning full message like "kernel panic after install".  if you should mention the network issue as an aside,  as it happened before the install of the drivers.

---

### Post by Slodeine on 2007-01-04
Thanks, Trubble.  In which section would you recommend I post?

---

### Post by trubblemaker on 2007-01-04
try[ installation and upgrades]("http://ubuntuforums.org/forumdisplay.php?f=140") there are also some sticky's that might be worth reading through for help.  Good luck, if you get the issue fixed and still need help with networking send me a pm and I'll try and help you.

---

### Post by quarkcool on 2007-01-06
Thanks! It worked with my old HP laptop and Linksys PCMCIA card WPC54G.
Although I'm not sure why it worked; I'll try to describe my experience here, maybe it will be of some use for other users :[LIST=1]
[*]Fresh Ubuntu 6.10 install
[*]Followed nickm tutorial (very nice by the way). Reboot. Didn't work. I deleted the sections about eth1 (my wireless interface) and eth0 (my ethernet interface) in /etc/network/interfaces then reboot : I was able to connect to my linksys access point, so it worked like a charm
[*]There were 90 upgrades to install, including Linux Kernel 2.6.17-10. I did that, reboot (because of the new kernel), and wireless didn't work anymore.
[*]At this point I tried to redo the howto several times; to redo it from scrath I deleted the bcm43xx_* files in /lib/firmware and /lib/firmware/linux-*, I removed the network-manager and network-manager-gnome packages, ran rmmod bcm43xx, then I followed the HOWTO again, ran modprobe bcm43xx, reboot
[*]It didn't seem to work, I tried several times and after each reboot it didn't work; I decided to let go for a moment, and shutdown the computer. I returned several hours later, and suddenly it was working. I rebooted the computer once and it worked again. So I guess it's working now (I hope)[/LIST]As you can see, my only concern is that it seemed to work a bit randomly. So I hope I won't have to go through this again if my wireless card suddenly decides not to work anymore.

For those who are wondering, I used the wl_apsta.o file linked from [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy") to extract the firmware (see the bold part about linux 2.6.17).

Anyway, thanks a bunch! Great HOWTO

---

### Post by Gor3 on 2007-01-06
Hello. I just isntalled Ubuntu Edgy and manage to figure out what the console was. I read ubuntu guides for beginners and I'm a bit lost. I've tried following this guide step by step and I can't get my wireless to work. I have an iMac G5 1gb of ram PPC with Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). I'm dual booting Edgy with Mac OSx and my kernell is 2.6.17. I read in a few other threads that the kernell 2.6.15 or so and above have the driver to recognize my wireless card which apparently it does, but I cannot connect to my network.

I installed bcm43xx-fwcutter and when i get to the step "sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o" I get the following error:
*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.*****: But this can be added in the future...

I've download several other drivers I found in this thread, but none worked. Now, also in this thread I read about G5's and my wireless card not working or having some problems. I've searched around and followed several step by step guides and there is always 1 step that I either don't understand or the command just doesnt do anything for me. I'm about to give up and uninstall ubuntu alltogether. If anyone has a noob-friendly step by step guide for a guy that is a few days new to linux will be much appreciated. :KS 

Thanks,
Gore

---

### Post by joshthejest on 2007-01-10
For some reason it did not work for me.  I did a clean install on my machine and followed your steps exactly.  I did not get any errors during the process, but it still doesn't seem to work.

Here are some of my outputs, any help would be greatly appreciated.

```
**lspci | grep Broadcom\ Corporation**
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

```
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```


```
**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:11:43:63:63:CE  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe63:63ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169654 (165.6 KiB)  TX bytes:4027 (3.9 KiB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:0B:7D:0E:61:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:11760 (11.4 KiB)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

---

### Post by Celil Rifat on 2007-01-10
The installation went fine for me, and the wireless worked,  but after an hour it mysteriously stopped working.

---

### Post by spd106 on 2007-01-10
Thanks again nickm for this handy guide.
 
I'm feeling really pleased that my Belkin F5D7000 v1 is now finally working with WPA-PSK. I thought I'd never get more than WEP. Network Manager didn't work, so I tried wpa_supplicant from the /etc/network/interfaces file with the wext driver. After about two hours of tinkering it suddenly just worked. Then again on reboot.
 
lspci says "Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)"

The weird part is that I can't get it to work on Win2K. Belkin doesn't provide a WPA utiility so I've had to use the free McAfee one, but it just won't connect. Even though my F5D7010 with the same chipset does.

I found this howto to be quite useful [http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

---

### Post by spd106 on 2007-01-10
@joshthejest 

Try scanning for APs with **sudo iwlist eth1 scan**.

---

### Post by vliegje20 on 2007-01-13
The tutorial worked for me except on 1 point. The startup for the gnome-network-manager. The startpost says:

You may find that Network Manager adds itself to system > preferences > sessions >startup programs
or you may not, if you find its not inlcuded, add nm-applet --sm-disable. 

When i put that in the Terminal i get:
(nm-applet:4895): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(nm-applet:4895): Gdk-WARNING **: locale not supported by C library
/bin/sh: /usr/bin/esd: No such file or directory

Networkmanager doesnt work at startup. First i have to open the terminal. Then i must add nm-applet --sm-disable. Then i see the gnome-network-manager. But when i close the terminal the gnome-network-manager disappeears from the screen. But the internet connection still works.

---

### Post by davy-mobil on 2007-01-13
Thank you for your tutorial.  I have a Broadcom 4318 and it worked for me.

---

### Post by BiggerBadderBen on 2007-01-14
Thanks so much.  It worked like a charm on my 3-year old Dell D600 with Broadcom BCM4306 Wi-fi chipset.  Previously I used ndis-wrapper and wpasupplicant and invariably got confused and depressed.  Setting up a wlan connection is getting easier in Linux and documentation like this really helps!

---

### Post by buMPer on 2007-01-19
hello all!  my card used to work following this HOW-TO until i patched my 2.6.17-generic-amd64 kernel to 2.6.19.1 and reboot for the new kernel to load.  when i got the login page suddenly the keyboard lights started flashing and i couldn't move my mouse and keyboard don't respond anymore.  i reboot using the old kernel and same result.  i tried using the safe mode kernel and everything was loading smoothly until it started loading the bcw43xx module.  i know i messed up bigtime with the kernel compilation but i'm stumped.  dunno what to do anymore.

as a last resort, i installed WINXP :frown: :frown:  just to go online and post here.  i thought i was finally free from winxp......

please help.....

---

### Post by trubblemaker on 2007-01-19
if your still trying to recover, use a live cd,

once boot is completed, open a terminal:

I hope you know what partition your '/' is on here I use /dev/hda1 the most common:
```

mkdir oldfiles
mount /dev/hda1 oldfiles
cd oldfile/etc/modprobe.d/
echo 'blacklist bcm43xx' | sudo tee -a blacklist

```
and reboot. this should stop bcm43xx from intializing.

If this works, great if not post back and I can help you "keep" alot of your info, with the loss of some installed programs.

---

### Post by Coombabah on 2007-01-19
Close but not there yet :(
This appeared to work, I voted yes but now discover that after a while wireless always fails then my system locks up completely requiring power off. &#901;
I googled and found others with the same crash problem when trying to use broadcom wireless under Linux :( 
Back to plan A and using a Linux friendly PCMCIA card instead.

---

### Post by buMPer on 2007-01-20
> **trubblemaker said:**
> if your still trying to recover, use a live cd,

once boot is completed, open a terminal:

I hope you know what partition your '/' is on here I use /dev/hda1 the most common:
```

mkdir oldfiles
mount /dev/hda1 oldfiles
cd oldfile/etc/modprobe.d/
echo 'blacklist bcm43xx' | sudo tee -a blacklist

```
and reboot. this should stop bcm43xx from intializing............

thanks man!  i was able to run it in recover mode using the cd.  then i..

```
modprobe -r bcm43xx
```

as fast as i can type coz the first 3 attempts it only takes less than 5 secs after logging into recover mode and kernel starts to panic again.  too much coffee maybe (LOL)

i went to /etc/modprobe.d and vim the blacklist and added "blacklist bcm433" just to make sure.  don't want it to sneak up on me next reboot.

> **Coombabah said:**
> ..................Close but not there yet :(
This appeared to work, I voted yes but now discover that after a while wireless always fails then my system locks up completely requiring power off.................


same thing happened to me man.  started to work after updating 2.6.17.10-x86_64 generic kernel to 2.6.19.1 kernel.

trubblemaker, now i can't see my NIC when in "iwconfig".  i did "ifdown" and "ifup" still no luck.  stumped again.  anybody has a solution?  a walkthrough?

thanks again trubblemaker!

---

### Post by trubblemaker on 2007-01-20
As bcm43xx is your wireless driver it seems and you blacklisted it, you no longer have a wireless card driver.   

If you updated to the new kernel again, it will reinstate the driver.

 BUT all is not lost you can replace bcm43xx with ndiswrapper and then use the windows driver.  see my signature for the** 'ndis from source'** in my signature.  It's actually  faster than the bcm43xx driver which only operates at 11M/bs.   any link in my signature should have a ndiswrapper method.  I do suggest perphaps going to [ndiswrapper source forge]("http://sourceforge.net/project/showfiles.php?group_id=93482") and downloading the latest source though to do it, as it's most likely to work with your new kernel.

If you want to file a bug report so bcm43xx gets fixed or see if it's already posted as a bug

[go here]("https://launchpad.net/ubuntu/+source/gnome-power-manager/+filebug")
and explain your bug with the following output

```
uname -a >> output

sudo lspci -vv >> output

sudo lspci -vvn >> output

sudo dmidecode >>output
```

OK know attach your above "output" file also attach /var/log/kern.log.0 to your bug report and you will get the attention of a developer.  They will work on bugs that have output.

Hope this helps.

Matt

More questions? post back.

---

### Post by donniebnyc on 2007-01-22
Thanks so much for an easy to follow procedure that worked on the first try.  =D>

---

### Post by erothoff on 2007-01-22
Your How To works great with both i386 and AMD64 Edgy using Broadcom 4311, if you want just 802.11 b. Is there anything coming up that will allow use to use 802.11 g without using ndiswrapper?

---

### Post by wncben on 2007-01-24
YAY, I have wifi!   (on an AMD64, with the 4318 chipset) following a combination of compwiz's howto, and this one, and some other kind folks out here...


I started with a FRESH install of ubuntu 6.10
I then installed a newer kernel (compwiz has a good stable 2.6.19.2) as the amd64 flavor of ubuntu, and the generic 2.17.10 don't combine for happy wifi 
activated multiverse and universe repos
I then installed ndiswrapper 1.34 from sourceforge
then i ran the fwcutter from this thread
I installed network manager (wifi radar badly broke my touchpad)
then I commented out all the lines in /etc/network/interfaces except for these two
> auto lo
iface lo inet loopback


now wifi works, though my touchpad is not 100% as scrolling and touch and drag don't work...  I have read this may be because of an inharent conflict between the bcm43XX driver and the touchpad driver.

---

### Post by buMPer on 2007-01-24
> **trubblemaker said:**
> As bcm43xx is your wireless driver it seems and you blacklisted it, you no longer have a wireless card driver.   



hey it works now.  i just made sure that eth1 or eth0 is changed to wlan0 on all entries and make sure you enable eth1 or eth0 


```

sudo gedit /etc/modules (should have ndiswrapper entry)
sudo gedit /etc/modeprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab

sudo modeprobe


```

then reboot.  hit firefox

---

### Post by discord on 2007-01-25
look here got it working and with network manager!

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

### Post by LouO on 2007-01-26
This worked perfectly on my HP zv6130us (using the wl_apsta driver).
The only thing is that your wireless light now flickers (looks like from the send/receive signal) instead of being on steady like the "original hp configuration".

I'm pretty new to Linux and Ubuntu and following these instructions was just what I needed - THANK YOU!

:D

---

### Post by taosaur on 2007-01-29
My issue may have nothing to do with the drivers:  this guide got me running with a 4318 chip (thankyouthankyouthankyou), but my connection frequently 'breaks;' while Wifi Radar shows everything kosher, none of my software (Firefox, Package Manager, Songbird) can access the net.  A restart fixes it for anywhere from 15 minutes to an hour, but why is this happening in the first place?  Can I do anything to correct this problem without restarting?

---

### Post by saris on 2007-01-29
After trying all kinds of things for a week, this really did the trick!  Finally got my wireless working, thank you very much for posting this thread.

---

### Post by bailey_jatt on 2007-01-30
thank you sir, indeed an excellent how to.

---

### Post by duouk2000 on 2007-01-30
Bah, I have the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) chip and predictably, it doesn't work :(

---

### Post by Uncelilo on 2007-01-30
Thanks! So much! This worked on my HP dv8210. I have the BCM4318 [AirForce One 54g]. 

Before I've tried using ndiswrapper and couldn't ever get it to work. I spent a good 5 hours just messing around with it.

Then went through this and now it works.  I had tried configuring the wireless card through the System / Administration / Networking thing. So I had to remove all the settings from there first. But now it works great. I used the driver found here: [URL="http://sidulus.textdrive.com/bcmwl5sys.zip"]

---

### Post by taosaur on 2007-01-31
> **duouk2000 said:**
> Bah, I have the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) chip and predictably, it doesn't work :(

That's my chip, and I got it running.  Key for me was removing Network Manager and putting in WiFi Radar.

---

### Post by duouk2000 on 2007-01-31
It's working now, god knows why, it just appeared out of no where in network manager before O.o

Still, as long as it works I'm grateful, cheers OP :D

---

### Post by kelleychambers on 2007-02-01
Dude... after 18 months of not being able to use my built in wireless modem, this tutorial WORKED!  You guys have made me one happy camper.  It's all I needed to fully convert to Linux.  Thank you so much!

:D

PS - I have the nasty rev 2 also:  
kelley@Greene:~$  lspci | grep Broadcom\ Corporation05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by ilopriz on 2007-02-03
Hello!
I've a problem.
When I execute step 4 (Extract your Cards firmware from the driver)
When I execute the comand
```
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
```
the first time I tried with this driver:

[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)

and I receive the following:
```

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
extracting bcm43xx_microcode11.fw ...
*****: Sorry, it's not possible to extract "bcm43xx_microcode13.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Lucily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in yhe future...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...

```

I tried also all these drivers:
-Windows driver in /Windows/System32/Drivers/bcmwl5.sys
-http://sidulus.textdrive.com/bcmwl5sys.zip
-http://svit.epfl.ch/stuff/wl_apsta.o

but the result is similar.

Where is the problem???

---

### Post by Justin Holt on 2007-02-04
I also have the same problem as ilopriz with the old firmware. 
Could some one also tell me if my card in this HP dv2000 works, here is the output from the lspci command from the tutorial:
[CODE

justin@jusitn-hp:~$ lspci | grep Broadcom\ Corporation
01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

[/CODE]

any help would be appriciated

---

### Post by ggendron on 2007-02-04
Just want to say thank you.  Have been trying unsuccessfully for 3 years ( every 6 months or so ) to get wireless G working on HP zv5000z (AMD).

---

### Post by #Reistlehr- on 2007-02-05
i got an HP Dv9000z, bcm4310. i have been unsuccessful with ndiswrapper, and this method. i am also running with noapic and apic=off, otherwise x crashes from nvidia. any help woudl be appreciated.

---

### Post by #Reistlehr- on 2007-02-06
i have a 4310 and i get this

```
mike@ubuntu:~$  nm-applet --sm-disable
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM default

(nm-applet:10489): libnotify-CRITICAL **: notify_notification_close: assertion `notification != NULL' failed

(nm-applet:10489): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```


fwcutter and ndiswrapper both failed to work

---

### Post by Chamith on 2007-02-09
hey

one of the best guides I've seen for Ubuntu or Linux in general.  As a completely new user it was super easy to follow and fix my wireless problem (Dell 600m)

---

### Post by iamtherealwoody on 2007-02-09
Thank you, Thank you, Thank You.
Been reading stuff for the past 2 days trying to get wireless to work, ndiswrapper, all that.  This worked in 5 minutes!  Thank you again.  Now if i can just get my sound to work.

Gateway M675
Broadcom 4306

Matt

---

### Post by vegascoop on 2007-02-13
I can confirm this guide works perfectly with a Buffalo Wireless-G 125 PCI Adapter (WLI2-PCI-G54S) using the suggested wl_apsta.o driver on the 32bit version of Ubuntu 6.10.

Thank you so much.

---

### Post by Neodragon90 on 2007-02-14
Is there anyway to get this to work with wireless-g because i have a wireless g card but i can only connect with b and my router has a verry shoddy b connection
Edit:
```
andy@Ubuntu-Laptop:~$ lspci | grep Broadcom\ Corporation
03:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

```

Thats what my lspci is and b does work when it feels like  it.

---

### Post by sourabhbora on 2007-02-16
Thank you for this nice guide. But, its not working for me. :(
I have a brand new compaq presario c502us. with the infamous bcm 4311 card (from lspci and lspci -n)

The only version of bcmwl5.sys that works with this card is 4.40 (in windows)
but, bcm43xx-fwcutter -l says versions upto 3.90 only are supported.

Has anybody got it working on latest compaq machines?

---

### Post by meaghanz on 2007-02-18
I've had ubuntu on my laptop for about a year now...but barely used because I couldn't get the wireless card to work (yes, i'm a newbie).  Finally, a guide that made sense, was easy to do, and most of all, actually worked!!!  Thanks!!!

---

### Post by Devastator9 on 2007-02-20
Hey
I just followed your post here to set up wireless on an HP DV6226us that had vista on it. I works great. No problems what so ever. Wireless card 
Broadcom 4311 in a laptop
Dev

---

### Post by DirtyBerty on 2007-02-22
Thank you very much :) 

I have finally got my Gateway mx3220b to connect having dl driver from Gateway UK and applying the blacklist ndiswarapper fix

I was starting to lose faith in the while thing!

Now if only my sound would work :confused:

---

### Post by thirstygerry on 2007-02-23
It worked for me
Even though I got "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)"

A couple of days ago I used
[http://www.ubuntuforums.org/showthread.php?t=327524](http://www.ubuntuforums.org/showthread.php?t=327524)
this walkthrough and It worked for my wpc54G v3.1

Then I had to reïnstall Ubuntu and it no longer worked, so I tried this and here I am posting wireless :)

---

### Post by thehodgie on 2007-02-24
I hate to sound like every one else on this thread but, thank you very much for writing a great guide. I spent _days_ upon _days_ trying to figure out how to get my stupid wireless card to work and it only took me 10 minutes with your guide.

One tiny hiccup I had was that I am on Kubuntu (I don't know how much of a difference that makes) and I attempted to connect to my network using the wireless assistant that comes with it and it showed me the networks once, tried to connect, failed and then the networks wouldn't appear again. SO I tried the WifiRadar and it worked, I just had to wait.

Again, thank you a lot for this wonderful guide!

---

### Post by swedish cook on 2007-02-25
I got Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) back, but worked first time, Mac Mini Power PC G4.

Great thanks.

---

### Post by DarkN00b on 2007-02-25
I just used this HOWTO on Edgy and I must say it worked perfectly. I am posting this through my Linksys WPC54G ver.3 (BCM4318 ) CARD NOW. :D

Here's the proof:
```
eth1      IEEE 802.11b/g  ESSID:"*****"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:49:22:3B:06   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=45/100  Signal level=-61 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Thanks for the great HOWTO!

---

### Post by AccidenT on 2007-02-25
This HOWTO worked great for me in Edgy with a Linksys WMP54GS. Using the bcmwl5.sys from my windows partition didn't work, but using the provided wl_apsta.o file worked like a charm.

---

### Post by DarkN00b on 2007-02-25
Most Excellent! [img]http://smileys.smileycentral.com/cat/36/36_1_75.gif[/img]

Glad you got it working.

---

### Post by kyuuketsuki47 on 2007-02-26
Well I must give my thanks. I tried everything before this. The windows wireless driver adapter and everything. Yours worked so easily with only the wireless assistant that was included in the Kubuntu Edgy install. And I think this even has more range than my windows driver gives me for some reason...

---

### Post by unclernie on 2007-02-28
This worked for me.
  Machine is an emachines M6810 laptop with Broadcom BCM4306 mini-PCI card
I found two versions of the bcmwl5.sys driver on the XP partition, and successfully extracted the firmware from the later one, version 3.100.46.0
I'm using Kubuntu Feisty herd 4

---

### Post by GrahamA on 2007-03-02
It's sort of half-worked for me. The driver loads no problems and I can scan for other networks and stuff. But I'm having trouble actually getting connected to an AP and running DHCP. Could anyone give me any suggestions as to what could cause this?

---

### Post by trubblemaker on 2007-03-02
depends on how you are trying to connect to the ap

Manually from commandline:

```

sudo iwlist scan

```
give you a list of essid's then and what interface to use: most often eth1
```

sudo iwconfig eth1 essid <your essid>
sudo dhclient eth1

```

if you are using 
```

sudo ifup eth1

```
you need to have your /etc/network/interfaces file setup properly otherwise it won't work.  The above mentioned method doesn't rely on /etc/network/interfaces.  if you want to know how to setup your /etc/network/interfaces file you can 'man interfaces' or post back here and I'm sure people will help.

Sorry I know these aren't nice GUI commands but for troubleshooting commandline rules.  Remeber no output often means everything is working fine.

---

### Post by ginoe on 2007-03-04
thank you, thank you, thank you!!!

i followed these directions to the letter and am now wireless!

this rocks! :guitar: 

now, if i can only get my laptop battery to last more than 15mins...   :(

---

### Post by 22350 on 2007-03-04
i have one of those airforce one cards and have tried everything, to no avail.

this is what i got:

mateo@mateo-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:03:88:3A  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe03:883a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2282310 (2.1 MiB)  TX bytes:301268 (294.2 KiB)

eth1      Link encap:Ethernet  HWaddr 00:90:4B:D7:A7:BA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Memory:dfdfe000-dfe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69876 (68.2 KiB)  TX bytes:69876 (68.2 KiB)

mateo@mateo-laptop:~$ modprobe bcm43xx
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.17-10-generic/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
WARNING: Error inserting ieee80211 (/lib/modules/2.6.17-10-generic/kernel/net/ieee80211/ieee80211.ko): Operation not permitted
WARNING: Error inserting ieee80211softmac (/lib/modules/2.6.17-10-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko): Operation not permitted
FATAL: Error inserting bcm43xx (/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko): Operation not permitted
mateo@mateo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mateo@mateo-laptop:~$

---

### Post by 22350 on 2007-03-04
and this:

mateo@mateo-laptop:~$ sudo iwconfig eth1 essid paul
mateo@mateo-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:d7:a7:ba
Sending on   LPF/eth1/00:90:4b:d7:a7:ba
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
mateo@mateo-laptop:~$

---

### Post by memilanuk on 2007-03-04
I had to click 'No', as the guide did not work straight up for me.  The part about bcm43xx-fwcutter did, so I suppose one could argue the point.  As it was, since the Linksys WMP54G wireless card (BCM4318 AirForce One chipset) is the *_only_* network connection I have on this machine, getting bcm43xx-fwcutter installed was a bit of a rodeo for me.  I'm just getting started again after a loooong hiatus (4-5 years) from Linux.  Some of the commands weren't completely unfamiliar, but having to go look in one thread or another on how to find single .deb files in the repository, d/l them to a USB drive (along w/ the .0 file), transfer them across, read up on how to manually install a single deb file (and pray there were no dependencies to go hunting down), etc. took a bit of a leap of faith after such a long break.  For someone completely unfamiliar w/ Linux... who knows.  At any rate, it did work, albeit w/ a couple detours.  I'm typing this from Firefox inside Ubuntu 'Edgy' right now!

Thanks,

Monte

---

### Post by countryparson on 2007-03-06
Thank you so much!  This works perfectly on my Gateway MX3225.

---

### Post by acconrad on 2007-03-07
I honestly have no idea what is wrong or where to begin...I have the exact same wireless card as nick and I have a Dell Latitude D800...I followed the instructions to a T and nothing is working...tell me what i need to post on this board and i'll post it so we can diagnose what my problem is please!

---

### Post by unclernie on 2007-03-07
Testing Feisty Herd 5:  Worked for me, both on herd 4 and herd 5.  Didn't have to go past step 4, and knetworkmanager popped up and told me it had a connection!
  System is emachines M6810 AMD64 with Broadcom bcm4306 (rev 03). System is dual-boot, so I extracted the firmware from the bcmwl5.sys I found on the WinXP partition (version 3.100.46.0)

---

### Post by fusionisthefuture on 2007-03-07
well i was thrilled when i first tried this tutorial and it worked for my broadcom 4310 a/g/b network card,  i tried it and it started working with my home unencrypted network, and then the next day i went to school, and messed around with my xorg.conf file a bunch.  when i was at school, before i messed with ANYTHING i noticed that it couldnt see the main network in the school (but i could see an ad-hoc network, just couldnt connect to it), which was an unencrypted b network.  so then i messed with my xorg.conf file which im told couldnt have aything to do with my wireless, and then i went home, and when i got home i couldnt connect or see my home network either.  yesterday i went back to school, and now i cant even see the ad-hoc network at school.  now today when i booted my computer up, i cant even see eth1, my wireless network in system>administration>network?!?!?!  its changing all on its own  it seems.  whats going on?
thanks
-arne

---

### Post by nadarockyraccoon on 2007-03-07
though it would seem that this worked just fine as my card turned on, it does not consistently connect and when it does things tend to be very slow (1000 B/s slow) and as i said that is when it connects. I have tried every possible combination of wireless management that i could find including only the preloaded wireless tools alone, different routers, different firmware, fresh installs    and so forth. Months ago to make this card work I found a link in these forums that just made it work, but I cna't find it anymore. I've been using ubuntu since the Dapper Drake release and would hate to have to revert back to windows permantly as i have now, but if it doesn't work and i can't make then that might happen. Any suggestions, and please don't tell me to use the driver off the cd with ndiswrapper, i did that, and every other driver that i thought could possably work, it doesn't work

---

### Post by garomly on 2007-03-07
Thank you, Thank you, Thank you! After 3 weeks, 4 distros and countless reinstallations, my wireless is finally working, just as i was about to give up on entering the Linux world.

---

### Post by Jamina1 on 2007-03-08
This worked great on my Dell Inspiron 9100

UNFORTUNATELY, every time I restart, I have to reinitialize the card with

```
sudo modprobe bcm43xx
```

Did I forget a step?

---

### Post by marlobello on 2007-03-09
It worked on my BCM4318 with FF Herd 5, but I had no luck with 6.06! Granted my landlords network is wide open so I can't vouch for any encryption methods.

Thank you for this post. I have been through 5 distros (if you count different releases of openSuSE and Ubuntu) and 2 network cards but finally I have network on my desktop.

---

### Post by Pazuzu on 2007-03-09
In a compleatly plutonic way of course. Thank you very much, your guide was extreamly helpful. In fact i dont think there is anyway it could be anymore helpful considring that it fixed my problem. Thanks again.:KS :KS :KS :KS :KS 

PS: I am using a Linksys WPC54GS card, even though ubuntu reconized the card immediatly, this was all i needed.

---

### Post by venom9122 on 2007-03-09
This worked like a charm, except the connection is REALLY REALLY SLOW!  I'm limited to about 10-20 kb/sec, on my windows partition i get 150-200, am i just gonna have to deal with it, or what?

---

### Post by siciliancasanova on 2007-03-09
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
Cannot open input file /home/anthony/Desktop/wl_apsta.o

I am getting this for the response when I get to this point.  My machine said it already had  fwcutter on it, so I ran that line.  Didn't work, uninstalled it and reinstalled it.  I'm completely new to ubuntu so I'm not sure exactly what I'm looking at or where the problem lies.  

I do have a broadcom (linksyswmp54gs) and the system is detecting it, just need to get the firmware installed on it.

---

### Post by visualnoise on 2007-03-11
I have one of those tricky BCM4318 [AirForce One 54g] 802.11g cards, but this worked perfectly for me.  The only extra step I took was to add an entry for eth1 in /etc/network/interfaces.  I'm no guru, so I don't know where/how I could have configured the wlan0 interface properly, but w/e.  I'm using it now to post this message!  Thanks very much.

(I'm using Edgy i386 6.10 on an HP L2000 laptop, fyi.)

---

### Post by bcorcoran on 2007-03-12
Followed to step 4, and it just started working.. (connected to a wireless router w/ radio off and 128bit hex wep ... so if something wasn't working I'm pretty sure I wouldn't have gotten this far :)

I am on a Acer Ferrari 4006WLMi, with the BCM4318 Airforce card. I used the synaptics package manager method, and it asked to fetch the firmware, so I did, and it just started working. I didn't even have to do ifconfig or anything... SSID's started to show up under the network icon in the top right, and I added my network (radio off SSID like I said above).

One thing that might be of note: I am using Feisty Fawn Herd 5, so maybe something has changed... but I didn't have any problems whatsoever.

Good luck to those with the BCM4318, and thanks for the how-to!

---

### Post by GS2 on 2007-03-13
Worked a treat with a WL12-PCI-G54 Buffalo card on Feisty - used the firmware etc from this link:

[ftp://ftp.dell.com/network/R81433.EXE](ftp://ftp.dell.com/network/R81433.EXE)
(thanks to the sourceforge ndiswrapper list for that)

A great how-to thank you :)

---

### Post by indica on 2007-03-15
ok seriously, i can't get my wifi to work
i'm running an ibook g4 800 12" airport extreme and edgy.  i've tried this, and several other random howtos and people's suggestions and i can't get this to work.  i don't have osx so i can't get the driver there and i don't want to have to buy it and reinstall it when i don't want to use it anyway. i've tried both network manager and wifi-radar.  i could see my network, and another in my building with wifi radar where networkmanager wouldn't even give me the option to connect to wifi. i've followed this howto step by step, several times, on dapper and edgy. i've tried it with clean installs several times
i can't figure it out, i'm not getting any errors.  it simply doesn't connect, and if i have to reinstall many more times i'm going to just give up and give osx a try  :( :mad: 
does anyone have any suggestions? please?

---

### Post by trubblemaker on 2007-03-15
remove wifi radara and then try these steps, it's a great program but I seem to recall it doesn't play nice with ndiswrapper

---

### Post by indica on 2007-03-15
i've already tried it without wifi-radar.  networkmanager doesn't even give me the option to connect to a wireless network.  wifi radar sees it but doesn't connect or get an ip.   i'm not using ndiswrapper.  i can ping my connection, it responds.  i just can't figure it out

---

### Post by indica on 2007-03-15
ok so under iwconfig i'm getting access point invalid       

any guesses?

---

### Post by deeemster on 2007-03-15
A huge thanks for putting the HowTo together.  This one worked perfectly first try.   Also I am currently using Feisty.  Not sure if anybody had posted about that yet (74 pages of posts).  Does anybody now if there is a way to get 54Mb speeds instead of just 11?  I'll due some further searching, but am reluctant to "mess" around because I don't want to lose my connection.  :)

---

### Post by fusionisthefuture on 2007-03-16
> **venom9122 said:**
> This worked like a charm, except the connection is REALLY REALLY SLOW!  I'm limited to about 10-20 kb/sec, on my windows partition i get 150-200, am i just gonna have to deal with it, or what?

i have this same problem, of course i dont get rates like that to start with, but its gone from like 60 kB/s to 20ish.  its quite annoying, especially cuz this is an a/g/b capable card, (4310) and for some reason i also cant connect to the unsecured network at my school either.  i cant even see it if i do iwlist eth0 scan, but i can on my windows partition.  
thanks
-arne

---

### Post by trubblemaker on 2007-03-16
> **indica said:**
> ok so under iwconfig i'm getting access point invalid       

any guesses?



yeah why don't you try, 
(assuming that your wireless interface is eth1)
```
 
sudo iwconfig eth1 ap any

```
check that it's no longer got invalid.....
```

iwconfig

```
if this doesn't fix it. try unloading the module and reloading, rebooting, dual booting into windows, user wireless then come back.
(Your driver is in an invlaid state. and we need to "reset" it.)
then try a manual connect to the ap
```

iwlist scan # gets list of essid's
sudo iwconfig eth1 essid <fav-essid>
sudo dhclient eth1

```
at this point please don't use "ifup". it reads from the /etc/network/interfaces file and will ignore the essid that you use just set above. (plus if interfaces file isn't set up correctly it will cause some errors.)

hope this helps, please post output back if this doesn't fix it.

---

### Post by indica on 2007-03-16
i wasn't running a dual boot, but i'm reinstalling mac os now so i can dual boot. it didn't look like it worked before i screwed with my ethernet and lost my whole network for a few hours.   i'll let you know what the output is once i get edgy reinstalled

---

### Post by indica on 2007-03-17
ok, i got it to work, YAY!:KS  fresh install of edgy, driver from macos partition, ran the whole nickm howto, installed networkmanager, followed your instructions above (didn't work) but while i was screwing around before i could get around to copying the output i came across this 
[http://www.ubuntuforums.org/showthread.php?t=341357]("http://www.ubuntuforums.org/showthread.php?t=341357")
which worked, go figure

---

### Post by ikehack on 2007-03-17
I had the AirForce 54g, and surprisingly it worked :)

---

### Post by peterhs on 2007-03-18
Hey, I am having problems too.  I have a bcm4311 card

I have tried everything, and the problem seems to be locked up in my pci bridge.  After I install the system, LinuxMint 2.2, the card is seen, after I boot up the second time, the card disappears, I have reinstalled the system 4x now, it is frustrating.  

after install and first attempt with [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#head-1b040ccda848cfa35bf7a805c8b817d00f7df33a](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#head-1b040ccda848cfa35bf7a805c8b817d00f7df33a)

iwconfig :
l0 no wireless extensions

eth0 no wireless extensions

wlan0
IEEE 802.11b  ESSID: off/any
          Mode:Managed  Frequency: 2.412 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s
          RTS thr:2432 B   Fragment thr: 2432 B
          Power Management: off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

after rebooting the system

iwconfig :
l0   no wireless extensions.

eth0  no wireless extensions

(anytime)
after typing lspci :
05:00.0 Network Controller: **Broadcom Corporation Unknown  Device 4311 (rev 01)**
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37

I also do not get any sound, if that helps any.

When i type ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

Any help is greatly appreciated

Thanks ahead of time.

---

### Post by HunkieChan on 2007-03-18
01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

^ i have this modem, and i followed the instruction and it worked for me thanks alot

---

### Post by dan13l on 2007-03-19
I've got a BT Voyager 1065 PCMCIA card, and the guide worked brilliantly.

Interestingly, I was able to skip several steps:

Step two wasn't required, as running "sudo apt-get install bcm43xx-fwcutter" offered to download the driver for me. 

Subsequent steps could also be skipped - fwcutter seemed to install all the drivers in the right place for me anyway.

With that done, I ran "sudo apt-get install network-manager-gnome" and the card's lights came on!

The last step was to select which network to join using the icon at the top right, and all was good.

I'm running FF Herd 5 - the official release wouldn't even boot on my laptop.

Awesome guide, and thanks to you I'm now reading to have a play with Ubuntu.

---

### Post by Feenix3k on 2007-03-20
I got as far as step 5 and locked up the computer. Im a newbe, so I must have hit something wrong. But it was doing good till then. Will try it again

---

### Post by Cesium on 2007-03-20
[CENTER]```
sudo apt-get install bcm43xx-fwcutter
```[/CENTER]



When I try this step I get the error "Couldn't find package bcm43xx-fwcutter"

Any thoughts? I'm trying to do this on Edgy. Thanks!

---

### Post by damu on 2007-03-22
Thanks for this how to. I thought it was not working as I could see some wireless network once and then nothing. I did again some of the steps of the how to , mainly copying the driver files in the upgraded kernel folder.

Now, I can see from time to time one or another of the wireless network of neighbors, but  mine has never been detected!

It seems there is a problem with the detection. As I am writing this thread, there are no more wireless network available at ll, which is most of the time the case.

My 3Com wireless modem/router is just next to this laptop "compaq nx6325", and 4 others computers are wirelessly connected to this network (including 2 ubuntus), all of them being much further to the modem than this laptop.

The broadcom card in this laptop is the bcm4310.

I prepare it for a friend, and kept her laptop for few days now, trying to sort out this wireless issue. 
Should I consider trying the driver of broadcom? If so, how do I remove the files already installed?

Any help/suggestion very much appreciated.

---

### Post by Feenix3k on 2007-03-22
This set up works to a point. I see the networks around me. I can tag the DHCP server. But I don't recieve DHCP offers. My card read out from the lspci -vv command is

:02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
        Subsystem: Dell Truemobile 1400
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 193
        Region 0: Memory at faffc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

---

### Post by Crazytom on 2007-03-24
Thanks for the Guide.  I've used it twice now.  This time it worked great.  I don't know yet if it will still work when i reboot but i guess we'll see.  also I just used it for fiesty and it worked great after i uninstalled ndiswrapper and did modprobe bcm43xx
thanks again

---

### Post by zorkerz on 2007-03-24
scratch that.  Its what i get for not reading the forum well enough

---

### Post by handaxe on 2007-03-25
> **Cesium said:**
> [CENTER]```
sudo apt-get install bcm43xx-fwcutter
```[/CENTER]



When I try this step I get the error "Couldn't find package bcm43xx-fwcutter"

Any thoughts? I'm trying to do this on Edgy. Thanks!

Use the universe repos - that's where the proggie resides.

HA

---

### Post by jim.guenzel on 2007-03-25
Worked perfectly - I stopped at step 4 as the network montor showed activity!
Thank you!
Jim

---

### Post by chadwicktr on 2007-03-26
thanks! finally got my wireless working :)

---

### Post by TigPT on 2007-03-26
finally my broadcom 4318 works.. thks a lot.. :)

---

### Post by Feenix3k on 2007-03-26
I have a dell Inspiron 5150, the internal card is ID bcm4309. It is listed someplace as unstable.

But I got my bcm4309 working using the bcm4318 directions found Here

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by BinaryMadman on 2007-03-27
Why does it not allow me to enable my BCM4318 card?  Under System-->Administration-->Networking, it shows my wireless connection with a minus sign and says 'this network interface is not configured'.  I go to properties and check 'Enable this connection' then press enter and nothing happens.  I go back to properties and the box is unchecked.  Do I have to enter a ESSID?  If so...what is it and what do I write? X]

Edit: Hmm...I think it's working but I have no clue if it was the ndiswrapper or the cutter thing that made it work.  I see a listing of available wireless networks around me.  I can't test it until I get on campus though (through their wifi).

---

### Post by des4ij on 2007-03-31
Hey,

I previously installed ubuntu and jsut came back to it. My wireless card works fine with the original network manager, but for it I have to input the SSID myself manually each time. So then I installed network-manager-gnome, but it only shows me a wired option. Any ideas as to what I can do? My internet works I just need network manager to somehow work with my eth1 connection.

---

### Post by acmarfil31 on 2007-03-31
At last, thank you for posting this.  Never been better without wireless connection, and never been better without this community.

---

### Post by Athanasius on 2007-03-31
None of this worked for me.  My wireless network card was never recognized until I reformatted and installed Feisty Beta and then I installed bcmxx.fwcutter then ndiswrapper and the driver from the ndis wiki.  All of that followed by a restart and now all is good.. well as good as it gets anyways

---

### Post by des4ij on 2007-03-31
> **des4ij said:**
> Hey,

I previously installed ubuntu and jsut came back to it. My wireless card works fine with the original network manager, but for it I have to input the SSID myself manually each time. So then I installed network-manager-gnome, but it only shows me a wired option. Any ideas as to what I can do? My internet works I just need network manager to somehow work with my eth1 connection.

Hey I jsut read through the thred and tried to uncheck it from networking, then rebooting and it still didnt work. Any ideas?

---

### Post by des4ij on 2007-03-31
got it working... u dont disable the wireless adapter but just the configure apparently... I dont think thats how its suppose to be but it worked so im happy :)

---

### Post by dtcwee on 2007-03-31
Dell Inspiron 1300 with the dreaded Dell 1370 card (4318 rev 2 chipset). Ubuntu Edgy.

The following guide complemented the one you are reading now:
[URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy"]
https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy[/URL]

Cafuego's drivers, I think, made the difference.

Notes:
[LIST]
[*]Do this after a fresh install, before you do your updates.
[*]ESSID can be case sensitive
[*]Thoroughly disable ndiswrapper (follow the guides)
[/LIST]

Working after 1 day. I hope you have the same good luck.

---

### Post by Puzzled_Pete on 2007-04-01
Thanks a lot.  It worked for me on a Dell Inspiron 1300 after a bit of a faff blacklisting ndiswrapper utils, and then following the advice given by crag277 in post no 1105667.  

:) :) :)

---

### Post by Juxta on 2007-04-03
> **nickm said:**
> 

It seems that if you get the following string back: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) that this guide is VERY unlikly to work for you although it does sometimes, dont ask me why, but basically every "no" vote and "this didnt work for me" post comes from a BCM4318 user....

I have the card above mentioned. However, when I turned on my notebook just now, I could connect to my wireless! Thank you so much for this amazing guide.

Greetings from sunny Germany,
Juxta.

---

### Post by huzelj on 2007-04-04
Hey,

I followed the guide and everything seemed to work perfectly, however I can not connect to any wireless network. I can see them all listed with network manager or wifiradar, but when I connect it tells me it can't get the IP address, even with my own router.

I have typed modprobe bcm43xx but nothing happens after I hit enter, I am not sure what the outcome of that command is supposed to be.

When I type iwconfig this is what I get, it is still showing the last network I tried to connect to before plugging back in the network cable.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"SAIT"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I am running a Dell D400, its BCM4306 chipset,

Any help would be greatly appreciated!

Thanks,

Jake

---

### Post by king minger on 2007-04-05
Thank you for this **SUPERB** HOWTO :)
I suspected i was going to have issues getting the wireless to work on an ex-work laptop, but this saw me through.

details:
Dell latitude D600 
Pentium M 1.4
Broadcom BCM4309 (dell1450) mini PCI card

fresh feisty beta install(after updates, the wireless was the first thing sorted out)
the dell windows driver installed on the XP partition didn't work with fwcutter but one of the ones indicated in the HOWTO did (can't be specific as i can't remember what the last one was as some of it was getting the network manager to play as well...)

so once again thanks loads!
Now i just need to get my ATI mobile 9000 running......
Al

---

### Post by ComputerGuru on 2007-04-06
An exact great tutorial for the exact card that you used!

Works great now! THX so much:D

---

### Post by digitalwired on 2007-04-06
Worked perfectly on my Dell Inspiron 8600 on 7.4

---

### Post by thisisnotkathy on 2007-04-07
This worked fabulously on my HP dv1207 laptop, using a Broadcom BCM4309 card. I had tried ndiswrapper and it didn't work, so I was skeptical for this method. Worked great! I should have tried this first...

Thanks so much! These forums keep a linux n00b like me from getting discouraged and returning to windows!
:)

---

### Post by SuneC on 2007-04-11
Hi!

I'm a Linux newbie - just installed Ubuntu 6.10 today - and have been struggling with getting my wireless connection to work. It is the right wireless card, even the one that the author of this thread owns, and I've followed all steps, multiple times, all with success until the point of rebooting, number 6.

When the system has rebooted and I log on, I look at the top-left of the screen, where the clock is located and I see 2 black screens and an exclamation mark (!) in front. I hover my mouse and receives the message "No network connection", I rightclick and see a tick where "Enable Networking" stands.

Before starting to mess with this, I could also find my wireless card in System>Administration>Networking, but now it's simply gone. Before trying this guide I had to tried to modify the settings of the wireless card in Networking, but with no results at all.

Now my question is: What have I done wrong?
I have followed the guide point-by-point, doublechecking, and even done the guide multiple times, with still the same frustrating result.

After speculating a bit, my thoughts goes in the direction of my driver. Can there be anything wrong with it? Maybe I downloaded a too old one? To be honest, I have absolutely no idea.

I really do hope that someone will be able to aid me in this, because I'm starting to like Ubuntu already, and it will be sad if I just have to remove it again so quickly. I have no intention on using this without my wireless internet, since having a cable through the half house is not really a nice solution.


Sincerely,
Sune C

---

### Post by herrison on 2007-04-11
Thank you. Sorted me out (Edubuntu, Dell Latitude Broadcom wireless).

Pity the Ubuntu documentation doesn't detail the missing piece between the driver (supplied with kernel) and actual connectivity.

---

### Post by trubblemaker on 2007-04-11
Do you have a question about it or are you just stating a need for documentation? 
If you have a question post and we'll try and help...
In terms of documentation it is documented, on wiki's and their is a method to those included in documentation, but I can't remember how to nominate it...

---

### Post by MikeBee on 2007-04-14
Suggest that the Wiki doc gets updated with a Feisty method.

On release this thread may get flooded with 'the wiki doesn't work' posts?

---

### Post by n00bWillingToLearn on 2007-04-16
> **MikeBee said:**
> Suggest that the Wiki doc gets updated with a Feisty method.

On release this thread may get flooded with 'the wiki doesn't work' posts?
In Feisty all you need to do is install the bcm43xxfwcutter package , when you do this it will ask you if you want to have it automatically install the firmware for your card, ( if in synaptic you may need to show the console output to see this message ) choose yes and either reboot or run "sudo modprobe bcm43xx"

I will add a page in the wiki for Feisty

---

### Post by Strelz on 2007-04-17
I've been chugging my way through this post, and I apologize if the solution to my problem is here and i didn't find it.  I followed the original instructions to try to install wireless on my Inspiron 1150 which is running 6.10.  I used the wi_apsta.o driver.  I ran bcm43xx-fwcutter as instructed.

Here's what I get:

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:12:17:08:77:DE   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=45/100  Signal level=-80 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


looks almost ok, or does it?

and I also get:

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:69:39:5B  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe69:395b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29938 (29.2 KiB)  TX bytes:21701 (21.1 KiB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:0B:7D:12:F2:9E  
          inet6 addr: fe80::20b:7dff:fe12:f29e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28993 (28.3 KiB)  TX bytes:21856 (21.3 KiB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

My linksys router is set to defaults and worked fine when this Inspiron used to be Windows.  So I know it works.  Its SSID is lynksys and I put that in the wireless configuration field where it asked for ESSID.  I loaded Gnome network manager, and at first it listed a wireless network.  When I rebooted that went away.  I tried modprobe bcm43xx and got a prompt back, rebooted, but no change.  Can anyone tell what I am doing wrong from what I am providing, or if not, tell me what additional information I can give so they can get me going?  Thanks very much.

---

### Post by steveyeager on 2007-04-18
This post got my wireless working, but i cannot see my router.  I have two other computers running ubuntu that use different wireless devices that connect to my wireless router just fine.  I see all my neighbor's routers, but not mine.   Any suggestions?

---

### Post by Strelz on 2007-04-20
Here is the solution to the post I made a few days ago on this page.

The post seems to show that all is ok, yet it didn't work.  I had followed the instructions of NickM to the letter.  The conclusion is that NickM instructions work perfectly for a Dell Inspiron 1150.  I am embarrassed to say that the problem was with the settings in my router.  I thought it required a password, and it didn't.  When I got Feisty, this was a big help because of the additional information it provided.  That is, with 6.10, network manager did not see the eth1 interface.  But with 7.04, it did.   This lead me to go back and re-examine the router.

In conclusion, if you have a Dell Inspiron 1150 and you follow NickM's instructions it will work.  I used the wl-ap... driver that he recommended.  As he said, you don't need to go past his instruction 4.  And it works a lot better in 7.04 because you get more information.

This is surely a great community when you can find all this information and get all your problems solved!

---

### Post by Ripfox on 2007-04-20
bcm43xxfwcutter sucks over here...I have a bcm4311 internal and the bcm43xxfwcutter method gives me like, dial up speed?? I finally used this [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice#head-f744e28e6c78eb83d22be77819b130016a8e51f3](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice#head-f744e28e6c78eb83d22be77819b130016a8e51f3) and now I get 6mb on a speed test. Ndiswrapper works WAY better here.

---

### Post by kryton9 on 2007-04-21
Thanks, with your great instructions it worked and I finally have wireless on my gateway notebook, thanks again!!

---

### Post by vince1027 on 2007-04-21
My Broadcom version is this:
```

03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

If you have a silimar version as I do, there is a very simple way to install the driver using ndiswrapper.

What I did was:
1.) make sure you have the right sources, update you sources list. I used the list of sources found in ubuntuguide.org

2.) install ndiswrapper and ndisgtk. This can be easily done via synaptic so dont worry about the command.

3.) get your .inf driver. this is a bit weird cause I tried other drivers and it did not work. so you need to have the official .inf driver of your device.

4.) run ndisgtk.
```
$ sudo ndisgtk
```

5.) choose to install your driver and point the location of the .inf file.

6.) check to see if the wi-fi light is on. If it is then you are good. If not then this might not be the solution for you.

7.) configure the network options.

then, rejoice cause you did it in a very simple way.

---

### Post by SiRusty on 2007-04-23
This guide worked very well for me but I had to compile a 2.6.21.rc7 kernel to be able to max out my wireless speeds (I get about 130 kb/s with a wired connection) and was getting only ~20kb/s before upgrading the kernel. So if you are having very slow wireless speeds with the base install of feisty, I suggest you upgrade your kernel to at least 2.6.21.rc6. 

I have a compaq v6000 laptop with the dell wireless 1390 mini-pci card.

---

### Post by CalcProgrammer1 on 2007-04-23
This worked perfectly!  I have a Buffalo WLI-CB-G54S based on the Broadcom chipset that you said wouldn't work!  It works perfectly, but now that Ethernet card I bought because my wireless one wouldn't work was only useful for a day lol. :D :D :D

---

### Post by Wizkizz@hotmail.com on 2007-04-25
Thank you so much. I LOVE UBUNTU!!!!!!

---

### Post by ScarySquirrel on 2007-04-26
From now on I will use this guide as a template for making sets of instructions for buggy humans.   I especially admire the "human exception handling" the author employs.:KS

---

### Post by Darko8472 on 2007-04-26
Would these directions work with Feisty as well?

Wireless is the ony thing stopping me from going full Linux on my Dell. Everything else works a treat, I can get 915resolution to work (it's an Inspiron 1300), just not the wireless :(

---

### Post by CalcProgrammer1 on 2007-04-26
I'm using it on Feisty just fine (I installed it on Edgy, then I upgraded to Feisty, but it should still work).

---

### Post by Darko8472 on 2007-04-26
:( Seems it doesn't want to. I have the 4318 card that people are having problems with.

The wierd thing is, it's picking up the fact that my network is THERE... it's just not connecting to it or at least isn't using it for any network traffic.

---

### Post by Sokraates on 2007-04-27
> **Darko8472 said:**
> :( Seems it doesn't want to. I have the 4318 card that people are having problems with.

The wierd thing is, it's picking up the fact that my network is THERE... it's just not connecting to it or at least isn't using it for any network traffic.

Does the network use WPA-encryption? If yes, try WEP and see, if it works. If this doesn't work, try Ndiswrapper instead of the bcm43xx-driver.

Here are two How-Tos (they are more or less the same, but each explains different things better):

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
[http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)

---

### Post by Darko8472 on 2007-04-27
Yes, unfortunately it's using WPA-PSK. And if I change it I'll have some rather annoyed housemates...

I'll try the How-To's and see if they work :) Thanks.

---

### Post by Dieter1967 on 2007-04-28
So far, so good.  My connection isn't exactly the strongest, but it IS working.

I have a Dell Latitude D610 with the Broadcom 4813 chipset on the wireless card.  It's been giving me fits for a week, but I THINK it's going to behave now.

Thanks for the info!

---

### Post by Aaragon on 2007-04-28
Great tutorial! I'm running I had minimal success with ndiswrapper running in ubuntu . Wanted to try Kubuntu anyway so reformated and following your directions i was up in about 2 min...awesome. Crossing my fingers but I hopeful it will continue to work. BTW, my laptop is a Latitude D420 with a integrated Dell 1390 Wireless mini-card.

I thought for sure Id have to use my bcmw15 firmware but it seems that is no the case. ;) Again, thanks for a great tut!

Aaragon

---

### Post by keefer on 2007-04-28
NickM, I owe ya somehow boss.  Worked great, was very easy to follow.  I've got VERY limited experience with Linux systems, and felt confident going through this guide.  Worked on FF for me.  Thanks!

...kkm

---

### Post by Kazol on 2007-04-29
I tried doing this procedure and the LEDs turned on; however, I still could not connect, although I am a step closer. I enabled it from the network tool but it said something like "No network found", even though I put the WAP right next to the antenna. The "link" LED is always on, and when I enable it, the "activity" link lights up, but never blinks. I tried rebooting and enabling it through the system networking menu, but the problem persists.

---

### Post by Kazol on 2007-04-29
Never mind, I figured it out. This new icon did not report the network status correctly. I enabled the wifi card in this new icon and network manager, removed the new icon, and added a system network status icon in the panel. Thanks for the drivers! My wifi card (finally) works now!

---

### Post by kncarlsen on 2007-04-30
For the first time my Broadcom card 43xx is just working without ndiswrapper.  Thanx!

---

### Post by x.1.alvin on 2007-05-04
Nickm, you rock! I was able to get my linksys wifi card working at last by following your instructions. I previously tried a lot of methods, but yours was the one that worked. You da man!!!

---

### Post by Jorge32 on 2007-05-05
I have an nx6325 HP Compaq computher and the wireless card is the following:
Broadcom Corporation Dell Wireless 1390 WLAN Mini-PC I Card


and I've found that the nx6325 usually comes with a bcm card or something like that...


but anyway I can't connect!

---

### Post by jangeles on 2007-05-06
Just wanted to say i was VERY happy to find this post, and even happier it worked for me.

I've installed kubuntu a number of times and always have a nightmare trying to get my wireless working with the ndiswrapper method. My router is on the other side of my flat and i don't have a long LAN cable, so i have to stretch all the wires to breaking point to connect directly. 

When i found this article i thought i'd still have to do that, but i downloaded the recommended driver, and then googled fwcutter and downloaded the .deb onto my laptop. Then i put the 2 files on a USB key and transfered to my desktop. All worked straight away!

Very happy, thank you! Great solution.

---

### Post by Nasiom on 2007-05-07
Hi,

just to let you know that a new Mac Pro (Quad Zeon) has a 4328 card...

lspci | grep Broadcom\ Corporation

returns:

12:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)

so none of these seems to be working.  However Wifi-radar detects my access point as a G network (That is good) but there is no way to make Ubuntu using this connection.

Thanks

Nasiom

---

### Post by megabenman on 2007-05-07
I have the Broadcom Corporation BCM4318, and I did all the steps (except a couple, and I changed a few, since I'm running Kubuntu).  Of course, my internet still didn't work.  I tried to use the first link that the tutorial said to do if you have the BCM4318 card, but everytime I type it in (I replaced gedit with Kate of course).  Konsole spit out a bunch of error messages, but it still opened Kate.  However, everytime I try to edit blacklist and try to add "blacklist ndiswrapper" when I save it it tells me that I don't have permission or disk space.  What is the problem, and what can I do to fix this? (please remember I'm on PPC Kubuntu, so not anything that's Intel or AMD only, please :) )  I'll try to post the error message.

---

### Post by megabenman on 2007-05-07
Ok, I've gotten blacklist ndiswrapper in the file thanks to the kdesu command.  But now, it still isn't working!  Every time I try to connect to the network it stops at 28 % (configuring device).  Only a couple times it reached 57% (configuring IP address... I think).  I can't see what's wrong.  Here is what I've done (remember I'm using Kubuntu, not Ubuntu).

1.  Updated repositories.
2.  Ran sudo apt-get install bcm43xx-fwcutter with success.
3.  Downloaded the wl_apsta.o file to my desktop.
4.  Ran sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o with success.
5.  Ran sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` -/Desktop/wl_apsta.o with success.
6.  Ran modrpboe bcm43xx.
7.  Ran sudo ifconfig eth1 up.

Nothing seems to work.  Any suggestions?

---

### Post by ongbk619 on 2007-05-08
Thanks so much for the guide.  I got my wireless card to work by following your instructions.

My wireless card:
Linksys WRT54G
Broadcom Corporation
BCM4306 802.11 b/g Wireless LAN

Thanks again!

-b

---

### Post by pospam on 2007-05-08
> **jangeles said:**
> Just wanted to say i was VERY happy to find this post, and even happier it worked for me.

I've installed kubuntu a number of times and always have a nightmare trying to get my wireless working with the ndiswrapper method. My router is on the other side of my flat and i don't have a long LAN cable, so i have to stretch all the wires to breaking point to connect directly. 

When i found this article i thought i'd still have to do that, but i downloaded the recommended driver, and then googled fwcutter and downloaded the .deb onto my laptop. Then i put the 2 files on a USB key and transfered to my desktop. All worked straight away!

Very happy, thank you! Great solution.

Hi jangeles and all in the forum:
I just installed kubuntu feisty yesterday I cannot use my wifi. The problem I have is that I only have a wireless connection and cannot use a ethernet connection. From your post I am guessing that I could download the driver and the fwcutter deb from the internet in my windows partition and then write copy then in my desktop in my linux partition and then I might be able to get my wifi working. Is this right?
Can you please tell what steps you did to make it work. Could you also give the links to the links to the driver and deb package you downloaded (in case this is all I need to get).
Thanks for you help.
P.

---

### Post by macron1 on 2007-05-08
i just want to thank very, very, very much whoever posted this how-to. i had been messing around for a very long time with ndiswrapper and having absolutly no luck what so ever. this method however worked first time for me. 

for reference to others who are/will be in my postion, i got this working on a Compaq Presario V6000 (intel core duo) with the *Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)* chip (using "lspci | grep Broad com\ Corporation" command). 

this information as posted would have helped me very much, not to mention saved me several hours, had it been available when i started, so i thought i better post it. thanks again

---

### Post by ongbk619 on 2007-05-08
> **pospam said:**
> Hi jangeles and all in the forum:
I just installed kubuntu feisty yesterday I cannot use my wifi. The problem I have is that I only have a wireless connection and cannot use a ethernet connection. From your post I am guessing that I could download the driver and the fwcutter deb from the internet in my windows partition and then write copy then in my desktop in my linux partition and then I might be able to get my wifi working. Is this right?
Can you please tell what steps you did to make it work. Could you also give the links to the links to the driver and deb package you downloaded (in case this is all I need to get).
Thanks for you help.
P.

If you go to the first page of the thread the how to and links to the drivers are all there.  Make sure you run the lspci command in the command line to determine that your wireless card uses the Broadcom chip set.  Otherwise this how to may not work.

I'm also new, and just installed Feisty on my machine.  Found this thread after hours of surfing and it was the only one that got my wireless to work.  Many thanks to the author!

- Ben

Wiresless card:
Linksys WRT54G with bcm4306 chipset.

---

### Post by pospam on 2007-05-08
Hi all:
Here I am posting using Kubuntu and my wireless connection.
Just to let all know what I did.
1.- Downloaded bcm43xx-fwcutter_20060108-6build1_i386.deb
from here:
[http://packages.ubuntu.com/dapper/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/dapper/utils/bcm43xx-fwcutter)
2.- Downloaded the driver wl_apsta.o from the link in the 1st post of thread.
3.- Followed steps 1 to 4 in first post. (step 5 is not needed in Feisty)
Rebooted and voila.
I downloaded everything using my windows partition and then I copied it to the desktop of my linux partition. I had previously installed EXT2IFS ([http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm#Download](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm#Download)) to be able to read in write to my ext partitions in windows.
Thanks all your help and thanks for this great how-to
P.

Hp pavilion zx5190US
Broadcom BCM4306
audio, video, wireless working in feisty.

---

### Post by macron1 on 2007-05-08
> Here I am posting using Kubuntu and my wireless connection.

just out of interest, hows your wireless speed? i finally got it going with ubuntu on an presario v6000 (see above post), but am only getting 20 KBps compared to my imac on the same wireless net work getting 175 KBps.
 
thanks

---

### Post by dArt8 on 2007-05-08
> **macron1 said:**
> just out of interest, hows your wireless speed? i finally got it going with ubuntu on an presario v6000 (see above post), but am only getting 20 KBps compared to my imac on the same wireless net work getting 175 KBps.
 
thanks
Same here. 
20 instead of 400 KBps. 
Is it posible to get better result by using different driver.

02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
30:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

---

### Post by pospam on 2007-05-09
> **dArt8 said:**
> Same here. 
20 instead of 400 KBps. 
Is it posible to get better result by using different driver.

02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
30:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

Hi all:
Well I don't see any difference in the download speed.
I ran a speed test and I get the exact same results in Kubuntu than in Windows.
[[IMG]http://www.speedtest.net/result/123859379.png[/IMG]](http://www.speedtest.net)
in the Knetworkmanager I get
Bandwidth:62Mb/s
Cheers
P.

---

### Post by Catsworth on 2007-05-10
Hi guys, could do with some assistance with this.

All seems to be working ok, except that when I tell it to connect to my wirless network (detected ok) it reports that it has connected at 0% and then I can't actually use the network.  The router's control panel shows that there aren't actually any devices connected at all :(

Any thoughts?

Thanks.

---

### Post by Aloir on 2007-05-10
Fantastic guide, thank you very much. This worked for me in Feisty.

Another late night attempting to make the Broadcom 4318 work. The light is now on! 

However, the wireless network i normally connect to (in Windows) is not working now.

Any ideas about what to check?

Thanks again.

---

### Post by macron1 on 2007-05-11
> **pospam said:**
> Hi all:
Well I don't see any difference in the download speed.
I ran a speed test and I get the exact same results in Kubuntu than in Windows.

in the Knetworkmanager I get
Bandwidth:62Mb/s
Cheers
P.

Just to follow up on the previous wireless speed thing i was questioning previously...

[[IMG]http://www.speedtest.net/result/124643654.png[/IMG]](http://www.speedtest.net)

vs 1271 kb/s down 107 up using the same test on my imac. miserable! -well, the uploads slightly better.  Any advice much appreciated, i clearly have a problem. thanks

---

### Post by LinkinCable on 2007-05-11
i have a issue your HOW TO finally got me rolling but, when I try to connect.. it fails.. it finds it right (AP) but fails at connetion

Any Ideas?

LinkinCable

---

### Post by earobinson on 2007-05-14
solved it for me, the weird thing is I only had to do steps 1 2 and 3 and that was it, and ideas why?

---

### Post by ChipG on 2007-05-17
I am an absolute noob, and while I managed to install Ubuntu onto my HP Pavilion dv1000, I was unhappy that my wireless wasn't working.

But then I found this thread.  I followed the instructions and it worked great, even though I have a BCM4318.

Thanks!

---

### Post by digital-adapt on 2007-05-17
Woohoo, my wireless is working :D

My system:
Dell Latitude 131L with the 1390 802.11g Mini Card wireless card.
Ubuntu 7.04 (feisty fawn) and Windows XP Home.

Now, if I could only get my printer to work and I could give up Windows altogether :)

---

### Post by ChipG on 2007-05-17
> **ChipG said:**
> I am an absolute noob, and while I managed to install Ubuntu onto my HP Pavilion dv1000, I was unhappy that my wireless wasn't working.

But then I found this thread.  I followed the instructions and it worked great, even though I have a BCM4318.

Thanks!

I spoke too soon...

It was working great. Then I rebooted.  The wireless lights were on. For the first minute or so after the desktop came on, I was able to connect to the internet. But then, the connection didn't work anymore, even though the little bars showed that the wireless was still receiving a signal.

I reinstalled using these same instructions, but the same result.

Any thoughts on what this is about?  Thanks!

On edit: I did a clean reinstall, and followed the directions again. But this time, no luck.  The little bars are showing a signal, the name of my wireless network shows up, the wireless lights on my laptop are on, but it doesn't connect to the internet... :(

But then, I fiddled a bit more in network manager, choosing other networks (which didn't work), then manually connecting, and now it is working. Very inconsistent...

---

### Post by V. Wayne on 2007-05-17
It worked with the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02).  I enabled the roaming mode and presto!

---

### Post by newbie_noob on 2007-05-20
I get this message when i do an lspci | grep Broadcom\ Corporation

Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

Currently when i do an ifconfig i do not see any wireless connection, but the wireless connection is shown as enabled in system>admin>networking

i did follow the instructions and everything seemed to go fine, the network manager now shows just a wired connection.

please help me!

---

### Post by esaldana on 2007-05-20
Thanks!!!!

The only extra step was to turn on my card by pressing FN+F2 and the LED turned on.

I was close to give up but thank God I did not.

Regards

---

### Post by bknitram on 2007-05-22
This didn't work for me, but the BCM4306(Rev 03) instructions at [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom) did.

If anyone else is having problems with anything (there are instructions for other models there too) I would advise you to look there.

---

### Post by lnm477 on 2007-05-23
Nick!  Thank you for taking the time and trouble to create such a tutorial.

That being said, maybe you can help me further.  After installing network-manager-gnome in Xubuntu Feisty 7.04, I still don't get a wireless icon.  If I type iwconfig I ge the following:

lo     no wireless extensions.

eth0  no wireless extensions.

eth1  IEEE 802.11b/g  ESSID: "linksys" Nickname:"Broadcom 4306"
         Mode:  Managed   Frequency= 2.422GHz  Access Point:  numbers and letters grouped in 2 separated by a :
        Bit Rate=11 Mb/s  Tx-Power=16 ddBm
       Link Quality=103/100  Signal level=-28dBm  Noise Level=-69 dBm

The link and power lights are lit on the wireless card, but still cannot connect to the internet.:(

By the way, I forgot to mention that I am using a linksys wpc54g card.

Any advise would be greatly appreciated.  Thank you in advance

Ellen

---

### Post by TSXDriver on 2007-05-25
This How To is awesome.  I'm a new Linux user and put 6-7 hours into the other methods found in the Wiki to no avail.  After 5 minutes of time with this it worked perfectly!  Excellent work.  I'm going to browse other posts by this person whenever I need help on stuff.

---

### Post by eric p on 2007-05-25
Dude you are THE MAN thank you very much for that how to.

---

### Post by kokopelli69 on 2007-05-27
:KS Thanks a bunch for this post nickm.... I've spent a day and a half trying to get this to work using other posts.....  As for me, I only needed to use the fwcutter program and the wl_apsta.o driver from the googlepages....

Compaq R4000 Amd 64bit laptop
Driver: Broadcom 802.11b/g WLAN

 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Cheers,
Chris

:popcorn:

---

### Post by dphipps on 2007-05-28
I am ok with this until I come to this.

> **nickm said:**
> 

** 4B ) Extract your Cards firmware from the driver**
Just to be safe we'll put the driver in the kernel folder too
[CENTER]
```

sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o

```
[/CENTER]

you may have to repeat this step each time the kernel is updated or you may not, your results may vary.

***Note* The location and name of the .o file for this command may differ in your case,  if you really get stuck type bcm43xx-fwcutter and then hit space, find your file using the GUI and then drag and drop it into the terminal.**



What is `uname -r` supposed to be.

```
user@laptop:~$ ls /lib/firmware/
2.6.20-15-generic         bcm43xx_initval05.fw  bcm43xx_microcode11.fw
2.6.20-16-generic         bcm43xx_initval06.fw  bcm43xx_microcode2.fw
bcm43xx_initval01.fw  bcm43xx_initval07.fw  bcm43xx_microcode4.fw
bcm43xx_initval02.fw  bcm43xx_initval08.fw  bcm43xx_microcode5.fw
bcm43xx_initval03.fw  bcm43xx_initval09.fw  bcm43xx_pcm4.fw
bcm43xx_initval04.fw  bcm43xx_initval10.fw  bcm43xx_pcm5.fw
user@laptop:~$ 
```

---

### Post by ronniew on 2007-05-29
how do you get wpa working with this card.... if i have to use ndiswrapper then how do i uninstall this module?

---

### Post by lemike on 2007-05-31
**Thank you so much.**
I really didn't expect this to work as I'm using one of those Airforce cards that were mentioned, but this message is being posted wirelessly.  
You are now definitely my favourite person on the internets.

---

### Post by francilla on 2007-06-01
thank you so much. it did work, even though my broadcom card is a 4311 one!:popcorn:

---

### Post by JoshBenner on 2007-06-03
Thanks very much! 
Tried various different methods trying to get my wireless card working (including ndiswrapper) but to no avail.
But then I tried this method and it worked straight away!
Thanks again :D

Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by Acidfire68594 on 2007-06-03
ok ive read threw like all the posts and the most i could do is get my wireless working for 30 seconds, ive got a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) and if anyone could walk me threw this PLZ email me at [email]acidfire68594@gmail.com[/email]             :(

---

### Post by new_siscosab on 2007-06-03
I am a very new beginner. I installed Feisty 7.04. Thank you so much for the instructions for the Belkin card. It absolutely works.

Belkin F5D7230-4 Router
Belkin F5D7010 802.11g Wireless card
Dell Inspiron 4150 Notebook

---

### Post by jdmcbr on 2007-06-05
So, I have a brand new installation of dapper 6.06. Coming to this page and following these directions were the absolute first thing that I did. As nearly as I can tell, I followed the directions exactly. However, I am still unable to connect wirelessly. I looked through this thread a bit (though not extensively), and did not see any answer that addressed this exact issue. It seems that most people had errors along the way, but everything I did seemed to go smoothly. 

```
jmcbride@jmcbride-laptop:~$ more /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"
jmcbride@jmcbride-laptop:~$ lspci | grep Broadcom\ Corporation
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
jmcbride@jmcbride-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

I am using an hp pavilion zv5000. Thank you in advance for any help.

---

### Post by macron1 on 2007-06-08
> So, I have a brand new installation of dapper 6.06. Coming to this page and following these directions 
upgrade to feisty then try it again?

---

### Post by jpyanowski on 2007-06-08
I just want to thank all of the Ubuntu forums. I now have a HP Pavillion dv2010us AMD64 laptop dual booting Vista and Fiesty with a working Broadcom wireless. Life is sweet.....:-\"

---

### Post by goodtimetribe on 2007-06-11
It didn't work for me. I'm one of the no votes with a 4318 AirForce. (ASUS WL-120)

---

### Post by hypedup05 on 2007-06-11
I'm having a problem enabling the universal packages step. I clicked on the link and tried to follow the instructions, but I after going into the synaptic package manager > settings > repositories I don't have an Add button like the instructionis say.

I'm using the newest version of Ubuntu, 7.04

---

### Post by Cialciut on 2007-06-11
Thank you nickm, your guide works perfectly for me [-o<

I used it on my Dell Inspiron 1300 with 1370 wireless minipci card ( yes... Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) :) ) and Ubuntu 7.04

The only precondition, on my case, it was to turn on the wireless device inside the BIOS (set off by default).
After that I followed your guide exactly step by step.

Thank's again.

---

### Post by anndruu12 on 2007-06-13
Is there a guide anywhere for how to get wireless working with a WPC54G ver. 3 Broadcom Corporation BCM4318[Airforce One 54g] 802.11g Wireless LAN Controller (rev 02)? I read in the HowTo post that it is highly unlikely it would work if that is the version I have. I tried it anyway but as was said, it didn't work. Any ideas?

---

### Post by Cialciut on 2007-06-13
Have you checked inside your bios if the wireless device is set on?
On windows startup there is a software that turn on the wireless card but on ubuntu this software doesn't exist. So you have to turn it on by default in your bios settings.  After that this guide worked for my pc (Dell inspiron 1300). Try.

---

### Post by modal_realism on 2007-06-14
First post here.

After several Ubuntu versions... Dapper, Edgy, and now Feisty Fawn.  After a couple PCLinuxOS distros and countless other releases...

I have FINALLY gotten wireless to work on my HP dv6000z ( BCM4310 ).  Thank you so much!  I always kept trying the ndiswrapper manual way.  I remember something about the fwcutter, but this recent try that I made had an ANSI-GUI popup on the apt-get command and automatically extracted the bcm drivers for me.  It worked like a charm.  On reboot, it popped up with all the wireless connections!  Everything works on this laptop now.  I can FINALLY sever myself from Windows.  Well at least on the laptop.  The gaming rig has gotta stay; Crysis is coming out soon afterall ;)  But it has Feisty Fawn on it as well; so its all good!

Thanks again guys!  You've made a believer out of me once again! :p :p :)

---

### Post by Tulip on 2007-06-14
> Originally Posted by DW5
Upgraded from Breezy, tried all day yesterday to get this to work following the guide. Have an Compaq nx9010 with a Broadcom 4303. ...used the cutter, modprobed, etc. To no avail, could see network, but dhcp failed to get an ip.
DW


> **PPower said:**
> Is it a nx9110? That is supported but 9010 is not on the list. Please try again once Ubuntu has updated their kernels.

I've got the same Compaq nx9010/Broadcom 4303 chipset, and am running into the same problems. Im using a freshly updated install of Feisty What/where is this list and has the 9010 been added onto it yet?

Regards

---

### Post by soapytheclown on 2007-06-14
> **hypedup05 said:**
> I'm having a problem enabling the universal packages step. I clicked on the link and tried to follow the instructions, but I after going into the synaptic package manager > settings > repositories I don't have an Add button like the instructionis say.

I'm using the newest version of Ubuntu, 7.04


i believe that in fiesty you can just install the firmware cutter and the rest sorts itself out automatically atleast thats all i had to do for my bcm43xx card ;) just try that for now

---

### Post by Dmitri on 2007-06-21
Hey, will this work for Kubuntu 7.04? (pure KDE, no Gnome programs/libraries)

EDIT:
To answer my own question:
Yes, it did work! Big thanks to everyone who made this possible!

Though I did not install any other network manager, I just decided I'd stick with KNetworkManager.. and it works fine.
So, to all KDE users, you don't have to go with Gnome apps for this to work.

P.S. Finally removing Windows from my profile :-P

---

### Post by slickrik on 2007-06-22
Thank you so much for this post.
It worked like a charm!!!

Kind regards Rik :D

---

### Post by Dmitri on 2007-06-22
Hm, for some reason, it worked before but stopped working after a second restart..

I always get stuck at 
"Activation stage: IP configuration Started"" when trying to connect to an unencrypted 
OR
"Activation stage: Configuring device." when the wireless network is encrypted

Also, now I'm unable to shut down my computer normally (and when it tries to shut down), the network button on my laptop flashes like crazy!
I have Compaq R4000, with Kubuntu 7.04... That I just installed the other day after formating my whole drive.

Hm, any help here? 
I also tried to repeat the steps.. but to no avail. 

Oh, and I can still see all the networks that are available.. it's just that the network card acts like crazy when trying to configure itself.

-Dmitri

---

### Post by nunnst on 2007-06-22
EXCELLENT!   I can return the new cards I bought (of which only 1 of the 2 worked).  You saved me $70 bucks! 

I now have an HP dv8210us laptop w/ Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)  working very very nicely!

God I wish I'd found this 4 days ago when I first made the leap!!!

NOTE:  I did make 1 change, I couldn't find bcm43xx_fwcutter in the Synaptics Repository so I got it from here:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fb%2Fbcm43xx-fwcutter%2Fbcm43xx-fwcutter_20060108-6build1_i386.deb&md5sum=a86e66aba8afc1a7ba1c872ae4192a57&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fb%2Fbcm43xx-fwcutter%2Fbcm43xx-fwcutter_20060108-6build1_i386.deb&md5sum=a86e66aba8afc1a7ba1c872ae4192a57&arch=i386&type=main)

When I went to step 4 of the guide I hit an error because the .deb install script from the different site placed bcm43xx-fwcutter in  /usr/bin instead of in /lib/firmware.  This required the following change to step 4:

       4 ) Extract your Cards firmware from the driver.  Open a terminal (dont worry) and type
             the following:

             Code:

             sudo bcm43xx-fwcutter -w **[COLOR="Red"][SIZE="2"]/usr/bin[/SIZE][/COLOR]** ~/Desktop/wl_apsta.o


THANKS AGAIN

---

### Post by Ahslan on 2007-06-22
could someone plz help me...i have absolutely no idea wat im doing...i installed the latest ubuntu desktop version and tried to get the wireless working but have no clue wat to do...i get stuck on the fwcutter part...it says it cant find it. A little help would be appreciated..

---

### Post by Dmitri on 2007-06-23
> **Dmitri said:**
> Hm, for some reason, it worked before but stopped working after a second restart..

I always get stuck at 
"Activation stage: IP configuration Started"" when trying to connect to an unencrypted 
OR
"Activation stage: Configuring device." when the wireless network is encrypted

Also, now I'm unable to shut down my computer normally (and when it tries to shut down), the network button on my laptop flashes like crazy!
I have Compaq R4000, with Kubuntu 7.04... That I just installed the other day after formating my whole drive.

Hm, any help here? 
I also tried to repeat the steps.. but to no avail. 

Oh, and I can still see all the networks that are available.. it's just that the network card acts like crazy when trying to configure itself.

-Dmitri

Hm, now it works again....
duh.

I didn't do anything... and I'm almost afraid of touching my system now (since I'm going to travel now... and I seriously need wireless.)
It is somewhat inconsistent as a fix... but it's better that no wireless at all. I'll keep you posted if I can ;)

---

### Post by Dmitri on 2007-06-23
> **Ahslan said:**
> could someone plz help me...i have absolutely no idea wat im doing...i installed the latest ubuntu desktop version and tried to get the wireless working but have no clue wat to do...i get stuck on the fwcutter part...it says it cant find it. A little help would be appreciated..

Do you have Universe Repository enabled?
[https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)

---

### Post by thoman on 2007-06-27
Great ....
I have follow the instructions and it work fine with me..
Testing on Ubuntu 7.04

---

### Post by gletob on 2007-06-27
Thanks worked great I have BCM4318 Rev 2 and it worked perfectly on 7.04 no issues at all.

---

### Post by Hmoobgolian on 2007-07-03
Has anyone able to get this working with WEP?  I can't connect to my AP with WEP enabled on it.  All else is fine though...  Please help!!??

---

### Post by HeinekenPissr on 2007-07-04
Why do you want to use WEP?  Use WPA, it's more secure anyway.

---

### Post by Sokraates on 2007-07-04
For whatever reason since Feisty my card refuses to connect to WPA-encrypted connections. WEP and unprotected works.

Hmoobgolian: If you have any influence on the encryption used (i.e. your home network etc), try WPA instead. Concerning WEP I can only imagine, that either the wrong type is used (at least oon my router I have 3 or 4 types of WEP-connections) or the password was simply entered as HEX instead of ASCII or vice versa.

---

### Post by Hmoobgolian on 2007-07-05
Actually, my WEP hex key is correct and works in Windows, but not in the Gnome Network Manager.  I know that WPA is more secure, but because I share it with my neighbor, it's more of a hassle to reconfigure the new encryption.  I was just wondering if anyone has been able to get their Gnome Network Manager to work using WEP.  If so, please share on how you got it working.  Thanks.

---

### Post by archangel.jason on 2007-07-05
I have the 4318 and this worked for me. I am using the new 7.04 Feisty Fawn. Thanks a lot for this page.

---

### Post by Graham Joyce on 2007-07-07
Thank YOU very much .........
BCM4318 card running on Dell GX270 with Feisty Fawn, exactly as detailed in "How to" post.

---

### Post by diablo75 on 2007-07-07
Does anybody know if this guide will work for a BCM94306?  I don't have the laptop with me to try this out (it's a clients laptop I just installed Ubuntu on, and I'd like to get that internal card working for them).

---

### Post by t0xy on 2007-07-08
@nickm, Thanks alot for this information. The tutorial given worked perfectly for me!
Just wish it worked faster then 11mbps.

---

### Post by saifu on 2007-07-11
worked great..I have bcm4318 and feisty 7.04 on hp nx6125...tnx alot \\:D/

---

### Post by jimbster2 on 2007-07-12
Thanks!

It works great!  I'm using Ubuntu 7.04 on an IBook G4 powerpc, dual boot with OSX 10.39, 60 gb drive, 500 mb ram.  Router is Linksys WRT54G on Verizon DSL 3mb/s.

802.11b is just fine with me with 3mb/s.

I also use Ubuntu 7.04 on my Dell desktop, dual boot with Windows XP, no wireless.

Thanks again.
jimbster2

---

### Post by peewee3ie on 2007-07-18
this work very will on Kubuntu ver 7.04 (Is what i Have on my laptop) as well as ubuntu. My laptop is a Acer Aspire 5050. Thank you for the info on making the wireless card work

Tony MC Gurie

---

### Post by tgbrowning on 2007-07-18
I'm getting a result that confuses me a bit. In the terminal, when I entered:  

 lspci | grep Broadcom\ Corporation

I'm getting the following result:

01:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 03)

The reason this confuses me is I just set up a computer for my daughter -- same model, using the exact same distro (Feisty Fawn) with all of the hardware identical, and things proceeded exactly like your "How To" -- letter by letter.  Obviously, something isn't the same, but I damned if I can figure out what.  Any ideas why a machine with the same hardware would turn up a wifi card as unknown one time and known another?

Browning>>>

---

### Post by peewee3ie on 2007-07-19
tgbrowning

JUst do it. I had the same thing as you and it worked when i done it all. I world try it and it should work.

---

### Post by tgbrowning on 2007-07-19
Tha's probably what I'll end up doing, since it did work the first time on the other machine. I was just worried about the fact that the computer seems to see it as an unknown device. 

Browning>>>

---

### Post by djino on 2007-07-26
OMG!!! The guide work.. BEST GUIDE EVER!!!!.. THANK YOU!!!!!

djino
"Who is now wired-free thanks to the guide"

---

### Post by jazzflight on 2007-07-26
> **xXx 0wn3d xXx said:**
> This worked great with my Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) card. And to everyone who is having problems with getting this to work, try this:


and add:

to a new line.



Thank God!!! I could kiss you.

---

### Post by Elloyd on 2007-07-28
Your directions worked great! The cutter did the trick.

---

### Post by ahchong on 2007-07-28
ARGH!!!
you all know what?
after all the methods that u gave me, i still can NOT run the wireless card.
i still not given up in this thing.
sure ive been bless by broadcom. i dont want to waste my money to buy wireless card PCMCIA.
erm... anyone that can help? other than give me the idea to buy new card!!!

---

### Post by wzardd on 2007-07-28
This guide worked for me (as least for now).

Many thanks.

---

### Post by smoore on 2007-07-28
YES vote on the poll.

feisty fawn, gateway laptop something or other.  My wife's machine (she's a linux user now, wooo!)

broadcom 43xx chipset

All I had to do was install the firmware extractor mentioned in the OP and reboot (it asked me to download and extract the firmware... enter means YES!).  I had already set up the ssid and put the 128bit HEX password (yeah, I'm slackin' but the stepkids' machines won't do WPA) before installing the FW extractor.

Good stuff, this Ubuntu.  Here I've been buying hardware that I KNOW works with Linux... she decides to "try it" and manages to find a distro with point-n-click + one forum search wireless install.  I guess I'm cheating a little knowing how *nix works so I don't have to follow tutorials to the letter.

This is, indeed, posted on her laptop using the aforementioned wireless connection.  Sound controller next.

Sweet.  You Ubuntu guys are going to bring Linux to The Masses.  Good job.

---

### Post by Elloyd on 2007-07-30
> **ahchong said:**
> ARGH!!!
you all know what?
after all the methods that u gave me, i still can NOT run the wireless card.
i still not given up in this thing.
sure ive been bless by broadcom. i dont want to waste my money to buy wireless card PCMCIA.
erm... anyone that can help? other than give me the idea to buy new card!!!

Ok so since we can't read minds, what part of this guide did you try and what results did you get especially in the query about whether or not you have a broadcom chipset? Give the group some details so we can help.

---

### Post by und3rtug4 on 2007-07-31
Nice... very nice!

I have a fuc**** old broadcom at my old & busted laptop!

I tried a lot of ways, but it only worked out using the "CUTTER"!

Thanks dude! Brought my old busted laptop back in action!

Props!

---

### Post by aaaantoine on 2007-08-01
I apparently have one of the Air Station wifi adapters, but I followed the steps and got wifi working pretty quickly.

The only problem I had was that the fwcutter could not be verified.  The installation of fwcutter didn't finish when I tried it in a terminal, but it worked via the Synaptic Package Manager.

Specs:
Acer Aspire 5050
Ubuntu 7.04 Feisty Fawn AMD64

---

### Post by wawjohn on 2007-08-07
Worked fine for me with a Linksys card. I'm running Kubuntu 7.04, and using KNetworkManager on a client's old Packard Bell laptop.

However, the bcm43xx-fwcutter configure script wanted to download from its built-in URL, whose site is apparently over its bandwidth limit, so the configure script failed.

I sucessfully downloaded the file from [http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip), and extracted the firmware files into my curent kernel directory only. One reboot later, and the card was working and sucessfully connected to an open network, then to a WPA network.

One problem remained, however. Each time I ran synaptic or apt-get, it would attempt to configure the bcm43xx-fwcutter package. This failed, because the download site is still unavailable. To stop apt from complaining any more,i edited /var/lib/dpkg/info/bcm43xx-fwcutter.postinst and simply put an exit at the beginning of the script. Then I ran dpkg --configure -a and satified apt's hunger for sucess.

So thanks a lot!

---

### Post by nickm on 2007-08-07
woah, seems the fwcutter developers modified their code to download a file from my googlepages site without telling me. now my site is out of bandwidth so their code broke!

:popcorn:

---

### Post by InfinityCircuit on 2007-08-10
Is it possible to move wl_apsta.o to another mirror?  At the moment, attempting to extract bcmwl5.sys from the windows partition on my computer gives me this error:

Sorry, the input file is either wrong or not supported by bcm43xx-fwcutter.
I can't find the MD5sum b89bcf0a25aeb3b47030ac83287f894a :(

I was only able to get wl_apsta.o to work.  It is unfortunate that the site was overloaded, apparently without the manager's knowledge.

---

### Post by coniferous on 2007-08-12
Just a small note that would of saved me alot of fustration - After your done following the steps, make SURE your press the button that turns your wireless off or on! it should be on by default, but mine wasn't for some odd reason... 

Oh well, works now!

Thanks for the howto!

---

### Post by colombo187 on 2007-08-15
AWSOME!! I've been trying other ubuntu tutorials for a couple of days - but this one worked, and very quickly I might Add. 

I have the BCM4318 and no wired networking but I downloaded the fwcutter package at work and used the NT driver that came with the CD....


Thanks again!!
:guitar:

---

### Post by higgsboson on 2007-08-16
Hi,

I have a Fedora 7 installation on my powerbook G4. The is no kernel directory in my /lib/firmware, unlike the screenshot shown in this tutorial. Its occupied by a folder named "zd1211", two LICENSE files, and a bunch of bcm43xx firmwares that were there from installation. Therefore I can't proceed with step 4b. 

Is anyone familiar with this sisuation? How to work around it?
:confused:

---

### Post by PerfMonk on 2007-08-17
Hi,

I'm sending this reply from my brand new wireless connection!

My card is :

02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I would like thank everybody that contribute to this great howto : THANKS!
You are the ones that make Ubuntu such a great distro.

Second,  I would like to highlight an area where instructions where not very clear to me.   The part about copying the windows driver got me confuse a bit.  I had some drivers on the CD in a  ./drivers/nt/  directory...  There was another w98 directory and an executable in the root of the CD.  So I wasn't sure wich file to use with fwcutter ...  I wasn't sure neither of the name of the file.  Finally I used the bcmwl5.sys I had on the NT directory and it obviously work great.

This area of the howto could be made clearer to a newbie like me.

Regards,
             BT

---

### Post by watercooled on 2007-08-29
anybody know where wl_apsta.o is hosted now?

The original link is down and i cannot find this anywhere.  Would someone mind emailing this too me?  

PM me if you can spare 1 min to send this.  Thanks everyone

---

### Post by cjgtaz2510 on 2007-08-29
I am setting up wireless on my Compaq and received this error when I followed the instructions:

Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:02:08 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)


What am I doing wrong? 

Thanks.

---

### Post by antm88 on 2007-08-31
@watercooled, you can use [www.archive.org](www.archive.org) (the web archive) to find the file before it was taken down. That site is unbelievably useful!
Ant

---

### Post by Immanuel on 2007-09-01
I confirm not all the links in the post work correctly: here I provide a possible solution.

I first tried using the bcm driver I found in my windows system folders, the fwcutter did work correctly but the driver didn't work, as apparently the  bcm43xx in kernels before 2.6.23 is not compatible with "version 4" drivers. My problem was highlighted by messages shown by dmesg, and saying:
> bcm43xx: Firmware: no support for microcode extracted from version 4.x binary drivers.

I then made a number of google searches and finally had[COLOR="Red"][SIZE="7"] **success**[/SIZE][/COLOR] (in Ubuntu Feisty 7.04, with a broadcomm 4311  on a Dell 1390 MiniPCI card installed on a Latitude 131l laptop) following the instructions found here: [COLOR="Red"][SIZE="7"]**[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)**[/SIZE][/COLOR]
(in particular, using the "version 3" file).

In short, what I had to do that was not specified in this article was:
[LIST]
[*]download the apsta file from here: [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[*]run the following commands (found here: [http://doc.fedora-fr.org/Installation_du_wifi_-_bcm43xx](http://doc.fedora-fr.org/Installation_du_wifi_-_bcm43xx) ) to restart the driver:
# sudo rmmod bcm43xx         < -- unload module
# sudo modprobe bcm43xx      < -- load module
# sudo dmesg | grep bcm      < -- verify it's working, no error msgs.
# sudo dmesg | grep 80211   
# sudo lsmod                 < -- verify module is loaded
[/LIST]

I think the linuxwireless link should be put in evidence on the top of the original post, and the links from that site to the .o files should be explicited.

---

### Post by jcaledun on 2007-09-06
this worked a few weeks ago,  i just reloaded my Dell Latitude D610 today and it no longer works.  Any ideas?  

Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bcm43xx-fwcutter (006-1) ...
--19:19:35--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:19:35 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by crisnoh on 2007-09-13
nevermind

---

### Post by ruggrat on 2007-09-14
I had the same problem as jcaledun:


Reading package lists... Done
Building dependency tree        
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bcm43xx-fwcutter (006-1) ...
--16:38:18--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:38:18 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

What can I do to fix it?

---

### Post by jude01 on 2007-09-25
worked for me!!

I had to run modprobe bcm43xx and reinstall network manager, but after I rebooted it worked fine :)

you all rock! :guitar:

---

### Post by auraness on 2007-09-25
This was amazingly difficult with other guides, but this one was easy to follow. Thanks.

---

### Post by Zizo on 2007-09-30
I couldn't go through all the 92 pages of this thread to check if someone had my problem and had it solved.
 
I know it is for bcm43xx but why not giving it a try. My Broadcom is 4401 and I am not able to get my wireless working. I can see the wireless connection, it says "excellent strengh". I put the sucurity key in Hex and activate the eth1. The bars in the network manager are all green, but I cannot browse the internet or use this connection.
 
My ubuntu is 6.06, my laptop is a Dell Inspiron 8600. I can post more info about hardware and other things but right now I am forced to post from my Windows so I have no access to a terminal. 
 
Thank you in advance.

---

### Post by proghead on 2007-10-01
Just wanted to say thanks, you saved me a lot of work. This works great!:)

prog.

---

### Post by markp1989 on 2007-10-02
thanks i tried this in gusty tribe  5 and it worked perfectly

---

### Post by twhitney on 2007-10-04
I have the "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" you said was unlikely to work, and this description worked just fine to me. In a matter of minutes I was up and running. However, the link to the wl_apsta.o was broken... but I had found an alternative download location so I could use that one you recommended... and after that like I said, 5 minutes and I was good to go... I didnt even have to reboot, the wireless network I was near picked up immediately... after numerous reboots it connects automatically and it seems very stable. Kudos to you, Im alright with linux, but when it comes to wireless and drivers etc. I get very very frustrated/confused... Thanks so much.

---

### Post by markp1989 on 2007-10-04
> **twhitney said:**
> I have the "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" you said was unlikely to work, and this description worked just fine to me. In a matter of minutes I was up and running. However, the link to the wl_apsta.o was broken... but I had found an alternative download location so I could use that one you recommended... and after that like I said, 5 minutes and I was good to go... I didnt even have to reboot, the wireless network I was near picked up immediately... after numerous reboots it connects automatically and it seems very stable. Kudos to you, Im alright with linux, but when it comes to wireless and drivers etc. I get very very frustrated/confused... Thanks so much.

do you have a link to the alternative download

---

### Post by LennyCZ on 2007-10-04
Hi!

  I have an BCM4318 WL card (ASUS WL-138g V2), and it works! Maybe I`m lucky, but thank you for this manual!!!

---

### Post by rcatman on 2007-10-05
I have 
> Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I used the bc43-fwcutter at first to extract the firmware and install the bcm43xx module but was limited to 11Mbps wireless connection. Connecting took a while too.

I recently switched to ndiswrapper and I can connect up to 54Mbps and the connection and wireless detection process is much faster! I used a script called bcm43xx-gtk-installer (version 0.2.1) by Darkn00b and it installed everything perfect. 

Also, I never use network-manager (in gnome and kde). I always install wicd ([http://wicd.sourceforge.net](http://wicd.sourceforge.net)). I use feisty fawn. Hopefully in Gutsy the network-manager will be improved and actually show wireless networks.

---

### Post by n00bWillingToLearn on 2007-10-05
I'd like to note that Gutsy's restricted manager now does this for you, it would be nice if somehow the parent could update his first comment to reflect this since this thread has gotten so long.

---

### Post by DapperMe17 on 2007-10-07
Zizo...maybe a firewall conflict. If you have green bars...you've GOT internet connection to your PC or laptop. Your browser may say "unable to connect to server".

Uninstall "iptables" & then restart your wireless network in Ubuntu. If you get a connect, then it was just a firewall conflict.. Then, you can simply reinstall iptables (ps...you may have to fetch updates first, before iptables can be found in the repositories).

---

### Post by capsfans6366 on 2007-10-07
So Laptop magazine made it sound like installing and using Ubuntu would be a walk in the park.  In fact, they said, "connecting to wireless access points was easy, even encrypted ones".  Well, they weren't installing on MY laptop. I've got the dreaded Broadcom 4306 ver 3 built-in wireless card, and I can't get the thing to work.  Ubuntu shows the card as existing, but it won't go looking for wireless networks, nor will it connect manually to my network.  It does say that it's using a driver for Broadcom 43xx cards.

I've tried installing and using FCCUTTER and NDISwrapper (got the windows driver from HP), but I'm not sure that I'm using either one of them correctly.  I'm computer literate (used to build my own desktops and can troubleshoot Windows problems pretty well), but I'm a complete neophyte to LINUX (I'm not afraid to use the terminal window, but I haven't a clue what commands to use).  I've tried going through this and other help sites, but I can't figure out what to do where.

Any help would be greatly appreciated, before I go scuttling back to the gentle confines of Win-dom.
:confused:

---

### Post by jodoj80 on 2007-10-07
Hi.

I read the "How to: Broadcom Wireless cards without Ndiswrapper for Dapper and Edgy". Actually, my laptop is running feisty fawn and I thought that this guide will help me with my problem. But, I got a problem in step three when I try to install "bcm43xx.." from Synaptic Package Manager. ```
E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1
``` If I try it from the terminal I get this message ```
Err http://do.archive.ubuntu.com feisty/universe bcm43xx-fwcutter 1:006-1
  Could not resolve 'do.archive.ubuntu.com'
Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-1_i386.deb  Could not resolve 'do.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
``` I want to know if there's other method using feisty fawn.

It's really hard to connect in places where they only had wireless access.

---

### Post by n00bWillingToLearn on 2007-10-08
> **diablo75 said:**
> Does anybody know if this guide will work for a BCM94306?  I don't have the laptop with me to try this out (it's a clients laptop I just installed Ubuntu on, and I'd like to get that internal card working for them).

4306 is supported according to [http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices) so it should work, on Feisty just install the bcm43xx package and it will offer to grab and extract the firmware, in Gutsy just go to System -> Administration -> Restricted Driver Manager.

---

### Post by kambad on 2007-10-09
I am a noob, Yes ;( I really appreciate the work you have done, I really didn't wanted to go through ndiswrapper as it broke my computer once. I followed your preocedure and I am stuck at **step No.4** *"sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o"*. I get a *"Cannot open input file /home/kambiz/wl_apsta.o"* response and I can't go any furthur in the procedure. Your help would be appreciated.

---

### Post by Techbot on 2007-10-11
Thank you. Just installed my first *nix . 
Once I saw that ubuntu could see the card but not the network I was convinced I was in for a long haul. A quick google, a bit of copy and pasting and the thing was working in about 5 mins.

I'm not even exactly sure what I did, I simply followed the instructions.

Well done.

---

### Post by cghost on 2007-10-21
Currently, I'm running Gentoo and thinking of switching to Ubuntu. The thing that is stopping me is that Ubuntu uses 2.6.22, and recently in 2.6.23 there were improvements for the Broadcom wireless driver that fixed a problem I was having with my card (a 4311 model which are known to have major problems with the bcm43xx driver.)

Have these improvements been included in the latest Ubuntu? Is there any way I can take advantage of the 2.6.23 improvements if not?

---

### Post by cyb3rj on 2007-10-22
> **Buelldozer said:**
> Davers007,

Go into your /etc/network/interfaces file and comment out everything after "auto lo
iface lo inet loopback"

The gnome network manager will NOT work correctly unless you do this! I'm not "good" enough to know if that is your only problem, but it sure is one of your problems at least.

Anyway, when you're done your file should look like this:

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto ppp0
#iface ppp0 inet dhcp

Removing the additional entries for my eth1 were exactly the solution to this after I followed these steps:  [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Always more than one way to skin a cat, I guess.  However, the initial tutorial on this gave me some good ideas on what could get this working.  MARVELOUS!

---

### Post by Klaus die Maus on 2007-10-22
> **Buelldozer said:**
> Davers007,

Go into your /etc/network/interfaces file and comment out everything after "auto lo
iface lo inet loopback"

The gnome network manager will NOT work correctly unless you do this! I'm not "good" enough to know if that is your only problem, but it sure is one of your problems at least.

Anyway, when you're done your file should look like this:

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto ppp0
#iface ppp0 inet dhcp

My nm-applet was broken until I this so now I can choose my connection, however my wired connection won't work. I had to go to manual configuration and change it from roaming mode to dhcp, but once I do that I can't choose my wired connection from the applet.

---

### Post by phdpeabody on 2007-10-24
Can anyone post a guide for this that will work in KDE instead of Gnome?

---

### Post by meth on 2007-10-25
I have 4303 chipset wireless card:

lshw -C network ouput:
>   *-network:0             
       description: Wireless interface
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 02
       serial: 00:90:4b:57:2d:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:d0002000-d0003fff irq:10


I have installed firmware like you say, but i get:

dmesg | grep bcm
> [   24.028000] bcm43xx driver
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1128
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1128
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1128
[   32.448000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1128


I can see the networks, but i cant connect, even in unsecure networks.

What can i do?

---

### Post by now-new on 2007-11-07
Great Job, I had Red Hat 5, then Ubuntu 7.04 and because I couldn't put to work my internet card I switch back to Windows XP Pro. but now thinking that Ubuntu 7.10 would have change all of it I switch again, but couldn't understand and finding your tutorial it was great, thanks
in less than 15 min.

---

### Post by Ahslan on 2007-11-07
Great instructions...worked perfectly for me...I just wanted to ask if there is a way to get the full 54mbs G working...right now it works perfectly under B (11mbs) but i wanted to see if there is a way get it going any faster...?

---

### Post by heyster on 2007-11-14
It worked for me too.
Good work dude!!!

---

### Post by oraldlight on 2007-12-10
2 years of off-and-on attempts and this thread solved my built-in wifi problems.
[COLOR="Red"][SIZE="5"]YES!!!!!![/SIZE][/COLOR]

---

### Post by buccaneere on 2007-12-10
You got a lot of effort here, nickm. That's to be lauded.

The punctuation and semantics however, makes for a VERY, VERY difficult read. It is horrible.

---

### Post by TwoFlightsDown on 2007-12-17
I have a Broadcom BCM 4306 on a five-year-old notebook computer (Compaq Presario 2500).  I was frustrated with my wireless card, but your directions worked like a charm.  Thank you so much for offering your help!

---

### Post by mr_dna on 2007-12-22
This works great on an old Inspiron 8100 with a Motorola WN825G NIC (running OpenSUSE 10.3).  Ndiswrapper worked briefly for me in Dapper, but was more trouble than it was worth - the card wouldn't initialize at boot, and would intermittently work, only if plugged in while the system was already running.

I've noticed in other posts that bcm43xx-fwcutter results in 11Mb/s connections on some systems, mine is running great at 22Mb/s without any tweaking, so if you've got an old 8100 and a WN825G, you may be in luck!

Anyway, thanks for posting this!  My old notebook has new life :)

---

### Post by downtownmicah on 2007-12-29
so maybe im just retarded but ive been working on this issue for a while now and nothing seems to work ive followed the directions from several forum's step by step and restarted the process several times 
under my kinfoCenter this is my wireless card 

BCM4328 802.11 a/b/g/n (rev 3)

and yes i know this is an ubuntu forum and i am running kubuntu gutsy but over all this has been the most helpful in beginning to understand the problem
so SOMEONE PLEASE HELP!!!

---

### Post by ShadowBlade on 2007-12-31
It is awesome, now it works for me, thank you so much!

For information, here is what I did on Edgy (I followed the tutorial):
lspci | grep Broadcom\ Corporation
0b:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

blacklist ndiswrapper
Remove all but lo in sudo gedit /etc/network/interfaces
wl_apsta and bcm43xx_pcm5
network-manager-gnome

my wifi card was lit up but I couldn't connect to an AP, I used wifi-radar and now it works!

---

### Post by virtuallinux on 2008-01-09
wow, I've finally got this card working. Thanks!  I've got a USR 5411 MAXg card (uses BCM4318 chipset), and had never been able to get it to work with ndiswrapper.  This was the first time I had tried the fwcutter method.

For the record, here's my system:

Sony Vaio PCG-F430
USR MAXg 5411PC card
Fresh install of Gutsy Gibbon
Used the driver located on my Windows partition

---

### Post by barisilk on 2008-01-18
Hi,I have the wrong checksum error too but at fwcutter's web page it seems that my wireless card which is Broadcom 4311 is supported.There seems to be 2 different versions of fwcutter I tried both of them but nothing changed :( have anyone dealt with this problem?

---

### Post by mukherjee.siddhartha on 2008-01-18
Hi,
I am using Gusty now...And all wireless problem solved.
So i just suggest you all guys to use Gusty if you use wireless :guitar:

---

### Post by cariocakev on 2008-01-25
FYI, I'm running Ubuntu 7.04 on a Powerbook G4 1GHz machine with a Broadcom 4306. 

This set of instructions worked fairly well, but there were bugs in the firmware that affected this machine's startup and shutdown sequences, hanging Nautilus for a couple minutes on startup for example.

I found that this firmware works well and seems to have few system-snagging bugs:

[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

I was only able to get a connection to a wireless router with security disabled and MAC authentication turned on. I don't like that lack of encryption. I will try messing more with WEP soon. I hear you MUST have a 13-digit key, but I still haven't gotten that to work.

Good luck all!

Anyone know if there's a tool to extract the *Apple*-loaded firmware rather than using PC or third-party firmware? Apple's drivers for the card are pretty solid.

---

### Post by mckemie on 2008-01-29
With Gutsy, apparently bcm43xx-fwcutter downloads the firmware from the internet.  It seemed to go well.  I did the bcm43xx-fwcutter thing using a working Orinco type card.  However, the new setup did not connect to my AP.  The AP is configured to take either b or g connections.

Here is my lspci:
---
root@ubuntu710a:~# lspci | grep Broadcom\ Corporation
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
root@ubuntu710a:~#
---
It is a  Motorola badged card.  When installed, it seems to work; lights come one and it becomes eth2 and appears under iwconfig.  However, it does not connect to my (also Motorola) AP and I can not do a dhclient.

Suggestions solicited.

---

### Post by noah420 on 2008-01-30
I followed the steps you showed and this is what resulted (linux user since yesterday morning)

Before I did this my wireless card would not turn on, thus not find any networks

Now, it turns on, and detects the network, but will not connect

I made sure I have '802.11g Only' unchecked in my router settings
(the help says leave unchecked if your network is comprised of 802.11g and 802.11b devices)

As I am totally unfamiliar with anything linux I have come to a stand still.

Any help that can be offered would be greatly appreciated.

*UPDATE*
Removed Network Manager and WiFi Radar, installed WicD, signal strength is showing 67%, when I click connect the little bar goes back and forth, then nothing
Is this a problem with my network or is this a problem with the drivers?
I have to boot into Windows in order to go online (no access to ethernet) to view these forums or download files
I'm going to start the process over with modern drivers, I was before using the ones in the system32/drivers/ directory of WINDOWS

-Noah

*EDIT* Using BCM4318 (I know it said this tutorial probably wouldnt work for this card, but it did "improve")
*EDIT* Running Ubuntu 7.1 (gutsy gibbon??) on HP Pavilion ze2000 notebook

*UPDATE*
Well, I give up. I don't see how everyone can justify saying linux is better than Windows. I've never run into any problems like this with Windows before, and you don't have to have an IQ of 1000 to operate it. So for now, bye bye linux. Welcome back XP.

---

### Post by tyrell_turing on 2008-02-03
Worked like a charm for me. Thanks!  However, FYI, the first link to the wl_apsta.o file appears to be dead.

---

### Post by eagle-eye on 2008-02-05
I have just installed Gutsy on my Dell Inspiron 6400.  

Wireless works out of the box when I'm using Gnome.  Unfortunately I'm having problems when I use KDE. The KWifiManager can see my router (and my neighbour's) but won't connect.

I've been searching around for why this is different under KDE but haven't found anythiing.

Grateful for any help and I apologise if I've missed something obvious.

---

### Post by eagle-eye on 2008-02-05
Problem solved. Just had to install knetworkmanager in KDE.

---

### Post by iulian on 2008-02-09
HI, I'm using a Dell Inspiron with Ubuntu gutsy newly installed. I have problems using my wireless. I can see wifi newtworks in range but can't connect to any. Using an HP6720s from with Ubuntu gutsy it works, so my AP is working correctly.

Any Idea?
I use also wifi-radar but with no success.

```
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

My AP supports only 802.11g.

Edit:
As I see in the top bar, right corner, my laptop is not sending any data. I say this because no circle becomes green.

---

### Post by biloxibeachboy on 2008-02-13
The link to the bordlink.googlepages.com is no longer a valid link.  I've tried to install according to the instructions here but it keeps telling me that the link is not a valid link and exits with an error showing the above link as the problem.  I didn't try to tell it to use that link either so it's in the installer somewhere.

---

### Post by obform on 2008-02-14
After I installed Gutsy dual-boot on my Dell Latitude 610 with the Broadcom 4318 card, like many others, I couldn't connect to wireless.  	

     After struggling, I found [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy) and followed the offline instructions so that the Restricted Driver Manager now shows Broadcom firmware in use.

    Then I got Wifi Radar and installed it.  I could see all the networks in the neighborhood with it and with [COLOR="darkred"]iwconfig[/COLOR].

    I told Wifi Radar to connect to my wireless network SSID, and it said it did.  

    I couldn't ping either the router or Yahoo.  Then I noticed on the first page that

[COLOR="Blue"] Remember that you can use network-admin or network-manager, but not both! You have to set your card to roaming mode in network-admin to use network-manager, if you have already configured it in network-admin.[/COLOR]

    I went to a terminal and did [COLOR="DarkRed"]man network-admin[/COLOR], then [COLOR="DarkRed"]sudo[/COLOR] [COLOR="darkred"]network-admin -c[/COLOR], which got me a configuration box that looked just like the network manager dialog.  When I checked enable roaming, my whole system froze, including the mouse.  After I shut it down and restarted, things seemed as they were before I messed with network-admin.

	I uninstalled Wifi-radar, which didn't seem to be helping.

	[COLOR="darkred"]/sbin/iwconfig[/COLOR] reports that eth1 is my wireless network.

	[COLOR="darkred"]sudo dhclient eth1[/COLOR] reports "DHCPDISCOVER on eth1 to 255.255.255.255 port 67" four times with different intervals, then "No DHCP offers received.  No working leases in persistent database - sleeping"

	I'm doing this with occasional e-mail help from a son who is ahead of me, but he's contributed a lot of time, and I wonder if anybody recognizes this situation.

Thanks,
--obform

---

### Post by kathryn on 2008-02-18
Hello everyone,

Tonight I installed Gutsy as a dual-boot onto my Vista laptop.  The first (and only) problem thus far under Gutsy has been wireless internet.  Specifically, using a Broadcom 4311 wireless card in a Compaq Presario laptop.

I started with this How-to, and unexpectedly found that the solution for me was quite simple.

- Run Synaptic package manager
- Find bcm43xx-fwcutter (as instructed in the how-to)
- Install bcm43xx-fwcutter
- When it is nearly finished it offers a check box, asking whether you want it to "fetch and extract the firmware"
- I ticked this box and proceeded.  The firmware was fetched from a remote location, since I did not direct it to any file
- The wireless connections available in my neighborhood appeared
- I connected to my own network successfully but the connection dropped out every time

but 

- Reboot seemed to fix it

Hooray!  Hope this helps other Gutsy users. :)

---

### Post by ind on 2008-02-28
A BIG THANK YOU!!

This worked for me, I was using a Dell 1100 with a Linksys Wireless Card of WPC54G (ver 1.2) Broadcom (BCM4306).

The only problem I encountered was I couldn't get the WPA TKIP to work and had to switch to WEP 128bit hex. Odd...

---

### Post by Preetam on 2008-02-29
Hello All,

I have tried all the steps mentioned in the link 

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) 

to get XMicro Wifi USB Dongle to work on Dell Laptop E1405 running ubuntu 6.06

After installation of drivers and doing ndiswrapper -l it shows bcmwl5 installed but no presence of wlan device. I have pluged in USB (Wifi)
and done modprobe ndiswrapper as well . Also tried the fwcutter way!

Still the device led doesnt glow :(

---

### Post by tvdirector on 2008-03-09
So this solution was posted in april 2006.
Earlier I tried to turn to Fedora 4. But I could not get the wireless card working. (Maybe because I thought the card had a Sweex chipset but Sweex was "just" the vendor). I spent 2 weeks figuring things out. Alas, the wireless card did not work, back in 2004.
Just recently I discovered on the Ubuntu forums that I had the BCM4306.(This revelation took my a week)
But then, many forums could not give me a chronicle and clear solution. Then I found out the base article. (Took me an other week).
But within some hours I had my wireless card running well.


Thanks:guitar:.

March 2008

---

### Post by Phil1954 on 2008-03-11
Thank you for this excellent tutorial, which resulted in my BT 1060 firing up in xubuntu and me happily using our college wireless network.  My first work with xubuntu Terminal and installing drivers/firmware in xubuntu linux.

I am exceedingly obliged.

phil

---

### Post by Phil1954 on 2008-03-11
Brilliant tutorial - thank you so much.

phil

---

### Post by w8tah on 2008-03-24
any news or updates to this thread for the upcomming hardy heron release?

TIM

---

### Post by dahoiv on 2008-03-25
> **w8tah said:**
> any news or updates to this thread for the upcomming hardy heron release?

TIM

I got it work with the latest beta version.

First i followed this guide: 

> **kathryn said:**
> Hello everyone,

Tonight I installed Gutsy as a dual-boot onto my Vista laptop.  The first (and only) problem thus far under Gutsy has been wireless internet.  Specifically, using a Broadcom 4311 wireless card in a Compaq Presario laptop.

I started with this How-to, and unexpectedly found that the solution for me was quite simple.

- Run Synaptic package manager
- Find bcm43xx-fwcutter (as instructed in the how-to)
- Install bcm43xx-fwcutter
- When it is nearly finished it offers a check box, asking whether you want it to "fetch and extract the firmware"
- I ticked this box and proceeded.  The firmware was fetched from a remote location, since I did not direct it to any file
- The wireless connections available in my neighborhood appeared
- I connected to my own network successfully but the connection dropped out every time

but 

- Reboot seemed to fix it

Hooray!  Hope this helps other Gutsy users. :)

And then I enabled the driver:
System >> Administration >> Hardware drivers >> enable the wireless driver.

---

### Post by Hughmoris on 2008-03-25
> **kathryn said:**
> Hello everyone,

Tonight I installed Gutsy as a dual-boot onto my Vista laptop.  The first (and only) problem thus far under Gutsy has been wireless internet.  Specifically, using a Broadcom 4311 wireless card in a Compaq Presario laptop.

I started with this How-to, and unexpectedly found that the solution for me was quite simple.

- Run Synaptic package manager
- Find bcm43xx-fwcutter (as instructed in the how-to)
- Install bcm43xx-fwcutter
- When it is nearly finished it offers a check box, asking whether you want it to "fetch and extract the firmware"
- I ticked this box and proceeded.  The firmware was fetched from a remote location, since I did not direct it to any file
- The wireless connections available in my neighborhood appeared
- I connected to my own network successfully but the connection dropped out every time

but 

- Reboot seemed to fix it

Hooray!  Hope this helps other Gutsy users. :)

I too started this HOW-TO but stopped at the same point as Kathryn, after fetching and extracting the firmware.  I rebooted my computer, found my SSID and connected no problem.

Thanks for the help!

---

### Post by matiasargentina on 2008-04-20
> **nickm said:**
> 
----------------------------------------------------
people seem to be having trouble getting this specific card: *Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)* working using this guide, take a look at this post for help:
[http://ubuntuforums.org/showpost.php?p=1084114&postcount=43](http://ubuntuforums.org/showpost.php?p=1084114&postcount=43)
or
[http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218) if your looking to Ndis instead


I couldn't make it, must be cause I have controller revision 02. I followed the link for ndiswrapper and it works! Thank you for sharing your experiences.

---

### Post by TorqueMaster on 2008-04-20
This is a great tutorial and I got it to work for me (finally).  I would like to emphasize that the wl_apsta.o link on the first page is very out of date.  Just to update the tail end of this thread, a current link is: 

[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

Thanks for the help!

---

### Post by Estesark on 2008-04-22
It didn't work for me, the wireless network/card doesn't show up in the network manager. 'modprobe bcm43xx' gives no output. Any ideas?

My card is a Buffalo AirStation G54, and I'm running Gutsy.

---

### Post by tobydeemer on 2008-04-22
Hi all-

I did an upgrade last night to 8.04 and it broke the broadcom for me. I followed this post also:
[http://ubuntuforums.org/showpost.php?p=1084114&postcount=43](http://ubuntuforums.org/showpost.php?p=1084114&postcount=43)
And all I had to do was comment out the bcm-xx line and restart, and my wireless capabilities were restored. I didn't have to add any lines however.

---

### Post by Hector40 on 2008-04-25
I just installed 8.04 for the first time.  Previously I had Fedora and I had gotten the wirless to work with a similar process.

Unfortunately after following the steps in this process I can't get the wireless to work.  I have an Inspiron 5100 with the BCM4306 wireless card.

I have also removed BCM43xx from the blacklist file.  I also used the latest version of the driver, wl_apsta-3.130.20.0.o

The iwconfig command gives me the follwing...
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If anyone has any ideas it would be appreciated.

---

### Post by ranran on 2008-04-29
> **kathryn said:**
> Hello everyone,

Tonight I installed Gutsy as a dual-boot onto my Vista laptop.  The first (and only) problem thus far under Gutsy has been wireless internet.  Specifically, using a Broadcom 4311 wireless card in a Compaq Presario laptop.

I started with this How-to, and unexpectedly found that the solution for me was quite simple.

- Run Synaptic package manager
- Find bcm43xx-fwcutter (as instructed in the how-to)
- Install bcm43xx-fwcutter
- When it is nearly finished it offers a check box, asking whether you want it to "fetch and extract the firmware"
- I ticked this box and proceeded.  The firmware was fetched from a remote location, since I did not direct it to any file
- The wireless connections available in my neighborhood appeared
- I connected to my own network successfully but the connection dropped out every time

but 

- Reboot seemed to fix it

Hooray!  Hope this helps other Gutsy users. :)

Kathryn, Kudos to you!

All I had to do was go to Synaptic and download the bcm43xxx cutter (the one with the ubuntu logo next to it).

I let it extract the firmware, download, and voila!  my wireless network is accessible.

I am using a Dell Inspiron 8600c with the Dell wireless card.

EXCELLENT and THANKYOU! :) :) :)

---

### Post by gabetz08 on 2008-07-09
nickm i dont know if you are still checking t06:03.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
his post but i followed your directions and i can now see the wireless networks that are around but i am not able to connect to them at all, no matter what the encryption is. this is my wire less card info 06:03.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02). i used the driver from my windows cd because the website was down. any suggestions what i can do to get my card to connect to the wifi

---

### Post by pfeifdog on 2008-07-21
This was incredibly helpful -- thanks so much!

However, I'm experiencing a weird glitch.  The wireless card doesn't activate when I start up the computer, or when I insert the card after the first start.  The only way I've found to get it working is to put the computer on "Hibernate" and then revive it.  After that, I'm good to go (11mb/s on a G-router) until I shutdown again.

This isn't a big deal, but can anyone explain why it happens or how to make it work right on startup?

I'm running Hardy, fully updated.

---

### Post by ashleycurtis on 2008-07-24
Nice tutorial. Thanks a lot! It worked for me.

---

### Post by midwinter_ on 2008-09-13
> **gabetz08 said:**
> i can now see the wireless networks that are around but i am not able to connect to them at all, no matter what the encryption is.

I'm having the same problem.  I got it working at one point but then had to re-install, so I know that it *can* work.  But right now, I can see my network but can't join it.

Any ideas?

---

### Post by the_genrl on 2008-10-05
nickm...i love you.  right when im about to turn my back on ubuntu and the linux community, you shine light on the power of community by solving my half year long battle with this problem.  

thanks again sir!

06:00.0 Network Controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)   


on ubuntu 8.04

---

### Post by hoxi on 2008-10-14
Dont know if it matter but ,in my folder i found BCMWL6.SYS in stead of BCMWL5.SYS soooo.... if anyone needs that ... go here :) 
[http://www.mediafire.com/?lncz3zlz5z9](http://www.mediafire.com/?lncz3zlz5z9)

---

### Post by DapKo on 2008-11-05
[http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/)

"Extract the contents of the zip file into /lib/firmware/ - thats all there is to it, the rest should "just work". Fwcutter is NOT required to use this - these files have already been extracted."

:popcorn:

---

### Post by dranick on 2008-11-07
Hello and thank you for the tutorial.

I have everything in place but the wireless NIC gets turned off as soon as GDM starts (the wireless led is turned on during system boot but it turns off when the graphical interface loads).

I can see all the available wireless networks in range but I can't connect to my wireless network (I guess it has to do to the wireless network card being turned off).

Please help.

Thank you,

Nick

***Later edit***

System info: Asus A7D with a  BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller wireless network card.

on a lshw -C network command I have the following output:

```

  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: wlan0
       version: 02
       serial: 00:17:31:2f:fd:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

The dmesg shows:

```

 b43-phy0: Broadcom 4318 WLAN found
 Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
 [   19.980175] b43-pci-bridge 0000:03:03.0: PCI INT A disabled
 [   20.099614] ndiswrapper version 1.53 loaded (smp=yes, preempt=no) 
 [   20.226737] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver 
 [   20.229543] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded 
 [   20.229931] ndiswrapper 0000:03:03.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
 [   20.238699] ndiswrapper: using IRQ 22 
 [   20.598753] wlan0: ethernet device 00:17:31:2f:fd:02 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS     Network  Adapter', 14E4:4318.5.conf    
 [   20.598814] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

```

but yet my wireless card remains turned off (the wireless ledd is off even though the bluetooth one is lit).

I will appreciate any help you can provide on this matter as I really can't use the system without a working wireless card.

Thank you in advance!

---

### Post by trescott3 on 2008-11-12
I got my BCM94311 wireless card working on an HP DV6000 laptop using the guide here: 

[http://trentscott.org/?p=1]("http://trentscott.org/?p=1")

---

### Post by Greg F on 2008-12-18
> **DapKo said:**
> [http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/)

"Extract the contents of the zip file into /lib/firmware/ - thats all there is to it, the rest should "just work". Fwcutter is NOT required to use this - these files have already been extracted."

:popcorn:
This solved the problem with my wireless card. It was as easy as it sounds.

---

### Post by venkatesh_b87 on 2009-01-30
hi everybody, i am trying out the procedure specified here. but i did not understand the 4th point. what is that extracting firmware??? from which setup file??

---

### Post by rickfisher on 2009-04-11
More up to date info as of 2009-04-10

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by krstofer on 2009-05-09
Hey Guys, Sorry if this was addressed, but I can't seem to find the answer in this thread.

I am pretty new to linux (ubuntu). I am getting the error message, "Can't find package bmc43xx-fwcutter"

I think I enabled the repositories right, but I am including a screen shot, just in case.

Right now I am using a USB d-link device which worked upon install, however I have the built in broadcom 4306 that I want to use instead.

I have an HP dv1000 laptop. I included the screenshot of the repository.

---

### Post by krstofer on 2009-05-09
> **rickfisher said:**
> More up to date info as of 2009-04-10

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)


Nevermind, I was able to get it working using this link. Maybe this should be added to the OP.

Thanks guys!!!

---

### Post by bulgedeyes on 2009-05-22
> **crag277 said:**
> First of all, thanks to all the posts on these forums I'm posting from a wireless connection, and I have a Broadcom 4318 "AirForce One 54g".

Here's how I did it, maybe it'll help someone.  You don't even need an internet connection.

The drivers I used are attached to the message.  To follow this guide to a T downlad them and place in a folder bcm43xx on your desktop.

I've tried the procedure in this HowTo several times, on different versions of Dapper, with different drivers and it would never work.  I had to use ndiswrapper to get it working.

I'm running Ubuntu i386 Dapper, Turion 64, ATI Radeon XPRESS 200M.

1) ** Blacklist bcm43xx driver**
Open a Terminal window
Type "sudo gedit etc/modprobe.d/blacklist"
At the bottom add the lines
# get rid of the default kernel drivers
blacklist bcm43xx

2)  **Make sure network interfaces file is correct**
Type "sudo gedit /etc/network/interfaces"
Remove all comments ('#') that you see so that all devices arehandled by the default network manager.
I would reboot here and make sure the wireless light goes out

3) ** Install ndiswrapper**
Put in Ubuntu CD.  Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.You could also type "sudo apt-get install ndiswrapper-utils

4)  **Conigure ndiswrapper**
Open termianl and navigate the folder where your drivers are."cd Desktop/bcm43xx"
Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit.  If it worked, you should be able to click the Network Manager icon in the top right.  It will probably show a disconnected ennection becuase the computer is not plugged in.  
Left click it and select eth1 from the drop down menu. 
Click Configure
Click Wireless Connection, then Properties.  Here just enter your network information.  If you're using an unprotected network you should only have to type yout SSID.

Click OK and you should now be connected!  If a green signal meter and connected network icon appear in the upper right you'll know it worked.

Hope this helps!

I know I'm VERY late to the party and everything, but, dude, you effin ROCK! After three days, no clear answer, this solution, which I thought would be as fruitless as the countless others, solved my problem.

---

### Post by jeb800e on 2009-08-03
Whenever I try this method, the thing that only comes up is my 56k Modem. Will this work with my Belkin Wireless-G Desktop Card? Am I able to safely and successfully install the Belkin Wireless-G Desktop Card under Wine?

---

### Post by cicero33333 on 2010-05-17
When I try to ectract the firmware from the driver, it says 

adam@adam-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
sudo: bcm43xx-fwcutter: command not found

Any suggestions?  Any and all help would be much appreciated.  I'm new to this!

---

### Post by theboss9999 on 2010-08-03
Hi i have Broadcom BCM4312 wifi card, everything was fine until 4-th step when i have to extract the firmware
this is what i get :
root@ubuntu:~# sudo b43-fwcutter -w /lib/firmware ~/home/a123/broadcom-wl-4.178.10.4/linux/wl_apsta.o  
Cannot open input file /home/a123/home/a123/broadcom-wl-4.178.10.4/linux/wl_apsta.o
can somebody tell me what can cause this message? how do i solve this

---

### Post by coolsnowmen on 2010-09-09
> **theboss9999 said:**
> Hi i have Broadcom BCM4312 wifi card,  everything was fine until 4-th step when i have to extract the firmware
 this is what i get :
 root@ubuntu:~# sudo b43-fwcutter -w /lib/firmware ~/home/a123/broadcom-wl-4.178.10.4/linux/wl_apsta.o  
 Cannot open input file /home/a123/home/a123/broadcom-wl-4.178.10.4/linux/wl_apsta.o
 can somebody tell me what can cause this message? how do i solve this
 The message means that the file you are looking for probably doesn't exist.
 
 Where did you put wl_apsta.o ?  My guess is that you don't know what the  ~ means or you mistyped it.  ([http://www.gnu.org/software/bash/manual/bashref.html#Tilde-Expansion](http://www.gnu.org/software/bash/manual/bashref.html#Tilde-Expansion))

---

### Post by stafio on 2010-09-10
Good news everyone! Broadcom has [open sourced their wireless drivers]("http://www.osnews.com/story/23786/BREAKING_BROADCOM_OPEN_SOURCES_WIRELESS_DRIVERS").

---

### Post by WarrenSH on 2011-08-23
I'm having the same issues and I did the below... 

> **chili555 said:**
> If it works fine if you issue the command, then it's healthy. Let's automate it:```
sudo su
echo b43 >> /etc/modules
exit
```Reboot, without the ethernet cable, and let us know how the wireless is working.

After the restart it still did not work for me. 

I did this in the terminal **lspci | grep Broadcom\ Corporation** and this is the outcome 

```
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

---

### Post by RavanH on 2011-10-26
> **WarrenSH said:**
> I'm having the same issues and I did the below... 



After the restart it still did not work for me. 

I did this in the terminal **lspci | grep Broadcom\ Corporation** and this is the outcome 

```
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```


Simply do ```
sudo apt-get install firmware-b43-installer
``` in a terminal window :)

---

