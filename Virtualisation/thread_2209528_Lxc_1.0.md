---
title: "Lxc 1.0"
date: 2014-03-06
forum: Virtualisation
---

### Post by sdpagent on 2014-03-06
I [just read]("http://www.vyomtech.com/2014/03/04/docker_and_linux_containers_lxc_1_0_release.html?utm_source=Docker+News&utm_campaign=4cab6bb881-Docker_0_5_0_7_18_2013&utm_medium=email&utm_term=0_c0995b6e8f-4cab6bb881-235722885") that LXC 1.0 was released on the 20th of February which amongst other things, features "Support for fully unprivileged containers". It is now considered "production ready" according to [linuxcontainers.org]("https://linuxcontainers.org/news/"). 

**Does this mean that it would now be "safe" to host third party containers as a service?** E.g. just like how I can rent a Virtual machine in the form of Xen/Kvm from various providers. Yes, I realize these ar "containers" and not virtual machines, but essentially they both fulfill my needs.

---

### Post by TheFu on 2014-03-22
For certain values of "safe" yes.
I won't be doing it until a few years have passed and nothing bad has happened between any LXC instances running on the same machine. 

When it comes to security - the early adopter is almost always toast.

---

