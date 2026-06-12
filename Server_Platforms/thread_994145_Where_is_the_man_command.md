---
title: "Where is the man command?"
date: 2008-11-26
forum: Server Platforms
---

### Post by chiggsy on 2008-11-26
Ok, I've run aptitude install manpages manpages-dev

when i try to run 'man aptitude'

i get 

bash: man: command not found


this is really irritating!  how can I install the man command?

---

### Post by Titan8990 on 2008-11-26
I have actually never seen a UNIX based system without man.


Post the outputs for the following:


```
which man
```


```
echo $PATH
```

---

### Post by chiggsy on 2008-11-26
root@psss:~# which man
root@psss:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
root@psss:~# 
 
aptitude install manpages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

root@psss:~# man
bash: man: command not found

---

### Post by Keith Hedger on 2008-11-26
> **Titan8990 said:**
> I have actually never seen a UNIX based system without man.

Not helpful i know but linpus on the acer one webbook doesn't have man installed.

Just tried doing a package search using apt-file and man doesn't seem to be in any of the packages in the repos:confused: , what do you get if you try ```
/usr/bin/man
```

---

### Post by Titan8990 on 2008-11-26
I did find it in the repos but I am running 7.10 so lets hope that it is the same:


sudo apt-get install manpages

---

### Post by MJN on 2008-11-26
manpages contains only the man(ual) pages for various system functions.

The reader, man, should be in /usr/bin/ (as a symbolic link to /usr/lib/man-db/man).

If it's not, install it with **sudo apt-get install man-db**

Mathew

---

### Post by chiggsy on 2008-11-26
Thanks, that seems to have done it.

---

