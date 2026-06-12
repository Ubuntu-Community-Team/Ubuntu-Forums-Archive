---
title: "Bind9 Not working"
date: 2008-09-24
forum: Server Platforms
---

### Post by dethredic on 2008-09-24
So, I have had this server up and running for a month or so now, but yesterday the power went out in my house, and after turning on the server, I can no longer access my site by its domain name, but I can access it by its IP. The IPs are all what they should be, and I have restarted Bind9 and apache.

This is what I have tried:
> 
root@server:/home/server# /etc/init.d/bind9 restart
 * Stopping domain name service... bind                                  [ OK ] 
 * Starting domain name service... bind                                  [ OK ] 
root@server:/home/server# /etc/init.d/apache2 restart
 * Restarting web server apache2                                         [ OK ] 
root@server:/home/server# ps -ef | grep named
bind      6352     1  0 12:38 ?        00:00:00 /usr/sbin/named -u bind
root      6396  6287  0 12:41 pts/0    00:00:00 grep named
root@server:/home/server# killall -9 named
root@server:/home/server# /etc/init.d/bind9 start
 * Starting domain name service... bind                                  [ OK ] 
root@server:/home/server# 


Any ideas?

---

### Post by dave on 2008-09-24
> **dethredic said:**
> root@server:/home/server# /etc/init.d/bind9 restart
* Stopping domain name service... bind [ OK ]
* Starting domain name service... bind [ OK ]
root@server:/home/server# /etc/init.d/apache2 restart
* Restarting web server apache2 [ OK ]
root@server:/home/server# ps -ef | grep named
bind 6352 1 0 12:38 ? 00:00:00 /usr/sbin/named -u bind
root 6396 6287 0 12:41 pts/0 00:00:00 grep named
root@server:/home/server# killall -9 named
root@server:/home/server# /etc/init.d/bind9 start
* Starting domain name service... bind [ OK ]
root@server:/home/server#

By my best assumption is that it's running: because of this line

```
bind 6352 1 0 12:38 ? 00:00:00 /usr/sbin/named -u bind
```

Seems the bind user has started named (bind server process).  You can test it by running the following command:

```
dig google.com @localhost
```

This will ask the DNS server on the localhost for the IP of google.com.  You should get a valid response, if your machine is connected to the web.

--
Dave

---

### Post by dave on 2008-09-24
Or, as I just thought, if it was down for long enough the other name servers may have timed out when looking for the name, and you'll need to let the cache on those machines reset.  Obviously, test to see if you can `dig` against your server directly to make sure it's not named acting up.

---

### Post by dethredic on 2008-09-24
Ok, Well, it was down for 2-3 days. The internet is working on the server. In 24 hours if it is not up I will post here again.

EDIT: I got a valid response from the dig.

---

### Post by TomB19 on 2008-09-24
> **dave said:**
> Or, as I just thought, if it was down for long enough the other name servers may have timed out when looking for the name, and you'll need to let the cache on those machines reset.  Obviously, test to see if you can `dig` against your server directly to make sure it's not named acting up.

> **dethredic said:**
> Ok, Well, it was down for 2-3 days. The internet is working on the server. In 24 hours if it is not up I will post here again.

I think Dave nailed it.

---

### Post by dethredic on 2008-09-25
Well, it has been 24 hours since I got the server back up, and the domain name still does not work. I will keep hopeing, but is there anything else I can try while I wait?

---

### Post by dethredic on 2008-09-26
Ok, the domain name name is still not working. And I think the dig gave positive results.

> root@server:/home/server# dig google.com @localhost

; <<>> DiG 9.4.1-P1.1 <<>> google.com @localhost
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52980
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             300     IN      A       72.14.207.99
google.com.             300     IN      A       64.233.187.99
google.com.             300     IN      A       64.233.167.99

;; AUTHORITY SECTION:
google.com.             170928  IN      NS      ns2.google.com.
google.com.             170928  IN      NS      ns4.google.com.
google.com.             170928  IN      NS      ns3.google.com.
google.com.             170928  IN      NS      ns1.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.         172800  IN      A       216.239.32.10
ns2.google.com.         172800  IN      A       216.239.34.10
ns3.google.com.         172800  IN      A       216.239.36.10
ns4.google.com.         172800  IN      A       216.239.38.10

;; Query time: 173 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Sep 26 19:28:00 2008
;; MSG SIZE  rcvd: 212

root@server:/home/server# 


well, I decided to run one for my domain name as I have no ideas why this is not working...
> root@server:/home/server# dig hatchseadgroup.com @localhost

; <<>> DiG 9.4.1-P1.1 <<>> hatchseadgroup.com @localhost
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 28755
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;hatchseadgroup.com.            IN      A

;; ANSWER SECTION:
hatchseadgroup.com.     604800  IN      A       24.57.219.152

;; AUTHORITY SECTION:
hatchseadgroup.com.     604800  IN      NS      ns.hatchseadgroup.com.

;; Query time: 2 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Sep 26 19:29:34 2008
;; MSG SIZE  rcvd: 69

root@server:/home/server# 


---

### Post by dethredic on 2008-09-27
Ok, I am getting desprite. Last night I went through the bind9 folder and in some of the config files. the IP was different than my current one. That got me thinking, maybe they power outtage caused my router to get a new IP from my ISP.

I got all excited thinking I figured it out. I went through all the config files, and changed the IP to my current one, and restarted bind9. That was 24 hours ago, and my domain name is still not working.

Anywone have any ideas?

---

### Post by dethredic on 2008-09-29
anyone?

---

