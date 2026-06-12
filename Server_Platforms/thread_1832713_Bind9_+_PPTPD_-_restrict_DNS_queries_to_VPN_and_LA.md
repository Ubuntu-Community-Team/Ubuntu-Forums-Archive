---
title: "Bind9 + PPTPD - restrict DNS queries to VPN and LAN only"
date: 2011-08-25
forum: Server Platforms
---

### Post by kalosh on 2011-08-25
Hi.
I would like to have my bind9 DNS server to allow queries only from LAN or VPN. I now how to restrict it to LAN only. If I do that and connect with VPN to my local network I can not query the DNS because it denies querys from outside the local. DNS queries from VPN are shown in the logs as queries from outside the local network (the true IP is being used instead of local). I am connecting from many places to my home so it is not comfortable to add all networks to 'allowed' in DNS server configuration. The goal is to allow DNS queries from LAN and VPN and restrict queries from outside my LAN.
Do you have idea how to solve that? Is it possible?
Best regards, Dawid.

My named.conf:
```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                195.66.144.2;
                217.17.34.10;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
        listen-on {any;}; # DNS does not answer to queries from VPN if I restrict
                                  # here to my  LAN only
        allow-query-cache {any;};
};
```

---

### Post by kalosh on 2011-08-25
Hi.
I have tried, but no luck. If I add my companies public IP to acl 'vpn' then I can resolve names while I am connected from work to home. But if I am using GPRS then each time I have to check my current IP, add it tp 'vpn' acl and then connect using VPN. My problem is more like: how to force PPTPD to traslate DNS queries packets' IPs to my local IPs. I thought that if I am connected through VPN all my packets' IPs are translated to my local IPs but DNS queries are not.
If the description is a too confused let me know I will try to write it again and more clearly:P

---

### Post by kalosh on 2011-08-31
Hi.
Thanks for response.
I have in my pptp option file following configuration:
ms-dns 10.0.0.1 // my local ip
ms-dns 195.66.145.26 //my ISP server.
In PPTP client I have following serevrs listed as dns. The problem is in two cases:
1. Bind9 rejects connections from other addresses than local.
2. DNS queries from PPTP client are incoming to Bind9 from client's public IP (not VPN's local).
Dawid.

---

