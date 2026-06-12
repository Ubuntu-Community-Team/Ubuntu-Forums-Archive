---
title: "LUKS and XFS"
date: 2006-10-16
forum: Server Platforms
---

### Post by ivoencarnacao on 2006-10-16
Greetings!

Have anyone tried this LUKS guide [https://help.ubuntu.com/community/EncryptedFilesystem]("https://help.ubuntu.com/community/EncryptedFilesystem")  with any other filesystem than ext3? 

I was planning to try it with XFS but would rather wait for your stories to check whats ahead of me! :-k 

Thanks!

---

### Post by etienne.navarro on 2006-10-17
I've been using it and have had no problems, haven't done any testing though or stressful disk operations

---

### Post by ivoencarnacao on 2006-10-17
And what filesystem are using with it?

---

### Post by etienne.navarro on 2006-10-18
with XFS, no special parameters, just been doing
```
mkfs.xfs /dev/mapper/X
```

---

### Post by srf21c on 2006-11-21
I been using JFS without any problems.  Only caveat I would add is make sure to perform the original unencrypted installation using the same filesystem that you plan using on encrypted luksformatted target /root partition.  Otherwise you may have problems loading the proper filesystem kernel modules if you switch them up between the unencrypted root, and the encrypted target root.

---

### Post by GiggleStick on 2007-01-17
I couldn't get it to work.  When I do the luksformat command like so:

sudo luksformat -t xfs /dev/hde6

I get the following error:

Error: invalid file system: xfs

The weird thing is I have another unencrypted partition mounted and it's XFS and it works fine.  I'm not sure what I can do to make it work.  Does anyone know why it thinks XFS is invalid? I should mention I was able to do it with ext3, but I really wanted to use xfs.

---

### Post by GiggleStick on 2007-01-17
Well, I've looked at the luksformat script, and it turns out to be a perl script, and I see that it looks for th mkfs.xfs executable when you specify xfs, and it turns out that isn't in my sbin directory (which is where it looks), so it quits.  Now I don't know why there is no mkfs.xfs in there, I guess when I created the xfs partitions, it was from the installer disk, so it didn't need to use it off the hdd, and it never put it there.  I will try to fix this, and post my results.

---

### Post by GiggleStick on 2007-01-17
OK, it looks like I just needed to do an "apt-get install xfsdump" to get mkfs.xfs installed, then it worked fine.  I was pretty much following the instructions of the above mentioned HowTo, and when I installed a server installation of Ubuntu, it didn't include mkfs.xfs.  Probably a newbie mistake, but it seems to work now.

---

### Post by pgf111000 on 2007-02-20
I have run into problems implementing a luks, lvm and xfs on a hardware raid array based system; my io performance is low on large partitions.  I usually receive the following error message when I mkfs.xfs...

 "mkfs.xfs: libxfs_device_zero write failed: Input/output error"

 ....and while the mkfs.xfs is executing I notice that the io wait on my opteron is high.  When I format partions below 2-3gb, there is no problem whatsoever.  

The reason that I chose xfs was based on evidence that it has practically no size limitations [important because I have  a multi-terrabyte raid6 array], it's fast, it handles large files well and it's incredibly easy to expand partitions.

If anyone has any suggestions as to how to resolve this issue....

---

### Post by pgf111000 on 2007-02-20
answer: You must specify the size of the LUKS partition with the command "cryptsetup resize /dev/mapper/mappedlukspartition xxxgb" where "xxx" is the size of the desired xfs partition.  This is required for mkfs.xfs to work properly on a LUKS partition (greater than 2gb).  Hopefully this will save some people some time....

---

