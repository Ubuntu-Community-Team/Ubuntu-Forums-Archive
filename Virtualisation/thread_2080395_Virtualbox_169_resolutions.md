---
title: "Virtualbox 16:9 resolutions??"
date: 2012-11-03
forum: Virtualisation
---

### Post by indy1172 on 2012-11-03
Hi.  I have Ubuntu 12.10 64bit VM running in Virtualbox in Windows7.  I can only view the virtual machine in 4:3 ratio.  I installed the Virtualbox Additions and got a bigger selection of resolutions, but all still 4:3.  My host machine is Win7 pro on a Lenovo i3 with interated Intel HD display. My resolution in windows in 1366x768.  Please help!!! Thanks.

---

### Post by Kavoos on 2012-11-18
Same problem :(

---

### Post by pkadeel on 2012-11-18
the guest additions are currently not fully compatible with ubuntu 12.10. For 16:9 or full screen resolutions you will have to use ubuntu 12.04

---

### Post by Kavoos on 2012-11-18
Work perfectly :D 
just follow the instruction
[http://virtualboxes.org/doc/installing-guest-additions-on-ubuntu/](http://virtualboxes.org/doc/installing-guest-additions-on-ubuntu/)

---

### Post by apu2 on 2013-09-24
Hi to everyone. I'm new with "VirtualBox".
I'm Using "Ubuntu 12.04" in a Virtual unit under "Windows 8" and I have the same problem, Ubuntu only works with 4:3 resolutions. I tried with Kavoos' solution but in my case "* /media/cdrom/VBoxLinuxAdditions.run" *doesn't exist. 
Can anybody help me?
Thank you very much.

---

### Post by JKyleOKC on 2013-09-24
> **apu2 said:**
> Hi to everyone. I'm new with "VirtualBox".
I'm Using "Ubuntu 12.04" in a Virtual unit under "Windows 8" and I have the same problem, Ubuntu only works with 4:3 resolutions. I tried with Kavoos' solution but in my case "* /media/cdrom/VBoxLinuxAdditions.run" *doesn't exist. 
Can anybody help me?Did you install VirtualBox through the Software Center, or did you download the newest version direct from Oracle's web site?

The version in the Software Center is several minor versions out of date, so many of us who use vbox daily recommend replacing it with the current version direct from Oracle. While it's usually best to get programs direct from Software Center or through the official repositories, VirtualBox is a notable exception to this rule.

In either case, you must also have an Extension Pack for VirtualBox installed in order to be able to use the Guest Additions features, and the version of this Extension Pack must match that of the VirtualBox copy you have on your system. You can check this from the VirtualBox main screen: select **File** on the menu bar, then **Preferences**, and finally **Extensions**. If the extension pack is present, it will be listed in the resulting dialog. If the dialog is empty, you must install the Extension Pack and this will provide the missing file.

Hope this helps! Let us know the outcome. And welcome to the world of virtualization!

---

