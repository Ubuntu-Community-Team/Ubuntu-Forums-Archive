---
title: "Best way to boot Ubuntu from a network location?"
date: 2019-08-19
forum: Virtualisation
---

### Post by DebilMudak on 2019-08-19
I have one desktop PC and one laptop, both running Windows 10 currently. I would like to use a remote Ubuntu on both of these PCs. Basically the same system which I would boot from a network location. What is the best way to go about this?

Both of my PCs have already VirtualBox installed on them. I thought about creating a VDI on my Synology NAS and then launching the virtual system through VirtualBox from the computer I am using at the moment. I reckon running Ubuntu through VirtualBox would eat up resources though. Maybe there are more straightforward methods of doing this? My NAS appears to be TFTP-capable. Any ideas?

---

### Post by TheFu on 2019-08-19
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
For 18.04 [https://askubuntu.com/questions/1029017/pxe-boot-of-18-04-iso](https://askubuntu.com/questions/1029017/pxe-boot-of-18-04-iso)

---

### Post by Tadaen_Sylvermane on 2019-08-28
LTSP is a foolproof way to do this. I do it at home. I run it off my server not a nas though so I'm not sure how that affects things. If you can create vms or containers on the nas  then just make an ubuntu server vm and roll on through.

---

### Post by DebilMudak on 2019-08-31
> **Tadaen_Sylvermane said:**
> LTSP is a foolproof way to do this. I do it at home. I run it off my server not a nas though so I'm not sure how that affects things. If you can create vms or containers on the nas  then just make an ubuntu server vm and roll on through.

If I understand correctly, LTSP is a thin client solution. My Synology NAS would be nowhere near powerful enough to function as an LTSP server.

---

### Post by Tadaen_Sylvermane on 2019-09-03
Also functions for fat clients. I run my home media centers off of it. They use their local hardware, my server just serves the root image and /home directories. I think as soon as you install a desktop environment into the chroot you are enabling fat client mode.

---

### Post by kevdog on 2019-09-07
Why do you need to boot it from a network location?  Why not always keep it running?  I like VirtualBox - but its not the most stable way to run a server. I'd think about KVM, or other virtualization software if you really need stable virtualization.

---

### Post by DebilMudak on 2019-09-11
> **kevdog said:**
> Why do you need to boot it from a network  location?  Why not always keep it running?  I like VirtualBox - but its  not the most stable way to run a server. I'd think about KVM, or other  virtualization software if you really need stable  virtualization.

I have 2 computers and I can't always use the same one. I have to  take turns on these machines. I would like to have a way to run the same  Ubuntu system regardless of which computer I am using.

> **Tadaen_Sylvermane said:**
> Also functions for fat clients. I run my home media centers off of it. They use their local hardware, my server just serves the root image and /home directories. I think as soon as you install a desktop environment into the chroot you are enabling fat client mode.

Oh really? That actually sounds like what I have been looking for! Gotta delve into that.

---

