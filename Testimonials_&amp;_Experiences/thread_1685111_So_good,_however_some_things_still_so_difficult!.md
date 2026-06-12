---
title: "So good, however some things still so difficult!"
date: 2011-02-10
forum: Testimonials &amp; Experiences
---

### Post by Judson J on 2011-02-10
Hi all, I love ubuntu, and so does my girlfriend who knows nothing about computers. we have installed 10.10, and its great for 99% of home work.
But as a user myself, who knows a lot more about OS than her, I am still very frustrated. It seems that so many things in ubuntu work seamlessy, flawlessy, automatically, simply, wonderfully and yet, some other parts are still only for geeks, like deleting a program, or getting wireless to install (the help menu mentions an icon but I dont know what it looks like)(things that could be made easy, but are seemingly very frustrating). Some other things are made so basic, like installing google earth, that if it doesnt work, theres no obvious solution on how to fix it, unless your a geek. 
Plugged in an ethernet cable, we had internet without doing anything at all! Tried wireless, and it wont even see the router! why!?  
Installed google earth, says its fine, but its not anywhere to be found on the machine to run, or delete!
and then you get offered solutions like go to some drive sector called e09/dhoujd/ doyd/ doid or whatever, and run dos and blah blah...some lenthgy and detailed manouvre to do a 1 button function, with someother quite basic function.
yes, I am not an expert, but I've been well trained by my nerd buddy. Now i see that 99% of computer probs are software related, and that these day computers have more in common than differences. My buddy installed a xp hard drive on a mac, no big deal! And so to get ubuntu, so good, for free, Im in smooth computer heaven. Except that some things still require a deep technical know how, and other things are so bubble gum easy it puts mac/PC to shame ( not that I mind having it made easy) (10 years of computer frustration, and this is the only light).
So please, ubuntu, 10 out of 10, but it could be 11! 
cheers
Judson

---

### Post by overdrank on 2011-02-10
Hi and welcome, this is not a support request so moved to Ubuntu Testimonials & Experiences. Good luck :)

---

### Post by cchhrriiss121212 on 2011-02-10
Some things are not obvious, but you can always ask for help, people here will be happy to explain things in non technical terms. :)

Regarding wireless it is likely you need a driver, so try using the Hardware Drivers app in the System menu. It will scan for anything that needs additional drivers and install them for you.

---

### Post by P4man on 2011-02-10
A few things; about google earth, what you install through Ubuntu software center is NOT google earth the app, but a little utility to help create a package. Google earth is not opensource, and probably due to licensing restrictions, not included in the repository. Just download it from google. More info here:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

As for removing apps; sure its easy. Same way you install it: software center? Just click installed software, and select anything you want to remove.

As for the command line interface, in short CLI, or terminal ('DOS' as you call it); I know how you feel. I remember being new to ubuntu and thinking the exact thing. It seems awkward and old fashioned. And its not intuitive. 

However, there are VERY good reasons why we use it so often. Its universal: it works on pretty much all versions of ubuntu, kubuntu, lubuntu, mythbuntu, xubuntu, even usually on debian, Mint, whatever other debian based linux version (even Nokia Maemo cell phones!), even though the GUI's would be **totally **different.   Its no fun having to write how to's for every possible GUI out there, there are so many!

CLI is also language independent. Ever tried following a tutorial written in French on an English or chinese PC? With the CLI, you usually can.

And since you can copy/paste commands and just as importantly, the **output **of the commands, its far and away the most efficient way for us to help you and for you to get our help. Trust me on that one.

Ill give you an example. You have problems with wifi. To help I need to know exactly what wifi card you have. Now, I could write half a page explaining how to get that information from the device manager using a GUI, and hoping you are using GNOME and not KDE. OR I can tell you to run

```
lspci
```

In a terminal and copy paste the result here. Which is faster?
BTW, do post the output, lets see what card you have and if we can fix it.

---

### Post by mastablasta on 2011-02-10
not to mention that you can copy command to the terminal. so you can give a lot of big commands at once.

---

### Post by Judson J on 2011-02-10
HI thanks all, yes I appreciate the command prompt; Im no programmer, but I appreciate what a terminal does, and I like the direct control- windows terminal turns me off learning it. Being able to cut and paste within it is not possible on windows, so Im totally open this.
So heres the wireless card results:

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
06:00.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
06:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

Im on her Packard Bell and have not trawled through it at all to check components (it was dead, so we installed ubuntu and here we are). She thinks its magic.
Am also having a bit of a video card issue (seems to be ghosting, flickering, and has an occasional 'memory' of pages viewed 10 pages back, while surfing net).
Thanks for the input
were in Lismore, Australia
cheers 
and isn't Mark Shuttleworth a champion?! he made ubuntu- what is ever going stop it from spreading?!

---

### Post by P4man on 2011-02-10
There is no wifi card in there. Perhaps its internally connected to the USB bus. Can you post the output of

```
lsusb
```

and perhaps also of

```
sudo rfkill list
```

As for the video glitches, did you install the nvidia drivers? Make sure you are connected to the internet, then go system > administration > hardware drivers.

---

### Post by rg4w on 2011-02-10
> **Judson J said:**
> ...And so to get ubuntu, so good, for free, Im in smooth computer heaven. Except that some things still require a deep technical know how, and other things are so bubble gum easy it puts mac/PC to shame ( not that I mind having it made easy) (10 years of computer frustration, and this is the only light).
IMNSHO the central reason for the remaining weaknesses in Ubuntu boils down to market share.  I know many here don't give a hoot about that, and as along-time Mac user I'm accustomed to working in a minority OS, so it's not about being in some sort of "in crowd" but something far more pragmatic:

More people using an OS means more contributors to fix issues like you described, and it also means more incentive for hardware and software to support the platform.

There are many reasons why Linux has remained at ~1% market share for so long, and we don't need to get into them here.

But my hope is that Ubuntu's continued emphasis on usability will eventually push those numbers up a bit, however slowly, so that one day Linux will reach the tipping point at which Google would be embarassed to deliver such a crappy installer for Google Earth, and all wireless vendors wouldn't think about shipping a wireless card without provide excellent Linux drivers, etc.

---

### Post by mips on 2011-02-10
Proper paragraphs would would attract more readers. I gave up after the third line.

---

### Post by Tamlynmac on 2011-02-10
> overdrank
Hi and welcome, this is not a support request so moved to Ubuntu Testimonials & Experiences. Good luck :)

Possible OOP's? Seems it may actually be a support question.

> Am also having a bit of a video card issue (seems to be ghosting,  flickering, and has an occasional 'memory' of pages viewed 10 pages  back, while surfing net).

Potentially, more than one. :D

---

### Post by jmszr on 2011-02-10
Judson J,

Just a thought, go to System > Preferences > Main Menu and in the lefthand panel click on Internet and check in the righthand panel to see 1.) if Google Earth is listed, and 2.) if it has been checkmarked. If it is not, of course, checkmark it. Just a thought.

---

### Post by Judson J on 2011-02-15
> **mips said:**
> Proper paragraphs would would attract more readers. I gave up after the third line.

Hi, thanks, no problem at all. If you read the whole thing you would see that I have not really asked a question. !. Its an open statement that you can interpret anyway you wish. Some have answered it beautifully. Isn't it a scream! The irony of the thread title is not lost on me.

---

