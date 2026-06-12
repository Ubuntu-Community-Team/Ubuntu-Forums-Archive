---
title: "bind9 error on Ubuntu 12.04 headless server"
date: 2013-11-12
forum: Server Platforms
---

### Post by brent1975 on 2013-11-12
Hello, I have a brand new headless ubuntu 12.04 server standing. The server is configured to my specs outside of two elements. bind9 and iptables. Naturally I leave iptables as the last object on my to-do-list. It keeps me from having to trouble shoot the firewall when I come across an issue.

I wanted to install bind as a cache local dns server.  I have created a forward using google's DNS (8.8.8.8) and my server is set statically. For some reason from my server I am unable to ping any device on my network. I could use a new set of eyes on this. I am sure I am missing something small. Any assistance would be much appreciated.

Lets dive in shall we...

my FQDN for this server is: Server1.linux.local  

Here is my Interfaces file:
```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static


                address 192.168.2.110
                netmask 255.255.255.0
                network 192.168.2.0
                gateway 192.168.2.1
                broadcast 192.168.2.255




        dns-nameservers 192.168.2.110
        dns-search linux.local
        dns-domain linux.local


pre-up iptables-restore < /etc/iptables.rules
post-down iptables-save > /etc/iptables.rules
```


Step 1
         Setting up DNS forward
      [B]sudo nano /etc/bind/named.conf.options
                    
[/B] ```
options {        directory "/var/cache/bind";


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
        listen-on-v6 { any; };
};



```


Step 2
                 [B][U]Creating the Zones.
[/U][/B] 
             [B]sudo nano /etc/bind/named.conf.local
[/B]
```
/// Do any local configuration here
//


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


zone "linux.local" {
             type master;
             file "/etc/bind/db.linux.local";
        };


zone "2.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};



```

Step 3

      [B][U]Building DNS forward Zones


[/U][/B]                         ```
**sudo cp /etc/bind/db.local /etc/bind/db.linux.local**
```
                         ```
**sudo nano /etc/bind/db.linux.local**
```
```
;; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     Server1.linux.local.  root.localhost. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      Server1.linux.local.
@       IN      A       127.0.0.1
@       IN      AAAA    ::1


;Below are A Record Addresses


firewall        IN      A       192.168.2.1
Server1         IN      A       192.168.2.110
Printer         IN      A       192.168.2.135


; Below are CNAME Record Addresses (Aliases) - Point to an A Record Address


Server1         IN      CNAME   Server1.linux.local.
firewall        IN      CNAME   firewall.linux.local.
printer         IN      CNAME   printer.linux.local.
```


Step 4
          Building a Reverse Lookup

                    [B]sudo cp /etc/bind/db.127 /etc/bind/db.192
[/B]
```
;; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     Server1.linux.local. root.localhost. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      Server1.linux.local.
1       IN      PTR     firewall.linux.local.
110     IN      PTR     Server1.linux.local.
135     IN      PTR     printer.linux.local.
```

I have at this point restarted bind9 with no errors.

When I dig firewall, Server1, and printer I get no results.
```
; <<>> DiG 9.8.1-P1 <<>> firewall.linux.local;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 57615
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;firewall.linux.local.          IN      A


;; Query time: 0 msec
;; SERVER: 192.168.2.110#53(192.168.2.110)
;; WHEN: Tue Nov 12 09:33:12 2013
;; MSG SIZE  rcvd: 38
```



Here are the results of pinging my local devices. Server is working. not sure why it's coming back as loopback 127.0.0.1
```
brent@Server1:~$ ping Server1 -c 4PING Server1 (127.0.1.1) 56(84) bytes of data.
64 bytes from Server1 (127.0.1.1): icmp_req=1 ttl=64 time=0.024 ms
64 bytes from Server1 (127.0.1.1): icmp_req=2 ttl=64 time=0.016 ms
64 bytes from Server1 (127.0.1.1): icmp_req=3 ttl=64 time=0.020 ms
64 bytes from Server1 (127.0.1.1): icmp_req=4 ttl=64 time=0.018 ms


--- Server1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.016/0.019/0.024/0.005 ms
brent@Server1:~$ ping firewall -c 4
ping: unknown host firewall
brent@Server1:~$ ping printer -c 4
ping: unknown host printer
```

---

### Post by Doug S on 2013-11-12
> **brent1975 said:**
> ... I have at this point restarted bind9 with no errors ...Are you sure? Search for "named" in /var/log/kern.log and/or /var/log/syslog. The file db.linux.local does not pass named-checkzone test. Delete the CNAME records, the last 3 lines and try again.```
doug@doug-64:~/config/bind/tempg$ [COLOR=#ff0000]named-checkzone linux.local db.linux.local[/COLOR]
dns_master_load: db.linux.local:27: Server1.linux.local: CNAME and other data
dns_master_load: db.linux.local:28: firewall.linux.local: CNAME and other data
dns_master_load: db.linux.local:29: printer.linux.local: CNAME and other data
zone linux.local/IN: loading from master file db.linux.local failed: CNAME and other data
zone linux.local/IN: not loaded due to errors.
doug@doug-64:~/config/bind/tempg$ nano db.linux.local  [COLOR=#ff0000]<<< deleted CNAME lines[/COLOR]
doug@doug-64:~/config/bind/tempg$ [COLOR=#ff0000]named-checkzone linux.local db.linux.local[/COLOR]
zone linux.local/IN: loaded serial 2
[COLOR=#ff0000]OK[/COLOR]
doug@doug-64:~/config/bind/tempg$
```Suggest [the ubuntu server guide]("https://help.ubuntu.com/13.10/serverguide/dns.html") as a reference.

---

### Post by chrisguk on 2013-11-12
```
sudo ufw allow 53
```  comes to mind.  This is the port for DNS

---

### Post by brent1975 on 2013-11-12
I commented out the 3 CNAME's I also found that I had an error in my hosts file. 

I can now ping the 3 devices.

```
brent@Server1:~$ ping firewall -c 1PING firewall.linux.local (192.168.2.1) 56(84) bytes of data.
64 bytes from firewall.linux.local (192.168.2.1): icmp_req=1 ttl=64 time=0.314 ms


--- firewall.linux.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.314/0.314/0.314/0.000 ms
brent@Server1:~$ ping server1 -c 1
PING server1.linux.local (192.168.2.110) 56(84) bytes of data.
64 bytes from Server1.linux.local (192.168.2.110): icmp_req=1 ttl=64 time=0.019 ms


--- server1.linux.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.019/0.019/0.019/0.000 ms
brent@Server1:~$ ping printer -c 1
PING printer.linux.local (192.168.2.135) 56(84) bytes of data.
64 bytes from printer.linux.local (192.168.2.135): icmp_req=1 ttl=64 time=14.0 ms


--- printer.linux.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 14.064/14.064/14.064/0.000 ms
```

NSLOOKUP looks good...
```
brent@Server1:~$ nslookup firewallServer:         192.168.2.110
Address:        192.168.2.110#53


Name:   firewall.linux.local
Address: 192.168.2.1


brent@Server1:~$ nslookup server1
Server:         192.168.2.110
Address:        192.168.2.110#53


Name:   server1.linux.local
Address: 192.168.2.110


brent@Server1:~$ nslookup printer
Server:         192.168.2.110
Address:        192.168.2.110#53


Name:   printer.linux.local
Address: 192.168.2.135



```


Thanks, Everything appears to be good to go now.

---

