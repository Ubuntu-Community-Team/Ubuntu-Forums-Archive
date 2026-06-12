---
title: "Unable to see grub bootloader in external monitor (laptop) HELP! (after install)"
date: 2015-05-16
forum: Ubuntu/Debian BASED
---

### Post by adithya3 on 2015-05-16
Hi,
I had installed zorin os 9 (based on ubuntu) (I know that I should've posted on the zorin forum but due to multiple captcha-solving error, I am not allowed temporarily to create an account, and I am in hurry) on my Dell Inspiron 1440. The laptop screen is broken, so in order to see the BIOS & etc, I disconnected the screen, and now I can see the BIOS in my external monitor (i.e. an LG LED TV with VGA Input, I was able to see Windows 8 and 7). The installer & os is based on ubuntu. 

At the end of the succesfull installation, it asked to reboot, and I rebooted, the Dell logo came up but after that there is **no signal **on my external monitor. OMG. :eek: :( :( :( :!: :!:

NOW Somebody please help!!!! 
After the dell logo, after 5 secs, I tried pressing down arrow 2 imes and then pressing enter, but nothing happens. Then I made a force shutdown and again booted and when the no signal came, I pressed enter 5 times, but nothing happened. Then I again force shutdown & rebooted, and I pressed enter, waited for 5 mins, then pressed F1 and Fn+F1 and zorin came up on my screen (the os, not the bootloader) but it was automatically logged on to guest account. Now I restarted the system and at the time of no signal, i tried pressing F1 & Fn+F1 (since it is the monitor change button in my laptop, and this method worked with the installer) but nothing happened. 

Now I am even not able to boot to windows 8 or 7 and also unable to log in to my user account (always automatically gets logged on to Guest account)!!! (I opened GParted, and it shows my windows 8, 7 & the system reserved partition) I am currently posting from live session user. 

So please find a way to make the bootloader appear in my external monitor. Thank you. Any help will be appreciated.

---

### Post by adithya3 on 2015-05-16
Atleast I want my windows boot manager back.

---

### Post by oldfred on 2015-05-16
Moved to Other OS as we do not know differences to Ubuntu.

UEFI or BIOS installs?
If UEFI you can just use UEFI/BIOS to choose what to boot.
If BIOS you have to reinstall a Windows boot loader to directly boot Windows.

If UEFI does escape get you a grub menu?
Or if BIOS does shift key immediately after Dell screen does grub menu appear?

Can you still boot installer in flash drive or DVD?

---

