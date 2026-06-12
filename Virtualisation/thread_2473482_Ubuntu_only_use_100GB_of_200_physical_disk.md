---
title: "Ubuntu only use 100GB of 200 physical disk"
date: 2022-04-06
forum: Virtualisation
---

### Post by hienlp on 2022-04-06
Hello Guys,

I installed Utuntu server 20.4 LTS on my VM.
Hard disk space configed on VM is 200 GB, but in the Ubuntu OS, it only use 100GB.
Could you please help me exteand my volume on Ubuntu?

[ATTACH=CONFIG]290243[/ATTACH]

[ATTACH=CONFIG]290244[/ATTACH]

[ATTACH=CONFIG]290245[/ATTACH]

[ATTACH=CONFIG]290246[/ATTACH]

Thank with the best regards,

Hien Le

---

### Post by The Cog on 2022-04-06
Copy more files to it? 
Unused means it's free space that is available for storing more files/data.
I don't see any problem in what you show.

---

### Post by slickymaster on 2022-04-06
*Thread moved to **Virtualisation**.*

---

### Post by The Cog on 2022-04-06
Now I'm looking at a better screen, I can read the text screenshots better, and can see that the OS claims that the / partition is only 98G, whereas the  "physical" disk is 200G. But I also see that your root partition is mounting something in /dev/mapper. I think you are using an LVM (Logical Volume Management) configuration of some sort. This involves configuring PVs (Physical Volumes), collecting those into VGs (Volume Groups) and then allocating them to LVs (Logical Volumes). The LVs are what show up in /dev/mapper. There's quite a bit of indirection going on there, and I'm really not familiar with LVM, but I think that would be a good place to start reading up about. There may be quotas or size limits or something in the configuration doing this. I do remember that this command will show you the way LVs are children of PVs, but I don't remember the commands to view detailed LVM configuration parts:
```
lsblk -p
```
Sorry for misunderstanding you earlier.

---

### Post by hienlp on 2022-04-06
> **The Cog said:**
> Now I'm looking at a better screen, I can read the text screenshots better, and can see that the OS claims that the / partition is only 98G, whereas the  "physical" disk is 200G. But I also see that your root partition is mounting something in /dev/mapper. I think you are using an LVM (Logical Volume Management) configuration of some sort. This involves configuring PVs (Physical Volumes), collecting those into VGs (Volume Groups) and then allocating them to LVs (Logical Volumes). The LVs are what show up in /dev/mapper. There's quite a bit of indirection going on there, and I'm really not familiar with LVM, but I think that would be a good place to start reading up about. There may be quotas or size limits or something in the configuration doing this. I do remember that this command will show you the way LVs are children of PVs, but I don't remember the commands to view detailed LVM configuration parts:
```
lsblk -p
```
Sorry for misunderstanding you earlier.

Sorry for the wording that confused to you.

Here is the resuilt of command: lsblk -p

```
NAME                                  MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
/dev/loop0                              7:0    0 55.5M  1 loop /snap/core18/2284
/dev/loop1                              7:1    0 55.5M  1 loop /snap/core18/2344
/dev/loop2                              7:2    0 61.9M  1 loop /snap/core20/1376
/dev/loop3                              7:3    0 67.9M  1 loop /snap/lxd/22526
/dev/loop4                              7:4    0 61.9M  1 loop /snap/core20/1405
/dev/loop5                              7:5    0 67.8M  1 loop /snap/lxd/22753
/dev/loop6                              7:6    0 43.6M  1 loop /snap/snapd/15177
/dev/loop7                              7:7    0 44.7M  1 loop /snap/snapd/15314
/dev/sda                                8:0    0  200G  0 disk
&#9500;&#9472;/dev/sda1                             8:1    0    1M  0 part
&#9500;&#9472;/dev/sda2                             8:2    0    1G  0 part /boot
&#9492;&#9472;/dev/sda3                             8:3    0  199G  0 part
  &#9492;&#9472;/dev/mapper/ubuntu--vg-ubuntu--lv 253:0    0 99.5G  0 lvm  /
```

I used the following commands to expand mapper lvm:
```
lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv
resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```
Thank you for your support!

---

