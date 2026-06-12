---
title: "Virtualbox winxp question."
date: 2010-05-13
forum: Virtualisation
---

### Post by aklo on 2010-05-13
So am using an original copy of winxp on 1 of my partitions, i just installed virtual box on ubuntu and i'm using the SAME cd and cd key for it...is this legal?

I'm only using virtual box for installing java and tomcat since my windows partition is too messy with other stuff and i wanted to start with a clean state.

Also will virtualbox save anything i installed on my virtual winxp?

Also the usb doesn't work are there any fix for this? Or can i share files in virtual winxp with my ubuntu?

---

### Post by quixote on 2010-05-15
I believe the spirit of the license is that only one user is supposed to be using a given copy of Windows at a time.  Since you can't be using both the virtual and the actual copy at the same time, I would think that's totally okay.  But: I am not a lawyer! :D

Everything you do on your virtual xp is saved to vbox's image of that install. That's located in /home/your-login-name/.VirtualBox/HardDisks/virtual-xp-name.vdi  So long as you have your .VirtualBox directory, you could install a completely new copy of vbox, and it would still give you access to your previously set up virtual machines.

The USB only works properly on the "non-free" version of vbox.  If you installed the open-source version via synaptic, then uninstall it, There are instructions on adding the right repository and installing it [here]("http://linuxhints.blogspot.com/2009/08/running-windowsxp-on-virtualbox-on.html"), near the beginning, under "PUEL version".  Except: where it says "jaunty" in the repo line, you would put whatever your version is: lucid or karmic. (There's a section further down on setting up USB support, but I believe that's now built in.  You have to add the device in vbox itself, not in the virtual machine.)

You'll also want Vbox Guest Additions.  Once you have your virtual windows machine, start it.  Then, on the **vbox** menu, not the virtual winxp menu, go to Devices > Install Guest Additions.  That actually only downloads the iso and mounts it on the virtual winxp desktop.  Find the right Windows executable on the iso (in the virtual winxp machine now) and double click it.  Restart the virtwinxp for it to take effect.  This gives you much better mouse control, and allows you to set up shared folders with the host (ubuntu) system.  That allows you to share files between the two.  Under the "Network folders" heading in the same link above, it tells you how to do the actual sharing.  

I believe with a virtual windows, it's also supposed to give you drag and drop between your ubuntu host and windows guest, but I'm not certain.

---

