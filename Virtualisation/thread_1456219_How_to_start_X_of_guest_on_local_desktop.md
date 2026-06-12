---
title: "How to start X of guest on local desktop"
date: 2010-04-16
forum: Virtualisation
---

### Post by satimis on 2010-04-16
Hi folks,

Host - debian 5.0
Guests - ubuntu 9.04 and windows vista
KVM - virtualizer
LAN - workstation, ubuntu 9.10

How to connect guests on the workstation and starting X ? 

I can ssh connect the guests on their IP address with X forward.  But I can't start X of Ubuntu 9.04 (guest) on the workstation.   rdesktop is running on the workstation.  It can't connect ubuntu 9.04 (guest).  Please help.

TIA

B.R.
satimis

---

### Post by TheFu on 2010-04-18
I don't know of a direct way to have X/Windows running on a single monitor from two machines (virtual or not) directly. However, and I've never tried this, you might look into an** XDMCP connection to the client**.  This FAQ may be helpful [http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html)  It will still be over the network and there are security problems with XDMCP so you'll want to keep it on the same LAN with other trusted systems.

Most of us use VNC with KVM when we need a GUI.

---

### Post by satimis on 2010-04-18
> **TheFu said:**
>  - snip -
Most of us use VNC with KVM when we need a GUI.

Hi TheFu,

Thanks for your advice and URL.

I have tried both VNC and RDP here.  None of them can allow "copy and paste" and dragging files across desktops(host and guest) on same screen.  That is what I need.  VirtualBox has this feature.

IIRC several years back I tried cygwin on LTSP (Linux Terminal Server Project)/K16 it supported this function. (Remark: Nowadays some software companies repack it with a fancy name "Thin Client").  I hesitate whether I should invest further effort adding cygwin here.  Or waiting for another release of KVM.  I obtained information on KVM mailing list that they will have this feature on next version.

B.R.
satimis

---

### Post by TheFu on 2010-04-18
Have you considered NFS or sshfs?  I don't know your environment, but having files accessible on a single machine from multiple machines has sorta been solved .... like 15+ yrs ago.

---

### Post by HermanAB on 2010-04-19
Uhmmm, why do you want to run X on the workstation if there is nobody there?

SSH should be able to do what you want without the need for X on the distant machine.

---

### Post by satimis on 2010-04-19
> **TheFu said:**
> Have you considered NFS or sshfs?  I don't know your environment, but having files accessible on a single machine from multiple machines has sorta been solved .... like 15+ yrs ago.

Hi TheFu,

I have no problem on a local workstation to access a distant machine and/or the guest running on the distant machine, a virtual machine, which runs KVM as virtualizer retrieving files and sending files to them.  What I'm trying to do is to forward X to the local workstation so that files can be dragged across the desktops on the same screen.  Copy-and-paste works across desktops on the same screen.

satimis

---

### Post by TheFu on 2010-04-20
Obviously, there must be something important missing for why you want/need cross machine drag-n-drop. BTW, I've written code to perform this for very specific client/server apps. We had a Win32 client and an X/Windows client where engineering data about a part was shared between the DB query tool and the CAD system over Drag-n-Drop. The user could go either way to get the other system to look up or place the part on the drawing.  It was impressive to the customer and marketing liked it, but there were more efficient ways to make it happen.

Ok, so what you want is for every local workstation to have access to server files. That's why NFS was invented.
If the clients are all Windows, use Samba instead.

If the client apps are just normal GNome or MS-Explorer apps, the NFS/Samba solution will work.

I realize I'm not helping anymore. I know sometimes I've gotten a solution into my head when a simpler answer with a proven solution stack will solve it easier.

---

