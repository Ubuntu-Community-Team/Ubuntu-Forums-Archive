---
title: "du mystery"
date: 2014-05-04
forum: Server Platforms
---

### Post by geohei on 2014-05-04
Hi.

This is weird ...

```

root@gan:/media/raid-main# du -a -B1
...
304758784       ./20021011#katab_20021126_141249-000120_029.avi
...
root@gan:/media/raid-main# ls -l
...
-rwxr-xr-x 1 root root 304755998 Nov  5 08:48 20021011#katab_20021126_141249-000120_029.avi
...

```
du command matches rounded up 4K blocks as shown by ls command. All fine.

Now I copied the file to a different server and I got:
```

root@cal:/media/raid-1# du -a -B1
...
304762880       ./20021011#katab_20021126_141249-000120_029.avi
...
root@cal:/media/raid-1# ls -l
...
-rwxr-xr-x 1 root root 304755998 May  2 11:55 20021011#katab_20021126_141249-000120_029.avi
...

```
du command shows 4K more than the rounded up 4K blocks from the ls command.

How come?

Both filesystems are ext4 and their block size is 4K as shown by dumpe2fs.

What am I missing?

---

### Post by Gyokuro on 2014-05-04
Hi

du is showing normally the disk usage which can vary but you can try:

du --apparent-size -k katab*.avi

and to be sure that everything got transfered I would md5sum the file and check.

- HTH

---

### Post by SeijiSensei on 2014-05-04
Or use diff:

```
diff /path/to/file1 /path/to/file2
```

For binary comparisons, diff reports when the files don't match and returns the empty string if they do.

---

### Post by geohei on 2014-05-05
> **Gyokuro said:**
> 
du is showing normally the disk usage which can vary but you can try:
du --apparent-size -k katab*.avi
and to be sure that everything got transfered I would md5sum the file and check.
Now ...
```

root@gan:/media/raid-main# du --apparent-size -k
10620071        .
root@gan:/media/raid-main# du --apparent-size -B1
10874952352     .
root@gan:/media/raid-main# du -B1
10875158528     .

```
```

root@cal:/media/raid-1# du --apparent-size -k
10620071        .
root@cal:/media/raid-1# du --apparent-size -B1
10874952352     .
root@cal:/media/raid-1# du -B1
10875166720     .

```

--apparent-size seems to make the difference. However I don't understand what it is in fact doing (man pages).
> 
       --apparent-size
              print  apparent  sizes, rather than disk usage; although the apparent size is usually
              smaller, it may be larger due to holes in (`sparse') files,  internal  fragmentation,
              indirect blocks, and the like

As far as I see, nothing of all this applies for my directories. Any ideas?

BTW ... both computers are connected via Samba to a LAN. If I use a Windows 7 machine and check Properties of subject shares, they show exactly the same size (0 byte difference). Also same number of files and directories.

> **SeijiSensei said:**
> ...
For binary comparisons, diff reports when the files don't match and returns the empty string if they do.
I forgot to mention that md5sums are 100% correct. I'm talking of a total of +700 GB copied!

---

### Post by Gyokuro on 2014-05-05
Hi

Ok - count me in I'm interested in what's up. Have you already tried what SeiijiSensei mentioned to check via diff? Another check would be:

od file1.avi > mother.txt
od file2.avi > daughter.txt

diff mother.txt daughter.txt

and how have you copied the file? You are mentioning to another server, via scp, ftp?? I would go via rsync over ssh or scp as all our files go over ssh+rsync and the files are matching each other.

---

### Post by geohei on 2014-05-05
No, I didn't try SeiijiSensei's check using diff, because ...
1. the number of files is identical (Samba check from Windows 7 machine).
2. the number of directories is identical (Samba check from Windows 7 machine).
3. the md5sum of all files is correct.

So it must be the way du works.

---

### Post by geohei on 2014-07-27
Some more tests ...
```
root@cal:/media/raid-1/DV/20021011#katab# ls -l *029.avi
-rwxr-xr-x 1 root root 304755998 May  2 11:55 20021011#katab_20021126_141249-000120_029.avi
root@cal:/media/raid-1/DV/20021011#katab# cp *029.avi 029new.avi
root@cal:/media/raid-1/DV/20021011#katab# du -B1 *029.avi
304762880       20021011#katab_20021126_141249-000120_029.avi
root@cal:/media/raid-1/DV/20021011#katab# du -B1 029new.avi
304758784       029new.avi
root@cal:/media/raid-1/DV/20021011#katab# md5sum *029.avi
f33f89734a3189db46ade0758375740c  20021011#katab_20021126_141249-000120_029.avi
root@cal:/media/raid-1/DV/20021011#katab# md5sum 029new.avi
f33f89734a3189db46ade0758375740c  029new.avi
```
When I copy the file, du gives the correct size!

In summary:
**katab_20021126_141249-000120_029.avi** is 304.755.998 bytes.
This results in 74.404 4K Blocks which is 304.758.784 bytes.
However du shows 304.762.880 Bytes, which are 74.405 4K blocks ... hence one 4K block too much!
Now ... when I copy the **katab_20021126_141249-000120_029.avi** to **029new.avi**, du shows 304.758.784 bytes, which is correct.
md5sum checksums of both files are identical.

How is it possible that du shows 4K too much for **katab_20021126_141249-000120_029.avi**?

---

### Post by geohei on 2014-07-29
Some more tests.

Host "gan". This is the departing point for the copy operation.
```
root@gan:/media/raid-main/DV/20011011#breno# du -B4096 *
41834   20011011#breno_20011011_065855-000045_001.avi
78793   20011011#breno_20011011_081758-000126_002.avi
1866890 20011011#breno_20011011_085016-003410_003.avi
49117   20011011#breno_20011011_092441-000053_004.avi
94741   20011011#breno_20011011_101746-000144_005.avi
649327  20011011#breno_20011011_110804-001153_006.avi
101587  20011011#breno_20011013_142213-000151_007.avi
59676   20011011#breno_20011014_094653-000105_008.avi
294986  20011011#breno_20011015_094438-000524_009.avi
46641   20011011#breno_20011016_082640-000051_010.avi
```

Host "cal". All files from "gan" were copied into this directory using scp. A first difference appear. File #002 +1 block! all other files show identical du values than for "cal".
```
root@cal:/media/raid-1/DV/20011011#breno# du -B4096 *
41834   20011011#breno_20011011_065855-000045_001.avi
78794   20011011#breno_20011011_081758-000126_002.avi
1866890 20011011#breno_20011011_085016-003410_003.avi
49117   20011011#breno_20011011_092441-000053_004.avi
94741   20011011#breno_20011011_101746-000144_005.avi
649327  20011011#breno_20011011_110804-001153_006.avi
101587  20011011#breno_20011013_142213-000151_007.avi
59676   20011011#breno_20011014_094653-000105_008.avi
294986  20011011#breno_20011015_094438-000524_009.avi
46641   20011011#breno_20011016_082640-000051_010.avi
```

Host "cal". Local copy from directoty above to "copyDV" using "cp -a". Some more differences appaer.
File #002 again back to -1 block, like for "cal".
File #005 now +1 block.
```
root@cal:/media/raid-1/DV/20011011#breno# du -B4096 ../copyDV/20011011#breno/*
41834   ../copyDV/20011011#breno/20011011#breno_20011011_065855-000045_001.avi
78793   ../copyDV/20011011#breno/20011011#breno_20011011_081758-000126_002.avi
1866890 ../copyDV/20011011#breno/20011011#breno_20011011_085016-003410_003.avi
49117   ../copyDV/20011011#breno/20011011#breno_20011011_092441-000053_004.avi
94742   ../copyDV/20011011#breno/20011011#breno_20011011_101746-000144_005.avi
649327  ../copyDV/20011011#breno/20011011#breno_20011011_110804-001153_006.avi
101587  ../copyDV/20011011#breno/20011011#breno_20011013_142213-000151_007.avi
59676   ../copyDV/20011011#breno/20011011#breno_20011014_094653-000105_008.avi
294986  ../copyDV/20011011#breno/20011011#breno_20011015_094438-000524_009.avi
46641   ../copyDV/20011011#breno/20011011#breno_20011016_082640-000051_010.avi
```

All filesystems are ext4 with 4K blocks.

Needless to say that all md5 checksums are identical. Also ... ls shows identical filesizes. But du shows differences in disk usage.

The block discrepancies show for scp (network copy) as well for cp (local copy).

It looks like for some reason, there's sometimes 1 block added after a copy. Why is that?

```
root@cal:/media/raid-1/DV/20011011#breno# du -B4096 ../copyDV/20011011#breno/*.avi --apparent-size
41834   ../copyDV/20011011#breno/20011011#breno_20011011_065855-000045_001.avi
78793   ../copyDV/20011011#breno/20011011#breno_20011011_081758-000126_002.avi
1866889 ../copyDV/20011011#breno/20011011#breno_20011011_085016-003410_003.avi
49117   ../copyDV/20011011#breno/20011011#breno_20011011_092441-000053_004.avi
94741   ../copyDV/20011011#breno/20011011#breno_20011011_101746-000144_005.avi
649326  ../copyDV/20011011#breno/20011011#breno_20011011_110804-001153_006.avi
101587  ../copyDV/20011011#breno/20011011#breno_20011013_142213-000151_007.avi
59676   ../copyDV/20011011#breno/20011011#breno_20011014_094653-000105_008.avi
294985  ../copyDV/20011011#breno/20011011#breno_20011015_094438-000524_009.avi
46641   ../copyDV/20011011#breno/20011011#breno_20011016_082640-000051_010.avi
root@cal:/media/raid-1/DV/20011011#breno# ls -l *003.avi *006.avi *009.avi
-rwxr-xr-x 1 root root 7646776106 May  2 08:04 20011011#breno_20011011_085016-003410_003.avi
-rwxr-xr-x 1 root root 2659636446 May  2 07:49 20011011#breno_20011011_110804-001153_006.avi
-rwxr-xr-x 1 root root 1208255486 May  2 07:51 20011011#breno_20011015_094438-000524_009.avi
```
Now last directory (local copy on "cal") with --apparent-size option. Files #003, #006 and #009 show again 1 block less. ls -l confirms that disk usage shown with --apparent-size option is the correct one.

So ... why does du without --apparent-size option show more than actually required. The du man pape excerpt doesn't really help since I don't see which item mentioned (... holes in (`sparse') files, internal fragmentation, indirect blocks, and the like) might apply to my very simple file copy.

---

