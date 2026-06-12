---
title: "Truecrypt  + LVM: Would it work the way I'm thinking?"
date: 2008-06-19
forum: Security
---

### Post by rdd on 2008-06-19
I have a fileserver with quite a few disks and they're encrypted with truecrypt. Now it would be neat to be able to pool them into one virtual volume. 

I'm thinking this should work using the mapper thing, since it makes the truecrypt-ed drive available as a block device at /dev/mapper/truecryptN.

So theoretically I should be able to use a number of these block devices to create a virtual volume with lvm.

Can you girls/guys find an error in my thinking? 

You might think I'm lazy for not just going ahead and trying but all the drives are pretty full and I'll have to "park" some data to do this. So it will be a bit of work.

Regards and thanks for your input

Tom

---

### Post by hyper_ch on 2008-06-19
well, haven't used TC that much on linux.... but I know encrypted LVM with luks/dm_crypt can be accomplished...

---

### Post by rdd on 2008-06-19
Might just have to try it. By the way, Germany just won. Wohoo.

---

### Post by rdd on 2008-06-20
Just to wrap this up. I devised a test scenario and, good news first, it works.

I used the current Truecrypt 5.1a and lvm2 from the repos. I also used [this guide]("http://www.linuxconfig.org/Linux_lvm_-_Logical_Volume_Manager"), since I'm not that firm on lvm.

First I created three truecrypt volumes of 1024 MB in file containers. I then mapped those with truecrypt with the --filesystem=NONE option. (1,2 and 3 are the filenames of the container files) 

```
tom@tom-desktop:~/tcs$truecrypt ./1 --filesystem=NONE
tom@tom-desktop:~/tcs$truecrypt ./2 --filesystem=NONE
```

Then truecrypt -t -l shows the block devices where the encrypted volumes are available.

```
tom@tom-desktop:~/tcs$ sudo truecrypt -t -l
1: /home/tom/tcs/1 /dev/loop0 - 
2: /home/tom/tcs/2 /dev/loop1 - 

```

Then I used pvcreate, vgcreate, and lvcreate to make a logical volume from those two block devices.

```
tom@tom-desktop:~/tcs$ sudo pvcreate /dev/loop0
tom@tom-desktop:~/tcs$ sudo pvcreate /dev/loop1
```

```
tom@tom-desktop:~/tcs$ sudo vgcreate testvg /dev/loop0 /dev/loop1
```

```
tom@tom-desktop:~/tcs$ sudo lvcreate -L 1.99G -n testvol testvg
```

Then we need a filesystem on the logical volume.

```
tom@tom-desktop:~/tcs$ sudo mke2fs -j -m 0 /dev/testvg/testvol
```

Now the LVM on Truecrypt combination can be mounted and used just like a normal ext3 volume.

Next I tried extending it to the third TC device and that works just as advertised.

The question comes to mind "Why bother?". The main advantage for me is, that I want encrypted storage that I can add cheap disks to. Until now I had to bother with separate volumes and having one large storage is a lot cooler and easier to use. Now, there's no redundancy in this so if one disk fails, I lose data. I only lose the data on the drive that fails though. So no disadvantage to the current situation.

That was fun, back to work now.

---

### Post by rdd on 2008-11-19
I've been using this setup for a few months now, pooling a total of 4 drives to a logical volume of 1.5 TB. It works beautifully, have not had a single problem with it. 

The thing that could be improved is the startup. It stops because lvm complains of missing physical volumes (they are of course not there because TC isn't started yet). You have to press CTRL-D to boot the machine. Then I run a script that starts TC and makes the PVs available. LVM picks up on that fact a few seconds later and voila, the volume is there.

Now this is obviously not a very elegant way, but I haven't figured out, when LVM starts and how I could include that script into the startup sequence. Has anyone done something similar? Like automounting the TC-ed /home partition?

regards

tom

---

### Post by HermanAB on 2008-11-19
Hmm, the thing I would worry about is reliability.  One bit failure in the right spot can corrupt a whole encrypted volume (to me it always happens in that magic spot).  By concatenating the volumes you reduce the reliability of the system and a single bit failure on any one of the disks can toast the whole lot.

Soooooo, based on my own sad experience with encrypted drives - and I use a lot of them - I would not do that.

Cheers,

H.

---

### Post by teddks on 2008-11-21
I believe the source of the initramfs builds (from update-initramfs) is in /usr/share/initramfs-tools. You could poke around there and see what you can do.

---

### Post by rdd on 2009-02-19
> **HermanAB said:**
> Hmm, the thing I would worry about is reliability.  One bit failure in the right spot can corrupt a whole encrypted volume (to me it always happens in that magic spot).  By concatenating the volumes you reduce the reliability of the system and a single bit failure on any one of the disks can toast the whole lot.

Soooooo, based on my own sad experience with encrypted drives - and I use a lot of them - I would not do that.

Cheers,

H.

Alright, but thats the beauty with this setup. It's the underlying block devices that are encrypted. not the volume. So if there's a corrupted bit on one of the drives, only that drive fails and only the data on that drive is lost. Lvm provides for this. It just sees normal block devices.

Regards, tom

---

