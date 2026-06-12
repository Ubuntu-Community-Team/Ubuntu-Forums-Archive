---
title: "Maas installation problem"
date: 2014-06-12
forum: Ubuntu Cloud and Juju
---

### Post by Usman_Shahid on 2014-06-12
Hi,
I have installed MAAS on server machine and tried to install the nodes. I got this error
[COLOR=#333333][FONT=Ubuntu]failed [3/6] (00-maas-03-install-lldpd, 99-maas-01-wait-for-lldpd, 99-maas-02-capture-lldp)

On the internet, i found the solution to add the local network in the squid proxy setting file. I just did that the error didn't went away. Kindly help me out 


[/FONT][/COLOR]

---

### Post by karthik085 on 2014-06-18
Were you able to find a solution to this problem? I am having the same problem...Can you post your solution?

---

### Post by riccardo-magrini on 2014-06-19
Hi,
the solution is this, edit in the region controller the file
**sudo nano /etc/squid-deb-proxy/allowed-networks-src.acl **and add the range IP you used for the nodes. Reboot it after to make that.

---

### Post by Usman_Shahid on 2014-06-19
@Riccardo
I did that, the solution worked when I was testing on virtual machines but on real hardware, even after adding the range in the allowed network in squid proxy didn't worked. Same error stayed there.

---

