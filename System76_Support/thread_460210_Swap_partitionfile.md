---
title: "Swap partition/file?"
date: 2007-05-31
forum: System76 Support
---

### Post by greg_g on 2007-05-31
I received my Ratel on Tuesday.  Everything seemed fine.  Until last night when I noticed something interesting.

I wouldn't have noticed it unless I had installed kde.  I was familiarizing myself with kde and I was looking at the KSysGuard app (System Monitor for gnome folk), and where it had the stats for swap, well, there were none.

So, I ran the command "swapon -s" and the output is simply:
```
$ swapon -s
Filename                                Type            Size    Used    Priority

```
Thats it, no, there is nothing under that line.

So, I believe that means that my swap is not enabled.

Here is the list of partitions on my drive (sda)
```
$ sudo sfdisk -l /dev/sda

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  29244   29245- 234910431   83  Linux
/dev/sda2      29245   30401-   1157-   9288121+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      29245+  30401-   1157-   9288090   82  Linux swap / Solaris
```

So, I believe that last part, sda5, is a 9 gig unused swap partition.

How does one enable swap?
I found this howto from a Redhat manual:
[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

If I start at step 3 and substitute sda5 where appropriate, will that work?  I assume it will since those commands are linux, not Redhat specific.

Just want the reassurance from you guys.

By the way, I searched this system76 support forum and found a couple other references to computers coming without the swap enabled.  Might need to update a script somewhere.

Thanks for everything though.  My system is working fine since I was able to get 2gigs of ram, but I just want everything how it should be.

Thanks again,

greg

EDIT:  I just took a look at my fstab, and it looks like there is a swap line in there, so now this is confusing me.
```
$ cat fstab
# /etc/fstab: static file system information.
#
# &lt;file system&gt; &lt;mount point&gt;   &lt;type&gt;  &lt;options&gt;       &lt;dump&gt;  &lt;pass&gt;
proc    /proc   proc    defaults        0       0
# /dev/sda1
UUID=3a2e2fde-ce08-4544-b6d6-7da473bc2080       /       ext3    defaults,errors=remount-ro      0       1
# /dev/sda5
UUID=4f5df747-f6cd-4c73-96c3-ed07a5fbc6fd       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto     0       0
```

---

### Post by thomasaaron on 2007-05-31
Go to a terminal and type: top

The fifth line down will tell you how much swap you have and how much is being used.
If it says none of it is being used, open GIMP and pull up a big file. You should see that some of your swap is being used, and, by extension, that it is activated.

Attached is a screenshot of my swap usage.

Best,
Tom

---

### Post by greg_g on 2007-05-31
Well, here is a screenshot of my top.  While gimp was open and I was messing with a full screen screenshot. 

The 0k total is the part that worries me.

greg

---

### Post by greg_g on 2007-05-31
Also, might as well ask this question too; why is my swap partition 9.2 gigs large?  I think the motherboard only supports 2 x 2gig dimms.  I could be wrong, I only opened the case for about 2 minutes when it first came.  I like to see how people install hardware (tie cables, etc).

Thanks again thomas

greg

---

### Post by thomasaaron on 2007-05-31
The swap partition sized on the Ratel is based on the size of your hard drive.
So, the 9GB swap is probably correct.

OK, it looks like your fstab might be hosed.
Please post the results of cat /etc/fstab > ~/Desktop/fstab

ALso post the results of:
ls /dev/disk/by-uuid/ -alh

---

### Post by greg_g on 2007-05-31
Tom,

My fstab is above a couple replies.

Here is the other command:

```
$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root  80 2007-05-31 09:13 .
drwxr-xr-x 5 root root 100 2007-05-31 09:13 ..
lrwxrwxrwx 1 root root  10 2007-05-31 09:13 2d7b8510-389a-401b-9b16-d44e6ca91248 -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-05-31 09:13 3a2e2fde-ce08-4544-b6d6-7da473bc2080 -> ../../sda1
```

Thanks,

greg

PS: I will be away for a bit, so no more of my 10 minute reply times ;).

---

### Post by greg_g on 2007-05-31
So, just asking in general for all who are looking that might know.

It looks like the UUID numbers are different for the drives than what is in the fstab. If I replace the bad UUID with the ones from the command "ls /dev/disk/by-uuid/ -alh" it should work right?

For completeness, here is my current fstab:
```

# /etc/fstab: static file system information.
#
# &lt;file system&gt; &lt;mount point&gt;   &lt;type&gt;  &lt;options&gt;       &lt;dump&gt;  &lt;pass&gt;
proc    /proc   proc    defaults        0       0
# /dev/sda1
UUID=3a2e2fde-ce08-4544-b6d6-7da473bc2080       /       ext3    defaults,errors=remount-ro      0       1
# /dev/sda5
UUID=4f5df747-f6cd-4c73-96c3-ed07a5fbc6fd       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto     0       0
```

Here is the output of the other command:
```
$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root  80 2007-05-31 09:13 .
drwxr-xr-x 5 root root 100 2007-05-31 09:13 ..
lrwxrwxrwx 1 root root  10 2007-05-31 09:13 2d7b8510-389a-401b-9b16-d44e6ca91248 -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-05-31 09:13 3a2e2fde-ce08-4544-b6d6-7da473bc2080 -> ../../sda1
```

So I should just have to make my fstab look like this right?:
```

# /etc/fstab: static file system information.
#
# &lt;file system&gt; &lt;mount point&gt;   &lt;type&gt;  &lt;options&gt;       &lt;dump&gt;  &lt;pass&gt;
proc    /proc   proc    defaults        0       0
# /dev/sda1
UUID=3a2e2fde-ce08-4544-b6d6-7da473bc2080       /       ext3    defaults,errors=remount-ro      0       1
# /dev/sda5
UUID=2d7b8510-389a-401b-9b16-d44e6ca91248       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto     0       0
```

Or do I also need to change the "none" from the sda5 line to something like "swap"?  I am unsure of the syntax for that one.

Thanks all,

greg

---

### Post by greg_g on 2007-05-31
tom-

Well, after some googling I did this:

"swapon /dev/sda5"

then "free" and it is now listed there!  Weee!

Then, I changed my fstab to have the correct UUID.  And I also changed the "none" to "swap" because that is how all of the guides online had it set.

If that is wrong, let me know.

Thanks,

greg

---

### Post by thomasaaron on 2007-06-01
That sound right.
Does it show up now in "top"?

---

### Post by greg_g on 2007-06-01
Yep, shows up in top. All good now.

Thanks for the help tom.


greg

---

### Post by southernman on 2007-06-04
Thank you both... Greg for posting this thread and Tom for helping you (along with all our friends at google) get this problem resolved.

I had botched my swap file doing the Gparted thing several days ago. Although never noticing any slow down on my system, it bugged me none the less. Deciding that I'd search the forums (knowing the problem had already been discussed and resolved), when you guys saved the day.

After getting swap back... and running gimp, I still don't get into the swap part of memory. That's not a complaint, just an observation! 

Isn't the search feature wonderful?

Thanks again!

[edited]Added screeny to show the 0 swap useage.[/edited]

---

