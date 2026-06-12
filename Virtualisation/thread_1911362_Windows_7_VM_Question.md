---
title: "Windows 7 VM Question"
date: 2012-01-18
forum: Virtualisation
---

### Post by RiffRuff on 2012-01-18
First off, I'm a newbie with linux -- just recently changed to it as I've got some friends at school using it and liked it thus far.

At my school, the workstations "dual boot" windows/linux.  I believe linux is the "host" OS and and windows is in a VM.  I understand what a VM is, and know how to set one up.

However, the computers at school have a key combination you can hit to switch between linux and the windows vm.  My question is how to do that.  The key combination is like ctrl+alt+f7 to switch to windows and then ctrl+alt+f5 to switch back to linux.

I've searched and haven't been able to find out a VM program to do this, or really gotten any ideas.

---

### Post by Dedoimedo on 2012-01-19
What virtualization software?
Dedoimedo

---

### Post by CharlesA on 2012-01-19
Looks like they either configured ctrl+alt+f7 to go to a different workspace, or they are two window managers running (or something..), since ctrl+alt+f1(f2....f7) just switch to different ttys.

---

### Post by japzone on 2012-01-19
> **CharlesA said:**
> Looks like they either configured ctrl+alt+f7 to go to a different workspace, or they are two window managers running (or something..), since ctrl+alt+f1(f2....f7) just switch to different ttys.
What's the boot up sequence like? I've never heard of such a setup.

---

### Post by CharlesA on 2012-01-19
> **japzone said:**
> What's the boot up sequence like? I've never heard of such a setup.
Me either. I was just guessing.

---

### Post by japzone on 2012-01-19
~nevermind~

---

### Post by RiffRuff on 2012-01-19
> **Dedoimedo said:**
> What virtualization software?
Dedoimedo
I don't have enough access to the workstation to figure that out -- or if I do have enough access, I don't know how to figure it out :/

> **japzone said:**
> What's the boot up sequence like? I've never heard of such a setup.
Actually, the IT department has told us NOT to reboot the computers, and to instead only allow them to reboot them.  So I'm not able to find out what the boot up sequence is like.  Maybe they have to manually run the VM each time the computer reboots?

---

### Post by CharlesA on 2012-01-19
> **RiffRuff said:**
> Actually, the IT department has told us NOT to reboot the computers, and to instead only allow them to reboot them.  So I'm not able to find out what the boot up sequence is like.  Maybe they have to manually run the VM each time the computer reboots?

Could be.

---

### Post by japzone on 2012-01-20
Could be some kind of Xen setup. Maybe the PC your using is just a client to a server running virtualization software and they set it up so that you could switch between Desktops using a Key Combo. I've seen setups in places before where the computers were just slaves to a server running VMs of Windows XP. I've just never heard of a Dual-OS setup like yours. It's definitly a possibilty. That would also explain why only the IT department is allowed to Reboot the PCs as they probably need special Login Credentials to Connect to the Server and start the VMs.

---

