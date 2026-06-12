---
title: "Inconsistent VirtualHost behavior with Apache 2.2.22 on 12.04 LTS"
date: 2013-11-17
forum: Server Platforms
---

### Post by patrick.kramer on 2013-11-17
I recently integrated four domains to my my Ubuntu server 12.04 VPS Apache2 system and I am running into inconsistent behavior across 2 of the domains using near identical implementations:

[TABLE="class: grid, width: 700, align: left"]
[TR]
[TD](cross-sections are linked)[/TD]
[TD]**domain.tld**[/TD]
[TD]**www .domain.tld**[/TD]
[/TR]
[TR]
[TD]**meton.net**[/TD]
[TD]**[[COLOR=#00cc00]Work[/COLOR]]("http://meton.net")[[COLOR=#00cc00]ing[/COLOR]]("http://meton.net")**[/TD]
[TD]**[[COLOR=#00cc00]Work[/COLOR]]("http://www.meton.net")[[COLOR=#00cc00]ing[/COLOR]]("http://www.meton.net")**[/TD]
[/TR]
[TR]
[TD]**cloudnvr.net**[/TD]
[TD]**[[COLOR=#00cc00]Work[/COLOR]]("http://cloudnvr.net")[[COLOR=#00cc00]ing[/COLOR]]("http://cloudnvr.net")**[/TD]
[TD]**[[COLOR=#00cc00]Work[/COLOR]]("http://www.cloudnvr.net")[[COLOR=#00cc00]ing[/COLOR]]("http://www.cloudnvr.net")**[/TD]
[/TR]
[TR]
[TD]**kramerdynamics.com**[/TD]
[TD]**[[COLOR=#00cc00]Work[/COLOR]]("http://kramerdynamics.com")[[COLOR=#00cc00]ing[/COLOR]]("http://kramerdynamics.com")**[/TD]
[TD]**[[COLOR=#b22222]Broken[/COLOR]]("http://www.kramerdynamics.com")**[/TD]
[/TR]
[TR]
[TD]**localizehouston.co **(no typo)[/TD]
[TD]**[[COLOR=#00cc00]Work[/COLOR]]("http://localizehouston.co")[[COLOR=#00cc00]ing[/COLOR]]("http://localizehouston.co")**[/TD]
[TD]**[[COLOR=#b22222]Broken[/COLOR]]("http://www.localizehouston.co")**[/TD]
[/TR]
[/TABLE]









The following code block is a cat dump of my /etc/apache2/sites-available/ directory; the patterns between the files are template.

```
root@server1:/etc/apache2/sites-available# tail -n +1 -- *
==> cloudnvr.net.conf <==
<VirtualHost *:80>
    DocumentRoot /var/www/cloudnvr.net
    DirectoryIndex index.html


    ServerName     "cloudnvr.net"
    ServerAlias "www.cloudnvr.net"


    LogLevel    Warn
    ErrorLog    /var/log/vhosts/cloudnvr.error.log
    CustomLog   /var/log/vhosts/cloudnvr.access.log combined
</VirtualHost>


==> kramerdynamics.com.conf <==
<VirtualHost *:80>
    DocumentRoot /var/www/kramerdynamics.com
    DirectoryIndex index.html


    ServerName     "kramerdynamics.com"
    ServerAlias "www.kramerdynamics.com"


    LogLevel    Warn
    ErrorLog    /var/log/vhosts/kramerdynamics.error.log
    CustomLog   /var/log/vhosts/kramerdynamics.access.log combined
</VirtualHost>


==> localizehouston.co.conf <==
<VirtualHost *:80>
    DocumentRoot /var/www/localizehouston.co
    DirectoryIndex index.html


    ServerName     "localizehouston.co"
    ServerAlias "www.localizehouston.co"


    LogLevel    Warn
    ErrorLog    /var/log/vhosts/localizehouston.error.log
    CustomLog   /var/log/vhosts/localizehouston.access.log combined
</VirtualHost>


==> meton.net.conf <==
<VirtualHost *:80>
    DocumentRoot /var/www/meton.net
    DirectoryIndex index.html


    ServerName     "meton.net"
    ServerAlias "www.meton.net"


    LogLevel    Warn
    ErrorLog    /var/log/vhosts/meton.error.log
    CustomLog   /var/log/vhosts/meton.access.log combined
</VirtualHost>



```

I am losing some precious hair on this; Why do the longer domains fail when linking to the www .domain.tld?

---

### Post by Doug S on 2013-11-17
Isn't the problem a dns issue and not an apache issue?```
doug@doug-64:~$ [COLOR=#ff0000]ping meton.net[/COLOR]
PING meton.net (173.245.5.174) 56(84) bytes of data.
64 bytes from 173.245.5.174: icmp_req=1 ttl=52 time=110 ms
64 bytes from 173.245.5.174: icmp_req=2 ttl=52 time=110 ms
64 bytes from 173.245.5.174: icmp_req=3 ttl=52 time=109 ms
^C
--- meton.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2010ms
rtt min/avg/max/mdev = 109.977/110.164/110.277/0.133 ms
doug@doug-64:~$ [COLOR=#ff0000]ping www.meton.net[/COLOR]
PING meton.net (173.245.5.174) 56(84) bytes of data.
64 bytes from 173.245.5.174: icmp_req=1 ttl=52 time=111 ms
64 bytes from 173.245.5.174: icmp_req=2 ttl=52 time=109 ms
^C
--- meton.net ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2002ms
rtt min/avg/max/mdev = 109.944/110.726/111.508/0.782 ms
doug@doug-64:~$ [COLOR=#ff0000]ping cloudnvr.net[/COLOR]
PING cloudnvr.net (173.245.5.174) 56(84) bytes of data.
64 bytes from 173.245.5.174: icmp_req=1 ttl=52 time=284 ms
64 bytes from 173.245.5.174: icmp_req=3 ttl=52 time=169 ms
^C
--- cloudnvr.net ping statistics ---
4 packets transmitted, 2 received, 50% packet loss, time 3006ms
rtt min/avg/max/mdev = 169.384/226.791/284.198/57.407 ms
doug@doug-64:~$ [COLOR=#ff0000]ping www.cloudnvr.net[/COLOR]
PING cloudnvr.net (173.245.5.174) 56(84) bytes of data.
64 bytes from 173.245.5.174: icmp_req=1 ttl=52 time=110 ms
64 bytes from 173.245.5.174: icmp_req=2 ttl=52 time=110 ms
^C64 bytes from 173.245.5.174: icmp_req=3 ttl=52 time=110 ms

--- cloudnvr.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 110.123/110.162/110.233/0.386 ms
doug@doug-64:~$ [COLOR=#ff0000]ping kramerdynamics.com[/COLOR]
PING kramerdynamics.com (173.245.5.174) 56(84) bytes of data.
64 bytes from 173.245.5.174: icmp_req=1 ttl=52 time=111 ms
64 bytes from 173.245.5.174: icmp_req=2 ttl=52 time=110 ms
^C
--- kramerdynamics.com ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2002ms
rtt min/avg/max/mdev = 110.977/111.203/111.430/0.403 ms
doug@doug-64:~$ [COLOR=#ff0000]ping www.kramerdynamics.com[/COLOR]
ping: [COLOR=#ff0000]unknown host www.kramerdynamics.com[/COLOR]
doug@doug-64:~$ [COLOR=#ff0000]ping kramerdynamics.com[/COLOR]
PING kramerdynamics.com (173.245.5.174) 56(84) bytes of data.
64 bytes from 173.245.5.174: icmp_req=1 ttl=52 time=110 ms
64 bytes from 173.245.5.174: icmp_req=2 ttl=52 time=111 ms
^C
--- kramerdynamics.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 110.668/110.919/111.171/0.417 ms
doug@doug-64:~$ [COLOR=#ff0000]ping www.kramerdynamics.com[/COLOR]
ping: [COLOR=#ff0000]unknown host www.kramerdynamics.com[/COLOR]
doug@doug-64:~$ ^C
doug@doug-64:~$ [COLOR=#ff0000]ping localizehouston.co[/COLOR]
PING localizehouston.co (173.245.5.174) 56(84) bytes of data.
64 bytes from 173.245.5.174: icmp_req=1 ttl=52 time=111 ms
64 bytes from 173.245.5.174: icmp_req=2 ttl=52 time=110 ms
^C
--- localizehouston.co ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 110.967/111.131/111.295/0.164 ms
doug@doug-64:~$ [COLOR=#ff0000]ping www.localizehouston.co[/COLOR]
ping: [COLOR=#ff0000]unknown host www.localizehouston.co[/COLOR]
```

Oh, by the way, welcome to Ubuntu forums.

---

### Post by patrick.kramer on 2013-11-18
I actually don't know.... I have a just a bit more than functional understanding of DNS, I am using godaddy's DNS manager service to manage the DNS entries; I simply added an **A @ 173.245.5.174** entry to each domain and removed all the auto garbage that godaddy adds. 
 
I was using mod_rewrite before but that made the whole www .domain.tld column fail, I moved to the **sites-available -> a2ensite** method after that and the shorter domains started to work.  

I don't understand why the other two are failing.

Any advice on how to manage the issue via DNS?

---

### Post by Doug S on 2013-11-18
There does not appear to be any DNS records for the two that are not working. There does seem to be a lot of junk in the DNS records for the domains. The two that work have CNAME records, the two that do not work do not have CNAME (or A) records.```
doug@doug-64:~$ [COLOR=#ff0000]dig -t any  www.meton.net[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> -t any www.meton.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, [COLOR=#ff0000]status: NOERROR[/COLOR], id: 8052
;; flags: qr rd ra; QUERY: 1, [COLOR=#ff0000]ANSWER: 2[/COLOR], AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;www.meton.net.                 IN      ANY

;; ANSWER SECTION:
www.meton.net.          3317    IN      RRSIG   CNAME 8 3 3600 20131130073239 20131115073239 45498 meton.net. fYFsWvehqKx6nptrsivWnSnsL5qjNaibDA20WyJhgTCxFiOu0sbnWWYo 1BO5hwt9u6NEZXUrV9kmcJu6jSJnNVaLBx00BUH3kDYWSz6z6JWxhUjm EsOpbiqUNrEmk9saFr3OboJFYq9Iv88EgTeTfOUIpGJILZYUAcbh/pja 7jg=
[COLOR=#ff0000]www.meton.net.          3317    IN      CNAME   meton.net.[/COLOR]

;; AUTHORITY SECTION:
meton.net.              3295    IN      NS      pdns04.domaincontrol.com.
meton.net.              3295    IN      NS      pdns03.domaincontrol.com.

;; Query time: 3 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Nov 17 21:58:16 2013
;; MSG SIZE  rcvd: 273
``````
doug@doug-64:~$ [COLOR=#ff0000]dig -t any www.cloudnvr.net[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> -t any www.cloudnvr.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, [COLOR=#ff0000]status: NOERROR[/COLOR], id: 13857
;; flags: qr rd ra; QUERY: 1, [COLOR=#ff0000]ANSWER: 2[/COLOR], AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;www.cloudnvr.net.              IN      ANY

;; ANSWER SECTION:
www.cloudnvr.net.       3373    IN      RRSIG   CNAME 8 3 3600 20131202212804 20131117212804 50670 cloudnvr.net. gUWQHCtPYvEo0/93xDNhnEH1rTP6zoVAwOrjay0HMVPAU6zcd4MKdBSH RYijipEqOLVsp84wayefZNKUw1u5fVKup7DwTJcvP2Shi+/8/VifVnBL IhClOufnQWO79tisyAQ9MIoGmDQx0a+awNqWLiAbwMCxi3ZwrCsZMPDq PY4=
[COLOR=#ff0000]www.cloudnvr.net.       3373    IN      CNAME   cloudnvr.net.[/COLOR]

;; AUTHORITY SECTION:
cloudnvr.net.           3357    IN      NS      pdns03.domaincontrol.com.
cloudnvr.net.           3357    IN      NS      pdns04.domaincontrol.com.

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Nov 17 21:59:14 2013
;; MSG SIZE  rcvd: 279
``````
doug@doug-64:~$ [COLOR=#ff0000]dig -t any www.localizehouston.co[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> -t any www.localizehouston.co
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, [COLOR=#ff0000]status: NXDOMAIN[/COLOR], id: 17121
;; flags: qr rd ra; QUERY: 1, [COLOR=#ff0000]ANSWER: 0[/COLOR], AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;www.localizehouston.co.                IN      ANY

;; AUTHORITY SECTION:
localizehouston.co.     3082    IN      SOA     pdns03.domaincontrol.com. dns.jomax.net. 2013111601 28800 7200 604800 600

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Nov 17 22:00:04 2013
;; MSG SIZE  rcvd: 113
``````
doug@doug-64:~$ [COLOR=#ff0000]dig -t any www.kramerdynamics.com[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> -t any www.kramerdynamics.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, [COLOR=#ff0000]status: NXDOMAIN[/COLOR], id: 21077
;; flags: qr rd ra; QUERY: 1, [COLOR=#ff0000]ANSWER: 0[/COLOR], AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;www.kramerdynamics.com.                IN      ANY

;; AUTHORITY SECTION:
kramerdynamics.com.     600     IN      SOA     pdns03.domaincontrol.com. dns.jomax.net. 2013111701 28800 7200 604800 600

;; Query time: 106 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Nov 17 22:02:28 2013
;; MSG SIZE  rcvd: 110
```

---

### Post by patrick.kramer on 2013-11-18
Ah I see the issue, the CNAME entries of the broken [www.*]("http://www.*") domains were missing the **www **points to **@ **entries.

Thanks for the dig examples, i'll use that tool in the future check my DNS records; It's also cool to see the RRSIG records for DNSSEC.
 
```
root@server1:~# [COLOR=#ff0000]dig -t any [/COLOR][COLOR=#ff0000]www.kramerdynamics.com[/COLOR][COLOR=#ff0000]
[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> -t any www.kramerdynamics.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, [COLOR=#ff0000]status: NOERROR[/COLOR], id: 48467
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;www.kramerdynamics.com.                IN      ANY


;; ANSWER SECTION:
[COLOR=#ff0000]www.kramerdynamics.com[/COLOR][COLOR=#ff0000]. 3600    IN      CNAME   kramerdynamics.com.[/COLOR]
[COLOR=#dda0dd]www.kramerdynamics.com[/COLOR][COLOR=#dda0dd]. 3600    IN      RRSIG   CNAME 8 3 3600 20131203070141 20131118070141 15354 kramerdynamics.com. u+hD7R+JIoObOrqerGpJGR4DWnYDUnIBCQjeZlCzZKA/fiNbIH3YqBJz kuJf4VbF7ZNzg98JZCLDE841rWsGQikuY40XzKpQMWfJALUZ0WsfvNeu cm9xJJK0kGukfZoCGY6KKLKh3amscbBHwm+mBzJwrY3qkXaS+v0mxVJx 4I4=[/COLOR]


;; Query time: 19 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Nov 18 02:22:44 2013
;; MSG SIZE  rcvd: 232

```

```
root@server1:~# [COLOR=#ff0000]dig -t any www.localizehouston.co[/COLOR]


; <<>> DiG 9.8.1-P1 <<>> -t any www.localizehouston.co
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, [COLOR=#ff0000]status: NOERROR[/COLOR], id: 48230
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;www.localizehouston.co.                IN      ANY


;; ANSWER SECTION:
[COLOR=#ff0000]www.localizehouston.co. 1627    IN      CNAME   localizehouston.co.[/COLOR]


;; Query time: 9 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Nov 18 02:37:33 2013
;; MSG SIZE  rcvd: 54
```

---

