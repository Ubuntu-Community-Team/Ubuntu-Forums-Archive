---
title: "Bind &amp; Logs"
date: 2013-05-17
forum: Server Platforms
---

### Post by adm2p on 2013-05-17
Hello,

i just virtualized two servers, a Pangolin Precise and a Raring Ringtail, just to learn Bind ;)
The first is master of one zone.lan and the other one is slave.
Everything was ok 'til i wanted to customize logs, the syslog returns

> 
May 17 12:43:24 precise named[1258]: isc_stdio_open '/var/log/update_debug.log' failed: permission denied May 17 12:43:24 precise named[1258]: configuring logging: permission denied May 17 12:43:24 precise named[1258]: loading configuration: permission denied May 17 12:43:24 precise named[1258]: exiting (due to fatal error)


> /var/log/** rw added to > /etc/apparmor.d/usr.sbin.named but not solved
Heres the named.conf.log file
> logging {
        channel update_debug {
                file "/var/log/update_debug.log" versions 3 size 100k;
                severity debug;
                print-severity  yes;
                print-time      yes;
        };
        channel security_info {
                file "/var/log/security_info.log" versions 1 size 100k;
                severity info;
                print-severity  yes;
                print-time      yes;
        };
        channel bind_log {
                file "/var/log/bind.log" versions 3 size 1m;
                severity info;
                print-category  yes;
                print-severity  yes;
                print-time      yes;
        };

        category default { bind_log; };
        category lame-servers { null; };
        category update { update_debug; };
        category update-security { update_debug; };
        category security { security_info; };
};



Im beginning with Ubuntu servers :cool:.
Tia for your answers

---

### Post by SeijiSensei on 2013-05-17
If you are running a "chrooted" server, one where the server runs as the user bind rather than root, then the bind user has to be able to write to /var/log.  I'm not sure how Ubuntu handles this as I use CentOS for servers which has a different BIND chroot structure.

---

### Post by adm2p on 2013-05-17
its not a chrooted server, cos i read it was not useful with the latest versions
Anyway, i've worked on it last night and i just solved the issue 
mkdir /var/log/named
chown bind:bind /var/log/named
bind9 restart
rndc: connect failed: 127.0.0.1#953: connection refused
rndc reload
bind9 restart and..found 3 new files in named dir \\:D/
tnx

---

### Post by adm2p on 2013-06-14
i keep moving with Bind9
get the following error with checkzone on the secondary ns2.zone.lan
everything is ok with the primary ns1.
> named-checkzone zone.lan /var/cache/bind/192.168.165.rev 
/var/cache/bind/192.168.165.rev:3: ignoring out-of-zone data (165.168.192.in-addr.arpa)
/var/cache/bind/192.168.165.rev:13: ignoring out-of-zone data (1.0.0.165.168.192.in-addr.arpa)
/var/cache/bind/192.168.165.rev:14: ignoring out-of-zone data (17.165.168.192.in-addr.arpa)
/var/cache/bind/192.168.165.rev:15: ignoring out-of-zone data (18.165.168.192.in-addr.arpa)
zone zone.lan/IN: has 0 SOA records
zone zone.lan/IN: has no NS records
zone zone.lan/IN: not loaded due to errors.

heres the rev file
> $ORIGIN .
$TTL 10800      ; 3 hours
165.168.192.in-addr.arpa IN SOA ns1.zone.lan. admin.zone.lan. (
                                1          ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                604800     ; minimum (1 week)
                                )
                        NS      ns1.
                        NS      ns2.
$ORIGIN 165.168.192.in-addr.arpa.
1.0.0                  PTR     localhost.
17                      PTR     ns1.zone.lan.
18                      PTR     ns2.zone.lan.

Any clue ?
tia :cool:

---

### Post by Doug S on 2013-06-14
I'm not sure, but my suggestion is this:```
doug@doug-64:~/config/bind/tempd$ [COLOR=#ff0000]cat 192.168.165.rev[/COLOR]
;
; BIND reverse data file for local 192.168.165.XXX net
;
$TTL    10800
@       IN      SOA     ns1.zone.lan. admin.zone.lan. (
                         2013061401     ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.zone.lan.
@       IN      NS      ns2.zone.lan.
17      IN      PTR     ns1.zone.lan.
18      IN      PTR     ns2.zone.lan.
```And to use named-checkzone on a reverse file, you do this:```
doug@doug-64:~/config/bind/tempd$ [COLOR=#ff0000]named-checkzone 165.168.192.in-addr.arpa 192.168.165.rev[/COLOR]
zone 165.168.192.in-addr.arpa/IN: loaded serial 2013061401
OK
doug@doug-64:~/config/bind/tempd$
```

---

### Post by adm2p on 2013-06-16
Tnx for your answer.
Indeed I just discovered that the serial value could be the date ;)
named-checkzone is correct now
i used your suggestion for the rev file and everything is running
tnx again

---

