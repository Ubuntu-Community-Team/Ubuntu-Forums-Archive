---
title: "Deprecated packages in 8.04LTS"
date: 2010-02-23
forum: Server Platforms
---

### Post by rsp2010 on 2010-02-23
When do deprecated packages in an LTS version get replaced with currently-supported packages, such as is the case with samba 3.0 presently in 8.04 LTS?

---

### Post by scottuss on 2010-02-23
They don't, unless it fixes bugs. An LTS is Long Term Release which means it needs to be stable for the length of it's life.

This means not upgrading packages that would cause the OS to become unstable by introducing potential new bugs, being that 8.04 LTS is very stable (generally), it will not receive newer versions of packages. This will be the same for 10.04.

---

### Post by slakkie on 2010-02-23
They won't, unless you create the package and offer it as a backport (or via a ppa).

---

### Post by rsp2010 on 2010-02-23
If a package version is deprecated, it cannot be considered stable because nobody would be able to identify & fix bugs or other issues. Therefore it is logical that deprecated versions should be upgraded to ones that have mainstream support.

---

### Post by scottuss on 2010-02-23
> **rsp2010 said:**
> If a package version is deprecated, it cannot be considered stable because nobody would be able to identify & fix bugs or other issues. Therefore it is logical that deprecated versions should be upgraded to ones that have mainstream support.

Technically incorrect. The packages in the LTS are supposedly at a point where the bugs in their respective versions are minimal and will not impede the system. Also, bug fixing does happen to these packages, they just don't get new features. Most of the fixes I have received on my 8.04 LTS laptop are security fixes and major bug fixes. The only real major updates came from the 8.04.4 release not so long ago

---

### Post by snowpine on 2010-02-23
Ubuntu 8.04 = April 2008 and will never have newer software than that.

Red Hat Enterprise Linux uses samba 3.0 too, and it is used on many mission-critical servers.

That's the beauty of Linux, though. You can easily install a newer samba on your Ubuntu 8.04, or upgrade to a later release/different distro that gives you what you need.

---

### Post by OrangeCrate on 2010-02-23
You can find a summary of what's in each Ubuntu release here:

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by rsp2010 on 2010-02-23
Apologies, there is conflicting information on the Samba site regarding the availability of patches; the FAQ says it's maintained for bug and security fixes, but the release notes for 3.0.27 say it is no longer maintained and therefore fixes will not be forthcoming.
 
If a package is no longer maintained, then the distribution maintainers who have committed to a long term support must either pick up the package themselves, or replace it. Otherwise a distribution can not be considered "supported".

---

### Post by snowpine on 2010-02-23
> **rsp2010 said:**
> Apologies, there is conflicting information on the Samba site regarding the availability of patches; the FAQ says it's maintained for bug and security fixes, but the release notes for 3.0.27 say it is no longer maintained and therefore fixes will not be forthcoming.
 
If a package is no longer maintained, then the distribution maintainers who have committed to a long term support must either pick up the package themselves, or replace it. Otherwise a distribution can not be considered "supported".

All "stable" Linux distributions (Ubuntu LTS, Debian, Red Hat, etc.) run into this problem eventually. [Here's a link ]("http://www.redhat.com/security/updates/backporting/?sc_cid=3093")that will shed more light on the issue. (It's from the Red Hat documentation, but the same principle applies to Ubuntu as well.)

As I mentioned above, there is absolutely nothing preventing you from installing a newer version of samba on your Ubuntu system. You will never get the update automatically due to Ubuntu policy.

---

### Post by rsp2010 on 2010-02-23
@snowpine, great explanation, thanks.
 
Effectively a package is maintained by the distribution providers, if I read it correctly, no matter what its own maintainers have set as its status.

---

