---
title: "Request: Boost 1.32"
date: 2005-05-16
forum: Ubuntu Backports
---

### Post by BertR on 2005-05-16
I would like to have [Boost](http://www.boost.org/) 1.32.0 in Ubuntu Backports. The source code can be found at [http://sourceforge.net/project/showfiles.php?group_id=7586](http://sourceforge.net/project/showfiles.php?group_id=7586) 
Ubuntu still uses 1.31.0 (which is more than a year old) as can be seen at [http://packages.ubuntu.com/hoary/libdevel/](http://packages.ubuntu.com/hoary/libdevel/)

Debian has 1.32.0 libraries in testing: [http://packages.debian.org/testing/source/boost](http://packages.debian.org/testing/source/boost)

---

### Post by Technoviking on 2005-05-16
It is in Breezy, I will try to backport it.

Mike

---

### Post by BertR on 2005-05-16
[QUOTE=Mike Basinger]It is in Breezy, I will try to backport it.

Mike[/QUOTE]

Thank you!

---

### Post by mics on 2005-05-16
I installed libboost-dev directly from breezy, all dependencies are met anyway. Working without any problems.

---

### Post by Technoviking on 2005-05-16
[QUOTE=BertR]Thank you![/QUOTE]
Compiled, but it wants to compile againist Python, I want to solve that problem first before I post it.

Mike

---

### Post by BertR on 2005-05-21
[QUOTE=Mike Basinger]Compiled, but it wants to compile againist Python, I want to solve that problem first before I post it.

Mike[/QUOTE]

Still having problems? ;-)

---

### Post by BertR on 2005-07-04
Almost two months later...

---

### Post by Seth on 2005-07-04
[QUOTE=BertR]Almost two months later...[/QUOTE]
 This is built from Breezy sources on a clean Hoary chroot. It only depends on original Hoary libs (e.g., not backported ones) and so should be 100% kosher.

[http://sethkinast.com/ubuntu/hoary/backports/boost/](http://sethkinast.com/ubuntu/hoary/backports/boost/)

---

### Post by AndyWHV on 2005-08-04
Hi Seth...

I would also like to use the new boost lib.

I am new to Ubuntu (Debian) deb package management...

is it possible to add your backports to the sources list ?

would you recommend to do it ?

if its possible please let me know how to do it...otherwise i will install it via dpkg

thank you
Andy

---

### Post by matthias_k on 2005-08-17
Can't *bump* this enough.

Boost is so essential to C++ programming, and 1.31 doesn't have some features I'm using in my code, e.g. comparison operators on boost::filesystem::pathS. Please add at least 1.32 (even better 1.33) to the official respositories.

Thanks a lot.

PS: I noticed that the path to the debs you posted does not have the structure of a apt repository. Is it possible at all to include this path into sources.list and install through synaptic?

---

### Post by hod139 on 2005-09-01
[QUOTE=matthias_k]Can't *bump* this enough.

Boost is so essential to C++ programming, and 1.31 doesn't have some features I'm using in my code, e.g. comparison operators on boost::filesystem::pathS. Please add at least 1.32 (even better 1.33) to the official respositories.
[/QUOTE]

I second adding boost 1.33 (at least to the backports).  I don't see the point in adding 1.32 with 1.33 out, especially since 1.32 doesn't support g++ 4.  Boost 1.31 is _very_ old even though the versioning scheme doesn't make it appear that way.

---

