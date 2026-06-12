---
title: "DNS-Server on Ubuntu not responding to queries from other machines."
date: 2013-06-09
forum: Server Platforms
---

### Post by LarsEbert on 2013-06-09
Edit: Woops, wrong language. I translated it from german to english now.

Hello!

I am trying to setup a small Ubuntu-Server (v12.04.2) to run an Apache. The Apache is up and running, on visiting the IP of the server in a browser on a windows machine in the same network, I receive the "It-Works"-page of apache. So that is not the problem!

I do not want to type in the IP of the server to access the Apache, neither do I want to edit all the clients hosts-files, so I thought I just run a DNS-Server on the Ubuntu-Server. This should make it possible to access the Server through for example [http://advitum](http://advitum), shouldn't it?

When running ```
dig A advitum @192.168.2.19
``` on the server (192.168.2.19 is the servers IP), I get this:

```
; <<>> DiG 9.8.1-P1 <<>> A advitum @192.168.2.19
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 53132
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;advitum.                       IN      A

;; Query time: 0 msec
;; SERVER: 192.168.2.19#53(192.168.2.19)
;; WHEN: Sun Jun  9 14:00:48 2013
;; MSG SIZE  rcvd: 25
```

But when running ```
nslookup advitum 192.168.2.19
``` on the windows-machine in the network, I get:

```
Server: ns.advitum
Address: 192.168.2.19

*** advitum wurde von ns.advitum nicht gefunden: Non-existend domain.
```
(Translation: advitum was not found at ns.advitum...)

The DNS is configured like this:

/etc/bind/named.conf.options
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
                80.69.100.102;
                80.69.100.230;
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

As forwarders I inserted the ISPs DNS-Servers, that is correct, isn't it?

/etc/bind/named.conf.local
```
zone "advitum" {
        type master;
        file "/etc/bind/db.advitum";
};

zone "2.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};
```

/etc/bind/db.advitum
```
$TTL    604800
@       IN      SOA     ns.advitum. info.advitum.de. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.advitum.
@       IN      A       192.168.2.19
advitum IN      A       192.168.2.19
```

/etc/bind/db.192
```
$TTL    604800
@       IN      SOA     ns.advitum. info.advitum.de. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
19      IN      PTR     ns.advitum.
```

I hope, you will be able to help me with this. I am trying for hours now and have no result yet.

Thanks in advance for your help!

---

### Post by Vitsliputsli on 2013-06-09
try this:
/etc/bind/db.advitum
```
$TTL    604800
@       IN      SOA     dns.advitum. root.dns.advitum. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
         IN      NS      loalhost.
         IN      A       127.0.0.0
localhost IN CNAME localhost.
*       IN      A       192.168.2.19
```

---

### Post by LarsEbert on 2013-06-09
Hi Vitsliputsli,

I included your changes and now get the following on the Server:

```
dig advitum @192.168.2.19
```
```
; <<>> DiG 9.8.1-P1 <<>> advitum @192.168.2.19
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18978
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

;; QUESTION SECTION:
;advitum.                       IN      A

;; ANSWER SECTION:
advitum.                604800  IN      A       127.0.0.1

;; AUTHORITY SECTION:
advitum.                604800  IN      NS      localhost.

;; ADDITIONAL SECTION:
localhost.              604800  IN      A       127.0.0.1
localhost.              604800  IN      AAAA    ::1

;; Query time: 0 msec
;; SERVER: 192.168.2.19#53(192.168.2.19)
;; WHEN: Sun Jun  9 15:23:09 2013
;; MSG SIZE  rcvd: 108


```

That looks much better to me, but on the windows machine, nothing changed! Do I have to change something else?

---

### Post by Vitsliputsli on 2013-06-09
Sorry, 
string
         IN      A       127.0.0.0
must be
         IN      A       192.168.2.19
for resolve advitum.

/etc/bind/named.conf.local only for local configuration. Use /etc/bind/named.conf

---

### Post by LarsEbert on 2013-06-09
Thank you for your answer. I changed 127.0.0.1 to 192.168.2.19 and move the zones from named.conf.local to named.conf. But sadly, the nslookup on the windows machine still returns "advitum was not found by ns.advitum: Non-existent domain." Do I have to configure a something else maybe?

Edit: Is it correct that we changed ns.advitum to dns.advitum in db.advitum while in db.192 it still says ns.advitum?

---

### Post by Vitsliputsli on 2013-06-09
Add into /etc/bind/named.conf, into options:
allow-query { 0.0.0.0/0; 127.0.01; };
Correct 0.0.0.0/0 to your sub-net for most security.

Long time I have not use bind, so I forgot many things.

---

### Post by LarsEbert on 2013-06-10
Thank you very much, you have been a great help!
Here's what I added to named.conf.options:

```
allow-query { 255.255.255.0/0; 127.0.0.1; };
```

I am not entirely sure what to add after the Slash. With the 0 it again gives me the result "Non existent domain", with any other number the nslookup-result changes to "Query refused";

On the Server, everything seems to be running fine, on running ```
curl http://advitum
``` it outputs the "It-Works"-page the Apache delivers, but it does not work on the windows machine. Do you have any idea why?

---

### Post by Vitsliputsli on 2013-06-10
0.0.0.0/0 - allow query from all ip. 0.0.0.0 - ip of network, /0 - mask for this network.
127.0.0.1 - local loop back.

For example, if you whant to connect only from ip 192.168.1.1 - 192.168.1.255:
192.168.1.0/24

from 10.0.0.1 - 10.0.255.255:
10.0.0.0/16

---

### Post by LarsEbert on 2013-06-10
Ah, okay. Understood!

I now set the value to 192.168.2.0/24 and 127.0.0.1.
Still I get the response "non-existent domain".

I guess the problem has to be the server. The query seems to reach it, otherwise the error message would not have changed when I had set allow-query to 255.255.255.0/24. In that case, the Query was rejected with "Query refused". So the query at least reaches the server.

I appreciate your help very much. Do you (or anyone else) have any more ideas where to check? It has to be possible to set this up the right way!

Edit: I just discovered by accident that querying for ns.advitum instead of advitum succeeded and delivered the IP of my server, just as well as any other subdomain of advitum. So I guess the problem seems to lie somewhere in /etc/bind/db.advitum (Servers IP was changed from .19 to .2, fyi):

```
            IN    NS        localhost.
            IN    A         192.168.2.2
localhost   IN    CNAME     localhost.
*           IN    A         192.168.2.2
```

---

### Post by Vitsliputsli on 2013-06-10
Check another time:
```
$TTL    604800@       IN      SOA     dns.advitum. root.dns.advitum. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
         IN      NS      advitum.
         IN      A       192.168.2.19
*       IN      A       192.168.2.19
```
String before last for resolve first domain name: advitum.
Last string for resolve second domain name: something.advitum.

---

### Post by LarsEbert on 2013-06-10
Okay, thanks. But it still does not work. Strangely, querying for advitum. instead of advitum results in the correct ip. 
I guess the problem lies somwhere in windows' nslookup. A possible  workaround might be to change advitum to advi.tum or something. I'll try  that tomorrow. It's a shame that just advitum does not work, though...

---

### Post by LarsEbert on 2013-06-10
Edit: Sorry for the double post.

---

### Post by newbie-user on 2013-06-11
Shouldn't you be using a fully qualified domain name in your bind configuration?

Example:
```
$TTL    604800@       IN      SOA     dns.advitum.de root.dns.advitum.de (
```

Also, is your Windows box using your DNS server to do name resolution? Try flushing the DNS cache on the Windows box too:
```
ipconfig /flushdns
```

---

### Post by LarsEbert on 2013-06-13
The Windows-Box definitely uses the correct DNS, when querying for a subdomain of advitum, it gets the right results, just as well as querying for advitum. (with a trailing dot!) I don't want to use something like advitum.de as my goal was to create short, memorably urls only for my local network and I figured that just advitum, without any tld would not result in replacing an existing website (at least locally). My solution (for now) is to use [http://advitum](http://advitum). with a trailing dot, which is kind of ugly but works! If I happen to find another solution in the future, I will be back!

---

### Post by newbie-user on 2013-06-17
Oh, you wanted to be able to resolve hostnames only. I get it now. You have to have your clients automatically append your domain name to any hostname-only search. One way to do this is in the /etc/network/interfaces file with the line:

```
dns-search example.com
```

Another way, IIRC, is to specify the default domain in your DHCP server so that it is distributed to all the clients.

---

### Post by koenn on 2013-06-18
I think newbie is right, it's a matter of  using FQDN.

you've declared a zone advitum and a host advitum, so the FQDN of your server as actually advitum.advitum .  you try that (dig, nslookup), it probably works
You can indeed have clients append a domain name to a hostname automatically so DNS can handle them - in windows it's in the dialog where you set the computer name IIRC. 

about the dots : a dot has meaning in a DNS record (something about appending domain name or not, but i always forget which is which)
IIRC, a dot means that the hostname in the A record is a FQDN, so in your zone file, "advitum"  should not be followed by a dot, because it doesn't have a domain part in its name and is supposed to get its domain from the zone declaration.  
Ask  yourself what DNS stands for.  


FWIW, bind is overkill for this setup. You might want to have a look at dnsmasq. it works like a networked 'hosts' file so the rules are far less strict, and you can have it working in under 5 minutes.

---

### Post by SeijiSensei on 2013-06-19
The trailing dot represents the "root" domain which houses all the top-level domains like com or uk.  It's the DNS equivalent of the root directory /.

---

