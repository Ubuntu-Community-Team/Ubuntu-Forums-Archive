---
title: "sarg replacement"
date: 2007-12-26
forum: Server Platforms
---

### Post by xyrer on 2007-12-26
Hi, I have a HP proliant ml115 server, which has ubuntu server amd64, works great so far, the problem comes with the "squid analysis report generator" aka sarg.
When i do "sarg -z -x" it starts working and then it gives me this "segmentation fault" and nothing else, having found nothing on google or any other way, I would like to ask if there is any replacement for this software, or some way to do what sarg does by other means.

If anyone knows of something that could give me a small report of browsing per user base, please tell me.

Thanks.

---

### Post by Re Persina on 2007-12-29
Hello,
I was faced with the same problem today after setting up a 64-bit ubuntu squid server. Sarg segfaults pretty much every time it is run. I researched and found reports from others with the same problem on other 64-bit Linux platforms.

Since sarg happens to do exactly what I need and I've used it other places, I decided to try to get it working rather than try to replace it with something else (I've looked before anyway and never found a suitable candidate). My solution, at least for now, was to install the 32-bit version of sarg, and it is working great.

Here's what I did:

- Remove the 64-bit version:  apt-get remove sarg

- download i386 pkg for sarg and install with dpkg --force-architecture -i
([https://launchpad.net/ubuntu/gutsy/i386/sarg](https://launchpad.net/ubuntu/gutsy/i386/sarg))

- apt-get install ia32-libs

- download i386 pkg for libgd. ([https://launchpad.net/ubuntu/gutsy/i386/libgd2-noxpm/](https://launchpad.net/ubuntu/gutsy/i386/libgd2-noxpm/)) 
I had to manually install the file unfortunately, but it's pretty simple. Extract data.tar.gz from the pkg and then extract libgd.so.2.0.0 from the tarball and save it as **/usr/lib32/libgd.so.2.0.0** (I used ark to do the extracting)

- Create symlink: ln -s /usr/lib32/libgd.so.2.0.0 /usr/lib32/libgd.so.2

- Run [sudo] ldconfig

After that sarg should work as expected.

---

### Post by xyrer on 2007-12-31
Well, That would solve only part of it, as I have a 32 bits ubuntu server 7.10, the error is different but it fails to work anyway, it seems to happen with some reports in particular, but the logs are far too long for me to check them.
I will post details later, thanks for the tips thou.

---

### Post by xyrer on 2008-02-28
I'm changing sarg for a great software called surftrackr, althoght lightsquid works fine for the ones not much demanding

---

