---
title: "ubuntu dns help"
date: 2010-07-28
forum: Server Platforms
---

### Post by pehden on 2010-07-28
Ok im not sure if i doing this wrong or some thing but i know with these 15 records my dns sub domains work as long as there only 1.domain.net or 2.domain.net ect, there as to only be 1 character in front of the domain in order for it to actually work any more and it fails other then [www.domain.net](www.domain.net), here is a screen shot of my dns list via my isp.

---

### Post by cdenley on 2010-07-28
Works fine for me.
```

cdenley@ubuntu:~$ host pehden.net
pehden.net has address 67.60.26.61
cdenley@ubuntu:~$ host 1.pehden.net
1.pehden.net has address 67.60.26.61
cdenley@ubuntu:~$ host 2.pehden.net
2.pehden.net has address 67.60.26.61
cdenley@ubuntu:~$ host www.pehden.net
www.pehden.net has address 67.60.26.61

```

Did you change anything recently? It can take 4 hours (14400 seconds) for any changes to propagate to any DNS servers which may have cached your old records, since you're using a 14400 TTL.

---

### Post by pehden on 2010-07-28
I think that aI made a change right before i got the screen shot but is it really needed for 15 dns records, i mean wow i think its alot. and the issue was when i tried connecting to a sub domain like this.domain.net it would say timed out or not found as a server, I think im still missing something. cause the ads.domain.net is showing the real domain instead of the google page it should be showing.

> **cdenley said:**
> Works fine for me.
```

cdenley@ubuntu:~$ host pehden.net
pehden.net has address 67.60.26.61
cdenley@ubuntu:~$ host 1.pehden.net
1.pehden.net has address 67.60.26.61
cdenley@ubuntu:~$ host 2.pehden.net
2.pehden.net has address 67.60.26.61
cdenley@ubuntu:~$ host www.pehden.net
www.pehden.net has address 67.60.26.61

```

Did you change anything recently? It can take 4 hours (14400 seconds) for any changes to propagate to any DNS servers which may have cached your old records, since you're using a 14400 TTL.

---

### Post by pehden on 2010-07-28
Ok I went to go to some of the domains i had set up like s.domian.net and it failed, when it was working here the new records.

---

### Post by cdenley on 2010-07-28
> **pehden said:**
> Ok I went to go to some of the domains i had set up like s.domian.net and it failed, when it was working here the new records.

What failed? Are the domains not resolving to the correct IP? They all seem to resolve to 67.60.26.61. Exactly what domain is "failing"? What IP does it resolve to and what IP were you expecting it to resolve to?
```

cdenley@ubuntu:~$ host s.pehden.net
s.pehden.net has address 67.60.26.61

```

---

### Post by pehden on 2010-07-28
Server not found

Firefox can't find the server at [https://s.pehden.net/ssh/](https://s.pehden.net/ssh/)

failed.


[https://www.pehden.net](https://www.pehden.net) same error.  
Host s.pehden.net not found: 2(SERVFAIL)


> **cdenley said:**
> What failed? Are the domains not resolving to the correct IP? They all seem to resolve to 67.60.26.61. Exactly what domain is "failing"? What IP does it resolve to and what IP were you expecting it to resolve to?
```

cdenley@ubuntu:~$ host s.pehden.net
s.pehden.net has address 67.60.26.61

```

---

### Post by cdenley on 2010-07-28
That does not necessarily indicate a DNS problem. Post this output:
```

getent hosts s.pehden.net
host s.pehden.net
nc -z -v -w 5 s.pehden.net 443
nc -z -v -w 5 67.60.26.61 443

```

---

### Post by pehden on 2010-07-28
pehden@pehden-laptop:~$ getent hosts s.pehden.net
pehden@pehden-laptop:~$ host s.pehden.net
Host s.pehden.net not found: 2(SERVFAIL)
pehden@pehden-laptop:~$ nc -z -v -w 5 s.pehden.net 443
nc: getaddrinfo: Name or service not known
pehden@pehden-laptop:~$ nc -z -v -w 5 67.60.26.61 443
Connection to 67.60.26.61 443 port [tcp/https] succeeded!
pehden@pehden-laptop:~$ B



Netstat 


tcp        0      0 128.100.1.10:6666       0.0.0.0:*               LISTEN      1269/ircd-hybrid
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      870/mysqld      
tcp        0      0 128.100.1.10:6667       0.0.0.0:*               LISTEN      1269/ircd-hybrid
tcp        0      0 128.100.1.10:6668       0.0.0.0:*               LISTEN      1269/ircd-hybrid
tcp        0      0 128.100.1.10:6669       0.0.0.0:*               LISTEN      1269/ircd-hybrid
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      1435/dovecot    
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      1435/dovecot    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      24144/apache2   
tcp        0      0 0.0.0.0:2000            0.0.0.0:*               LISTEN      1435/dovecot    
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      1228/dnsmasq    
tcp        0      0 128.100.1.10:53         0.0.0.0:*               LISTEN      1117/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1117/named      
tcp        0      0 0.0.0.0:86              0.0.0.0:*               LISTEN      15565/perl      
tcp        0      0 127.0.0.1:8022          0.0.0.0:*               LISTEN      1233/python     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      855/sshd        
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1414/master     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1117/named      
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      24144/apache2   
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      1435/dovecot    
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      1435/dovecot    
tcp        0      0 128.100.1.10:6665       0.0.0.0:*               LISTEN      1269/ircd-hybrid
tcp6       0      0 :::21                   :::*                    LISTEN      16205/proftpd: (acc
tcp6       0      0 :::53                   :::*                    LISTEN      1117/named      
tcp6       0      0 :::22                   :::*                    LISTEN      855/sshd        
tcp6       0      0 ::1:953                 :::*                    LISTEN      1117/named

---

### Post by cdenley on 2010-07-28
Your DNS server isn't resolving the domains. Mine does fine. Either your DNS isn't working, or you just have to wait for your changes to propagate.

```

cat /etc/resolv.conf

```

---

### Post by pehden on 2010-07-28
lol thats the wierd thing my dns is the same company i set my dns records with for my site.


and im not sure about this but in the dns records web page is the domain.net.   the dot at the very end needed or can it be domain.net      with out the dot.

---

### Post by cdenley on 2010-07-28
> **pehden said:**
> and im not sure about this but in the dns records web page is the domain.net.   the dot at the very end needed or can it be domain.net      with out the dot.

I don't know how that particular web interface works. Typically, for A records, you would provide only the subdomain part. Something like:
```

$TTL    604800
@       IN      SOA     my.dns.server. myemail.pehden.net. (
                              6
                         604800
                          86400
                        2419200
                         604800
);
@       IN      NS      my.dns.server.
@       IN      A       67.60.26.61
s       IN      A       67.60.26.61
*       IN      A       67.60.26.61

```

You can always use google's DNS or opendns instead of your ISP's, if you have problems with it. Like I said, maybe changes are still propagating. They might have separate DNS servers for hosting and lookups.

---

### Post by pehden on 2010-07-28
what i mean is my my isp is cableone the site that i have to update is cableonehosting.net i have to manually enter in the dns records.

but if there was an easier way i would jump to it.


> **cdenley said:**
> I don't know how that particular web interface works. Typically, for A records, you would provide only the subdomain part. Something like:
```

$TTL    604800
@       IN      SOA     my.dns.server. myemail.pehden.net. (
                              6
                         604800
                          86400
                        2419200
                         604800
);
@       IN      NS      my.dns.server.
@       IN      A       67.60.26.61
*       IN      A       67.60.26.61

```

You can always use google's DNS or opendns instead of your ISP's, if you have problems with it. Like I said, maybe changes are still propagating. They might have separate DNS servers for hosting and lookups.

---

### Post by cdenley on 2010-07-28
> **pehden said:**
> what i mean is my my isp is cableone the site that i have to update is cableonehosting.net i have to manually enter in the dns records.

but if there was an easier way i would jump to it.

Well, what I mean is I would guess you only need two A records, since everything seems to resolve to the same IP. One for "@", which means there is no subdomain part (pehden.net), and one for "*", for any subdomain (anything.pehden.net). I can't be sure about that particular interface for that particular service, though.

---

### Post by pehden on 2010-07-28
thats what i was thinking but i dont know if there has to be a dot at the end of the ldt or not?

so should i only put * in box one and the ip in the other for the A record? or does it need to be *.pehden.net or *pehden.net    or any of those with a dot at the end?



> **cdenley said:**
> Well, what I mean is I would guess you only need two A records, since everything seems to resolve to the same IP. One for "@", which means there is no subdomain part (pehden.net), and one for "*", for any subdomain (anything.pehden.net). I can't be sure about that particular interface for that particular service, though.

---

### Post by pehden on 2010-07-28
i would be asking my isp but there support for this topic isnt on there help center.

---

### Post by cdenley on 2010-07-28
> **pehden said:**
> thats what i was thinking but i dont know if there has to be a dot at the end of the ldt or not?

No dots at all, unless you want something like "sub.domain.pehden.net", which would mean a record for "sub.domain". For a CNAME or MX record, you should use a period after a full domain in the right column, but not the left. The left column should not have "pehden.net" in it. At least that is the way I expect it to work.

---

### Post by pehden on 2010-07-28
Then I will remove the dots from the left and that should cut back on the number of dns records.



as for the left should i use *   or *.pehden.net or *pehden.net    i still dont get that part?

> **cdenley said:**
> No dots at all, unless you want something like "sub.domain.pehden.net", which would mean a record for "sub.domain". For a CNAME or MX record, you should use a period after a full domain in the right column, but not the left.

---

### Post by cdenley on 2010-07-28
> **pehden said:**
> Then I will remove the dots from the left and that should cut back on the number of dns records.



as for the left should i use *   or *.pehden.net or *pehden.net    i still dont get that part?

Just simply "*" for a wilcard subdomain. "@" for no subdomain.

---

### Post by pehden on 2010-07-28
ill will update everything and then check back in 4 hours. ill let you know how it goes. heck i think ill put this on my blog lmao.

> **cdenley said:**
> Just simply "*" for a wilcard subdomain. "@" for no subdomain.

---

### Post by pehden on 2010-07-28
Ok well the sub domains started working but now the domain stopped, only [www.domainltd](www.domainltd) works, lol not domain.ltd, i going to add pehden.net to the row on the left now i got 8 dns records instead of 15.

> **pehden said:**
> ill will update everything and then check back in 4 hours. ill let you know how it goes. heck i think ill put this on my blog lmao.

---

### Post by pehden on 2010-09-01
This was solved with my previous post.

---

