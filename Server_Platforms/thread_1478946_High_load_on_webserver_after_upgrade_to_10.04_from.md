---
title: "High load on webserver after upgrade to 10.04 from 9.10"
date: 2010-05-10
forum: Server Platforms
---

### Post by masterdead on 2010-05-10
Hi, 

I upgraded webserver to new ubuntu server 10.04 (x86-64).  After upgrade the increased load from 0,3 to 1,4. On webserver running phpbb, which generating slow quieres, which not before upgrade to lucid.

HW conf: Intel Core i7, 8GB ram, WD Raptor 10k rpm.

Week17 upgrade to new version.

---

### Post by arrrghhh on 2010-05-10
Did you happen to notice any process stealing more processor time than usual?

---

### Post by masterdead on 2010-05-12
No, all processes in normal. Only load increased. Cpu usage in normal, maybe few percent up....

---

### Post by JPorter on 2010-05-12
This is very interesting... I may hold off updating our boxes to 10.04 if this is at all common.

Can anyone else report their own experience?

---

### Post by arrrghhh on 2010-05-12
I haven't noticed any spikes or high utilzation in 10.04.  I run apache2, php, mysql, and a ton of other crap.

However, I wouldn't put a 'production' server on 10.04 yet.  I'd wait at the very least until the .1 gets added.  8.04.3 is still completely supported on the server, and will continue to be for 3 more years I believe.

---

### Post by windependence on 2010-05-12
> **arrrghhh said:**
> I haven't noticed any spikes or high utilzation in 10.04.  I run apache2, php, mysql, and a ton of other crap.

However, I wouldn't put a 'production' server on 10.04 yet.  I'd wait at the very least until the .1 gets added.  8.04.3 is still completely supported on the server, and will continue to be for 3 more years I believe.
I'll second this 100%. Latest and greatest isn't always the best. 10.4 is really buggy IMHO, and I would wait a good 3-6 months to even think about an upgrade. Also, if you don't NEED any of the specific features of the new version, why upgrade? Cause it's "cool" or everybody else is doing it? Not if you run something that has to be up all the time.

-Tim

---

### Post by masterdead on 2010-06-04
If you are using eAccelerator and PHP installed with apt, few days back releases new version of eAccelerator (0.9.6.1). Version 0.9.6 causes more problems and load on webserver.

---

### Post by JPorter on 2010-06-13
> **windependence said:**
> I'll second this 100%. Latest and greatest isn't always the best. 10.4 is really buggy IMHO, and I would wait a good 3-6 months to even think about an upgrade. Also, if you don't NEED any of the specific features of the new version, why upgrade? Cause it's "cool" or everybody else is doing it? Not if you run something that has to be up all the time.

-Tim

For the servers we're running, which are brand new, the default kernel in Karmic doesn't have full support for the CPU's power management features (new Nehalem Xeon with QPI and "Turbo Boost").  The newer kernel in Lucid does, I believe.

Have there been any updates on the issues raised in this thread yet?  Did it turn out to be an issue with eAccelerator, or not?

---

### Post by masterdead on 2010-06-23
Load decrease after upgrade kernel to latest version from this:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I am use kernel 2.6.35rc1. Current load is still on 0.2 :)

Ubuntu kernel 2.6.32-22-server is bad...

---

### Post by arrrghhh on 2010-06-23
> **masterdead said:**
> Load decrease after upgrade kernel to latest version from this:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I am use kernel 2.6.35rc1. Current load is still on 0.2 :)

Ubuntu kernel 2.6.32-22-server is bad...

I think my statement about production earlier rings true here...  However, is anyone else having issues with this kernel?  I unfortunately installed the 32-bit version of Ubuntu on my server, so I run the generic-pae kernel instead of the so-called 'server' kernel...

---

### Post by pschroth on 2010-07-06
I had the same behavior on my laptop and another desktop.

---

### Post by JPorter on 2010-07-06
Any news on the root cause of the high load issue?  Or what was changed in the updated kernels that fixes it?

Has anyone tried an updated "server" kernel to see if the problem persists there?

---

### Post by JeshurunDaniel on 2010-08-14
I've installed 10.04 on my home server and have the same issues. The load is always around 0.1 - 0.2 although I know there is nothing hitting my server. I'm running apache/mysql/php and also an instance of tomcat. Any suggestions on fixing this is much appreciated.

---

