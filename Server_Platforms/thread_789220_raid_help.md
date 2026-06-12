---
title: "raid help"
date: 2008-05-10
forum: Server Platforms
---

### Post by reckless2k2 on 2008-05-10
i've got a 3ware 7000-2 that requires format for array setup. i've got a 250GB hard drive that's been running my server. for the raid array, i've got two 750gb drives. 

how do i get the image from the 250gb to the raid array? 

i'm thinking i tar the entire 250gb drive and then copy it to the 750 array after it's been formatted. i'm just wondering if this is the right approach. i'm thinking that if i do that as well i'll have to use the disk partitioner to expand to the remaining 500gb from the 250gb image. 

am i right? 

help!

---

### Post by reckless2k2 on 2008-05-10
or could i just rsync my / partition to my NAS and then install clean on the new 750gb raid and then rsync back the / partition? sounds like a winning and then i don't have to worry about the drive size change.

---

### Post by windependence on 2008-05-11
You could do that or you could set up your RAID partition and then just do a copy with dd.

dd if=/dev/sda of=/dev/sdb bs=4k conv=notrunc,noerror

Where sda is your source and sdb is your destination. Of course if you are using an ATA drive your source would probably be hda. You will have to check the device names after they are set up.

-Tim

---

### Post by reckless2k2 on 2008-05-15
i appreciate the response but i'm still struggling because it is going from hda to sda and i would have to boot from a live cd to do what you're suggesting i think. i don't think i could even rsync over the entire / while it's active. 

i installed the OS on the formatted array but i'm struggling to get the old image on it. i know i have to preserve some settings in fstab and mtab for sda.

---

