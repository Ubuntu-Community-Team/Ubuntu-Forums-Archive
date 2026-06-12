---
title: "NFS Underground 2"
date: 2010-11-16
forum: Wine
---

### Post by karogi on 2010-11-16
I have a problem with Need For Speed: Underground 2 installation. When it ask to mount 2nd disk, i mount it, but it still ask to mount 2nd disk.

Any ideas how install it?

---

### Post by Stunts on 2010-11-16
Try using:
```
wine eject d:
```
to unmount the 1st CD and then mounting the second one.
This is assuming you have your CD-rom (or mount folder) mapped in wine as drive d.

---

### Post by karogi on 2010-11-16
nothing... or i don't understand what i must to do.

Can you explain more a bit ? :)

1cd mount poin is at   /home/karogi/Desktop/NFS
2cd mount point is at /home/karogi/Desktop/NFS2

---

### Post by Stunts on 2010-11-16
OK, so let's assume that *winecfg* is pointing /media/cd to d: . If it is not you must adjust these instructions to your specific needs.
I am also assuming that /home/karogi/Desktop/NFS is the directory where the NFS cd 1 ISO image is loacted.
```
sudo mount /home/karogi/Desktop/NFS/CD.iso /media/cd
```Then install the game from /media/cd
```
wine start /media/cd/setup.exe
```Or whatever your executable is named. Do not "cd" into /media/cdrom
When the game asks you to change CDs just do (open a new terminal window to do this):
```
wine eject d:
sudo umount /media/cd
sudo mount /home/karogi/Desktop/NFS2/CD.iso

```And you should be good to go.
I haven't used "wine eject" in a long time, so please let me know if it worked ok. I'm giving you these instructions form memory.

---

### Post by psycho5 on 2011-03-10
arg, i've mounted image 1 with fuseiso to ~/dvd then in wine configuration i have given ~/dvd drive letter H: and in advanced options make it think it's a cd. when it asks for 2nd cd, fusermount -u doesn't allow me to unmount the image even if wine has released it. 

```

:~$ wine eject -u h:
:~$ fusermount -u /home/oj/dvd
umount: /home/oj/dvd: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
:~$ wine eject h:
:~$ fusermount -u /home/oj/dvd
umount: /home/oj/dvd: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
:~$ wine eject -a
:~$ fusermount -u /home/oj/dvd
umount: /home/oj/dvd: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
:~$

```

---

### Post by jayden123 on 2011-05-15
i need help with this exact same thing i am kinda new to linux and all of this terminal stuff so if any one has an easier way for me to install with detailed instructions please help me

---

### Post by jayden123 on 2011-05-15
yeah i have same sort of problem im using wine and it installs upto 53 % and im using iso so im not sure what to do and im new to this whole linux thing so if any1 can help?

---

### Post by Stunts on 2011-05-15
If these instructions don't cut it for you, try this:
[http://ubuntuforums.org/showthread.php?t=512803](http://ubuntuforums.org/showthread.php?t=512803)

Good luck.

---

### Post by it it Frozen on 2013-04-01
I'm new to Ubuntu and if anyone knows a step by step video to download and mount "nfs underground" that would be nice.

---

