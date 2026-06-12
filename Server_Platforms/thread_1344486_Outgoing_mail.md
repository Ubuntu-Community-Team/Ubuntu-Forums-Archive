---
title: "Outgoing mail"
date: 2009-12-03
forum: Server Platforms
---

### Post by JohnAxis on 2009-12-03
I'm New to here and linux so take it easy on me plz.
i have a HP DL380 G3 runing server 9.10
i'm runing it as a 
router - firestarter
Web server -apache
email - postfix, Dovecot, Squirrelmail
and i just got my own .com whitch i will call "domain.com"
 
now my problem is i can sometimes (2 out of 20 time) send mail from "@domain.com" to like gmail or yahoo so on and so on.
and i cant get any incoming mail at all.
 
can anyone help me

---

### Post by Dinu. on 2009-12-03
Same problem facing by me to.but no one is replaying about this problem any way we can wait till someone reply about this

---

### Post by JohnAxis on 2009-12-03
> **Dinu. said:**
> Same problem facing by me to.but no one is replaying about this problem any way we can wait till someone reply about this
 
 
i have been working on this for about 5 weeks i was hoping some would know

---

### Post by espmartin on 2009-12-03
I would like to know myself!

---

### Post by Xipher on 2009-12-03
Do you have your MX records setup? If you can provide the domain I'm sure some one here can check it for you. If all you did was buy the domain but didn't setup any of the records mail isn't going to reach you at all.

---

### Post by JohnAxis on 2009-12-03
> **Xipher said:**
> Do you have your MX records setup? If you can provide the domain I'm sure some one here can check it for you. If all you did was buy the domain but didn't setup any of the records mail isn't going to reach you at all.
 
i set up my mx but let me post it and see if its right
 
type------ host------------- address------------------------- Priority 
 
MX-------- @--------------- mydomain.com -------------------10
a ---------www -------------my server's public ip 
a----------- *--------------- my server's public ip 
a---------- @--------------- my server's public ip

---

### Post by koenn on 2009-12-03
> **JohnAxis said:**
> i set up my mx but let me post it and see if its right
 
type------ host------------- address------------------------- Priority 
 
MX-------- @--------------- mydomain.com -------------------10
a ---------www -------------my server's public ip 
a----------- *--------------- my server's public ip 
a---------- @--------------- my server's public ip

you need a **hostname** for your MX, not a domain name, and you need to have an address record for that host. An alias record (CNAME) might work too. 
So something like this
```

 
MX      mail.mydomain.com      <priority>
A       mail.mydomain.com     123.123.123.123

```
the exact format will depend on what DNS server your using or how the user interface presents this kind of stuff.

---

### Post by JohnAxis on 2009-12-03
> **koenn said:**
> you need a **hostname** for your MX, not a domain name, and you need to have an address record for that host. An alias record (CNAME) might work too. 
So something like this
```

 
MX      mail.mydomain.com      <priority>
A       mail.mydomain.com     123.123.123.123

```
the exact format will depend on what DNS server your using or how the user interface presents this kind of stuff.
 
ok i changed my DNS
 
type------ host------------- address------------------------- Priority 
 
MX-------- @--------------- mail.mydomain.com -------------10
a----------mail--------------my server's public ip
a ---------www -------------my server's public ip 
a----------- *--------------- my server's public ip 
 
still nohting. i use moniker.com for my domain
 
i print sreened my DNS page 
[http://i607.photobucket.com/albums/tt156/Antec1022/Untitled-1.png](http://i607.photobucket.com/albums/tt156/Antec1022/Untitled-1.png)

---

### Post by koenn on 2009-12-03
try putting mail.mydomain.com  in the host field, not the address field

what's your domain name, anyway. It's a lot easier to check with real values, and you're setting up a public service, so why hide it ?
(or PM it)

---

### Post by JohnAxis on 2009-12-03
> **koenn said:**
> try putting mail.mydomain.com in the host field, not the address field
 
what's your domain name, anyway. It's a lot easier to check with real values, and you're setting up a public service, so why hide it ?
(or PM it)
 
it will not allow it. it just give me an error
my domain is johnaxis.com
 
and i just got off the phone with my isp and thay say nothing is block on any port

---

### Post by koenn on 2009-12-03
i can get an IP address for mail.johnaxis.com so your DNS is working, but the address is not replying on port 25, so either the IP address is wrong, or something is blocking it on your side. 
Do you have a firewall or a NAT router ?

edit - OK, you have firestarter. explain how your mail server connects to the internet and where the firewall is located.

---

### Post by JohnAxis on 2009-12-03
> **koenn said:**
> i can get an IP address for  so your DNS is working, but the address is not replying on port 25, so either the IP address is wrong, or something is blocking it on your side. 
Do you have a firewall or a NAT router ?
ya i'm runing firestarter but i have port 25 open
ip :

---

### Post by koenn on 2009-12-03
this is what it looks like on the internet:
```


; <<>> DiG 9.3.2 <<>> @ns1.moniker.com mail.johnaxis.com A
 ; (1 server found)
 ;; global options:  printcmd
 ;; Got answer:
 ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57109
 ;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 4
 
 ;; QUESTION SECTION:
 ;mail.johnaxis.com.		IN	A
 
 ;; ANSWER SECTION:
 mail.johnaxis.com.	21600	IN	A	98.149.205.119

```
so far so good (unless I miss something)


this is (more ore less) what other mail servers will get when they try to connect to your server to deliver mail:
```

:~$ telnet 98.149.205.119 25
Trying 98.149.205.119...
telnet: Unable to connect to remote host: Connection timed out

```

Is your mail server running ? And are you absolutely sure about that your firewall doesn't block port 25/tcp ?

---

### Post by JohnAxis on 2009-12-03
ya every thing looks good i just did a restart on the server. checked the firewall every looks good

---

### Post by JohnAxis on 2009-12-03
well after the restart now everything is working mail in and out just fine

---

### Post by kustomjs on 2009-12-03
first of all what kind of email server you got up? is it virtual system or what? we need to know the full setup.  Are you hosting this at your home with a static IP? if your behind a router are the correct ports open like 110 and 25? do you have your services running?  we need more info on your setup.

---

