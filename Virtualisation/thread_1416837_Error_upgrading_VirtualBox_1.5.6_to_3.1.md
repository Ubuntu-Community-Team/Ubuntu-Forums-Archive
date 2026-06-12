---
title: "Error upgrading VirtualBox 1.5.6 to 3.1"
date: 2010-02-26
forum: Virtualisation
---

### Post by alayahlan on 2010-02-26
I'm running Ubuntu 8.04 and initially has installed VirtualBox through the Applications Add/Remove. Unfortunately this version of VirtualBox was really out of date, version 1.5.6. New to the program (and fairly new to Ubuntu in general) I went with that installation and installed a Windows XP box. Installation went fine, used that box with no issues for about two months. Other than getting files from the VirtualBox to my host computer, things worked fine. Guest additions were giving me issues, so I had planned to upgrade soon anyway.

Today when attempting to log in to my VirtualBox, I got an error stating "virtualbox kernel driver not installed the vboxdrv kernel module was not loaded or /dev/vboxdvr was not created for some reason..:" I figured this was a good time to go ahead an upgrade and just reinstall a clean newer version.

I removed the old version of VirtualBox, logged out, logged back in and then installed VirtualBox 3.1 through the i386 download on VirtualBox's website and let the package manager install in. Logged out, logged back in, attempted to start the program and I get this:

"Failed to create the VirtualBox COM object
The application will now terminate
Error in /home/myuser/.VirtualBox/VirtualBox.xml (line3)
cannot handle settings version '1.2 - Linux'
/home/vbox/vbox-3.1.4/src/vbox/main/VirtualBoxlmpl.cppl(420)
cnsresult virtualbox::init())."

I went through the synaptic package manager and removed Virtual Box and both generic kernel packages associated with it, logged out, logged back in and reinstalled again. I still get the same error.

How do I resolve this error? I unfortunately need the Windowx XP virtual box for work (that I'm supposed to be doing right now). I'm hoping the box itself is still in tact and will be usable once I get VirtualBox working again. Thank you.

---

### Post by Steven_B on 2010-02-27
First, you're probably better off using the apt source (describe on the VirtualBox download page under "Debian-based Linux distributions") rather than downloading the package itself.  This will ensure that you always get the latest updates directly from the VirtualBox folks.
But that wasn't what you asked. :-)

Make sure you reboot after installing a new version of VirtualBox - don't just log out and back in.  Unlike most Ubuntu software, VirtualBox adds a kernel module, which means you have to restart the kernel to use it.  Post back if the problem persists.

---

