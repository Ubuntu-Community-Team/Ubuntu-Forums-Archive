---
title: "Ubuntu server 10.04 OTRS instll problem"
date: 2012-02-05
forum: Server Platforms
---

### Post by deepakdeshp on 2012-02-05
First I ran 
#apt-get  update
#apt-get upgrade

I was installing OTRS on Ubuntu server 10,04 with 
#apt-get install otrs2

It threw some error which I did not note down and I ma not able to launch OTRS from the browser.
The error message in /var/www/dpkg.log is **status half-configured otrs2 2.4.7-1ubuntu0.1**

Any suggestions please.

---

### Post by deepakdeshp on 2012-02-07
I just removed the package completely with dpkg -P and resinstalled the package from the tar ball and it is working now.

Is it an error that the #apt-get install otrs2 doesnt work ? Is the package untested?

---

