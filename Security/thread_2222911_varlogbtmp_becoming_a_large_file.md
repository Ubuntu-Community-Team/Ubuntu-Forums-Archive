---
title: "/var/log/btmp becoming a large file"
date: 2014-05-08
forum: Security
---

### Post by odror on 2014-05-08
OS: ubuntu 14.04
I have numerous attempts per second to access my computer from china (using ssh and user root; root login is disabled). My /var/log/btmp is getting to be too large.

Is there a was to block .cn domain from accessing my computer.

or

is there a way to generate a blacklist of ips from the btmp file

or is there an internet blacklist file somewhere

Thanks

---

### Post by Lars Noodén on 2014-05-08
You can download the list of Chinese nets here: [http://www.ipdeny.com/ipblocks/data/countries/](http://www.ipdeny.com/ipblocks/data/countries/)
and feed it into iptables.  I'm not sure how frequently it is updated, maybe monthly.

However, you might look at fail2ban which scans the log files and blocks based on failed attempts to get in.

---

### Post by odror on 2014-05-08
> You can download the list of Chinese nets here: [http://www.ipdeny.com/ipblocks/data/countries/](http://www.ipdeny.com/ipblocks/data/countries/)Is this going to slow internet access. If for each request the IP will need to compared with such a long list.

---

### Post by Lars Noodén on 2014-05-09
It would depend on how you form your iptables rules.  If you have the RELATED, ESTABLISHED packets checked first before descending into the long list, then it should have negligible effect -- I think.  That order would also allow you to access any site on the blacklist, if you are the one initiating contact.  

Others with more knowledge and experience with iptables would be able to say more.

---

