---
title: "Starcraft 2 Crash"
date: 2010-08-11
forum: Wine
---

### Post by jc4orr on 2010-08-11
I just built fresh system running 10.04. I installed wine and it is version 1.2. I got SC2 and tried to run it on my desktop, since it wouldnt run that great on my laptop. I followed an instruction on a site about how to install it, and it installed and ran the patch. when I double click on the icon, I get an error screen. I tried to open the map editor, to see if I could, and I got the same error. I have seen that people can play SC2 in wine, but havent had any luck. any help is appreciated.

---

### Post by urbanus on 2010-08-12
Try PlayOnLinux (aka POL)!

> sudo apt-get playonlinux

Its a free graphical tool to configure wine. But install it using the digital download version from battle.net, the DVD install didn't work for me at least.

Also sound doesn't work out of the box, but just right click on the game and choose configure wine. Now click on the libraries tab and find "mmdevapi" in the dropdown box (or copy paste it), add it, choose it in the list below and click the edit button, select "Disable". Now sound should work.

If you have an Ati card and get graphic corruption, check here:
[http://ubuntuforums.org/showpost.php?p=9710988&postcount=48](http://ubuntuforums.org/showpost.php?p=9710988&postcount=48)

Other threads:
[http://ubuntuforums.org/showthread.php?t=1435314](http://ubuntuforums.org/showthread.php?t=1435314)
[http://ubuntuforums.org/showthread.php?p=9710998](http://ubuntuforums.org/showthread.php?p=9710998)

Questions?

---

### Post by jc4orr on 2010-08-12
thanks for the response. 
but I tried the first thread a couple of times, and still no luck. and I have an NVIDIA 9500GT, not an ATI. I know its not the best, but its above the card Blizzard recommends.
Right now, it is installed and fully patched, but when I start it, sometimes it will log me out, and other times not open, but run in the background.

---

### Post by jc4orr on 2010-08-13
Right after I posted ^that, I updated wine to 1.3 and updated the NVIDIA driver, I thought it was the most up-to-date, but it wasnt. after I did that it started right up. Ive been busy playing, and havent had any problems yet. thanks for the advice though.

---

### Post by urbanus on 2010-08-13
Glad things worked out :-)

PS! Just know that Windows will give you better performance with this specific software, but you probably know this :-P

---

### Post by beastrace91 on 2010-08-16
> **jc4orr said:**
> Right after I posted ^that, I updated wine to 1.3 and updated the NVIDIA driver, I thought it was the most up-to-date, but it wasnt. after I did that it started right up. Ive been busy playing, and havent had any problems yet. thanks for the advice though.

Glad to hear it! Most Wine issues are solved by A.) Upgrading Wine or B.) Upgrading graphics drivers :D

~Jeff

---

