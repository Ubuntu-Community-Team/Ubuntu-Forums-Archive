---
title: "HOW-TO : Ubuntu + Wine + Garena + WarCraft 3 TFT"
date: 2011-04-11
forum: Wine
---

### Post by Ramon444 on 2011-04-11
As a fan of Dota i decided to try to play Dota via Garena under Wine in Ubuntu 10.10

And here Is HOW-TO:

1. You need to have installed Ubuntu or any other Linux distro you use. Also i had installed proprietary driver for my video card for better Video performance.

2. You need to install Wine 1.3.16-18 (with previous versions i didn't tested). Don't install any library's or programs from winetricks, especially any version of IE, cause wine 1.3.16 and higher have it already. Else GUI of Garena will not work normally. AND set it to WinXP mode.

3. Install latest Garena from [www.Garena.com](www.Garena.com)

4. Now you need to install Warcraft + TFT or use Warcraft TFT folder (licensed install) already installed under windows and just copy it to Program Files folder in Wine. And download DOTA map to maps/downloads (as in windows).

5. To have normal scrolling of Map in game go to Compiz settings -- >> Cube Rotations -->> Tab Binds -- >> here in Cube Rotation put NONE to rotation_flip_left_edge and rotation_flip_right_edge

6. To be able create games you need to open Warcraft and Garena ports in your firewall (6112-6113 , 1513).

7. Then launch Garena, enter your login info and DON'T forget in Advanced network settings to check UPnP Port forward.

8. In Garena settings enter the route to war3.exe and press update

9. Then just select needed room, and press start game. Go to settings and enter your Video settings.

10. And now have fun in playing DOTA in Linux :)



If you will have any questions, ask me here in this thread and i will try to help you. :)


P.S. After you will start WarCraft from Garena you will not be able to switch via Alt+Tab to Garena until you will exit Warcraft.

P.P.S In case of not working keyboard in game just use Alt+Tab and select war3 window. But on my PC all worked fine without Alt+Tab.

---

### Post by Erufailon on 2011-04-20
I have a problem with Garena. It crashes at startup with a message that's saying if I want to sent a report. Any ideas why is this happening?
Warcraft works fine by itself but I can't manage to run Garena

Edit : I set wine to winXP and worked fine (win2008SP2 by default)

---

### Post by Ramon444 on 2011-04-21
> **Erufailon said:**
> Edit : I set wine to winXP and worked fine (win2008SP2 by default)
Yes, my wine is set up like it's WinXP too. And i recommend to use WinXP mode for all programs you want to use in wine, it's more stable and developed.

---

### Post by lun on 2011-05-22
Ok. I have followed this howto step by step and i am on step 9. I click 'start game' in garena and wc3 starts. I click on LAN and no games show up.  I can play wc3 and dota fine offline on wine.

So, this has me wondering what could be wrong. My first guess is that somehow my ports are not forwarded correctly. Under port forward range i have ports 6112 to 6113 enabled under my correct internet address (verified using ifconfig) for wc3 and 1513 for garena.

I have even turned off firewall protection under security and block anonymous internet requests(linksys) just to check.

Second that the dota map is not in the right directory. I have it in C:\Program Files\Warcraft III\Maps\Download as directed by [http://www.getdota.com/install_guide](http://www.getdota.com/install_guide)

I have configured garena in the way instructed. I checked UPnP Port forward and set the path to war3.exe.

The only difference from this guide is the version of wine: wine-1.3.20. The dota version: DotA v6.72b.

I have tried the stable version of vine (1.2.2) also with the same results.

Any suggestions?

Thanks,
Nick

EDIT: Ok. found out that all the rooms i was joining were not hosting any games. :oops: Thanks for the awesome guide; it solved more than one of my problems :D

---

### Post by Ramon444 on 2011-05-23
> **lun said:**
> EDIT: Ok. found out that all the rooms i was joining were not hosting any games. :oops: Thanks for the awesome guide; it solved more than one of my problems :D

Nice. :D Have fun. :)

---

### Post by drake on 2011-05-23
Is there a way to get it to play in a higher res maybe 1680x1050 ?

---

### Post by Ramon444 on 2011-05-23
> **drake said:**
> Is there a way to get it to play in a higher res maybe 1680x1050 ?

I don't know. It can be game limit. I play 1280x800 on my laptop.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-26
how do i change ports in firewall? (i dont think i have one)

---

### Post by Ramon444 on 2011-05-26
> **gyyug78fg87ogguiioioioioi said:**
> how do i change ports in firewall? (i dont think i have one)

By default they all are open. But in router by default ports are closed (so you must set up port forwarding)

---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-26
cool with your fast reply! :D
wich firewall should i download?

---

### Post by Ramon444 on 2011-05-26
> **gyyug78fg87ogguiioioioioi said:**
> cool with your fast reply! :D
wich firewall should i download?
Firewall is already installed by default in Ubuntu. BUT if you are not expirienced with console commands, install Firestarter (It's good GUI for it). How to set up it you can find many guides in internet.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-26
ok i installed it now firestarter can you please tell me how i change the ports?

---

### Post by Ramon444 on 2011-05-26
> **gyyug78fg87ogguiioioioioi said:**
> ok i installed it now firestarter can you please tell me how i change the ports?
Try to read here - [http://firestarter.sourceforge.net/manual/wizard.php]("http://firestarter.sourceforge.net/manual/wizard.php") and on other sites.
P.S Firestarter is offtopic in this Thread. And you don't need to install it to play DOTA(warcraft, etc).

---

### Post by LeonYeap on 2011-06-28
hello.. thx for the guide.. it was very useful...but got small problem.. when i start the game... the error message no base sound is found... and the is no voice when play.. got any solution.. thx in advance:p

---

### Post by Ramon444 on 2011-06-28
> **LeonYeap said:**
> hello.. thx for the guide.. it was very useful...but got small problem.. when i start the game... the error message no base sound is found... and the is no voice when play.. got any solution.. thx in advance:p

In other applications you have sound or no ?

Well, i think that first of all you should check your WarCraft 3 installation, it must have all needed files and latest patch. So the best is clean install from original CD, or copy of full install from MS Windows. 
Also go into Wine settings and look in audiotab. When you first time go there it's look for default sound device in your PC, press apply(or OR), or if you know what must be there you can change it. And try to launch the game again.

---

### Post by Steam. on 2012-03-14
I'm having issues with this.I use the latest Wine(1.4-rc6).I can install Garena and War3, but, if i go to Garena, and select a room, the next screen doesn't show the start game button.Infact, half of the middle part is gray (including the location of the start game button).I tried click anywhere but it's not there.Help?

---

### Post by rousseau09 on 2013-02-13
> **Ramon444 said:**
> 
If you will have any questions, ask me here in this thread and i will try to help you. :)


Nice guide. Works fine the first time in Ubuntu 12.04LTS and Wine-1.4. Thanks. 

Few questions, are you able to run Warcraft3 in full screen mode? (means no black border) How to turn off "Maintain Aspect Ratio"?

Also when you run GarenaMessenger.exe, and press the X button on top right, it disappears and is not available in any screens/placeholder anymore. Is there a solution to that?

Apart from that, kudos to you for writing it up nice and concisely.

---

### Post by Ramon444 on 2013-02-13
> **rousseau09 said:**
> Nice guide. Works fine the first time in Ubuntu 12.04LTS and Wine-1.4. Thanks.
Few questions, are you able to run Warcraft3 in full screen mode? (means no black border)
Yes, i run it in full screen mode.

> **rousseau09 said:**
> How to turn off "Maintain Aspect Ratio"?
Maybe in settings ? I am not sure, it was OK for me on 15" wide laptop screen.

> **rousseau09 said:**
> Also when you run GarenaMessenger.exe, and press the X button on top right, it disappears and is not available in any screens/placeholder anymore. Is there a solution to that?

Don't close it. Thats all i can say.

> **rousseau09 said:**
> Apart from that, kudos to you for writing it up nice and concisely.
you're welcome

---

### Post by randy87p on 2013-06-10
hi i was able to install garena with wine 1.5.31 on ubuntu 12.04LTS. but when i run it i get:

fatal error: access denied! pleas try to run garena plus as administrator once to solve this problem

anyone know a fix for this?

---

### Post by bmx666 on 2013-06-24
> **randy87p said:**
> hi i was able to install garena with wine 1.5.31 on ubuntu 12.04LTS. but when i run it i get:fatal error: access denied! pleas try to run garena plus as administrator once to solve this problemanyone know a fix for this?run it with root user.my Q: after garena start, when click on my friends or setting , garena close!!what can i do now?

---

### Post by ukhupacha on 2013-10-21
> **bmx666 said:**
> run it with root user.my Q: after garena start, when click on my friends or setting , garena close!!what can i do now?

Hell i'm having the same problem
everytime that i want to see settings garena closes

---

### Post by kutalion on 2013-10-30
Well, to put it gently - Garena doesn't work under Ubuntu anymore since year and a half back (more precisely 12.04). I wasn't able to particularly pinpoint the problem but WineHQ forums suggested incompatibility with latest openssl package. Oh, here comes the fun part - the old one is still in repos but you can't remove 1.0 since everything there is depends on this one and installing 0.98 (as I remember this was the version - too lazy to open Synaptic right now) won't do anything for Wine and particularly the connection problem Garena faces. And yeah, don't install it under XP simulation. It won't open at all.
   The only thing Garena can do right now is to only log-in and chat with your friends. The rooms window is COMPLETELY unavailable. If you click LAN Garena friezes for a few seconds and then nothing happens after it unfreezes. I also tried force starting the Room.exe but it authenticates me with the server forever. AND further more any error that Garena throws at you is kinda generic and doesn't actually stop it operating in any way. I've investigated almost all of them for days. Nothing budges at all. So Garena+Ubuntu (and few other OSes too) is a no-go.
   In conclusion I must say that I presume that having older systems that don't change their base (like 2010-2011 portable Linux - e.g. Puppy Lucid) COULD do the trick but then you'd have to dualboot just to play a game which is almost equal to having your old 'doze around for the same purpose (if we don't take into account that Puppy is actually about 200 megs and doesn't need partitioning of you hard drive, which is good for me because I only have 160GB, and it loads faster). You could always use virtual machine but I must warn you that they are slower than Wine's performance and can't actually use (fully) enhanced OpenGL graphics card (if this wasn't already obvious).

All may have a good day.

---

