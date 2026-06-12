---
title: "VMWare Server 2 stopped working with 'loading' message"
date: 2009-05-15
forum: Virtualisation
---

### Post by bernie888 on 2009-05-15
hi there

I've been happily using VMWare Server 2.0 on Ubuntu 8.10 Desktop for several months.
All of a sudden VMWare stopped working today after I booted up.
It just hangs on the webpage when trying to bring up Insfrastructue Web Access. So I can't load any VMs or do anything.
Could this have been caused by a Ubuntu package update? I've never had this problem before and dont really know where to begin troubleshooting.
Any help would be very much appreciated as I have a whole network of VMs built and can't work on any of them currently.

---

### Post by whoop on 2009-05-15
Maybe you upgraded your kernel or something?

Try running vmware-config.pl

---

### Post by bernie888 on 2009-05-15
holy smoke, yep, looks like Ubuntu updated to a new kernel on the last reboot. Wonder if there is a way of switching that off? I didnt choose it to do that.
Anyway, I went back and booted from the old kernel from the bootloader menu but still same problem.

But now its working!! 
:o)

As Whoop suggested i needed to re-run:
/usr/bin/vmware-config.pl

Accepted the defaults pretty much and now I can login again.
thanks for your help!!

---

### Post by whoop on 2009-05-15
> **bernie888 said:**
> holy smoke, yep, looks like Ubuntu updated to a new kernel on the last reboot. Wonder if there is a way of switching that off? I didnt choose it to do that.
thanks for your help!!
Do you have automatic updating enabled in software sources?

---

### Post by VirtualEntity on 2009-06-20
> **bernie888 said:**
> holy smoke, yep, looks like Ubuntu updated to a new kernel on the last reboot. Wonder if there is a way of switching that off? I didnt choose it to do that.
Anyway, I went back and booted from the old kernel from the bootloader menu but still same problem.

But now its working!! 
:o)

As Whoop suggested i needed to re-run:
/usr/bin/vmware-config.pl

Accepted the defaults pretty much and now I can login again.
thanks for your help!!

For what it is worth, the symptoms you experienced can result from two different problems.  First is the need to re-run vmware-config.pl to configure VM to the new kernel.

The other is more insidious, where a perfectly good VMware installation suddenly decides to simply display a blank page in your web-browser instead of the usual Login screen.  If you have multiple tabs open, you may see the caption "Loading..." in the tab, but nothing ever loads.  This is a flaw in the design of VMware webAccess (or something that your web browser (notably Firefox, but also happens with MS Internet Exploder), wherein some compressed files (.wbc.js and .jslib.js) do not uncompress properly (if at all) and, well, basically the whole thing hangs on load.  Usually removing and reinstalling the certificate for your client in VMware will sort this problem.  (No idea why...).  Also, you will need to clean your web-page cache before doing the certificate remove/replace.  You may also need to execute "/etc/init.d/vmware-mgmt restart" (on Linux systems).  This last may help.  Usually the cache-clean and certificate reinstall does the trick.....

---

### Post by HermanAB on 2009-06-20
Howdy,

Two recommendations from my own experience:
a. Avoid using Vmware 2.X.  It is too buggy. Maybe next year.
b. turn off auto-update on the host system, else things can break and you may only notice it long after and then you have no idea what the heck happened.

---

### Post by zmartant on 2010-02-12
No kernel upgrade for me!  When I tried accessing the VM via Windows IE 8, I was able to login.  When I went back to my Ubuntu 9.10 box, Firefox 3.5.7, still received the Loading..... blank screen.  I cleared the cache, still the same.  I cleared the cookies, BAM!  I got the login and password screen.  So, I believe the cookies have to be cleared when one gets this type of issue!  If I get the same issue again, I will varify my hypothesis. ;)
--
Zmartant

---

