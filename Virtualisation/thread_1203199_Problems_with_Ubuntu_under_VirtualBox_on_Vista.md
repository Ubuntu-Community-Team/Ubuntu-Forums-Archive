---
title: "Problems with Ubuntu under VirtualBox on Vista"
date: 2009-07-03
forum: Virtualisation
---

### Post by sinex9000 on 2009-07-03
Hi everybody!
I installed Ubuntu 9.04 under VirtualBox 3.0.0 on Vista Home Premium. Everything is ok, but when I make apt-get, my Ubuntu hangs up :confused:

---

### Post by gbeard7 on 2009-07-04
I am having exactly the same problem - Ubuntu 9.04 hangs during updates. Many thousands of others are also having this problem. Guess we'll just have to wait until Sun updates VirtualBox.

---

### Post by memilanuk on 2009-07-04
Just to be clear... when you say "...when I make apt-get", are you referring to running 'make' to compile apt-get from source, or are you just running the apt-get command?

I recently (last week) got a new computer, and have been going nutz playing with things that would not have been feasible on my older computers - VirtualBox being one of them.

My first big disappointment was finding that even thought I have a new 64-bit system, with a 64-bit host OS... my chipset doesn't support hardware virtualization, so no 64-bit guest OS for me :(

I've noticed some issues while installing various operating systems over the last couple days... I'd read that having the network adapter set to NAT may not work the best - mine are set to 'bridged', and pick up a DHCP lease from my regular LAN server.  The other thing I've noticed is that navigating away from the VM window while it's doing network updates during install is not a Good Idea - tends to seize up the VM.  Still shows as 'Running' but its dead to the world for all intents and purposes.  Once the system is installed, I didn't have any problems letting the Update Manager run and do its thing with the VM window in the background.

I did get an odd one late yesterday afternoon, though.  I'd downloaded the i386 CD isos for 9.04 desktop and 8.04.2 LTS Server.  The desktop installed into a VM just fine; the LTS server installed and then errored out on reboot - said it was the wrong kind of kernel or something.  I'll have to run it through the process again and see what it says.

Monte

---

