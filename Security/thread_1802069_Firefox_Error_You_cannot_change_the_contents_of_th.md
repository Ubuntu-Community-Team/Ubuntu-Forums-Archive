---
title: "Firefox Error: You cannot change the contents of that folder"
date: 2011-07-11
forum: Security
---

### Post by martycombs on 2011-07-11
I have a separate mount point from my home directory to which I save files for later installation, etc.  However, when attempting to save files images, pdfs, tarballs, in firefox to this directory using the firefox installation included with Ubuntu 10.04 LTS, I am presented with the error "...you cannot change the contents of that folder."  

I am owner of this directory and I have even tried giving it more open permissions (even attempting chmod 777) with the problem still present.  I have also tried deleting the downloads.sqlite in my firefox profile as well as removing my profile altogether.  

This error does not present itself when I run firefox from a tarball installation in /usr/local/.  It is specific to the Ubuntu installation of firefox.

I have searched around multiple times attempting to find a solution but have not seen anything posted.

If anyone could point me to a solution, I would be most appreciative.

Regards,
/marty/

---

### Post by bodhi.zazen on 2011-07-11
Probably apparmor. See the sticky on apparmor and check your logs.

---

