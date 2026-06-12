---
title: "'chmod +x /bin' a bad idea?"
date: 2012-11-15
forum: Security
---

### Post by chrisinpants on 2012-11-15
Would it be bad form to execute 'chmod +x /bin' as root? I'm guessing no, that's what the bin is for right?

---

### Post by drmrgd on 2012-11-15
/bin already is executable by default.  I think the perms on it are 755 as are most of the files within.  Do you mean something else?

---

### Post by vandorjw on 2012-11-15
```

joost@ubuntu:/bin$ ls -l
total 9004
-rwxr-xr-x 1 root root  955024 Apr  3  2012 bash
-rwxr-xr-x 3 root root   31112 Dec 15  2011 bunzip2
-rwxr-xr-x 1 root root 1827920 Apr 13  2012 busybox
.....
-rwxr-xr-x 1 root root   51760 Oct  1 23:23 chmod
-rwxr-xr-x 1 root root   60016 Oct  1 23:23 chown
-rwxr-xr-x 1 root root   10392 Mar 31  2012 chvt
-rwxr-xr-x 1 root root  126032 Oct  1 23:23 cp

```


as you can see, everything in this folder has execute permission by everyone. (last collumn for others)

As well, the actuall folder
> 
drwxr-xr-x   2 root root  4096 Nov 15 12:03 bin


But I think what you want to do is


```

# chmod -R a+x /bin

```

Which should be saf.

---

### Post by chrisinpants on 2012-11-15
That is what I want to do, as I've already done the former :). 'Glad that I didn't cause myself another headache,  thanks for the tips

CHris

---

