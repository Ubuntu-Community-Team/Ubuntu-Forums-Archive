---
title: "KVM howto"
date: 2010-05-18
forum: Virtualisation
---

### Post by jonsjo on 2010-05-18
Hi there,

I've just installed Ubuntu server 10.04 LTS.
The plan is to deploy a lot of guest on this server.

To begin with I tried to install xen which I have worked with in the past. Then I found out that xen is not a part of the packages included. I next tried KVM, that ubuntu supports, alltough I have no  experience there=). After a full day of trying I'm now giving up and posting this post..

What I want is virtual servers, that can be administraded from ssh and cosole from the host (no GUI). The guest server should be on static IPs.

Can someone please tell me howto do that...=)

Much thanks for ALL the help I can get here..
 -- Jon

---

### Post by totallynewbie on 2010-06-09
Still no reply for this question? Coz i'm doing the same thing and waiting for answer too.

---

### Post by kemra on 2010-06-09
Check the Ubuntu Wiki here: [https://help.ubuntu.com/community/KVM]("https://help.ubuntu.com/community/KVM")

It contains plenty of links including installation, creating VM's etc.

---

### Post by stewagd on 2010-06-30
Would there happen to be any published HowTo for going from Xen 3 to KVM?  I found lots of info on moving PV UML guests but our organization has a dozen or so Windows Server 2003 domU I now need to move to KVM under Lucid.  I haven't had much success finding a clean way to do it -- a colleague suggested I simply install the guests/everything from scratch instead of migrating.  I resisted the temptation to throttle him, but barely. ;) 

A HowTo or some pointers would be nice.

ATB,
Geo

---

### Post by sh1ny on 2010-07-02
I think you can do Xen -> vmware -> kvm.

Use this for the second part :

[http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/](http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/)

---

