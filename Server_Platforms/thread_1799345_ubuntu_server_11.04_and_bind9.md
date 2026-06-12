---
title: "ubuntu server 11.04 and bind9"
date: 2011-07-07
forum: Server Platforms
---

### Post by Athens on 2011-07-07
Hello and thanks for taking the time to read my request. I've recently tried configuring bind9 on ubuntu server 11.04 with a bind configuration I have used and performed countless times. My configuration has two views "internal" and "external". Now my problem is I can always ping or perform a lookup on the zones defined in the first view, however zones in the second view will timeout. If I switch the order of the views, I can then perform a lookup on the previously *dead* zone and now can no longer lookup or ping the zones from the previous view. I did not have this problem with previous releases of bind, so maybe there is something I am missing? The ironic thing is, I am getting this same result on just about every distro I have tried to install over the last couple of days. This current setup is working fine on 10.02 LTS, however, I have not updated bind to the most current version in fear of this issue.

***/etc/bind/named.conf:***
```

acl internals { localhost; localnets; };

include "/etc/bind/named.conf.options";

view "internal"
{
    match-clients { internals; };
    recursion yes;
    notify no;

    include "/etc/bind/named.conf.local";
    include "/etc/bind/named.conf.default-zones";
};
view "external"
{
    match-clients { any; };
    recursion no;
    notify yes;

    include "/etc/bind/named.conf.external";
};

```***/etc/bind/named.conf.options***
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

    auth-nxdomain no;    # conform to RFC1035

    listen-on { any; };
    listen-on-v6 { any; };

    managed-keys-directory "/var/lib/bind/keys";
    
    dnssec-enable yes;
    dnssec-validation yes;
    dnssec-lookaside auto;
};

```***/etc/bind/named.conf.local***
```

include "/etc/bind/zones.rfc1918";

zone "mydomain.local" {
    type master;
    file "/var/lib/bind/mydomain.local.db";
};

```***/etc/bind/named.conf.external***
```

zone "mydomain.com" {
    type master;
    file "/etc/bind/master/mydomain.com.db";
};
zone "mydomain.us" {
    type master;
    file "/etc/bind/master/mydomain.us.db";
};

```***/var/lib/bind/mydomain.local.db***
```

$TTL 172800
mydomain.local.        IN SOA    olympus.mydomain.local. hostmaster.mydomain.com. (
                2011070601
                3H
                1H
                1W
                1H
                )
;
mydomain.local.        IN NS    olympus.mydomain.local.
mydomain.local.        IN A    172.16.1.2
olympus            IN A    172.16.1.2

```**/etc/bind/master/mydomain.com.db**
```

$TTL 172800
mydomain.com.        IN SOA    olympus.mydomain.com. hostmaster.mydomain.com. (
                2011070601
                604800
                86400
                2419200
                604800
                )
;
mydomain.com.        IN NS    olympus.mydomain.com.
mydomain.com.        IN A    172.16.1.253
olympus            IN A    172.16.1.253

```**/etc/bind/master/mydomain.us.db**
```

$TTL 172800
mydomain.us.        IN SOA    olympus.mydomain.us. hostmaster.mydomain.us. (
                2011070601
                604800
                86400
                2419200
                604800
                )
;
mydomain.us.        IN NS    olympus.mydomain.us.
mydomain.us.        IN A    172.16.1.253
olympus            IN A    172.16.1.253

```Any help would be greatly appreciated!

NOTE: Updated and attached debug log for someone who has more seasoned eyes.

---

### Post by Athens on 2011-07-07
I have this working now, seems it was always working, but could not ping these domains from the server itself. So I added my internal and copies of my external zones (pointing to the server instead of the external ip) to a new view only available to the localhost. This must be a new requirement for the current release of bind? I've never had to do this until now.

I found a good article here: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch18_:_Configuring_DNS#Configuring_BIND_Views_in_named.conf](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch18_:_Configuring_DNS#Configuring_BIND_Views_in_named.conf)

---

