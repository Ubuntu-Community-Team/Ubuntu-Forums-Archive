---
title: "VirtualBox host interface problems"
date: 2009-04-12
forum: Virtualisation
---

### Post by Vunutus on 2009-04-12
I'm new to virtualization in general. I got Windows XP set up inside virtual box just fine, but I'm having some problems with the networking. The main thing I'm wanting to virtualize XP for is remote desktop to other computers running XP both on my local network and separate networks.

I don't think I'll have a problems with with the computers on a separate network since basic internet functions work by default. The local network, however, is more of an issue. I read the guide stickied in this forum and found out that I need to set up host interface networking for this type of thing. It gives a large and confusing solution that I'm likely to mess up, but mentions that recent versions of VirtualBox (which I'm running) have support for a much easier way and says to read the VirtualBox manual. I read the manual and found the applicable area then followed the instructions. Unfortunately it does not work.

I opened up the Windows XP machine settings, went to the "Network" section. then enabled Adapter 2 and set it as "attached to host interface" with "eth0" in the "Interface Name" box.

Whenever I try to start the XP box, it gives this error:

```


Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

```

What am I doing wrong? It's probably something obvious, as always.

---

### Post by Jose Catre-Vandis on 2009-04-13
What version of VBox? 2.1.4 plus? If so this should make host interface (bridged networking) easier than before.

Does it work OK as NAT?

Did you disable the first adapter?

Its easy enough to swap around on the first adapter so just try the same with that.

---

