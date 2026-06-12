---
title: "Can't find kernel header files with 2.6.24-18-rt"
date: 2008-06-05
forum: Virtualisation
---

### Post by who_cares on 2008-06-05
I have the 2.6.24-18-rt kernel that came with Ubuntu Studio and when I run vmware-config.pl it asks for the location of the header files so I put in "/usr/src/linux-headers-2.6.24-18/include" but it comes back with this:
> The path "/usr/src/linux-headers-2.6.24-18/include" is a kernel header file 
directory, but it does not contain the file "linux/version.h" as expected.  
This can happen if the kernel has never been built, or if you have invoked the 
"make mrproper" command in your kernel directory.  In any case, you may want to
rebuild your kernel.


Anyone know how to finish installing vmware here?

---

### Post by Z2. on 2008-06-05
Having the same issue here too - VMWare Server 2 Beta huh?

---

### Post by Z2. on 2008-06-05
Found the answer [HERE]("http://ubuntuforums.org/archive/index.php/t-25258.html")

---

