---
title: "slow server response (ssh, ftp, ...) - timeout"
date: 2005-01-06
forum: Server Platforms
---

### Post by flade on 2005-01-06
I've got some questions regarding ssh, ftp, ... 

When I connect to my server using ssh, after typing username, the server does not automatically respond with [ password: ] but I have to wait about 15 - 30 sec.  for [password: ] to appear.

When using ftp to send files to server, it  takes long time to transfer about 30Mb of data. I just put 2 pictures though ftp and In Filezilla I can see that I have to wait about same time as mentioned before fro ssgh (about 10 - 30 sec.) for file upload.

I belive that is called timeout - am I right.


How can I solve this problem. It's very annoying.  I did not have these problems using FC2 or on FreeBSD.

Computer configuration is:

Intel PII 350 MHZ
192 MB RAM
AGP graphics (ATI RAGE 3D)
HDD 1x 6Gb
HDD 1x 20Gb


--------------
++ Fladé

---

### Post by flade on 2005-01-11
To answer myself...

Problem was in DNS settings. I use DNS from my ISP but link is DialUp. 

Problem solved.



Fladé

---

### Post by Mano[FA] on 2005-11-02
Hi!
I hope you'll read this.
I have the same problem. Very long delay before any network service (ftp, ssh...) answer. I also set the DNS because I use it in a LAN not connected to internet and I need that entering "ubuntu" in the address bar of the browser it get the right conversion.
However I didn't exactly understood you auto-answer. Could you explain it mare clearly?

Thanks a lot in advance.

---

### Post by ericbarch on 2006-11-16
I had this same problem and it sure was DNS. I had my system connecting to my Router's DNS address and I had a DNS server running on the computer. I changed the DNS to 127.0.0.1 and everything works great now.

---

### Post by treyd on 2007-01-02
Hate to bring up an old post, but I am having this same problem. I have a server connected to a Linksys WRT54G V.6 Router on the ip address 192.168.1.100.

I fixed my ftpd client by adding 

"IdentLookups off
UseReverseDNS off"

but now, I cannot even connect via ssh. I get a broken pipe or connection closed error when I try to connect. Any ideas?

---

### Post by Kingghost on 2008-01-17
Hello,

I'm having the exact same issues, I have the DNS set to my router and my router uses 4.2.2.2 and 4.2.2.3 DNS. Anyone know how to reslove this?

---

