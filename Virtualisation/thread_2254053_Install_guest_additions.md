---
title: "Install guest additions"
date: 2014-11-24
forum: Virtualisation
---

### Post by Klaster on 2014-11-24
Hey there,
I have a running virtualbox with Win 7 as guest and Ubuntu 12.04 LTS as host. Works well, but I didn't know that I needed to install the guest additions as well for better support of full screen etc.

As I wanted to install the guest additions now, I need to reinstall virtualbox completely with it. My question whether I'll have problems reinstalling and reactivating my copy of Win 7 afterwards. I don't want to loose the license, obviously.

Will I be able to use the same Win 7 copy after reinstalling virtualbox?

Thanks and cheers,
Jakob

---

### Post by deadflowr on 2014-11-24
?
You install guest additions from within the VM.
When you start the Vm, in the menu bar in the top panel's menu bar for virtualbox, click on Devices, then Insert guest additions cd image.
Then it'll download the guest additions packages., if it can't find it on the system.
When the image is mounted, Windows should autostart the installer.
More on that here
[https://www.virtualbox.org/manual/ch04.html#additions-windows](https://www.virtualbox.org/manual/ch04.html#additions-windows)

Good luck

---

### Post by QIII on 2014-11-24
If the installer does not start automatically after adding the Guest Additions image, navigate to the CD/iso image while in the guest OS and find the .exe file that I believe is named "VBoxWindowsGuestAdditions.exe".  Run that.  You will need to reboot the VM.  

After that, you may select full screen mode from the VirtualBox menu bar.

---

### Post by Klaster on 2014-11-24
> **deadflowr said:**
> ?
You install guest additions from within the VM.
When you start the Vm, in the menu bar in the top panel's menu bar for virtualbox, click on Devices, then Insert guest additions cd image.
Then it'll download the guest additions packages., if it can't find it on the system.
When the image is mounted, Windows should autostart the installer.
More on that here
[https://www.virtualbox.org/manual/ch04.html#additions-windows](https://www.virtualbox.org/manual/ch04.html#additions-windows)

Good luck

Hey,
unfortunately clicking "insert guest additions cd image" doesn't do anything for me (see screenshot). My VM is connected to the internet though.
Any hints?

[ATTACH=CONFIG]258180[/ATTACH]

---

### Post by Klaster on 2014-11-24
Hey again,
I eventually found the VBGuestAdditions.iso on my host system and mounted it manually on my guest system. (under /usr/share/virtualbox/ --> you can check the location on the host system on the Virtualbox main window -> Settings -> Storage -> Controler:IDE)
Thanks for your help!

---

