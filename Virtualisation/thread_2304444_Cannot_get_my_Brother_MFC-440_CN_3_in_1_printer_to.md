---
title: "Cannot get my Brother MFC-440 CN 3 in 1 printer to work"
date: 2015-11-26
forum: Virtualisation
---

### Post by Bonnie_Hallow on 2015-11-26
Hi, and Happy Thanksgiving. I am new to Linux Ubuntu and on my virtual machine I downloaded Ubuntu 14.4 operating system and downloaded the drivers for my Brother MFC-440 CN printer and YET it is still not printing.  I am trying to figure out why?  I am pretty new here and some of the commands I am still not that familiar with.  Can anyone give me any advice, I just want my 3 in 1 MFC 440 CN printer to print.  Does my brother printer not printing have anything to do with my Ubuntu 14.4 being loaded in my virtual box?  Thanks to anyone that can help a newbie.:p

---

### Post by howefield on 2015-11-26
Hello Bonnie_Hallow and welcome to the forum.

Your issue may well be connected to virtualbox so your thread has been moved here away from the chat area that "Ubuntu, Linux and OS Chat" is, how is the printer connected to the virtual machine, is it USB or wireless or what ?

---

### Post by Bonnie_Hallow on 2015-12-01
Thank you for welcoming me.  What do you mean it was moved away?  To what part of this forum was my question moved too?

---

### Post by kurt18947 on 2015-12-01
USB or network connection is a primary question. I use network connections and added a second virtual network adapter making it bridged (The default seems to be NAT). Using NAT I was able to ping the printer but not print. USB would likely require being a member of the vbox user's group among other things. I also use Brother's installer rather than installing the .deb files manually. The script seems to do a pretty good job of configuring things. See the 'driver install tool' at the top of the printer driver list.

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc440cn_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc440cn_all&os=128)

---

### Post by SeijiSensei on 2015-12-02
If you are using an USB cable and VirtualBox, that is likely the issue. At a minimum you need the Guest Additions installed.  Then you have to define your device in the VB manager.

I see that your printer has network capabilities.  If you are using a USB cable, you should try connecting it to the network with an Ethernet cable instead.  Give it a static IP address.  Then all your devices will be able to see it including the VM in VirtualBox.

I also endorse using Brother's Driver Install Tool as kurt suggests.

---

