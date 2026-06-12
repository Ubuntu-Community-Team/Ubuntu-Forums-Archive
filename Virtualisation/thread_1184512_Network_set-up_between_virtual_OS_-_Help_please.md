---
title: "Network set-up between virtual OS - Help please"
date: 2009-06-11
forum: Virtualisation
---

### Post by sahabcse on 2009-06-11
Hi

I have installed RHEL 5 and SUSE 11 using virtual box sunXVM. I need to know is there any method to set network connection between those to guest OS. By using vmware we can setup bridge connect between two. Any one have ideas please share with me. My main OS ubuntu 8.10.

---

### Post by caver1 on 2009-06-11
If you are running the PUEL version of VirtualBox 2.2.4.
Go to Settins-Network and in the Attached To box change it to Bridged
Adapter.
If you don't have 2.2.4 I would recommend upgrading.
caver1

---

### Post by bodhi.zazen on 2009-06-11
To be honest, VBox offers a rich set of options for networking, including host only and internal networking.

I respectfully suggest you read the networking section on the [VBox User Manual (PDF)](http://download.virtualbox.org/virtualbox/2.2.4/UserManual.pdf) (which I find to be quite informative).

---

