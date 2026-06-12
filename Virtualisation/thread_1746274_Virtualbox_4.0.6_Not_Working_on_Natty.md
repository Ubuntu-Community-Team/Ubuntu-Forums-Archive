---
title: "Virtualbox 4.0.6 Not Working on Natty"
date: 2011-05-01
forum: Virtualisation
---

### Post by pianoplayer123 on 2011-05-01
I just installed Ubuntu 11.04 (wubi, if that makes a difference) and I love it! But when I try to start Virtualbox (version 4.0.6, downloaded directly from the website) it says this in a window titled "VirtualBox - Critical Error":

Failed to create the VirtualBox COM object.

The application will now terminate.

Start tag expected,'<' not found.

Location: '/home/james/.VirtualBox/VirtualBox.xml', line 1 (0), column 1.

/home/vbox/vbox-4.0.6/src/VBox/Main/src-server/VirtualBoxImpl.cpp[518] (nsresult VirtualBox::init())

Can someone please tell me what to do? I'm kind of new, so just explain everything please!
Thank you in advance! :)

---

### Post by underdog512 on 2011-05-02
I am having the same issue since the upgrade to 11.04.  I went ahead and upgrade my virtualbox install to the latest version and I did get a the same error noted in [another post]("http://ubuntuforums.org/showthread.php?t=1742102")

Not sure how to fix this. Any help would be greatly appreciated.

---

### Post by underdog512 on 2011-05-02
I just discovered that this issue seems to be related to virtual machines that are in a saved state.  I seem to be able to start the one that was in a Powered off state prior to the upgrade.

---

### Post by underdog512 on 2011-05-02
> **underdog512 said:**
> I just discovered that this issue seems to be related to virtual machines that are in a saved state.  I seem to be able to start the one that was in a Powered off state prior to the upgrade.

I was just able to correct this issue by creating a new virtual machine and using the existing virtual hard disk instead of creating a new one.

Hope this helps.

---

### Post by pianoplayer123 on 2011-05-02
> **underdog512 said:**
> I was just able to correct this issue by creating a new virtual machine and using the existing virtual hard disk instead of creating a new one.

Hope this helps.
How would you create a virtual machine if VirtualBox isn't starting? I've tried uninstalling and reinstalling a million times, and the issue stays the same.

---

### Post by darryl on 2011-05-02
I used the Ubuntu Software Center to install VirtualBox OSE and it works perfectly.  I've been playing with Virtualbox for the last few days installing different flavors of linux, windows, dos, and considering trying out Haiku.  Granted it's only v4.04, but it works well.

---

### Post by collisionystm on 2011-05-02
> **darryl said:**
> I used the Ubuntu Software Center to install VirtualBox OSE and it works perfectly.  I've been playing with Virtualbox for the last few days installing different flavors of linux, windows, dos, and considering trying out Haiku.  Granted it's only v4.04, but it works well.


I also ended up installing VBox OSE due to complications with the official. 

Oracle is destroying our precious Virtualbox.

---

### Post by pianoplayer123 on 2011-05-02
Thanks for your suggestions! I just tried installing VirtualBox OSE but I got the SAME EXACT ERROR! Does anyone know what to do?

---

### Post by collisionystm on 2011-05-02
> **pianoplayer123 said:**
> Thanks for your suggestions! I just tried installing VirtualBox OSE but I got the SAME EXACT ERROR! Does anyone know what to do?

Un-install Virtualbox. 

Delete the .virtualbox folder from your home directory. Reinstall

---

