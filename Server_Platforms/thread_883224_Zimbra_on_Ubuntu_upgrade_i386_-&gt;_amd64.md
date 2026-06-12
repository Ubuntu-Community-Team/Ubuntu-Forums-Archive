---
title: "Zimbra on Ubuntu upgrade i386 -&gt; amd64"
date: 2008-08-07
forum: Server Platforms
---

### Post by brianfinley on 2008-08-07
I am using Zimbra on Ubuntu i386, but want to upgrade to Ubuntu amd64.  There is currently a complicated procedure for doing this, but it could be really easy.  If you also want to do this, or even upgrade to Ubuntu amd64 from another i386 Linux distro, consider voting for this feature improvement on the Zimbra site:

[http://bugzilla.zimbra.com/show_bug.cgi?id=29297](http://bugzilla.zimbra.com/show_bug.cgi?id=29297)

---

### Post by windependence on 2008-08-08
As far as I know 64 bit is not supported or recommended by Zimbra. It's also probably not necessary. Many people want 64 bit because it's "
cool" or the latest and greatest but 64 bit can actually be SLOWER than 32 bit depending on the application. If you were rendering graphics I would say sure but for e-mail, I really don't think it's necessary.

-Tim

---

### Post by brianfinley on 2008-08-11
Tim,

I appreciate your comments, but Zimbra does support 64bit, and it is recommended:

[http://wiki.zimbra.com/index.php?title=Performance_Tuning_Guidelines_for_Large_Deployments#RAM_and_CPU](http://wiki.zimbra.com/index.php?title=Performance_Tuning_Guidelines_for_Large_Deployments#RAM_and_CPU)

---

### Post by windependence on 2008-08-11
> Almost all recent 'x86' server CPUs support installing a 32-bit/i686 version of Linux or a 64-bit/x86_64 version. We strongly recommend installing the 64-bit version if you have more than 4GB of RAM. If you have 4GB of RAM or less, **it is unclear that the 64-bit version will boost performance**, but you shouldn't really be running a large install on a system with < 8GB of RAM. If you anticipate adding more RAM in the near future during a maintenance window, do install the 64-bit version now - upgrade from 32-bit to 64-bit is possible, but a lot of work. 

Thanks this is great news. Less than a year ago they were saying you should only run it on 32 bit OS. Note the bold section though. Don't expect a performance gain, but if you want to run more than 4GB RAM, you sure don't want to be running PAE.

Also note that they recommend you don't try to run anything else on the box because so many things are customized for Zimbra and may confilct with it. Trust me from experience, they are correct. ;)

-Tim

---

### Post by brianfinley on 2008-08-11
We are currently running with 16GB (w/PAE -- possible, but not ideal), in anticipation of upgrading to 64bit, and it's been interesting to configure JVM and innodb buffer cache sizes correctly.  For these very reasons, they also say, "If you anticipate adding more RAM in the near future during a maintenance window, do install the 64-bit version now - upgrade from 32-bit to 64-bit is possible, but a lot of work.".  

But alas, we had been running on 32bit for over a year prior to the 64bit version being available on Ubuntu.

Cheers, -Brian

---

### Post by windependence on 2008-08-11
Well moving from 32 bit to 64 bit is extemely painful. It definitely is better to start off with 64 bit if that's the way you are going but unfortunately in your case you have no choice. Good luck. If I can help at all just ask.

-Tim

---

