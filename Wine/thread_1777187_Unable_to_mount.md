---
title: "Unable to mount"
date: 2011-06-07
forum: Wine
---

### Post by ronheidtmann on 2011-06-07
Can someone please help me!

I am trying to install various software on my new laptop with 11.04, the problem is some software has 2 or more disks.

When I had 10.10, after I installed disk 1 I would right click and select unmount disk and then insert the second disk and select mount disk and it would install.  Now I see on 11.04 there's no option and it doesn't matter how I install software, wine or not, it won't read the second disk.

What can I do?

---

### Post by sanderd17 on 2011-06-07
At login time (when you fill in your password), you could go into gnome classic and I think that will bring you in a comfortable UI.

---

### Post by ronheidtmann on 2011-06-07
I always use classic.  Does anyone else know what to do?

---

### Post by sanderd17 on 2011-06-07
Ok, then we go back to command line :P

see what is mounted with
```

mount -l

```

say your CDrom (/dev/cdrom) is mounted to /media/disk, than you can unmount it with
```

umount /media/disk

```

if you need to mount your second drive to the same spot, than you can mount it with
```

mount /dev/cdrom /media/disk

```

maybe you need to be root for some of these commands, in that case, put "sudo" before the command.

I don't know if the two drives need to be mounted to the same directory or just not, but now you have some things you can try.

---

### Post by ronheidtmann on 2011-06-07
It doesn't work because I don't understand.  Can you explain more clearly?

What happened to the right clicking on the icon and then selecting mount and unmount?

---

### Post by sanderd17 on 2011-06-07
the right-clicking thingy is a nautilus plugin (I don't know which one, maybe you can find it somewhere in synaptic or on the internet). I believe they removed it because it "confused users" since most users don't need the different options "unmount", "eject" and "safely remove".

the umount command is just an alternative for the right-click-unmount procedure (since I don't know which plugin it is). normally the mount will happen automatically.

to unmount, just execute the umount command followed by the directory where the drive is mounted.

---

### Post by ronheidtmann on 2011-06-07
If I typed in the terminal:

mount /dev/cdrom 

And then it does nothing, and if I quit then it just says there's a function still processing.  What do I do?

---

### Post by ronheidtmann on 2011-06-07
In Linux there's a difference between mount/unmount and ejecting.  What do I do to make linux know that the second disk is in? It will always read the first disk, but when it says enter the second disk and I do and click next it says it's the incorrect disk? It's doing this for everything. I never had this issue with 10.10, so what now?

---

### Post by sanderd17 on 2011-06-07
to see what devices you have, do
```

ls -l /dev
[code]
this will show everything, try to find the relevant ones (with cd or cdrom in it)

As a second thing: while you do the process, can you keep an eye on the /media directory?
[code]
ls /media

```
check it every time you mount/unmount/enter/eject a disk, just to be sure.

I think that wine expects the new disk to be in the same directory as before. If this is not the case, you need to unmount the disk an mount it back to where the original disk was.

---

### Post by ronheidtmann on 2011-06-07
Now,

The unmounting works perfectly fine.

I'm trying to install Sims 1 to test.  Now I'm trying to mount and when I give the command it tells me:

[code]
according to mtab, /dev/sr0 is already mounted on /media/SIMSDELUXE2
[code]

Now I got back to the installation where it tells me to insert disc 2 and click next, I do, and it still tells me I must insert the right disk.

---

### Post by ronheidtmann on 2011-06-07
All the programmes which I need only one disc to install is done, but everytime I try to run it doesn't work.  Is this a issue with wine?

---

### Post by sanderd17 on 2011-06-07
> **ronheidtmann said:**
> All the programmes which I need only one disc to install is done, but everytime I try to run it doesn't work.  Is this a issue with wine?

This is probably a problem of wine, check the wine databases. I don't know how to solve that.

For your two-disk problems: it sais that /dev/sr0 is mounted as /media/SIMSDELUXE2, so you need to unmount it first

```

umount /media/SIMSDELUXE2

```

and then mount it like the first disk was called (I guess SIMSDELUXE1??) You should see how it is called when your first disk is inserted and you check the ls /media command.

```

mount /dev/sr0 /media/SIMSDELUXE1

```

then click next.

---

### Post by ronheidtmann on 2011-06-07
The unmount works fine, when I mount it tells me it's already mounted and nothing happens.

I have reinstalled WINE, and tried to install Age of Empires 2.  I inserted the disc, it installs perfectly fine, when I click play it tells me to insert the CD, but it's the same CD I used to install and didn't eject or unmount it.

---

### Post by ronheidtmann on 2011-06-08
Does anyone know what to do?

---

### Post by ronheidtmann on 2011-06-08
Does anyone know what to do?

---

