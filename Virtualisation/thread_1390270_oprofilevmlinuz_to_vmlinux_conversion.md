---
title: "oprofile:vmlinuz to vmlinux conversion"
date: 2010-01-25
forum: Virtualisation
---

### Post by sirajrathore on 2010-01-25
Hi
 
I am using Ubuntu distribution 8.04. I installed Openvz kernel 2.6.18-14-ovz-amd64-smp.Now i want to use oprofile on my system.For Oprofile with kernel debugging it is compulsory to have uncompressed (vmlinux-2.6.18-14-ovz-amd64-smp) file in /boot. Where as vmlinuz-2.6.18-14-ovz-amd64-smp file exists in boot directory which should be decompressed.I am using the following command to decompress it but error occurs
 
$Gzip -d </boot/vmlinuz-2.6.18-14-ovz-amd64-smp> /tmp/vmlinux-2.6.18-14-ovz-amd64-smp
 
 stdin:not in gzip format
 
other method for decompression is also described here
 
[http://www.codeguru.com/forum/showthread.php?t=415186](http://www.codeguru.com/forum/showthread.php?t=415186)
 
but it is not showing any output: (first command from above reference)
> Od-A d-t x1 vmlinuz | grep '1 f 8b 08 00 '
 
 
Any idea, any other way to get vmlinux from vmlinuz
 
 
Best Regards
Siraj

---

