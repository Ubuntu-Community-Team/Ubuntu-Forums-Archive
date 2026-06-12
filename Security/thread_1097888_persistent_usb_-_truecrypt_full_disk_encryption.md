---
title: "persistent usb - truecrypt full disk encryption"
date: 2009-03-16
forum: Security
---

### Post by Spitphire on 2009-03-16
Hello,

Here's the scenario.  I would like to create a bootable persistent usb drive running ubuntu 8.10, which i've created following the guide posted at:

[URL="http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/"]http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/
[/URL]

I would like to use truecrypt to encrypt the entire usb drive, requiring pre-boot authentication.  That way I have a fully bootable distro, but it is **all** encrypted encase I lose it.

I've searched near and far for some type of resource covering this.  Does anyone have any knowledge about doing this?

When I install truecrypt on the persistent usb drive, it does not give me the option for full disk encryption.  Not sure why it's doing this, does it think that it's a cd-rom maybe?? 

Any help would be greatly appreciated :)  

Thanks,
-Spit

---

### Post by Tubes6al4v on 2009-03-16
I don't believe Truecrypt supports full disk encryption with linux. I would look to dm-crypt for that. Pendrive is rpm, right? I don't know, but that might change the way you would set this up. At least its a start.

---

### Post by Spitphire on 2009-03-16
> **Tubes6al4v said:**
> I don't believe Truecrypt supports full disk encryption with linux. I would look to dm-crypt for that. Pendrive is rpm, right? I don't know, but that might change the way you would set this up. At least its a start.


Well, I guess that would explain why I didn't see the feature :).  I will look into dm-crypt.  For anyone else interested in this I will post my results here.

---

### Post by Mykle87 on 2009-05-02
I am looking to do the exact same thing. On top of having a persistent live usb, I would like to use my flash drive for portable windows apps. Let me know what you end up doing. I will keep researching as well.

---

### Post by excogitation on 2009-05-21
An easier way to create a persistent installation on a USB stick (or SD card, ...) is to use the alternate cd and install straight to the USB stick.

You just have to make sure to also install the bootloader (grub) to that USB stick.


I guess you already know you can encrypt your entire home folder since 9.04 (easier using the alternate CD) - if that's not enough, you can also encrypt the whole system using the alternate CD (at least from what I read).

If you really want to encrypt your system using TrueCrypt - I don't know how to do that.

---

### Post by Mykle87 on 2009-05-21
If you install Ubuntu to a USB device using the alternate cd, you do not have the luxury of using the pen drive on any machine. This is the benefit of creating a Live USB. When you add persistence, any changes you make are saved from session to session. I want to encrypt this because I carry this on my key chain and want the extra protection in case it is stolen. Honestly though it would be overkill for me since I don't keep sensitive data on it. It was just a thought. 

My research tells me that you cannot use Truecrypt for pre-boot authentication which is unfortunate. I wonder if you can encrypt the /home directory on a Live USB?

---

### Post by jcreneau on 2011-09-17
Any update on this?

---

