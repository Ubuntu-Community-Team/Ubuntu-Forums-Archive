---
title: "Expand LVM with underlying LVs and EXT4 to the whole disk space."
date: 2016-01-13
forum: Virtualisation
---

### Post by hierstehtnormaleinname on 2016-01-13
Hi,
meanwhile I gave up fixing my problems on an virtual image that I got because is to much time consuming. Now I switched back to an older backup and manually reconfigured all chances that I set since than.[B]

I also considered tipps [/B][URL="http://ubuntuforums.org/member.php?u=1044547"][B][COLOR=#DD4814][B]MAFoElffen
[/B][/COLOR][/B][/URL]      gave me in a previous thread. 

Now my virtual server is up and running. I copied the 50 Gb backup to a new fix 200 Gbyte disk. Everything work fine and the server is up. 
There is just a last question for what I may ask for help. 

What is the best solution to expand the copied 50 Gb LVM (dd copy of an 50 GByte virtual disk image to a new 200 GByte disk) since it is still claiming 50 GByte only.
I guess it should be necessary to expand the volume group to the whole disk including the new free disk space. Also I will need to expand the logical volume for the system (swap can remain in its size) and than I need to expand the underlying ext4.

I would recommend that instate of adding a second disk to my lvm.

What would be the best way to do this?

I have found one tutorial from [http://bhaisaab.org/logs/lvm-cloning/](http://bhaisaab.org/logs/lvm-cloning/) 

But he is removing the the partition using fdsik and than he is adding it again to get the whole disk space. Afterwards the usual pvresize and so on.
Is his way really save? I own a backup but I mean is that way he solves it via fdisk the way you would do it?

---

### Post by hierstehtnormaleinname on 2016-01-13
Well I tried this and it works fine so far. Hope there will be no error later on relating to this :P

---

