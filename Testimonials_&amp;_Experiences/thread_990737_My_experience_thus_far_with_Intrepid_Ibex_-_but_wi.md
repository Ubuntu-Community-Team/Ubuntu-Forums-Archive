---
title: "My experience thus far with Intrepid Ibex - but will it continue?"
date: 2008-11-23
forum: Testimonials &amp; Experiences
---

### Post by ispyamoose on 2008-11-23
Greetings.

First off, I would like to say that I really want to use Ubuntu. In addition, I would like to continue using this operating system. I have been an advanced user of Windows for a very long time, but I don't really see Windows products being the prime operating system any more. Yes, Windows Vista is bad, and everyone knows that. Now the word on the street is that there is an "expansion pack" for Vista coming Holiday 2009, in the form of Windows 7. 
Besides that stuff, Ubuntu seems great on the outside, but lots of things are still difficult to use (at least for me). Just because the OS is open source doesn't mean it has to be a pain in the butt to use.

I want to point out that using an operating system should not involve building part of its overall functionality by yourself. The goal of an operating system should be to help the user get things done quickly and efficiently. I would be more apt to experiment with the "terminal" or other such things if I didn't have any fears of accidentally terminating my system.

My system:
Ubuntu Intrepid Ibex 8.10
Dell Vostro 1500
Core2 Duo T9300 @ 2.5 GHz
4 GB DDR2 667 MHz
250 GB SATA 7200 RPM
Integrated Sigmatel Audio
8600M GT 256 MB
Dell Wireless N 1505 (I think)
Bluetooth 2.0
Built-in webcam

Peripherals
Logitech MX-518 Mouse
Microsoft Internet Pro Keyboard
Microsoft LX-3000 Headset

---

**[COLOR="Red"]NOTE THAT I COULD VERY WELL BE WRONG ON MY OPINIONS BELOW:[/COLOR]**

The good things:

The OS is free.

Tight security.

No threat of computer viruses? Or at least that's what I've heard..

Relatively easy-to-use user interface with lots of options for themes/customization.

Decent open source alternatives for most business/school oriented commercial software (some of which I was already using with Windows XP).

The OS seems light on the memory and the cpu.

Multiple desktop views from one screen.

---

The bad things:

USB headset + anything with sound = bad. I've found it impossible to configure my USB headset (Microsoft LX-3000). [COLOR="Red"]I would appreciate having some help with getting my headset to work. I have done search after search looking for a solution![/COLOR]

Occasionally buggy/flickering user interface.

Setting up a wireless connection. From what I've seen it's all manual. Plus, there's no way to install proprietary drivers in a way that is obvious to a novice. I still haven't figured it out.

Installing drivers for hardware besides a video card. Who the h*** wants to compile??? Installing .inf files for hardware does not work well, as most setups for Windows come in .exe. Extracting the .exe to find the .inf does not work for me.

Installing programs besides the ones listed in Add/Remove is a pain. Knowing what programs work and how to configure them often leads back to the terminal.


So there you have it. Feel free to comment on any mistakes I've made. I'm sure there are some.

---

### Post by a0u on 2008-11-23
> **ispyamoose said:**
> 
I would be more **apt** to experiment with the "terminal" or other such things if I didn't have any fears of accidentally terminating my system.

I find your use of the word "apt" ironic, considering APT is Ubuntu's software installation tool that works via command-line...
In all seriousness, though, GNU/Linux and other *nix OS's [have their differences from Windows]("http://linux.oneandoneis2.org/LNW.htm"), and learning how to use the terminal is a great advantage since it's currently the most common (and reliable) way that solutions are given.  There are some [helpful online tutorials]("http://ubuntuforums.org/showthread.php?p=990636"), if you need them.
Much of the system configuration in GNU/Linux involves text files (another *nix convention), and so always be sure to do a backup before editing.  As long as you're careful, permanently crashing your installation remains a remote possibility.

A flickering display may either mean a bad graphics driver or bad X.Org configuration.  You may want to post about it in more detail.

As for wireless...
People have managed to get the Dell Wireless N 1505 [working using the bcm43xx driver]("http://ubuntuforums.org/showthread.php?t=859693"), which should be included in the kernel by default, if you're using 8.04 or later.

Yeah, drivers in GNU/Linux need some more work, but it's difficult if the hardware vendors are uncooperative.  If you can, please help out the developers by offering user feedback, bug reports, etc.


Tip: in fixing problems with peripheral hardware, it helps to know what you are dealing with.
Call up hardware information with the terminal command:
```
sudo lshw
```It will prompt you for your password (for security reasons, your password will not be echoed back as you type it in).
Or if you prefer a "Device Manager"-like GUI:
```
sudo aptitude install gnome-device-manager
```and then run the program with
```
gnome-device-manager
```I hope this post helps. ;)

---

### Post by stalkingwolf on 2008-11-23
> Installing programs besides the ones listed in Add/Remove is a pain.

I dont see how synaptic could be any easier, Mark for install > apply > apply.

Removing applications is just as easy.

---

### Post by Lapp-Same on 2008-11-23
> **ispyamoose said:**
> 
My system:
Ubuntu Intrepid Ibex 8.10
Dell Vostro 1500
Core2 Duo T9300 @ 2.5 GHz
4 GB DDR2 667 MHz
250 GB SATA 7200 RPM
Integrated Sigmatel Audio
8600M GT 256 MB
Dell Wireless N 1505 (I think)
Bluetooth 2.0
Built-in webcam

Peripherals
Logitech MX-518 Mouse
Microsoft Internet Pro Keyboard
Microsoft LX-3000 Headset



After what I can see you are using a Latop, right?
If you do so i would HIGLY recommend you to forget Ubuntu!!

And I can say this because I've tried with 7 diffrent laptops, and you would get it to work at the end, but if you dont wanna program and install the next months and wanna have somthing that just works i RECOMMEND you to use Linux Mint, otherwise if you have a DESKTOP that just works i RECOMMEND Ubuntu! soo my final comment is

Latop = Use Mint
Server = Ubuntu!
Desktop = Ubuntu!
PDA = Ubuntu!

---

### Post by ispyamoose on 2008-11-23
> **Lapp-Same said:**
> After what I can see you are using a Latop, right?
If you do so i would HIGLY recommend you to forget Ubuntu!!

And I can say this because I've tried with 7 diffrent laptops, and you would get it to work at the end, but if you dont wanna program and install the next months and wanna have somthing that just works i RECOMMEND you to use Linux Mint, otherwise if you have a DESKTOP that just works i RECOMMEND Ubuntu! soo my final comment is

Latop = Use Mint
Server = Ubuntu!
Desktop = Ubuntu!
PDA = Ubuntu!

So what are the advantages/disadvantages of using Mint instead of Ubuntu? I have already had a tough time so far with Ubuntu working on my laptop, like you've said, but would Mint really be any easier?

---

### Post by Lapp-Same on 2008-11-23
> **ispyamoose said:**
> So what are the advantages/disadvantages of using Mint instead of Ubuntu? I have already had a tough time so far with Ubuntu working on my laptop, like you've said, but would Mint really be any easier?

I installed it for my old school on theire Laptops and they are 4-5 years old and where just to install and everything worked

offcourse i MAY happend that you have to Install 1 or 2 things but to a Laptop it is 1000 times easier to use, maintance and install

I reallt Recommend you t use Mint for a Laptop!

---

### Post by ispyamoose on 2008-11-23
> **Lapp-Same said:**
> I installed it for my old school on theire Laptops and they are 4-5 years old and where just to install and everything worked

offcourse i MAY happend that you have to Install 1 or 2 things but to a Laptop it is 1000 times easier to use, maintance and install

I reallt Recommend you t use Mint for a Laptop!

How well does Mint work for wireless networking and Nvidia graphics cards? I've also had trouble with my usb headset while using Ubuntu. Do you know if I would still have the same trouble with my headset while using Mint?

---

### Post by spawn. on 2008-11-23
As far as  your wireless goes, 8.04 and 8.10 is extremely user friendly - even while under WEP. Now WPA, is a different story. It usually requires you to edit the config files and what not. NDiswrapper installation tool should make the process easier. It works well with Windows Drivers and your wireless hardware.

That is just one of many tools you can find in the synaptic package manager that would make it a breeze to configure your wireless. It's basically as easy as point, click, enter information, and there you go. I think the biggest problem you have is getting used to a new OS. During this period, I would dual boot Windows/Ubuntu.

---

### Post by Lapp-Same on 2008-11-23
> **ispyamoose said:**
> How well does Mint work for wireless networking and Nvidia graphics cards? I've also had trouble with my usb headset while using Ubuntu. Do you know if I would still have the same trouble with my headset while using Mint?

One big RULE in Linux is:
All Nividia cards Are the BEST thing to use on every linux distros.

And on those old machines wit old hardware everything worked! The Wireless did work from install, Grapich where old ATI-card and it did work, and the USB thing i'am affraid I dont know if gonna work, but the intregrated sound did work from install.

and it is supposed to be easy to use and rock solid

---

### Post by ispyamoose on 2008-11-23
> **spawn. said:**
> As far as  your wireless goes, 8.04 and 8.10 is extremely user friendly - even while under WEP. Now WPA, is a different story. It usually requires you to edit the config files and what not. NDiswrapper installation tool should make the process easier. It works well with Windows Drivers and your wireless hardware.

That is just one of many tools you can find in the synaptic package manager that would make it a breeze to configure your wireless. It's basically as easy as point, click, enter information, and there you go. I think the biggest problem you have is getting used to a new OS. During this period, I would dual boot Windows/Ubuntu.

Well, Ubuntu hasn't been too terribly friendly with the wireless card I have. I have configured my router to use WEP, and I've gone into the network settings on Ubuntu to add SSID, etc, to make the connection. The result? It doesn't work. It's interesting that the wireless configuration is not automatic for me.

---

### Post by ispyamoose on 2008-11-23
> **Lapp-Same said:**
> One big RULE in Linux is:
All Nividia cards Are the BEST thing to use on every linux distros.

And on those old machines wit old hardware everything worked! The Wireless did work from install, Grapich where old ATI-card and it did work, and the USB thing i'am affraid I dont know if gonna work, but the intregrated sound did work from install.

and it is supposed to be easy to use and rock solid

I also have an external microphone and a built-in webcam. I'm afraid I won't have fun getting those to work.

---

### Post by Lapp-Same on 2008-11-23
> **ispyamoose said:**
> I also have an external microphone and a built-in webcam. I'm afraid I won't have fun getting those to work.

The internal microphone did work for me in Mint, but i dont have a intregrated cam so that i dont know... =)

---

### Post by Lapp-Same on 2008-11-23
> **ispyamoose said:**
> I also have an external microphone and a built-in webcam. I'm afraid I won't have fun getting those to work.

One more thing i dont see wat you have to loose trying Mint, and if you dont like it, Ubuntu isn't gonna Run away

or 

If you wanna Use Ubuntu, Mint are neigther gonna run away for future testing ;)

---

### Post by ispyamoose on 2008-11-23
> **Lapp-Same said:**
> One more thing i dont see wat you have to loose trying Mint, and if you dont like it, Ubuntu isn't gonna Run away

or 

If you wanna Use Ubuntu, Mint are neigther gonna run away for future testing ;)

I'm considering giving Mint a try. It wouldn't hurt anything since I have a week off of college anyways.

---

### Post by Lapp-Same on 2008-11-23
> **ispyamoose said:**
> I'm considering giving Mint a try. It wouldn't hurt anything since I have a week off of college anyways.

=) I hope for a replay on how it did goes! =)

---

