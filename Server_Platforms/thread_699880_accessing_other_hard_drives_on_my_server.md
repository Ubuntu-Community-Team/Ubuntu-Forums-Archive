---
title: "accessing other hard drives on my server"
date: 2008-02-17
forum: Server Platforms
---

### Post by miju on 2008-02-17
hi,

I am a novice and I have a server with 3 hard drives, but I see only 1 when I log in. How do I make sure all 3 are mounted always and that when I use all the space on the first hard drive that the others will then be used? thanks

---

### Post by astrotech226 on 2008-02-17
If you didn't make provisions in the beginning during the installation, you aren't going to get what you are expecting.  Right now, you probably have the equivalent of a Windows C:, D: and E: drive.  You can get creative with symbolic links and things to help use the three drives, but you won't get them used evenly like I think you are wanting.

What you need to do is set up some sort of RAID.  I don't know what your drive sizes are, but you probably want a RAID5 or even a RAID0 if you don't care about your data.

In a RAID5, basically two of the three drives are used for data and the other is used for redundancy (there's actually striping involved).  Linux will see one big drive out of this.

RAID0 will give you all the capacity of the three drives in one big unit. But... if one of the drives fail, you are out of operation.

In either of the last two cases, you will get a device like /dev/md0.  Where now you most likely have /dev/hda, /dev/hdb and /dev/hdc.

Does this sound like what you are looking to do?

---

### Post by miju on 2008-02-17
yes it does, thanks.

But when I did the installation process I don't remember seeing anything about a raid option. I selected the option to create a LAMP server that was encrypted. I chose to create lvm's. I can see that I have the 3 hards drives. 2 are 9 Gb and 1 is 18 Gb. What should I have done differently?

---

### Post by freebeer on 2008-02-17
A linux system uses a "unitary" file system.  There is no C:, D:, E:, etc. to designate different physical drives.  They are simply mounted under a unified tree structure.

For instance, on my server, I have two drives.  The second drive is mounted under my /home directory as /home/disk2.  So when I save stuff to /home/disk2 (and any folders under it) the data will be saved to the second physical hard drive.

It's a little confusing at first (just because it's different) but it is a superior method, IMHO.

If you want to check to see if they are "all there", issuing this command should help:

```

df -h

```

---

### Post by miju on 2008-02-17
it appear that using that command I have only the root and swap partitions on one of the 8 Gb drives. 

It does not show the other drives.

Using Webmin, However,  when I investigate further it seems I have a logical volume manager  that shows another partion with the remaining space. I am not sure if this other 27 Gb partition will be written to automatically when all my space on the first hard drive is full. How can I clarify.

---

### Post by miju on 2008-02-17
also, I'm not sure if I should mention that this server is a dual P3 SCSI harddrive setup. thanks for all suggestions.

---

### Post by freebeer on 2008-02-17
Post the output so we can have a look-see.  (There are other commands available, but I'm very unfamiliar with them.)

---

### Post by miju on 2008-02-18
I forgot how to save the output of a command to a file so I can copy and paste it here.  :(

I am very concerned that the files will not save to the other hard drives when the first becomes full. I  tried the initial installation steps again and I see no option to make that happen automatically.

Another major worry for me is that it seems only the first hard drive with the root and swap are encrypted. How do I extend the root partition so that the other hard drives will be encrypted also? :confused:

---

### Post by freebeer on 2008-02-18
you use the redirect symbol ">" to put the output to a file.  Think of it as an arrowhead.  The output will go to the filename you specify.

```

df -h > disk.txt

```

will create a file called disk.txt with the output of that command.

To my knowledge, there's no included support for automatically falling over to a second drive when the first is full.  Just like in Windows, if your C: drive is full, and you try to save to C:, it'll fail.  It won't automatically save to D: (nor would you want it to, IMHO... how would you ever find it again?).  It's up to the operator to properly manage disk space.

---

