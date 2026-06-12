---
title: "18446744067 GB unallocatad space"
date: 2010-02-28
forum: The Cafe
---

### Post by cent on 2010-02-28
Apparently there is a rift in the bit continuum inside my hard drive: 
[ATTACH]148535[/ATTACH]
what happens if I press create? will it create a FAT file system with the size of 18446744067491 MB?

---

### Post by jflaker on 2010-02-28
Something tells me the Drive is a bit over zealous.

It will probably try/start to create a file system but will quickly run out of real estate in doing so.

I remember back before the GB drives, I had a 700MB drive that claimed it was in the TB....so I formatted and the drive crashed as it ran out of real estate.....I ended up having to use the manufacturer's utility to low level format and start over.

---

### Post by koleoptero on 2010-02-28
I suggest backing up everything and kill everything in the drive and create the partition table from the beginning.

---

### Post by nerdopolis on 2010-02-28
I would not recommend creating that partition. Its probably an error with your partition table or program you are using. I don't know what that would do to your partition table.
And the FAT32 file system cant see over 32gb anyway.

---

### Post by cent on 2010-02-28
Testdisk tells the following on the partition table

```

     Partition                  Start        End    Size in sectors
 1 P Linux                    0   1  1  3915 254 63   62910477
 2 * HPFS - NTFS           3916   0  1 19876 254 63  256413465
 3 E extended             19877   0  1 38912 254 63  305813340
 4 P Linux Swap           38157   1  1 38912 254 63   12145077
Space conflict between the following two partitions
 3 E extended             19877   0  1 38912 254 63  305813340
 4 P Linux Swap           38157   1  1 38912 254 63   12145077
   X extended             19877   0  2 38156 254 63  293668199
 5 L Linux                19877   2  1 38156 254 63  293668074

```

and this is the real layout of the disk:
```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1  3915 254 63   62910477
P HPFS - NTFS           3916   0  1 19876 254 63  256413465
L Linux                19877   2  1 38156 254 63  293668074
L Linux Swap           38157   1  1 38912 254 63   12145077

```

Its weird how this conflict works just fine

---

### Post by gjoellee on 2010-02-28
> **cent said:**
> Apparently there is a rift in the bit continuum inside my hard drive: 
[ATTACH]148535[/ATTACH]
what happens if I press create? will it create a FAT file system with the size of 18446744067491 MB?

May I get your hard disk? :P

Take a look at launchpad.net for similar bugs, or make a new bug report.

---

### Post by cent on 2010-02-28
The problem occurs because Palimpset Disk Utility does not expect a currupted partition table. Which i apparantly have. I have written the correct MBR to the disk and I`ll se whether that fixes the problem

The SMART-data seams all fine except for one: Hardware ECC Recovered (Number of ECC on-the-fly errors) increased about 1,8 million times when I ran the short self-test and it's continuing to increase at about 10000/min

EDIT: according to wikipedia this might not mean anything at all

---

