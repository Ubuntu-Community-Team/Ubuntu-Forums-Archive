---
title: "No init found. Try passing init= bootarg   (initramfs)"
date: 2013-11-27
forum: Server Platforms
---

### Post by khayamshah52 on 2013-11-27
hello dear 

its very much urgent 

i am new usser of ubuntu 
i install KOHA in ubuntu server

there is my very much important data in this system 
now when i boot system without CD 
 
it show this message

No init found. Try passing init= bootarg  
(initramfs)


from googling 

i also try below solutions 
but no result 
what can i do 
please me its urgent 


what i already try 

*************************************
jst sample content not orignal 

sudo fdisk -l


/dev/sda1 * 1 19076 153219072 83 Linux
/dev/sda2 19076 19458 3068929 5 Extended
/dev/sda5 19076 19458 3068928 82 Linux swap / Solaris

then i try 

sudo fsck /dev/sda1


fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

then i try this also

sudo umount /dev/sda1

umount: /dev/sda1: not mounted

sudo fsck /dev/sda1

fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?


now what can i do 

guide me with simple ans 
i cant bear to re install it 
please do something for it boot properly 

thankyou 

thanks & regards
khayam Shah

---

### Post by jeanjd63 on 2013-11-27
Hello 

If fou have à LiveCD version 10.10 this message is normal :

[COLOR=#000000]fsck from util-linux-ng 2.17.2[/COLOR]
[COLOR=#000000]e2fsck 1.41.12 (17-May-2010)[/COLOR]
[B][COLOR=#000000]fsck.ext4: Device or resource busy while trying to open /dev/sda1[/COLOR]
[/B][COLOR=#000000]**Filesystem mounted or opened exclusively by another program?**

[/COLOR]
You better download a [SystemRescueCd]("http://www.sysresccd.org/Download") to do an fsck

Bye

---

### Post by khayamshah52 on 2013-12-07
but after that i'll not able to normal boot........... ?????? plz reply ........

---

