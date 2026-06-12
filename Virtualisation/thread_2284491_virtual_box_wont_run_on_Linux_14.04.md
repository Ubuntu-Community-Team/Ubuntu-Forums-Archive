---
title: "virtual box wont run on Linux 14.04"
date: 2015-06-29
forum: Virtualisation
---

### Post by vincefish on 2015-06-29
I have loaded and removed virtualbox for Linux 14.04 trusty  4 times each time it comes up with the error  Runtime error opening '/home/vince/VirtualBox VMs/v/v.vbox' for reading: -102(File not found.).
 /home/vbox/vbox-4.3.28/src/VBox/Main/src-server/MachineImpl.cpp[731] (nsresult Machine::registeredInit()).
 [TABLE]
[TR]
[TD] Result Code:[/TD]
[TD] NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD] Component:[/TD]
[TD] Machine[/TD]
[/TR]
[TR]
[TD] Interface: [/TD]
[TD] IMachine {480cf695-2d8d-4256-9c7c-cce4184fa048} 
[/TD]
[/TR]
[/TABLE]
I can't see where I went wrong, I'm trying to use the puel vb as I need to use the 2.0 usb and cd 
.
Thanks Vince

---

### Post by v3.xx on 2015-06-30
How did you install vBox?  From the software center or from the site?  I run vBox that I installed from the site without issue.

I came across this, but not sure if it applies to you.
[http://ubuntuforums.org/showthread.php?t=1909978&p=11620643#post11620643](http://ubuntuforums.org/showthread.php?t=1909978&p=11620643#post11620643)

---

