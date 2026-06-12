---
title: "LXD: learning container mac on wrong port of bridge"
date: 2016-06-30
forum: Virtualisation
---

### Post by krim2 on 2016-06-30
Hi,
i have a big problem with my installation using LXD.

whenever i set up a new container the system wants to get an ip adress  via dhcp. it submits the request on the bridged interface, response  arrives to the bridge and then... error.

reason:
albeit being on port 2 of the linux bridge, the brctl showmacs tells me,  the mac adress of the container is on port 1. this makes lil sense,  because the mac used for the dhcp request is the "faked" one (set in  config). So the response will never arrive at the container, because the  bridge filters it.

I already found 2 solutions on the net, one with a NAT (no option), one  with buggy intel drivers - both dont apply for me. I'll have to use  brctl - so are there any solutions or tips?

edit:ps: it gets semi fixed when i ping the server from outside every 300 secs.

---

### Post by MAFoElffen on 2016-07-01
There is also bridge, macvlan and macvtap. It0 all depends how you configure the network settings of your host, your container... and the network settings of the OS in your container.

---

### Post by krim2 on 2016-07-01
solution:
brctl setageing lxdbr0 0

does not work on Kernel 4.4.6, older OR newer required. Was hard to realize it was a kernel bug

---

### Post by MAFoElffen on 2016-07-02
Congrats on finding a solution. I think that is an important find. To help us here and others:

Please report this to launchpad so that they know about it and can apply a patch to that kernel. Link this thread  in that bug as reference.

Then post the bug number link back here.

Please mark this thread as solved (Upper right of this page > Select link "Thread Tools" > Select "Mark thread as Solved") so that other people can find your fix.

---

