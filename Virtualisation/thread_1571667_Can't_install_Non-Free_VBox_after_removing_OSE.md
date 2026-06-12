---
title: "Can't install Non-Free VBox after removing OSE"
date: 2010-09-09
forum: Virtualisation
---

### Post by MikeinVA on 2010-09-09
After installing and loading Windows on VBox OSE, I discovered that I should read stickies first and know that the OSE version does not support USB. I removed the checked packages via the Synaptic Package Manager and tried to install the VirtualBox.org version for 10.04 Lucid Lynx. After it downloaded, I got the following error message:

Error: Conflicts with the installed package 'virtualbox-ose'

I am sure I made some kind of newbie mistake, but I don't know what it is. Please help! Thanks!

---

### Post by drs305 on 2010-09-09
The terminal might give you a bit more information about what is happening. Since we don't know the status of the OSE install/uninstall, I'd recommend installing OSE again from the terminal, then purging it. It shouldn't remove your .vdi's but I'd make backups regardless.

```
sudo apt-get install virtualbox-ose
sudo apt-get purge virtualbox-ose
```

You should then either be able to double-click the PUEL version of VirtualBox to install it or use the command:
```
sudo dpkg -i /path/<packagename>
```

If the install still fails let us know what error messages you get.

---

### Post by MikeinVA on 2010-09-15
Thanks for the tips! Sorry it took so long to get back, I just started school and am buried between that and work. I just uninstalled it and installed the web version. Now the only two problems I have is the USB isn't being seen. (I read a post somewhere that I have to change some settings) and the CD isn't recognized by Windows. Ubuntu highjacks it if I load the CD/DVD player from the Windows virtualization. Not sure what is causing that.

---

### Post by wilee-nilee on 2010-09-16
> **MikeinVA said:**
> Thanks for the tips! Sorry it took so long to get back, I just started school and am buried between that and work. I just uninstalled it and installed the web version. Now the only two problems I have is the USB isn't being seen. (I read a post somewhere that I have to change some settings) and the CD isn't recognized by Windows. Ubuntu highjacks it if I load the CD/DVD player from the Windows virtualization. Not sure what is causing that.

Go to places-admin-users groups-manage groups double click on vboxusers, and click your name on. Then with the OS on virtual shutdown open setting for that OS then usb hit the plus sign and look for your usb add it and you should be set. 

I have found to that if you want to turn that usb on and off for the virtual so that it defaults to the host right click on the usb icon at the bottom of the screen and turn it off it will magically open in the host. Turn it back on and I think it goes back to the virtual.

---

