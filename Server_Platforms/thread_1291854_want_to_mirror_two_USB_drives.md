---
title: "want to mirror two USB drives"
date: 2009-10-15
forum: Server Platforms
---

### Post by Roclemir on 2009-10-15
I've heard of mirroring as a great way to protect your data if you have a raid setup etc. I don't have a raid setup on my ubuntu server, however I do want to protect my data. I have two 1TB drives. One is Iomega (we'll call I for short) and the other is a Maxtor (M for short). Both are USB drives. Both are pugged into my ubuntu machine. Currently the I drive has all my photos and videos etc and is the one that is accessible from the samba server, the vsftpd server, and the apache server. I was wondering if there was a way to setup two different branded USB drives to mirror eachother.
 
Thanks for everyone's help in previous threads, they have been great helps!
 
p.s. And those that told me to use Photorec to get my 6 years of photos of my crashed Maxtor drive, I LOVE YOU! got em all back safe and sound. And now I'm happily watching my movies again too! :popcorn:

---

### Post by kevin11951 on 2009-10-15
> **Roclemir said:**
> I've heard of mirroring as a great way to protect your data if you have a raid setup etc. I don't have a raid setup on my ubuntu server, however I do want to protect my data. I have two 1TB drives. One is Iomega (we'll call I for short) and the other is a Maxtor (M for short). Both are USB drives. Both are pugged into my ubuntu machine. Currently the I drive has all my photos and videos etc and is the one that is accessible from the samba server, the vsftpd server, and the apache server. I was wondering if there was a way to setup two different branded USB drives to mirror eachother.
 
Thanks for everyone's help in previous threads, they have been great helps!
 
p.s. And those that told me to use Photorec to get my 6 years of photos of my crashed Maxtor drive, I LOVE YOU! got em all back safe and sound. And now I'm happily watching my movies again too! :popcorn:

Is this a desktop or a server (ie. do you have a gui).  If its a desktop, you can wait till 9.10, because it will have a gui for making software raid stacks (which is what you want).  If you really want it now though, then look up "mdadm".

a simple mirror is like this

```
sudo apt-get install mdadm
```

```
mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sdc1 /dev/sde1
```

[COLOR="Red"]MOVE ALL FILES OFF THE DRIVES FIRST, OR YOU WILL LOSE EVERYTHING![/COLOR]

---

### Post by Roclemir on 2009-10-15
It's a server, although I've installed X and xubuntu as well as gnome and KDE desktops as it is an NX server, and the various users want various desktops etc. I'll give that code a go, let ya know if I hit some dramas, thanks

---

### Post by Roclemir on 2009-10-15
mdadm unpacked a mail server that I wasn't plannin on running. But thats all good. An error popped up saying 
 
KEDEV: not found
failed
 
about half way through, didn't stop the rest of the installation though

---

### Post by Roclemir on 2009-10-15
hmm. I'm glad I double checked your thread. Almost missed the bit in red! I just got one problem with that though, where am I doing to get a spair 450GB? Might be able to work it out between all 5 computers of the house, but sounds like a weekend job to me.

---

### Post by kevin11951 on 2009-10-15
> **Roclemir said:**
> mdadm unpacked a mail server that I wasn't plannin on running. But thats all good. An error popped up saying 
 
KEDEV: not found
failed
 
about half way through, didn't stop the rest of the installation though

Im not sure about the kdev thing, but it installs postfix as a way to warn you about problems (if it was setup correctly it would email your real email, and tell you about problems)

---

### Post by Roclemir on 2009-11-16
Hey Kevin. I have both drives blank now. I've DL'd and installed Ubuntu desktop (not server) 9.10. Now, how do I mirror these two drives. They are mounted at:

/data1
/data2

Whats the code? etc?
Thanks

---

### Post by Roclemir on 2009-11-16
at this point, if i use the "exact" code above, I'm getting:

mdadm: failed to create /dev/md0

---

### Post by Roclemir on 2009-11-16
if i type

sudo mdadm --create /dev/md0 --level=mirror --raid-devices=2 /data1 /data2

I get:

mdadm: Cannot get size of /data1: Inappropriate ioctl for devicmdadm: Cannot get size of /data2: Inappropriate ioctl for devicmdadm: create aborted

---

### Post by fjgaude on 2009-11-16
Whatever the names of the two USBs are in Computer menu is what should be used in the --create command of mdadm.

---

### Post by kevin11951 on 2009-11-16
> **Roclemir said:**
> if i type

sudo mdadm --create /dev/md0 --level=mirror --raid-devices=2 /data1 /data2

I get:

mdadm: Cannot get size of /data1: Inappropriate ioctl for devicmdadm: Cannot get size of /data2: Inappropriate ioctl for devicmdadm: create aborted

first unmount the devices

then format the drives for "Linux RAID autodetect" using the disk utility in System > Admin. > Disk Utility.

then use the devices real names (ie. /dev/sdb1, /dev/sdc1, etc...) in mdadm
the partition number is important.

---

### Post by Roclemir on 2009-11-16
err... thanks. That really didn't help at all. What computer menu? at this point, all I know is mount points and that one is called sdb and the other sdc, don't know which is which.

---

### Post by Roclemir on 2009-11-16
sorry kev, didn't see your reply there. I'm having trouble unmounting the drives. Their mount points are /data1 and /data2, how do I unmount them? When I use disk utility to unmount them, I get error:

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=302a0afb-3335-419c-bb24-803d3779b9f3 from /data1

What's the sudo code for command line? and is there a place i can look up all these command lines?

Thanks

---

### Post by kevin11951 on 2009-11-16
> **Roclemir said:**
> sorry kev, didn't see your reply there. I'm having trouble unmounting the drives. Their mount points are /data1 and /data2, how do I unmount them? When I use disk utility to unmount them, I get error:

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=302a0afb-3335-419c-bb24-803d3779b9f3 from /data1

What's the sudo code for command line? and is there a place i can look up all these command lines?

Thanks

sudo umount /dev/sdb1 

sudo umount /dev/sdc1

(depending on drive and partition name)

---

### Post by Roclemir on 2009-11-16
> **Roclemir said:**
> sorry kev, didn't see your reply there. I'm having trouble unmounting the drives. Their mount points are /data1 and /data2, how do I unmount them? When I use disk utility to unmount them, I get error:

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=302a0afb-3335-419c-bb24-803d3779b9f3 from /data1

What's the sudo code for command line? and is there a place i can look up all these command lines?

Thanks


Nevermind, found a thread with code there:

sudo umount /data1
sudo umount /data2

worked a treat

---

### Post by Roclemir on 2009-11-16
Good to see your on same time as me :). Next problem, I'm in disk utility, i've deleted the partitions that were on each drive, but i'm not seeing raid autodetect anywhere for a new partition.

---

### Post by Roclemir on 2009-11-16
> **Roclemir said:**
> Good to see your on same time as me :). Next problem, I'm in disk utility, i've deleted the partitions that were on each drive, but i'm not seeing raid autodetect anywhere for a new partition.


Stupid me... I should look around. Found it. Now, if you could just answer for me a couple of questions.

I see RAID-1 is morror
What are the other setups? what is distributed parity? and whats stripe?
Perhaps this would be bettter if i could im you these questions

---

### Post by kevin11951 on 2009-11-16
> **Roclemir said:**
> Good to see your on same time as me :). Next problem, I'm in disk utility, i've deleted the partitions that were on each drive, but i'm not seeing raid autodetect anywhere for a new partition.

i dont know if this is against the rules or not, but do you have aim, msn, or yahoo (IM)?

edit: i would guess it is not against the rules, if it was, why would we put out IM info in our profiles? :)

---

### Post by Roclemir on 2009-11-16
check your inbox

---

