---
title: "Google Chrome in 13.10"
date: 2013-05-06
forum: Ubuntu Development Version
---

### Post by roly33 on 2013-05-06
I've just had to do a re-install of my Notebook that was running 13.04 that I rolled over to 13.10 Development Release and I'm now unable to Install Google Chrome.  I was able to Install it in 13.04 by manually Installing libudev0, but that work around is no longer working in 13.10.

Is there a way to get Gogle Chrome to Install on 13.10 or am I stuck with Firefox until 13.10 is further along the Development cycle?

Roland

---

### Post by slickymaster on 2013-05-06
I have Chrome installed on my Suacy box with kernel 3.9rc3.

```
slickymaster@IMT-VirtualBox:~$ lsb_release -a; uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
Linux IMT-VirtualBox 3.9.0-030900rc3-generic #201303171935 SMP Sun Mar 17 23:44:49 UTC 2013 i686 i686 i686 GNU/Linux
```

```
slickymaster@IMT-VirtualBox:~$ dpkg --get-selections | grep google*
google-chrome-stable    install
```

---

### Post by roly33 on 2013-05-06
> **slickymaster said:**
> I have Chrome installed on my Suacy box with kernel 3.9rc3.

```
slickymaster@IMT-VirtualBox:~$ lsb_release -a; uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
Linux IMT-VirtualBox 3.9.0-030900rc3-generic #201303171935 SMP Sun Mar 17 23:44:49 UTC 2013 i686 i686 i686 GNU/Linux
```

```
slickymaster@IMT-VirtualBox:~$ dpkg --get-selections | grep google*
google-chrome-stable    install
```

I managed to get Chrome to install just before I checked for a reply by using the current unstable build, and it installed without a problem without having to use the Terminal to get it to install.

[ATTACH=CONFIG]242269[/ATTACH]

Roland

---

### Post by craig10x on 2013-05-06
@Roland: That worked because Chrome unstable HAS the fix in it...it just hasn't filtered down to the beta and stable channels yet...

---

