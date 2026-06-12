---
title: "Networking in Hardy/VirtualBox combination"
date: 2008-10-06
forum: Virtualisation
---

### Post by herman2992 on 2008-10-06
I have successfully installed VirtualBox 2.0.2 on Hardy 8.0.4 (Desktop).  

The purpose:  I am a networking teacher.  I have an .iso file that creates a complete pre-configured Linux Fedora 6 server that integrates nicely with my classroom labs.  

The problem:  the .iso won't run on modern hardware, only old PC's.  I need to rackmount 4 servers running this .iso, so I need to get it to run on the new rack-mount equipment I've acquired.

The solution:  Virtualize! Hide the hardware!

I need help on the networking piece.  I want the host box (Hardy Desktop) to be transparent.  I want the Guest process running in VirtualBox session (the Fedora 6 .iso) to be hardwired at 172.17.1.1/16

What is the specific process for setting up the host NIC, bridge, tap connection to the Guest process under these conditions?  I can probably figure it out, given enough time and all the vaguely similar advice I've read here and at VirtualBox forums.  But I'm hoping someone can shorten the learning curve for me!

Thanks in advance for your help, experts!

---

### Post by psylover on 2008-10-18
Have you got this figured out yet? I'm interseted too

Greetings

---

