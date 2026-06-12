---
title: "Diskless Multiboot setup..."
date: 2007-01-20
forum: Server Platforms
---

### Post by genesis[OFT] on 2007-01-20
Hi guys,

I know that this question isn't strictly Ubuntu and possibly not even Linux related, but, I thought I'd just throw it up here anyway.

I'm helping out a mate who is the Systems Administrator at a School in Queensland, Australia with about 800 Users all up, mostly Students.  Anyway, he recently bought some new, shiny HP ThinClient Computers however is having some issues with remotely booting them.

Firstly, the only way that you really can boot these things is via PXE - they do have an onboard BootROM, however, it is really to small to be of any use.  And this is where the problem begins - he has 2 services he needs to have boot via PXE.  These are:

[LIST]
[*]Altiris Remote Installations (Microsoft Windows XP SP2, mainly)
[*]2X ThinClient O\S - for the new HP ThinClients
[/LIST]

Now, as far as I'm aware, the Altiris setup is ONLY able to boot off PXE, and even though 2X ThinClient O\S can boot off both PXE and a BootROM image, as I said, the BootROM is too small to install it onto them.  So, we need to find a way to have:

[LIST=1]
[*]Any computer in the domain turn on and automatically boot off the Network\PXE (Easy) 
[*]Any computer to load a Network based, via Network\PXE, Multiboot loader, like GRUB - I'm pretty sure that this can be done with GRUB.  Well, at least, you CAN boot GRUB off a network.
[*]Any computer to show three choices in the GRUB menu: "Boot into Altiris Remote Installation Environment (Password Protected)", "Boot 2X ThinClient O\S" and "Boot Windows off the Hard Drive"
[*]When Option 1 or 2 are selected, to somehow get GRUB to start booting into the different software, depending on the option. (No idea how you do this - this is what we need :\)
[/LIST]

Again, I know this isn't strictly Ubuntu-related, and not very much Linux related either, but, do the SysAdmins amoung you all have any idea how to do this?  Next stop I think is going to be LinuxQuestions.Org and then some SysAdmins board.

---

### Post by genesis[OFT] on 2007-01-21
I hate to bump a message about something that isn't really Ubuntu\Linux related, but, that aside, please?  Does anyone have any ideas :confused:...

---

### Post by abeverley on 2007-02-01
Can't really help you with this as I don't have much knowledge.

Just a quick suggestion though, have you looked at pxelinux and etherboot? I've never used etherboot but I believe it may be able to do something similar to what you want.

[email]andy@andybev.com[/email]

---

