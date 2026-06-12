---
title: "Ubuntu 8.04 server guest on 8.04 server"
date: 2008-05-13
forum: Virtualisation
---

### Post by sndnichols on 2008-05-13
Hi, I have looked at all of the threads and many sites. I have seen the problem, but none of the solutions work for me. I can get the kvm VM made just fine, using ubuntu-vm-builder, but when I go to start it, I get something similar to this (I am at work and copied this from a different site)

```
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;- DirectFB v0.9.25 &#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;
(c) 2000-2002 convergence integrated media GmbH
(c) 2002-2004 convergence GmbH
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;

(*) DirectFB/Core: Single Application Core. (2007-08-07 19:21)
(*) Direct/Memcpy: Using MMX optimized memcpy()
(!) Direct/Util: opening &#8216;/dev/fb0&#8242; and &#8216;/dev/fb/0&#8242; failed
&#8211;> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use &#8216;fbdev&#8217; option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize &#8217;system&#8217; core!
&#8211;> Initialization error!


```

I have no GUI, which was one "workaround" I found, and would prefer to not have one. I use webmin for my remote management and when I need to, I use the command line at the server. My video card is an ATI X700, and I have tried installing ther drivers and the output hasn't changed, I tried -std-vga, adding to the device list "flgrx" and a couple of others. I am happy to post any outputs that one would like to see in about 6 hours when I get home. I have a Tyan 2915 WA2NRF-E mobo, 8G RAM, (2) AMD 2350's, and a wd 1tb hard drive. Any assistance is greatly appreciated.

---

### Post by sndnichols on 2008-05-14
Bump. Any links to more than the server guide would help. I noticed in the sticky there arte no links. Is KVM just too new to use?

---

### Post by prshah on 2008-05-14
> **sndnichols said:**
> ```

(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use ‘fbdev’ option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize ’system’ core!
–> Initialization error!

```
I have no GUI, which was one "workaround" I found, and would prefer to not have one. 

What you're trying here is way over my head, so my hint below may or may not be suitable:

[http://en.wikipedia.org/wiki/Xvfb](http://en.wikipedia.org/wiki/Xvfb)

---

### Post by sndnichols on 2008-05-16
That seems like it could be something to try. I will this weekend. Thanks for the suggestion!

---

