---
title: "vboxwebsrc seg fault after upgrading to Ubuntu 13.10"
date: 2014-02-09
forum: Virtualisation
---

### Post by sumpi2 on 2014-02-09
Hi all!

After upgrading my ubuntu host yesterday, I am no longer able to log into my phpvirtualbox as it says, that it can not connect to the host. After searching the web, I found out, that there is a problem with the vboxwebsrv and it was no longer running on my host. So I tried to start the service from the commandline. 
When I open a commandline and start the vboxwebsrv service manually, I get this error:
[FONT=courier new]sumpi@foo:~$ vboxwebsrv -H 127.0.0.1
Oracle VM VirtualBox web service Version 4.2.16_Ubuntu
(C) 2007-2013 Oracle Corporation
All rights reserved.
VirtualBox web service 4.2.16_Ubuntu r86992 linux.amd64 (Sep 21 2013 11:46:57) release log
00:00:00.017616 main     Log opened 2014-02-09T07:11:12.179733000Z
00:00:00.017626 main     OS Product: Linux
00:00:00.017628 main     OS Release: 3.11.0-15-generic
00:00:00.017630 main     OS Version: #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014
00:00:00.017674 main     DMI Product Name: 965QM-DS2
00:00:00.017692 main     DMI Product Version:
00:00:00.017799 main     Host RAM: 1984MB total, 641MB available
00:00:00.017807 main     Executable: /usr/lib/virtualbox/vboxwebsrv
00:00:00.017808 main     Process ID: 6608
00:00:00.017810 main     Package type: LINUX_64BITS_GENERIC (OSE)
00:00:00.197387 SQPmp    #### SOAP FAULT:  [SOAP-ENV:Server]
Speicherzugriffsfehler (Speicherabzug geschrieben)
[/FONT]Which means, a segfault occured.

So where should I go from here? Do I need to reinstall something, which was broken during upgrade?

Thanks in advance for any help!

BR,
Sumpi

---

### Post by ketaj27 on 2014-02-09
Hello Sumpi,

I've run into this same problem today after updating to release 3.11.0-15-generic.  I haven't figured out how to resolve this yet.  I've found this post which seems to be related:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1254071]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1254071") 

Hoping someone can help us out with this.

Toby

**** Message when starting vboxwebsrv ****
toby@4LBd6k1:~$ vboxwebsrv -H 127.0.0.1
Oracle VM VirtualBox web service Version 4.2.16_Ubuntu
(C) 2007-2013 Oracle Corporation
All rights reserved.
VirtualBox web service 4.2.16_Ubuntu r86992 linux.amd64 (Sep 21 2013 11:46:57) release log
00:00:00.003941 main     Log opened 2014-02-10T01:52:38.325369000Z
00:00:00.003950 main     OS Product: Linux
00:00:00.003951 main     OS Release: 3.11.0-15-generic
00:00:00.003952 main     OS Version: #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014
00:00:00.003996 main     DMI Product Name: OptiPlex 760
00:00:00.004007 main     DMI Product Version:
00:00:00.004102 main     Host RAM: 3791MB total, 3483MB available
00:00:00.004107 main     Executable: /usr/lib/virtualbox/vboxwebsrv
00:00:00.004107 main     Process ID: 16323
00:00:00.004108 main     Package type: LINUX_64BITS_GENERIC (OSE)
00:00:00.270389 SQPmp    #### SOAP FAULT:  [SOAP-ENV:Server]
Segmentation fault (core dumped)

*****  Release Information ********
toby@4LBd6k1:~$ uname -r
3.11.0-15-generic

---

### Post by sumpi2 on 2014-02-11
Hi Toby!

Yeah, looks like it is the same or at least an related issue. Hopefully, someone will help us with this!

Bye,
Sumpi

---

