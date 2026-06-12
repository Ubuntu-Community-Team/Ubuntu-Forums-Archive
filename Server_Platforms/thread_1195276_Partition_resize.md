---
title: "/ Partition resize"
date: 2009-06-23
forum: Server Platforms
---

### Post by xkaliburx on 2009-06-23
We upgraded all our servers from old fedora 5 OS's to Ubunutu, then used CloneZilla to move that image across the web servers.

Just realized that it made the image out of the image drive as we ran out of disk space on one of the servers.

The main / partition size it made was only 32gb yet it's a 160GB drive.  These are running Ubuntu-server (no x) so the question is how hard is it to re-size.  I know parted will get me to the prompt, and I will do some reading but if there is a 'parted' guru or someone who can simply say, it's just x,y,z no worries and your done, it would be greatly appreciated.

After some quick looks, could it really just be a;

resize partition#   start   end  ?

Well this is partition1, fdisk shows;
/dev/sda1   *           1        4240    34057768+  83  Linux

so it looks like resize 1 1  ?
The ? is the end in megabytes so a little confused.  If it's currently 32GB and it's a 160GB drive, for a round number test, and if I said add 100GB, how would I interpret that?

Thanks

---

### Post by Bachstelze on 2009-06-23
You can't resize a mounted filesystem, so the only way to resize your root filesystem is to use some kind of live CD.

---

### Post by papenpj on 2009-06-23
Well one option is you could add a new partition and just mount it somewhere on the root file system.

Or as stated above you will need to use some form of a live CD.

---

