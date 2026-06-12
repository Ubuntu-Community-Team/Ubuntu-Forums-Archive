---
title: "Squid - help"
date: 2009-05-04
forum: Server Platforms
---

### Post by rcbandit on 2009-05-04
Hi, 
  I would like to ask you is there a way to configure squid to redirect IPs. I want squid to read IP's from file saved in .TXT format saved on HDD or server on internet. And when user's IP matches with the IP from the TXT file squid redirects it to external URL hosted on remote server. 
Second question - is there a way to configure squid to read the external TXT file every 10 minutes for example so when I manually enter new IP or remove old one squid reads it and reconfigure itself. 

Regards

---

### Post by koenn on 2009-05-05
squid can use access control lists, whitelists, blacklists, .... of all sorts (hostnames, network ranges, ip addresses, ...). 
You can also map addresses to hostnames/domain names in /etc/hosts 

What exactly are you tying to achieve ?

---

### Post by rcbandit on 2009-05-05
I want to write a billing program for ISPs and web hosting, it's a hobby project.
My I idea is to install a squid proxy server to control the access to the internet.
I am going to write a program in PHP witch controls squid so when access period of IP expire squid redirects the web browser's page to external web page - "you must pay for access" for example and blocks the access to the internet.

PHP must send IPs for blocking(redirecting) access by simple .TXT saved on server. So I want to configure squid to read IPs from external .TXT file. That .TXT file will be edited by PHP program.
Squid will read that .TXT file every 10 minutes and reconfirure with the command "squid -k reconfigure" with cron job. 

There are other thing like collecting how much thaffic IP have made for 1 mounth and etc. but they are not important right now.

---

### Post by slakkie on 2009-05-05
At work we have implement such a thing with wccp.

We move customers who have to pay to a private IP space, where the wccp routers will route all traffic to a squid box which acts as a transparant proxy.

We redirect all http traffic to squid and allow specific sites to be accessed by the customer (so he can pay his internet bill). When the transaction is validated by the bank we reprovision the customer again and he will get a public IP address again and is able to browse the web without any restriction.

[http://wiki.squid-cache.org/ConfigExamples/SquidAndWccp2](http://wiki.squid-cache.org/ConfigExamples/SquidAndWccp2)

---

### Post by rcbandit on 2009-05-05
No this is not a solution for me. I need a external list of IP edited by PHP application and read by squid.
Can anyone tell me how to force squid to redirect IPs from a .txt external list

---

### Post by koenn on 2009-05-05
think someting along the lines of :

in squid.conf:
```


acl acl_allow src "/etc/squid/client_allow.txt"
acl acl_deny src "/etc/squid/client_deny.txt"

http_access deny acl_deny
http_access allow acl_allow

```

your php should update /etc/squid/client_deny.txt and/or /etc/squid/client_allow.txt". 
You could passibly reduce this to a deny all, allow only from /etc/squid/client_allow.txt construction.

when squids denies access, it returns an "access denied" page. 
figure out where it comes from or how its called, and either let it call your own custom "you must pay first" page, or replace the content of squids "access denied" page accordingly.

---

### Post by rcbandit on 2009-05-05
Ok, very good example.
Instead "access denied" to appear I must edit it to "User temporary locked". Where in squid I can edit that option?


I am thinking instead reconfiguring squid with the command "squid -k reconfigure" to reload the .txt file using cron every 10 minutes is there another more efficient solution to write the blocked IPs directly from the PHP program to the RAM memory where squid keeps the rules of working.

---

### Post by rcbandit on 2009-05-06
I know that PHP can pass IPs with .TXT file. Is there other more efficient way to pass IPs from the PHP program to the squid server?

---

### Post by rcbandit on 2009-05-07
Hi,
   I have news - my friend advice me to use LDAP - PHP writes the IPs to LDAP and squid reads them. Is it possible to do it?

---

### Post by juancarlospaco on 2009-05-07
Install **webmin**, the Squid module let you do what you want to do...

---

