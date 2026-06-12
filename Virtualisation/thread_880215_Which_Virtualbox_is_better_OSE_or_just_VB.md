---
title: "Which Virtualbox is better OSE or just VB"
date: 2008-08-04
forum: Virtualisation
---

### Post by deadlySniper on 2008-08-04
I have read about both editions but which is better?

---

### Post by Victormd on 2008-08-04
They're both good. However, I find Virtualbox easier to get going (just my opinion), but not the OSE version, PUEL is better. You can download it for free directly from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").

---

### Post by Oldsoldier2003 on 2008-08-04
> **Victormd said:**
> They're both good. However, I find Virtualbox easier to get going (just my opinion), but not the OSE version, PUEL is better. You can download it for free directly from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").

Having used both I tend to agree that the Puel licensed version is better.

---

### Post by bodhi.zazen on 2008-08-04
Better for what ?

---

### Post by Oldsoldier2003 on 2008-08-04
Across the board. The Puel has usb support and you dont have to wait on the modules to be added to the repositories after a kernel update. The OSE version doesn't support kernel module compilation IIRC.

edit: This was the reason I switched to the Puel version some time back.

---

### Post by Victormd on 2008-08-04
> **Oldsoldier2003 said:**
> Across the board. The Puel has usb support and you dont have to wait on the modules to be added to the repositories after a kernel update. The OSE version doesn't support kernel module compilation IIRC.

edit: This was the reason I switched to the Puel version some time back.

Exactly!

---

### Post by The_Reckoning on 2008-08-04
I work at an enterprise level company so I am a bit biased when it comes to virtualization. Now unless I am missing something I believe that vmware server can do everything that Virtual Box can do. I use vmware every day and am pretty comfortable with it, so that is what I tend to stick with when it comes to virtualizing machines.

If anybody has reasons that vmware is not the best solution I would love to hear them. I am always looking for a superior product. ;)

---

### Post by Victormd on 2008-08-04
I didn't say that virtualbox is better than vmware. As far as I know, they're very similar, I just think that virtualbox is more straight forward and easier to get working. The main comparison was between the PUEL version of virtualbox and the OSE version... If you're going to use virtualbox, use the PUEL version.

---

### Post by dominiquec on 2008-08-04
I used VMWare ESX back in 2003-2004, and at that time it was pretty revolutionary: multi-processor guest VMs, granular resource control, Fibre Channel access....  Actually, it still pretty much is as other virtualization products don't have the capabilities it had five years ago.  It was also pretty expensive.

However, since I don't work for a big enterprise company anymore, I have to go with the free (as in beer) stuff.

Tried VMWare Player on Ubuntu last year and it was okay.  Not great, but okay.  It certainly didn't have all the ESX features (then again, I didn't need those.)

The problem was it wouldn't let me create my own VMs in any easy way.  There were hacks, sure, but that shouldn't be what it's about.

Virtualbox?  Well, for an end-user like me who's not attached to a large enterprise company, it's already most of what I'm looking for.

---

### Post by The_Reckoning on 2008-08-04
I apologize. I have had limited experiences with virtualbox. So in that regard, maybe I should not have posted. 

If you are just trying out different virtualization technologies, I suggest experimenting with vmware.

---

### Post by The_Reckoning on 2008-08-04
> **dominiquec said:**
> 
However, since I don't work for a big enterprise company anymore, I have to go with the free (as in beer) stuff.


Vmware server is FREE (as in beer) ;)

I think it is all about personal taste

---

### Post by snowpine on 2008-08-04
Hi guys, based on this thread, I uninstalled virtualbox-ose, then downloaded the PUEL version from Victormd's link. Installation seemed to work, but when I type 'virtualbox' at the command prompt I get the following message: 

The program 'virtualbox' is currently not installed. You can install it by typing: sudo apt-get install virtualbox-ose

Won't this just reinstall the OSE version? Am I missing a step here?

---

### Post by Victormd on 2008-08-04
> **snowpine said:**
> The program 'virtualbox' is currently not installed. You can install it by typing: sudo apt-get install virtualbox-ose

Won't this just reinstall the OSE version? Am I missing a step here?

You're right, that will just reinstall the OSE version and you don't want that. There should be a link for it under "Applications>System tools" menu.

---

### Post by Oldsoldier2003 on 2008-08-04
> **Victormd said:**
> You're right, that will just reinstall the OSE version and you don't want that. There should be a link for it under "Applications" menu.

Applications >System Tools > Sun xVM VirtualBox

---

### Post by snowpine on 2008-08-04
> **snowpine said:**
> Hi guys, based on this thread, I uninstalled virtualbox-ose, then downloaded the PUEL version from Victormd's link. Installation seemed to work, but when I type 'virtualbox' at the command prompt I get the following message: 

The program 'virtualbox' is currently not installed. You can install it by typing: sudo apt-get install virtualbox-ose

Won't this just reinstall the OSE version? Am I missing a step here?

Simple fix; I was typing 'virtualbox' instead of 'VirtualBox'. Problem solved!

---

### Post by deadlySniper on 2008-08-04
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

I got this error message when setting up vbox for the first time. Will this cause me to be able to use USB 2.0?

---

### Post by Victormd on 2008-08-04
Under Settings, go to USB and select only the "Enable USB Controller" option and see if you get the same error (un-mark "enable USB 2.0"). Furthermore, you need to "install Guest Additions" under the "Devices" menu (after you've loaded the virtual OS).

---

