---
title: "Setting up Bind9 as recursive fails, why.  Worked like a charm in 15.10"
date: 2016-12-13
forum: Server Platforms
---

### Post by MechaMechanism on 2016-12-13
When I set bind to do recursive it fails.  I just apt install bind9 and that was it, I didn't touch or edit any files.  Back in 15.10 and earlier it worked out of the box.  Did something change in 16.04 and 16.10?

How do I make bind just work?  I have attached the bind config files.

```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    // forwarders {
    //     0.0.0.0;
    // };

    //========================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See https://www.isc.org/bind-keys
    //========================================================================
    dnssec-validation auto;

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};


```

---

### Post by MechaMechanism on 2017-07-11
Works now. I think it needed the following;```
listen-on    { any; };
```Why that's not included by default I don't know. Started working as soon as I added the IPv4 in addition to the IPv6.

---

