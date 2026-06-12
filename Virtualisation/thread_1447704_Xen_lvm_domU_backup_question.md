---
title: "Xen lvm domU backup question"
date: 2010-04-05
forum: Virtualisation
---

### Post by pbrille on 2010-04-05
Hi,

I'm running XEN with the guests stored in lvm Volumes.
In order to do a full system backup I do
1) freeze guest
2) do a lvm snapshot
3) unfreeze guest
4) copy the lvm snapshot with "dd" onto a ftp server.

My Restore procedure would be:
1) Installing new server
2) Restoring xen-configuration of the dom0
3) Restoring the lvm image
4) Start domUs

Now 2 Questions:
1) Is this going to work?
2) What if the hardware between old and new server is slightly OR very different?

THX!!!!!

---

### Post by pbrille on 2010-04-10
Somebody, please?

---

### Post by senor_smile on 2010-06-03
bump... this is a very interesting question that I'm not finding the answer to.

---

