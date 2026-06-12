---
title: "Windows XP logs on to Samba PDC instead of BDC"
date: 2011-02-03
forum: Server Platforms
---

### Post by oohshiny on 2011-02-03
I'm running a set of virtual machines (most in ESXi, one in VirtualBox on my desktop) to try and replicate an existing physical network structure with a Samba domain operating across multiple subnets. The layout is:

(ESXi)
* Router - Ubuntu 8.04, running dnsmasq, bridging my 2 virtual subnets (10.10.4.1/24 & 10.10.5.1/24) and my physical network
* PDC - Ubuntu 8.04, configured as a Samba PDC with PAM configured to use LDAP, SMBLDAP etc. on 10.10.4.11
* LDAP - Ubuntu 8.04, running Zimbra 5 mail server, acting as the LDAP backend for Samba on 10.10.4.12
* BDC - Ubuntu 8.04, configured as a Samba BDC with PAM LDAP etc.
* Client1 - Windows XP, joined to domain on 10.10.5.100

(Virtualbox)
* Client2 - Windows XP, joined to domain on 10.10.5.99

Watching /var/log/daemon.log, /var/log/samba/*, smbstatus -bd0 shows that Client1 successfully logs on to the BDC (10.10.5.2) but Client2 logs on to the PDC (10.10.4.11) instead. Both clients have the same subnet, DNS, WINS settings etc.

What could be causing this and how do I fix it? I've seen the issue happen in our physical setup too but very infrequently and usually when there's been a network interruption between the BDC(s) and the LDAP server.

---

### Post by oohshiny on 2011-03-09
Well, I solved it using `nltest /sc_reset` - it appears that in a "normal" environment the network latency would guarantee that the (local) BDC would service the logon query, but in a VM environment (or if the network goes weird) a race condition exists and sometimes the PDC wins.

---

