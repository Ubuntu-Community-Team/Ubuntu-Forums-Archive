---
title: "Encrypted Raid, reboot=mapped drive vanish"
date: 2008-06-30
forum: Security
---

### Post by goldfish2 on 2008-06-30
To set up my encrypted raid I ran the following commands:
```
#Creates raid with missing drive
mdadm --create /dev/md0 --level 5 -n 3 /dev/sda1 /dev/sdc1 missing

#Puts random noise on drive
dd if=/dev/urandom of=/dev/md0 bs=1M

#Adds the twofish kernel module
modprobe twofish
lsmod |grep twofish
echo "twofish" >> /etc/modules

#Creates the Encrypted drive
cryptsetup -y -c twofish-cbc-essiv:sha256 create TowerRaid /dev/md0 

#Format the mapped drive
mkfs.ext3 -b 4096 -R stride=8 /dev/mapper/TowerRaid 

#Mount
mount -O noatime /dev/mapper/TowerRaid /mnt/raid

#Add my last drive after copying over old data
mdadm /dev/md0 -a /dev/sde1 

#Saves raid configuration
mdadm --detail --scan >> /etc/mdadm/mdadm.conf

#watch raid creation progress
watch cat /proc/mdstat
```

My issue:
The pseudo-device /dev/mapper/TowerRaid has disappeared

I can recreate it by running:
```
cryptsetup -c twofish-cbc-essiv:sha256 create TowerRaid /dev/md0
```
But don't know what configuration file to put this in so it will mount automatically (and theoretically ask for my password sometime during the boot process)

Thanks,
GoldFish2

---

### Post by hyper_ch on 2008-06-30
/etc/crypttab

either
```

sda4_crypt      /dev/disk/by-uuid/7db6b61a-eab4-4451-a410-d7108c355191  none    luks

```

or

```

sdb1_crypt      /dev/disk/by-uuid/6a636e05-c562-4d4b-b3fa-54dc3d3dda3c  /root/root.key  luks

```

first one will prompt for password entry, second one will use a keyfile

then add the mapper to /etc/fstab like any other partition

---

### Post by goldfish2 on 2008-06-30
Thanks! That worked great!  Just did man crypttab for the rest of the info.  Ended up doing:

```
echo "TowerRaid /dev/md0 none cipher=twofish" >> /etc/crypttab
```

because I'm not sure if there is a UUID associated with the raid array

I tried to get the UUID by:

```
# cryptsetup luksUUID /dev/mapper/TowerRaid
/dev/mapper/TowerRaid is not a LUKS partition
Command failed.
```

I also have
```
# mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=7001fd5f:3971021d:f0a4069a:979a0f3f
```

But I think this is a different UUID, as it isn't found in that /dev folder.

Once I verify that my crypttab works I'm onto adding to my fstab, and then I think I'll encrypt my swap (I don't know why ubuntu didn't by default encrypt my swap when I told it to encrypt my root partition... seems like a bit of a waste if my password could end up as plaintext on the swap partition).

Thanks!
GoldFish2

---

### Post by hyper_ch on 2008-06-30
root partition != swap partition ;)

use something like this for swap:

```

swap    /dev/disk/by-uuid/43c8e91d-06d4-4984-9e0f-5d521fe7daa4  /dev/urandom    swap

```

---

### Post by goldfish2 on 2008-06-30
> **hyper_ch said:**
> root partition != swap partition ;)

use something like this for swap:

```

swap    /dev/disk/by-uuid/43c8e91d-06d4-4984-9e0f-5d521fe7daa4  /dev/urandom    swap

```

I worded that poorly.  I'm just saying that when I installed ubuntu and encrypting the root partition was an option, if the password to my root partition ends up in swap all is lost.  So they should encrypt both. Maybe there is something behind the scenes making sure this doesn't happen?  Donno, but I'm going to encrypt my swap anyway as my next project.

Thanks again for all your help,

GoldFish2

---

### Post by hyper_ch on 2008-07-01
if you select auto encrypt then swap will also be encrypted

---

