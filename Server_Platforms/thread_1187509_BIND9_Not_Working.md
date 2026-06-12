---
title: "BIND9 Not Working"
date: 2009-06-14
forum: Server Platforms
---

### Post by magicman5421 on 2009-06-14
I have a server running BIND9, which I just installed. I have checked and double-checked everything, but I don't know enough about DNS to spot something I may have done wrong. nslookup of any host on my network returns Open-DNS(which I'm using)'s ip address. What am I doing wrong?

Relevant files follow:

/etc/bind/named.conf.local
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "mysite.net"{
type master;
file "/etc/bind/zones/mysite.net.db";
};

zone "1.168.192.in-addr.arpa"{
type master;
file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};
```

/etc/bind/named.conf.options
```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        // query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                208.67.222.222; //Open-DNS
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
```

/etc/bind/zones/mysite.net.db
```
$TTL 1500
mysite.net. IN SOA ns.mysite.net. (
                             2007062703        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 minutes
mysite.net.      IN      NS      ns.mysite.net.
ns      IN      A       192.168.1.2
router        IN      A      192.168.1.1
mysite.net.      IN      MX      10    mail.mysite.net.
```

/etc/bind/zones/rev.1.168.192.in-addr.arpa
```
$TTL 1500
@  IN SOA ns.mysite.net. (
                             2007062703        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 minutes

                    IN    NS     ns.mysite.net.
2                  IN    PTR    ns.mysite.net.
1                  IN    PTR    router.mysite.net.
```

All the computers on my network recognize 192.168.1.2 as the DNS, and the windows computers confusingly are able to ping ns and get a response from 192.168.1.2, but the non-windows computers (2 linux, 2 mac), when the ping ns, receive replies from Open-DNS. nslookup also returns Open-DNS.

What am I doing wrong?

---

### Post by hictio on 2009-06-15
Have you checked the logs?
Re init the bind9 service, and then check the log file '/var/log/daemon.log', like this:

```

sudo less /var/log/daemon.log

```

It will ask your password, to get out of the less paginator, and get back to get the CLI, type 'q'.

---

### Post by magicman5421 on 2009-06-16
I tried to re-init bind9 and this is what came up.
```
admin@ns:~$ sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind                                         rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [fail]
 * Starting domain name service... bind                                  [ OK ] 
admin@ns:~$
```

I then ran nmap on my server with bind9 supposedly running:

```
admin@ns:~$ nmap localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2009-06-16 09:56 EDT
Interesting ports on localhost.localdomain (127.0.0.1):
Not shown: 1704 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
80/tcp    open  http
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
3306/tcp  open  mysql
5901/tcp  open  vnc-1
6001/tcp  open  X11:1
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.055 seconds
admin@ns:~$
```

Also, this is the last entry in daemon.log (it's from 2 days ago)

```
Jun 14 17:34:55 ns named[4960]: shutting down: flushing changes
Jun 14 17:34:55 ns named[4960]: stopping command channel on 127.0.0$
Jun 14 17:34:55 ns named[4960]: stopping command channel on ::1#953
Jun 14 17:34:55 ns named[4960]: no longer listening on ::#53
Jun 14 17:34:55 ns named[4960]: no longer listening on 127.0.0.1#53
Jun 14 17:34:55 ns named[4960]: no longer listening on 192.168.1.2#$
Jun 14 17:34:55 ns named[4960]: exiting
```

---

### Post by drave on 2009-06-16
that looks like named is not running. what do you get if you

sudo named -f -d 10

---

### Post by magicman5421 on 2009-06-16
If I run that, nothing pops up in the terminal window. However, port 53 does open, and it writes to daemon.log. Now the next problem is the log itself. Apparently there's an unexpected end of input before the eol.

```

Jun 16 12:51:55 ns named[14724]: isc_log_open 'named.run' failed: permission denied
Jun 16 12:51:55 ns named[14724]: starting BIND 9.4.2-P2 -d 10
Jun 16 12:51:55 ns named[14724]: found 2 CPUs, using 2 worker threads
Jun 16 12:51:55 ns named[14724]: loading configuration from '/etc/bind/named.conf'
Jun 16 12:51:55 ns named[14724]: listening on IPv6 interfaces, port 53
Jun 16 12:51:55 ns named[14724]: listening on IPv4 interface lo, 127.0.0.1#53
Jun 16 12:51:55 ns named[14724]: listening on IPv4 interface eth0, 192.168.1.2#53
Jun 16 12:51:55 ns named[14724]: automatic empty zone: 254.169.IN-ADDR.ARPA
Jun 16 12:51:55 ns named[14724]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Jun 16 12:51:55 ns named[14724]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Jun 16 12:51:55 ns named[14724]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jun 16 12:51:55 ns named[14724]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jun 16 12:51:55 ns named[14724]: automatic empty zone: D.F.IP6.ARPA
Jun 16 12:51:55 ns named[14724]: automatic empty zone: 8.E.F.IP6.ARPA
Jun 16 12:51:55 ns named[14724]: automatic empty zone: 9.E.F.IP6.ARPA
Jun 16 12:51:55 ns named[14724]: automatic empty zone: A.E.F.IP6.ARPA
Jun 16 12:51:55 ns named[14724]: automatic empty zone: B.E.F.IP6.ARPA
Jun 16 12:51:55 ns named[14724]: none:0: open: /etc/bind/rndc.key: permission denied
Jun 16 12:51:55 ns named[14724]: couldn't add command channel 127.0.0.1#953: permission denied
Jun 16 12:51:55 ns named[14724]: none:0: open: /etc/bind/rndc.key: permission denied
Jun 16 12:51:55 ns named[14724]: couldn't add command channel ::1#953: permission denied
Jun 16 12:51:55 ns named[14724]: zone 0.in-addr.arpa/IN: loaded serial 1
Jun 16 12:51:55 ns named[14724]: zone 127.in-addr.arpa/IN: loaded serial 1
Jun 16 12:51:55 ns named[14724]: dns_rdata_fromtext: /etc/bind/zones/rev.1.168.192.in-addr.arpa:7: near eol: unexpected end of input
Jun 16 12:51:55 ns named[14724]: zone 1.168.192.in-addr.arpa/IN: loading from master file /etc/bind/zones/rev.1.168.192.in-addr.arpa failed: unexpected end of input
Jun 16 12:51:55 ns named[14724]: zone 255.in-addr.arpa/IN: loaded serial 1
Jun 16 12:51:55 ns named[14724]: zone localhost/IN: loaded serial 2
Jun 16 12:51:55 ns named[14724]: dns_rdata_fromtext: /etc/bind/zones/mysite.net.db:7: near eol: unexpected end of input
Jun 16 12:51:55 ns named[14724]: zone mysite.net/IN: loading from master file /etc/bind/zones/mysite.net.db failed: unexpected end of input
Jun 16 12:51:55 ns named[14724]: running
```

---

### Post by binary10 on 2009-06-16
You might want to fix your eols by adding the domain address of the maintainer to your Start Of Authority line.

In your mysite.net.db 
Instead of:
```
mysite.net. IN SOA ns.mysite.net. (
```

Use:
```

mysite.net. IN SOA ns.mysite.net. postmaster.mysite.net. (

```

Then make a likewise change to your reverse file.


As for your /etc/bind/rndc.key file error, does it exist ? User bind:bind should be able to touch file in that directory if not.. touch it and set some non-world readable access on it.

---

