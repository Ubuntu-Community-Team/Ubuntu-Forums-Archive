---
title: "Ubuntu Server 6.0.6.2 LTS Zoneminder 1.24.2 Install"
date: 2009-10-15
forum: Server Platforms
---

### Post by Diubidone on 2009-10-15
Hello to everyone,

I'm beeing asked for a Zoneminder 1.24.2 installation on an UBUNTU server platform 6.0.6.2 (Don't ask why please...another italian style mistery).

Anyways I bumped in a problem with gnutls libraries. When do I do .configure on zoneminder 1.24.2 the system gives this problem:

> configure: error: zm requires gnutls/openssl.h - use ZM_SSL_LIB option to select openssl instead

Whereas configure goes really fine on Zoneminder version 1.22.2.

On my system at command dpkg -l *gnutls* I get this output:

un  gnutls-bin                             
un  gnutls0                                 
un  gnutls0.4                               
un  gnutls3                                
un  libcurl3-gnutls-dev                     
ii  libgnutls12                             1.2.9-2ubuntu1.7                   the GNU TLS library - runtime library
un  libgnutls5                             

When I tried to install gnutls3 I got the message that tells me that gnutls 3 is obsolete and is substituted by libgnutls11 libgnutls12 so apparently gnutls is present.

How do I solve this issue?

PS this is very urgent!

---

### Post by yknivag on 2009-10-15
Ubuntu 6.06 (whilst being an LTS) is now a long way out of support and it is very likely that dependant packages will be out of date.

Your best option would be to upgrade to the latest LTS (8.04) and then try again.

---

### Post by ugm6hr on 2009-10-15
> **yknivag said:**
> Ubuntu 6.06 (whilst being an LTS) is now a long way out of support
Not true.  5 years = 2011 June.
> and it is very likely that dependant packages will be out of date.
Unfortunately, this statement re: modern dependencies in the repos is accurate.

---

### Post by lykwydchykyn on 2009-10-15
If I need to get newer software on an old release like this, the safest and easiest way I've found is to use apt-src with a newer source repository.

In other words, add a deb-src repository for 8.04 to your 6.06 repository list (and only src, not binary).

Then install apt-src.

Now, to get the source for a package you do:
```

apt-src install packagename

```
It will get the source code and any build-dependencies will be installed.  

Then you just do
```

sudo apt-src build -i packagename

```

If the build dependencies aren't available, you'll be told when you do "apt-src install".  In which case, you do the above for the dependencies.

Yes, it can get a bit tedious if you have to track back a lot of dependencies, but most of the time it's not bad, and it's easier than compiling from upstream source (not to mention it works with the package manager for easier uninstall).

Hope that makes sense.

---

### Post by bbiandov on 2013-02-17
> sudo apt-get install libssl-dev 

Did it for me, no more error on ./configure

---

### Post by Bucky Ball on 2013-02-17
[I][B]Thread Closed

Reason:[/B][/I] Necromancy. Old thread put to eternal sleep.

This thread has been inactive for nearly three and a half years. Please do not resurrect old threads (inactive for a year or more). Thanks.

---

