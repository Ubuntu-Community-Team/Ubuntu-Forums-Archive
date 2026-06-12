---
title: "Bind DNS server - Limited forwarding"
date: 2015-06-29
forum: Server Platforms
---

### Post by alberto22 on 2015-06-29
[COLOR=#333333][FONT=Segoe UI]Hello, is it possible to configure Bind to forward DNS requests (to an external server) only for a set of domain names and reject all other requests? [/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-06-30
Yes, you can set up zones in /etc/named.conf like this:
```

zone "example.com" {
     type forward;
     forward only;
     forwarders { 10.10.10.10; 10.10.10.11; };
};

```

I believe if you then include "recursion off" in the global options, the server will only reply for the specified domains.

---

### Post by alberto22 on 2015-07-02
Unfortunately with this configuration the server rejects all the requests.

This is the config:
options {
        directory ".......";
        recursion no;
        allow-query { any; };
        dnssec-validation auto;
        auth-nxdomain no;
        listen-on-v6 { any; };
};
zone "example.com" {
     type forward;
     forwarders {
             8.8.8.8;
             8.8.4.4;
     };
     forward only;
};

Any suggestions?

---

### Post by SeijiSensei on 2015-07-02
I've never been able to get my head around when recursion is required and when it is not.

How about enabling recursion, but limiting the list of valid clients with "allow-query"?  Include localhost and the IP addresses for any local networks using the server in the allow list.
```

recursion yes;
allow-query { 127.0.0.1; 192.168.1.0/24; };

```

I don't think this will keep them from resolving arbitrary-name.com though.  You'll probably have to plow through the BIND documentation to find the right combination of settings.

I think the problem comes with wanting to set up an authoritative-only server, but needing to forward requests for specified domains.  In [this document](http://ftp.isc.org/isc/pubs/tn/isc-tn-2002-2.html), for instance, the authors turn off recursion but use master zone files for the specified domains.  Is there a reason you can't use this method rather than forwarding?

[This posting](http://askubuntu.com/questions/170728/how-to-disable-external-dns-recursion) about using "views" might be helpful.

---

