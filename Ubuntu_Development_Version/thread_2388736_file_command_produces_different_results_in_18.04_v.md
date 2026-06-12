---
title: "file command produces different results in 18.04 vs 16.04"
date: 2018-04-06
forum: Ubuntu Development Version
---

### Post by &amp;KyT$0P# on 2018-04-06
Just downloaded the new Xubuntu 18.04 beta 2 ISO, and was going to customise it, but my LiveCD customisation script complained that it's not a valid CD image.

Turns out it's because of the result of the first command here -
```
$ file -b --mime-type xubuntu-18.04-beta2-desktop-amd64.iso
application/octet-stream

$ file xubuntu-18.04-beta2-desktop-amd64.iso
xubuntu-18.04-beta2-desktop-amd64.iso: DOS/MBR boot sector; partition 2 : ID=0xef, start-CHS (0x3ff,254,63), end-CHS (0x3ff,254,63), startsector 2716460, 4672 sectors

```

In 16.04 with the **same file**, I get this -
```
$ file -b --mime-type xubuntu-18.04-beta2-desktop-amd64.iso
application/x-iso9660-image

$ file xubuntu-18.04-beta2-desktop-amd64.iso
xubuntu-18.04-beta2-desktop-amd64.iso: DOS/MBR boot sector ISO 9660 CD-ROM filesystem data (DOS/MBR boot sector) 'Xubuntu 18.04 LTS amd64' (bootable); partition 2 : ID=0xef, start-CHS (0x3ff,254,63), end-CHS (0x3ff,254,63), startsector 2716460, 4672 sectors
```

Why the difference?

---

### Post by dino99 on 2018-04-06
a think you get the usual output: an alpha/beta image is not a final image (not yet released, so no trusted)

---

### Post by &amp;KyT$0P# on 2018-04-06
> **dino99 said:**
> a think you get the usual output: an alpha/beta image is not a final image (not yet released, so no trusted)
But I get the same discrepancy with the official Xubuntu 16.04 release ISO.

---

### Post by dino99 on 2018-04-06
Possible explication: [https://askubuntu.com/questions/806411/file-types-in-xubuntu-16-04](https://askubuntu.com/questions/806411/file-types-in-xubuntu-16-04)

---

### Post by &amp;KyT$0P# on 2018-04-06
> **dino99 said:**
> Possible explication: 
Nope.  That is unrelated to the behavior of the [FONT=Courier New]file[/FONT] command.

---

### Post by zika on 2018-04-06
In 18.04 do:```
apt changelog file
```

---

### Post by &amp;KyT$0P# on 2018-04-06
Thanks zika, that looks useful - it downloads and displays [http://changelogs.ubuntu.com/changelogs/pool/main/f/file/file_5.32-2/changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/f/file/file_5.32-2/changelog").
(For comparison, 16.04 has [FONT=Courier New]file[/FONT] version 5.25-2ubuntu1.)

What are we looking for in there?

---

### Post by &amp;KyT$0P# on 2018-04-13
As a test, I tried building the 16.04's version of [FONT=Courier New]file[/FONT] on 18.04.  The result works same as in 16.04.

I'm thinking the change in behavior is a bug.

Edit: Filed [https://bugs.launchpad.net/ubuntu/+source/file/+bug/1763570]("https://bugs.launchpad.net/ubuntu/+source/file/+bug/1763570")

---

### Post by flocculant on 2018-04-13
> **halogen2 said:**
> As a test, I tried building the 16.04's version of [FONT=Courier New]file[/FONT] on 18.04.  The result works same as in 16.04.

I'm thinking the change in behavior is a bug.

Edit: Filed [https://bugs.launchpad.net/ubuntu/+source/file/+bug/1763570]("https://bugs.launchpad.net/ubuntu/+source/file/+bug/1763570")

Have you tested this with ubuntu itself?

Edit : if something is likely to not be 'Xubuntu' eg not Xfce then I try to test it with Ubuntu as well - less chance of them blaming us then :) Also - if it is in fact a regression - you can tag bugs as such.

---

### Post by &amp;KyT$0P# on 2018-04-13
> **flocculant said:**
> Have you tested this with ubuntu itself?
No I only have Xubuntu set up at the moment.

---

### Post by flocculant on 2018-04-13
> **halogen2 said:**
> No I only have Xubuntu set up at the moment.

I'll try to get to it later today.

---

### Post by flocculant on 2018-04-13
From the current Ubuntu iso
```

root@ubuntu:~# cd /media/ubuntu/Data/iso/Xubuntu/18.04/
root@ubuntu:/media/ubuntu/Data/iso/Xubuntu/18.04# file bionic-desktop-amd64.iso bionic-desktop-amd64.iso: DOS/MBR boot sector; partition 2 : ID=0xef, start-CHS (0x3ff,254,63), end-CHS (0x3ff,254,63), startsector 2712108, 4672 sectors
root@ubuntu:/media/ubuntu/Data/iso/Xubuntu/18.04# file -b --mime-type bionic-desktop-amd64.iso 
application/octet-stream
root@ubuntu:/media/ubuntu/Data/iso/Xubuntu/18.04# 

```

Didn't anticipate it being different - but good to be sure.

---

### Post by &amp;KyT$0P# on 2018-04-13
Thanks flocculant for your help with this! :KS

> **flocculant said:**
> if it is in fact a regression - you can tag bugs as such.
There are three different regression tags, which one should I use for this?
```
regression-proposed
regression-release
regression-update
```

---

### Post by flocculant on 2018-04-13
> **halogen2 said:**
> Thanks flocculant for your help with this! :KS


There are three different regression tags, which one should I use for this?
```
regression-proposed
regression-release
regression-update
```

Definitely not -proposed as it's not in there.

As far as the other 2 go - your guess would be as good as mine.

I'd probably go for -release as it's been released, on the other hand it's a regression caused by an update ...

If it's wrong - someone will change it I assume.

---

