---
title: "Ubuntu PPTPD /  PPTP Support - How can I block all sites except one on my VPN?"
date: 2012-12-12
forum: Server Platforms
---

### Post by Zyzy on 2012-12-12
Hello,

I have an ubuntu PPTPD VPN set up and working,
How can i limit it so when users login they can only access 1 website? 

Thanks for your support.
ZyZy

---

### Post by SeijiSensei on 2012-12-12
Use iptables rules like this:

```

sudo iptables -A INPUT -i ppp0 -p tcp -d ip.addr.of.site --dport 80 -j ACCEPT
sudo iptables -A INPUT -i ppp0 -p tcp --dport 80 -j REJECT

```

That tells the machine to accept traffic arriving on the ppp0 interface and destined for the machine at ip.addr.of.site.  All other traffic on ppp0 destined for a remote web site is blocked.

If you want to block HTTPS traffic as well, duplicate those two commands and replace "80" with "443".

---

### Post by Zyzy on 2012-12-13
Thanks!!, but what about if I wanted to allow only access to netflix.com   could i put netflix.com or do i have to specify an ip address?

---

### Post by SeijiSensei on 2012-12-13
If the rules are installed before the network starts, then you must use IP addresses because DNS resolution will not be available.  Large sites like Netflix pose more complicated problems because they typically have multiple hosts that all share a single name.  Connect to the Internet and run the command "host www.netflix.com".  I see about eight different hosts that respond to that name.  So you would need to write a rule for each of those IP addresses.

---

