---
title: "Virtualbox remote access"
date: 2009-12-08
forum: Virtualisation
---

### Post by dmizer on 2009-12-08
I've just started using Virtualbox in favor of my long trusted VMware. VMware server 1 did exactly what I needed, but it has not recieved any updates in several years and is no longer under development. I have been using VMware server 2 now for about 6 or 7 months, but I am extremely displeased with the web interface and other strange things.

Virtualbox seems to bring back many of the things I was happy with under VMware server 1, but my biggest problem is remote access.

With both server 1 and server 2, I have to admit that remote access was seamless. Even with a wireless connection, I could attach to my virtual guests and use them as if I was sitting right at the machine. Graphics were speedy, and I had perfect integration.

With Virtualbox, it seems that the only way for me to access guests is via some kind of RDP client, but RDP performance is beyond pitiful. I have to sit and wait for the desktop to draw when I connect. The mouse changes into something that is barely visible. I have to wait, or move the mouse around after clicking menus. And, the keymap is completely wrong.

Currently, the only thing I've been able to successfully use for connecting to the guests has been rdesktop and Terminal Services Client, and I've tried all the little tweaks and switches in an attempt to get things working satisfactorily.

Is there anything that offers anything near VMware like guest access for Virtualbox? Otherwise, despite the fact that I love the server side interface for Virtualbox, I'll have to move to something with better remote guest access.

---

### Post by dmizer on 2009-12-11
Here is the command I've been using to connect remotely:
```
rdesktop -a 24 -N -g 1024x768 -k en-us -z -x l -5 japan:3389
```
Keyboard map does not work but shows no error, many keys are incorrect.
Screen still draws.
Keyboard hangs during typing so I regularly get repeated characters.
Menus are delayed.

But VMware can send me a completely functional desktop on the same connection, even on my extremely low spec laptop and a wireless b (not g) network card. I'd just continue using VMware, but VMware has a fatal flaw: [http://ubuntuforums.org/showthread.php?t=1348028](http://ubuntuforums.org/showthread.php?t=1348028)

Is there any useful way to connect remotely to a virtualbox guest?

---

### Post by Druke on 2009-12-11
for remote desktop, nothing really comes built in other than the rdp.

If your guest is linux based you could try XDMCP, or ssh -X and starting gnome-session.

I doubt you're going to find a super speedy solution (unless XDMCP does it).

---

### Post by egravede on 2009-12-16
> **dmizer said:**
> I've just started using Virtualbox in favor of my long trusted VMware. VMware server 1 did exactly what I needed, but it has not recieved any updates in several years and is no longer under development. I have been using VMware server 2 now for about 6 or 7 months, but I am extremely displeased with the web interface and other strange things.

Virtualbox seems to bring back many of the things I was happy with under VMware server 1, but my biggest problem is remote access.

With both server 1 and server 2, I have to admit that remote access was seamless. Even with a wireless connection, I could attach to my virtual guests and use them as if I was sitting right at the machine. Graphics were speedy, and I had perfect integration.

With Virtualbox, it seems that the only way for me to access guests is via some kind of RDP client, but RDP performance is beyond pitiful. I have to sit and wait for the desktop to draw when I connect. The mouse changes into something that is barely visible. I have to wait, or move the mouse around after clicking menus. And, the keymap is completely wrong.

Currently, the only thing I've been able to successfully use for connecting to the guests has been rdesktop and Terminal Services Client, and I've tried all the little tweaks and switches in an attempt to get things working satisfactorily.

Is there anything that offers anything near VMware like guest access for Virtualbox? Otherwise, despite the fact that I love the server side interface for Virtualbox, I'll have to move to something with better remote guest access.
The new vmware 7 is pretty awesome.  I'm actually typing this out on it (Win XP SP3) with hostOS Ubuntu 9.10 :D

Our linux server also has it running and we remote into it daily to run database queries for our listings on ebay.  So far no problems.  Give it a shot.

---

### Post by dmizer on 2009-12-17
> **egravede said:**
> The new vmware 7 is pretty awesome.  I'm actually typing this out on it (Win XP SP3) with hostOS Ubuntu 9.10 :D

Our linux server also has it running and we remote into it daily to run database queries for our listings on ebay.  So far no problems.  Give it a shot.

I see nothing anywhere about vmware 7 on VMware's homepage. Are you talking about ESXi? I'm actually interested in a bare metal hypervisor, but last I saw, you needed a Windows box for the install and/or management.

If you're talking about VMware workstation, I'm not willing to invest in virtualization software just yet.

---

### Post by Druke on 2009-12-17
To be more clear, what is your guest/host setup?

---

### Post by dmizer on 2009-12-17
Host is xubuntu 9.04 64bit quad core with 4gig of ram and g-bit networking.

I run a variety of guests, but mostly Ubuntu. I have a few servers, and two virtual gateways with virtual subnets so I can keep traffic off the physical LAN. I haven't been able to make xdmcp work any better than rdp. The real goal here is for me to get access to an Ubuntu 9.04 or 9.10 guest from any of the physical LAN clients so that I can use it like a thin client

Physical LAN clients are all Xubuntu. Mostly Hardy, but I have two Karmic boxes as well.

---

### Post by Druke on 2009-12-17
if you were to convert to kvm with libvert, you could use virt-viewer which closely mimcs the sort of remote access you are thinking.

Other than that you need to look into other remote desktop applications.

If you are settled on VBox, you could try doing ssh -x into your remote machine, and launching "Virtualbox". YMMV, really depends on your lan speed (wifi not recommended). Depending on how bad you want it you may want to go for a direct ltsp setup.

(but it really does sound like you virtual network should be based in kvm if your vm server can handle it)

---

### Post by dmizer on 2009-12-18
> **Druke said:**
> if you were to convert to kvm with libvert, you could use virt-viewer which closely mimcs the sort of remote access you are thinking.

Other than that you need to look into other remote desktop applications.

If you are settled on VBox, you could try doing ssh -x into your remote machine, and launching "Virtualbox". YMMV, really depends on your lan speed (wifi not recommended). Depending on how bad you want it you may want to go for a direct ltsp setup.

(but it really does sound like you virtual network should be based in kvm if your vm server can handle it)

I am not set on Vbox. Really, I'm looking for a good solution that's going to offer vmware like access without the recent disk I/O bugginess I've run into. But, I was under the impression that KVM remote access also relied on rdp.

I'll revisit direct ltsp, but the last time I played with it, it didn't really do what I needed. I have learned a significant amount about Linux and Ubuntu since then though.

---

