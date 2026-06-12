---
title: "How to file official request to remove some program from official Ubuntu repository"
date: 2023-02-16
forum: Ubuntu, Linux and OS Chat
---

### Post by abcuser on 2023-02-16
There are some of the programs using deb package that can be installed from Ubuntu Software that are 5+ years old. There also exist the same application as snap and/or flatpak package and that package is at the latest stable version.

How to file an official request to remove some application from Ubuntu repository?

What I am trying to do is just like Firefox/snap, where there is no official Ubuntu Firefox/deb repository. I would like this for some of the apps in official Ubuntu repository.

---

### Post by TheFu on 2023-02-16
Open a bug that the package is out of date.  
If it is a dead project, perhaps removal makes sense.  
If it still works, but just isn't the latest version, that might be fine for some users.
If the project is still going, it is likely that Debian isn't getting any newer versions either, so you could sign up to be the Debian maintainer.

I'd rather have 5 yr old software in the repos than be forced to use a snap package.

---

### Post by ajgreeny on 2023-02-16
Give us some examples of the packages you are seeing with old packages and we may be able to help you with ways around the problem, if problem it is for them.

---

### Post by grahammechanical on 2023-02-16
There are lots of packages that do not get upgraded during the life of the Ubuntu version. For an LTS version coming to end of life that could mean 5 year old packages. To get newer versions (if available) we need to upgrade to newer versions of Ubuntu. For example, to get a newer version of an application than the one in Ubuntu 18.04 we would have needed to upgrade to 18.10. Or upgrade to 20.04 when it was released if we wanted to continue using a LTS version with its 5 year support.

Regards

---

### Post by TheFu on 2023-02-16
> **grahammechanical said:**
> There are lots of packages that do not get upgraded during the life of the Ubuntu version. For an LTS version coming to end of life that could mean 5 year old packages. To get newer versions (if available) we need to upgrade to newer versions of Ubuntu. For example, to get a newer version of an application than the one in Ubuntu 18.04 we would have needed to upgrade to 18.10. Or upgrade to 20.04 when it was released if we wanted to continue using a LTS version with its 5 year support.

Regards

Excellent point.  If using an LTS, corporations WANT only bug fixes and security updates, not new features or capabilities.  Stability and behaving as expected is highly desired.  

Canonical does address a few internet connected end-user programs where being on the latest release is important to work with other internet APIs, but for things that use stable internet APIs or are LAN-only APIs, then NOT getting "new" is a huge feature.

---

### Post by ian-weisser on 2023-02-16
Packages that are truly abandoned or unsupported are routinely removed from Debian and Ubuntu already.

---

### Post by monkeybrain20122 on 2023-02-16
> **grahammechanical said:**
> There are lots of packages that do not get upgraded during the life of the Ubuntu version. For an LTS version coming to end of life that could mean 5 year old packages. To get newer versions (if available) we need to upgrade to newer versions of Ubuntu. For example, to get a newer version of an application than the one in Ubuntu 18.04 we would have needed to upgrade to 18.10. Or upgrade to 20.04 when it was released if we wanted to continue using a LTS version with its 5 year support.

Regards

For Ubuntu users there are many options other than upgrading the OS to get the latest vlc or gimp: ppa, snap or flatpak, or compile from source for those who are up to it. I never think it makes sense to upgrade the whole OS just because you need some latest features or bugfix for a few apps or be stuck with software that should go to the museum.

That's why I used Ubuntu rather than Debian. Debian "stability" actually means predictability, that includes predictably broken since upstream bugfixes are unavailable or discouraged.  (At the other extreme is Arch where you always get the latest. It is probably not a great idea to get the latest and greatest for system components though surprisingly Arch seems to be remarkably stable)

---

