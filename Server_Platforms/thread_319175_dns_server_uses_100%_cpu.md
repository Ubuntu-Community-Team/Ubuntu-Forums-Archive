---
title: "dns server uses 100% cpu"
date: 2006-12-15
forum: Server Platforms
---

### Post by grossi on 2006-12-15
I have installer ad old compaq server (PIII 1.3Ghz, 768Mb ram) with ubuntu dapper server version, used as public dns server (bind9.3.2-2ubuntu1.1).
the problem is that after a few days the named proces starts to use more and more cpu, reaching 99% after about 10hours,  and the dns service become slower and slower.
I restart the service (bind9 stop/start) and the service restarts flawlessly, with cpu usage around 20%.
the server is configured as master for some zones (about 100), and slave for others (about 700 zones).
nothing on the log files .. today i increased the debug level.
have you gays any advice for this problem?
thank you

---

### Post by samiux on 2006-12-15
> **grossi said:**
> I have installer ad old compaq server (PIII 1.3Ghz, 768Mb ram) with ubuntu dapper server version, used as public dns server (bind9.3.2-2ubuntu1.1).
the problem is that after a few days the named proces starts to use more and more cpu, reaching 99% after about 10hours,  and the dns service become slower and slower.
I restart the service (bind9 stop/start) and the service restarts flawlessly, with cpu usage around 20%.
the server is configured as master for some zones (about 100), and slave for others (about 700 zones).
nothing on the log files .. today i increased the debug level.
have you gays any advice for this problem?
thank you

Hi,

Go to the following websites to check if your DNS setting has error or not.  Make sure your DNS is not an open DNS.

[www.dnsstuff.com](www.dnsstuff.com)
[www.pingability.com](www.pingability.com)

Samiux

---

### Post by chrisfay on 2006-12-15
> have you [COLOR="Red"]gays[/COLOR] any advice for this problem?:mrgreen: 

> Go to the following websites to check if your DNS setting has error or not. Make sure your DNS is not an open DNS.

Sounds more like a software/package issue than a surface configuration issue....

Anything strange in your logs?

---

### Post by grossi on 2006-12-15
> **samiux said:**
> Hi,

Go to the following websites to check if your DNS setting has error or not.  Make sure your DNS is not an open DNS.

[www.dnsstuff.com](www.dnsstuff.com)
[www.pingability.com](www.pingability.com)

Samiux

the server is not an open dns, i checked with dnsreport.com, and when the cpu is 99% "rndc status" displays :
recursive clients: 43/2500
that if far below the limit.
thx
--
GRossi

---

### Post by grossi on 2006-12-15
> **chrisfay said:**
> :mrgreen: 

..opps!! :D
what a illfated typo for my first post! 

> **chrisfay said:**
> 
Sounds more like a software/package issue than a surface configuration issue....

Anything strange in your logs?

none, i have now changed the verbosity to "info" (was warning)

thx
--
GRossi

---

