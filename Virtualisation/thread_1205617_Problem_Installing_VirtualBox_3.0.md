---
title: "Problem Installing VirtualBox 3.0"
date: 2009-07-06
forum: Virtualisation
---

### Post by tacantara on 2009-07-06
I downloaded the .deb package for VirtualBox 3.0 from the Sun website.  When I go to install it, the GUI indicates an error becuase I presently have VirtualBox 2.2.4 installed, and the Install button is grayed out.

I assume this means that I have to uninstall the current version of VB before installing the new one.  If I uninstall VB, will the current info on my virutal machine be retained, or will I have to start from scratch?  Is there a way to install the new VB without uninstalling the old?

---

### Post by howefield on 2009-07-06
The "information" in the VirtualBox startup window will be lost, but your virtual machine installation will not be. It will still be in ~/.VirtualBox

You will only have to recreate the settings pointing to your vm.

---

### Post by tacantara on 2009-07-06
Okay, so it sounds like I have to uninstall the old and install the new.  If I use sudo apt-get remove, will that remove the ~/.VirtualBox folder along with everything else, or am I safe running the terminal command?

---

### Post by howefield on 2009-07-06
> **tacantara said:**
> Okay, so it sounds like I have to uninstall the old and install the new.  If I use sudo apt-get remove, will that remove the ~/.VirtualBox folder along with everything else, or am I safe running the terminal command?

I am not saying you_have_to uninstall the old, just that it won't affect your vm if you do.

sudo apt-get remove should not touch the ~/.Virtualbox folder, but if you are a little unsure, you could make a backup of your VM using the clonehd command, eg in terminal

VBoxManage clonehd source destination

That way, you have a little insurance policy...

---

### Post by tacantara on 2009-07-06
I went ahead and uninstalled the old, and installed the new.  Worked like a charm, and all my old settings are showing up in the new install.  Thanks for the replies.  They helped me out very much :)

---

