---
title: "Setting the name server with a static eth0"
date: 2005-11-09
forum: Server Platforms
---

### Post by joepotter on 2005-11-09
If I use a router and dhcp, then the name servers set by the ISP are all automatic. However, if I want to set the interface as static, how do I tell the system what nameserver to use?

One could put it in /etc/resolv.conf in the old days, but that file gets over-written at boot these days. So, what magic file should I stuff this info into?

Thanks much.

---

### Post by LordHunter317 on 2005-11-09
You can specify it in /etc/network/interfaces.

---

### Post by joepotter on 2005-11-09
[QUOTE=LordHunter317]You can specify it in /etc/network/interfaces.[/QUOTE]



That is what I thought, but I read the man page this morning and it did not document any way to do this.

What have you used? I would guess:

nameserver	xxxx.xxxx.xxxx.xxxx

but, I would have guessed I would see it in "man interfaces" but it was not.

---

### Post by tonym on 2005-11-13
Are you sure resolv.conf gets overidden?  I thought that only happened if using DHCP?

---

### Post by pitufo on 2005-11-13
Yes, resolv.conf is overridden by DHCP (when dhclient is run during network configuration).  The only way I found to force it to keep the static nameservers is by modifying file /etc/dhcp3/dhclient-script as follows:

sudo vi /etc/dhcp3/dhclient-script (keep a backup copy)

look for a function named "make_resolv_conf()"
comment out all lines in the function *except:*

egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
             $new_resolv_conf

AND

chown --reference=/etc/resolv.conf $new_resolv_conf
chmod --reference=/etc/resolv.conf $new_resolv_conf
mv $new_resolv_conf /etc/resolv.conf

save the file and reboot.  The static nameserver IPs should still be in resolv.conf.

dhclient-script, as originally coded, is replacing one of the nameservers in resolv.conf with the IP of the DHCP server in your network.

Hope this helps.

---

### Post by LordHunter317 on 2005-11-14
[QUOTE=tonym]Are you sure resolv.conf gets overidden?  I thought that only happened if using DHCP?[/QUOTE]Yes, it gets overriden by the resolvconf application.

The eaisest way to solve this is to add the following directives per interface in /etc/network/interfaces:```
dns-nameservers 11.22.33.44 55.66.77.88
dns-search foo.org bar.com
```

---

