---
title: "Pointing a domain to IP address"
date: 2011-08-09
forum: Server Platforms
---

### Post by Quizmo on 2011-08-09
Hi there.
New guy at the forum, I hope I have posted at the right forum and you guys can help me out, because I have almost given up now.

I have a server hosted with greatseeder.com, its a dedicated ubuntu server using Ubuntu 10.4.

I have set up apache2 together with php5, and build a website from that. 

If you go though the ip address ([http://94.23.251.209](http://94.23.251.209)) the website loads fine, but if you go though the domain ([athenagaming.com](athenagaming.com)) it don't.

I have registered the domain at domain.com. The nameservers I got from the host did not work, so I used a free dns site, to refer the domain to the ip address. The site I use is, [http://freedns.afraid.org](http://freedns.afraid.org). I have signed up the domain, and added the nameservers i got from free dns to domain.com. But still it can't find the server though the domain, even though when I trace the domain it comes back all fine. ([http://freedns.afraid.org/domain/dnstrace.php?domain=athenagaming.com&submit=Trace](http://freedns.afraid.org/domain/dnstrace.php?domain=athenagaming.com&submit=Trace))

Does anybody know what could be wrong?

Thank you so much for you time, And sorry for my english.

---

### Post by hawkmage on 2011-08-09
I am getting the same thing by both the IP and name you gave.  

I did a little DNS digging and it looks OK to me.  The authoritative DNS for your domain are ns1.afraid.org, ns2.afraid.org, ns3.afraid.org and ns4.afraid.org.  They are showing:
```
nslookup -type=ANY athenagaming.com ns1.afraid.org
Server:		ns1.afraid.org
Address:	67.19.72.206#53

Name:	athenagaming.com
Address: 94.23.251.209
athenagaming.com	mail exchanger = 10 mail.athenagaming.com.
athenagaming.com
	origin = ns1.afraid.org
	mail addr = dnsadmin.afraid.org
	serial = 1108090003
	refresh = 86400
	retry = 7200
	expire = 3600000
	minimum = 3600
athenagaming.com	nameserver = ns2.afraid.org.
athenagaming.com	nameserver = ns1.afraid.org.
athenagaming.com	nameserver = ns4.afraid.org.
athenagaming.com	nameserver = ns3.afraid.org.
```

---

### Post by e79 on 2011-08-09
> **Quizmo said:**
> If you go though the ip address ([http://94.23.251.209](http://94.23.251.209)) the website loads fine, but if you go though the domain ([athenagaming.com]("http://athenagaming.com")) it don't.

Your english is fine as is your domain redirection as shown in the pic.

Cheers

---

### Post by brighty22 on 2011-08-09
yep. both work fine from here.

---

### Post by Habitual on 2011-08-09
Same here.

---

### Post by Quizmo on 2011-08-10
okay, now i'm confused... How come you guys can visit the site without any problems but I can't?

---

### Post by Quizmo on 2011-08-10
Well I talked to some other people, and they too can all connect to the domain so it seems like its just me...

Well Thank you everybody for you reply's, you have been very helpful..

---

