---
title: "VMware Server on 8.04 server edition?"
date: 2008-05-18
forum: Virtualisation
---

### Post by Thirtysixway on 2008-05-18
I was looking at setting up vmware server on my other computer, but it has Ubuntu 8.04 Server on it [no gui].

I had it setup and running when I had 7.10 server edition setup, I would just use the vmware console to connect to it.  But when I hit Start on a virtual machine, it would give me a blank error.

Has anyone made this work? :popcorn:

---

### Post by jjamessyd on 2008-05-18
I am about to try this.
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p5](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p5)
This is also another article:-
[http://www.howtoforge.com/vmware-server-on-ubuntu8.04](http://www.howtoforge.com/vmware-server-on-ubuntu8.04)

I'm still debating which way to go as have concerns about what these patches do. Here is an insight.

[http://eitchpress.eitchnet.ch/?p=13](http://eitchpress.eitchnet.ch/?p=13)

Will post another message when done.

---

### Post by bradmkjr on 2008-05-19
VMware is not upto date with the 8.04 Kernel, so I wouldn't recommend going to 8.04 Virtual Server yet. I have been really happy running 7.10 with 1.0.4/1.05 but holding off on upgrading to 8.04 until I get confirmation that they are compatible with the current ubuntu kernel.

Just my thoughts,
Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

### Post by Nampla on 2008-05-20
I am sucessfully running vmware server for 3 win xp vm's under hardy 8.04 server (no gui).  Fortunatly we have a couple pc's running hardy desktop which I can NoMachine into for a gui if needed.  I have not experienced any real issues with Hardy and vmware yet.

---

### Post by jjamessyd on 2008-05-20
Have installed the server with no problems. We are about to try to stress test a Ubuntu 8.04 based virtual machine on the newly configured system. We will be testing web hosting capabilities and comparing our existing virtual server config based on VMware GSX. I am trying 8.04 JeOS images to have a low profile guest OS.
No doubt this configuration works. The question is how long will it run without problems.

Our current config has run for over a year without the need for reboot. The host has been running for almost 2 years without reboot.

I agree if you intend to run this in production for hosting etc evaluate and perhaps wait for a while.

I intend to stress test it and the run it with several willing customers for web hosting.

If you intend to have a play and evaluate, perhaps use in a controlled inhouse application then try it. If you intend to host a significant amount of websites and put it into production wait and use 7.10.

If you want more specific details on the methods I used let me know, but in essence it was an install based on the vmware-any-any-update116.

Will post findings as soon as available.

---

