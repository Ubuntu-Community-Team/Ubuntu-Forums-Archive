---
title: "How to update DDNS for fixed-address hosts?"
date: 2011-04-03
forum: Server Platforms
---

### Post by damateem on 2011-04-03
I have DDNS configured and working for dynamic addresses, but it's not quite right for static addresses yet. The DHCP server assigns the static address, but it doesn't update the DNS sever with the associated host name. Which means I have to use the IP address when accessing the host instead of the host name. How can I get the DHCP server to update the DNS with the host name associated with the fixed-address?

Here is my current dhcpd.conf.

```

ddns-update-style       interim;
ignore                  client-updates;

include "/etc/bind/rndc.key";

zone home.lan. {
        primary 127.0.0.1;
        key     "rndc-key";
}

authoritative;
subnet 192.168.0.0 netmask 255.255.255.0 {
        range                           192.168.0.100 192.168.0.199;
        option domain-name-servers      192.168.0.2;
        option domain-name              "home.lan";
        option routers                  192.168.0.3;
        default-lease-time              600;
        max-lease-time                  7200;

        zone server1.home.lan. {
                primary 192.168.0.2;
                key "rndc-key";
        }

        zone 0.168.192.in-addr.arpa. {
                primary 192.168.0.2;
                key "rndc-key";
        }
}

# Assign static IP addresses
host david-notebook {
  hardware ethernet 00:90:f5:3f:a2:3a;
  fixed-address 192.168.0.14;
}

```


Thanks,
David

---

### Post by elico on 2011-04-04
i dont understand yet.
and what about your named/bind settings zone settings file?

---

### Post by damateem on 2011-04-04
Since it is working fine for dynamic addresses, I expect the other configuration files are correct. I just need a way to get the dhcp server to tell update the dns when it doles out a fixed-address.

I found a web page that recommended adding

```
update-static-leases    on;
```

to the top of dhcpd.conf and

```
ddns-hostname "david-notebook";
ddns-domain-name "home.lan";
option host-name "david-notebook";
option domain-name "home.lan";
```

to the host statement of the fixed-address host. When I restarted the server, I got an error for the line

```
ddns-domain-name "home.lan";
```

After commenting out that line the server restarted without error. Now my dhcpd.conf looks as follows.

```

ddns-update-style       interim;

# We want fixed-address entries you want to use dynamic dns.
update-static-leases    on;

ignore                  client-updates;

include "/etc/bind/rndc.key";

zone home.lan. {
        primary 127.0.0.1;
        key     "rndc-key";
}

authoritative;
subnet 192.168.0.0 netmask 255.255.255.0 {
        range                           192.168.0.100 192.168.0.199;
        option domain-name-servers      192.168.0.2;
        option domain-name              "home.lan";
        option routers                  192.168.0.3;
        default-lease-time              600;
        max-lease-time                  7200;

        zone server1.home.lan. {
                primary 192.168.0.2;
                key "rndc-key";
        }

        zone 0.168.192.in-addr.arpa. {
                primary 192.168.0.2;
                key "rndc-key";
        }
}

host david-notebook {
  hardware ethernet 00:90:f5:3f:a2:3a;
  fixed-address 192.168.0.14;
  ddns-hostname "david-notebook";
  #ddns-domain-name "home.lan";
  option host-name "david-notebook";
  option domain-name "home.lan";
}

```

This works and I can now access david-notebook by name. Before, I had to use the ip address.

Even though it works, I'm still concerned because the website I found is dated 2008. Do I have it right for dhcp3 and bind9?

Thanks,
David

---

### Post by sgm277 on 2012-04-13
Hi,

I have the same issue as you, could you show me your configuration detail ? appreciated.

---

### Post by Costas7 on 2013-03-01
Hello. After nearly a year I have come up with the same issue. [COLOR=#000000]How can I get the DHCP server to update the DNS with the host name associated with the fixed-address? [/COLOR] Can anyone help me on this ? nsupdate works well but DHCP does not seem to update the DNS records. Also for the above post complaining about the line > [LEFT][COLOR=#000000][FONT=Ubuntu Mono]ddns-domain-name "home.lan";[/FONT][/COLOR][/LEFT] it should be > [LEFT][COLOR=#000000][FONT=Ubuntu Mono]ddns-domainname "home.lan";[/FONT][/COLOR][/LEFT] i.e. withput the dash

---

