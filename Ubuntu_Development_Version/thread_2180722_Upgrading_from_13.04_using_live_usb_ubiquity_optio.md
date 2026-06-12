---
title: "Upgrading from 13.04 using live usb ubiquity option. Problem with multiple OS's"
date: 2013-10-14
forum: Ubuntu Development Version
---

### Post by philinux on 2013-10-14
If you have more than one install then ubiquity will not offer an upgrade option.

In my case I have 13.04 on sda and 13.10 on sdb.

If I had one hard drive with just 13.04 then the upgrade option would be displayed.

Also if you have more than one install on one hard drive I think it would not work either.

Note - i forgot this was only a test case report and not a real bug report when i commented.

[https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1229511](https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1229511)

---

### Post by richardsdma on 2013-10-14
sad o hear this! i have 3 OS on my sda

---

### Post by Cavsfan on 2013-10-14
I've got 7 operating systems on my drive. I only upgrade my LTS version though. Always clean installs on everything else but, this is interesting nonetheless.

---

### Post by philinux on 2013-10-14
> **Cavsfan said:**
> I've got 7 operating systems on my drive. I only upgrade my LTS version though. Always clean installs on everything else but, this is interesting nonetheless.

Yes, if that is the case you'll see this instead of an Upgrade option.  More of a feature than a bug?

---

### Post by Cavsfan on 2013-10-14
> **philinux said:**
> Yes, if that is the case you'll see this instead of an Upgrade option.  More of a feature than a bug?

Actually I use the "something else" option. It scares the heck out of me every time too. I am usually using a partition that I have used before.
For example, when Saucy is finally released, I'll back up everything important (which isn't a whole lot on a development system) on my USB drive.
Then install the Saucy ISO on the same partition that it was previously. I always make sure the format option is checked.

That way my custom grub on my other installs are still up to speed and I just have to re-label the new Saucy partition via
```
sudo tune2fs -L "Saucy" /dev/sda7
```

Drs305 showed me how to do that a while back. It makes it much easier to look at Devices under Files.

```
cavsfan@cavsfan-MS-7529:~$ sudo blkid
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Precise" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="e14dc02e-6ea8-4c95-b4d0-9dc04d32294d" TYPE="swap" 
/dev/sda5: LABEL="Mint-Olivia" UUID="b796e378-c9dd-4557-825b-5d5687197609" TYPE="ext4" 
/dev/sda6: LABEL="Quantal" UUID="4d6a25ba-5a4b-4da4-8ae1-9939bc6b6b4c" TYPE="ext4" 
/dev/sda7: LABEL="Saucy" UUID="91e5e39f-e198-4726-a165-a6ea24ea3d67" TYPE="ext4" 
/dev/sda8: LABEL="Raring" UUID="21fd827b-a771-4e96-9311-5ad11382d6f1" TYPE="ext4" 
/dev/sda9: LABEL="Mint-Maya" UUID="77cf61db-2e8b-4531-9594-80f35ad4dc69" TYPE="ext4" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs" 

```

[ATTACH=CONFIG]246944[/ATTACH]

---

### Post by craig10x on 2013-10-14
Hmmm... was not aware of this....so the live iso installer only shows the upgrade option if you just have ubuntu by itself on your drive (as i do)?
Perhaps someone who has several distros on their drive can run the live iso and check it out...i can't because i am not dual (or multiple) booting....

If that is the case, it is a shame because it seems like probably one of the best ways to upgrade...as far as reliability goes...

---

### Post by philinux on 2013-10-14
> **craig10x said:**
> 
Perhaps someone who has several distros on their drive can run the live iso and check it out...i can't because i am not dual (or multiple) booting....
.

That would be me then . ):P

It detected two.

---

