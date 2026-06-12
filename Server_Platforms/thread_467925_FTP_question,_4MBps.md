---
title: "FTP question, 4MBps"
date: 2007-06-08
forum: Server Platforms
---

### Post by jonasx5 on 2007-06-08
Alright, so I installed proftpd and it worked perfectly and was transfering between my 2 computers at 10-12MBps, however after installing apache2 and php5 the speed went down to 4MBps and I can't find the reason to this.

So is there a way to get the speed back to max?

Thanks in Advance // Jonas

---

### Post by Mr. C. on 2007-06-08
This shouldn't be the case in general.

Try shutting down the apache service to see if that has any impact.  It is possible that you may have reached your RAM limitations and are swapping.

It is also possible that either of those installations installed a shared library that is used by your ftp server, but has some incompatibility/bug.

MrC

---

### Post by jonasx5 on 2007-06-08
stopping apache2 didnt work, and I have 1,5GB of RAM, I wouldnt think that was it.

And is there any way to know if it has some shared libs?

---

### Post by Mr. C. on 2007-06-08
Ok, it does not seem related to the running of apache, or swapping issues.

Well, I can think of several choices:

You can reinstall (or update) your FTP server software to see if that helps
You can run dpkg -c on each of the packages you believe have caused the conflict and look for different versions of the same.
You can examine the shared libraries in use using ldd (eg. ldd /bin/ls shows you the shared libraries used by the ls program), and check the modification dates.

Other than those, I'm not sure how else to help.  Ultimately, it will boil down to having to uninstall or reinstall some component.

Without knowing more about how things were installed and configured, its all speculation.

Sorry,
MrC

---

### Post by jonasx5 on 2007-06-08
Alright,

I have installed:
proftpd (from atp-get, newest version)
Everything worked, transfered in 12mBps
apache2 & php5 (from apt-get)
Then the problems came,

So there must be something with apache2/php5

I know this is probably impossible to find out, so if you have no idea its ok.

Thanks anyways, any ideas are welcome, but if you dont know, its also just fine :\

---

### Post by Mr. C. on 2007-06-08
Something just occurred to me.  It might be that IPv6 is causing some troubles since your installation, but I haven't thought through exactly why or how.  It won't hurt to try disabling IPv6 globally.

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

MrC

---

