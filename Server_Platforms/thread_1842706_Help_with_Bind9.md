---
title: "Help with Bind9"
date: 2011-09-12
forum: Server Platforms
---

### Post by Steviedallas on 2011-09-12
Hello all,

I'm trying to get a bind9 "Primary Master" dns configured so my FQDN (domain) is always pointing to my server (running apache2) because it has a dynamic IP. Is this right?

Anywho, I am somewhat a newbie and I want to make sure I'm doing this right because the article I'm reading (below) isn't completely straightforward.

[http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html#dns-primarymaster-configuration]("http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html#dns-primarymaster-configuration")

```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.example.com. root.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.example.com.
@       IN      A       127.0.0.1
@       IN      AAAA    ::1
ns      IN      A       192.168.1.10

```

Looking at this section, where you edit "/etc/bind/db.example.com" I have to assume..

[INDENT]127.0.0.1 represents my actual IP[/INDENT]

[INDENT]192.168.1.10 represents my servers IP on LAN[/INDENT]

[INDENT]The code shows **ns.**example.com but in the instructions it says nothing about adding in the **ns.** part..[/INDENT]

I changed the IPs, added 'ns.' to all domains shown in example, and restarted bind9 successfully.

So far, so good? How do I know it is working correctly?

Any input is greatly appreciated - thanks.

---

### Post by Steviedallas on 2011-09-12
Bump

---

### Post by Dangertux on 2011-09-12
Try 

```

nslookup yourdomain.com

```

Does it query your DNS server? Does it resolve to the right IP? That is how you will find out if it is working.

Also... You probably don't want it resolving to 127.0.0.1 (that's localhost)

You need to also add an actual host for your nameserver, unless it is in fact ns1.example.com

---

### Post by Steviedallas on 2011-09-13
> **Dangertux said:**
> Try 

```

nslookup yourdomain.com

```

Does it query your DNS server? Does it resolve to the right IP? That is how you will find out if it is working.

Also... You probably don't want it resolving to 127.0.0.1 (that's localhost)

You need to also add an actual host for your nameserver, unless it is in fact ns1.example.com

Thanks. When you say "does it query your dns server?" you mean the server with bind9 installed, then no. When i use nslookup, it shows the "server:           " as the ip of the first ns listed in my resolv.conf file. 

then it says "name:          " followed by the actual domain and "address:           " followed by some random IP, idk where it came from.

It's not actually 127.0.0.1 - i've replaced this with my public IP.

---

### Post by Dangertux on 2011-09-13
The random ip is probably the authoritative nameserver or the registrar's server. 

If you want your dns server to be used by your machine  you have to set it in your resolv.conf

---

### Post by Steviedallas on 2011-09-13
> **Dangertux said:**
> The random ip is probably the authoritative nameserver or the registrar's server. 

If you want your dns server to be used by your machine  you have to set it in your resolv.conf

ok - changed the first dns entry to my public ip, made exception to ufw, forwarded port 53, but it skipped it and went to secondary dns:

```
;; Got recursion not available from [PUBLIC IP], trying next server
```

---

### Post by Dangertux on 2011-09-13
That's because you're on a network with the server behind a NAT router. You may have to use the local address of your dns server in resolv and even then I am not sure if  it will work right due to the fact that youre nat'ed. 

Perhaps someone else can shed some light on this who has run a similar set up? I am not in a position to test anything as I am on my phone atm

EDIT : the work around is actually to create a PTR record for hosts on the LAN with the domain and the servers internal IP.
Additionally you can probably change the A record to just be your local IP as well so long as this isn't going to be the authoritative nameserver for the domain.

---

### Post by Steviedallas on 2011-09-13
> **Dangertux said:**
> That's because you're on a network with the server behind a NAT router. You may have to use the local address of your dns server in resolv and even then I am not sure if  it will work right due to the fact that youre nat'ed. 

Perhaps someone else can shed some light on this who has run a similar set up? I am not in a position to test anything as I am on my phone atm

EDIT : the work around is actually to create a PTR record for hosts on the LAN with the domain and the servers internal IP.
Additionally you can probably change the A record to just be your local IP as well so long as this isn't going to be the authoritative nameserver for the domain.

Ok - before I saw your edit, I changed the first dns entry in resolv to the local IP of the server and rebooted.

nslookup now shows..

```
Server:		[SERVER'S LOCAL IP]
Address:	[SERVER'S LOCAL IP]#53

Name:	example.com
Address: [SERVER'S PUBLIC IP]
```

Did it work? Bear with me - i'm somewhat new to this.

Again - thanks for your help.

---

