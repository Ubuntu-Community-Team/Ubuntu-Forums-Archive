---
title: "Server or Desktop?"
date: 2008-09-11
forum: Virtualisation
---

### Post by Another Monkey on 2008-09-11
Very simple question - which version would be "best" for acting as a host of VMWare?  Server or Desktop?  The actual OS will be doing very little, the major work will be done in the images (demos etc).  It will just be a stand-along instance of VMware Workstation we will be running.

Or is the a different Linux distro which would be more appropriate (but still usable by the Linux-inexperienced)?

We're interested in trying Linux out to see if we get a performance boost over Windows.  I think we will, but I need to prove it.

Thanks.

---

### Post by Thelasko on 2008-09-11
The server version is basically a striped down desktop version. (with a few exceptions like PAE support)  It doesn't have a graphical user interface,(it's all command line like DOS) so if you are new to Ubuntu it will be difficult to use.

If your physical machine has more than 4GB of RAM you may want to consider the server version of Ubuntu as it comes with support for [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") preinstalled.  [64-bit]("http://ubuntuforums.org/showthread.php?t=914034") can address more than 4GB natively, or you can install PAE on the standard desktop version.

You can always install the server version and then install the GUI by entering the command:
```
sudo apt-get install ubuntu-desktop
```For that matter, you can always install the desktop version and remove software that you don't need.

---

### Post by tuxxy on 2008-09-11
You could also install the desktop edition and them remove the packages/services as necessary, giving you the same end result

---

### Post by Another Monkey on 2008-09-11
Thanks - that was kinda what I thought.  As it will be used by a variety of people I'll just go for desktop and uninstall the bits we don't need.

---

### Post by veloce on 2008-09-11
The server version does have a different kernel, so you won't get quite the same result - however, I don't think that will be noticeable.

I have vmware running on ubuntu server and it's quite easy to use.  Once installed, you just control it with the server console on another machine.  This way, multiple users can be working on their vms without anyone needing to sit at the vm server.

The key thing with a vm server is to provide plenty of ram to the vms.  For that reason I have avoided having a gui running.  (guis are for the thin end of the thin client!)

Most of my vms are windows so users rdp to them rather than using any vmware interfaces.  I was using a windowed X server to access the ubuntu vms as well but these don't get used much now that I just run ubuntu locally.

---

