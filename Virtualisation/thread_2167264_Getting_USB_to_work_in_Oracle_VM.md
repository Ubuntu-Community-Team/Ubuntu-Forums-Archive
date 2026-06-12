---
title: "Getting USB to work in Oracle VM"
date: 2013-08-13
forum: Virtualisation
---

### Post by grier-devon on 2013-08-13
Hey everyone so I just go Windows XP running in a virtual machine so if I need it for college but I need to be able to use the external ports but when I try to enable USB 2.0 I get this message
"  USB 2.0 is currently enabled for this virtual machine. However, this requires the Oracle VM VirtualBox Extension Pack to be installed."
I went to the website and tried downloading them but it won't install. is there a extension pack I get get from PPA or something? Thanks for any help.

---

### Post by Cheesemill on 2013-08-13
Just download the Extension Pack from here...
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Then either just double-click on it or go to the File > Preferences > Extensions menu in VirtualBox to install.

---

### Post by grier-devon on 2013-08-14
Awesome, upon download it automatically installed which is wierd because it did not do that last time and that is why I was posting. Thanks for the help.

---

### Post by Gilad_Pellaeon on 2013-08-14
> **Cheesemill said:**
> Just download the Extension Pack from here...
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Then either just double-click on it or go to the File > Preferences > Extensions menu in VirtualBox to install.

Isn't this the same thing as the Virtualbox Guest Additions that I had to install for Lubuntu as well as inside my own Windows XP VM so I could access a shared folder?

---

### Post by PJs Ronin on 2013-08-14
> **Gilad_Pellaeon said:**
> Isn't this the same thing as the Virtualbox Guest Additions that I had to install for Lubuntu as well as inside my own Windows XP VM so I could access a shared folder?
I do not believe so.   The extension pack is (IIRC) primarily concerned with USB connectivity whereas the Guest Additions focus on shared folders, display settings etc.   In a nutshell, extensions are installed external to the VM whereas additions are installed within the VM.

---

