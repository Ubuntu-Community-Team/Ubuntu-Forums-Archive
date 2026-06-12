---
title: "XEN incorrect time (one hour to late)"
date: 2008-03-10
forum: Virtualisation
---

### Post by frenkel on 2008-03-10
I'm hiring a XEN virtual machine at a hosting company. My XEN virtual machine is hosted on a server which has some other VM's running on it. They all use ubuntu or debian. After a crash sometime last week, the systemclock of my VM is off by an hour (it says 17:05, although it's 16:05 here now). The other VM's don't have this problem, and according to the admin of the server, the server clock is running correctly and my XEN config is correct also.

I checked everything. Timezone is correct (in /etc/timezone), the localtime symlink is correct (/etc/localtime). UTC=yes in /etc/defaults/rcS, although changing it to no doesn't make a difference.

The admin of the server fixed it temporally by running:
echo 1 > /proc/sys/xen/independent_wallclock
And setting the date/time manually. Every hour the time is now set through ntpdate.

Does anybody know what's wrong with the vm? How can I fix this?

Frank

---

### Post by homegrown on 2008-03-10
Sounds like  the clock on the host machine is out or maybe in a different timezone. 
Either way you should configure your machine to use a ntp client & point it to a trusted source.

---

### Post by frenkel on 2008-03-10
As I posted in my original post, the clock of the server is running correctly and the other VM's don't have any problems.

---

