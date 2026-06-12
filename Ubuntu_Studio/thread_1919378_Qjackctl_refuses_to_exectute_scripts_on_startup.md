---
title: "Qjackctl refuses to exectute scripts on startup"
date: 2012-02-02
forum: Ubuntu Studio
---

### Post by asuastrophysics on 2012-02-02
Hey all,

I have configured through the "setup" option for qjackctl to execute certain scripts on startup. However, from what I can tell, the program simply isn't executing the scripts, even though I checked the boxes under "execute script before startup....during startup....etc" 
If I double click on my script, it executes just fine. Is this a bug in qjackctl? How else can I instruct it to launch scripts besides doing what I've already done? Thanks in advance

---

### Post by sgx on 2012-02-02
Hi, if you post the scripts, qjackctl version, distro version,
and the .jackdrc textfile, it will help folks to offer solutions.
Cheers

---

### Post by CivilizationII on 2012-02-17
> **asuastrophysics said:**
> Hey all,

I have configured through the "setup" option for qjackctl to execute certain scripts on startup. However, from what I can tell, the program simply isn't executing the scripts, even though I checked the boxes under "execute script before startup....during startup....etc" 
If I double click on my script, it executes just fine. Is this a bug in qjackctl? How else can I instruct it to launch scripts besides doing what I've already done? Thanks in advance


You must specify the whole path for your script in qjackctl. Be also sure of access and executable right.

---

