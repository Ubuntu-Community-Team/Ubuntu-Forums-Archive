---
title: "Recovering data from an ecrypted image"
date: 2009-03-31
forum: Security
---

### Post by Paradoxfox93 on 2009-03-31
Using gddrescue I copied the contents of an ecrypted partition as an image to another hard drive as detailed here:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

It's aes-256 set up using dm-crypt from the alternate install cd but I'm a little confused about where to go from here as far as mounting, decrypting and recovering files now.

Anyone have any ideas?

---

### Post by Paradoxfox93 on 2009-03-31
alternatively it has just occured to me that the partition is exactly the same size (and key) after I've reinstalled the system.  It would work perfect I believe to just copy the image back into its old spot if I could do that...

Incidentally thi sis not the laptop in my signature but the HD in question actually is from it and I've just installed 8.10 although the image was from 8.04 it was the /home partition.

---

### Post by hyper_ch on 2009-03-31
what is the problem now?

---

### Post by Paradoxfox93 on 2009-03-31
how do i mount and decrypt the image so i can access my data?  I've never used dm crypt for any other than at install or boot up

---

### Post by hyper_ch on 2009-04-01
you need to load the crypto modules, then you need to open the container by creating a mapper and then you can mount the mapper into your filesystem somewhere,

Below I have the crypto modules for 64bit:

```

aes_x86_64             16384  9 
aes_generic            36392  1 aes_x86_64
dm_crypt               22792  1 
dm_mod                 72944  11 dm_crypt
crypto_blkcipher       27780  8 ecb,cbc,dm_crypt

```

and for creating a mapper have a look at "cryptsetup luksOpen"

---

