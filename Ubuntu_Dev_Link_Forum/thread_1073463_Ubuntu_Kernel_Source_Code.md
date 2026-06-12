---
title: "Ubuntu Kernel Source Code"
date: 2009-02-18
forum: Ubuntu Dev Link Forum
---

### Post by yida on 2009-02-18
Hi, guys:
I'm looking for a set of Ubuntu source code that could match my running kernel. I was trying this for a whole day and there was NO luck.
I've downloaded the source code dvd from a mirror site and found out the *.orig.gz,*.diff.gz,*.dsc files for kernel 2.6.27.7.14. But after dpkg-source -x *.dsc file, I've got a source code versioned as 2.6.27.2.
I've also tried to get the version 2.6.27.11.14 (package name was linux-source and versioned as 2.6.27.11.14), but there were NO *.diff.gz available in the source code package downloaded from repository. But it was having a dependency of the other package named 'linux-source-2.6.27', which is versioned as 2.6.27.11.27. This packaged includes a bz2 file and after I extracted the file, the version reads 2.6.27.10.
All the source code version, I got them from the first few lines in the "Makfile" file resides right in the source code directory.
I'm now having 2.6.27.7.14 kernel image and 2.6.27.11.14 image available in my system, from which I can boot with.
My purpose is to get a source code set that could match either kernel image I can boot from and it seemed I can not make it.
Is there anybody can tell me a way of achieving this? Thanks.

Regards,
Yida 
a newbie in Ubuntu just got 8.10 desktop version up and running.

---

### Post by yida on 2009-02-20
Source code seem to be the right ones.
I've installed git-core and used git to get all the versions of v8.10 kernel source code (which took me another day, for that my network speed was so poor that day). The two versions of my download from packages agree with the ones I got through git. Which should mean that I've got the correct kernel source code.
So the next step should be compiling them to the versions matching my running kernel to have a look and feel about how to compile kernel from source code.
Will let you guys know when I'm finished with it. Thanks.

---

