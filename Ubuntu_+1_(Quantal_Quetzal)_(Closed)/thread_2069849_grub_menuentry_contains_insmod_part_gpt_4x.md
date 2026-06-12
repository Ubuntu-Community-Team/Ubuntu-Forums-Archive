---
title: "grub menuentry contains insmod part_gpt 4x"
date: 2012-10-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by masuch on 2012-10-11
Hi,

After 12.04 to 12.10 upgrade I have noticed that grub menuetry contains 
> 	insmod gzio
	insmod part_gpt
	insmod part_gpt
	insmod part_gpt
	insmod part_gpt
	insmod diskfilter
	insmod mdraid1x
	insmod ext2
Is there any good reason to have 4 times "insmod part_gpt" in menuentry ?

thank you, 
kind regards,
Martin

---

### Post by dino99 on 2012-10-11
be sure to fully purge 1.99, because 2.0 is way different

---

### Post by masuch on 2012-10-11
> **dino99 said:**
> be sure to fully purge 1.99, because 2.0 is way different

So, is it safe to manually remove it - should I report it as a bug ?

(( I am not using generated grub.cfg to boot up my OS instances - I am maintaining my own menuentries in 40_custom - I have my reasons for it ))

---

### Post by grahammechanical on 2012-10-11
From this:

[http://www.gnu.org/software/grub/manual/]("http://www.gnu.org/software/grub/manual/")

I found this:

> Some newer systems use the GUID Partition Table (GPT) format.

I also saw that insmod means insert module. Do you need the module for dealing with a GUID partition table inserted four times?

It is your system. The set up might be very specific to you. Is this your main install? You are now a tester.

Regards.

---

### Post by masuch on 2012-10-11
> **grahammechanical said:**
> From this:

[http://www.gnu.org/software/grub/manual/]("http://www.gnu.org/software/grub/manual/")

I found this:



I also saw that insmod means insert module. Do you need the module for dealing with a GUID partition table inserted four times?

It is your system. The set up might be very specific to you. Is this your main install? You are now a tester.

Regards.

insmod part_gpt is necessary to be there (yes , i am using gpt). I am just surprised it is 4 times. It should be there just once. Just looking for confirmation If I can have only "one line with insmod part_gpt".

---

### Post by masuch on 2012-10-13
Thank you all for help. 
It is a bug - have been reported on launchpad.

---

