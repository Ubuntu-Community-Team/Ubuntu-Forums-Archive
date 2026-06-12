---
title: "vmware-tools on a guest ubuntu system"
date: 2008-02-28
forum: Virtualisation
---

### Post by sigmoid on 2008-02-28
Hi!

I've installed an Ubuntu JEOS on the newest vmware server, and currently I'm in the process of deleting the ruddy thing and starting a new, clean install, as trying to install vmware-tools fragged my (originally working) eth0, and you know what they say, no net no nothing. -.-!

Right now I think I'll install standard vmware-server, and switch over to the linux-virtual kernel, as JEOS seems a bit work-in-progress.
Anyway...

About vmware-tools. Vmware constantly whines about not having it installed, but I'm quite interested in what it exactly does. I mean, is it worth the fuss?

In case it is, it strangely doesn't compile. It spat out a bunch of errors saying "struct inode" doesnt have a member named "u". I guess it might be a kernel version incompatibility. Still strange that we have a "linux-virtual" kernel, apparently managed by people especially FOR vmware-server, and then vmware-tools don't compile. And then there's no reference or documentation about this at all.

Also, how do I prevent vmware-tools from fregging my eth0? :D

---

### Post by bodhi.zazen on 2008-02-28
See this link : [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

If you are running a server (no X) vmware-tools may not be worth it. Not sure why you lose eth0 (I do not have that problem when I install the tools).

---

