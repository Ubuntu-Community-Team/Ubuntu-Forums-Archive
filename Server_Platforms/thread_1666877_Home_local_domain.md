---
title: "Home local domain"
date: 2011-01-14
forum: Server Platforms
---

### Post by karq on 2011-01-14
Hey everyone!

Maybe someone can point me to a good tutorial how to make a local domain? I have a laptop and server in my localhost. How can I make so that when I type backup.home or something like that into chrome it points to my server? I have apache2 installed with some virtualhost and mypage.192.168.1.4(my server ip) dosent work I propably need a domain or something like that.

I'm quite a noob in networking, hope someone can help.

---

### Post by rubylaser on 2011-01-14
Probably the quickest way to do this is to edit your /etc/hosts file.
```
sudo nano /etc/hosts
```
And paste this into each machine.
```
192.168.1.5 backup
192.168.1.4 web
```

The above are examples, but after adding those entries, the hostname backup would resolve to 192.168.1.5 and web would resolve to 192.168.1.4.

A better long term solution is a add the hostnames and ip's to your DNS server.

---

### Post by rubylaser on 2011-01-14
Probably the quickest way to do this is to edit your /etc/hosts file.
```
sudo nano /etc/hosts
```
And paste this into each machine.
```
192.168.1.5 backup
192.168.1.4 web
```

The above are examples, but after adding those entries, the hostname backup would resolve to 192.168.1.5 and web would resolve to 192.168.1.4.

A better long term solution is a add the hostnames and ip's to your DNS server.

---

### Post by karq on 2011-01-15
Thanks alot!

But I have another question. How do I configure my system so that when I have many sites hosting on apache like site1.web site2.web and so on that when I point my laptop to site1.web it points me in the right direction. I tried mysite.192.168.1.4(my server ip) but that dosent work.

---

### Post by rubylaser on 2011-01-15
You need to add a vhost file to apache.
```
sudo nano /etc/apache2/sites-available/site1.web
```

You need to populate it with some info like this...

```
<VirtualHost *:80>
    ServerName site1.web
    DocumentRoot /var/www/site1.web/
</VirtualHost>
```
Obviously, you'll need to have your code at /var/www/site1.web, and you'll want to chown the owner and group to www-data.

```
sudo chown www-data:www-data /var/www/site1.web/
```

Then enable the site...
```
sudo a2ensite site1.web
```
And reload Apache
```
sudo /etc/init.d/apache2 reload
```

---

### Post by karq on 2011-01-15
Yes, I know how to make virtualhosts, but the problem is this that the server runs in a another machine. And when I type into my laptop site1.web.192.168.1.4 or site2.web.... then it dosent go to my site1 or site2 page. I know that I have to setup a dns server locally, but I dont know how to. That name resolving part gets me confused. 

So I tried to setup a local dns server
I installed bind9
I want to make a local domain called home.lan.
In my household I have a laptop and my ubuntu server.

My setup:
ISP cabel is connected to a wrt54g router. Then there's a switch connected to a router and my laptop and server are connected to that switch.

My internal ip range is 192.168.1.0
My servers internal ip is 192.168.1.4
and my laptop is 192.168.1.5


Here are my conf files
/etc/bind/named.conf.local
```
# Our domain zone
zone "home.lan" {
   type master;
   file "/etc/bind/zones/home.lan.db";
};

# For reverse DNS
zone "1.168.192.in-addr.arpa" {
   type master;
   file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

```

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
                208.67.222.222;
                208.67.220.220;
         };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```
/etc/bind/zones/home.lan.db
```
$TTL 3D
@       IN      SOA     ns.home.lan. chantra.home.lan. (
                        200608081       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        2H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
;
                NS      ns              ; Inet Address of name server
                MX      10 mail         ; Primary Mail Exchanger
                MX      20 mail2        ; Secondary Mail Exchanger
;
ns              A       192.168.1.4
www             CNAME   www.home.lan
ftp             CNAME   ns
gw              A       192.168.1.1
                TXT     "Network gateway"

```

/etc/bind/zones/rev.1.168.192.in-addr.arpa
```
$TTL 3D
@       IN      SOA     ns.home.lan. admin.home.lan. (
                2007062001
                28800
                604800
                604800
                86400
)
        IN      NS      ns.home.lan.
1       IN      PTR     gw.home.lan.
10      IN      PTR     dns.home.lan.

```

My laptops /etc/resolv.conf
```
nameserver 192.168.1.4
# Generated by NetworkManager
domain home.lan
search home.lan
nameserver 192.168.1.4
```


What am I making wrong? If I point my browser to home.lan, then It just dosent find it.

---

