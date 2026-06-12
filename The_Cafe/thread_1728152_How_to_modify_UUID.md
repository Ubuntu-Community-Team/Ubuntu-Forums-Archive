---
title: "How to modify UUID"
date: 2011-04-13
forum: The Cafe
---

### Post by kiyop on 2011-04-13
You can modify UUID of partition as you like.

The UUID is written in the following place.

"EXT2, EXT3, EXT4"
16 bytes starting at 0x468=4*16^2+6*16+8=1128 bytes

"LINUX SWAP"
16 bytes starting at 0x40c bytes

"FAT16"
4 bytes starting at 0x27 (Little Endian)

"FAT32"
4 bytes starting at 0x43 (Little Endian)

"NTFS"
8 bytes starting at 0x48 (Little Endian)

"REISERFS"
16 bytes starting at 0x10054

"BTRFS"
(main)
16 bytes starting at 0x10020
(sub)
16 bytes starting at 0x1010b

===============
You can edit UUID of EXT3 partition (/dev/sda1) by the following method.

~$ sudo dd if=/dev/sda1 bs=1 count=16 skip=1128 > test
~$ hexedit test
Edit UUID as you like and save by pressing CTRL+X.
~$ sudo dd if=test bs=1 count=16 seek=1128 of=/dev/sda1

You must be wise enough to modify /etc/fstab and /etc/initramfs-tools/conf.d/resume et al. to boot correctly, if you changed the UUID of / partition and so on of Ubuntu.

EDIT at 2011/4/28 0:28 in JAPAN:[COLOR=red]
Windows may have information on UUID of partitions in registry.
[http://ubuntuforums.org/showthread.php?t=480226&page=2](http://ubuntuforums.org/showthread.php?t=480226&page=2)

So it may be dangerous to change UUID of partition Windows uses.[/COLOR]

---

### Post by kiyop on 2011-04-20
I wrote a script for changing UUID of a partition as you like.

It works on my ubuntu 10.10-desktop-jp.

Currently, it can deal only ext2,ext3,ext4,ntfs,reiserfs,fat16,fat32 and swap partition.

```
#!/bin/bash
echo "==============================================="
echo "UUID manipulater by Kiyoshi SUZUKI at 2011/4/20"
echo "==============================================="
gksu sleep 0
sudo blkid
echo "==============================================="
echo "Type the partition device file name the UUID of which you want to modify (for example, sda1)"
read a
if [ ! -e /dev/$a ];then
 echo "/dev/$a does not exist. Abort!"
 exit 0
fi
filesystem=$(sudo blkid /dev/$a|sed -e "s/.*TYPE=\"//" -e "s/\".*//")
echo "filesystem of /dev/$a is $filesystem"
littleendian () {
 if [ $(expr $(echo $check1|wc -c) % 2) = 0 ];then
  echo "number of word \"$check1\" is odd. Abort."
  exit 0
 else
  repeatnum=$(expr $(expr $(echo $check1|wc -c) - 1) / 2 - 1)
  len=$(expr $(echo $check1|wc -c) - 1)
  while [ 0 -lt $repeatnum ];do
   check1="$(echo $check1|cut -c3-$(expr $(expr $repeatnum \* 2) + 2))$(echo $check1|cut -c1-2)$(if [ $(expr $(expr $repeatnum + 1) \* 2) -lt $len ];then echo $check1|cut -c$(expr $(expr $repeatnum \* 2) + 3)-;fi)"
   repeatnum=$(expr $repeatnum - 1)
  done
 fi
}
modify () {
 sudo dd if=/dev/$a bs=1 count=$num skip=$skip > test 2>/dev/null
 check1=$(hd test |head -n 1| sed -e "s/|.*//"|cut -c 9-|tr -d " ")
 if [ $littleendian = "on" ];then littleendian;fi
 check2=$(sudo blkid /dev/$a|tr -d "-"|sed -e "s/.*UUID=\"//" -e "s/\".*//")
 echo $check1 : $check2 :
 if [ $check1 = $(echo $check2|tr "[A-Z]" "[a-z]") ];then
  echo "UUID is $check2"
  echo "Please type what UUID you want to change to"
  read newuuid
  newuuid=$(echo "${newuuid}00000000000000000000000000000000"|cut -b1-$(expr $num + $num))
  if [ $(echo $newuuid|tr -d "0123456789abcdef") ];then
   echo "==============================================="
   echo "UUID must consist of \"0123456789abcdef\" only. Abort."
   echo "==============================================="
   exit 0
  fi
  echo "==============================================="
  echo "Do you want to change UUID of /dev/$a to ${newuuid} ? (Yes:y or No:other)"
  read b
  if [ $b = "y" ];then
   if [ $littleendian = "on" ];then
    check1=$newuuid
    littleendian
    newuuid=$check1
   fi
   echo "${newuuid}y"|hexedit test 2>/dev/null
   check1=$(hd test|head -n 1| sed -e "s/|.*//"|cut -c 9-|tr -d " ")
   if [ $littleendian = "on" ];then littleendian;fi
   echo "==============================================="
   echo "Please confirm new UUID of /dev/$a is:"
   echo $check1
   echo "Is it OK? (Yes:y, No:other)"
   read ans
   if [ $ans = "y" ];then
    sudo dd if=test bs=1 count=$num of=/dev/$a seek=$skip 2>/dev/null && echo "UUID is modified. \"blkid\" command gives:
$(sudo blkid /dev/$a)
You should manually update (modify) system settings such as /etc/fstab, /boot/grub/grub.cfg, /etc/initramfs-tools/conf.d/resume and so on."
    sudo sync
    exit 0
   else
    echo "If you want to change, type \"y\". Abort."
    exit 0
   fi
  else
   echo "If you want to change, type \"y\". Abort."
   exit 0
  fi
 else
  echo "Something is wrong. Abort!"
  exit 0
 fi
}
case $filesystem in
 ext2|ext3|ext4)
  echo "Please type what UUID you want to change to"
  read newuuid
  newuuid=$(echo $newuuid|tr "[A-Z]" "[a-z]"|tr -d -- -)
  newuuid=$(echo "${newuuid}00000000000000000000000000000000"|cut -b1-32)
  if [ $(echo $newuuid|tr -d "0123456789abcdef") ];then
   echo "==============================================="
   echo "UUID must consist of \"0123456789abcdef\" only. Abort."
   echo "==============================================="
   exit 0
  fi
  echo "==============================================="
  echo "Do you want to change UUID of /dev/$a to ${newuuid} ? (Yes:y or No:other)"
  read b
  if [ $b = "y" ];then
   sudo tune2fs -U "$(echo $newuuid|cut -c1-8)-$(echo $newuuid|cut -c9-12)-$(echo $newuuid|cut -c13-16)-$(echo $newuuid|cut -c17-20)-$(echo $newuuid|cut -c21-32)" /dev/$a && echo "UUID is modified. \"blkid\" command gives:
$(sudo blkid /dev/$a)
You should manually update (modify) system settings such as /etc/fstab, /boot/grub/grub.cfg, /etc/initramfs-tools/conf.d/resume and so on."
   sudo sync
   exit 0
  else
   echo "If you want to change, type \"y\". Abort."
   exit 0
  fi
 ;;
 swap)
  num=16
  skip=1036
  littleendian="off"
  modify
 ;;
 ntfs)
  num=8
  skip=72
  littleendian="on"
  modify
 ;;
 reiserfs)
  num=16
  skip=65620
  littleendian="off"
  modify
 ;;
 btrfs)
  num=16
  skip=65568
  littleendian="off"
  modify
 ;;
 vfat)
  if [ -n "$(sudo blkid /dev/$a|grep msdos)" ];then
   num=4
   skip=39
   littleendian="on"
   modify
  else
   num=4
   skip=67
   littleendian="on"
   modify
  fi
 ;;
 *)
  echo "Filesystem type $filesystem is not supported. Abort."
  exit 0
 ;;
esac
exit 0

```
save it as "UUIDmanipulater.sh".
And execute in terminal, for example,
[COLOR=#0000FF]bash UUIDmanipulater.sh[/COLOR]

* Known problems *

UUID of swap partition did not changed by this script sometimes.

---

### Post by Artemis3 on 2011-04-20
Great, So now you can now label your stuff...

deadbeef-cafe-babe-feed-defacefacade or something ;)

---

### Post by kiyop on 2011-04-21
Yes!:guitar:

We can use:

face
babe
bad
dad
ace
aced
cab 
cafe 
baba 
aba
abaca
abbe
abd
abed
baa
bade
fade
ba11
ab1e-b0d1ed;)

et al.

I want to make a sentence.:P

By the way, 
I want to include some function to search former UUID value in /etc/fstab and/or /boot/grub/grub.cfg or /boot/grub/menu.lst and/or /etc/initramfs-tools/conf.d/resume, 
and to help changing them into my script.

***
The reason I tried to change UUID is that I sometimes need to type kernel option such as "root=UUID=..." and it is difficult to remember and type UUID value correctly.
I changed UUID of partitions like,
100000000000...
1234567890abcdef...

Of course, now I know that I can write like "root=LABEL=...", which is easier for me to remember. I can modify label of partition easily.

---

### Post by kiyop on 2011-04-25
I added the function to search old UUID value from /etc/fstab, /boot/grub/grub.cfg, /boot/grub/menu.lst, and /etc/initramfs-tools/conf.d/resume and give chance to change the old UUID value to the new one.

Edit: I fixed a bug at 2011/4/26 12:06 in Japan

The script is as follows:
```
#!/bin/bash
echo "==============================================="
echo "UUID manipulater by Kiyoshi SUZUKI at 2011/4/25"
echo "==============================================="
gksu sleep 0
sudo blkid
echo "==============================================="
echo "Type the partition device file name the UUID of which you want to modify (for example, sda1)"
read a
if [ ! -e /dev/$a ];then
 echo "/dev/$a does not exist. Abort!"
 exit 0
fi
filesystem=$(sudo blkid /dev/$a|sed -e "s/.*TYPE=\"//" -e "s/\".*//")
echo "filesystem of /dev/$a is $filesystem"
littleendian () {
 if [ $(expr $(echo $check1|wc -c) % 2) = 0 ];then
  echo "number of word \"$check1\" is odd. Abort."
  exit 0
 else
  repeatnum=$(expr $(expr $(echo $check1|wc -c) - 1) / 2 - 1)
  len=$(expr $(echo $check1|wc -c) - 1)
  while [ 0 -lt $repeatnum ];do
   check1="$(echo $check1|cut -c3-$(expr $(expr $repeatnum \* 2) + 2))$(echo $check1|cut -c1-2)$(if [ $(expr $(expr $repeatnum + 1) \* 2) -lt $len ];then echo $check1|cut -c$(expr $(expr $repeatnum \* 2) + 3)-;fi)"
   repeatnum=$(expr $repeatnum - 1)
  done
 fi
}
modify () {
 sudo dd if=/dev/$a bs=1 count=$num skip=$skip > test 2>/dev/null
 check1=$(hd test |head -n 1| sed -e "s/|.*//"|cut -c 9-|tr -d " ")
 if [ $littleendian = "on" ];then littleendian;fi
 check2=$(sudo blkid /dev/$a|tr -d "-"|sed -e "s/.*UUID=\"//" -e "s/\".*//")
 if [ $check1 = $(echo $check2|tr "[A-Z]" "[a-z]") ];then
  olduuid=$(sudo blkid /dev/$a|sed -e "s/.*UUID=\"//" -e "s/\".*//")
  echo "UUID is $olduuid"
  echo "Please type what UUID you want to change to"
  read newuuid
  newuuid=$(echo "${newuuid}00000000000000000000000000000000"|cut -b1-$(expr $num + $num))
  if [ $(echo $newuuid|tr -d "0123456789abcdef") ];then
   echo "==============================================="
   echo "UUID must consist of \"0123456789abcdef\" only. Abort."
   echo "==============================================="
   exit 0
  fi
  echo "==============================================="
  echo "Do you want to change UUID of /dev/$a to ${newuuid} ? (Yes:y or No:other)"
  read b
  if [ $b = "y" ];then
   check1=$newuuid
   if [ $littleendian = "on" ];then
    littleendian
   fi
   echo "${check1}y"|hexedit test 2>/dev/null
   check1=$(hd test|head -n 1| sed -e "s/|.*//"|cut -c 9-|tr -d " ")
   if [ $littleendian = "on" ];then littleendian;fi
   echo "==============================================="
   echo "Please confirm new UUID of /dev/$a is:"
   echo $check1
   echo "Is it OK? (Yes:y, No:other)"
   read ans
   if [ $ans = "y" ];then
    sudo dd if=test bs=1 count=$num of=/dev/$a seek=$skip 2>/dev/null && echo "UUID is modified. \"blkid\" command gives:
$(sudo blkid /dev/$a)
You should manually update (modify) system settings such as /etc/fstab, /boot/grub/grub.cfg, /etc/initramfs-tools/conf.d/resume and so on.
I will check /etc/fstab, /boot/grub/grub.cfg, /etc/initramfs-tools/conf.d/resume for $olduuid."
    sudo sync
    newuuid=$(echo $check1|cut -c1-$(echo $cutspace|cut -d " " -f1))
    loc1=$(echo $cutspace|cut -d " " -f1)
    cutspace=$(echo "$cutspace"|cut -d " " -f2-)
    for loc2 in $cutspace;do
     newuuid=$newuuid$(echo -$(echo $check1|cut -c$(expr $loc1 + 1)-$loc2))
     loc1=$loc2
    done
    changefstabetal
   else
    echo "If you want to change, type \"y\". Abort."
    exit 0
   fi
  else
   echo "If you want to change, type \"y\". Abort."
   exit 0
  fi
 else
  echo "Something is wrong. Abort!"
  exit 0
 fi
}
modifyfile () { 
 if [ -e /mnt$file ];then
  if [ "$(grep $olduuid /mnt/$file|grep -v ^#)" ];then
   for line in $(grep -n $olduuid /mnt$file|grep -v ^[0-9]*:#|tr " " "_");do
    answer="1"
    while :;do
     echo "There is the following line in $file in /dev/$aa:"
     echo $(echo $line|sed -e "s/^[0-9]*:/& lines:/")
     echo "Do you change \"$olduuid\" to \"$newuuid\" ?(yes=y,no=n)"
     read answer
     if [ "$answer" = "y" ];then
      perm=$(ls -l /mnt$file|cut -c2-10)
      perm2=$(expr 0 $(echo $perm|cut -c1-3|sed -e "s/r/ + 4/" -e "s/w/ + 2/" -e "s/x/ + 1/" -e "s/-//g"))$(expr 0 $(echo $perm|cut -c4-6|sed -e "s/r/ + 4/" -e "s/w/ + 2/" -e "s/x/ + 1/" -e "s/-//g"))$(expr 0 $(echo $perm|cut -c7-9|sed -e "s/r/ + 4/" -e "s/w/ + 2/" -e "s/x/ + 1/" -e "s/-//g"))
      sudo mv -f /mnt$file /mnt${file}.backup
      sudo touch /mnt$file
      sudo chmod a+w /mnt$file
      cat /mnt${file}.backup|sed "$(echo $line|cut -d: -f1)s/$olduuid/$newuuid/" > /mnt$file
      sudo chmod $perm2 /mnt$file
      break
     elif [ "$answer" = "n" ];then break
     fi     
    done
   done
  fi
 fi
}
changefstabetal () {
 deviceslist=$(sudo blkid|cut -d: -f1)
 for aa in $deviceslist;do
  sudo umount -l /mnt 2>/dev/null
  sudo mount -t $(sudo blkid $aa|sed -e "s/.*TYPE=\"//"|sed -e "s/\".*//") $aa /mnt 2>/dev/null || continue
  echo "checking $aa"
  file="/etc/fstab"
  modifyfile
  file="/boot/grub/grub.cfg"
  modifyfile
  file="/boot/grub/menu.lst"
  modifyfile
  file="/etc/initramfs-tools/conf.d/resume"
  modifyfile
  umount -l /mnt 2>/dev/null
 done
}
case $filesystem in
 ext2|ext3|ext4)
  olduuid=$(sudo blkid /dev/$a|sed -e "s/.*UUID=\"//" -e "s/\".*//")
  echo "UUID is $olduuid"
  echo "Please type what UUID you want to change to"
  read newuuid
  newuuid=$(echo $newuuid|tr "[A-Z]" "[a-z]"|tr -d -- -)
  newuuid=$(echo "${newuuid}00000000000000000000000000000000"|cut -b1-32)
  if [ $(echo $newuuid|tr -d "0123456789abcdef") ];then
   echo "==============================================="
   echo "UUID must consist of \"0123456789abcdef\" only. Abort."
   echo "==============================================="
   exit 0
  fi
  newuuid="$(echo $newuuid|cut -c1-8)-$(echo $newuuid|cut -c9-12)-$(echo $newuuid|cut -c13-16)-$(echo $newuuid|cut -c17-20)-$(echo $newuuid|cut -c21-32)"
  echo "==============================================="
  echo "Do you want to change UUID of /dev/$a to ${newuuid} ? (Yes:y or No:other)"
  read b
  if [ $b = "y" ];then
   sudo tune2fs -U $newuuid /dev/$a && echo "UUID is modified. \"blkid\" command gives:
$(sudo blkid /dev/$a)
You should manually update (modify) system settings such as /etc/fstab, /boot/grub/grub.cfg, /etc/initramfs-tools/conf.d/resume and so on.
I will check /etc/fstab, /boot/grub/grub.cfg, /etc/initramfs-tools/conf.d/resume."
   sudo sync
   changefstabetal
   exit 0
  else
   echo "If you want to change, type \"y\". Abort."
   exit 0
  fi
 ;;
 swap)
  num=16
  skip=1036
  littleendian="off"
  cutspace="8 12 16 20 32"
  modify
 ;;
 ntfs)
  num=8
  skip=72
  littleendian="on"
  cutspace="16 "
  modify
 ;;
 reiserfs)
  num=16
  skip=65620
  littleendian="off"
  cutspace="8 12 16 20 32"
  modify
 ;;
 btrfs)
  num=16
  skip=65568
  littleendian="off"
  cutspace="8 12 16 20 32"
  modify
 ;;
 vfat)
  littleendian="on"
  cutspace="4 8"
  if [ -n "$(sudo blkid /dev/$a|grep msdos)" ];then
   num=4
   skip=39
  else
   num=4
   skip=67
  fi
  modify
 ;;
 *)
  echo "Filesystem type $filesystem is not supported. Abort."
  exit 0
 ;;
esac
exit 0
```

---

### Post by kiyop on 2011-04-25
Sometimes, the odd word "" which means CTRL+x is eliminated after submission.
```
echo "${check1}y"|hexedit test 2>/dev/null
```Edit at 2011/4/26 12:11 in Japan:
 I cannot correctly submit "" which means CTRL+x in this forum.
 I submitted the correct script at
[http://kiyoandkei.blog68.fc2.com/blog-entry-51.html](http://kiyoandkei.blog68.fc2.com/blog-entry-51.html)

EDIT at 2011/4/28 0:35 in JAPAN
A recent one is
[http://blog-imgs-17.fc2.com/k/i/y/kiyoandkei/UUIDmanipulater110427no1.txt]("http://blog-imgs-17.fc2.com/k/i/y/kiyoandkei/UUIDmanipulater110426no1.txt")

---

### Post by kiyop on 2011-04-27
I am not sure, but Windows may have information on UUID of partitions in registry.
[http://ubuntuforums.org/showthread.php?t=480226&page=2](http://ubuntuforums.org/showthread.php?t=480226&page=2)

So it may be dangerous to change UUID of partition Windows uses.

I will write this in #1

---

