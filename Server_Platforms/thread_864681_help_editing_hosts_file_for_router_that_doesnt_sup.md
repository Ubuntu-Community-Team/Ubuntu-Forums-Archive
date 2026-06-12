---
title: "help editing hosts file for router that doesnt support DNS loopback"
date: 2008-07-19
forum: Server Platforms
---

### Post by semiliko on 2008-07-19
hi all,

i am trying to get sphider (php search engine @ [www.sphider.eu](www.sphider.eu)) to work on my website on my home server. my router does not support DNS loopback and i am having some difficulty resolving my external ip to my local webserver. i am trying to edit my hosts file (/etc/hosts) to rectify this. 

to start with my details are;
OS: Ubuntu 8.04 (Hardy Heron) Server edition
Sphider version: 1.3.4
Router: Netcomm NB5Plus4W
external ip address: 220.233.xxx.xxx
hostname: ubuntuserver, on port 8080 [I chose port 8080 because 80 wasn't working (possibly blocked by my ISP?)]
static ip address of webserver on LAN: 192.168.1.10
ip address of modem on LAN: 192.168.1.1

the following are the contents of my hosts file:
127.0.0.1	localhost
127.0.1.1	ubuntuserver
192.168.1.10	220.233.xxx.xxx
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


I get the following results in my browser:
[http://220.233.xxx.xxx/](http://220.233.xxx.xxx/) = router login page
[http://220.233.xxx.xxx:8080/](http://220.233.xxx.xxx:8080/) = failed to connect error message
[http://ubuntuserver:8080/](http://ubuntuserver:8080/) = webserver index.html
[http://localhost:8080/](http://localhost:8080/) = webserver index.html

to create the correct keywords and links for sphider, i need to set sphider to index my external ip address, and therein lies the problem. Since DNS loopback is not allowed through the router, sphider running on a computer within the LAN can't index my website using the external ip. it does work however if i set it to index [http://localhost:8080/](http://localhost:8080/), but that of course is of no use to outside users.

the following is a printout of the sphider log when trying to index my external ip address:

Spidering [http://220.233.xxx.xxx:8080](http://220.233.xxx.xxx:8080)
1. Retrieving: [http://220.233.xxx.xxx:8080](http://220.233.xxx.xxx:8080) at 10:43:00.
Connection refused NOHOST
Links found: 0. New links: 0



the following are wget and dig outputs for my external ip address:

wget [http://220.233.xxx.xxx](http://220.233.xxx.xxx)
--10:45:17--  [http://220.233.xxx.xxx/](http://220.233.xxx.xxx/)
           => `index.html.1'
Connecting to 220.233.xxx.xxx:80... connected.
HTTP request sent, awaiting response... 200 Ok
Length: 4,683 (4.6K) [text/html]
100%[====================================>] 4,683         --.--K/s             
10:45:17 (1.83 MB/s) - `index.html.1' saved [4683/4683]


wget [http://220.233.xxx.xxx:8080](http://220.233.xxx.xxx:8080)
--10:49:46--  [http://220.233.xxx.xxx:8080/](http://220.233.xxx.xxx:8080/)
           => `index.html.3'
Connecting to 220.233.xxx.xxx:8080... failed: Connection refused.


wget [http://ubuntuserver:8080](http://ubuntuserver:8080)
--10:50:09--  [http://ubuntuserver:8080/](http://ubuntuserver:8080/)
           => `index.html.3'
Resolving ubuntuserver... 127.0.1.1
Connecting to ubuntuserver|127.0.1.1|:8080... connected.
HTTP request sent, awaiting response... 200 OK
Length: 800 [text/html]
100%[====================================>] 800           --.--K/s             
10:50:09 (44.35 MB/s) - `index.html.3' saved [800/800]


dig [http://220.233.xxx.xxx](http://220.233.xxx.xxx)
; <<>> DiG 9.4.2-P1 <<>> [http://220.233.xxx.xxx](http://220.233.xxx.xxx)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 18209
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available
;; QUESTION SECTION:
;[http://220.233.xxx.xxx](http://220.233.xxx.xxx).		IN	A
;; Query time: 4043 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Jul 20 10:45:40 2008
;; MSG SIZE  rcvd: 40

dig [http://220.233.xxx.xxx:8080](http://220.233.xxx.xxx:8080)
; <<>> DiG 9.4.2-P1 <<>> [http://220.233.xxx.xxx:8080](http://220.233.xxx.xxx:8080)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 49900
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available
;; QUESTION SECTION:
;[http://220.233.xxx.xxx:8080](http://220.233.xxx.xxx:8080).	IN	A
;; Query time: 4059 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Jul 20 10:58:49 2008
;; MSG SIZE  rcvd: 45

dig [http://ubuntuserver:8080](http://ubuntuserver:8080)
; <<>> DiG 9.4.2-P1 <<>> [http://ubuntuserver:8080](http://ubuntuserver:8080)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 14231
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available
;; QUESTION SECTION:
;[http://ubuntuserver:8080](http://ubuntuserver:8080).	IN	A
;; Query time: 4187 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Jul 20 11:24:56 2008
;; MSG SIZE  rcvd: 42

going by the file sizes wget quotes, 220.233.xxx.xxx resolves to the router login page (4683kb), while ubuntuserver:8080 resolves to my website index.html (800kb). 

i have tried various changes to the hosts file with no improvement. i have read [http://ubuntuforums.org/showthread.php?t=846410&highlight=DNS+loopback](http://ubuntuforums.org/showthread.php?t=846410&highlight=DNS+loopback), but am still unsure how to fix the issue.
can anyone help?
thanks in advance.

---

### Post by skunkbad on 2008-07-20
try:

127.0.0.1   localhost   ubuntuserver
127.0.1.1   ubuntuserver

also, what's your /etc/resolv.conf look like?

---

### Post by windependence on 2008-07-20
I don't think you understand exactly how this product works. You do not need any reference to your outside IP to use the search feature. This is in no way intended to make your search ranking better in external search engines, just a nice fast way to search your own site. It can certainly use the internal address of your site without any problems for it's search function and the results can be displayed to external users in your internal DNS is set up properly to resolve to your actual domain name.

So, the following has some problems:
```

127.0.0.1 localhost
[B]127.0.1.1 ubuntuserver
192.168.1.10 220.233.xxx.xxx[/B]
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

The first highlighted line is OK, but we would normally do it this way:

```
192.168.1.10    ubuntuserver.yourdomain.tld   ubuntuserver
```

The second one just should not be done that way at all:

```
192.168.1.10 220.233.xxx.xxx
```

You could try this:

```
220.233.xxx.xxx  yourdomain.tld
```

When someone requests a search on your server, and the results come back, it doesn't matter if the links point to local IPs as long as they work. You should have an alias as I pointed out to resolve to your domain name, and then outside visitors will never see your internal addresses.

-Tim

---

### Post by semiliko on 2008-07-26
thanks for your assistance skunkbad and windependence. i solved my problems by modifying/deleting the above suggested entries, getting a domain name from dyndns.org, and resolving all internal traffic to the webserver to 192.168.1.10 (the internal LAN address of the webserver) in my hosts file.
sphider now indexes my site, and is searchable by the outside world.
thanks once again!
semiliko

---

### Post by windependence on 2008-07-26
Good deal! Glad to have helped.

-Tim

---

