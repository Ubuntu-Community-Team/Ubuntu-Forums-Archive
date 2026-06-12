---
title: "strange connections in netsta"
date: 2008-02-22
forum: Security Discussions
---

### Post by Locuss on 2008-02-22
I've been getting messages from google saying that my search queries look a lot like virus spam, so they're aren't processing my queries. 
I ran a netstat, a few times, with and without my browsers on, and I saw some weird connections that I was not making. For example:

>>netstat -ta
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:31416                 *:*                     LISTEN     
tcp        0      0 localhost:postgresql    *:*                     LISTEN     
tcp        0      0 Surak.local:44127       204.2.145.58:www        TIME_WAIT  
tcp        0      0 Surak.local:44128       204.2.145.58:www        TIME_WAIT  
tcp        0      0 Surak.local:50368       po-in-f91.google.co:www TIME_WAIT 

No browser open, no web server, no ssh, no ftp. All web services closed down... and this is what shows up. How do I track down what processes spawned those connections? There appear to be no weird processes in ps aux...

And now that I found the -p switch, these weird connections don't show up anymore!

---

