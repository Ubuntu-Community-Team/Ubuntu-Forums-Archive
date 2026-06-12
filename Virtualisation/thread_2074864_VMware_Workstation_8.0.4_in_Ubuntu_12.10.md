---
title: "VMware Workstation 8.0.4 in Ubuntu 12.10"
date: 2012-10-22
forum: Virtualisation
---

### Post by davidmb37 on 2012-10-22
I just rebuilt my laptop and installed Ubuntu 12.10 64 bit.  I had previously installed VMware Workstation 8.0.4 on Ubuntu 12.04 so I already know about running the patch to get the network to work.  This time, when I first launch Workstation I get this message instead of it failing on the network, and I don't know what to do from here.  I've spent a while Googling the problem but it doesn't look like anyone has had this issue yet.  Can someone point me in the right direction?

---

### Post by davidmb37 on 2012-10-22
Well I guess that might have been a stupid question.  On a whim I ran sudo apt-get install linux-headers-generic and that seemed to fix the issue.  I can launch Workstation now.

---

### Post by Slim Odds on 2012-10-22
> **davidmb37 said:**
> Well I guess that might have been a stupid question.  On a whim I ran sudo apt-get install linux-headers-generic and that seemed to fix the issue.  I can launch Workstation now.
It's usually good to install "build-essentials" for doing things like this. That would include the headers and some other potentially useful stuff.

---

### Post by davidmb37 on 2012-10-22
Thanks for the tip - much appreciated.  The VMware installer worked without doing this in 12.04 so I got a little confused.  I would love to not even need VMware but since I work for an IT company I am pretty sure I will never be able to really get away from Windows completely.

---

### Post by Slim Odds on 2012-10-22
> **davidmb37 said:**
> Thanks for the tip - much appreciated.  The VMware installer worked without doing this in 12.04 so I got a little confused.  I would love to not even need VMware but since I work for an IT company I am pretty sure I will never be able to really get away from Windows completely.
Yes, even with VirtualBox using the VirtualBox Guess additions requires some of the tools and headers. I just always install 'build-essentials' shortly after any fresh install.

---

