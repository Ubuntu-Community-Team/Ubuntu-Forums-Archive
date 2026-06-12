---
title: "Cool program I just found: Furius ISO Mount"
date: 2010-11-19
forum: The Cafe
---

### Post by user1397 on 2010-11-19
[http://en.wikipedia.org/wiki/Furius_ISO_Mount](http://en.wikipedia.org/wiki/Furius_ISO_Mount)

This program is basically an equivalent of daemon tools lite for Windows, give or take a few features.

It is extremely simple, and works perfectly for me (0 bugs/issues so far).

Anyone else using it?

---

### Post by cariboo on 2010-11-19
What's wrong with:

```
mount -o loop some.iso /mnt
```

:) :) :)

---

### Post by user1397 on 2010-11-19
well ya know, GUIs are where it's at :)

---

### Post by leef on 2010-11-19
> **cariboo907 said:**
> 
```
mount -o loop some.iso /mnt
```


```
mount: only root can do that
```

lol but seriously the way to do it is to have something like this in fstab;

```
/home/lee/cd.iso	/home/lee/cdrom	iso9660		loop,user,ro			0	0

```

and the point your file browser to a script like this when you click .iso files;

```

#!/bin/bash
cdlink=/home/lee/cd.iso
cddir=/home/lee/cdrom

rm $cdlink
ln -s "$@" $cdlink
mount $cddir
rox -n $cddir
umount $cddir

```

---

### Post by beew on 2010-11-19
> **cariboo907 said:**
> What's wrong with:

```
mount -o loop some.iso /mnt
```:) :) :)
Furius iso mount can mount and umount multiple isos at once. 

There may be an easier way, but the only way I know to do this with command lines would be to create all the mount points one by one (mkdir statement) and then mount the isos one by one using the mount -o loop command, and then you will have to umount the mount points and delete them one by one afterwards. It is quite tedious.

---

### Post by earthpigg on 2010-11-19
what advanced features does this offer that double clicking on an .iso to mount it, and opening it with the archive manager, does not have?

what is it that i may want to do, that i would need something like this to use?

---

### Post by leef on 2010-11-19
> **beew said:**
> Furius iso mount can mount and umount multiple isos at once. 

There may be an easier way, but the only way I know to do this with command lines would be to create all the mount points one by one (mkdir statement) and then mount the isos one by one using the mount -o loop command, and then you will have to umount the mount points and delete them one by one afterwards. It is quite tedious.

Well my way doesn't work with multiple isos, so Furius sounds quite cool, how does it play with wine?

---

### Post by beew on 2010-11-19
> **earthpigg said:**
> what advanced features does this offer that double clicking on an .iso to mount it, and opening it with the archive manager, does not have?

what is it that i may want to do, that i would need something like this to use?
 
I think it can mount isos only recently, when I started with 10.04 I had to use something called gmount, it was quite buggy because I never could unmount! (gave you some fstab errors)  I think furius isos has been around longer than archive manager is able to mount isos.

Also mounting and unmounting multiple isos.

---

### Post by leef on 2010-11-19
> **beew said:**
> I think it can mount isos only recently, when I started with 10.04 I had to use something called gmount, it was quite buggy because I never could unmount! (gave you some fstab errors)  I think furius isos has been around longer than archive manager is able to mount isos.

Also mounting and unmounting multiple isos.

Do you need a command other than umount to unmount the isos?

Also is this purely a gnome thing or does it work with window managers?

---

### Post by cariboo on 2010-11-19
> **leef said:**
> Do you need a command other than umount to unmount the isos?

Also is this purely a gnome thing or does it work with window managers?

My post was only supposed to be a joke, but the mount command has nothing to do with gnome, it is part of the Linux utilities, that can be used on any distribution with any Desktop Environment.

---

### Post by leef on 2010-11-19
> **cariboo907 said:**
> My post was only supposed to be a joke, but the mount command has nothing to do with gnome, it is part of the Linux utilities, that can be used on any distribution with any Desktop Environment.

Sorry I think you miss-quoted me, the quote was referring only to Furius and not just the mount command. If your post was a joke, I don't get it?

---

### Post by johntaylor1887 on 2010-11-19
gmountiso works for me.

---

