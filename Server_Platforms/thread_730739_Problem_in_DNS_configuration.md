---
title: "Problem in DNS configuration"
date: 2008-03-21
forum: Server Platforms
---

### Post by fnkhan on 2008-03-21
I have a problem for configuring DNS 
my system IP is 190.160.0.4
and using xx.xx.xx.xx gatway e.g 190.160.0.1
first i installed bind9
#sudo apt-get install bind
then after installation completed
setting up domain resolution
sudo vi /etc/bind/named.conf
zone "abc.com" {
type master;
file "abc.com.db";
notify no;
};

zone "0.160.190.in-addr.arpa" {
type master;
notify no;
file "reverse/190.160.0";
};

after this creating a dir and file
sudo mkdir /var/cache/bind/reverse
vi /var/cache/bind reverse/190.160.0
@   IN   SOA   ns.br.com   root.br.com
      NS   ns
ns   A    190.160.0.3


then add reverse zone
zone"0.168.190.in-addr.arpa"{
type master;
notify no;
file "reverse/190.160.0";
};

then create a dir and file
mkdir /var/cache/bind/reverse
vi  /var/cache/bind/reverse/192.168.0
@   IN   SOA    ns.br.com    root.br.com
      NS       ns.br.com
3    PTR     ns.br.com.


then go to /usr/bin
and check nslookup

>190.160.0.3

OR

>br.com
there is an error on both
:;connection time out; no server reached

Plz tell me what can I do
is there important for add /etc/bind/named.conf.options

---

### Post by fredEbay on 2008-03-23
Not sure if this means anything, but there is a discrepancy between these zone entries you provided as I denoted with arrows :



---> zone "0.160.190.in-addr.arpa" {
type master;
notify no;
file "reverse/190.160.0";
};

[snip]

then add reverse zone
---> zone"0.168.190.in-addr.arpa"{
type master;
notify no;
file "reverse/190.160.0";
};

---

### Post by ghost_ryder35 on 2008-03-23
> **fnkhan said:**
> I have a problem for configuring DNS 
**my system IP is 190.160.0.4**
and using xx.xx.xx.xx gatway e.g 190.160.0.1
first i installed bind9
#sudo apt-get install bind
then after installation completed
setting up domain resolution
sudo vi /etc/bind/named.conf
zone "abc.com" {
type master;
file "abc.com.db";
notify no;
};

zone "0.160.190.in-addr.arpa" {
type master;
notify no;
file "reverse/190.160.0";
};

after this creating a dir and file
sudo mkdir /var/cache/bind/reverse
vi /var/cache/bind reverse/190.160.0
@   IN   SOA   ns.br.com   root.br.com
      NS   ns
**ns   A    190.160.0.3**


then add reverse zone
**zone"0.168.190.in-addr.arpa"{**
type master;
notify no;
file "reverse/190.160.0";
};

then create a dir and file
mkdir /var/cache/bind/reverse
**vi  /var/cache/bind/reverse/192.168.0**
@   IN   SOA    ns.br.com    root.br.com
      NS       ns.br.com
3    PTR     ns.br.com.


then go to /usr/bin
and check nslookup

>190.160.0.3

OR

>br.com
there is an error on both
:;connection time out; no server reached

Plz tell me what can I do
is there important for add /etc/bind/named.conf.options

You have problems everywhere:
Your computer must have a STATIC ip
(if your computers IP is 190.160.0.4 then your "ns A" should be)
currently your ns A is set to 190.160.0.3 which is wrong for your configuration it should be,
```
**ns   A    190.160.0.4**
```
Then this,


**zone"0.168.190.in-addr.arpa"{**
type master;
notify no;
file "reverse/190.160.0";
};

then create a dir and file
mkdir /var/cache/bind/reverse
**vi  /var/cache/bind/reverse/192.168.0**
@   IN   SOA    ns.br.com    root.br.com
      NS       ns.br.com
3    PTR     ns.br.com.

_IS WRONG, it should be_
```

**zone"0.160.190.in-addr.arpa"{**
type master;
notify no;
file "reverse/190.160.0";
};

then create a dir and file
mkdir /var/cache/bind/reverse
**vi  /var/cache/bind/reverse/190.160.0**
@   IN   SOA    ns.br.com    root.br.com
      NS       ns.br.com
3    PTR     ns.br.com.
```

---

