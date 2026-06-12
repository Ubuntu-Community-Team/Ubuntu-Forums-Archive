---
title: "Snap-freezing a Windows install"
date: 2006-10-16
forum: The Cafe
---

### Post by Littleweseth on 2006-10-16
I'm wiping my hard drive tonight and repartitioning my hard drive to 20gb NTFS for windows, 20gb ext3 for linux /, and 40gb (or 35gb or whatever the bit on the end is) ext3 for /home (under linux), a.k.a. D: (under windows, using the ext2IFS driver). I plan to reinstall Windows first, then Ubuntu.

My question is : What's the best way to 'snap freeze' a windows install? Setting up Windows with the device drivers and whatnots is a very time consuming and painful process, so what I want to do is get a fairly minimal done right once (i.e. XP SP2 + all my drivers + a few essentials), and then make some kind of image or snapshot so I can just restore to that in case of the unforseen.

Any pointers towards good bits of (preferably free) software or guides on the subject would be appreciated. There's simply too much noise searching things like 'windows snap freeze' - gives you a list of forum posts bitching about windows freezing up - or 'windows image' - gives you a list of image editing tools :)

---

### Post by Havoc on 2006-10-16
Norton Ghost for Windows, dd for Linux.

To do the job with dd, just do this command:

```
dd if=/dev/hda1 of=/home/$USER/windows.img
```

That will copy the contents of your first partition into an image file, which you can mount, and/or use the files embedded to be copied into the Windows partition you want to rescue.

---

### Post by mips on 2006-10-16
> **Havoc said:**
> Norton Ghost for Windows, dd for Linux.

To do the job with dd, just do this command:

```
dd if=/dev/hda1 of=/home/$USER/windows.img
```That will copy the contents of your first partition into an image file, which you can mount, and/or use the files embedded to be copied into the Windows partition you want to rescue.

Be VERY carefull when you use DD. Make sure you got the right partition.

sudo fdisk -l will list your drives/partitions.

---

### Post by Littleweseth on 2006-10-16
I was talking to one of my mates on IRC, and he says that dd also copies blank space (!!) I assume this isn't true - it hardly makes sense.

So how would the restore process go for this thing? More specifically, would it have to be done from Linux? I still don't like the state of NTFS write support for linux, and i don't see too many other ways of reimaging other than norton ghost + network image.

Oh, and as of last week, i am *ultra* paranoid about typing the correct device name. mkfs.ext3 -cc on my main data partition... great great badness.

---

### Post by mips on 2006-10-16
A very nice dd thread, [http://www.linuxquestions.org/questions/showthread.php?t=362506](http://www.linuxquestions.org/questions/showthread.php?t=362506)

I'm not 100% certain but I think there is way to use dd and not copy the blank sectors.

Read this section on the zero issue:
[http://www.partimage.org/Partimage-FAQ#What_does_partimage_give_you_over_the_following:_clear_the_free_blocks_with_DD.2C_and_copy_with_DD](http://www.partimage.org/Partimage-FAQ#What_does_partimage_give_you_over_the_following:_clear_the_free_blocks_with_DD.2C_and_copy_with_DD)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by Littleweseth on 2006-10-16
Okay, I read all of that, but it doesn't seem terribly useful for actually restoring an image of an NTFS partition. Partimage still has only experimental support for NTFS, and the DD thread doesn't mention NTFS at all (though it does contain a wealth of useful information i'll have to file away somewhere.)

At this point, I guess most open-source software simply can't do anything with NTFS and have it guaranteed to work - for my current objective, it's either flaky NTFS kernel drivers or something non opensource :)

---

