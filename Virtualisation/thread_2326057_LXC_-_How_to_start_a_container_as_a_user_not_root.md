---
title: "LXC - How to start a container as a user not root"
date: 2016-05-27
forum: Virtualisation
---

### Post by denizen45 on 2016-05-27
Hi

I'm wondering if it is possible to set up a container to be a non-root user. The host Os is Ubuntu 16.04 root, the container is Ubuntu 16.04.
The reason i would like to do this so that I can run Google Chrome, VLC ... in a non-root user mode since they will not run properly in a root
account. Any and all tips welcome.

Thanks Murray

---

### Post by QDR06VV9 on 2016-05-28
> **denizen45 said:**
> Hi

I'm wondering if it is possible to set up a container to be a non-root user. The host Os is Ubuntu 16.04 root, the container is Ubuntu 16.04.
The reason i would like to do this so that I can run Google Chrome, VLC ... in a non-root user mode since they will not run properly in a root
account. Any and all tips welcome.

Thanks Murray
Well there is quite a bit of information to run LXC container's as unprivileged containers...but check this out: [https://www.stgraber.org/2014/01/17/lxc-1-0-unprivileged-containers/](https://www.stgraber.org/2014/01/17/lxc-1-0-unprivileged-containers/)

There is also sand-boxing most applications with Firejail [https://firejail.wordpress.com/](https://firejail.wordpress.com/)
I use Firejail Quite a bit.
Happy Reading:D
Regards

---

