---
title: "No Install Inside On Windows?"
date: 2015-03-03
forum: Ubuntu, Linux and OS Chat
---

### Post by Jokubas_Matonis_LT on 2015-03-03
no! it cant be well it must be back to use please fix to allow install inside on windows please im so sad that im cant install inside :(

please im want to install beacuse its hard on boot

---

### Post by QIII on 2015-03-03
Which version of Windows are you using?

---

### Post by MartyBuntu on 2015-03-03
If you're talking about **Wubi**, forget it. It's not advisable to use Wubi anymore.

Look into virtualised installs (like VirtualBox for example). Much cleaner and safer.

---

### Post by hakuna_matata on 2015-03-03
> **Jokubas_Matonis_LT said:**
> please fix to allow install inside on windows
There are workarounds for known issues:

14.04 and above: [bug 1317437]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437") workaround: [http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted](http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted)
14.04.1 and 14.04.2: [bug 1367071]("http://bugs.launchpad.net/wubi/+bug/1367071") workaround: [http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html](http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html)
14.10: [bug 1385930]("https://bugs.launchpad.net/wubi/+bug/1385930") workaround: [http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861](http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861)
Wubi and UEFI: [bug 1004628]("https://bugs.launchpad.net/wubi/+bug/1004628") workaround: [https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na?dl=0](https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na?dl=0)

But it seems to be impossible to release bugfixes for Wubi: [https://code.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/+merge/219927](https://code.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/+merge/219927)
IMHO that is the main reason why it is not advisable to use Wubi

---

### Post by grahammechanical on 2015-03-03
You are allowed to do what you like with your computer. The problems of wubi.exe are explained here

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

wubi.exe is still available in the Ubuntu ISO image for those people who have computers with Windows 7 or less but support will prove to be hard to find. I certainly have no experience with it. And installing Ubuntu was meant for the purpose of providing a longer test period for those people who to make a transition from Microsoft to Ubuntu. It is not suitable for very long use. Remember, Ubuntu developers have no control over what the Microsoft developers do with their updates to Windows. Intentionally or not a wubi install of Ubuntu could get broken with a Windows update.

Regards.

---

### Post by Jokubas_Matonis_LT on 2015-03-04
windows 8 pro media center 32bit @QIII

---

### Post by mastablasta on 2015-03-05
an alternative option: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

