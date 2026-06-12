---
title: "Setting up a DNS server?"
date: 2010-07-06
forum: Server Platforms
---

### Post by Doulos1 on 2010-07-06
Hello, I am having issues setting up Bind9  setup according to the instructions found in these forums (conf files  to follow).

**1.**  dig doulos-usa.com gives> ; <<>> DiG 9.7.0-P1 <<>> doulos-usa.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 13810
;; flags: qr aa rd ra; QUERY: 1, **ANSWER: 0**, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;doulos-usa.com.                        IN      A

;; AUTHORITY SECTION:
doulos-usa.com.         38400   IN      SOA     ns1.doulos-usa.com. crcheek1.gmail.com. 2010070402 28800 3600 604800 38400

;; Query time: 0 msec
;; SERVER: 192.168.1.8#53(192.168.1.8)
;; WHEN: Tue Jul  6 12:54:13 2010
;; MSG SIZE  rcvd: 87

Whereas dig [www.doulos-usa]("http://www.doulos-usa") returns:> ; <<>> DiG 9.7.0-P1 <<>> [www.doulos-usa.com]("http://www.doulos-usa.com")
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 36064
;; flags: qr aa rd ra; QUERY: 1, **ANSWER: 1**, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;[www.doulos-usa.com]("http://www.doulos-usa.com").            IN      A

;; ANSWER SECTION:
[www.doulos-usa.com]("http://www.doulos-usa.com").     604800  IN      A       192.168.1.8

;; AUTHORITY SECTION:
doulos-usa.com.         604800  IN      NS      ns1.doulos-usa.com.

;; ADDITIONAL SECTION:
ns1.doulos-usa.com.     604800  IN      A       192.168.1.8

;; Query time: 0 msec
;; SERVER: 192.168.1.8#53(192.168.1.8)
;; WHEN: Tue Jul  6 12:58:08 2010
;; MSG SIZE rcvd: 96

**2.**  doulos-usa.com cannot be found internally, but [www.doulos-usa.com]("http://www.doulos-usa.com/")  is found. 
Neither one can be found externally.  I want this website to be able to be accessed from the internet.

nslookup doulos-usa.com gives me > Server:         192.168.1.8
Address:        192.168.1.8#53

*** Can't find doulos-usa.com: No answer
whereas nslookup [www.doulos-usa.com]("http://www.doulos-usa.com") returns:> root@ubuntu-server:~# nslookup [www.doulos-usa.com]("http://www.doulos-usa.com")
Server:         192.168.1.8
Address:        192.168.1.8#53

Name:   [www.doulos-usa.com]("http://www.doulos-usa.com")
Address: 192.168.1.8
/etc/apache2/doulos-usa.com```
<VirtualHost 192.168.1.8:80>
    ServerName doulos-usa.com
    ServerAdmin crcheek1@gmail.com
    ServerAlias www.doulos-usa.com
    DocumentRoot /home/doulosusa/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /home/doulosusa/public_html/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/doulosusa/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```**/etc/bind/named.conf.local**```

zone "doulos-usa.com" {
        type master;
        file "/etc/bind/zones/doulos-usa.com.db";
        };


zone "1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.1.168.192.in-addr.arpa.db";
};

```**/etc/bind/zones/doulos-usa.com.db**```
doulos-usa.com.      IN      SOA     ns1.doulos-usa.com. me.myemail.com. (
                                                        2010070402
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )
doulos-usa.com.      IN      NS              ns1.doulos-usa.com.
www              IN      A       192.168.1.8
ns1              IN      A       192.168.1.8

```**/etc/bind/zones/rev.1.168.192.in-addr.arpa.db**```
@ IN SOA ns1.doulos-usa.com. me.myemail.com. (
2010070401;
28800;
604800;
604800;
86400
)

@ IN NS ns1.doulos-usa.com.
8 IN PTR doulos-usa.com.

```I have registered my nameserver and set my nameserver for doulos-usa.com at my domain registrar (godaddy).

Any help would be appreciated.

---

### Post by Bachstelze on 2010-07-06
> **Doulos1 said:**
> **/etc/bind/zones/doulos-usa.com.db**```
doulos-usa.com.      IN      SOA     ns1.doulos-usa.com. me.myemail.com. (
                                                        2010070402
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )
doulos-usa.com.      IN      NS              ns1.doulos-usa.com.
www              IN      A       192.168.1.8
ns1              IN      A       192.168.1.8

```

If you want [font=monospace]doulos-usa.com.[/font] to resolve, you need to add an A record for it:

```
doulos-usa.com.    IN    A    192.168.1.8
```

---

### Post by Ryan Dwyer on 2010-07-06
To make your DNS settings accessible from the outside, you need to update your nameservers to your public IP address, not your private IP address. And forward the port.

---

### Post by Doulos1 on 2010-07-06
> **Ryan Dwyer said:**
> To make your DNS settings accessible from the outside, you need to update your nameservers to your public IP address, not your private IP address. And forward the port.
Are you telling me I need to use my external ip address for all these records instead of 192.168.1.8 ??

I registered my nameservers at godaddy to my real ipaddress, and changed my nameservers for doulos-usa.com (at godaddy) to ns1.doulos-usa.com.  My router is forwarding port 80 to 192.168.1.8.  Also, port 53 forwarded to 192.168.1.8.

---

### Post by Doulos1 on 2010-07-06
> **Bachstelze said:**
> If you want [FONT=monospace]doulos-usa.com.[/FONT] to resolve, you need to add an A record for it:

```
doulos-usa.com.    IN    A    192.168.1.8
```

Thanks, that now shows >  nslookup doulos-usa.com
Server:         192.168.1.8
Address:        192.168.1.8#53

Name:   doulos-usa.com
Address: 192.168.1.8

When I do.. named-checkconf doulos-usa.com.db I get this:> named-checkconf /etc/bind/zones/doulos-usa.com.db
/etc/bind/zones/doulos-usa.com.db:1: unknown option 'doulos-usa.com.'
/etc/bind/zones/doulos-usa.com.db:11: unexpected token near end of file

---

### Post by Bachstelze on 2010-07-06
> **Doulos1 said:**
> Thanks, that now shows When I do.. named-checkconf doulos-usa.com.db I get this:

You must use named-checkzone to check your zone files. named-checkconf is for named.conf et al..

---

### Post by Doulos1 on 2010-07-06
thank you, [Bachstelze]("http://ubuntuforums.org/member.php?u=51114"). 

named-checkzone -d doulos-usa.com doulos-usa.com.db shows> named-checkzone -d doulos-usa.com doulos-usa.com.db
loading "doulos-usa.com" from "doulos-usa.com.db" class "IN"
doulos-usa.com.db:1: no TTL specified; using SOA MINTTL instead
doulos-usa.com.db:11: file does not end with newline
zone doulos-usa.com/IN: loaded serial 2010070404
OK



---

### Post by Doulos1 on 2010-07-07
OK, I changed all my network IP's to my real IP and now the site can be accessed from outside.

However, for some reason doulos-usa.com get routed to my default site at /var/www, while [www.doulos-usa.com](www.doulos-usa.com) goes to the actual website at /home/doulos-usa/public_html.

Any idea why?  I changed nothing in /etc/apache2/sites-available/doulos-usa.com.

Do I need to change the virtual host from 192.168.1.8:80 to myrealipaddress:80?

---

### Post by Ryan Dwyer on 2010-07-07
Change your VitualHost statement from <VirtualHost 192.168.1.8:80> to <VirtualHost *:80>

---

### Post by Doulos1 on 2010-07-07
Ok, thanks, it is working now.

---

