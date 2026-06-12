---
title: "Connect to SSH via hostname?"
date: 2009-12-02
forum: Server Platforms
---

### Post by Stan* on 2009-12-02
Each time I try to connect to my server via "ssh user@hostname" the server gives the error the hostname couldn't be resolved. I have to connect via "ssh user@ipaddress" instead.
How could it be the hostname wasn't resolved? I am in the same network as the server though.

---

### Post by slakkie on 2009-12-02
man hosts

---

### Post by Vegan on 2009-12-02
Do you have a DNS server with the URL setup or not? If not then you can use the hosts file and create short names for machines.

---

### Post by BkkBonanza on 2009-12-02
You should read up on the docs for your router. Typically the router is running a name service like dnsmasq doing DHCP and DNS. It will keep track of the names for various LAN ips and usually adds those names into the DNS entries it handles. Doing it this way should mean not manually entering hostnames into the hosts file on each machine.

---

### Post by Iowan on 2009-12-02
If your DHCP server also runs DNS (as mentioned), your machine(s) will need to send hostname along with IP request. You'll need to edit */etc/dhcp3/dhclient.conf* - change the line ```
send host-name "<hostname>";
```

---

### Post by stefanadelbert on 2009-12-03
Try

```
ssh user@hostname.local
```

Works for me and doesn't seem to rely on DNS or /etc/hosts. This will almost certainly only work for machines on your local network...

---

### Post by Stan* on 2009-12-03
Thanks. It works now.

---

