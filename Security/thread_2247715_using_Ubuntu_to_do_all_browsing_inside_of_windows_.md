---
title: "using Ubuntu to do all browsing inside of windows via VM"
date: 2014-10-09
forum: Security
---

### Post by eival on 2014-10-09
if you keep all shared folder access disabled how safe would this be?

is there any chance of something windows related being effected or would the VDI keep everything contained and unless its linux specific i could use a windows machine safely

P.S., doing this the other way around isnt feasible as the only reason im going to use windows is for gaming

just wondering if this has actually been tested

---

### Post by TheFu on 2014-10-10
The method above has been used millions of times around the world for years.

If you don't connect the VM to anything on Windows (no shared folders) then the risks are minimal on a secure network. Of course, Linux systems are not completely safe everywhere on the internet and we still need to be careful with flash, pdfs, java applets and javascript just like on every other platform.

If you want to be secure for online banking, I'd still use a non-writeable ISO booted inside a VM, not a general purpose distro.  [http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/](http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/) explains from a highly reputable source.

You know - some people do use KVM or Xen on their hostOS and get VGA passthru to work for a Windows VM to get native GPU performance. There's a thread going on in the virtualization forum here about that. It is still non-trivial, but seems possible if the correct hardware is used.  I've never tried - don't have the right hardware myself.

---

