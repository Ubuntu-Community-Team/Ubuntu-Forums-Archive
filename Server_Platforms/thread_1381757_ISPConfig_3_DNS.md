---
title: "ISPConfig 3 DNS"
date: 2010-01-15
forum: Server Platforms
---

### Post by trentscott4 on 2010-01-15
I followed the "Perfect Ubuntu 9.10 Server Guide" and have a working ISPConfig3 server w/ apache, mail, dns and ftp.  I own a domain name thru GoDaddy and have the DNS hosted by ZoneEdit.  The A records and MX records point to my external IP and all is working fine.  Do I need to open any ports other than 80 and MySQL for it to work externally?

I've created a new client in ISPConfig and want to run a website for that user.  Lets say I added a user called myname by going "Add New Site" for domain myname.com.  Now how would I put the files in their necessary folder(s) to be viewed from myname.com and [www.myname.com?](www.myname.com?)  Do I need to mess with any DNS settings in ISPConfig?  Also, how would I get DNS setup for email within ISPConfig (I've already got an MX record at ZoneEdit forwarding to my external Comcast IP), just need to make sure the mail all routs correctly within my server.  Looks like I can SSH in and there's a 'myname.com' folder in /var/www and a 'clients' folder in /var/www with folders 'web1' and 'web2' within it.  So far, I can't access any of these direcories locally (i.e. 192.166.1.105/web1 for example).  Any help is appreciated, thanks in advance.

---

### Post by trentscott4 on 2010-01-15
Anyone?

---

### Post by trentscott4 on 2010-01-22
bump

---

