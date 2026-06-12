---
title: "Bind9 configuration for a workgroup"
date: 2013-05-16
forum: Server Platforms
---

### Post by WilJenMM on 2013-05-16
I just built Ubuntu Server and installed Bind9.  I can ping from this server externally via name, yet all internal servers come back as unknown host.  I can ping internally via IP.     I noted that all the configuration examples listed machines with a fully qualified domain name.  I only have a peer to peer workgroup.  How should the configuration be altered to work with this?    My zones SOA start like this:  @  IN   SOA dnssvr. mail.localhost. (  ...      later with a reference to the server itself  @  IN  NS dnssvr.   ... later followed by the A records for servers in my DMZ.    Likewise my reverse zones also only list the hostname followed only by a period.  The syslog lists no errors and all the zones are loaded.    Suggestions for modifications?  Suggestions on how to test?

---

### Post by SeijiSensei on 2013-05-16
> **WilJenMM said:**
> I just built Ubuntu Server and installed Bind9.  I can ping from this server externally via name, yet all internal servers come back as unknown host.

Do you have A records for each machine in your zone file?  That's the only solution to this unless you build a combined BIND/DHCP server and implement automatic zone updates when addresses are assigned to client machines.  Otherwise you need to populate the zone file manually.

As for the reverse zones, you'll just get back whatever appears in the appropriate PTR record.  If you have,
```
1   IN   PTR   jillspc.
```
the you'll just get "jillspc." back in a query.  If you want to have the reverse zone return fully-qualified domain names like "jillspc.example.com" you need to put that in the PTR record.

---

### Post by WilJenMM on 2013-05-16
Attached are my zones and a dig.  A ping responds unknown host dmztest   I am not sure that my resolv.conf should list the search extodlaw and nameserver (ip of extodlaw) plus and external isp dns server.

---

### Post by SeijiSensei on 2013-05-16
First off, given how client-side DNS is configured in 12.04 and later releases, you need to put your search list and DNS resolvers into /etc/network/interfaces like this.  
```

iface eth0 inet static
    address 192.168.3.3
    netmask 255.255.255.0
    gateway 192.168.3.1
    dns-search example.com
    dns-nameservers 192.168.3.45 192.168.8.10

```
Don't forget the "s" on "dns-nameservers".  It's a common mistake.

If you are not using static addressing on the clients, then you must put this information into the router or server that handles DHCP requests for your network.

Next, you have an NS record that points to the host extodlaw, but no corresponding A record for that hostname.  You need an A record for that hostname with the IP address of the nameserver.

See if that helps.

---

### Post by WilJenMM on 2013-05-20
I added the IP of odlaw (the Ubuntu nameservers) to eth0 and restarted.  I still have name resolution externally only.  All my devices have static IP's.  I also added the A record for odlaw.  Still no local name resolution.    My named.conf.options lists my ISP's dns servers under forwarders.  Should I have my local server's IP in there?  I used named-checkzone to test my zones.  My forward zone showed loaded to serial 2 and ok and my reverse zone loads to serial 1 and ok.    Other ideas why local resolution?

---

### Post by WilJenMM on 2013-05-20
I just did the command: sudo tcpdump -vvv -s 1600 -i any port 53       I went to another machine in my dmz which is pointed to odlaw as the dns server and tried pinging odlaw.  Watching the capture I see that it never tried internally and went straight out to the ISP then root servers.  I checked to make sure Bind9 was running and no errors in the syslog.  both were good.  when I did a named-checkconf -p /etc/bind/named.conf I see the all the zones. the file shows all the zones.  Not sure why it is not looking internally.

---

### Post by WilJenMM on 2013-05-20
the output of a dig to lookup a local machine listed with an A record on this dns server.  The server responding is my ISP's dns server.

---

### Post by Doug S on 2013-05-21
By default "dig" does not append the search domain to the name upon submission of the request to the DNS. You would have had to either do this:```
dig dmztest.extodlaw
```or this```
dig +search dmztest
```I do not think your reverse zone file will not work because it does not know what sub-net it is a reverse zone file for. I am saying that this:```
zone "rev.ext.dmz" {
        type master;
        file "/etc/bind/rev.ext.dmz";
};
```should be something like this:```
zone "1.168.192.in-addr.arpa" { type master; notify no; file "/etc/bind/rev.ext.dmz"; };
```

---

### Post by WilJenMM on 2013-05-21
I went back and renamed the reverse zone as suggested.  Still not processing.  I do note an error message in syslog which I attached a screen shot.  Found one reference to delete the file /var/cache/bind/managed-keys.bind    Deleted the file and restarted.  Same results and error.  Included are two dig +search.  Lost what to do next.

---

### Post by Doug S on 2013-05-21
Your system doesn't seem to know the default domain is extodlaw, as per Seinji's postings as few back. Here is an example from one of my computers:```
doug@s15:~/sguide-1304/doug_docs5$ [COLOR=#ff0000]dig +search s10[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> +search s10
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: [COLOR=#ff0000]NOERROR[/COLOR], id: 38148
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
[COLOR=#ff0000];s10.smythies.com.[/COLOR]              IN      A

;; ANSWER SECTION:
s10.smythies.com.       604800  IN      A       192.168.111.102

;; AUTHORITY SECTION:
smythies.com.           604800  IN      NS      ns1.smythies.com.

;; ADDITIONAL SECTION:
ns1.smythies.com.       604800  IN      A       192.168.111.1

;; Query time: 0 msec
;; SERVER: 192.168.111.1#53(192.168.111.1)
;; WHEN: Tue May 21 15:42:04 2013
;; MSG SIZE  rcvd: 84
``````
doug@s15:~/sguide-1304/doug_docs5$ [COLOR=#ff0000]dig s10[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> s10
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: [COLOR=#ff0000]NXDOMAIN[/COLOR], id: 6035
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;[COLOR=#ff0000]s10.[/COLOR]                           IN      A

;; AUTHORITY SECTION:
.                       10800   IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2013052101 1800 900 604800 86400

;; Query time: 143 msec
;; SERVER: 192.168.111.1#53(192.168.111.1)
;; WHEN: Tue May 21 15:43:36 2013
;; MSG SIZE  rcvd: 96
```Of course you would only use the "+search" option for your internal lookups, not [www.google.com]("http://www.google.com") as per one of your screen shots.

---

### Post by Doug S on 2013-05-21
Try this for your forward file:```
;
; BIND data file for internal domain extodlaw
;
$TTL    604800
@       IN      SOA     extodlaw. mail.extodlaw. (
                        2013052100      ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800 )        ; Negative Cache TTL
                IN      A       192.168.1.XXX
;
@               IN      NS      ns.extodlaw.
ns              IN      A       192.168.1.XXX
extspam02       IN      A       192.168.1.3
lsspamctrl01    IN      A       192.168.1.143
dmztest         IN      A       192.168.1.17
```Replace XXX with the actual address of the name server computer. I have never tried to do a one word domain name before, so am not sure about this suggestion.

---

