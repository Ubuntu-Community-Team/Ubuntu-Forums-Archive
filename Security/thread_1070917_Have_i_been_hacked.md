---
title: "Have i been hacked?"
date: 2009-02-15
forum: Security
---

### Post by MasterNetra on 2009-02-15
I was wondering how do i change a file's mode? I don't know how but most of my files in the main directory got switched over to my admin account as owner? I never changed the ownership of these folders are they by default set to the ownership to your first account or is there any reason the system by itself would do this to the files by itself? Also when i try to sudo this stuff back to root (or sudo period) i get a error message saying the sudoer file in /etc needs to be set to mode 0440? Thus the reason i wish to know how to change a files mode. I suspect though I may of been hacked. Just in case i DC-ed my Internet connection, changed my password and created a user account from which I'm using atm.

---

### Post by MasterNetra on 2009-02-15
... Well not sure still how all the folders turn to admin control from root. (which included the sudoer file) and thinks to some article i read while on my user account i learned i need to restart, go into recovery moder, use the root shell and change the ownership of the entire etc folder "chown -R root:root /etc/" which did the trick. After restarting i logged into my admin account (which isn't called admin fyi) and sure enough i gots sudo control back. :) I changed the entire main area back to root control. "chown root /*" Hopefully I'm all good now :)...Although i still wonder if i was hacked :/

---

### Post by shad0w_crash on 2009-03-11
> **MasterNetra said:**
> w :)...Although i still wonder if i was hacked :/

Well you could check the integrity of your files for rootkids (use rootkit hunter).

If you're afraid the'll come back you could install OSSEC (HIDS):

[http://www.ossec.net/](http://www.ossec.net/)

and monitor the logfiles for a while!

---

### Post by bodhi.zazen on 2009-03-11
+1 ossec ;)

---

