---
title: "Swap Partition Inactive"
date: 2009-04-08
forum: Security
---

### Post by yeehi on 2009-04-08
Whole disk encryption was set up manually during installation on Jaunty Jackalope. It isn´t possible, afaiu, to have the swap partition encrypted during setup, so after creating a partition for swap and marking it not for use, I added the following lines:

To /etc/crypttab 

```
cswap	/dev/sda2	/dev/urandom	swap

```

To /etc/fstab 

```
/dev/mapper/cswap	none	swap	sw	0	0
```


That should make swap work, but it isn´t going.

What can I do?

---

### Post by RansomStark on 2009-04-09
As you marked the partition do not use, you now need to create the encrypted partition, use the 3 commands below (you will need to change the device to match your names)

cryptsetup -d /dev/random create swap /dev/partition
mkswap /dev/mapper/swap
swapon /dev/mapper/swap

Usually I do a reboot at this point to make sure the init changes have taken effect.

Ransom

---

