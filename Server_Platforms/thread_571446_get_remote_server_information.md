---
title: "get remote server information"
date: 2007-10-09
forum: Server Platforms
---

### Post by erasmo.da.rotterdam on 2007-10-09
Hi!!
Can anybody suggest me a fast way to determine if a domain runs on a Linux or Windows server, maybe with some information about the web server used?
I am asking on this forum because that server will be conquered by Ubuntu of course...
Thanks in advance

---

### Post by HermanAB on 2007-10-09
telnet server 80
telnet server 22

Port 80 will show the web server banner.  However, Apache can run on Windows too.
Port 22 will show the OpenSSL banner.  This is almost always an indication of Linux, although Cygwin can run on Windows too.

Cheers,

H.

---

### Post by MJN on 2007-10-09
..although do bear in mind that banners can be fake/wrong.

Google for 'OS fingerprinting' for various methods to attempt to ascertain what OS a machine is running (nmap is one such tool that springs to mind) - this is an area where you can get as complex as you can imagine depending on what it is you're trying to achieve.

Mathew

---

### Post by netlogic on 2007-10-09
use nmap
nmap -v -A server1.domain.com, then use nc

---

### Post by netlogic on 2007-10-09
I am sorry. i am having a  busy day.
here are the links
for nmap
[http://insecure.org/nmap/](http://insecure.org/nmap/)

for nc (howto)
[http://www.datastronghold.com/articles/3.html](http://www.datastronghold.com/articles/3.html)

I hope these links help.

---

### Post by netlogic on 2007-10-09
I completely forgot! In certain countries, nmap is illegal, because it is treated as a hacker tool. Many people don't realize it is a great network debugging tool. Check your country law before using it.

---

### Post by erasmo.da.rotterdam on 2007-10-10
This nmap tells me everything I need to know
Thank you very very much to everybody
:guitar:

---

