---
title: "does ubuntu support rpm?"
date: 2006-08-07
forum: Server Platforms
---

### Post by newsci on 2006-08-07
I know some companies who provide their software for linux only in rpm packages. does ubuntu support rpm? all I need is a basic support for it, so I can install any software packages (with the --force option because of not satisfied dependencies) that come in rpm.

---

### Post by kaffelars on 2006-08-07
Ubuntu does not support RPMs.
However, it's easy to convert packages from RPM to DEB, and the converted DEBs usually work well :)

Try this:
**sudo apt-get install alien** 
(install the Alien-program that is used to convert from RPM to DEB.)

**sudo alien -d <packagename>.rpm**
(use the RPM to create a DEB)

**sudo dpkg -i <packagename>.deb**

Good luck :)

---

### Post by louis_nichols on 2006-08-07
rpm's can't be used directly in any deb-based distro, as is the case the other way around, but there is an application, called alien that converts rpm's to debs (and vice-versa, I think). it's in the repos.

Still, this doesn't guarantee the resulted package will work, but it's worth trying.

---

### Post by lamego on 2006-08-07
> Ubuntu does not support RPMs.
However, it's easy to convert packages from RPM to DEB, and the converted DEBs usually work well

The RPMs do assume you have a RedHat based distro, even if you do convert packages you may get into troubles because they assume you are using RH libraries and pathes, whenever possible it is preferable to compile from the sources or use generic linux binaries instead of converting from the RPMs.

---

### Post by kaffelars on 2006-08-08
I'm sure you're right in that compiling yourself is the best alternative, but I still think converting from RPM is worth a try, as it should be easier if you're not used to resolving the dependencies manually.

This is also based on my own experience, I've done it with a few packages and most of them works :)

---

### Post by louis_nichols on 2006-08-08
> **kaffelars said:**
> I'm sure you're right in that compiling yourself is the best alternative, but I still think converting from RPM is worth a try, as it should be easier if you're not used to resolving the dependencies manually.

This is also based on my own experience, I've done it with a few packages and most of them works :)

actually... alien-ating a package doesn't import any information about dependencies. that would be very difficult, because of various package naming conventions. you might still end up searching for the right dependencies to install. The only difference is you'll be searching for binaries insteda of devel packages. I agree it's worth trying, though.

I'd say that about 70-80% of the packages I tried using with alien  worked.

---

