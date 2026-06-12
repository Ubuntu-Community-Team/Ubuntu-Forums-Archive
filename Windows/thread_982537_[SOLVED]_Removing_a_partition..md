---
title: "[SOLVED] Removing a partition."
date: 2008-11-14
forum: Windows
---

### Post by Deep Blue on 2008-11-14
I made a partition to test out Windows 7, but apparently you can't install it on an External USB drive. I'm wondering how to get rid of this:

[http://img32.picoodle.com/img/img32/3/11/14/f_Untitledm_07688ef.jpg](http://img32.picoodle.com/img/img32/3/11/14/f_Untitledm_07688ef.jpg)

The green space, so I can have my 500 gigs back on Disk 1 and make a partition on Disk 0. (when I right click the empty space, delete partition is blanked out). 

Appreciate your aid,
nikoPSK

EDIT: To further elaborate, it shows up as free space and I have tried fiddling with extending the original volume.
EDIT 2: Nevermind, I got it now, now I just need to find out how to stop Windows restricting the shrink size in C:\\.

---

### Post by Jammanuser on 2008-12-12
> **Deep Blue said:**
> I made a partition to test out Windows 7, but apparently you can't install it on an External USB drive. I'm wondering how to get rid of this:

[http://img32.picoodle.com/img/img32/3/11/14/f_Untitledm_07688ef.jpg](http://img32.picoodle.com/img/img32/3/11/14/f_Untitledm_07688ef.jpg)

The green space, so I can have my 500 gigs back on Disk 1 and make a partition on Disk 0. [COLOR="Red"](when I right click the empty space, delete partition is blanked out)[/COLOR]. 

Appreciate your aid,
nikoPSK

EDIT: To further elaborate, it shows up as free space and I have tried fiddling with extending the original volume.
EDIT 2: Nevermind, I got it now, now I just need to find out how to stop Windows restricting the shrink size in C:\\.

You can't delete a partition that doesn't exist! ;) The empty space is what's left on ur Windows partition...in other words, its the free space not occupied by Windows files, programs, etc...hence the name "free space"! :D 

Just FYI u can also shrink the Windows partition with Diskpart...a command line tool accessed by the command prompt...simple type:

```
diskpart
```

and that will open up the tool, and then to shrink it, u can use the following commands:

```
list disk
select disk 0
list partition
select *partition u want to shrink* 
shrink
```

Its a simple as that! of course, obviously, the commands might change a little to fit ur particular situation...for instance, typing "list disk" might list more disks than 0, which would be odd, but would probably indicate that u have more than one physical, such as an external HDD! (but let's not go in that...unless u have one!) the *partition u want to shrink* obviously should be replaced with the correct partition...i.e. "partition 3" without the quotes!

Anyway...i'm sure u get my drift! 

Hope this helps! :guitar:

Cheers! ):P

Jam Man

:lolflag:

---

### Post by Deep Blue on 2008-12-14
> **Jammanuser said:**
> You can't delete a partition that doesn't exist! ;) The empty space is what's left on ur Windows partition...in other words, its the free space not occupied by Windows files, programs, etc...hence the name "free space"! :D 

Just FYI u can also shrink the Windows partition with Diskpart...a command line tool accessed by the command prompt...simple type:

```
diskpart
```

and that will open up the tool, and then to shrink it, u can use the following commands:

```
list disk
select disk 0
list partition
select *partition u want to shrink* 
shrink
```

Its a simple as that! of course, obviously, the commands might change a little to fit ur particular situation...for instance, typing "list disk" might list more disks than 0, which would be odd, but would probably indicate that u have more than one physical, such as an external HDD! (but let's not go in that...unless u have one!) the *partition u want to shrink* obviously should be replaced with the correct partition...i.e. "partition 3" without the quotes!

Anyway...i'm sure u get my drift! 

Hope this helps! :guitar:

Cheers! ):P

Jam Man

:lolflag:I actually got Windows 7 working, on C:\\ but I used GParted to make the partition. :)

---

