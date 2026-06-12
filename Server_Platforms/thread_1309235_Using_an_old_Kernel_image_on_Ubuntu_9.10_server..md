---
title: "Using an old Kernel image on Ubuntu 9.10 server."
date: 2009-11-01
forum: Server Platforms
---

### Post by robhauge on 2009-11-01
Due to problems with an usb-serial driver in Kernel version 2.6.31-14, I need to install Kernel version 2.6.28 on Ubuntu server 9.10. How do I install it the correct way?

---

### Post by slakkie on 2009-11-01
You could add some jaunty sources to your sources.list


```

apt-cache policy linux-image-generic
linux-image-generic:
  Installed: 2.6.31.14.27
  Candidate: 2.6.31.14.27
  Version table:
 *** 2.6.31.14.27 0
        990 http://archive.ubuntu.com lucid/main Packages
        500 http://archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status
     2.6.28.16.21 0
        500 http://security.ubuntu.com jaunty-security/main Packages
        500 http://archive.ubuntu.com jaunty-updates/main Packages
     2.6.28.11.15 0
        500 http://archive.ubuntu.com jaunty/main Packages

```

Install the Jaunty kernel:

```

sudo aptitude install linux-image-generic=2.6.28.11.15

```

Which installs the version from jaunty/main.

Then remove the jaunty sources, or do something with pinning (man apt_preferences)

---

