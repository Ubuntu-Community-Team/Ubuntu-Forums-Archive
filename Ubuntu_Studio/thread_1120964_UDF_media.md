---
title: "UDF media"
date: 2009-04-09
forum: Ubuntu Studio
---

### Post by inobe on 2009-04-09
i have a few UDF mini dvd's, i remember being able to view the media, that was last year and the os was opensuse.


the media mounts in ubuntu 8.10 but the contents of the disc is empty.

i forget the model of the sony dv cam, it's been in the trash for a few years.

thanks :)

---

### Post by inobe on 2009-04-09
let me add that i found a udf disk with some backup data and i can read and write to it' so it appears to be some codec encryption problem specific to the sony cam.

thanks for any suggestions :)

---

### Post by Matoridi on 2009-05-18
I had a similar problem with a UDF cd burned in Windows.

I went to the terminal and cd'd to the media directory, then displayed all the contents with their owners/permissions :

[INDENT]matoridi@Mekky:/media$ ls -la
total 46
drwxr-xr-x  9 root       root        4096 2009-05-18 00:21 .
drwxr-xr-x 22 root       root        4096 2009-03-02 11:42 ..
lrwxrwxrwx  1 root       root           6 2008-10-31 17:05 cdrom -> cdrom0
dr--r--r--  4 4294967295 4294967295   180 2006-06-20 17:35 cdrom0
[/INDENT]

I realized my problem was that the group/owner of this cd were not standard (in my case a string of numbers, 4294967295).  So my normal user id could not access the contents of the drive.

I logged as super-user (su) and then could cd to the cdrom and access the content. 

[INDENT]matoridi@Mekky:/media$ su
Password:
root@Mekky:/media# cd cdrom
root@Mekky:/media/cdrom# ls
** snip snip content of directory ** 
[/INDENT]


I started nautilus from there to have a more friendly file manager....


Hope this helps.
:p

---

