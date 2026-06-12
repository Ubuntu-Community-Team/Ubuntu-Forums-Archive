---
title: "Autoban proftpd"
date: 2011-06-01
forum: Server Platforms
---

### Post by DanHorniblow on 2011-06-01
I have a LAMP server running at home, which is also running proftpd, and the FTP is getting hammered with brutte force attacks from all over the world (probly bots). Is it possible to permatly ban an IP automatically after say 10 consecutive incorrect logins?

---

### Post by Lars Noodén on 2011-06-02
Something like this might work to throttle the rate at which new connection are attempted:

```

   ip6tables -N FTP;    # create chain
   iptables  -N FTP;    # create chain

   # send all incoming FTP trafficc to SSH chain
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 21 -m state --state NEW -j FTP;
   iptables  -I INPUT -i eth0 -p tcp --destination-port 21 -m state --state NEW -j FTP;

   # add host to "recent" list
   ip6tables -I FTP -m recent --set --name FTPLIMIT -j ACCEPT;
   iptables  -I FTP -m recent --set --name FTPLIMIT -j ACCEPT;

   # allow finite number of new connections per time limit
   ip6tables -I FTP -m recent --update --seconds 60 --hitcount 10 --name FTPLIMIT -j REJECT
   iptables  -I FTP -m recent --update --seconds 60 --hitcount 10 --name FTPLIMIT -j REJECT


```

You can also look at the package fail2ban.  It may also be time to retire FTP.

---

