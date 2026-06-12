---
title: "Where to go in order to try to persuade Ubuntu to offer two versions of chromium?"
date: 2020-10-26
forum: Ubuntu, Linux and OS Chat
---

### Post by HippoMan on 2020-10-26
What is the best way to try to persuade the powers that be at Ubuntu to offer two versions of ***chromium***: a ***snap***-based version and a non-***snap***-based version?

I recently upgraded to Ubuntu 20.04 from 18.04, and my long-standing software which makes use of ***chromium*** no longer works, because Ubuntu's offered ***chromium*** is now ***snap***-based, and some of that software references URL's such as ***file:///opt/path/to/somewhere***, and on my system, I have ***/opt*** mounted in ***/etc/fstab*** as a separate filesystem.

I know how to change that software, but it consists of lots of needless, time-consuming work that involves changing mounts, scripts, and various user procedures.

That work is onerous and mostly useless, because its only purpose would be to modify my system to accomodate Ubuntu's decision to force all of us to use a ***snap*** version of ***chromium***.

I have worked around this crippling of ***chromium*** by disabling the ***snap*** version of that package and installing the non-***snap*** version from a PPA. However, ideally, I believe that Ubuntu should offer two versions of ***chromium*** in its repos: (1) the default version which is built on top of ***snap***; (2) the legacy, non-***snap*** version which we could optionally install instead.

There are a number of forums and places for discussion that are offered by Ubuntu, and I'm not sure which is the best place to go in order to try to persuade Ubuntu to offer these two versions of ***chromium***. Thank you in advance for any pointers.

---

### Post by slickymaster on 2020-10-26
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by HippoMan on 2020-10-26
I am new to all these Ubuntu-related forums, so thank you very much for correcting my post by moving it to the proper forum.

---

### Post by ajgreeny on 2020-10-26
I do not think you will manage to get Canonical/Ubuntu to change their minds about packaging for chromium abd this forum is certainly not the place but there are already some PPA repos which can be used to install chromium; I am currently using [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) and it works very well, but there are other PPAs available such as the beta version at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta)

You can enable one or other of these following the instructions at those sites but you will have to accept the risk (I believe very small) of the PPA packages being risky to your system.

I note also that Linux-Mint is itself creating a .deb version of chromium which may be installable in Ubuntu though I have never tried it so this would be up to you to see if it works.  You may have to download the chromium packages from Mint and install them manually as I have no information about adding Mint repos to Ubuntu; might be worth a longer search on that.

---

### Post by HippoMan on 2020-10-26
> **ajgreeny said:**
> There are some PPA repos which can be used to install chromium; I am currently using [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) and it works very well, but there are other PPAs available such as the beta version at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta)

You can enable one or other of those following the instructions at those sites but you will have to accept the risk (I believe very small) of the packages being risky to your OS.

I note also that Linux-Mint is itself creating a .deb version of chromium which may be installable in Ubuntu though I have never tried it so this would be up to you to see if it works.  You may need to download the chromium packages from Mint and install them manually as I have no information about adding Mint repos to Ubuntu; might be worth a longer search on that.

Thank you very much. Coincidentally, that's the exact PPA I went to in order to replace the ***snap***-based ***chromium*** with the traditional version, and it's working.

And now I'll be checking that Linux Mint ***.deb*** package. Thank you for that reference, as well. I'll report my results back here.

What I'm hoping for here is to find a way to try to persuade Ubuntu to offer both the ***snap*** and non-***snap*** versions of ***chromium***, so we don't have to utilize PPA's or packages from other distros.

---

### Post by ayesc0tty89 on 2020-10-26
> **ajgreeny said:**
> I do not think you will manage to get Canonical/Ubuntu to change their minds about packaging for chromium abd this forum is certainly not the place but there are already some PPA repos which can be used to install chromium; I am currently using [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) and it works very well, but there are other PPAs available such as the beta version at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta)

You can enable one or other of these following the instructions at those sites but you will have to accept the risk (I believe very small) of the PPA packages being risky to your system.

I note also that Linux-Mint is itself creating a .deb version of chromium which may be installable in Ubuntu though I have never tried it so this would be up to you to see if it works.  You may have to download the chromium packages from Mint and install them manually as I have no information about adding Mint repos to Ubuntu; might be worth a longer search on that.

No arm64 builds :( thanks though.

---

### Post by TheFu on 2020-10-26
> **HippoMan said:**
>  What I'm hoping for here is to find a way to try to persuade Ubuntu to offer both the ***snap*** and non-***snap*** versions of ***chromium***, so we don't have to utilize PPA's or packages from other distros.

Bring them 10 clients with 100K+ paid support systems each who won't sign the contract without a non-snap chromium packing solution. But I seriously doubt that Canonical is packaging Chromium. I think the google Chromium team is behind it.

Canonical is a business. Money talks.

Snap deployments are strategic goals for Canonical, so by necessity, they may not entertain any other option for a number of years.

In the meantime, you do know that we can run the version of chromium contained inside the snap package, but without the snap confinement or settings, right?
```
$ more ~/bin/chromium.sh
#!/bin/bash
/snap/chromium/current/usr/lib/chromium-browser/chrome $* &

```
Unfortunately, chromium internal code is blocking the use of my preferred sandbox, firejail. I haven't done the research to figure out the new firejail profile settings needed for chromium as provided by the snap package, to work.  There is still a chromium for 16.04 that doesn't use a snap and it runs fine inside a firejail.

---

### Post by CatKiller on 2020-10-26
> **HippoMan said:**
> There are a number of forums and places for discussion that are offered by Ubuntu, and I'm not sure which is the best place to go in order to try to persuade Ubuntu to offer these two versions of ***chromium***. Thank you in advance for any pointers.

[The reasons](https://snapcraft.io/blog/chromium-in-ubuntu-deb-to-snap-transition) for having chromium as a snap are well-documented and widely publicised.

Ubuntu development discussions happen on [Discourse](https://discourse.ubuntu.com/).

---

### Post by HippoMan on 2020-10-27
> **TheFu said:**
> 
[ ... etc. ... ]
In the meantime, you do know that we can run the version of chromium contained inside the snap package, but without the snap confinement or settings, right?
```
$ more ~/bin/chromium.sh
#!/bin/bash
/snap/chromium/current/usr/lib/chromium-browser/chrome $* &
```

Thank  you! I didn't realize that I can do this.  I think that this solves my problem.

---

### Post by ayesc0tty89 on 2020-11-17
> **TheFu said:**
> Bring them 10 clients with 100K+ paid support systems each who won't sign the contract without a non-snap chromium packing solution. But I seriously doubt that Canonical is packaging Chromium. I think the google Chromium team is behind it.

Canonical is a business. Money talks.

Snap deployments are strategic goals for Canonical, so by necessity, they may not entertain any other option for a number of years.

In the meantime, you do know that we can run the version of chromium contained inside the snap package, but without the snap confinement or settings, right?
```
$ more ~/bin/chromium.sh
#!/bin/bash
/snap/chromium/current/usr/lib/chromium-browser/chrome $* &

```
Unfortunately, chromium internal code is blocking the use of my preferred sandbox, firejail. I haven't done the research to figure out the new firejail profile settings needed for chromium as provided by the snap package, to work.  There is still a chromium for 16.04 that doesn't use a snap and it runs fine inside a firejail.

Just want to post and say thanks for this workaround! SNAP with Chromium is horrible and slow but this makes things so much better.
Even hardware acceleration on an RPI4 is working with it. it does NOT with snap.

SO thank you!

---

