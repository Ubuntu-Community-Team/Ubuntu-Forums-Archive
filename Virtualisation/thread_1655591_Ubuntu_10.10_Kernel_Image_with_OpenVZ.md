---
title: "Ubuntu 10.10 Kernel Image with OpenVZ?"
date: 2010-12-29
forum: Virtualisation
---

### Post by ichilton on 2010-12-29
Hi,

I normally run Debian servers but I have an Ubuntu 10.10 x86_64 Desktop box I need to run an OpenVZ instance on.

However, Ubuntu doesn't seem to have any linux-image-openvz packages.

Is there an openvz kernel image available for Ubuntu 10.10 anywhere?

Thanks,

Ian

---

### Post by tghasemi on 2011-01-11
> **ichilton said:**
> Hi,

I normally run Debian servers but I have an Ubuntu 10.10 x86_64 Desktop box I need to run an OpenVZ instance on.

However, Ubuntu doesn't seem to have any linux-image-openvz packages.

Is there an openvz kernel image available for Ubuntu 10.10 anywhere?

Thanks,

Ian


Try LXC .. [https://help.ubuntu.com/community/LXC]("https://help.ubuntu.com/community/LXC")
according to Ubuntu's community LXC will eventually replace OpenVZ.

---

### Post by ichilton on 2011-01-11
Hi,

Interesting, thanks.

Ian

---

### Post by tghasemi on 2011-01-11
> **ichilton said:**
> Hi,

Interesting, thanks.

Ian

You can also make OpenVZ to work on 10.10 I guess but you'll probably need to recompile the Kernel : [http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_(the_Debian_way)]("http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_(the_Debian_way)")

---

### Post by ichilton on 2011-01-11
Yeah, I guessed that - I was just trying to stay with the stock packages though...

Thanks,

Ian

---

