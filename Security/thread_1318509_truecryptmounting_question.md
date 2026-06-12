---
title: "truecrypt/mounting question"
date: 2009-11-07
forum: Security
---

### Post by nihilum on 2009-11-07
I was wondering... Is there any way you could mount a truecrypt volume (or any volume for that matter) over an existing mounted filesystem? For example, suppose I have /mnt/disk1/folder1/file1 and a truecrypt volume that contains folder1/file2, and the end result would be file1 and file2 in the same folder? Haha I hope that makes sense

---

### Post by bodhi.zazen on 2009-11-07
Not that I know of.

---

### Post by niteshifter on 2009-11-08
Hi,

unionfs will do this but I think the result is risky. Setting aside the rules I was taught way back when on handling secured materials - ya keep the secured materials away from the unsecured stuff, thereby avoiding an unpleasant and expensive encounter with Command Authority - unionfs does copy-on-write.

Wasn't sure so I tested:
Touched a couple of file in ~/temp:
```
cd ~/temp
touch afile-intemp.txt
touch bfile-intemp.txt

```Added some text to each.

Made a 50MB container via Truecrypt, with ext3 fs. Mounted via Truecrypt, touched a couple of files there:
```
cd /media/truecrypt3
touch afile-intc.txt
touch bfile-intc.txt

```Added some text to each.

unified both to /mnt/xu:
```
sudo -i
mount -t unionfs -o dirs=/home/dlk/temp:/media/truecrypt3 none /mnt/xu

```
... and in /mnt/xu I have:
```
root@dlk-lt-1420:/mnt/xu# ls -al
total 30
drwxr-xr-x  3 dlk  dlk   4096 2009-11-08 07:39 .
drwxr-xr-x 12 root root  4096 2008-10-02 03:24 ..
-rw-r--r--  1 dlk  dlk     33 2009-11-08 07:39 afile-intc.txt
-rw-r--r--  1 dlk  dlk      0 2009-11-08 07:37 afile-intc.txt~
-rw-r--r--  1 dlk  dlk     22 2009-11-08 07:39 afile-intemp.txt
-rw-r--r--  1 dlk  dlk      0 2009-11-08 07:32 afile-intemp.txt~
-rw-r--r--  1 dlk  dlk     34 2009-11-08 07:40 bfile-intc.txt
-rw-r--r--  1 dlk  dlk      0 2009-11-08 07:37 bfile-intc.txt~
-rw-r--r--  1 dlk  dlk     23 2009-11-08 07:39 bfile-intemp.txt
-rw-r--r--  1 dlk  dlk      0 2009-11-08 07:32 bfile-intemp.txt~
drwx------  2 root root 12288 2009-11-08 07:35 lost+found

```

Test access:
```
root@dlk-lt-1420:/mnt/xu# cat afile-intc.txt
first file in /media/truecrypt3

root@dlk-lt-1420:/mnt/xu# cat afile-intemp.txt
first file in ~/temp

root@dlk-lt-1420:/mnt/xu# 

```

So far, so good - that's the text I put in each. But something bothered me - will an edited file stay put?

Fired up Gedit and made changes to both "afiles" accessing via /mnt/xu.
Unmounted /mnt/xu and checked the two places:
```
dlk@dlk-lt-1420:~/temp$ ls -l
total 16
-rw-r--r-- 1 dlk dlk 54 2009-11-08 08:03 afile-intc.txt
-rw-r--r-- 1 dlk dlk 43 2009-11-08 08:03 afile-intemp.txt
-rw-r--r-- 1 dlk dlk 22 2009-11-08 07:39 afile-intemp.txt~
-rw-r--r-- 1 dlk dlk 23 2009-11-08 07:39 bfile-intemp.txt
-rw-r--r-- 1 dlk dlk  0 2009-11-08 07:32 bfile-intemp.txt~
dlk@dlk-lt-1420:~/temp$ 
```
and in the truecrypt container:
```
dlk@dlk-lt-1420:/media/truecrypt3$ ls -l
total 14
-rw-r--r-- 1 dlk  dlk     33 2009-11-08 07:39 afile-intc.txt~
-rw-r--r-- 1 dlk  dlk     34 2009-11-08 07:40 bfile-intc.txt
-rw-r--r-- 1 dlk  dlk      0 2009-11-08 07:37 bfile-intc.txt~
drwx------ 2 root root 12288 2009-11-08 07:35 lost+found

```

Good news: The respective files showed the edits.

Bad news: The secured material leaked out. afile-intc.txt is now out of the secured box, it's in ~/temp That's because I gave ~/temp priority over /media/truecrypt3 in the mount command. Had I reversed them leakage would have went the other way I believe. But that's no good either: You'll spend time moving files back, increasing the odds of ordinary human error leaking secured material.

Either way, I think it's not something one wants to do, unifying a secured container mount with an open file system point if there's any chance of modifying the secured data.

---

