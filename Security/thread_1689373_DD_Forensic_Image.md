---
title: "DD Forensic Image"
date: 2011-02-16
forum: Security
---

### Post by Cooper88 on 2011-02-16
I was given a forensic Image which I now know is a DD image of the drive (Vista) and am trying to mount the image or extract the image to another drive. I'm not sure of the extention type or if the image is a partition or the entire drive. I think it is the entire drive.
 
Is it possible to mount a DD image to a device. If I can't do that I just want to extract the files to run some programs against the drive. Can I view the files under Ubuntu or do I have to remove the drive and stick it into a Vista computer.
 
I purchased a second drive today and was hoping the command line would be something simple.
 
Thanks for your community support. Much better then windows :)
 
Or am I on the wrong track, should I be doing this all in a windows environment. The reason I picked ubuntu was because of the reporting tools.

---

### Post by Cooper88 on 2011-02-16
I forgot to add, if this is a forensic image of the drive do I need to restore the image on a separate device. I have 2 images I need to restore 100 gigs each so I bought once 500 gig drive. Should I purchase a second drive?

---

### Post by iponeverything on 2011-02-16
fdisk -l will show you the partition structure. 

mount the selected partition via loopback - providing correct offset to the mount command. 

google "linux mount with offset"

---

### Post by movieman on 2011-02-16
And remember to mount it read-only. I'd guess you could make the file on disk read-only to ensure it can't be changed by accident.

---

### Post by Cooper88 on 2011-02-17
I've tried to do a restore using the following command:
 
dd if=/media/sdc2/QCE3_1/QCE3_1.001 of=/dev/sdb
 
and I'm able to extract the image onto a new disk but I can't view the files. 

The image was origionaly created by LOGICUBE TALON     
 
*  Operating Mode: DD Img(2GB)       Address Mode: LBA                 * 
*  Verify        : MD5-Fil+V             Speed   : UDMA-5              * 
*  Connection    : Direct                                              
 
Is there something I'm missing? I would think this would be the easy part.
 
I've tried to use MountManger and the Disk Utility. When that didn't work I moved the drive to xp, vista and windows 7 without any luck. 
 
Any ideas?

---

### Post by Cooper88 on 2011-02-17
I tried to mount but that didn't work either.

Disk QCE3_1.001: 242 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/240/63 (instead of 242/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

Device Boot    Start       End   #sectors  Id  System
QCE3_1.001p1          2048 152203255  152201208   7  HPFS/NTFS
QCE3_1.001p2   * 152203264 156299263    4096000   7  HPFS/NTFS
QCE3_1.001p3             0         -          0   0  Empty
QCE3_1.001p4             0         -          0   0  Empty

mount -o ro,loop,offset=77928066560 -t ntfs-3g QCE3_1.001 /media/sdb2

NTFS signature is missing.

---

### Post by unspawn on 2011-02-17
> **Cooper88 said:**
> I'm not sure of the extention type or if the image is a partition or the entire drive. I think it is the entire drive.
There is no need to "think" or "guess" as the Talon creates 'dd'-style images in 650 MB, 2 GB and 4 GB size segments. So knowing common hard disk sizes and your slice size (2 GB) you know how much slices make up the complete image.
 

> **Cooper88 said:**
> Or am I on the wrong track, should I be doing this all in a windows environment. The reason I picked ubuntu was because of the reporting tools.
IMHO that depends on your knowledge, experience and time frame. If you're used to say FTK or Encase you can't compare that with learning-Linux-in-a-day *and* working efficiently with say pyFLAG or the Sleuthkit.


> **Cooper88 said:**
> dd if=/media/sdc2/QCE3_1/QCE3_1.001 of=/dev/sdb
If you want to do that you'll have to write *all* segments to disk and at the right offset. OTOH the Sleuthkit can readin disk segments as does the free-of-cost FTK Imager on the other platform.

---

### Post by Kinstonian on 2011-02-18
Can you give any background on where the image came from and why you are investigating it?  If this has the possibility of going to court, I'd strongly recommend you contact a professional since there is a good possibility that you will ruin evidence.

If this is just for learning or fun...  Here's a [blog post](http://computer-forensics.sans.org/blog/2010/01/11/using-image-offsets) about how to mount dd images, which is a lot easier than copying the data to another drive.

You can either use "cat" to merge the split files or check out [this thread](http://www.forensicfocus.com/index.php?name=Forums&file=viewtopic&p=6539427) for some other options.

---

### Post by Cooper88 on 2011-02-18
[COLOR=black][FONT=Verdana]We had some students doing some bad things and we were going to create a super timeline to determine which student did what. I've used the tool before and the contractor created a forensic DD image using TALON and a simple restore command isn't working. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][http://www.ratzinhozen.com/samples/TalonMan.pdf](http://www.ratzinhozen.com/samples/TalonMan.pdf)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The talon manual says to use encase, but the dd is just  a raw image. How is this any different then when I create my own backup of an disk. I used this all the time a few years ago without any issues. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I'm running gparted to rebuild the partition table. Ubuntu shows me that the restore partition is complete. But it doesn't know what type of partition it is and can't mount the drive. But I know the files are there. However, when I import the images into Autopsy I can view the files so now I'm confused.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]As a test I imaged my own drive and restored it on the same drive and didn't have any problems. Which leads me to wonder if the image is corrupt or I'm missing something.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]Once again, thanks for everyone's help.[/FONT][/COLOR]

---

### Post by Cooper88 on 2011-02-18
root@cooper-desktop:/media/sdb1# mmls -t dos /media/sdc2/QCE3_1/QCE3_1.???DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

     Slot    Start        End          Length       Description
00:  Meta    0000000000   0000000000   0000000001   Primary Table (#0)
01:  -----   0000000000   0000002047   0000002048   Unallocated
02:  00:00   0000002048   0152203255   0152201208   NTFS (0x07)
03:  -----   0152203256   0152203263   0000000008   Unallocated
04:  00:01   0152203264   0156299263   0004096000   NTFS (0x07)
05:  -----   0156299264   0156301505   0000002242   Unallocated


root@cooper-desktop:/media/sdb1# sudo mount -t ntfs-3g -o ro,loop,show_sys_files,offset=1048576 /media/sdc2/QCE3_1/QCE3_1.001 /media/sdb1/DATA/
Failed to read last sector (152201207): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by Cooper88 on 2011-02-18
The dd I was given was split into 2 gig files. The DD image is also RAW. Do I have to create an image to do a proper mount and does the file partition type matter? 

/media/sdb1/DATA/ is not NTFS. I've also tried other formats with no success.

---

### Post by Cooper88 on 2011-02-19
I had to merge the files before running the command above. 
 
cat dd_.* > fullimage.dd
 
Once I did that I was able to mount the image. What a waste of time. I think I had the same issue a few years ago. And I asked this same question why?

---

### Post by cariboo on 2011-02-19
> Once I did that I was able to mount the image. What a waste of time. I think I had the same issue a few years ago. And I asked this same question why?

I use a combination of zim on my netbook and dokuwiki on my home file server to keep track of things like that.

---

### Post by cprofitt on 2011-02-20
Lucky you had a contractor who could make a forensic image. I do not have such luxury and lack a write blocker so I can not take true forensic images.

---

### Post by felixdzerzhinsky on 2012-05-12
> **cprofitt said:**
> Lucky you had a contractor who could make a forensic image. I do not have such luxury and lack a write blocker so I can not take true forensic images.



You can use an Ubuntu based Caine LiveCD or USB for making images without a write blocker. It does not mount any file systems writable.

[http://www.caine-live.net/](http://www.caine-live.net/)

Read the mounting policy carefully before using and document your step.

[http://www.caine-live.net/page8/page8.html](http://www.caine-live.net/page8/page8.html)

---

### Post by unspawn on 2012-05-14
> **felixdzerzhinsky said:**
> It does not mount any file systems writable.
...but don't *assume* block device read-only mode means read-only mode: [http://www.forensicswiki.org/wiki/Forensic_Linux_Live_CD_issues](http://www.forensicswiki.org/wiki/Forensic_Linux_Live_CD_issues). Compare disk hashes before and after the capture *to ensure* nothing is altered. BTW AFAIK Encase still provides it's Linux capture tool 'linen' for free.

---

### Post by a2j on 2012-05-14
dd images can be used with liveview and vmware server. You can boot that image up as if you had access to its original box.

---

