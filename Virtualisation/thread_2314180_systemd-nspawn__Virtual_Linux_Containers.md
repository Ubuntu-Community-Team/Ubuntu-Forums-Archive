---
title: "systemd-nspawn : Virtual Linux Containers"
date: 2016-02-19
forum: Virtualisation
---

### Post by MAFoElffen on 2016-02-19
When i was testing 15.10 in the dev cycle, I started playing with systemd-nspawn. What that is is the ability to run lightweight Virtual Linux Containers as a service. This works even better in 16.04. This is done without a hypervisor, with the Linux Kernel and systemd. It is like a chroot on steroids. I see possibilities there, but haven't found a robust practical use for it, yet... 

Some say it is like LXC. It uses systemd.container. You can boot as a service or by commandline. You can also boot Docker images.

Has anyone else had a chance to play with this yet?

---

