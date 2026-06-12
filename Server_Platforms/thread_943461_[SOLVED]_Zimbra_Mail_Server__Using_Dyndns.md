---
title: "[SOLVED] Zimbra Mail Server  Using Dyndns"
date: 2008-10-10
forum: Server Platforms
---

### Post by sil3nt on 2008-10-10
Hey Folks,
          I have recently purchased myself a new domain and rather than have this hosted as I usual do i figure it would be a bit of fun to host my own www and mail server. Since my ISP wont allow static ips without a business plan I am left with my Dynamic IP.

I have purchased 12 months of Custom DNS for my new domain,and I want to get everything setup on my home server. I know this is possible to do but I am unsure what my next step should be.

I am using Ubuntu Server 8.04 LTS and I have BIND9 setup in a chroot environment which is currently providing LAN DNS for my home machines and VM's. 

My First question is do I need to use BIND in conjunction with Dyndns or can I just setup the correct ports to be forwarded for the likes of Zimbra to work correctly?

If I do need to use BIND then obviously I need to setup the named.conf and the associated .db for my external domain DNS, has anyone had experience of this before?

I did find this[post]("http://ubuntuforums.org/showthread.php?t=556249") but because only the "dig" output is shown I am unsure how the .db is supposed to be configured.

Any help or pointers would be great and I am happy to supply any config details in regards to my system if needed.

For kicks here is the part of my current named.conf 
```
zone "mydomain.com"
{
        type master;
        file "/etc/bind/zones/mydomain.com.db"
};

```

I know this config is most definatley wrong but this is what I have in my .db so far:
```
$TTL 1500
@  IN SOA mydomain.com. root (
                             2007062703        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 minutes
@                IN      NS      ns1.mydyndns.org
@                IN      NS      ns2.mydyndns.org
@                IN      NS      ns3.mydyndns.org
@                IN      NS      ns4.mydyndns.org
@                IN      NS      ns5.mydyndns.org
@                IN      A       ns1.mydyndns.org
@                IN      A       ns2.mydyndns.org

```

This may help highlight how much I don't know what I am doing, although my internal DNS config for my local:guitar: domain works a treat ;)

Thanks in advance

---

### Post by sil3nt on 2008-10-14
Just in case anyone ever needs to setup a webserver/mailserver using a dynamic IP like me, I followed this guide along with a little help from the Zimbra forums.

[http://www.tickus.com/?q=node/15]("http://www.tickus.com/?q=node/15")

---

