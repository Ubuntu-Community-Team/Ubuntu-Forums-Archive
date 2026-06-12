---
title: "Virtualbox networking"
date: 2014-08-19
forum: Virtualisation
---

### Post by linuxyogi on 2014-08-19
Hi,

Host : Lubuntu : 14.04
Guest : Lubuntu 14.04

I want to run a service which needs a specific port to be opened.

I have done port forwarding on my router.

I don't want to open any ports on my host (Lubuntu).

I am thinking of opening that port only on the guest (also Lubuntu).

Is this possible ? Please tell me how how to configure the networking part in Virtualbox.

---

### Post by Tadaen_Sylvermane on 2014-08-20
In VirtualBox in the guest settings change the network from NAT to Bridged. Inside the guest give it a static ip. Then just forward that port directly to that guest ip.

For reference the bridged mode makes the virtual machine appear to be a physical computer on your network. It will be assigned from your router (unless you set a static ip).

---

### Post by linuxyogi on 2014-08-20
Its working. Thanks.

---

### Post by coldraven on 2014-08-20
I don't have Vbox installed at the moment but here is something that I posted a while ago.
[I]For some good info about networking in Virtualbox  go here and click on the image of issue 61 to download it  (pdf)
[http://fullcirclemagazine.org/issue-61/](http://fullcirclemagazine.org/issue-61/)  
Then read from page 15 onwards.

I found this to be easy to understand, I hope it helps you.[/I]

---

