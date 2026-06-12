---
title: "My computer snubed it's nose at Ubuntu"
date: 2009-07-15
forum: The Cafe
---

### Post by stuart.reinke on 2009-07-15
For two days (yesterday and the day before) my computer refused to boot Ubuntu.  It all started when I upgraded from Hardy to Intrepid via the update manager.  After the the update was completed the box locked up on reboot leaving me with a blank orange screen with a mouse pointer in the middle.

What was strange is that a live cd wouldn't boot either.(same lock up)

I could however boot and run a PCLinuxOS live cd.

No tech support is need because I solved the problem.
I installed PCLOS. After that Ubuntu live cd would boot again. I then installed Jaunty and all is fine.

I'm wondering what the heck happened to cause my computer to reject Ubuntu? (mainly wondering about the live cd not working when PCLOS did work)

There might be a connection to a small partition that I had with Karmic A2 installed, but I don't know. Grub2 failed to install and I had used a special install cd to restore grub1. That was before running the update. My Hardy install had been working fine. 

Any thoughts anybody?

---

### Post by calrogman on 2009-07-15
> **stuart.reinke said:**
> It all started when I upgraded from Hardy to Intrepid via the update manager.

This can cause all sorts of problems, something probably went wrong during the update.

---

### Post by swoll1980 on 2009-07-15
It's the PCLinuxOS install. About two years ago I was distro hoping, and both times I installed it, my computer wouldn't boot Ubuntu live cds afterward. It puts some kind of block on the drives. I would get a error that would say logical block on drive...

---

