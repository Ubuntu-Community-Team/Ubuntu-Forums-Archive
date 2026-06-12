---
title: "Firewalld routing based on CGroup"
date: 2017-11-06
forum: Security
---

### Post by autolycus2 on 2017-11-06
I've been searching around for a workable solution to route traffic between interfaces with firewalld based on cgroup membership of the process generating said traffic.  Something similar to [http://www.evolware.org/?p=369](http://www.evolware.org/?p=369).  I've found configurations based on iptables, but nothing for firewalld.  Anyone know how to accomplish the same with firewalld?

---

### Post by TheFu on 2017-11-06
I thought firewalld was RHEL/CentOS/Fedora only.   When did it become available on Ubuntu?  Looks like firewalld has been available for a while.  You are the first post I've seen about it related to Ubuntu.  I've used it on CentOS 7.x but nowhere else.  There seem to be some caveats with using firewalld on Ubuntu. Those are inside the manpage.  The ubuntu manpage for firewalld references files that aren't used on Ubuntu, so I wouldn't assume that using it would be problem free without lots of testing.

---

### Post by autolycus2 on 2017-11-07
Somehow it got loaded on my 16.04 device above all else.  I thought it was a little strange as well, but figured perhaps Canonical was moving in that direction.

---

### Post by TheFu on 2017-11-08
> **autolycus2 said:**
> Somehow it got loaded on my 16.04 device above all else.  I thought it was a little strange as well, but figured perhaps Canonical was moving in that direction.

I found firewalld for my needs on CentOS to be straight forward and capable. I wasn't doing anything complicated. The usage made sense to me and worked with zero issues, 1st time.

I would use iptables on Ubuntu for non-trivial firewall stuff.  There is a great book on it by No-Starch Press. That book covers more than I've ever needed to know.  I have seen methods using a uid to control traffic, but can't recall a way using cgroups.  There must be or all the container solutions with networked webapps wouldn't work.  I see a few search results from 2015 that say cgroup control using iptables had not been released.  Don't know what to make of that.

[https://www.slideshare.net/kerneltlv/advanced-namespaces-and-cgroups](https://www.slideshare.net/kerneltlv/advanced-namespaces-and-cgroups) seemed to be relevant. Guess you've already seen that?

---

