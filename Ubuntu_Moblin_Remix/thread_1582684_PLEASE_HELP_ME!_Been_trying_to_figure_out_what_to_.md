---
title: "PLEASE HELP ME! Been trying to figure out what to do for 8 hours! NEED HELP!"
date: 2010-09-26
forum: Ubuntu Moblin Remix
---

### Post by Bonger6693 on 2010-09-26
Ok, so here is the story.  I bought my wife a netbook for her bday and it came with no O/S on it.  So I read up on ubuntu netbook remix and it sounded really nice so I installed it on the netbook.  Seems to have problems with the trackpad not working. Some times it works and some times it doesn't, the computer is a Asus Eee PC H1005.  So anyways the wife got it yesterday and it still is giving us fits so we said screw it and we want to put XP on it.  So I have been spending all day today trying to get it on.  Now I got pretty much everything done until I actually have to go and install it on the HD.  I go and load up windows setup and the only HD it sees is my flash drive with XP cd on it.  I know now after reading that I should have had XP on it first THEN did ubuntu.  So please PLEASE tell me that I can put XP on this netbook somehow...:confused::(

---

### Post by kerry_s on 2010-09-26
are you booting from the flash drive?

---

### Post by jjakspaw6 on 2010-09-26
I personally have not attempted to install XP from anything other than a cd. If possible get a USB CD drive and install from that....

---

### Post by snowpine on 2010-09-27
A good question for a Windows forum. Ubuntu does not have any special utilities for installing Windows. :) 

One of my favorite forums for EEE questions is [http://forum.eeeuser.com](http://forum.eeeuser.com)

---

### Post by Chris1274 on 2010-09-27
You can always boot from a live USB and shred the HDD. Then you can start over from square one and install whatever OS you like.

---

### Post by CharlesA on 2010-09-27
The only thing you would have to do if you didn't install Windows first, is reinstall GRUB. Not a huge deal imo.

As for installing XP from USB: I've used [WinToFlash]("http://wintoflash.com/home/en/") before and it worked decently.

---

### Post by lbrty on 2010-09-27
> **Bonger6693 said:**
> I go and load up windows setup and the only HD it sees is my flash drive with XP cd on it.

If you did not slipstream the SATA drivers into the Windows XP OS disc before attempting to install Windows on the netbook, then that is why Windows cannot recognize the SATA hard drive (if the netbook has a SATA hard drive). Microsoft added the SATA drivers to the OS disc after Windows XP.

Does the netbook have a SATA hard drive? If you want to install Windows XP and the netbook does have a SATA hard drive, you need to download the SATA drivers and either slipstream with nLite or get a USB floppy drive, copy the drivers onto a floppy, and then press F5 or F6 to load the drivers at the beginning of the install of Windows XP. Slipstreaming is much easier and quicker.

Slipstreaming program (for Windows environment)
[http://nliteos.com/](http://nliteos.com/)

How to slipstream
[http://digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/]("http://www.digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/")

---

### Post by Bonger6693 on 2010-09-27
Hmm well maybe I did not clearly say what was going on from the first couple responses.  I have xp on a flash drive using usb_multiboot10.cmd.  So the usb drive is bootable, so I boot off that after restart and it loads up the windows install.  When I go to install it on the HD there is no HD to install it on other than the flash drive.  I need to know the easiest way if there is one to get the HD to show up to format it so I can put windows on it.  I really hope there is a way for this to happen..

---

### Post by Bonger6693 on 2010-09-27
> **CharlesA said:**
> The only thing you would have to do if you didn't install Windows first, is reinstall GRUB. Not a huge deal imo.

As for installing XP from USB: I've used [WinToFlash]("http://wintoflash.com/home/en/") before and it worked decently.


I tried wintoflash and for some reason it did not work.  How do I reinstall GRUB?? and what is GRUB lol :)

---

### Post by sdowney717 on 2010-09-27
> If you did not slipstream the SATA drivers into the Windows XP OS disc before attempting to install Windows on the netbook, then that is why Windows cannot recognize the SATA hard drive 
If that is true then you wont be able to install it using your USB install files.

---

### Post by CharlesA on 2010-09-27
> **Bonger6693 said:**
> I tried wintoflash and for some reason it did not work.  How do I reinstall GRUB?? and what is GRUB lol :)

What did it tell you when you tried to use it?

You should have been able to just select the ISO and what drive to put it on and go from there.

GRUB is the Linux Bootloader, without it you can't boot Linux.

> **sdowney717 said:**
> If that is true then you wont be able to install it using your USB install files.

You'd have the integrate the drivers using nLite first, then use WinToFlash to put the ISO on the thumb drive.

It's a bit of a pain in the butt tbh. Booting Windows 7 from USB is a hell of a lot easier.

---

### Post by Bonger6693 on 2010-09-27
I selected the windows cd not the .iso of windows and it put it on the jump drive.  It actually might have worked now that I think about it but at the time I had no idea wtf I was doing.  Ok so I have to put the SATA drivers on the .iso using nlite?  Then put that .iso on the jumpdrive and boot from that into the windows install and it will see my HD then?  Sorry guys I am a real noob on netbooks / linux and should have never done this.  Thank you so much for helping me.

---

### Post by CharlesA on 2010-09-27
> **Bonger6693 said:**
> I selected the windows cd not the .iso of windows and it put it on the jump drive.  It actually might have worked now that I think about it but at the time I had no idea wtf I was doing.  Ok so I have to put the SATA drivers on the .iso using nlite?  Then put that .iso on the jumpdrive and boot from that into the windows install and it will see my HD then?  Sorry guys I am a real noob on netbooks / linux and should have never done this.  Thank you so much for helping me.

That should be the way it works. I haven't used it since I had to install XP on my netbook (which has 7 on it now)

---

### Post by SlugSlug on 2010-09-27
what version is your CD -- as mentioned before some of the early XP versions don't support SATA

I think you need XP SP2 +

or download the sata drivers from manufactures website and hit F6 to load hard drive drivers during the loading of XP setup

---

### Post by CharlesA on 2010-09-27
> **SlugSlug said:**
> what version is your CD -- as mentioned before some of the early XP versions don't support SATA

I think you need XP SP2 +

or download the sata drivers from manufactures website and hit F6 to load hard drive drivers during the loading of XP setup

SP3 doesn't even have SATA drivers on the CD. You can't use the F6 option, since it requires a floppy disk (and drive) and who has one of those?

---

### Post by Bonger6693 on 2010-09-27
I have XP Home w/ SP3. Ok I am gonna try this tonight and pray that it works.  I don't have to do anything else but just incorporate the SATA drivers on the install cd for the HD to show up? Just seems really easy compared to all that I was reading and thinking there was no way to get XP on it if I installed Ubuntu first.  But again thank you for helpin me.

---

### Post by SlugSlug on 2010-09-27
Maybe your better off scrapping this thread and starting another "Help get my touchpad working" ?

---

### Post by CharlesA on 2010-09-27
> **Bonger6693 said:**
> I have XP Home w/ SP3. Ok I am gonna try this tonight and pray that it works.  I don't have to do anything else but just incorporate the SATA drivers on the install cd for the HD to show up? Just seems really easy compared to all that I was reading and thinking there was no way to get XP on it if I installed Ubuntu first.  But again thank you for helpin me.

That's about it. Also note: It'll install really slow over USB, since it'll only use USB 1.1 instead of 2.0.

---

### Post by Bonger6693 on 2010-09-27
Thank you so much Charles for the help! :)

---

### Post by Bonger6693 on 2010-09-27
nm :)

---

### Post by Bonger6693 on 2010-09-27
Quick question Charles if you dont mind telling me what you think.  In Eeeuser forum I posted my prob also and I got a response that I don't know if it will work or I should even try.  Let me know if I should just stick with what you said or try this first 

simple solution for installing XP.
go into the BIOS (keep bashing F2 right after you turned it on)
go to "advanced" -> "IDE Configuration" and set "Configure SATA as" to "IDE".
save & exit, try to install XP again.

if that still doesn't work, set the item above "IDE Configuration" from "Enhanced" to "Compatible".

after you installed XP and all the drivers from asus, you can set it back to SATA/Enhanced. 
(DONT  do it before you installed the drivers, as XP won't be able to boot  becaue of the missing chipset/SATA drivers -> no HDD access)

---

### Post by CharlesA on 2010-09-27
> **Bonger6693 said:**
> Quick question Charles if you dont mind telling me what you think.  In Eeeuser forum I posted my prob also and I got a response that I don't know if it will work or I should even try.  Let me know if I should just stick with what you said or try this first 

simple solution for installing XP.
go into the BIOS (keep bashing F2 right after you turned it on)
go to "advanced" -> "IDE Configuration" and set "Configure SATA as" to "IDE".
save & exit, try to install XP again.

if that still doesn't work, set the item above "IDE Configuration" from "Enhanced" to "Compatible".

after you installed XP and all the drivers from asus, you can set it back to SATA/Enhanced. 
(DONT  do it before you installed the drivers, as XP won't be able to boot  becaue of the missing chipset/SATA drivers -> no HDD access)

I've not tried switching it back to AHCI from IDE after installing XP, but it should work ok, assuming you have the drivers.

If it Blue Screens, just switch it back to IDE and leave it there.

Personally, I'd just leave it set to IDE, since there really isn't that much of a noticeable difference.

---

### Post by Bonger6693 on 2010-09-27
Got windows on my netbook!! Thank you SO much :)

---

