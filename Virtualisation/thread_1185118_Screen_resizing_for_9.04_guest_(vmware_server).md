---
title: "Screen resizing for 9.04 guest (vmware server)"
date: 2009-06-11
forum: Virtualisation
---

### Post by HDave on 2009-06-11
Using the patch I found [here]("http://ubuntuforums.org/showpost.php?p=6287536&postcount=22") I got vmware tools mostly working in my Jaunty guest on vmware server 2.0.

My main issue now is automatic screen resizing.  Has anybody got that working?  Right now the screen just stays one size unless you go in and edit xorg.conf.

---

### Post by HDave on 2009-06-11
Found the problem.  For compatibility with ESXi, I had left the machine at hardware version 4.  One click to take it up to version 7 and viola...it just worked.;)

---

### Post by HDave on 2009-06-11
Spoke too soon.  Rebooted and now its broken again.... ](*,)

---

