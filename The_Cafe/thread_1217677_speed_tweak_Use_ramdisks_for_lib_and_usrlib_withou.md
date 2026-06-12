---
title: "speed tweak: Use ramdisks for /lib and /usr/lib without partitions or even rebooting!"
date: 2009-07-19
forum: The Cafe
---

### Post by MaxIBoy on 2009-07-19
Currently, Firefox 3.5 and oowriter are both taking less than a second to start up to a full usable state. Gedit takes less than half a second. Even Emacs (X11 mode) takes only 0.416 seconds to start! (Measurements taken by running the command "time <program>," closing the program as soon as it has come up, and then noting the "user" measurement.)

This is the best performance I've had from ANY operating system on ANY computer. 


Some background: /usr/lib and /lib are the two most commonly-accessed directories. Their primary function is to contain dynamically-linkable libraries (*.so files) for use by other applications. However, a few programs (notably Firefox) will install themselves entirely in /usr/lib. Improving access times for either or both of these directories will result in major performance gains.

This wasn't lost on whoever posted [this]("http://forums.gentoo.org/viewtopic-t-296892.html") thread on the Gentoo forums. However, his/her solution involved creating dedicated partitions for pretty much every directory in "/".

I looked at the thread, and I wondered if there was a better way.

Turns out there is. I did it without repartitioning or even rebooting. This is how I did it.




(WARNING: This guide involves messing with the "guts" of your system, and trying it out is discouraged unless you know what you're doing.)






First, a few considerations. 

Nearly every program you're likely to run will use libraries from /lib. /lib contains the libraries which are absolutely essential to even a basic system, the same way /bin and /sbin contain binaries which are entirely mandatory. If you make a ramdisk of /lib, basically every single program you'll use will have at least a slight performance benefit. /usr/bin has many more contents, so if you make a ramdisk of it, slightly fewer programs will benefit, but you'll see larger benefits overall. In addition, as mentioned before, some programs are contained entirely in this directory. On the other hand, if you make a ramdisk of it, you'll use up a *lot* more memory. If you can, you should make ramdisks of both, but if you only have enough memory for one of them, pick /lib.

You'll also want to choose what kind of filesystems to use for your ramdisks. There are two choices available, "Ramfs" and "Tmpfs." Both will initially start at zero bytes in size. "Ramfs" will never use swap, and it will grow dynamically until you run out of memory and the kernel starts randomly killing off processes. "Tmpfs" filesystems are pegged at maximum sizes to which they can grow, and they will use swap if they have to. Keep in mind that if your ramdisks are swapping, you're loosing the performance benefit of having a ramdisk anyway. However, if only a few percent of a ramdisk is swapping, it's still an improvement. 


On my system, /lib is about 660 Mb, /usr/lib is about 1.6 Gb, and I have 4 gigs of RAM. Based on this, I decided to make ramdisks of both /lib and /usr/lib, and to use ramfs for both of them. Your decision should be influenced by the situation on your computer. 





First, create mountpoints for our ramdisks:
```
cd /mnt
sudo mkdir newlib
sudo mkdir newusrlib
```
Then, mount the ramdisks using your chosen filesystem.
for ramfs:
```
sudo mount -t ramfs ramfs /mnt/newlib
sudo mount -t ramfs ramfs /mnt/newusrlib
```for tmpfs:
```
#remember to change the size values to match your system! I suggest adding some extra leeway, just in case.
sudo mount -t tmpfs -o size=700m tmpfs /mnt/newlib 
sudo mount -t tmpfs -o size=1700m ramfs /mnt/newusrlib
```
Then, copy the files into the ramdisks. This can take a very long time, depending on the amount of data being transferred.
```
sudo cp -r /lib/* /mnt/newlib/
sudo cp -r /usr/lib/* /mnt/newusrlib/
```Be sure you do this right! On my first attempt, I did this:
```
sudo cp -r /lib /mnt/newlib/ #WRONG
sudo cp -r /usr/lib /mnt/newusrlib/ #WRONG 
``` That results in all the files being copied to /mnt/newlib/lib instead of /mnt/newlib, and /mnt/newusrlib/lib instead of /mnt/newusrlib. I wound up needing to reboot, because not even "mv" would work! A reboot fixed it though.


Finally, mount the ramdisks over the directories on your hard drive.
```
sudo mount -t unionfs -o dirs=/mnt/newlib:/lib=ro none /lib
sudo mount -t unionfs -o dirs=/mnt/newusrlib:/usr/lib=ro none /usr/lib
```And you're done!








More considerations:


If any changes get made to /lib or /usr/lib, **those changes are going to be applied only to the ramdisks!**

If this happens, here are the steps to applying those changes to your hard disk:

```
sudo umount /lib  # /lib is now a directory on the hard drive once again.
sudo cp -r /mnt/newlib/* /lib  # copy the new version of /lib onto your hardrive to make the changes permanent 
```

If you are going to be doing this on a regular basis, you may wish to create some new ramdisks specifically for changes:
```
sudo mkdir /mnt/newlib_changes #these directories will be empty
sudo mkdir /mnt/newusrlib_changes
```
Then, when creating your unionfs filesystems:
```
sudo mount -t unionfs -o dirs=/mnt/newlib_changes=rw:/mnt/newlib=ro:/lib=ro none /lib #all filesystems besides newlib_changes are now read-only
sudo mount -t unionfs -o dirs=/mnt/newusrlib_changes=rw:/mnt/newusrlib=ro:/usr/lib=ro none /usr/lib
```
After that, you will only need to copy files from newlib_changes and newusrlib_changes, saving you time.



Finally, you can choose to only copy some files into your ramdisks, and since the ramdisks are in unionfs with the hard drive directories, the non-copied files will come from your hard drive as normal. New files and modified files will still go in the ramdisks, though.

---

### Post by lswb on 2009-07-19
You might take a look at what programs like readahead and preload do. They have the advantage of not tying up memory in a ramdisk, i.e. it can still be freed by the system if necessary and made availble to a program.

For instance, you could make a list of files in /lib or whatever, then "sudo readahead-list filelist" which would cache all those files in unused memory. A program that subsequently needed to use one of these libs would load it from cached memory instead of disk.

---

### Post by MaxIBoy on 2009-07-19
Keep in mind that ramdisks will not use up any more space than they have to.

I have both preload and readahead installed, but for me they don't go far enough. Preload doesn't like to be "assertive" about how much RAM it takes up, and as for readahead, I'd rather not maintain a list of all the files in /lib or /usr/lib. Considering the fact that i have enough ram to "go the whole hog," my solution makes sense.

---

### Post by billdotson on 2009-09-01
Sounds similar to what I was working on the other day. I was writing up one that would move the /bin folder to the ramdisk and then make symlinks in the bin folder to replace those. That way all the files are on the ramdisk but the references and everything are still the same. I haven't figured out how to make it so it wouldn't copy the symlinks that were already in there but copy their destination files (if you just copy the symlinks they break).

I guess we are both doing the same thing: moving the files with the executable files and the libraries to the ramdisks and running them from there. I'll have to look at your code a little more in depth to see what you are doing different. I would show my code but I was working on a livecd and I lost it due to an unforeseen issue.

Pretty good speed tweak though, just moving ooffice.sh to a ramdisk it was loading in about 1/4-1/2 a second. Can't get much faster than that. Now if you also copy your documents and other files you know you are going to be working with then you could probably open an absolutely massive document in less than a second. Oh if hard drives could be this fast.

---

### Post by kk0sse54 on 2009-09-01
I remember reading about this over at the gentoo forums but I never did get a chance to try it. I have a spare NetBSD partition that I'm planning on playing around with a bit and see how aggressive I can get with system configuration.

---

### Post by chris200x9 on 2009-09-01
> **MaxIBoy said:**
> Currently, Firefox 3.5 and oowriter are both taking less than a second to start up to a full usable state. Gedit takes less than half a second. Even Emacs (X11 mode) takes only 0.416 seconds to start! (Measurements taken by running the command "time <program>," closing the program as soon as it has come up, and then noting the "user" measurement.)

This is the best performance I've had from ANY operating system on ANY computer. 



specs? Namely ram speed :) thanx

---

### Post by MaxIBoy on 2009-09-01
DDR2-1066, but my motherboard runs it at closer to 1100.

---

### Post by Rookie1337 on 2012-10-12
I know I'm bumping a 3+ year old thread but I'm dying to get a solution that replicates this method of using RAMdisks for /lib and /usr/lib. I'm aware that unionfs has long been forsaken and that overlayfs is supposed to replace it but how can I do what is shown in the first post with overlayfs? Does anyone know?

---

### Post by ssam on 2012-10-13
just install preload, you'll get most of the benefit for very little work.

---

### Post by overdrank on 2012-10-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

