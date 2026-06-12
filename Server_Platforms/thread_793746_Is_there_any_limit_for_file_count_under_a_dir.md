---
title: "Is there any limit for file count under a dir?"
date: 2008-05-14
forum: Server Platforms
---

### Post by magic22cn on 2008-05-14
I have create a hash dir , it just look like this:

/dir/0
/dir/0/0
/dir/0/0/0
/dir/0/0/0/1
/dir/0/0/0/1/a001.txt

/dir/1
/dir/1/0
/dir/1/0/2
/dir/1/0/2/3
/dir/0/0/2/3/b100.txt

I only put file in deepest dir and every 100 file in each dir.

But , when the application have used about 30% disk space , about 30G, it will say "no space on device".I can see we have 70% space on disk through df -h.

So I have to clear the disk by deleted some file in this dir.After deleting , it will be ok.

And then , i use some large file to test the disk , i can fill the disk to 90% with 60 10g file, so I think my disk has no bad track.

So I wonder there is some limit on ubuntu or linux to limit the total count of files in a directory , include it's sub-dir.

Anyone could kindly explain this and help me solve this problem?

Thx a lot for any tips!

---

### Post by prshah on 2008-05-14
> **magic22cn said:**
> I have create a hash dir , it just look like this:
I only put file in deepest dir and every 100 file in each dir.

But , when the application have used about 30% disk space , about 30G, it will say "no space on device".I can see we have 70% space on disk through df -h.


See the output of ```
df -i
```, you are running out of inodes. If you cannot change your way of operation, maybe you need to use another file system? ntfs, reiserfs, etc.. not that I know of anything except ext2/3, ntfs and fat. I just threw in resierfs because I've heard a lot about it.

---

### Post by magic22cn on 2008-05-14
> **prshah said:**
> See the output of ```
df -i
```, you are running out of inodes. If you cannot change your way of operation, maybe you need to use another file system? ntfs, reiserfs, etc.. not that I know of anything except ext2/3, ntfs and fat. I just threw in resierfs because I've heard a lot about it.

Ooops!you are quite right!

i have checked by df -i , i am really run out of inode.

Thx a lot!

And i have check what's feature the resierfs has,I think it can solve my problem , i will format my disk soon and report back what's the result of this change.

Thank you very much!

---

