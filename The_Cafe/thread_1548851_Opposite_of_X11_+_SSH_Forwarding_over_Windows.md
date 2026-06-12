---
title: "Opposite of X11 + SSH Forwarding over Windows"
date: 2010-08-09
forum: The Cafe
---

### Post by JustinR on 2010-08-09
Hey everybody,

I recently started messing with using SSH on Ubuntu and XMing + Putty on Windows to remote-forward an application to the windows desktop environment, like seamless mode in VirtualBox/VMWare.

Here is a guide ([http://solaris.reys.net/how-to-x11-forwarding-using-ssh-putty-and-xming/](http://solaris.reys.net/how-to-x11-forwarding-using-ssh-putty-and-xming/))

So now you know what I'm talking about - but can you do the opposite of this? Remote Windows applications over to the Linux Desktop Environment instead of having to use a fullblown virtual machine or WINE?

I can clarify if needed! It sounds very interesting to me - but I didn't really know how to word it to search around on Google!

Thanks.

---

### Post by betrunkenaffe on 2010-08-09
afaik, there are no free "forwarding" agents so you can forward specific programs to your machine when you are remotely connecting to the Windows machine. Remote desktop would work but is obviously something different.

---

### Post by nerdopolis on 2010-08-09
I think Citrix does to a degree, but I assume you are actually looking for something feasible...

I'm not sure if something like that exists...  All I can think of is running apps on WINE on a remote box... Then you can forward them via X11...

If someone could tweak windows to draw to an x server the way WINE does by using WINE's driver? [http://source.winehq.org/source/dlls/winex11.drv/](http://source.winehq.org/source/dlls/winex11.drv/)

---

