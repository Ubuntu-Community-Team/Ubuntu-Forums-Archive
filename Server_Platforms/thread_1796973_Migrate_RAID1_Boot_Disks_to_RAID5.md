---
title: "Migrate RAID1 Boot Disks to RAID5"
date: 2011-07-04
forum: Server Platforms
---

### Post by harshil102 on 2011-07-04
Hello, i have a server tower set up with 2 1.5tb drives in RAID1 using mdadm. I have seperate arrays for the /boot / and /Data (for my data) set up. Now i've got a new 1.5tb disk that i would like to add to this setup by converting this set up to RAID5. Im also considering the ZFS+ filesystem and am open to any other 3 disk fail-safe suggestions.
Because i am primarily considering RAID5 at the moment, my main question however is how do i convert my current setup to RAID5 considering that i've read RAID5 mdadm is not bootable?

-- I was thinking that i could remove one of my drives from the /Data array, convert the partition to RAID5 and then add in the third drive and add it to the /Boot and / RAID1 arrays as a RAID1 disk and then add it to the /Data array as a RAID5. I would then use the disk i removed from the array to copy over my Data partition to the new RAID5. I would then add this disk to the RAID1 and RAID5 arrays and allow it to rebuild. Does this seem like a feasible solution that would provide the correct results?

---

### Post by linuchsan on 2011-07-04
mdadm --create /dev/md0 --level=5 -n 2 devices you mean?

---

### Post by linuchsan on 2011-07-04
Would be -n 3 for you ;)

---

### Post by harshil102 on 2011-07-04
yupp, except md2, md0 is /boot raid1 and md1 is /. Now how do i alter those two arrays to add the third disk as another member in the RAID1 array for /boot and /?

---

