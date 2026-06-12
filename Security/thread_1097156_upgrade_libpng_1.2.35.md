---
title: "upgrade libpng 1.2.35"
date: 2009-03-15
forum: Security
---

### Post by mmix on 2009-03-15
upgrade your libpng package
[quote="[libpng](http://www.libpng.org/pub/png/libpng.html)"]
[color=red]Vulnerability Warning
All versions of libpng from 0.89c through 1.2.34 contain an uninitialized-data bug that can be triggered by a malicious user. Specifically, there are several instances in which a malloc'd array of pointers is then initialized by a secondary sequence of malloc() calls. If one of these calls fails, libpng's cleanup routine will attempt to free the entire array, including any uninitialized pointers, which could lead to execution of an attacker's code with the privileges of the libpng user (including remote compromise in the case of a libpng-based browser visiting a hostile web site). This vulnerability has been assigned ID CVE-2009-0040 and is fixed in version 1.2.35, released 18 February 2009.[/color] [/quote]

---

