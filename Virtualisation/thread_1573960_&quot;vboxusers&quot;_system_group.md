---
title: "&quot;vboxusers&quot; system group"
date: 2010-09-13
forum: Virtualisation
---

### Post by JohnPta on 2010-09-13
I installed on Ubuntu 10.04 the "Virtual Box" package of Oracle.
In that "Box" I loaded Windows XP. 
I have a USB device (GPS) which needs now and than a software update, however I can not get that WinXP will see the device. 
I even got so desperate the I started reading the manual of "Vir. Box" ;)
There I read the following:
"On newer Linux hosts, VirtualBox accesses USB devices through special files in the file system. When VirtualBox is installed, these are made available to all users in the vboxusers system group. In order to be able to access USB from guest systems, make sure that you are a member of this group."

Now my question is: The vboxusers is in Ubuntu or Windows??
I do under Ubuntu see a group vboxusers and everybody is a member of that group, even "squid".

But still WinXP does not see the "GPS USB device. Does somebody have advice?

---

### Post by wilee-nilee on 2010-09-13
You have to add your name to the vbox group in Ubuntu, then with XP shutdown open the settings go to usb and see if your device is showing to add, by clicking on the plus sign.

You said the Oracle version the puel correct.

I am assuming your aware of the user and groups program in the menu-system-admin.

---

### Post by JohnPta on 2010-09-13
Correct, I did that under System>Administration>Users and Group.
Than "Manage Groups" and a Window "Groups settings" opens here I go to "vboxusers". Highlight it and click on Properties. A new windows opens with the name "Group 'vboxusers' Properties" Here I tag all the users, even squid which is actually a proxy server, but nothing changes. I even went under "Users Settings" to "Advance Settings". Here I tagged for every user "Use VirtualBox virtualization solution" still I can not see the USB GPS in WinXp.

---

### Post by JohnPta on 2010-09-13
The system "WinXP" is seeing the GPS USB but it is grayed out.

---

### Post by wilee-nilee on 2010-09-13
I think you missed the add you to the vbox group, hey I might be wrong here happens on a minute by minute basis anyway.

Go to user groups-manage groups-vboxusers-properties. In here you should just see you user name in Ubuntu click it on, here is a picture. I guess you can double click on vboxusers and get the properties window as well.
[ATTACH]169374[/ATTACH]

It might help to post the usb device model so we can look on the net, I suspect your not the first person ever to try this setup.

---

### Post by wilee-nilee on 2010-09-13
I have found that sometimes a reboot of the computer is actually needed to get everything in place. For example installing the guest additions should be set after shutting down vbox and logging out of the desktop, I find that a reboot is actually needed on my setups to get everything working.

---

### Post by JohnPta on 2010-09-13
Yup, I will reboot now but here are screenshots of my setups.

/home/jan/Downloads/vboxusers.png This suppose to be a picture. 

And this I tried under the software of "Vir Box"
/home/jan/Downloads/VirBox.png

I hope I transfered the pictures.

---

### Post by JohnPta on 2010-09-13
No they didn't

---

### Post by JohnPta on 2010-09-13
Here I try it again.

---

### Post by wilee-nilee on 2010-09-13
To post a screen shot click on the paper-clip icon in the reply-browse for your pic, hit the upload button, after uploading close that window. Click on the paper clip again and the picture will be there to add to your post.

---

### Post by JohnPta on 2010-09-13
Ha, I got it to work. The USB Icon at the bottom of the screen is flashing. But now the virtual window keeps on rebooting. The fun never stops with windows.

---

### Post by wilee-nilee on 2010-09-13
> **JohnPta said:**
> Ha, I got it to work. The USB Icon at the bottom of the screen is flashing. But now the virtual window keeps on rebooting. The fun never stops with windows.

Your half way there, I have used the f8 prompt at boot to get to safe mode in XP and to run a chkdsk /f/r to get things straight, in Vbox. It will just ask if you want to to this on next startup, you probably know all this sorry if it's old news.

I have never seen anybody saying that a chkdsk in Vbox is bad.

---

### Post by wilee-nilee on 2010-09-13
Here is a thread you might find interesting it has a link to the pre-release guest additions. I have been using them the last week with no problems, and some Linux setups now will rewrite the kernel to get the full guest additions, when they wouldn't withe the one provided in the regular release.

My W7 and XP virtuals have always run full guest with the regular releases though.

[http://ubuntuforums.org/showthread.php?t=1568618](http://ubuntuforums.org/showthread.php?t=1568618)

---

### Post by JohnPta on 2010-09-14
I reinstalled WinXP but now the software of my GPS doesn't want to run on it, you see the fun never stops with windows. That OS keeps you out of trouble. Anyway tomorrow the fight with windows goes on.
The easiest way to get all the USB devices installed on Windows is to plug them all in and/or switch them all on while you are installing windows.

---

