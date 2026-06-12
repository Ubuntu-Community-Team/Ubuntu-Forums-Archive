---
title: "DNS server not working"
date: 2013-03-08
forum: Server Platforms
---

### Post by baicunko on 2013-03-08
Hello!
I've been trying to configure my own server but I'm currently stuck and I don't know what else to try.
I've got a domain ganganadores.cl and I'm trying to host my own DNS servers.
I'm using ISPConfig 3 and Bind9. I've used the guide from [http://www.howtoforge.com/perfect-server-ubuntu-12.10-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.10-apache2-bind-dovecot-ispconfig-3)
For some reason the DNS server is not working, if I try pinging ganganadores.cl I get an error as the server can't be found.
[http://www.intodns.com/ganganadores.cl](http://www.intodns.com/ganganadores.cl) shows the same thing.
What can I be doing wrong? here is my ISPConfig.

---

### Post by darkod on 2013-03-08
I don't know ISPConfig but in general I would start checking from the start.

1. First of all ask yourself whether you need your own DNS or not? Usually you can do everything you need in your registrar's control panel.

2. If you do want to use your own DNS, you have to set the registrar control panel to use your own nameservers. Did you do this?

---

### Post by baicunko on 2013-03-08
I need my own DNS server as my registrar sucks. If you check intodns.com you can see that the nameservers are registered but for some reasons they won't work!

---

### Post by darkod on 2013-03-08
Where is the server located? Is it possible the ISP blocks the ports needed?

Have you tried looking into the bind9 config files directly in terminal? Don't rely only on GUI, especially when you have problems.

Look into the config files of bind9 and compare them with this basic setup for example:
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

---

### Post by baicunko on 2013-03-09
I've fixed everything but I'm facing a last error.
This is being shown in my system logs
ar  9 02:03:14 server1 named[1157]: client 190.160.0.42#25767: query (cache) 'intodns.ganganadores.cl/A/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 200.83.1.179#52282: query (cache) 'ganganadores.cl/NS/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 190.160.0.42#45744: query (cache) 'intodns.ganganadores.cl/A/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 200.83.1.179#28479: query (cache) 'server1.ganganadores.cl/A/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 190.160.0.42#24819: query (cache) 'intodns.ganganadores.cl/A/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 200.83.1.179#65365: query (cache) 'ganganadores.cl/NS/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 200.83.1.179#35208: query (cache) 'server1.ganganadores.cl/A/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 190.160.0.42#55152: query (cache) 'ganganadores.cl/NS/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 190.160.0.42#59647: query (cache) 'server1.ganganadores.cl/A/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 200.83.1.179#56031: query (cache) 'ganganadores.cl/NS/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 200.83.1.179#39468: query (cache) 'server1.ganganadores.cl/A/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 190.160.0.42#36045: query (cache) 'ganganadores.cl/NS/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 190.160.0.42#19981: query (cache) 'server1.ganganadores.cl/A/IN' denied
Mar  9 02:03:14 server1 named[1157]: client 190.160.0.42#47111: query (cache) 'ganganadores.cl/NS/IN' denied



Why is this ocurring?

---

### Post by baicunko on 2013-03-09
OK, seems that my configuration got all screwed. I restarted bind and got this:
```
Mar  9 02:45:18 server1 named[5795]: zone 255.in-addr.arpa/IN: loaded serial 1
Mar  9 02:45:18 server1 named[5795]: zone ganganadores.cl/IN: NS 'server1.ganganadores.cl' has no address records (A or AAAA)
Mar  9 02:45:18 server1 named[5795]: zone ganganadores.cl/IN: NS 'server2.ganganadores.cl' has no address records (A or AAAA)
Mar  9 02:45:18 server1 named[5795]: zone ganganadores.cl/IN: not loaded due to errors.
Mar  9 02:45:18 server1 named[5795]: zone localhost/IN: loaded serial 2


```
here is my named.conf
```

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
named.conf.local
```
                                                         
zone "ganganadores.cl" {
        type master;
        file "/etc/bind/pri.ganganadores.cl.err";
        allow-transfer { any; };
        allow-query { any; };
        allow-update { any; };
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

        // forwarders {
        //      0.0.0.0;
        // };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```
and finally
/etc/bind/pri.ganganadores.cl.err
```
$TTL        3600
@       IN      SOA     server1.ganganadores.cl. elguru.soiuncrack.cl. (
                        2013030901       ; serial, todays date + todays serial #
                        7200              ; refresh, seconds
                        540              ; retry, seconds
                        604800              ; expire, seconds
                        86400 )            ; minimum, seconds
;

ganganadores.cl. 3600 A        200.74.52.17
ganganadores.cl. 3600      MX    10   mail.ganganadores.cl.
ganganadores.cl. 3600      NS        server1.ganganadores.cl.
ganganadores.cl. 3600      NS        server2.ganganadores.cl.
mail 3600 A        200.74.52.17
www 3600 A        200.74.52.17

```
I don't know what else to do. I've tryed everything!!!!

---

### Post by darkod on 2013-03-09
How about if you modify /etc/bind/pri.ganganadores.cl.err according to the link I posted into:
```
......
ganganadores.cl.  IN  NS  server1.ganganadores.cl.
ganganadores.cl.  IN  NS  server2.ganganadores.cl.

ganganadores.cl.  IN  MX  10  mail.ganganadores.cl.
ganganadores.cl.  IN  A  xxx.xxx.xxx.xxx

server1  IN  A  xxx.xxx.xxx.xxx
server2  IN  A  xxx.xxx.xxx.xxx
www  IN  CNAME  ganganadores.cl.
mail  IN  A  xxx.xxx.xxx.xxx
```

See if that changes anything. If we compare these two files (and the tutorial), you can notice that you didn't define server1 and server2 as A records. I think that is necessary, but I'm no expert in bind9 to know if that is what's missing for your setup to work.
But you definitely need to define them as A records, otherwise how will they be used. You have them set as NS (nameservers) for the domain but when a query tries to reach that nameserver, how can it reach it without an A record that specifies the public IP to look for?

---

### Post by SeijiSensei on 2013-03-09
Did you read the error?  You have no A records for server1 or server2.  You need both an NS record that points to the DNS server by name, and a separate A record for the server's address.  

```

@     IN NS ns1.example.com.

ns1   IN A    192.168.1.1

```

---

### Post by baicunko on 2013-03-09
Thanks!! For some reason ISPConfig wasn't making automatically the A records.
Now it works like a charm!! =)

---

### Post by darkod on 2013-03-09
> **baicunko said:**
> Thanks!! For some reason ISPConfig wasn't making automatically the A records.

That's the problem with many GUI admin tools. That's why they are rarely recommended.

---

