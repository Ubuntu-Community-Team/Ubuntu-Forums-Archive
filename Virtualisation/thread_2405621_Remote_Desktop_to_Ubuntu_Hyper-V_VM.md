---
title: "Remote Desktop to Ubuntu Hyper-V VM"
date: 2018-11-08
forum: Virtualisation
---

### Post by takeawaydave on 2018-11-08
I have an Ubuntu VM running on Hyper-V. The new enhanced sessions stuff has been setup and is working. I'm able to connect to the VM using the Hyper-V management console.
I would like to connect using mstsc / normal regular RDP however the connection fails with generic erorr: Remote Desktop can't connect to the remote computer for one of these reasons....

I have tried disabling the firewall on the ubuntu VM but this makes no difference - it would seem that xrdp is not listening on 3389/tcp 

What's the deail here to get RDP to connect ?

---

### Post by TheFu on 2018-11-08
I cannot help with RDP.  Normal RDP isn't secure on any Linux.  Using it requires using a VPN or ssh tunnel to ensure the security.
I don't know anything about hyper-V, but I have extensive virtualization experience over the last 2+ decades.

First, verify that normal networking is working.  Normally, NAT'd VMs can't be accessed from outside the VM, so make certain that the VM is on the same subnet as any client you want to connect from.  Can you ping the Ubuntu VM from other devices on the LAN? If not, fix that first.

Instead of RDP, you can load an NX-based remote desktop which uses ssh tunnelling (part of the NX protocol). X2go is the easiest, setup ssh first, then have a fairly fast remote desktop.  It feels 2-3x faster than VNC.  I don't know about RDP - doubt it will be as fast as a Win10 client to a Win10 RDP server. MSFT can do things inside their OS that external projects just cannot match or assume.

The key thing for good performance with any remote desktop is to avoid any that require direct access to GPUs. That would mean that avoiding Gnome3, KDE, Unity DEs will make for a much better experience.  That leaves Mate, LXDE, XFCE as the main DE options, or you can use just a Window Manager like openbox without any DE.

Setup ssh between the client and the server first.  Until that works, I wouldn't bother with any remote desktop.  ssh has thousands of uses and there are lots of other tools based on it - scp, sftp, rsync, and most Linux backup tools.  ssh is how Unix people connect machines together.  Bonus points if you setup ssh-keys.  Never use passwords over the internet, but ssh-keys are fine and considered secure, assuming both the client and server are properly maintained and patched.

---

