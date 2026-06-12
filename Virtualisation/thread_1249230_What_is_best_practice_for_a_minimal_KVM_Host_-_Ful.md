---
title: "What is best practice for a minimal KVM Host - Full blown GUI Guest ?"
date: 2009-08-25
forum: Virtualisation
---

### Post by live4fun on 2009-08-25
I am thinking about improving the stability/security of my system by putting a few services into KVM guest.

My intend would be to have a minimal KVM host with command line only (no Xserver no GUI) and have serveral KVM guest run on it. A Fileserver, a VDR and a GUI System I would use for everyday Mail, Surfing, Programming.

Is it possible to install a minimal command line base system and from within this minimal system to start a guest that starts an Xserver and natively displays on my monitor?

I don't want to install X in the host and connect via VNC or X-Forward. I want only the GUI guest to have a Xserver and natively take the graphics card if possible.

I think that would be best, as it should provide maximum security to my host system which only runs the absolute necessary services (just SSH server). Only SSH and an always up-to-date Kernel should make it a very secure base my guest can rely on.

Afaik it is most important to have a stable host as it is a single point of failure if somebody can hack it. If a VM is hacked it is separated from the others and the host. If the host is hacked all VMs are open to the intruder. That's what I understood.

I didn't use KVM or XEN so far only Paralles, VMWare etc. All started from within GUI.

What do you think. Is it possible to realize something like I tried to explain above? 
What would be your approach to have only one machine running your workstation for daily use as well as server you want to be accessible from the internet?

I am eager to learn from your experience.

---

### Post by bodhi.zazen on 2009-08-26
Based on your post I suggest Proxmox.

Proxmox is an OpenVZ kernel + KVM on a Debian Host. It is manages via a web interface, although you may ssh in if you need.

OpenVZ guests are light and fast and it is perfect for what you are asking.

If you need X in a guest, what is wrong with X forwarding or VNC ? tunnel VNC over ssh or VPN if you need.

In terms of graphics, at this time guests do not as of yet directly use your graphics card so that is not (yet) an option.

VMWare Workstation and VirtualBox, IMO, offer the best options for graphics at the moment.

---

