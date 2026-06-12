---
title: "Ubuntu external USB Drive w/ VMWare for XP"
date: 2008-12-20
forum: Virtualisation
---

### Post by andy@secured-ip.com on 2008-12-20
I have a Dell Latitude D630 issued to me by my work place.  The company has federal ties so the computer is locked down fairly tight and messing with the configuration is a no no.

I bought a 500GB WD Passport and installed Ubuntu Desktop 8.10 on it.  This part of the installation works well.  And now for several hair brained ideas that didn’t seem to work out so well.  I have some windows tools that I really need to be able to use like Visio.  So, I tried to dual boot Ubuntu and XP on the Passport.  [http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8) has a great article on how to do this.  However, I ran into problems modifying an enterprise version of the XP install disk… It doesn’t work.  Maybe I should rephrase, I couldn’t get it to work.  Anyway, my next endeavor was to install VMware-server2.0 and run XP in a VM inside Ubuntu.

Things get interesting on the first reboot after installing VMWare-Server.  If you have allowed vmware to start automatically in init 3 or init 5, vmware will load what I can only guess are its usb components.  These drivers immediately lock the drive and hose the OS.  (BTW if you try this, you will have to boot single user in grub to get back in the OS and stop vmware from auto loading.)At this point, you can’t do anything; ls, reboot, init 6 etc.  My next step was to start vmware manually instead of allowing rc5.d to start them on boot.  In this case, Ubuntu and the drive are stable.  However, when you try to install a guest OS in vmware, XP in my case, you are presented with an error saying that the OS can’t be read or installed.  I don’t remember the exact error.

This is reproducible on a Seagate 500GB FreeAgent Go and on a 500GB WD Passport.  Has anyone else tried this?  Is this a question for Ubuntu or Vmware?

---

### Post by ugm6hr on 2008-12-20
> **andy@secured-ip.com said:**
> Is this a question for Ubuntu or Vmware?

Probably the latter.

I have moved the thread to [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308"), since you are more likely to get help there.

The fact that Ubuntu is installed on a USB drive should not matter.

---

### Post by dubfazer on 2008-12-23
Not sure about starting vmware workstation from init - its a GUI application that needs you to be up and running and logged in to have the main X window in place. (You can however set it up as a session to run each time you log in). 
On the XP install inside a vm, you would need to post what the errors you are getting are. The main steps should be
a) Start workstation
b) Create a Virtual Machine (guest) from workstation
c) Attach an ISO image, or the physical CDROM and power on the VM.

You should then see the normal installation in the VM. If not then it sounds like workstation is not working correctly. (You may also be able to download a preloaded appliance from the vmware site with XP as a quick way to test an already built VM).

---

