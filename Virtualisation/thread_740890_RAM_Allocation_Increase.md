---
title: "RAM Allocation Increase"
date: 2008-03-31
forum: Virtualisation
---

### Post by thembimoyo on 2008-03-31
I Have a big server (10Gb Ram, 2 X Dual Core porcessors) I have VMware server 1.04 Running. But the VMware server is limited to 3.1Gb. How do I increase it to say 8Gb.

---

### Post by fjgaude on 2008-03-31
By re-installing and setting the drive limits to what you wish them to be.

---

### Post by prshah on 2008-03-31
> **thembimoyo said:**
> I Have a big server (10Gb Ram, 2 X Dual Core porcessors) I have VMware server 1.04 Running. But the VMware server is limited to 3.1Gb. How do I increase it to say 8Gb.

If you are running a 32 bit operating system, you have to enable PAE (Physical Address Extensions). This is enabled in Ubuntu server by default.

Or you can run a 64 bit operating system.

---

### Post by fjgaude on 2008-03-31
Sorry, I misread your first post.

I don't know how other than through the memory adjust feature in vmware, but I've never had that much memory so I can't say what to do.

---

### Post by dcstar on 2008-04-01
> **prshah said:**
> If you are running a 32 bit operating system, you have to enable PAE (Physical Address Extensions). This is enabled in Ubuntu server by default.

Or you can run a 64 bit operating system.

And VMware server runs exceptionally well in Ubuntu 64 bit.

---

### Post by prshah on 2008-04-02
> **fjgaude said:**
> Sorry, I misread your first post.

I don't know how other than through the memory adjust feature in vmware, but I've never had that much memory so I can't say what to do.

Yeah I had to take a second dekko at it too; 10 GB RAM!?!?!? What is that : 5 sticks of 2Gb each? Cause I cant imagine it to be 4x2 + 2x1, or 8x1 (if it exists)+ 2 x 1...

---

### Post by thembimoyo on 2008-04-07
Thank You all for the comments, I got it sorted out by recompiling my kernel to utilize the 10G RAM....

---

