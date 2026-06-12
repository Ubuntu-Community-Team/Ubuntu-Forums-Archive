---
title: "bind9 fails to start"
date: 2012-01-29
forum: Server Platforms
---

### Post by satimis on 2012-01-29
Hi all,

Ubuntu server 1010 64bit running as VM on Orcle Virtualbox.

I followed;
DNS (bind9) Configuration HowTo
[http://glonek.co.uk/linux-server/dns-bind9-configuration-howto/](http://glonek.co.uk/linux-server/dns-bind9-configuration-howto/)

to config bind9.  It went through w/o problem.

On restarting bind9;
# /etc/init.d/bind9 restart```

 * Stopping domain name service... bind9
   ...done.
 * Starting domain name service... bind9
   ...fail!

```

$ tail /var/log/syslog ```

Jan 29 16:43:33 server1 named[2467]: /etc/bind/named.conf.local:9: unknown option 'zone'
Jan 29 16:43:33 server1 named[2467]: /etc/bind/named.conf.local:14: unknown option 'zone'
Jan 29 16:43:33 server1 named[2467]: /etc/bind/named.conf.default-zones:2: unknown option 'zone'
Jan 29 16:43:33 server1 named[2467]: /etc/bind/named.conf.default-zones:10: unknown option 'zone'
Jan 29 16:43:33 server1 named[2467]: /etc/bind/named.conf.default-zones:15: unknown option 'zone'
Jan 29 16:43:33 server1 named[2467]: /etc/bind/named.conf.default-zones:20: unknown option 'zone'
Jan 29 16:43:33 server1 named[2467]: /etc/bind/named.conf.default-zones:25: unknown option 'zone'
Jan 29 16:43:33 server1 named[2467]: /etc/bind/named.conf:12: '}' expected near end of file
Jan 29 16:43:33 server1 named[2467]: loading configuration: unexpected token
Jan 29 16:43:33 server1 named[2467]: exiting (due to fatal error)

```

$ cat /etc/bind/named.conf.local ```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "server1.domain.com" {
        type master;
        file "/etc/bind/zones/server1.domain.com.db";
};

zone "0.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};

```

Pls help.  TIA

B.R.
satimis

---

### Post by e79 on 2012-01-29
> 29 16:43:33 server1 named[2467]: **/etc/bind/named.conf**:12: '}' expected near end of file

post your named.conf:

```
cat /etc/bind/named.conf
```

---

### Post by satimis on 2012-01-29
> **e79 said:**
> post your named.conf:

```
cat /etc/bind/named.conf
```

$ cat /etc/bind/named.conf```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

```

Thanks

Edit-1:

$ cat /etc/bind/named.conf.options ```

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
        //      0.0.0.0;
        // };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
allow-recursion { 127.0.0.1; 192.168.24.0/24;
};

```


$ cat /etc/bind/named.conf.default-zones ```

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

```


Edit-2;

# nano /etc/bind/named.conf.options
change the line;```

allow-recursion { 127.0.0.1; 192.168.24.0/24;

```

as;```

allow-recursion { 127.0.0.1; 192.168.24.0/24; };

```

# /etc/init.d/bind9 restart```

 * Stopping domain name service... bind9
   ...done.
 * Starting domain name service... bind9
   ...done.

```

Problem solved.  Thanks


B.R.
satimis

---

### Post by e79 on 2012-01-30
I'm glad you could sort it out.

Cheers

---

### Post by satimis on 2012-01-30
> **e79 said:**
> I'm glad you could sort it out.

Cheers
Hi,

Still there is a minor problem discovered.  I'll start another thread.

satimis

---

### Post by andrewhamming on 2013-03-02
Is it possible to get the tutorial [https://help.ubuntu.com/12.04/serverguide/dns-configuration.html](https://help.ubuntu.com/12.04/serverguide/dns-configuration.html)
updated to get people to edit /etc/bind/named.conf.options rather then /etc/bind/named.conf as this results in errors.

If you change forwarders options in named.conf.options everything runs sweet first go ;)

Thanks

---

### Post by Doug S on 2013-03-02
@ andrewhamming: Please explain in more detail, It already says to edit the named.conf.options file to set or change forwarders, so I don't understand what the issue is.
Anyway, if you still have an issue with the serverguide you would like to see fixed, then please fill out a bug report on Launchpad. However also check as maybe it already got fixed in the 12.10 version. Sometimes changes do not get back ported, even though 12.04 is LTS. Note that changes for the 13.04 release cycle close in just a few weeks now, but all the edits that are already pending aren't progressing well.

---

### Post by andrewhamming on 2013-03-02
My bad,

After re-reading i noticed the .option on end.

Thanks for checking up tho,
this is a great community you guys have here, I spend hours browsing these forums and finding answers ;)

Hammommah

---

