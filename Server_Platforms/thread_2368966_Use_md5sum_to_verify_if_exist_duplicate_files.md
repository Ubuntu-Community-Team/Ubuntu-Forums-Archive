---
title: "Use md5sum to verify if exist duplicate files"
date: 2017-08-17
forum: Server Platforms
---

### Post by sed_faster on 2017-08-17
Hello,

I need identify many files duplicate on a ubuntu server! For this task I am using the **md5sum** program! The files are mainly pdf or iso. I need know if the hash get through md5sum software it is the best option to verify if the files it is duplicate, it is the same.
At the moment I run script with md5sum and I get 500 occurs about files duplicate, with the same hash. Before delete the duplicate files I need know if there is full guarantee that the files are the same!

Thanks

---

### Post by TheFu on 2017-08-17
Don't use md5sum. There are collisions.  Didn't you ask this question today?

If you are looking for duplicate files on the system, there are tools for that - finddup.  Or you can write your own.  I did for fun after seeing a /. article about it.  I did it in perl.

* make a list of files and file sizes.
* group by size, then name
* if the size of any file is the same, run sha256sum.  If they match, then the files are identical. If not, they are different.

I used temporary files with this data:
```
{size}\t{filename}\t{date}\t{full path}
```

You can google on why md5sum isn't good enough - and other methods of comparison should be used BEFORE dropping to any hashing.  Hashing is expensive.  Files of different sizes are not the same, so don't bother.

---

### Post by sed_faster on 2017-08-22
Ok, This means which I have three methods to identify which files it is equal:

1-md5sum;
2-sha256sum;
3-finddup;

After thinking about the subject I decide use the three methods. What do you think about this?
 However I googled about software to identify equal files and I found Fdupes and Jdupes. How many programs do you know to do this task?

I don't like the finddup. Maybe because I don't know how works with this software ([http://manpages.ubuntu.com/manpages/precise/man1/finddup.1.html](http://manpages.ubuntu.com/manpages/precise/man1/finddup.1.html)) but I don't like the behaviour when I try discovery the equal files.

Thanks

---

