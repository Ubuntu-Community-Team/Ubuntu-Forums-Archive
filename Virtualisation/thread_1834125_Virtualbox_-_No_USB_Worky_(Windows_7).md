---
title: "Virtualbox - No USB Worky (Windows 7)"
date: 2011-08-27
forum: Virtualisation
---

### Post by A4orce84 on 2011-08-27
Hey Guys,

Been playing around with the latest version of Virtualbox (4.1,2) under Ubuntu 10.10 and having issues with USB support. My current set-up is:

Host OS = Ubuntu 10.10
Guest OS = Windows 7

I got sound, network, and USB all installed and working properly on my VM instance of Windows 7. However, everytime I try to create a filter and get any of my USB devices to be recognized, it fails to install. It appears to recognize the USB device I plug-in (such as a thumb driver), but when Windows 7 tries to install, it fails.

Anyone have any experience with this and know of a way to have my Guest Windows 7 OS to recognize and use my USB devices correctly?

Thanks in advance!


--Asif

---

### Post by dino99 on 2011-08-27
you need to download (Oracle) the usb extension and install it

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by A4orce84 on 2011-08-27
Do you mean the extension pack? Just tried downloading and configuring it, same result.

Maybe I'm not doing it correctly?    Thanks for the reply!


--Asif

---

### Post by CharlesA on 2011-08-27
Are you a part of the vboxusers group?

---

### Post by A4orce84 on 2011-08-27
Yes, I am. I had this issue before, where it wouldn't even detect is in the guest OS (Win 7). But after adding myself it detects my USB devices...just won't install them correctly.

---

### Post by vcrpex on 2011-08-28
I dunno how helpful the below link will be for you. I had previously used ubuntu 10.10 as host with windows 7(64bit) guest in virtualbox with not much issues. Except the already methods that you have tried, adding ur user to vboxnet and using the extension pack. While I have just jumped shipped to Debian Squeeze, you might see if the matters in the link can help. it work for me in Squeeze.

[http://www.sysadmin.im/2011/07/19/62.html](http://www.sysadmin.im/2011/07/19/62.html)

---

