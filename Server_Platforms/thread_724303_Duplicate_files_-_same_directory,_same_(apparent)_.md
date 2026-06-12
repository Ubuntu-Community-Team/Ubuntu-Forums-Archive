---
title: "Duplicate files - same directory, same (apparent) name, same inode"
date: 2008-03-14
forum: Server Platforms
---

### Post by leonv12 on 2008-03-14
Greetings,

I am using ubuntu server (6.06) as a backup server.  A problem recently developed that is driving me crazy.  I have two files in the same directory with the same (apparent) name pointing to the same inode.  I ran fsck - no help.  

If I do the full file name, only one shows up
# ls -lia 10640601.i24
> 45066517 -rwx------ 1 root root 272308 2008-03-14 11:05 10640601.i24
If add a *, I get both files
> ls -lia 10640601.i24*
45066517 -rwx------ 1 root root 272308 2008-03-14 11:05 10640601.i24
45066517 -rwx------ 1 root root 272308 2008-03-14 11:05 10640601.i24
If have piped the output file names to od -bc, they appear identical
> ls 10640601.i24*|od -bc
0000000 061 060 066 064 060 066 060 061 056 151 062 064 012 061 060 066
          1   0   6   4   0   6   0   1   .   i   2   4  \n   1   0   6
0000020 064 060 066 060 061 056 151 062 064 012
          4   0   6   0   1   .   i   2   4  \n
0000032
I have tride copying the full file name to a .bak it seems to work
> # cp 10640601.i24 10640601.i24.bak
# ls -lia 10640601.i24*
45066517 -rwx------ 1 root root 272308 2008-03-14 11:05 10640601.i24
45066517 -rwx------ 1 root root 272308 2008-03-14 11:05 10640601.i24
21971267 -rwx------ 1 root root 272308 2008-03-14 11:18 10640601.i24.bak
I them remove the original - appears to work
> # rm 10640601.i24
# ls -lia 10640601.i24*
21971267 -rwx------ 1 root root 272308 2008-03-14 11:18 10640601.i24.bak
I them rename (mv) gack to the original file name and BOOM, I have duplicates again.
> # mv 10640601.i24.bak 10640601.i24
# ls -lia 10640601.i24*
21971267 -rwx------ 1 root root 272308 2008-03-14 11:18 10640601.i24
21971267 -rwx------ 1 root root 272308 2008-03-14 11:18 10640601.i24
Can anyone please tell me what is going on here?  I am losing my mind!:confused:

---

### Post by timcredible on 2008-03-14
does one of them have a space at the end of the filename?

---

### Post by leonv12 on 2008-03-14
The octal dump (od -bc) shows the file names to be identical.  There are no spaces in the file name.

---

