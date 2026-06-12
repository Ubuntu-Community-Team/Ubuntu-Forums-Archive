---
title: "re-partion on ubuntu server"
date: 2009-05-03
forum: Server Platforms
---

### Post by salim.madni on 2009-05-03
hello gurus


we are going to start a new discussion series for testing environment then going to apply in live. 

a) we want to replace redhat advanced server 4 u3 on our axigen sa1 machine by ubuntu server.

b) we also need your guideline for 2 matters,just to make sure we are going correctly on linux machines

b.1) how we can do re-partion same axigen machine, this means currently 1 swap partition there, another ext3 "/" root partition there where mail server is installed under /var/opt/mail server.  the problem everything is under single partition which is very high alert and critical dangerious to keep mail  and root directory same "/" single share. so we are planning to create another partition where we can move our axigen


b.2) can you suggest and guide if we create ext4 partion as /mail and we want to install axigen there how we can do it?

there is no empty space in hard disk drive, under / root, but to create new partition no space. so i want to clarify can we do re-partion of root "/" or not?

if yes, can we get extra space and create another parition for mail server application

regarrds

---

### Post by salim.madni on 2009-05-04
can some one let me know how we can do re-partition on linux machine

say everything inside "/"

now we want to create /backup ext3 and move some data their

any guideline article links can provide

---

### Post by drave99 on 2009-05-04
> **salim.madni said:**
> can some one let me know how we can do re-partition on linux machine

say everything inside "/"

now we want to create /backup ext3 and move some data their

any guideline article links can provide


gparted

---

