---
title: "Ubuntu 7.04 sucks"
date: 2008-04-04
forum: Testimonials &amp; Experiences
---

### Post by Bad Hand on 2008-04-04
I loaded Ubuntu on to one of my 3 hard drives, I had windows XP on drive C and I loaded Ubuntu on to drive D I wanted a dual boot system what happened was Ubuntu took over both drive C and D and I lost windows XP and all of my programs I do have a back up for My Documents. I can't  access drive C and I can't get rid of Ubuntu. I have even tried reloading Windows XP but it doesn't work. How do I remove Ubuntu so I can use my C drive? 

I have ordered a new drive and when it arrives I am removing the other 2 drives.

---

### Post by caravel on 2008-04-04
Hmmm... "ubuntu 7.04 sucks" is not going to get you many positive responses on an Ubuntu forum.

First problem is that you installed 7.04 which is an old version of the OS, and secondly you didn't follow the installation instructions.

There are thousands of threads on here describing as to how to restore the windows MBR.  But, try booting from your XP CD and go to the recovery console, log in and enter the command "fixmbr" followed by "fixboot".  Then reboot the machine.  Once you're in to windows use the logical disk manager to partition and format the Ubuntu partitions back to NTFS or whatever.  Then you'll be good to go.

---

### Post by crjackson on 2008-04-04
> **Bad Hand said:**
> I loaded Ubuntu on to one of my 3 hard drives, I had windows XP on drive C and I loaded Ubuntu on to drive D I wanted a dual boot system what happened was Ubuntu took over both drive C and D and I lost windows XP and all of my programs I do have a back up for My Documents. I can't  access drive C and I can't get rid of Ubuntu. I have even tried reloading Windows XP but it doesn't work. How do I remove Ubuntu so I can use my C drive? 

I have ordered a new drive and when it arrives I am removing the other 2 drives.

I understand your frustration but your title doesn't appeal to the community for help.  Ubuntu doesn't prevent you from installing XP again.  It sounds like you either have a hardware problem or just made a really bad error during the install.

---

### Post by eternicode on 2008-04-04
> **Bad Hand said:**
> ...what happened was Ubuntu took over both drive C and D and I lost windows XP and all of my programs...

I would expect Ubuntu to install the grub boot manager, which should give you a choice between Windows or Ubuntu when you boot up.

> **crjackson said:**
> ...or just made a really bad error during the install.

Let us hope this really bad error wasn't installing over Windows...

Also, if you don't want those two HDs, can I have them? :D

---

### Post by lerigan on 2008-04-04
Maybe it's an ID 10 T error. It happens a lot with many users, regardless of the operating system they're using...:)

---

### Post by Technoviking on 2008-04-04
You can catch more flies with honey than with vinegar.

---

### Post by JoshuaRL on 2008-04-04
> **Mike said:**
> You can catch more flies with honey than with vinegar.

[http://xkcd.com/357/](http://xkcd.com/357/)

I am so sorry, I just had to do that.

---

### Post by Tatty on 2008-04-04
If you installed Ubuntu correctly, you should have a screen appear on boot which will give you an option between booting into Ubuntu, or booting into Windows.

If you did not install correctly then you may have told Ubuntu to erase windows.

Can you boot into ubuntu fine?  If so then please open a terminal (Applications->Accessories->terminal and post the output of ```
sudo fdisk -l
``` that way we can see if you have erased windows.

If there is still a windows partiton on your drive then it will probably be fixable.

**Edit:** Alternatively, if you simply want to remove ubuntu and re-install windows, all you have to do is put in a windows disc and reboot the machine.  The computer should load the cd on boot and then you can begin the installation.

---

### Post by slimdog360 on 2008-04-04
> **Bad Hand said:**
> I loaded Ubuntu on to one of my 3 hard drives, I had windows XP on drive C and I loaded Ubuntu on to drive D I wanted a dual boot system what happened was Ubuntu took over both drive C and D and I lost windows XP and all of my programs I do have a back up for My Documents. I can't  access drive C and I can't get rid of Ubuntu. I have even tried reloading Windows XP but it doesn't work. How do I remove Ubuntu so I can use my C drive? 

I have ordered a new drive and when it arrives I am removing the other 2 drives.

you suck

---

### Post by Technoviking on 2008-04-04
> **JoshuaRL said:**
> [http://xkcd.com/357/](http://xkcd.com/357/)

I am so sorry, I just had to do that.

Noooo, my world is a lie :).

---

### Post by Bad Hand on 2008-04-04
Ok I am sorry about the "sucks" but I followed all the steps, and have I have tried everything that has been mentioned and nothing works other than Ubuntu. I specified that I wanted to load Ubuntu on drive D but it took over both drive D and C and I had loaded it from a boot of the CD and not through Windows.

When my new drive arrives I am going to try again to recover C drive and Windows or just try to repartition, format it and start over.

---

### Post by Tatty on 2008-04-04
> **Bad Hand said:**
> Ok I am sorry about the "sucks" but I followed all the steps, and have I have tried everything that has been mentioned and nothing works other than Ubuntu. I specified that I wanted to load Ubuntu on drive D but it took over both drive D and C and I had loaded it from a boot of the CD and not through Windows.

When my new drive arrives I am going to try again to recover C drive and Windows or just try to repartition, format it and start over.

Please load up a terminal (Applications->Accessories->Terminal) and post the output of:

```
sudo fdisk -l
```

(note: thats a lowercase L not a 1)

---

### Post by lerigan on 2008-04-04
> **JoshuaRL said:**
> [http://xkcd.com/357/](http://xkcd.com/357/)

I am so sorry, I just had to do that.
LOL!!!

---

### Post by abhilashkumar on 2008-04-04
I think you used the auto partition option instead of the guided or manual...
Happened to me, but I fixed the error by booting using the Vista installer CD and fixing the MBR. Then I redid the Ubuntu installation.

---

### Post by niteshifter on 2008-04-04
> Maybe it's an ID 10 T error. It happens a lot with many users, regardless of the operating system they're using..
I used to work with an old curmudgeon of a sys-admin (Sun workstations / Sun OS) that called these situations thusly in his personal log:

/dev/iatk IO Error

(I***t At The Keyboard)

---

### Post by Bad Hand on 2008-04-04
Here is what came up. Thanks for the help this hasn't been one of my better days if anything could go wrong today it did.

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1023     8217243   54  OnTrackDM6
/dev/hda2   *        1024        4111    24804360    c  W95 FAT32 (LBA)

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9327    74919096   83  Linux
/dev/hdb2            9328        9729     3229065    5  Extended
/dev/hdb3            9730        9730           0    e  W95 FAT16 (LBA)
/dev/hdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sde: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        2434    19551073+   c  W95 FAT32 (LBA)
george@george-desktop:~$

---

### Post by Tatty on 2008-04-04
> **Bad Hand said:**
> Here is what came up. Thanks for the help this hasn't been one of my better days if anything could go wrong today it did.

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1023     8217243   54  OnTrackDM6
/dev/hda2   *        1024        4111    24804360    c  W95 FAT32 (LBA)

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9327    74919096   83  Linux
/dev/hdb2            9328        9729     3229065    5  Extended
/dev/hdb3            9730        9730           0    e  W95 FAT16 (LBA)
/dev/hdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sde: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        2434    19551073+   c  W95 FAT32 (LBA)
george@george-desktop:~$

Thats an interesting partition layout.  Did you have XP installed on a FAT32 partition?  If not then it looks like you have probably erased windows somewhere.  

Normally XP is installed on an NTFS partition - but i dont see one.  I do see 2 fat32 partitions and 1 FAT16 partition (although that is 0 blocks big)

can you post the ouput of:
```
cat /etc/fstab
```

**EDIT:** Also ```
cat /boot/grub/menu.lst
```

---

### Post by crashcoredump on 2008-04-04
Not having a level of commitment that allows you to just run Ubuntu (or you fav *nix flav) is about 90% of the problems I see.

*"Waah I lost my Winblows whatever"* is too frequent a complaint!

If you just install Ubuntu and make an honest effort to make it work it WILL do everything you need and MORE. 

But continuing to half commit and slide into *nix in a dual, tri boot environment is never going to cut it. What happens when you get stuck? Just boot back up into Win whatever???

What if you lived in a different country? 
You WOULD learn to adapt, but if you could just head to the English speaking section everytime it was difficult you would never progress......

Thats my spiel....

---

### Post by bodhi.zazen on 2008-04-04
wow

I moved this thread to what I feel is a more appropriate section of the forums.

I am also closing it now as I think it has run it's course. You had a bad experience, you are frustrated, and you expressed your frustration.

@Bad Hand : Despite the general tone of this thread I think we are all sorry you had this experience.

Lessons learned : Backup you data, read and understand the documentation before you install, and ask for help if you get stuck.

Try to learn from what happened to you and I think you will find this community quite helpful, but I advise you change your posting style.

Feel free to start a new (kinder) thread if you need further assistance ...

---

### Post by bodhi.zazen on 2008-04-04
> **JoshuaRL said:**
> [http://xkcd.com/357/](http://xkcd.com/357/)

I am so sorry, I just had to do that.

LOL to death.

---

