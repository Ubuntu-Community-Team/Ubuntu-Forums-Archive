---
title: "unable to install gimp"
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

