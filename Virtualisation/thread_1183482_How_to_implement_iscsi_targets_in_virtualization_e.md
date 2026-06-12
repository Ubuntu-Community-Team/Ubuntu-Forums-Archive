---
title: "How to implement iscsi targets in virtualization environment"
date: 2009-06-10
forum: Virtualisation
---

### Post by TheR on 2009-06-10
I have copied this question from server group.
----------------------------------

This is more like theoretical question.

I want to set up virtual environment with iscsi target server which is ubuntu based. On target decided to use single tid under which I create multple LUN-s, which represent disks used by initiator which is KVM server. One LUN becomes a disk used by one virtual machine on KVM server.

My problem is when I create new LUN on target (under same tid), this LUN doesn't get recognized by initiator without restarting initiator iscsi service. Which in return breaks all curently running machines on KVM server.

What do you do in this kind of environment. Do you create new tid on target for every new disk (machine)? Or have I missed something.


by
TheR

---

