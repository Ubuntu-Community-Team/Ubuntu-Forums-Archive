---
title: "KMyMoney2 and OFX Direct Connect support"
date: 2006-10-31
forum: Repositories &amp; Backports
---

### Post by cornlegend on 2006-10-31
I'm running Edgy dist-upgraded from Dapper, and I'm running into this problem with a properly configured OFX Direct Connect account in KMyMoney2 0.8.4...

Unable to import <b>OFX</b> file. There is no such plugin loaded.

As far as I can tell, all pre-requisite packages for OFX Direct Connect support are installed.  Does anyone have some advice?

I've even tried compiliing the package from source to verify that OFX Direct Connect support is in fact enabled, and it is...  and I installed all dependencies too.

](*,)

---

### Post by cornlegend on 2006-11-02
I reinstalled Dapper.. the KMyMoney2 package on Edgy is very broken.  None of the online banking plugins work there..

I got the plugins mostly working on Dapper, now I'm stuck trying to get it to download my account statements.. :-k  Anyone out there with Veridian Credit Union that has OFX Direct Connect working?

---

### Post by Blutack on 2006-11-03
Pull down the latest version from below.  It was built for dapper but it works great.  Has anyone filed a bug report?
[http://ubuntu-debs.de/downloads/dapper-drake/32bit/office/](http://ubuntu-debs.de/downloads/dapper-drake/32bit/office/)
EDIT!  this crashes on importing OFX.  If you get it working let me know how!

---

### Post by S.nazari on 2007-01-30
The link that you have given above doesn't work. 
There is only a link to a page that has another link to the sourceforge package or kmymoney2.
None of these packages can be installed on ubuntu because they for for debian. I tried and couldn't I keep getting the dependency problems with libkde4 and I tried to resolve but none of the libs were in the edgy repositories made by source-o-matic nore the backports.  
So your link is useless.
The best thing I have done is to make a package with ofx support and to host it myself. 
I tried to enable the kbanking but I got an error on make which is probebly why the package in edgy is still old.
So I have only been able to compile and package it with ofx and direct ofx I think. 
Here is the link. 
[www.alborz.uk.com/kmymoney2_0.8.5-1_i386.deb]("www.alborz.uk.com/kmymoney2_0.8.5-1_i386.deb") Please remember that this is my privet hosting. 
Please let me know if we could add this to the back port.

---

### Post by hikaricore on 2007-01-30
Thanks for posting your edgy package :)  this is really handy software to have.

---

### Post by jrogers360 on 2007-03-11
your link (to the custom .deb) no longer works (404).

---

### Post by msak007 on 2007-03-11
> **cornlegend said:**
> I'm running Edgy dist-upgraded from Dapper, and I'm running into this problem with a properly configured OFX Direct Connect account in KMyMoney2 0.8.4...

Unable to import <b>OFX</b> file. There is no such plugin loaded.

As far as I can tell, all pre-requisite packages for OFX Direct Connect support are installed.  Does anyone have some advice?

I've even tried compiliing the package from source to verify that OFX Direct Connect support is in fact enabled, and it is...  and I installed all dependencies too.

](*,)
Did you compile only KMyMoney from source? Or aqbanking as well? Aqbanking is actually what provides the OFX DirectConnect backend to connect to your bank. Simply compiling KMyMoney with the capability of using DirectConnect won't enable it if the backend wasn't compiled with aqbanking to begin with. Unfortunately, the version in the repos never has this option compiled. You can verify this by going to the Online Banking setup and check for the Backends section - you almost certainly won't find one called "aqofxbanking", which is what's required. I always end up having to compile KMyMoney, aqbanking, and gwenwhyfar from source to get this option enabled.

---

