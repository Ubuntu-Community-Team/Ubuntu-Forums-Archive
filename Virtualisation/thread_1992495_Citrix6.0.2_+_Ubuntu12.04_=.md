---
title: "Citrix6.0.2 + Ubuntu12.04 = ???"
date: 2012-05-31
forum: Virtualisation
---

### Post by jlindemann on 2012-05-31
Looking for some help with installing Ubuntu12.04 (64bit) as a virtual machine within a Citrix6.0.2 hypervisor.

I've tried it a couple different ways and it's not coming up (like it would if I installed Ubuntu on a physical desktop).

_First attempt_
- Downloaded the ISO, placed it into my ISO library and installed Ubuntu.
- During the installation I see everything and it works just fine.  After the installation and I tell it to restart I run into a problem where the the screen gets "blocky".  Not sure if it's an error with screen resolution or screen detection, but I'm not sure what happens.
- attempt my user/pass OR to restart the VM and I'm then sitting at a CLI.
- can't seem to start a GUI
- during installation I told it to autologin my user... but that doesn't happen either.

_Second attempt_
- Found something useful called [Paravirtulization with Citrix XenServer 6.0 and Ubuntu 12.04]("http://blog.403labs.com/post/22326590753/paravirtulization-with-citrix-xenserver-6-0-and-ubuntu")
- interesting article and it tells me how to get it set up.....sorta.
- I don't think I install everything that is needed.  I tell it I want to install the Ubuntu Desktop..... but after installation all I see is the CLI and xstart isn't recognized.
- are there certain features I need to install during the installation?


Not sure where to go from here.  I was trying to create a Ubuntu VM.  One that user's could launch from a provisioning server, and it would auto-login to a Ubuntu GUI desktop.  From there they could launch the Citrix receiver (enter their real credentials) and play away.
But my biggest pitfall right now is that I can't seem to get a desktop GUI running.

Any thoughts or suggestions?

Thanks,
Josh

---

