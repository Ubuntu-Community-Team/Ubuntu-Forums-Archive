---
title: "USB Raid 1 device names changing..."
date: 2006-09-15
forum: Server Platforms
---

### Post by jedu on 2006-09-15
Hi

After experimenting poor reliability of hard disk effects, I have been trying to add a RAID1 setup to my silent EPIA based server with two IDE to USB 2.0 boxes with identical IDE disks inside. . I followed advices around there and everything seemed to work fine: array was reconstructing and it finally get synced. Later I tried it and began copying files to the mounted partition. I decided to see how good and glamorous was RAID and switched off and on one of the disks... To my surprise, when the drive was switched again on, it was detected again and assigned a new device name (originally sda and sdb, now sdb and sdc)... Logically the array didn't synced.

All this with ubuntu dapper fully updated.

I began reading and I thought the solution was tweeking udev to create symbolink links to whichever the sd name was.

This is the 10-local.rules I finally put in /etc/udev

BUS=="usb", KERNEL=="sd*", SYSFS{serial}=="DEF10A7350A2", NAME="%k", SYMLINK+="raid11%n"
BUS=="usb", KERNEL=="sd*", SYSFS(serial)=="DEF10A84811F", NAME="%k", SYMLINK+="raid12%n"

It created succsefully a /dev/raid11, /dev/raid111, /dev/raid12 and /dev/raid121

Which apperars as 

lrwxrwxrwx 1 root root     3 Sep 16 00:19 /dev/raid11 -> sdb
lrwxrwxrwx 1 root root     4 Sep 16 00:19 /dev/raid111 -> sdb1
lrwxrwxrwx 1 root root     3 Sep 16 00:19 /dev/raid12 -> sda
lrwxrwxrwx 1 root root     4 Sep 16 00:19 /dev/raid121 -> sda1


I even sucessfully created an array using partitions /dev/raid111, and /dev/raid121

this is the mdadm.conf I am using:

DEVICE /dev/raid111 /dev/raid121
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=1369e13f:eb4fa45c:6d4b9c2a:8196aa1b

The problem is that raid software doesn't take in count those names and uses the low level name. Here is what you get when you shutdown and switch on one of the disks...

edu@kabia2:~$ cat /proc/mdstat 
Personalities : [raid1] 
md0 : active raid1 sda1[2](F) sdb1[0]
      293033536 blocks [2/1] [U_]

An this the way the links are now...

lrwxrwxrwx 1 root root     3 Sep 16 00:19 /dev/raid11 -> sdb
lrwxrwxrwx 1 root root     4 Sep 16 00:19 /dev/raid111 -> sdb1
lrwxrwxrwx 1 root root     3 Sep 16 00:46 /dev/raid12 -> sdd
lrwxrwxrwx 1 root root     4 Sep 16 00:46 /dev/raid121 -> sdd1

Any ideas?

Thak you,

Eduardo

---

