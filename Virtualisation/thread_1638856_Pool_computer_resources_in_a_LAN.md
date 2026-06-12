---
title: "Pool computer resources in a LAN"
date: 2010-12-06
forum: Virtualisation
---

### Post by garykrige on 2010-12-06
Hi All,

I am the network administrator for a school in KZN South Africa.  I am fairly new to the concepts of virtualization and cloud computing but am very keen to utilize it in our school network.  I would like somehow to 'pool' the resources of a computer lab, such that when a copmputer is standing idle, its cpu can be used by a neighbouring client.  

I have done quite a lot of reading on clustering and cloud computing, but neither seems to be capable of what I am asking.  In a school environment we need to utilize every machine at our disposal and so I don't want to setup a cloud where the nodes are not usable client machines.

I am really keen to get this setup to work as at the moment all our clients are windows.  We are slowly but surely migrating to Ubuntu and this will be the last straw to make us go fully linux.

Thanks in advance for any help offered.

---

### Post by HermanAB on 2010-12-07
No, it doesn't work like that.

---

### Post by surfer on 2010-12-07
if you want to migrate computing jobs (not desktop resources), condor is a pretty simple solution. it's in the repositories. it has a queue you can submit jobs to and it will send them to the next free cpu. condor can be configured in a way that the jobs will stop while someone is working on the machine (i.e. the mouse is moving or the keyboard is being used).

---

