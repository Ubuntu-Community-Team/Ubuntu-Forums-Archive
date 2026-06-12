---
title: "DNS confusion"
date: 2010-08-03
forum: Server Platforms
---

### Post by Smedvig on 2010-08-03
[FONT=Verdana][SIZE=2]I don't really know what I'm doing wrong, so I'll try to explain everything I've done in as much detail as possible in hopes that providing too much info is better than too little info :p

So recently I bought a dedicated server (running Ubuntu) which has two IP addresses, let's say 1.2.3.10 and 1.2.3.11. (I have set up the LAMP package and navigating to either IP brings up my webpage, as I want.) I have an existing domain registered, mydomain.com, and I'd like to make it so that the domain resolves to one of those IPs. mydomain.com is registered at hostmonster, and usually the way I'd do this is to take the two nameserver nam[/SIZE][/FONT][FONT=Verdana][SIZE=2]es given to me by my webhost, log into hostmonster's cPanel and insert them under mydomain.com's name server slots. In this case, however, the host I bought the dedicated server from didn't provide me with any nameserver names, and when I emailed them to ask[FONT=Verdana, Arial, Helvetica], here is what they wrote:
[/FONT][/SIZE][/FONT]> [FONT=Verdana, Arial, Helvetica][SIZE=2]You have dedicated server with us.
We dont provide DNS service for dedicated servers.

Either you have to use DNS service of your domain registrar to point to  that IP. Or you need to setup DNS service on your server and register  private nameservers at your registrar like

[ns1.yourdomain.com]("http://ns1.yourdomain.com/") > Your Ip 1
[ns2.yourdomain.com]("http://ns2.yourdomain.com/") > Your Ip 2

Let me know if you have any confusion.
[/SIZE][/FONT][FONT=Verdana, Arial, Helvetica][SIZE=2]

[/SIZE][/FONT][FONT=Verdana, Arial, Helvetica][SIZE=2][SIZE=2] So going by their "you need to setup DNS service on your server" line, I did some googling, and following this tutorial:
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
installed bind9 on my server.

Following the tutorial, my /etc/bind/named.conf.local file looks like this:
```

zone "mydomain.com" {
    type master;
    file "/etc/bind/db.mydomain.com";
};

zone "3.2.1.in-addr.arpa" {
    type master;
    notify no;
    file "/etc/bind/db.3";
};

```[/SIZE]
/etc/bind/db.mydomain.com looks like this:
```

$TTL    604800
@    IN    SOA    mydomain.com. root.mydomain.com. (
                  3        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    mydomain.com.
@    IN    A    1.2.3.10
ns  IN  A   1.2.3.10

```and /etc/bind/db.3 looks like this:
```

$TTL    604800
@    IN    SOA    ns.mydomain.com. root.mydomain.com. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.
10    IN    PTR    ns.mydomain.com.

```and /etc/resolv.conf looks like this:
```

search mydomain.com
nameserver 1.2.3.10

```With this I've gotten it so that running
```
host mydomain.com
```on the server returns:
```
mydomain.com has address 1.2.3.10
```which I think is what I want.

Now the problem is, the tutorial says for me to configure a "secondary master server", which involves installing bind9 on a different server- but I only have this one! So I'm at a loss as to what to do here. I need the IPs of two nameservers (a primary and secondary) to enter into the hostmonster mydomain.com nameserver configuration panel, but I don't know what to do... can I configure the same server to be both a primary and secondary master server? Or am I completely off base and doing something very wrong?

Any help is appreciated! Thanks for your time.
[/SIZE][/FONT]

---

### Post by chopinhauer on 2010-08-03
> **Smedvig said:**
> [FONT=Verdana][SIZE=2][/SIZE][/FONT][FONT=Verdana, Arial, Helvetica][SIZE=2][SIZE=2]
```

zone "mydomain.com" {
    type master;
    file "/etc/bind/db.mydomain.com";
};

zone "3.2.1.in-addr.arpa" {
    type master;
    notify no;
    file "/etc/bind/db.3";
};

```


The "3.2.1.in-addr.arpa" zone is not yours, you only have two IPs, so the data from your server will be ignored. Your hosting provider should let you set you reverse DNS on their servers.

[/SIZE][/SIZE][/FONT]> **Smedvig said:**
> [FONT=Verdana, Arial, Helvetica][SIZE=2][SIZE=2]
[/SIZE][/SIZE][/FONT][FONT=Verdana, Arial, Helvetica][SIZE=2]```

$TTL    604800
@    IN    NS    mydomain.com.
@    IN    A    1.2.3.10
ns  IN  A   1.2.3.10

```


Is there a reason you set the nameserver for the domain to be mydomain.com instead of ns.mydomain.com (the NS and SOA entries)? In such a case the ns entry is useless.

[/SIZE][/FONT]> **Smedvig said:**
> [FONT=Verdana, Arial, Helvetica][SIZE=2][SIZE=2]
[/SIZE][/SIZE][/FONT][FONT=Verdana, Arial, Helvetica][SIZE=2]Now the problem is, the tutorial says for me to configure a "secondary master server", which involves installing bind9 on a different server- but I only have this one! So I'm at a loss as to what to do here. I need the IPs of two nameservers (a primary and secondary) to enter into the hostmonster mydomain.com nameserver configuration panel, but I don't know what to do... can I configure the same server to be both a primary and secondary master server? Or am I completely off base and doing something very wrong?
[/SIZE][/FONT]

It is almost compulsory to have two DNS servers for the same domain, but since you have only one, leave the other entry blank.

All the registrars I tried have always offered to use their DNS servers, isn't it the case with hostmonster? Or there is a reason you want to run your own DNS server?

---

### Post by bovcan on 2010-08-03
Or, you can try free DNS. Much easyier to setup.

---

### Post by gordintoronto on 2010-08-03
Hostmonster rents a place to put your web site. They are not a registrar.

---

