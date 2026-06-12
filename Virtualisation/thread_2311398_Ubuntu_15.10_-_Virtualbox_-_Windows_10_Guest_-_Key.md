---
title: "Ubuntu 15.10 - Virtualbox - Windows 10 Guest - Keyboard not being captured by Guest"
date: 2016-01-26
forum: Virtualisation
---

### Post by Andy_Syrewicze on 2016-01-26
As the subject states. 

I'm running a Windows 10 virtual machine with virtualbox (installed with apt from the repos) on Ubuntu 15.10. 

For some reason, keyboard input is not being passed through to the guest OS. I've tried turning auto-capture on/off, installed the integration tools, tinkered with usb settings...etc...etc. 

When I press the windows key, it opens the Ubuntu Menu. when I press alt it opens the ubuntu command dialog regardless of whether virtualbox shows keyboard input is being captured or not, so I know the input is never making it to the guest OS.

The mouse works without any issues. 

Google/forum/bug report research has turned up nothing useful. 

Has anyone else run into this?

__
A

---

### Post by Andy_Syrewicze on 2016-01-27
Well, Found what it was. issue was occurring with other hypervisors as well. This VM was a P2Ved Win 10 install from a thinkpad so it contained the thinkpad keyboard drivers. I tried P2Ving it onto an ESXi host and had the same results. Further investigation into the guest OS layer turned this up. Removed the offending keyboard driver, rebooted and problem solved. 

Thanks!

---

