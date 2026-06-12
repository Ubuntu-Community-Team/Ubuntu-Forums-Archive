---
title: "DHCP server - Is a domain name required?"
date: 2013-06-22
forum: Server Platforms
---

### Post by Loki57701 on 2013-06-22
Hello, as the title says, when setting up a DHCP server is it required to specify a domain name? 

I'm planning to setup a DHCP server for a home network (for funsies), and I don't really have a domain name; although if I have to I could use home.local or something.

---

### Post by CharlesA on 2013-06-23
I have always used .local for any local machines at home.

While it isn't really required, it is a good thing to have if you set up a local DNS server.

---

### Post by SeijiSensei on 2013-06-23
I agree that having a domain is helpful, but the answer to your original question is no.  DHCP listens on the broadcast address for any packets that come by requesting an IP.  You can distribute various DNS parameters in the reply, like the IP addresses for DNS servers, or the search domain list, but these are all optional.  Here's my dhcpd.conf file:

```

ddns-update-style interim;
ignore client-updates;

subnet 192.168.100.0 netmask 255.255.255.0 {

        range 192.168.100.50 192.168.100.99;

        option routers              192.168.100.1;
        option subnet-mask          255.255.255.0;

        option domain-name             "example.com";
        option domain-name-servers      192.168.100.100, 8.8.8.8, 8.8.4.4;

        option time-offset              -18000; # Eastern Standard Time
        option ntp-servers              192.168.100.100;
        option netbios-name-servers     192.168.100.100;

}

```

---

