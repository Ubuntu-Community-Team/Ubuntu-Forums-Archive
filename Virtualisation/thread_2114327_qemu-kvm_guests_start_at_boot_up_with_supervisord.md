---
title: "qemu-kvm guests start at boot up with supervisord?"
date: 2013-02-09
forum: Virtualisation
---

### Post by CootCraig on 2013-02-09
I'm new to kvm, I would like to place a Ubuntu computer in my
company data center that will alway be running 2 guest vm's:

Ubuntu KVM host
guest 1 - Windows 2003 Server with MSSQL 2000
guest 2 - Ubuntu project server

What I've done so far.
I've built and run the 2 guest vm's using virt-manager.

My idea is to have supervisor start the vm's at boot time and
make sure they keep running.
[http://supervisord.org/](http://supervisord.org/)

I'm new to kvm and to supervisor.  I'm not sure of how to have supervisor start the vm's 
so that they are correctly monitored.

I'm about to install supervisor and work on this.  I would like
opinions on how to do this, including alternate approaches

Thanks.

---

