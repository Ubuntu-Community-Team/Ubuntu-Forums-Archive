---
title: "centos and chkconfig runlevels"
date: 2012-08-22
forum: Server Platforms
---

### Post by poolet on 2012-08-22
Well, I am trying to figure out how to configure all process in a centos dedicate server which is running as hosting.. All I want is to set all process to startup after a restart or shutdown automatically... I made a re-search and find out that, the most commond used is chkconfig which you must be very carefully what you're doing..!!! I also notice that the most usual configuration of chkconfig is -3-4-5- but I really don't get a general concept of what this numbers means..!! Any kind of article has not a detailed information about the --levels-- so, I am asking if someone knows something more than me please let me know!! Again, all I want is to be able to auto-start any process after a restart or after a shutdown of the server!!

Thank you!!!

---

### Post by SeijiSensei on 2012-08-22
Just use "chkconfig service_name on" (as root) to have service_name start at boot.  There are dozens and dozens of services in /etc/init.d/.  You should only activate those you know you really need.

The numbers refer to "[run levels.]("http://www.centos.org/docs/5/html/Installation_Guide-en-US/s1-boot-init-shutdown-sysv.html")"  RedHat-flavored machines use run level 3 for full, multiuser mode with text output; run level 5 adds support for X windows and the graphical user interface.

Ubuntu has [fewer]("http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html") run levels and does not make the distinction between text and graphics mode.

---

