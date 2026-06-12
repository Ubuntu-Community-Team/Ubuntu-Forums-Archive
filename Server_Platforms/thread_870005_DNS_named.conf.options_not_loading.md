---
title: "DNS named.conf.options not loading"
date: 2008-07-25
forum: Server Platforms
---

### Post by rgeddes on 2008-07-25
Hi,

I have a DNS server running on my network that services only my private lan with the following named.conf.options file:
```
options {
        directory "/var/cache/bind";
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
        listen-on { 192.168.0.150; };
        listen-on { 127.0.0.1; };
};
```

The other machines on my lan could not find the ipv6 address... tried to figure out ipv6, and ran out of gas or the gas was too expensive/confusing for me... something like that.

Anyway, I decided to have bind also listen on an ipv4 address... I added the 

listen-on { 192.168.0.150; }; 

line to the named.conf.options file.  Reloaded bind9 and everything worked as expected.

On boot up, most of the time, the added line does not take effect.  I have to make bind9 reload the config/options.

Can someone help me either get the ipv6 part straightened out or help me troubleshoot the ipv4 config/option not loading part?   

Thanks
Richard

---

