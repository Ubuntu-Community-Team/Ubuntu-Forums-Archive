---
title: "DNS settings... for main and virtuals"
date: 2011-09-19
forum: Server Platforms
---

### Post by Tavorisch on 2011-09-19
I have set up a bind9 server in a matter of hours once on ubuntu, now I think I am retarded, I would really appreciate if someone pointed out what I am doing wrong here. I am going to be using all my real info because I don't care anymore I just want this to work.. I have literally had ispconfig 2 and 3 working just not sure about DNS... please help, I plan to make an extremely detailed guide for someone else in my network situation for a virtual web host. (FTP + named based virtual hosting for your friends)

Step 1 - Add hosts to godaddy so I can assign them as name servers.
[IMG]http://www.organicconsultings.com/server/hosts.png[/IMG]

Step 2 - Add two hosts as nameservers for coriolis-institute.com

Step 3 - Install Ubuntu with network settings
[IMG]http://www.organicconsultings.com/server/local.png[/IMG]

Step 4 - Set resolv.conf to this
[IMG]http://www.organicconsultings.com/server/dns.png[/IMG]

Step 5 - Install bind or mydns or whatever an example named.conf and zone file below

```
zone "coriolis-institute.com" in{
  type master;
  file "master/master.coriolis-institute.com.com";
};

```

```
$TTL	86400 ; 24 hours could have been written as 24h or 1d
$ORIGIN coriolis-institute.com.
@  1D  IN	 SOA mainserv.coriolis-institute.com.com.	mainserver0.coriolis-institute.com. (
			      2002022401 ; serial
			      3H ; refresh
			      15 ; retry
			      1w ; expire
			      3h ; minimum
			     )
       IN  NS     mainserv.coriolis-institute.com. ; in the domain
       IN  NS     mainserv0.coriolis-institute.com. ; external to domain
       IN  MX  10 mail.coriolis-institute.com.com. ; external mail provider
; server host definitions
mainserv    IN  A      24.119.186.239  ;name server definition     
mainserv0   IN  A      24.119.186.239
www    IN  A      24.119.186.239  ;web server definition
ftp    IN  CNAME  24.119.186.239  ;ftp server definition
(coriolis-institute.com?)       IN  A      24.119.186.239

; non server domain hosts


```


This is not my current configuration that is not working I just want to make sure I have the right idea for where to put what IP addresses..  I am just a basic home user behind a router and obvioulsy am port forwarding TCP & UDP 53.  We can forget reverse DNS as I am not in charge of my 1 and only IP address and I don't expect mail to work (probably just point MX records to google apps)

For the other hosted DNS as I am aware this is possible, I just use nameservers mainserv.coriolis-institute.com / mainserv0.coriolis-institute.com but have everything else about that certain domain.... ?

---

### Post by Tavorisch on 2011-09-19
Also my hosts file

```
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1               localhost.localdomain localhost
10.0.1.25          mainserv.coriolis-institute.com mainserv
::1             localhost6.localdomain6 localhost6
```

---

### Post by Ryan Dwyer on 2011-09-20
I installed bind9 and copied your config. I changed the following things to make it work:

- In named.conf.local, used absolute path (/etc/bind/master/... instead of master/...).
- Zone file: Removed extra ".com" in SOA record.
- Zone file: Removed extra ".com" in MX record.
- Zone file: Changed ftp from CNAME to A record (CNAMEs must point to a hostname, not an IP).
- Zone file: Removed brackets and replaced "?" with ".".

After that, I restarted bind9 and did a test lookup OK (using "dig @localhost coriolis-institute.com ns").

If you still have problems, check your /var/log/syslog. Bind records errors there.

---

### Post by Tavorisch on 2011-09-20
Beautiful, I really appreciate your help Ryan
so my understanding of where to use inside and outside Ip addresses is not wrong.. what about my resolv.conf and hosts file?

---

### Post by Ryan Dwyer on 2011-09-20
They look fine to me. I don't think the hosts file is used when your server is responding to a DNS request, but I don't have time to check that right now.

---

