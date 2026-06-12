---
title: "brainless headless server"
date: 2007-08-28
forum: Server Platforms
---

### Post by sorryd on 2007-08-28
sorry about the obtuse title, but I could not resist.

I have been running ubuntu server 7.04 as a file server (samba) and central backup box (backuppc). I was away for a few days and took it offline, but since I came back, it has not been starting properly because the root partition is read-only and services aren't starting. 
I can SSH into it, but I am not sure where to go from there due to my shiny noobie qualities that have not gone away even after several years of dabbling with linux.

Can somebody put me on track? I don't even know what log files I should be looking at.

---

### Post by K.Mandla on 2007-08-28
I don't know if this applies or not, but can you boot the machine with the root partition set as read-write? I think I did that a year ago when I had a similar problem, and it let me fix the issue, and then I set it back.

Probably not helpful, but an idea, anyway. :|

---

### Post by sorryd on 2007-08-28
I used  
sudo mount -o remount,rw / to get it
sudo /etc/init.d/samba start

to get the file server up and running, but it doesn't boot cleanly if I restart. I suppose I will have to find a monitor to see what its doing at boot time.

---

### Post by MJN on 2007-08-28
It sounds like the filesystem is broken and hence the partition is being mounted as read-only as a safety measure to prevent further damage (you really don't want to write to a filesystem considered to be in an undefined, possibly broken, state).
 
You'll need to get to the machine and run a fsck check on the partition - it will hopefully find and fix whatever's wrong (particularly if it's ext3 or another journaling filesystem) allowing the drive to be mounted rw and boot successfully. SSHing will likely not suffice as you can't really check/repair the filesystem of a mounted partition and if you unmount it you won't then have access to the right tools to do the test.
 
Mathew
 
P.S. The best way to check your disk, in this instance, will be to boot the PC with a live disk (even the Ubuntu installer disk) and then run **fsck -aV** on the root partition. Shout if you need more specific guidance.
 
P.P.S. Second thoughts - just in case I'm barking up the wrong tree do as you initially suggested and sit in front of the machine whilst booting to see what the console output is (as to why it is being mounted read-only). Then we can take it from there.

---

### Post by sorryd on 2007-08-28
cheers. I was afraid that I might need a monitor. 
No biggy, but I was hoping to do it via SSH.

---

