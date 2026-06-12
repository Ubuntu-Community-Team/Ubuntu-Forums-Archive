---
title: "CVS Rancid Gui"
date: 2008-05-12
forum: The Cafe
---

### Post by Black Mage on 2008-05-12
Does anyone know off a CVS-Rancid Gui? I've install Rancid and got it work, along with a rancid-cgi, which I haven't gotten to work yet. I'm trying to get Rancid web based.

---

### Post by dotwaffle on 2009-01-27
Probably way too late for you, but I found this through Google, so it's appropriate.

Rancid does not have a web interface for the configs. The CGI package is for running a "looking-glass" style tool. You need to install a package that shows CVS trees on the web, as alluded to in the Rancid README.

Hope that helps!

---

### Post by daveonet on 2009-01-29
We use CVSWeb and it works great.  We are running it on Solaris9, but have also used it on a linux platform.  You can download it from the following site:

[http://www.freebsd.org/projects/cvsweb.html](http://www.freebsd.org/projects/cvsweb.html)

Hope this helps!

---

### Post by pininy on 2011-05-11
Hi,

I have an issue i have trying to solve, have search the internet but no solution.

Can anyone help?

I have installed rancid, cvsweb is up 


The file

thomas@cvni-nms-01:/var/lib/rancid/singapore$ ls
configs  router.db  routers.all  routers.down  routers.up
thomas@cvni-nms-01:/var/lib/rancid/singapore$ cd configs/
thomas@cvni-nms-01:/var/lib/rancid/singapore/configs$ ls
57.6.141.36  57.6.141.49  57.6.141.50


Logs

But i just can't seems to access or see the file within the configs... 
cvs status: cannot open CVS/Entries for reading: No such file or directory
cvs status: use `cvs add' to create an entry for `57.6.141.36'
cvs add: in directory `.':
cvs [add aborted]: there is no version here; do `cvs checkout' first
cvs added missing router 57.6.141.36
cvs status: cannot open CVS/Entries for reading: No such file or directory
cvs status: use `cvs add' to create an entry for `57.6.141.49'
cvs add: in directory `.':
cvs [add aborted]: there is no version here; do `cvs checkout' first
cvs added missing router 57.6.141.49
cvs status: cannot open CVS/Entries for reading: No such file or directory
cvs status: use `cvs add' to create an entry for `57.6.141.50'
cvs add: in directory `.':
cvs [add aborted]: there is no version here; do `cvs checkout' first
cvs added missing router 57.6.141.50

---

### Post by pininy on 2011-05-18
Got it fixed via the new ver from rancid..

---

