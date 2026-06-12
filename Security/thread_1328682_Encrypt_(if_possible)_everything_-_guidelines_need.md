---
title: "Encrypt (if possible) everything - guidelines needed"
date: 2009-11-16
forum: Security
---

### Post by Mis_Puchatek on 2009-11-16
EDITED : 18.11.2009 

Problem solved. Everyone with problem similar to me should have a start point.
dm-crypt:
1)[http://news.softpedia.com/news/Encry...04-85271.shtml](http://news.softpedia.com/news/Encry...04-85271.shtml)
2)[http://kuparinen.org/martti/comp/ubu...cryptolvm.html](http://kuparinen.org/martti/comp/ubu...cryptolvm.html)
Luks:
1)[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)
True crypt:
1)[http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)


Original Post:

Hello everyone.

Maybe it should be in beginners forum, if yes, please move that topic there if possible.

I need some guidelines/opinions about my issue. 

I want to encrypt my disk. I have few partitions.
[I]/dev/sda1 - windows
/dev/sda2 - extended, 
|--/dev/sda4 - fat32 
|--/dev/sda5 - ext3
|--/linux-swap
/dev/sda3 - linux(/)[/I]

All is not encrypted. I would like to encrypt those disks.
However there are few solutions, and I do not have any experience with that subject.
There are at least those tools : luks, aes-loop, dm-crypt and true-crypt.

Maybe some of you has similar configuration(dualboot) and was able to encrypt data.

Which tool(s) are you using in such case?
Are you happy with that solution, or if you have another chance, you would perform it in different way?

One notice : It is not important for me to access windows disks from linux, or viceversa.
Second notice : if you are able to provide me some guides about linux only solution but without breaking possibility for login to windows, great.

Best regards
Mis Puchatek

---

### Post by scorp123 on 2009-11-16
> **Mis_Puchatek said:**
>  luks, aes-loop, dm-crypt and true-crypt.

If you really really want everything encrypted from beginning to end you'd have to wipe your disks and start from scratch with the "Alternate Install CD" which offers to configure "Encrypted LVM".

I could be wrong but only TrueCrypt offers compatibility with Windoze. All other mechanisms are pretty much Linux-specific.

These instructions here were written for Ubuntu 8.04 LTS ... but they should still be valid and just having completed an installation of Ubuntu 9.10 with customized full-disk encryption I am 100% that the screenshots still show the same stuff:

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

---

### Post by Mis_Puchatek on 2009-11-17
Yeah. I think I will use alternate-installer. LVM with dm-crypt on top of that.

I have found great guide for that, it should be possible to use it for dual-boot system.  (it is from E2007, but I guess it should be ok).
[http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html](http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html)

Thx a lot.

---

### Post by EJeanmaire on 2009-11-17
> **Mis_Puchatek said:**
> Yeah. I think I will use alternate-installer. LVM with dm-crypt on top of that.

I have found great guide for that, it should be possible to use it for dual-boot system.  (it is from E2007, but I guess it should be ok).
[http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html](http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html)

Thx a lot.

I may be wrong but I am pretty sure TrueCrypt is also Linux.  It is possible to use the same encryption keys for all of your OS partitions, as well as secondary disks/partitions you have; although it would require some googling to figure out how.

---

### Post by HermanAB on 2009-11-17
Here is something:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

Read the Perl wizard code for more details.

---

### Post by EJeanmaire on 2009-11-18
> **EJeanmaire said:**
> I may be wrong but I am pretty sure TrueCrypt is also Linux.  It is possible to use the same encryption keys for all of your OS partitions, as well as secondary disks/partitions you have; although it would require some googling to figure out how.

Here is a good overall how-to on TrueCrypt pulled from the sticky in this forum:
[http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)

---

### Post by Mis_Puchatek on 2009-11-18
> **EJeanmaire said:**
> Here is a good overall how-to on TrueCrypt pulled from the sticky in this forum:
[http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)

Yeah, I have read that. Thx for notice anyway.
As for true-crypt, I will try to use it later under windows+fat32storage[so it is out-of-topic here, in Linux world]. I hope that it will not alter boot_sequence/mbr of Ubuntu.

Thx everyone for help/opinions.

---

