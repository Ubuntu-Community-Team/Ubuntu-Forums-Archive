---
title: "Bind failing after Update (Ubuntu 16.04 LTS)"
date: 2017-11-20
forum: Server Platforms
---

### Post by m-dw on 2017-11-20
Hello Forum

Since applying a system update (which included bind) on Sunday (19th November) named has been failing to start as a service. The error in syslog is typically:
```
rndc: connect failed: 127.0.0.1#953: connection refused
```. I haven't made any changes to my bind configuration for a couple of years so naturally I suspect the update to be the trigger, although am prepared to accept a sloppy initial configuration as being the root cause.

In troubleshooting I discovered that bind runs fine as a foreground process (which is how I'm able to post this). I started within a screen session with the command:
```
sudo /usr/sbin/named -u bind -g
```

/etc/bind/named.conf
```
// This is the primary configuration file for the BIND DNS server named.//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local


include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

```

/etc/bind/named.conf.local
```

//
// Do any local configuration here
//


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
//
include "/etc/bind/ddns.key";



zone "haggett.local" {
    type master;
    notify no;
    file "/var/cache/bind/db.haggett.local";
    allow-update { key DDNS_UPDATE; };
};


zone "254.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/var/cache/bind/db.192";
    allow-update { key DDNS_UPDATE; };
};


zone "253.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/var/cache/bind/db.192.168.253";
    allow-update { key DDNS_UPDATE; };
};



```

named.conf.options
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


    forwarders {
        8.8.8.8;
        8.8.4.4;
     };
    //========================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See https://www.isc.org/bind-keys
    //========================================================================
    dnssec-validation auto;


    auth-nxdomain no;    # conform to RFC1035
    //listen-on-v6 { any; };
    allow-query { any; };
};



```

rndc.key is in /etc/bind.
Any ideas what's gone wrong?

---

### Post by m-dw on 2017-11-21
Bump!

---

### Post by m-dw on 2017-11-22
Solved.

There was an errant backtick in /etc/default/bind9. Removed it and works again.

---

