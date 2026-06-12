---
title: "Do I need adding a 2nd NIC"
date: 2015-05-27
forum: Virtualisation
---

### Post by satimis on 2015-05-27
Hi all,

VirtualBox
========

Network connection - Onboard NIC

Internet -> Router -> PC Host -> Bridge Networking -> VM

If removing the Router
New Network Connection
Internet -> PC Host -> Bridge Networking -> VM

Do I need to add a 2nd NIC?  Thanks.

Regards
satimis

---

### Post by CharlesA on 2015-05-27
You would need to set the VM up to use NAT instead of bridged unless you have a plan that gives you more than one IP address.

---

### Post by satimis on 2015-05-27
> **CharlesA said:**
> You would need to set the VM up to use NAT instead of bridged unless you have a plan that gives you more than one IP address.
Hi,

Thanks for your advice.

I'm prepared to run VMs as web servers.  All websites are on name-based, built with Wordpress.  Do I need to assign static IP to each VM allowing the websites to be accessed on Internet?  In such case, do I need to run Haproxy, proxy server, on the host to forward port 80 to each VM?

Regards
satimis

---

### Post by CharlesA on 2015-05-27
> **satimis said:**
> Hi,

Thanks for your advice.

I'm prepared to run VMs as web servers.  All websites are on name-based, built with Wordpress.  Do I need to assign static IP to each VM allowing the websites to be accessed on Internet?  In such case, do I need to run Haproxy, proxy server, on the host to forward port 80 to each VM?

Regards
satimis

Depends on how your internet connection is set up. Most of the time you can just foward port 80 and 443 on the router, but if you are taking the router out of the picture, the host would be directly connected to the internet and you would need to fudge with the networking unless you had more IP addresses you could use.

---

