---
title: "nameservers did not respond"
date: 2014-04-19
forum: Server Platforms
---

### Post by jacksmith on 2014-04-19
Hi,

I'm using ubuntu 12.04 server + ISP config3 on a server call alpha.exemple1.com

I've create a first zone call for example example1.com with ns1.example1.com (for the moment there are no secondary dns server)
It's possible to ping example1.com & ns1.example1.com from anywhere.
example1.com is also working

Then, I've create another zone : example2.com and tell it that ns is ns1.example1.com

When login on the server alpha.example1.com, it's possible to ping example2.com.
Yet, from outside, it's not possible to ping example2.com ....
In the files below
- the real domain names have been change to example1.com and example2.com
- the real IP adress have been change to 155.242.23.12 (it's not the real address but an example).

Does somebody have an idea ???

I've search and search again during hours

Thanks in advance. 

**Informations in files are :**
[B]
File /etc/bind/named.conf :[/B]
> include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";




**File /etc/bind/named.conf.options**

> options {
        directory "/var/cache/bind";

        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { ::1; };
        listen-on { 127.0.0.1; };
        allow-recursion { 127.0.0.1; };
};

**file /etc/bind/named.conf.local : **
> zone "example2.com" {
type master;
allow-transfer {none;};
file "/etc/bind/pri.example2.com";
}; 

**file /etc/bind/pri.example1.com.err**
> $TTL 3600
@ IN SOA ns1.example1.com. somebody.gmail.com. (
2014032902 ; serial, todays date + todays serial #
7200 ; refresh, seconds
540 ; retry, seconds
604800 ; expire, seconds
86400 ) ; minimum, seconds
;

example1.com. 3600 A 155.242.23.12
example1.com. 3600 MX 10 mail.example1.com.
example1.com. 3600 NS ns1.example1.com.
example1.com. 3600 NS ns2.example1.com.
mail 3600 A 155.242.23.12
www 3600 A 155.242.23.12


@ IN NS ns1.example1.com
ns1 IN A 155.242.23.12 

**file /etc/bind/pri.example2.com :**
>  $TTL 3600
@ IN SOA ns1.example1.com. somebody.gmail.com. (
2014032901 ; serial, todays date + todays serial #
7200 ; refresh, seconds
540 ; retry, seconds
604800 ; expire, seconds
86400 ) ; minimum, seconds
;

example2.com. 3600 A 155.242.23.12 ;
example2.com. 3600 MX 10 mail.example2.com.
example2.com. 3600 NS ns1.example1.com.
example2.com. 3600 NS ns2.example1.com.
mail 3600 A 155.242.23.12 ;
www 3600 A 155.242.23.12 

---

### Post by Doug S on 2014-04-20
There is no SOA record for example2.com.
By the way, I do not see ns2.example1.com defined anywhere.

---

### Post by jacksmith on 2014-04-20
Hi, 
thanks for you answer. 
What do you mean by There is no SOA record for example2.com ?
Do you have an example ?

ns2.example1.com is not defined for the moment.

---

### Post by jacksmith on 2014-04-20
On other part, following nmap, I've seen that port 53 is not open from outside :
21/tcp   open     ftp
22/tcp   open     ssh
25/tcp   open     smtp
80/tcp   open     http
110/tcp  open     pop3
143/tcp  open     imap
445/tcp  filtered microsoft-ds
465/tcp  open     smtps
587/tcp  open     submission
993/tcp  open     imaps
995/tcp  open     pop3s
3306/tcp open     mysql
8080/tcp open     http-proxy
8081/tcp open     blackice-icecap

I've seen on : [http://bugtracker.ispconfig.org/index.php?do=details&task_id=2955](http://bugtracker.ispconfig.org/index.php?do=details&task_id=2955) that port 53 is closed by default.
The topic say to edit the file named.conf.options and, in order to open the port, add the line
listen-on port 53 { any; };

Yet, for me, it's not working... :-(

---

### Post by Doug S on 2014-04-20
> **jacksmith said:**
> What do you mean by There is no SOA record for example2.com ? Do you have an example ?The Start of Authority (SOA) resource record, this line:```
@ IN SOA ns1.example1.com. somebody.gmail.com. (
```You should have one for example2.com, probably that same line should be:```
@ IN SOA ns1.example2.com. somebody.gmail.com. (
```Although, myself I would have done this:```
@ IN SOA example2.com. somebody.gmail.com. (
```

---

### Post by jacksmith on 2014-04-20
I've find the solution following this page : 
[http://www.pawdata.com/gs/index.php?id=ispconfig3](http://www.pawdata.com/gs/index.php?id=ispconfig3)

The problem was only due to the fact that port53 was not open by default.

So the exact solution have been : 

edit /etc/bind/named.conf.options and change

> listen-on { 127.0.0.1; };

To : 

> listen-on { 127.0.0.1; my.server.ip.address; };

/etc/init.d/bind9 restart

---

