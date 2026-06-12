---
title: "Ubuntu 12.04 + VirtualBox + Win7 32 bit = short time destroyed your harddisk. WHY???"
date: 2013-05-24
forum: Virtualisation
---

### Post by petyabest on 2013-05-24
Hi,

I Have a very big problem with the virtualization.

I'm using Ubuntu 12.04 (64 bit) on a dell laptop. I don't have other computers.
In my work I need to use Windows Mobile SDK ans Visual Basic, which only works with windows7 or Windows8.

I dont known why, but my VirtualBox 64 bit edition (what I has downloaded from the official site) does not support 64 bit OS-es, so I tried to setup Win7 32 bit.
(It might be caused by that my computer has 2 cores, virtually 4 cores.)

Everything was ok, Win7 was started up, but it makes very huge disc load to my phisical hard disk.

After the third or fourth startup the phisical disc has damadged. After that I couldn't started my computer anymore, my harddisk not worked anymore.
It can't found that by Linux Live CDs also.

There is a way to avoid my harddisk from Windows's huge disc load?
(For eg. when windows try to find updates and then installing thats.)

---

### Post by GhettoMrBob on 2013-05-27
I wouldn't go as far as to blame your HDD failure on the virtual machine. More than likely your drive failed as they do on occasion. The amount of read/writes to it shouldn't really have a substantial effect on it's lifetime (unless it's an SSD).

How old is your laptop (and by extension the HDD)? If it's getting long in the tooth I wouldn't be too surprised if it failed. I've had brand new HDD's fail right out of the box so it's really a toss up in terms of dependability.

---

