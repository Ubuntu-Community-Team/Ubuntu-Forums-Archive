---
title: "cps - a useful addition to the cp command?"
date: 2024-01-13
forum: Ubuntu Application Development
---

### Post by dk000 on 2024-01-13
Hello!

I have just finished the 1.1 version of my copying/backup program called cps (stands for copy-synchronize). cps compares and synchronizes two directories by copying only the missing files and directories, but also enables you to overwrite the same files of different size or different last modification time, as well as to copy or delete any surplus data. It provides very useful information in it's statistical output after scanning and enables you to see the list and size of the files and directories that will be copied before commencing the copying operation. It also allows you to create a text file with the list of all the files and directories that are about to be copied without actually copying anything. The program recognizes when two directories are on different disks and will read the contents of the two directories simultaneously during the scanning. 

I've been testing it by deleting files and directories at various points in the file tree, scanning them with the program and copying, and I think it is safe to say that it is 100% accurate. I have used it to backup my own data for quite some time, but more people will have to test it to confirm that. So if you don't have nothing better to do or you are in need of such a program, you can provide some feedback on bugs and suggestions for other features that I should try to implement. Advice from the native English speakers about any unclear option names or descriptions is also welcome. There is a short tutorial for the program on my github page where you can also download it: [https://github.com/DK0352/cps](https://github.com/DK0352/cps).

I also plan to implement the networking part to enable remote copying, but that will come in the future if I persist working on the program.

I have two questions:

1. The program ignores all special files like sockets, device files, FIFOS. I'm not sure whether it is worth bothering with adding the option to copy these types of files?

2. Does the "surplus data" term makes sense in English or is there a more appropriate term for the data existing in the secondary/destination directory, but not in the main/source directory?

Also, the program doesn't differentiate pathname arguments based on the last slash character like rsync does. Synchronization of directories is always implied. 

For fastest copying/bench-marking, use -q or --no-questions option, possibly even -g or --dont-list-data-to-copy.

And finally, I think that I should mention that this is the first "serious" program that I have ever made, so if there are some dumb mistakes, now you know why. This can also be the case since I decided to change many option letters at some point and it could be that I forgot to change some parts of the code in relation to that.

---

### Post by TheFu on 2024-01-13
Can you compare it with **rsync**, the UNIX standard for this stuff?  Why would we use this rather than **rsync**?

Does it correctly handle sparse files?  ACLs?  xattrs?

"surplus data" sounds more like "new files" to me.

For my needs, backups that aren't pulled over the network and support versioning of the files, permissions/ACLs, xattrs, owner, group aren't very useful.

I like the differentiation that the trailing / provides with rsync. It allows me to know the exact level that all files will be mirrored.

Also, performance will be of major importance.  If it isn't faster than rsync, even for local-only copies, which is where rsync kinda fails without very specific options to prevent full copy from happening for files that have any changes at all.   

There are other sync tools which try to address the shortcomings of rsync.  **bsync** is one I looked at when my local backups weren't completing within the nightly backup window.  I was being stupid, trying to backup huge binary files (whole VM img files).  In the end, I completely changed how I did backups and now need less than 30 minutes total, when 8 hrs wasn't long enough before.  Most system backups finish in less than 2 minutes now, which just a few that have millions of files taking longer.

"surplus directories" doesn't convey clearly what you intend.  "Surplus" usually means "unimportant things" that aren't needed, so I doubt that is the intended term.

---

### Post by dk000 on 2024-01-20
> **TheFu said:**
> Can you compare it with **rsync**, the UNIX standard for this stuff?  Why would we use this rather than **rsync**?

cps is meant to be very easy to use and to give useful statistical information by default (with an option to disable it) rather than other way around like the rsync does it. To get equivalent information to running the cps without any arguments to sync the two directories, you would have to use: **rsync -rl --ignore-existing --stats --info=name --dry-run directory1/ directory2/**. Then if you decide that you do want to copy that data, you would have to run the command again without --dry-run, while with cps you would just type "yes" and the data copying would begin. With cps, even without any additional options you can find out if there are any files with the same name, but different size or modification time and list them out with just -L. I'm not sure if you are able to obtain such information with rsync without doing different type of scan, such as supplying rsync --size-only instead of --ignore-existing, but then also all the files that don't exist in the destination are listed out, so you have to add -i or --itemize-changes and look for files with the 's' letter in the string before the pathname. cps is very simple to use for copying operations and that is the reason why I "advertise" it as a useful addition to the cp command, since it doesn't posses all the options, especially the networking part, that a serious backup program like rsync does.

> Does it correctly handle sparse files?  ACLs?  xattrs?

It doesn't provide the support for ACLs, xattrs yet. But I don't think  it would be very complicated to add these features, so I might try to  add that very soon. I'm not sure about sparse files, I will have to  investigate that.

> Also, performance will be of major importance.  If it isn't faster than rsync, even for local-only copies, which is where rsync kinda fails without very specific options to prevent full copy from happening for files that have any changes at all.   

 I've done some tests during the development to get the general idea about performance of the program, but I've decided to perform them again because I lost some details about these tests over the time, so in order not to give some inaccurate information, I've decided to perform them again. That's also why it took longer to reply to your post. And I discovered that I accidentaly introduced an old bug into this 1.1 verson that I presented to the public, so I was under stress for some time trying to fix it. :-D Everybody should use 1.1.2 from now on. Benchmark results will be in the next post.


> "surplus directories" doesn't convey clearly what you intend.  "Surplus" usually means "unimportant things" that aren't needed, so I doubt that is the intended term.

Explanation of surplus data options: when you use cps directory1 directory2, directory1 never gets changed. All the data that doesn't exist in directory2 is copied from directory1. But that doesn't mean that there is no data in directory2 that doesn't exist in directory1. So I called this the suplus data. Now, you can just ignore this data or you can use --delete-surplus option to delete this data from directory2 and make directory1 and directory2 equal, or --copy-surplus-back to copy this additional data from directory2 to directory1 to again make them equal, but with this additional data from directory2. So in this case directory1 does get modified. rsync equivalent to --delete-surplus is --delete and rsync calls them extraneous files in the man page. I'm not sure about equivalent option for --copy-surplus-back.

---

### Post by dk000 on 2024-01-20
From now on use just 1.1.2 version as there were some bugs in 1.1.

The tests were done on a Xeon E3-1225v5, 8GB DDR4 with 1TB, 3TB and 6TB sata disks on Debian 11, Xubuntu 23.10 and Fedora 39. Some syncing tests with two disks happend to be on different filesystems. I don't know if that can impact performance in any visible way. I've used a small shell script that takes a text document with the list of files and directories to delete so to delete exacatly the same files and directories each time, and then ran both programs with the time command. I have restarted the OS inbetween each run, and did few runs with each program. The test directories were 596.67GB and 581.18GB in size, and I've used different levels of copy sizes. I've done more tests than what is show here and the only difference is that results fluctuate from 10-30 seconds. I've picked the best results that I received with each program. I will perform the tests with even bigger directories in the future. Also, suggestions for different/better types of benchmarks are welcome as I don't really have experience with this.

commands used:

cps -qgrw directory1 directory2
rsync -rl --ignore-existing --stats directory1/ directory2/

**Xubuntu 23.10 (xfs filesystem)**

Two directories on the same disk:

directory1: 581.29GB

Size of the data to copy: 11.90GB
Number of files to copy: 572
Number of directories to copy: 74

```
cps:
real    2m32,243s
user    0m4,093s
sys     0m20,384s

rsync:
real    2m43,732s
user    0m7,533s
sys    0m25,640s
```

Size of the data to copy: 50.51GB
Number of files to copy: 11175
Number of directories to copy: 589

```
cps:
real    14m35,204s
user    0m17,513s
sys    1m24,874s

rsync:
real    14m22,347s
user    0m32,287s
sys    1m51,335s
```

Size of the data to copy: 91.42GB
Number of files to copy: 13432
Number of directories to copy: 703

```
cps:
real    23m30,800s
user    0m31,796s
sys    2m30,802s

rsync:
real    23m16,686s
user    0m56,191s
sys     3m15,328s
```

Two directories on the different disks (second disk with the xfs filesystem):

Size of data to copy: 11.90GB
Number of files to copy: 572
Number of directories to copy: 74

```
cps:
real    2m32,243s
user    0m4,093s
sys     0m20,384s

rsync:
real    2m40,743s
user    0m7,577s
sys     0m25,922s

```
Size of the data to copy: 63.15GB
Number of files to copy: 12570
Number of directories to copy: 592

```
cps:
real    8m55,929s
user    0m21,644s
sys     1m26,772s

rsync:
real    9m0,735s
user    0m40,129s
sys     1m52,601s
```

Size of the data to copy: 91.42GB
Number of files to copy: 13432
Number of directories to copy: 703

```
cps:
real    12m10,194s
user    0m31,127s
sys     2m2,778s

rsync:
real    12m26,278s
user    0m58,397s
sys     2m40,277s
```

[B]
Debian 11 (ext4 filesystem)[/B]

Two directories on the same disk:

directory1: 591,18GB

Size of the data to copy: 12.53GB
Number of files to copy: 712
Number of directories to copy: 81

```
cps:
real    3m47.284s
user    0m5.292s
sys     0m24.453s

rsync:
real    4m0.605s
user    0m5.271s
sys     0m23.787s
```

Size of the data to copy: 63.51GB
Number of files to copy: 12638
Number of directories to copy: 598

```
cps:
real    20m59.690s
user    0m26.864s
sys     2m2.506s

rsync:
real    22m3.747s
user    0m58.654s
sys     2m48.546s
```

Size of the data to copy: 105.70GB
Number of files to copy: 13637
Number of directories to copy: 729

```
cps:
real    33m2.035s
user    0m43.929s
sys     3m17.635s

rsync:
real    32m7.915s
user    1m32.557s
sys     4m31.768s
```

Two directories on the different disks (second disk with the xfs filesystem):

Size of the data to copy: 63.51GB
Number of files to copy: 12638
Number of directories to copy: 598

```
cps:
real    10m12.624s
user    0m31.260s
sys     1m45.261s

rsync:
real    11m11.143s
user    0m57.825s
sys     2m16.927s
```

Size of the data to copy: 105.70GB
Number of files to copy: 13637
Number of directories to copy: 729

```
cps:
real    15m.762s
user    0m57.414s
sys     3m7.345s

rsync:
real    16m7.254s
user    1m31.635s
sys     3m39.779s
```

**Fedora 39 (btrfs)**

Two directories on the same disk:

directory1: 597.18GB

Size of the data to copy: 12.53GB
Number of files to copy: 712
Number of directories to copy: 81

```
cps:
real    3m21,448s
user    0m3,566s
sys     0m14,904s

rsync:
real    3m27,852s
user    0m7,215s
sys     0m17,114s
```

Size of the data to copy: 63.51GB
Number of files to copy: 12638
Number of directories to copy: 598

```
cps:
real    16m4,211s
user    0m17,393s
sys     1m9,931s

rsync:
real    17m32,169s
user    0m35,373s
sys     1m21,892s
```

Size of the data to copy: 105.70GB
Number of files to copy: 13637
Number of directories to copy: 729

```
cps:
real    25m25,975s
user    0m29,050s
sys     1m54,108s

rsync:
real    26m2,359s
user    0m57,765s
sys     2m16,175s
```

Two directories on the different disks (second disk with the xfs filesystem):

directory1: 597.18GB

Size of the data to copy: 12.53GB
Number of files to copy: 712
Number of directories to copy: 81

```
cps:
real    2m40,859s
user    0m3,700s
sys     0m14,996s

rsync:
real    3m31,256s
user    0m6,989s
sys     0m17,113s
```

Size of the data to copy: 63.51GB
Number of files to copy: 12638
Number of directories to copy: 598

```
cps:
real    13m29,253s
user    0m17,796s
sys     1m12,609s

rsync:
real    13m19,804s
user    0m36,075s
sys     1m24,027s
```

Size of the data to copy: 105.70GB
Number of files to copy: 13637
Number of directories to copy: 729

```
cps:
real    16m27,128s
user    0m29,237s
sys     1m59,896s

rsync:
real    15m54,411s
user    0m57,473s
sys     2m13,916s
```

---

