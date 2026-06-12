---
title: "DNS: NS has no address records (A or AAAA)"
date: 2011-10-27
forum: Server Platforms
---

### Post by veggis on 2011-10-27
Hey

have a dns problem (first time setting up dns)
Cant ping example.LAN
/var/log/syslog
NS has no address records (A or AAAA)

/etc/bind/zones/db.example.LAN
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    peter.example.LAN. root.example.LAN. (
            2011102704    ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    peter.example.LAN.
@    IN    A    192.168.1.10
ns    IN    A    192.168.1.10
@    IN    AAAA    ::1

/etc/bind/named.conf.local
zone "example.LAN"
{
    type master;
    file "/etc/bind/zones/db.example.LAN";
};
zone "1.168.192.in-addr.arpa"
{
    type master;
    notify no;
    file "/etc/bind/zones/db.192";
};

someone see anything wrong here? or need more info?

---

### Post by SeijiSensei on 2011-10-27
> zone "example.LAN"
{
type master;
file "/etc/bind/zones/db.example.LAN";
};

You're writing the zone file for "example.lan" not the zone "peter.example.lan".  So just remove the "peter." from the various statements in the zone file and try again.

---

### Post by veggis on 2011-10-27
peter is the name of the server, so it shall not be
@ IN SOA nameserver.example.LAN. root.example.LAN. ?
         (peter)?
Will try when I`m back at work

---

### Post by SeijiSensei on 2011-10-27
No, the entry in the SOA record should refer to the domain example.lan.  If you want to name a host peter.example.lan, you'd need an A record like this:

```
peter     IN     A    192.168.1.10
```

What you probably want is something like

```

@         IN   SOA    example.lan     you.somewhere.com {
               stuff
               }

          IN   NS      peter.example.lan.

peter     IN   A       192.168.1.10
ns        IN   CNAME   peter


```

That creates an A record for peter.example.lan that points to 192.168.1.10.  The NS record shows it's used as the nameserver for example.lan.  I also created an alias for "peter.example.lan" as "ns.example.lan" using a CNAME declaration.  That's not required, just convenient.

---

### Post by veggis on 2011-10-28
Thank you for the help its now working

---

### Post by SeijiSensei on 2011-10-28
You're welcome.  Please mark this thread as SOLVED.

---

### Post by DMJ on 2012-02-01
Solved? Hardly. Please make sure you know what you're talking about before answering questions here. You're misleading more than one person when you answer incorrectly.

SOA = start of authority.

The SOA line designates the the top-level authoritative DNS server in your domain. The syntax is:

<domain> IN SOA  <top-level name server> <admin email address>

Examples:

example.com. IN SOA dns1.example.com. admin.example.com.

@ IN SOA dns1.example.com. admin.example.com.

@ is shorthand for your domain. You can use @ because it's value is given in named.conf or named.conf.local. 

So your SOA line is correct. Your problem is elsewhere in the zone file. The error message suggests that your A and AAAA records are all incorrect.

The way you're using @, it looks like you don't quite understand what it's for. Do some reading on it. If your still stuck, re-post.

These forums can be very helpful, but they're no substitute for doing your homework.

---

### Post by DMJ on 2012-02-02
PS Please change the status of your thread to unsolved.

---

