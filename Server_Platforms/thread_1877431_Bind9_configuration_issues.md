---
title: "Bind9 configuration issues"
date: 2011-11-08
forum: Server Platforms
---

### Post by antoine.quinson on 2011-11-08
Hi,

So first of all I'm using a custom version of Ubuntu ```
Linux version 2.6.24-29-eole (eole@hardy32) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4))
``` but really i don't think there's any difference besides the name.

So here goes: I told my boss I could create a DNS server for our intranet, and now I'm feeling kind of silly because it's not as easy as I imagined on Linux ! I did some googling, read some threads here and there and it helped me progress toward making it work, but I feel like I need one more push from you guys.

Here are the relevant config files :

named.conf
```

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
    type hint;
    file "/etc/bind/db.root";
};

    zone "lsw42.fr" {
        type master;
        file "/etc/bind/db.lsw42.fr";
    };

    zone "16.172.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.172";
    };

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

include "/etc/bind/named.conf.local";

```db.lsw42.fr
```
$ORIGIN lsw42.fr
;
; Parametres du serveur BIND
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ns.lsw42.fr. admin.lsw42.fr. (
            11072011        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )        ; Negative Cache TTL
;
; Enregistrements INternet
;
;
@    IN    NS    ns.lsw42.fr.        ; Serveur NS du domaine
ns    IN    A    172.16.0.242        ; Addresse IP de ns.lsw42.fr
admin    IN    A    172.16.0.1        ; Addresse du poste admin
mail    IN    MX    172.16.0.242        ; 
```db.172
```
;
; BIND reverse data file for 172 area
;
$TTL    604800
@    IN    SOA    ns.lsw42.fr. admin.lsw42.fr. (
            07112011        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@        IN    NS    ns
172.16.0.242    IN    PTR    ns.lsw42.fr.

```named.conf.local
```

key "rndc-key" {
      algorithm hmac-md5;
      secret "[REDACTED]";
};

controls {
      inet 127.0.0.1 port 953
              allow { 127.0.0.1; } keys { "rndc-key"; };
};

```Running named-checkconf does not give any errors, and trying to run bind9 gives this:

```
root@srv-lsw42:~# service bind9 restart
 * Stopping domain name service... bind                                         rndc: connection to remote host closed
This may indicate that
* the remote server is using an older version of the command protocol,
* this host is not authorized to connect,
* the clocks are not syncronized, or
* the key is invalid.
                                                                         [fail]
 * Starting domain name service... bind                                  [ OK ]

```Please help ?

---

### Post by cconstantine on 2011-11-08
Not a direct solution, but you should consider a different style for your serial numbers in your SOA records.

SOA is only an integer in Bind's point of view. If the serial number has not INCREASED bind won't reload your zone's data.

So when you change the serial, you want to read it as a date, but it has to be an always-increasing integer. If you use YYYYMMDDNN then it will work. The serial number format you seem to be using has various dates where the new serial is a smaller integer. Eg, Nov 9 2012 (09112012) is less than Oct 10, 2011 (10102011). Also it is usual to add a two digit "serial number" on the right so you can do more than 10 revisions of a zone in one day.

First rev on nov 30 2011: 2011113000
Second rev same day: 2011113001
Next day: 2011120100
Feb of 2012: 2012020100

As for the failure to stop bind: make sure rndc is working. (ref its man page.) If you've a firewall, make sure traffic to/from the local host is allowed (check syslog's kern facility log.) Also look in Daemon facility for logs from Bind.

---

### Post by SeijiSensei on 2011-11-08
I usually delete the [rndc]("http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-bind-rndc.html") stanza from named.conf since I don't use the rndc app.

My other quick observation is that you need to revise the reverse domain.  Reverse zones are based on the first three "octets" of the IP address.  In named.conf you'd have:

```

zone "0.16.172.in-addr.arpa" {
     type master;
     file "/path/to/the/zone/file";
}:

```

and the zone file has entries like this:

```

1      IN    PTR    admin.lsw42.fr.
242    IN    PTR    ns.lsw42.fr.
```

---

### Post by antoine.quinson on 2011-11-09
Okay, so I think I have the configuration files down now, thanks to you. I deleted everything and restarted from scratch following your advice and some more I found online instead of using file templates I found here and there.

rndc starts properly now, but at the end of the process it says it couldn't connect to the remote host. Here's the error message:

```
root@srv-lsw42:~# rndc -V reload
create memory context
create socket manager
create task manager
create task
create logging context
setting log tag
creating log channel
enabling log channel
create parser
get key
decode base64 secret
reload
post event
using server 127.0.0.1 (127.0.0.1#953)
create socket
bind socket
connect
create message
render message
schedule recv
send message
rndc: connection to remote host closed
This may indicate that
* the remote server is using an older version of the command protocol,
* this host is not authorized to connect,
* the clocks are not syncronized, or
* the key is invalid.
```

So what exactly does it mean when it says the remote server ? I'm using SSH to connect to the server because I don't feel like dressing up in winter clothes to go to the server room, so does that mean that's the remote server ? I doubt it, but hey better ask. Or is it another remote server it's talking about ? If so, exactly which one, and how do I find out, so I can ask the firewall guys to open a port for me.

---

### Post by cconstantine on 2011-11-09
rndc can attempt to connect to any name server you wish to control. So when rndc says "remote server" it means the one you asked it to remotely control. If you don't specify on the command line, you get the remote server at host 'localhost' -- which in this case is the server you want to control.

You need to read and understand the rndc man page. Look at those errors from rndc -- probably not the protocol version one, because your named and rndc were installed together. Check your on-box firewall rules, check your syslog DAEMON facility logs to see what named said. You probably need to adjust your named config to allow the rndc to control it. Something like this, usually in your /etc/bind/named.conf.local file:

```
// controls and TSIG key for the "rndc" command line program...
controls {
	inet 127.0.0.1 allow { localhost; } keys { rndc-key; };
};
include "/etc/bind/rndc.key";
```

---

