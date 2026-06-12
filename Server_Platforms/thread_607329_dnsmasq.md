---
title: "dnsmasq"
date: 2007-11-08
forum: Server Platforms
---

### Post by davidmaxwaterman on 2007-11-08
Hi,

I'm moving from Fedora. I am used to using dnsmasq to do dhcp and dns/dnscaching.

During installation, I selected 'dns', but it wasn't dnsmasq. How can I turn off whatever it is using so that I can run dnsmasq instead?

Thanks.

Max.

---

### Post by DDuong on 2007-12-01
Hello,

Well, IMO, I would do the following:

Remove any DNS software from the machine:

> 
apt-get remove dns


Then, install dnsmasq

> 
apt-get install dnsmasq


---

### Post by sciurus on 2007-12-02
I believe Ubuntu Server's dns option installs bind9. You can disable it from starting at boot with ```
update-rc.d -f bind9 remove
```. You can remove it with ```
aptitude remove bind9
```.

---

