---
title: "which virtualization software?"
date: 2010-03-09
forum: Virtualisation
---

### Post by fiftyfour123 on 2010-03-09
So basically, I have a server with a surplus of power, and i have a not as powerful laptop. I want to have a virtual machine running on the server that i can use remotely on my laptop. I tried vrdp with virtualbox but thats not really what i want.

What my school does is they use citrix and i can access their virtual machine anywhere in the world from my laptop and i can login with my school account. Is there a way i can do this without citrix, like with KVM or VirtualBox or VMWare? or is citrix the only way to go for this?

Thanks.

---

### Post by Baneblade on 2010-03-09
I use virtual machines on my home server with Virtualbox and it does everything that you want.

The only thing that I struggled with is getting the USB support to work, but I did eventually solve that and posted a short guide [here.]("http://ubuntuforums.org/showthread.php?t=1413662")

---

### Post by fiftyfour123 on 2010-03-09
is there something other than VRDP i can use to access the machine? Even on the local network VRDP was a little laggy.

---

### Post by Baneblade on 2010-03-09
RDP requires quite a fast connection. VNC would be a better choice, especially for Ubuntu as its already installed you just need to enable it.

Personally i prefer [NXClient from Nomachine]("http://www.nomachine.com/download.php"). It uses SSH tunnelling to forward an X session securely, as well as compressing the data for speed. It is much faster over WAN's and has the added benefit of being secure too.

---

### Post by fiftyfour123 on 2010-03-09
will this still work for windows xp in the virtual machine?

---

### Post by Exca on 2010-03-10
Hello,
 
With Windows XP, I suggest you to use the embeded RDP. RDP protocol requires less bandwidth than VNC for the same quality. VNC can be better if you have a very very bad bandwidth !
Another good point for Windows XP is that the remote session automaticly change it resolution for the client request (VNC cannot).
 
I have a server running XP and I can connect from both my laptop (1900x400) and my Pocket PC (640x400) to work on it. And some crack allows you to avec 2 simultaneous sessions with the same user (MP me if you want some infos !).
 
Good luck,

---

### Post by fiftyfour123 on 2010-03-11
One problem. I can't make the resolution of the xp guest more than 800x600. I install the guest additions. It might have something to do with the fact that the ubuntu host machine doesn't have a monitor. But when I VNC into the ubuntu machine the resolution is 1024x768

any ideas?

---

### Post by fjgaude on 2010-03-11
In the VMware menu, I think in File/Perferences you will find a menu that lets you scale windows in the guest automatically. Check both buttoms and you are good to go.

---

### Post by fiftyfour123 on 2010-03-11
oh, my bad. i forgot to say i'm using virtualbox.

---

### Post by Exca on 2010-03-12
Hello Fiftyfour123,
 
> **fiftyfour123 said:**
> One problem. I can't make the resolution of the xp guest more than 800x600. I install the guest additions. It might have something to do with the fact that the ubuntu host machine doesn't have a monitor.
 
Screen resolution of a virtual machine is not affected by the host screen resolution. (Because i'ts a virtual machine ! :p). When you use a RDP client to connect on a XP guest, you can specify what is the resolution you want to display (even if you have a screen or not in your host).
 
> **fiftyfour123 said:**
> But when I VNC into the ubuntu machine the resolution is 1024x768 - any ideas?
 
VNC does not work as RDP ! RDP open a remote session on a machine, VNC controls the machine's console session.
Then VNC use the same resolution that is set on the machine. If you VNC on a machine having a 1024x786 resolution, then VNC window size will be 1024x786, even if your client screen does not support it.
 
Hope it answers to your questions! ;)

---

