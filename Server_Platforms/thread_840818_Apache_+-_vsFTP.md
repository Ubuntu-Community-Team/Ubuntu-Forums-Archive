---
title: "Apache +/- vsFTP"
date: 2008-06-25
forum: Server Platforms
---

### Post by Martyn Thompson on 2008-06-25
Hello readers, 

I am about to begin hosting a website on a Virtual Private Server.  The hosting company run Ubuntu servers which is the reason I was attracted to them.  
The website itself won't have much traffic however there will be a number of PDFs available to download. 
In the past I have placed the PDFs in their own directory and just hyperlinked to them (presumably served thro' Apache).  This has been done both on low cost servers and on my own 'webspace' that comes with my ISP account.  
I am writing to ask whether it is better to run vsFTP or some other FTP program for those file transfers as well as using Apache to serve the 'main' web content (html and php)?  
What are the benefits and drawbacks of using FTP server as well as Apache?  Is vsFTP more efficient at larger file transfers than using Apache? 

Do these question make any sense/do they seem valid?! 

Any advice, or pointers to advice in the form of HowTos etc would be gratefully accepted. 

Regards,

Martyn.

---

### Post by cdenley on 2008-06-26
> 
Is vsFTP more efficient at larger file transfers than using Apache?

I've heard this before, but I don't believe it. I tried comparing them on my LAN with proftpd, and apache seemed consistently faster. That may not be an accurate test for slower internet connections, though. I think if you're running apache, you might as well use that. Why bother with an FTP server? It only creates another server application you have to monitor and keep updated which is another possible attack vector. I think the only benefit is FTP server's typically allow better bandwidth restrictions. I'm not sure about vsftpd.

---

### Post by Martyn Thompson on 2008-06-26
Thanks for this cd..

---

### Post by MJN on 2008-06-26
To add to cdenley's comments, which I fully agree with, there are also other benefits in using Apache/HTTP such as supporting ubiquitous standard client access and minimal problems through firewalls/NATs/proxies etc. It definitely makes sense.

Mathew

---

