---
title: "Using Virtualbox 2.1.4 to Test Software"
date: 2009-04-08
forum: Virtualisation
---

### Post by kw1502 on 2009-04-08
I’m using Virtualbox 2.1.4 (PEUL) with Intrepid as host OS and Windows XP as guest OS. The XP VM has been setup to my liking and I’ve saved a snapshot of it so I can revert back to it. I’d like to create copies of my XP VM to install, test and delete Windows programs and then destroy this “sandbox” as I see fit without effecting the original XP VM (or snapshot or whatever is the correct term) . I know this is possible using Virtualbox but as you can see, I’m confused about how VMs, hard disk images, snapshots, etc play into this. I’ve searched the forum, looked at the user manual but am still not sure how to do this.

Can anyone tell me what I need to do in Virtualbox to do this?

---

### Post by ataraxia937 on 2009-04-08
What I do for this kind of testing, is to shut down the VM in question, go to where the hard disk images are, and just copy them somewhere. You can always copy them over the originals if you break your VM, or delete them later once you're sure you don't need them any more.

There's likely a more space-efficient way to do it using VirtualBox itself, but this is the simplest way I know of.

---

### Post by linuxuser21 on 2009-04-08
Virtualbox basically emulates a BIOS and maps your hardware so the guest OS can run.  It creates a file (.vdi) that is translated as a hard drive to the guest OS.  It uses however much you specify to use of RAM and the RAM of your graphics card.  The guest OS basically just thinks it's running on a computer by itself.

From what I understand, you want to get the OS exactly how you want it and then install it for real.  The way to do this is to back up the whole OS on to a external hard drive or something like that.  This gets a little tricky though.  You want to do this by running a Live CD within virtualbox on your Windows guest OS.  Creat a partition on your host machine with the same filesystem and everything and copy it over to that.

Hope that made sense and hope this helps.

---

