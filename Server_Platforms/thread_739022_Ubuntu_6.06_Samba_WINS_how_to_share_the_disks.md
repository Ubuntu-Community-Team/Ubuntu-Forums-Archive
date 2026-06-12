---
title: "Ubuntu 6.06 Samba WINS how to share the disks?"
date: 2008-03-29
forum: Server Platforms
---

### Post by icebear48 on 2008-03-29
I installed ubuntu 6.06 and got samba to run and being visible from my XP PC. Now I'd like to "mount" (?) the remaining disks in the ubuntu machine and make it availble in the net at home.
What do I have to do?
I know a little about puters but am a dummy on linux (yet).
Help appreciated.
regards
icebear48

---

### Post by Belnoctourne on 2008-03-29
if by disks you mean hard disks its not to hard, to get your configuration going just use the mount command in command line

```
 mount /dev/(your hard drive partition here) /(your mount location here ex ~/Desktop/hd1)
```

after the disk mounts correctly and you've decided on a location you can edit your fstab to have them automount (forum search it lots of explinations)

to add the shares to samba you can either right click share in the desktop environment or you can edit the samba config file again lots of documentation

---

### Post by icebear48 on 2008-03-29
I guess I wasn't precise enough.
I got three disks (40/40/200 gb) one has ubuntu on it.
2nd had XP on it, but I erased it. Is now empty but unformatted.
3rd is mounted but not visible from my XP-PC
Where do I find:
a) how to format a disk?
b) how to make both available with samba?
c) how to make some of the remainder of the hda1 as an NTFS partition?

I'll be glad to read where ever I can find information. 
Thanks in advance
icebear48

---

### Post by freebeer on 2008-03-29
You can format a disk with gparted.  It's in the repos and should be able to take care of a) and c).  (At least I think you can use gparted to create and format an NTFS partition but I'm not positive.

Once you've got those settled out, you should be able to add them to your samba configuration to enable sharing.

---

### Post by icebear48 on 2008-03-30
Thanks for the help so far.
I'll try it later today because I have to leave the house soon.
In case I face mor problems you'll read from me - you bet! :)

---

