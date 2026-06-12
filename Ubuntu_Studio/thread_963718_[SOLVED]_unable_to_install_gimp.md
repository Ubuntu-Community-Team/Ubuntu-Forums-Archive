---
title: "[SOLVED] unable to install gimp"
date: 2008-10-30
forum: Ubuntu Studio
---

### Post by nikosm on 2008-10-30
Hello everybody,

I wanted to try out a gimp plugin called gimp-resynthesizer, so I installed it with sudo apt-get and then went to filters>map>... but it wasn't there as it was supposed to be.

I thought the problem might be that I was using gimpshop (which was running fine) instead of gimp (side-question: is this likely to have been the problem?). So, I thought I'd just uninstall gimpshop and install gimp. Gimpshop uninstalled fine, but gimp doesn't want to install any more, here's the error message:

```

The following packages have unmet dependencies:
  gimp: Depends: gimp-data (< 2.4.5-z) but 2.5.4-1~ppa1 is to be installed
        Depends: libgimp2.0 (< 2.4.5-z) but 2.5.4-1~ppa1 is to be installed
E: Broken packages
```

running ```
sudo apt-get install -f
``` didn't help.

Any ideas?

Thanks a lot,
Nikos

---

### Post by DeadSuperHero on 2008-10-30
Which version of Ubuntu are you running?
The latest version of Ubuntu (8.10) has Gimp 2.6 in the repos.

---

### Post by unutbu on 2008-10-30
Along with answering Mr. Psychopath's questions, please post the output of
```

dpkg --get-selections | awk '/gimp/{print $1}' | xargs apt-cache policy
```

I think the problem is that you have installed
gimp-data version 2.5.4-1~ppa1 and
libgimp2.0 version 2.5.4-1~ppa1. These are not from the official repos. I'm guessing that if you uninstall gimp-data and libgimp2.0 and then reinstall gimp from the official repo, it will pull in the right versions of gimp-data and libgimp2.0 for you.

---

### Post by nikosm on 2008-10-30
Hello to both of you,

Mr. Psychopath, I am running 8.04, and also there gimp is in the repositories, if I remember well it was even pre-installed once you installed ubuntu (?), but I had to mess with it in order to get gimpshop running.

> **unutbu said:**
> 
I think the problem is that you have installed
gimp-data version 2.5.4-1~ppa1 and
libgimp2.0 version 2.5.4-1~ppa1. These are not from the official repos. I'm guessing that if you uninstall gimp-data and libgimp2.0 and then reinstall gimp from the official repo, it will pull in the right versions of gimp-data and libgimp2.0 for you.

unutbu, you were right, it now works great! And the resynthesizer plug-in appears where it should.

just for the record, here's the output of your suggested command:

```
gimp:
  Installed: (none)
  Candidate: 2.4.5-1ubuntu2
  Version table:
     2.5.4-1~ppa1 0
        100 /var/lib/dpkg/status
     2.4.5-1ubuntu2 0
        500 http://ch.archive.ubuntu.com hardy/main Packages
gimp-data:
  Installed: 2.5.4-1~ppa1
  Candidate: 2.5.4-1~ppa1
  Version table:
 *** 2.5.4-1~ppa1 0
        100 /var/lib/dpkg/status
     2.4.5-1ubuntu2 0
        500 http://ch.archive.ubuntu.com hardy/main Packages
gimp-help-common:
  Installed: 2.4.0-2
  Candidate: 2.4.0-2
  Version table:
 *** 2.4.0-2 0
        500 http://ch.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
gimp-help-en:
  Installed: 2.4.0-2
  Candidate: 2.4.0-2
  Version table:
 *** 2.4.0-2 0
        500 http://ch.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
libgimp2.0:
  Installed: 2.5.4-1~ppa1
  Candidate: 2.5.4-1~ppa1
  Version table:
 *** 2.5.4-1~ppa1 0
        100 /var/lib/dpkg/status
     2.4.5-1ubuntu2 0
        500 http://ch.archive.ubuntu.com hardy/main Packages
```

Thanks a lot!
Nikos

---

