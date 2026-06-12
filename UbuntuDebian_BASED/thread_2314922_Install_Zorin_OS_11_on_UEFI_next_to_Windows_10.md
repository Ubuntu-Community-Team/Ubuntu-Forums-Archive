---
title: "Install Zorin OS 11 on UEFI next to Windows 10"
date: 2016-02-24
forum: Ubuntu/Debian BASED
---

### Post by Aberts10 on 2016-02-24
Is there any way to install Zorin OS 11 alongside Windows 10 on UEFI (I don't want to have grub with Zorin & UEFI with Windows Anymore)

---

### Post by Rob Sayer on 2016-02-25
I really don't think you can install any ubuntu based distro without grub.

Also, while you may not want to hear this, I just looked at the Zorin support forum.  It looks pretty bad.  You should not have to post on ubuntuforums for such basic questions as you post here.  Why not just switch to ubuntu and get decent support?  BTW I don't actually have ubuntu installed at the moment but rather 2 mint 17.3 installs.  No dual boot anymore.

I always recommend ubuntu for linux newbies.  I don't link the Unity DE but Xubuntu and Kubuntu are more to my taste.  Lubuntu is also nice but it's not as well maintained ... AFAIK there are only one or two devs fof LXDE.  But there is no distro that's suitable for newbies that has tech support anywhere near ubuntu's.

---

### Post by Aberts10 on 2016-02-25
I found a useful tool on one of the forums: [http://askubuntu.com/questions/436096/uefi-and-reserved-bios-boot-area](http://askubuntu.com/questions/436096/uefi-and-reserved-bios-boot-area)
which allowed me to boot to the Zorin USB drive and install it with UEFI on... It didn't add it to Windows UEFI bootloader's operating system list, but it installed its own bootloader which allows me to directly boot to windows, or zorin... and access the UEFI settings.

---

