---
title: "ubuntu server +virtualbox"
date: 2012-09-26
forum: Virtualisation
---

### Post by binary_dreamer on 2012-09-26
hi.
i am running an installation of Ubuntu server 12 with virtualbox.
i need to create a set of 4 (in total) OS (ram in enough).
the thing is that i do need the server to be without monitor/keyboard. Is there a way to have a remote management or web page to manage virtualbox?

---

### Post by markbl on 2012-09-26
To be clear, what is the host OS and what are the guest OSes? VirtualBox and its guest hosts can be completely managed using the vbox* commands on the host. It you are installing Ubuntu server guests, then traditionally linux servers are well managed on the command line via ssh.

---

### Post by binary_dreamer on 2012-09-27
Hi. The server runs ubuntu server 12.04, which is the host.
the guest machines will be linux distros and a guest machine with win xp.
i am not looking how to manage each of the guest machines, but the host and its suite.
since the server will be headless, i am looking for a way to manage the virtualbox suiteremotely (ideally through a browser). is that feasible?

---

### Post by markbl on 2012-09-27
You can ssh in to your ubuntu host and manage your guests using vboxmanage on the command line. See the built-in help in VirtualBox which describes this well. Alternately, you can install [phpVirtualBox](http://code.google.com/p/phpvirtualbox/) which I have not used but seems popular.

---

### Post by idlemind324 on 2012-10-02
Have a look at VBoxHeadless if phpVirtualBox doesn't trip your trigger.

[http://www.virtualbox.org/manual/ch07.html](http://www.virtualbox.org/manual/ch07.html)

---

