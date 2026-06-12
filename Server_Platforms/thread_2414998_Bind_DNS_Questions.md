---
title: "Bind DNS Questions"
date: 2019-03-18
forum: Server Platforms
---

### Post by elcid91 on 2019-03-18
Greetings All:

I have set up a DNS server for my local netowrk using bind9 at ip 10.x.x.235:
conf.options:
```
options {
        directory "/var/cache/bind";
        auth-nxdomain no;    # conform to RFC1035
        listen-on port 53 { localhost; 10.0.10/24; };
        allow-query { localhost; 10.0.10/24; };
        forwarders { 8.8.8.8; };
        recursion yes;
};

```
forward:
```
$TTL    604800
@        IN    SOA    ns1.arrowleaftech.local. root.arrowleaftech.local. (
                  7        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;


@            IN    NS    ns1.arrowleaftech.local.
arrowleaftech.local    IN    A    10.0.10.236
ns1            IN    A    10.0.10.235
intergyserver        IN    A    10.0.10.202

```reverse:
```
$TTL    604800
@    IN    SOA    arrowleaftech.local.    root.arrowleaftect.local.(
            21         ; Serial
                        604820         ; Refresh
                        864500        ; Retry
                        2419270         ; Expire
                        604880 )       ; Negative Cache TTL


@    IN    NS    ns1.arrowleaftech.local.


;
236    IN    PTR    arrowleaftech.local.
235    IN    PTR    ns1.arrowleaftech.local.
202    IN    PTR    intergyserver.

```

Using a windows machine, I changed the DNS to point to the local network, Flushed the DNS and cleared any cache. The Windows 10 machine tells me it cannot find "nslookup intergyserver".  Is there a step I am missing?  Thanks for any help.

---

### Post by Doug S on 2019-03-19
Try this for forward:

```
$TTL    604800
@        IN    SOA    arrowleaftech.local. root.arrowleaftech.local. (
                  8        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
              IN    A    10.0.10.236

@             IN    NS    ns1.arrowleaftech.local.
ns1           IN    A    10.0.10.235
intergyserver IN    A    10.0.10.202

```
Additionally show us the exact results for your attempts from your windows computer. Examples:
```
C:\Users\Doug>[COLOR="#FF0000"]nslookup s15[/COLOR]
Server:  ns1.smythies.com
Address:  192.168.111.1

Name:    s15.smythies.com
Address:  192.168.111.112


C:\Users\Doug>[COLOR="#FF0000"]nslookup s15.smythies.com[/COLOR]
Server:  ns1.smythies.com
Address:  192.168.111.1

Name:    s15.smythies.com
Address:  192.168.111.112


C:\Users\Doug>[COLOR="#FF0000"]nslookup zxzxzx[/COLOR]
Server:  ns1.smythies.com
Address:  192.168.111.1

*** ns1.smythies.com can't find zxzxzx: Non-existent domain
```
EDIT: Additionally, for these two lines:
```
        listen-on port 53 { localhost; 10.0.10/24; };
        allow-query { localhost; 10.0.10/24; };
```I didn't know the specification could be shortened like that. I would have expected:
```
        listen-on port 53 { localhost; 10.0.10[COLOR="#FF0000"].0[/COLOR]/24; };
        allow-query { localhost; 10.0.10[COLOR="#FF0000"].0[/COLOR]/24; };
```But if that loads and works, I guess I learned something.

---

