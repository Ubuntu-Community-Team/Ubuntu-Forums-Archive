---
title: "Mount Partitions within a Drive Image"
date: 2009-06-14
forum: Virtualisation
---

### Post by Max Nanasy on 2009-06-14
Is there an easy way to mount partitions within a drive image?  Perhaps some way to &quot;mount&quot; the image in a way that makes its partitions devices?

---

### Post by ddrichardson on 2009-06-14
How was the image created? Images can be mounted as loopback devices but it depends on how you imaged the disk.

---

### Post by Max Nanasy on 2009-06-14
I know that I can mount a single filesystem image on the loopback device, but if I just dd'd an entire drive, is there an easy way to mount its partitions from the resulting image?

---

### Post by ddrichardson on 2009-06-14
No, not if you did the whole drive. How would you identify where to start/stop?

---

### Post by Max Nanasy on 2009-06-14
I assume the utility I am searching for would have to read the MBR to find out the specifics of the partitions.

---

### Post by ddrichardson on 2009-06-14
Have you tried mounting it?

---

### Post by Max Nanasy on 2009-06-14
Without '-o loop', it tells me that it is not a block device and that I should try '-o loop'; with '-o loop', it tells me that I must specify the filesystem type.

---

### Post by ddrichardson on 2009-06-14
Then specify the filesystem!```

sudo mount -o loop -t filesystem image destination
```

---

### Post by Max Nanasy on 2009-06-14
But the image isn't a filesystem: it's a drive that contains multiple filesystems.  Running fdisk on it does reveal something interesting, though: each partition is named image_path#n in the fdisk display, in which #n is the partition number, although I can't use these names for mounting.

---

### Post by ddrichardson on 2009-06-14
You know, its difficult to help when he information comes in dribs and drabs - mentioning the type of image, how it was obtained and what it contains would have been helpful in your first post!

You need to find where it starts then try it using:```

mount -oloop,offset=xxxx image.dd /mnt/point
```

---

### Post by ddrichardson on 2009-06-14
Oh  and I meant to say:```

sfdisk -l -uS image.dd
```To find the start offset.

---

### Post by iponeverything on 2009-06-14
It pretty strait forward. From the below the first partition starts at 63 and the sector size is 512. To mount it use an offset of 63*512. The same goes for second partition. The offset will 499968*512.

mount -o loop,offset=32256 imagefile.img /mnt

```
foo@bar:~$ fdisk -ul imagefile.img 
You must set cylinders.
You can do this from the extra functions menu.

Disk imagefile.img: 0 MB, 0 bytes
32 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07443446

        Device Boot      Start         End      Blocks   Id  System
imagefile.img1   *          63      499967      249952+  83  Linux
imagefile.img2          499968      997919      248976   83  Linux

```

---

### Post by Max Nanasy on 2009-06-14
That worked.  Thank you for your help.  I apologize for not giving enough information quickly enough: I thought that my meaning would be clear with the information I gave, but I was apparently wrong.

---

### Post by Max Nanasy on 2009-06-14
When I said "that worked", I was referring to [this post]("http://ubuntuforums.org/showpost.php?p=7454006&postcount=10"), BTW.

---

### Post by ddrichardson on 2009-06-14
Glad it worked for you.

---

