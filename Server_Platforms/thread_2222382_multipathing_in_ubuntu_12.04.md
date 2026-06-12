---
title: "multipathing in ubuntu 12.04"
date: 2014-05-06
forum: Server Platforms
---

### Post by jean-francois-datta on 2014-05-06
hi
I tried to configure multipathing in ubuntu 12.04.
When I add new luns on the server, I show it with the multipath OK, but if I boot the server, I lost the multipath ( with dmsetup ls --tree, I see only one path for the logical volume ). I haven't this problem in UBUNTu 10.04.
are there any change in the configuration of multipathing between ubuntu 10.04 and ubuntu 12.04. 
Thank you in advance for your help.

---

### Post by Gyokuro on 2014-05-06
Hi

Have you already checked this: [https://help.ubuntu.com/12.04/serverguide/device-mapper-multipathing.html](https://help.ubuntu.com/12.04/serverguide/device-mapper-multipathing.html)

- HTH

---

### Post by jean-francois-datta on 2014-05-12
I have seen this link.
I think that my problem is not in the multipath config but in the link between multipathing and the lvm layer.

I explain you my problem.

I create a lun on the server and I put il on a vg
I create a lv and a file system on it

At this moment, when I look on the server, I see a mounted file system which used multipath.

#dmsetup ls –tree
vg00-swap_1 (254:12)
ââ (8:101)
vg01-lv_mysql (254:3)
ââmpath7 (254:0)
ââ (8:0)
ââ (8:48)


If if try to access to the file system, I see with iostat command that the two path work

I reboot the server.

The file system goes up and I find my data on it.

When I'm looking on multipathing, 
I see 

ââmpath7 (254:0)
ââ (8:0)
ââ (8:48)
vg01-lv_mysql (254:3)
ââ (8:0)

When I look on the iostat result, I see that all the I/O go on one path. If I put this path down, I loose the access on the lv.

If I export/import the volume group, the multipathing returns ok.

---

### Post by jean-francois-datta on 2014-05-13
I have found the solution to my problem. I had to modify le line "filter" in the lvm.conf file.
I have put this :
filter = [ "r|/dev/cdrom|", "a|/dev/sda|", "r|/dev/sd.*|", "a|/dev/mapper/mpath.*|" ]

and now the multipath stays ok even if I boot the server.

Thanks for the help

---

