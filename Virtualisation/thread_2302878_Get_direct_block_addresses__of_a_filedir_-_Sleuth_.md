---
title: "Get direct block addresses  of a file/dir - Sleuth kit - XEN"
date: 2015-11-14
forum: Virtualisation
---

### Post by sklpr on 2015-11-14
Dear all,

I am using ***Sleuth kit library*** in order to write an introspection tool for **XEN** hypervisor running on ubuntu 12.04.5 x64bit and my question is if we have the inode number of a file on a disk [ guest VM - **ext4** filesystem], for example 6031126 and want to handle the *direct block pointers of a file/directory* later in a program,how can we get them(Direct Blocks : NumberX,NymberY etc) ? I used the *sleuth kit *function ***istat*** inside my program like on istat.cpp program of the library:

```
if (fs->istat(fs, stdout, inum, numblock, sec_skew)) {
tsk_error_print(stderr);
fs->close(fs);
img->close(img);
exit(1);
}
```

to get information about this inode and i got this :

```
inode: 6031126
Allocated
Group: 736
Generation Id: 3880935525
uid / gid: 1000 / 1000
mode: rrw-------
Flags: Extents, 
size: 6613
num of links: 1

Inode Times:
Accessed:   2015-11-12 17:47:55.857360000 (EET)
File Modified:  2015-03-27 14:05:13.000000000 (EET)
Inode Modified: 2015-07-12 00:51:07.489188000 (EEST)
File Created:   2015-07-12 00:51:07.489188000 (EEST)

Direct Blocks:
24172552 24172553
```

I know the block numbers by calling that function but i don't know where they are stored and how to retrieve them in a variable..? in order to use them later in my tool! 

Any tips/suggestions or documentation would be appreciated!
Thanks in advance!

---

