---
title: "Remmina and 2 ubuntu PCs"
date: 2014-05-19
forum: Virtualisation
---

### Post by fondatommaso2 on 2014-05-19
Hi folks,
I need to access another computer from my pc. They are both running Ubuntu 14.04 GNOME and I've read that I should use Remmina. I'd like to fully control that pc, with mouse and keyboard. Can you guys help me? I don't know which protocol to use (vnc, etc.). What do I need to do?
I've searched the Internet but I couldn't find any exhaustive answer...
Thank you!

---

### Post by TheFu on 2014-05-22
I've never used Remmina - don't know anything about it.
If you are connecting over the LAN, then any of the remote desktop protocols is fine.  X/Windows is the easiest, since that is built-into any GUI running UNIX/Linux systems.  Just set the DISPLAY variable and tell the remote machine to run the GUI program you like - that could be firefox or an entire DE. These are relatively non-secure protocols, hence why they are used ONLY over the LAN.  The wikipedia article on X/Windows will provide background information.  So will this: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) - the article is a few yrs old. 

If you want to do this over the WAN (internet), things become more complex with both bandwidth and security considerations usually prevent X/Windows/VNC/RDP from being used.

 These days I just use a FreeNX server and NoMachine v3.5.x client for everything - local or remote - thanks to the automatic ssh tunnel included inside the NX protocol. There is an ubuntu-specific how-to that works for 12.04 systems. I haven't tried with 14.04.

Why is this posted in the "virtualization" sub-forum?

---

### Post by QIII on 2014-05-22
I use NoMachine 4.0, which now has a Windows server (without SSH, unfortunately) in addition to the previous client if you are interested in remoting to Windows machines.  I connect to all of my machines, including my Win 7 one, via NoMachine.

There is an enhancement package that improves graphical performance you can buy for $4.95US, but if you are using Trusty 14.04 it won't work because ffmpeg is no longer available in the Trusty repo.  You can add it by other means, of course.

Even without that, the performance of NX is far and away better than any other remote desktop protocol.

---

