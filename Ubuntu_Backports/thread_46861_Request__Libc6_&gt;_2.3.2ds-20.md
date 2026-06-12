---
title: "Request : Libc6 &gt; 2.3.2ds-20"
date: 2005-07-06
forum: Ubuntu Backports
---

### Post by Dafatfab on 2005-07-06
Hello,

I've read the guidelines but I even do my request about the famous problem with the actual libc6 2.3.2.ds1-20ubuntu13.

More and more multimedia applications (for exemple marillat packages) are request a libc6 >= 2.3.2.ds1-21...

The Breezy branch have a 2.3.5 libc6 so, no problem for the future version and I know that libc6 cause dependances problems with locales...

So, is there any chance that a libc6 >= 2.3.2.ds1-21 can be backported ?


Thanks a lot !

*An Ubuntu French user*  [-o<

---

### Post by man.life on 2005-07-06
That would mean recompiling all the packages...  :roll: 

You don't need Marillat, everything is in Hoary, backports and extras repos.

---

### Post by Dafatfab on 2005-07-07
Ok, thanks for the answer.
So, this package is too major for expecting a backport... no problem ! :grin:

---

### Post by SpEcIeS on 2005-07-07
Try adding this to your sources list

deb [http://demudi.agnula.org/packages/demudi](http://demudi.agnula.org/packages/demudi) testing main

It may have what you are looking for. :)

---

### Post by Dafatfab on 2005-07-08
Thanks for the link...I will try it. O:) 

But, I don't want too much play with libc6.... [-X

---

### Post by Mez on 2005-07-08
put simply, if you change the libc6 to a newer version, everything that depends on it will need a recompile... which is most of ubuntu.

Hence why there's so many changes for breezy ;)

---

### Post by SpEcIeS on 2005-07-08
[QUOTE=Mez]put simply, if you change the libc6 to a newer version, everything that depends on it will need a recompile... which is most of ubuntu.

Hence why there's so many changes for breezy ;)[/QUOTE]
I can definatly understand the concern, however the upgrade that was perfomed on my sysetm was a simple **libc6 2.3.2-20ubuntu13** *->* **libc6 2.3.2-22demudi1**. Updating this library has allowed me to use some other updates that required the ***libc6 2.3.2-21*** in order to install without complaints. Broken dependencies are sometimes not a large issue, but when they pop-up it drives me mad. :) 

One example is clamtk 2.02, it depends on 0.8.6 clamav, but I have 0.8.5. After installing the deb package, complaints regarding broken dependencies. Since clamtk is as it says, tk, I downloaded the source and boom it works normally, as it did prior, but no dependency complaints.  ;-) 

Sometimes, it would seem, it is better to compile and install from source.

---

### Post by janit on 2005-08-11
[QUOTE=SpEcIeS]Try adding this to your sources list

deb [http://demudi.agnula.org/packages/demudi](http://demudi.agnula.org/packages/demudi) testing main

It may have what you are looking for. :)[/QUOTE]

Hallelujah! Handbrake installing from Debian package :)

---

### Post by thomax on 2005-09-16
Okay, great, it works :) Thanx alot  \\:D/

---

### Post by Brando569 on 2005-10-02
im trying to install superkaramba from a deb but it needs libc6-2.3.2.ds1-21. is there a work around for this or should A) wait until breezy is stable or B) use superkaramba v0.36?

---

### Post by trinaryouroboros on 2005-11-07
[QUOTE=thomax]Okay, great, it works :) Thanx alot  \\:D/[/QUOTE]

Will anyone ever support 64-bit?! :cry: 

> [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-amd64/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-amd64/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-amd64/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-amd64/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-amd64/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-amd64/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-amd64/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-amd64/Packages.gz:) 404 Not Found
[http://demudi.agnula.org/packages/demudi/dists/testing/main/binary-amd64/Packages.gz:](http://demudi.agnula.org/packages/demudi/dists/testing/main/binary-amd64/Packages.gz:) 404 Not Found
[ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-amd64/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-amd64/Packages.gz:) Unable to fetch file, server said 'Can't open /debian-marillat/dists/stable/main/binary-amd64/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
[ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-amd64/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-amd64/Packages.gz:) Unable to fetch file, server said 'Can't open /debian-marillat/dists/unstable/main/binary-amd64/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
[ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-amd64/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-amd64/Packages.gz:) Unable to fetch file, server said 'Can't open /debian-marillat/dists/testing/main/binary-amd64/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]

---

### Post by jdong on 2005-11-09
You're using **old and unsupported** backports -- see the sticky in the forum for the new URL.


Backports fully supports AMD64 and PPC.

---

