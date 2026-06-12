---
title: "Putting DSL on usb flash drive..need help"
date: 2007-11-18
forum: The Cafe
---

### Post by JESSU on 2007-11-18
I just got Sandisk Cruzer Micro USB 4.0GB.
I am following this [http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive#From_within_Linux](http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive#From_within_Linux)
I got to the part under From within Linux where you are deleting partions. Every time I try to delete one  I get this [I]No partition is defined yet!
[/I] How do I define a partition?

---

### Post by Atreus12 on 2007-11-18
If you just want an easy way to do it, boot to the DSL live cd and there is an option on the right click menu to install to usb pen drive.

-Andrew

---

### Post by JESSU on 2007-11-18
I don't have a DSL live CD. When ever I tried to make one for Ubuntu when I had windows It would freeze after the splash screen. I tied with other distros and CD brands. I went to a book store and picked up the Official Ubuntu Book that came with the CD.
EDIT: I will try burning one now that I'm using Ubuntu.  If the CD works do you think I be able to install to the USB drive with the GUI installation?

---

### Post by smartboyathome on 2007-11-18
Try installing Ubuntu Gutsy from a LiveCD [using this guide from pendrive linux]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") or just use pendrive linux's own remastered distro (which is now based on Gutsy 7.10, I think)!

---

### Post by JESSU on 2007-11-18
I made the cd and booted from it. I don't know what to type in though.


Edit: I guess I will try this
[http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/](http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/)

I heard DSL was the smallest though.

---

### Post by tgalati4 on 2007-11-18
In DSL, look in the System, Tools menu.  There are several ways to install DSL.

---

### Post by JESSU on 2007-11-19
Im following this [http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/](http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/)
and when I get the the optional part i get stuck on step 1
I type fdisk /dev/sdc and get this [I]Unable to open /dev/sdc
[/I]

What do I do?

---

### Post by smartboyathome on 2007-11-19
is it mounted? make sure it isn't. An easy way to check is to open up gparted and unmount the stuff on there (it is also the easy way to find out which /dev/sd** it uses).

---

### Post by JESSU on 2007-11-19
UGH! I followed all the steps here [http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/](http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/)
When I booted from the pendrive it said no os.


I will try dsl again. When I boot off the cd I dont know what to type. ??

---

### Post by smartboyathome on 2007-11-19
> **JESSU said:**
> UGH! I followed all the steps here [http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/](http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/)
When I booted from the pendrive it said no os.


I will try dsl again. When I boot off the cd I dont know what to type. ??

I did the one on putting Ubuntu on a USB drive, and it worked great. I have Xubuntu 7.10 (beta) on it right now, and have had no problems. Try the ubuntu one instead. :)

---

### Post by JESSU on 2007-11-19
Im trying the ubuntu one..
I get to step 16 here
[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install-for-linux-users/](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install-for-linux-users/)
 and get this *cp: invalid option*

What do I do?

---

