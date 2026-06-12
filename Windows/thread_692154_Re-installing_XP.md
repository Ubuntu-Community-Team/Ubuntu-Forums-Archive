---
title: "Re-installing XP"
date: 2008-02-09
forum: Windows
---

### Post by harley87 on 2008-02-09
I have recently partioned my hard drive to include XP and Ubuntu. I was on Vista before that. I am in the process now of creating a dual boot system for the 2 but have come across a problem with XP. I don't kniw if this is necessarily the best place to ask this but here goes. After installing XP my laptop is no longer picking up any sound device so I am not getting any sound playback from my internal speakers. Any idea on what may have caused this?

---

### Post by halitech on 2008-02-09
is this no sound in XP or in Ubuntu? If its in XP, probably a case of windows didn't load the drivers (surprise surprise) and you will probably just need to install the correct drivers. if its in Ubunut, might be a case of setting up ALSA with the right info and making sure its not muted.

---

### Post by harley87 on 2008-02-09
Yes in XP. Any ideas on how to go about installing those drivers?

---

### Post by halitech on 2008-02-09
you would need to know the manufacturer and model and then download the files and depending on what kind of card, could have an install.exe file or may have to do it manually.

ps. not to sound brash but this is a Linux forum, not windows so help in here may be limited (been 2 years since I've done much in windows except use it at work and not by choice)

---

### Post by mmb1 on 2008-02-09
Do you have the drivers CD that came with your computer?

---

### Post by stalkingwolf on 2008-02-09
You can try
right click My Computer
click properties
Click Hardware
click Device manager
click the + beside sound, video and game controlers
Double click your device
The box that opens will tell you if the device is working.
If not
click Drivers, Then
Click update drivers.

If that doesnt work you will have to go to the manufacturer.  Another place
you can try is driversguide.com   [http://www.driversguide.com]("http://www.driversguide.com")

---

### Post by amingv on 2008-02-09
Can you see the little speaker icon next to your clock? If not it's almost certain you need to get a driver. It's not that hard to find the in the manufacturer's webpage. (Assuming the network card has it's drivers working.)

After that it's all about clicking on a (glorious?) exe file.

---

### Post by p_quarles on 2008-02-09
Thread moved to Windows Discussions.

---

### Post by r76 on 2008-02-11
Was your laptop supplied with Vista? I got a Dell D630 latitude and the drivers worked fine in Vista but not in XP.  I had to reinstall everything XP in a very specific order, inserting some modules early on - the "dell utility" driver had to be installed before chipset etc.  When I was googling for the answer I saw the issue affects some other Latitudes and also Thinkpads using intel HDA audio, or something like that...

---

### Post by frankhdz on 2008-02-12
> **halitech said:**
> is this no sound in XP or in Ubuntu? If its in XP, probably a case of windows didn't load the drivers (surprise surprise) and you will probably just need to install the correct drivers. if its in Ubunut, might be a case of setting up ALSA with the right info and making sure its not muted.

LOL people like this crack me up. As if Linux is that much easier. It's easier to find and install drivers on Windows than it is on Linux. It was a nightmare trying to get a Graphics card running on Linux.

---

### Post by halitech on 2008-02-13
Never said it was easier in Ubuntu then in windows, just that it was no surprise that windows didn't load the drivers when he reloaded windows as I have never had windows detect and load much of anything in the way of add on cards in the 15 years I was using it. 

Far as finding them, if you know every detail about the card (be it video card, sound card, NIC, whatever) and you know where to look then yes, it's relativily easy. If you have some unknown brand, good luck getting it to work in either system. Far as Linux, other then the odd sound card issue (ussually ISA cards) and setting up a TV Tuner card, I've had basically no issues getting anything to work and my video card worked out of the box on the initial install.

---

### Post by frankhdz on 2008-02-13
> **halitech said:**
> Never said it was easier in Ubuntu then in windows...

Ubuntu is the same for me my video cards did not work right away I know every detail about my system because I built it and even when I know all that I could not get Ubuntu to play nice with my hardware.

I never got it to work actually.

---

### Post by halitech on 2008-02-13
Guess I got lucky then (nice thing about having older hardware, its mostly supported by now) but I know some people do have a lot of trouble with video cards if they want/need the latest drivers. Guess I'm lucky cause as long as it will do the resolutions I want, I don't worry much about 3d graphics and the special effects. Sorry to hear you couldn't get the graphics to work properly but maybe another distro will work with your hardware better then Ubuntu will.

---

### Post by SunnyRabbiera on 2008-02-13
> **frankhdz said:**
> LOL people like this crack me up. As if Linux is that much easier. It's easier to find and install drivers on Windows than it is on Linux. It was a nightmare trying to get a Graphics card running on Linux.

Thats because windows has the $$$, really though windows has its own problems... viruses, spyware, addware...

---

### Post by frankhdz on 2008-02-15
Adware and viruses are a problem only if you are stupid enough to download games from the web and open every single email from people offering to "enlarge" or promising to show you pics of some celebrity. 

I have never had problems with viruses. Don't get me wrong I'd like to switch to Ubuntu but it does not work with my hardware, my setup is not brand new hardware either it's failry old about 4 years old and the drivers for my hardware do not work. Mainly my dual screens I can't use ubuntu if it cannot do dual screens. I can't go back to using one screen.

---

