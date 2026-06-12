---
title: "Maximum supported version of firefox Ubuntu 15.10"
date: 2017-05-22
forum: Ubuntu/Debian BASED
---

### Post by goostech on 2017-05-22
So i had WAY to many problems with ubuntu 16.xx, the gnome based "Software Center" it refusing to download apps never connecting and, the whole RAM issue, do you know how EXPENSIVE DDR2 RAM is???? Canonical must think all the users are rich and can afford 112 USD for a stuck of DDR2 4GB, but i decided to downgrade to 15.10 or Zorin OS 11, now everything was perfect only 800MB of ram was used and not 1.8GB i wasnt encountering any wireless card issues, but then i kept getting notifications that this and that was out of date and wen i want to about firefox i was running 47.0 and all i want to know is, what is the maximum supported version of Firefox in ubuntu 15.10 i cant use chrome, and if 47.0 isnt the max supported version then how do i upgrade software updater says everything is up to date

---

### Post by mörgæs on 2017-05-22
If the hardware is too weak for a recent Ubuntu it's never a solution to install an old one. Your best option is a fresh install of Lubuntu 16.04.2.

After that you should change all passwords.

---

### Post by goostech on 2017-05-22
my hardware is not weak at all i just dont have alot of ram, also that "never a solution" worked for me at 16.10 at idle i got a minimum usage of ram at 1.8GB. On 15.10 my minimum usage of ram was 800MB

---

### Post by howefield on 2017-05-22
> **goostech said:**
> but i decided to downgrade to 15.10 or Zorin OS 11, now everything was perfect

Can't be perfect since both are end of life, meaning no support and no updates whatsoever. Which is that you are using, Ubuntu 15.10 or Zorin 11 ?

> but then i kept getting notifications that this and that was out of date and wen i want to about firefox i was running 47.0 and all i want to know is, what is the maximum supported version of Firefox in ubuntu 15.10 i cant use chrome, and if 47.0 isnt the max supported version then how do i upgrade software updater says everything is up to date

As above, Ubuntu 15.10 is end of life therefore shouldn't be used.

---

### Post by mörgæs on 2017-05-22
> **goostech said:**
> On 15.10 my minimum usage of ram was 800MB

If you try Lubuntu I expect you will get well below that.

---

### Post by goostech on 2017-05-22
i use Zorin OS 11 witch is based off of Ubuntu 15.10

i dont want to use Lubuntu becuase the ui is bland and boring and looks like the walmart version of Gnome 2

---

### Post by howefield on 2017-05-22
> **goostech said:**
> i use Zorin OS 11 witch is based off of Ubuntu 15.10

Thread moved to the "Ubuntu/Debian BASED" forum.

As said above, this version is unsupported so not surprising that you are having issues with "out of date" software applications.

---

### Post by goostech on 2017-05-22
im starting to wish Zorin devs only used LTS releases for there zorin OS

its a small price i have to pay for a Software center that works, i mean when i was using Zorin OS 12 i would have random permanent system lockups, like something would happen and i just couldn't get the computer to function like it did before, like one time i installed some updates for OS 12 and when i restarted all hell broke loose, it took 15 minutes to boot (on an SSD!) and when it did literally it was just a console and scrips and other stuff was just flowing, and another time i installed Nvidia Drivers for my GPU and when i restarted the mouse stops working like COMPLETELY, the trackpad and external mouse didnt work, i even tried the Trackpoint. Nothing, the other time is when i tried to get tap to click for the trackpad to work, because it didnt work out of the box on Zorin OS 12, Zorin os 11 nothing went wrong, when using Zorin OS 12 the Distro would last about 4-6 days before i had to do a clean install because of some BS issue, this OS 11 lasted and entire week and no problems yet and i want to keep it that way

---

### Post by gordintoronto on 2017-05-22
Using an old OS just asks for trouble. Consider Ubuntu Mate 17.04, which runs like gang busters with 2 GB of memory and an SSD.

---

### Post by Dennis N on 2017-05-22
> all i want to know is, what is the maximum supported version of Firefox in ubuntu 15.10

14.04 is able to use the latest version - Firefox 53.0.2 as of today; so could 15.10.

---

### Post by goostech on 2017-05-25
well, Dennis how would i be able to update?

---

### Post by vasa1 on 2017-05-26
> **goostech said:**
> well, Dennis how would i be able to update?

Update what to what :???:

---

### Post by goostech on 2017-06-15
i already use MATE on my T60, and its OK

---

### Post by goostech on 2017-06-15
Update Firefox

---

### Post by QIII on 2017-06-15
By updating your OS to a supported release so that you have access to a repo containing it?

---

### Post by Dennis N on 2017-06-15
> **goostech said:**
> Update Firefox

Mozilla offers it's Firefox version for Linux directly from their web site as a download. Most likely will work with your Zorin.
Try:

[https://www.mozilla.org/en-US/firefox/new/](https://www.mozilla.org/en-US/firefox/new/)

and click "Free Download". You will be offered a .tar.bz2 file - current Firefox is firefox-54.0.tar.bz2. 

Open with archive manager, and extract the firefox folder to Desktop. Using sudo, copy the folder to /opt and once it's there, change owner of folder and contents to your user (otherwise, it will not automatically install updates). Then you need to create a new menu entry or a new launcher to start the firefox executable file (firefox) inside that firefox folder. No need to remove the old Firefox.

---

