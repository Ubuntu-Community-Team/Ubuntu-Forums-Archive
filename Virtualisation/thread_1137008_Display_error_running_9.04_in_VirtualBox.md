---
title: "Display error running 9.04 in VirtualBox"
date: 2009-04-25
forum: Virtualisation
---

### Post by aufan19 on 2009-04-25
Hi everyone,

This morning I decided to make a virtual machine of 9.04. The setup and installation went well, except for my screen resolution not being detected. My actual screen resolution is 1280x800, and the Ubuntu resolution is 800x600,m and I would like to be able to run Ubuntu in full-screen mode with the corect resolution. The problems began when I installed the guest additions. During installation, I got a message about an unknown version of X Window, then a message that the guest additions had been installed sucessfully. I rebooted the virtual machine, and upon it starting again got this error:

Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "vboxvideo" (module does not exist, 0)
(EE) No drivers available.

I click OK, and I am presented with these options:

Run Ubuntu in low-graphics mode for just one session
Reconfigure graphics
Troubleshoot the error
Exit to console login

When I select the first option, Ubuntu boots, and I am presented with the login screen.

What is going on? What do I need to do to fix this?

Thanks!!

---

### Post by Perryg on 2009-04-25
Not knowing what version of VBox you have I will take a stab.  If you have the beta release of VB ver 2.2.0 it had a script error in it.  I can tell you how to work around this but you would be better off just downloading the final release.  The script was fixed in it.

Other than that I would need a little more information.

---

### Post by aufan19 on 2009-04-25
> **Perryg said:**
> Not knowing what version of VBox you have I will take a stab.  If you have the beta release of VB ver 2.2.0 it had a script error in it.  I can tell you how to work around this but you would be better off just downloading the final release.  The script was fixed in it.

Other than that I would need a little more information.

Thank you. I have version 2.1.4. I have it set to check for updates daily, but for some reason, I haven't been notified of any. I will download the latest release and see what happens.

---

### Post by hedwig4 on 2009-04-25
I'm experiencing the same issue with 9.04 as a guest OS.  I searched and found a work around here.

[http://www.ubuntugeek.com/ubuntu-904jaunty-and-virtualbox-video-driver-for-xguest-additions.html](http://www.ubuntugeek.com/ubuntu-904jaunty-and-virtualbox-video-driver-for-xguest-additions.html)

My host system is running Debian Lenny and VirtualBox is version 2.1.4.

---

### Post by hedwig4 on 2009-04-25
The fix at ubuntugeek.com worked for me. I'm running with the guest additions now.  Just followed the instructions.

---

### Post by aufan19 on 2009-04-25
I downloaded version 2.2.0 and installed the guest additions with no problems. Everything works perfectly now. Thanks!!!

---

