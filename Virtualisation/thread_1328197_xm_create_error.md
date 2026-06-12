---
title: "xm create error"
date: 2009-11-16
forum: Virtualisation
---

### Post by tapas_mishra on 2009-11-16
root@abhitech-desktop:/etc/xen# xm create /etc/xen/mydomU.cfg
Using config file "/etc/xen/mydomU.cfg".
Error: I need 526336 KiB, but dom0_min_mem is 200704 and shrinking to
200704 KiB would leave only 304392 KiB free.

What does that error means and how can I get rid of it,

---

### Post by aprigiosimoes on 2009-11-16
you xend daemon is running??

#xend status
#/etc/init.d/xend restart

#xm list

---

### Post by tapas_mishra on 2009-11-16
> **aprigiosimoes said:**
> you xend daemon is running??

#xend status
#/etc/init.d/xend restart

#xm list

root@desktop:~# xend status
root@desktop:~# /etc/init.d/xend status
root@desktop:~# xm list
Name                                        ID   Mem VCPUs      State   Time(s)
Domain-0                                     0   364     1     r-----   1397.0
mydomU                                       1   128     1     -b----      9.7

I changed the installation command replacing 512 MB with 128 MB in xm-create command and above are the output of
#xend status 
no thing else is produced
on the other tab the following output is there 


All done
root Started new Xen guest: mydomU [/etc/xen/mydomU.cfg]


Logfile produced at:
     /var/log/xen-tools/mydomU.log


but the machine has hanged from past 1 hour after this so no idea what else should I check

---

