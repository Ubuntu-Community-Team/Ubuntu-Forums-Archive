---
title: "how to reduce time of git pulling each time when you do a make world on Xen source"
date: 2011-02-26
forum: Virtualisation
---

### Post by tapas_mishra on 2011-02-26
I am compiling xen from source and each time I do a **make world**
it basically gives some or the other error
my problem are not those errors ( I am trying to debug them)
but the problem is each time when I do a **make world**

Xen basically pulls things from git repository
```

   + rm -rf linux-2.6-pvops.git linux-2.6-pvops.git.tmp
   + mkdir linux-2.6-pvops.git.tmp
   + rmdir linux-2.6-pvops.git.tmp
   + git clone -o xen -n
git://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git
linux-2.6-pvops.git.tmp
   Initialized empty Git repository in
/usr/src/xen-4.0.1/linux-2.6-pvops.git.tmp/.git/
   remote: Counting objects: 1941611, done.
   remote: Compressing objects: 100% (319127/319127), done.
remote: Total 1941611 (delta 1614302), reused 1930655 (delta 1604595)
****Receiving objects: 20% (1941611/1941611), 98.17 MiB | 87 KiB/s, done.****

```

and if you notice the last line it is still consuming my bandwidth
pulling things from internet.How can I stop this step each time and
use existing git repository?
When I searched an answer to this question I came across a  link
[http://lists.xensource.com/archives/html/xen-users/2010-04/msg00476.html](http://lists.xensource.com/archives/html/xen-users/2010-04/msg00476.html)
[http://web.archiveorange.com/archive/v/ZvO4jYCfIzdpcmkWRz5w](http://web.archiveorange.com/archive/v/ZvO4jYCfIzdpcmkWRz5w)

but I am not able to clearly understand where Boris mentions 

> 
make xen etc.
"Then clone JF's Git Repo, checkout git branch as you want and build
corresponding
kernel.That's all i always do."

Which kernel is he referring to is it Dom0?
because when I ran make xen it worked without  any problem and I can see in my
/usr/src/xen-4.0.1/dist/install/boot
> xen-4.0.1.gz  xen-4.0.gz  xen-4.gz  xen.gz  xen-syms-4.0.1

but I am not clear with how to save this git pull each time.
I have given a link which I think is a solution to my problem but I am not able understand what they have mentioned.Can some one explain that.

---

### Post by kamzhang on 2011-02-26
> **tapas_mishra said:**
> I am compiling xen from source and each time I do a **make world**
it basically gives some or the other error
my problem are not those errors ( I am trying to debug them)
but the problem is each time when I do a **make world**
 
Xen basically pulls things from git repository
```

   + rm -rf linux-2.6-pvops.git linux-2.6-pvops.git.tmp
   + mkdir linux-2.6-pvops.git.tmp
   + rmdir linux-2.6-pvops.git.tmp
   + git clone -o xen -n
git://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git
linux-2.6-pvops.git.tmp
   Initialized empty Git repository in
/usr/src/xen-4.0.1/linux-2.6-pvops.git.tmp/.git/
   remote: Counting objects: 1941611, done.
   remote: Compressing objects: 100% (319127/319127), done.
remote: Total 1941611 (delta 1614302), reused 1930655 (delta 1604595)
****Receiving objects: 20% (1941611/1941611), 98.17 MiB | 87 KiB/s, done.****

```
 
and if you notice the last line it is still consuming my bandwidth
pulling things from internet.How can I stop this step each time and
use existing git repository?
When I searched an answer to this question I came across a link
[http://lists.xensource.com/archives/html/xen-users/2010-04/msg00476.html](http://lists.xensource.com/archives/html/xen-users/2010-04/msg00476.html)
[http://web.archiveorange.com/archive/v/ZvO4jYCfIzdpcmkWRz5w](http://web.archiveorange.com/archive/v/ZvO4jYCfIzdpcmkWRz5w)
 
but I am not able to clearly understand where Boris mentions 
 
 
Which kernel is he referring to is it Dom0?
because when I ran make xen it worked without any problem and I can see in my
/usr/src/xen-4.0.1/dist/install/boot
 
but I am not clear with how to save this git pull each time.
I have given a link which I think is a solution to my problem but I am not able understand what they have mentioned.Can some one explain that.
 
I also want to know!:P

---

