---
title: "Connection closed by foreign host. (Mail Server)"
date: 2007-11-17
forum: Server Platforms
---

### Post by jwheel on 2007-11-17
Hi, I fairly new to Ubuntu (and linux in general). I recently started messing around with it about 3 weeks ago because I can see a definite use for it and Im really intrigued. I am running 7.10 server, I have apache/ftp/mysql and php all configured and I believe working fine. 

I recently got interested in setting up an email server. I'm not all that savvy when it comes to setting up the email server for use from the internet, Im sure that&#347; where I´m going wrong. I set up a dynamic domain and it ¨seems" to work (jwheelubuntu.mooo.com) but when I do 

**telnet jwheelubuntu.mooo.com 25**     I get error message 

[B]Trying 72.184.41.101...
Connected to jwheelubuntu.mooo.com.
Escape character is '^]'.
Connection closed by foreign host.[/B]

Supposedly (according to a tutorial Im following) I should be able to 

**telnet mail.jwheelubuntu.mooo.com 25**     in order to do a test but that gives me error message 

**telnet: could not resolve mail.jwheelubuntu.mooo.com/25: Name or service not known**

The tutorial I am following is located at  **[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)**

I´m sure you will need more info, I will supply whatever it is I need to. Any help is greatly appreciated! 

Thanks

---

### Post by adaptu on 2008-03-28
I'm experiencing the same problem on Ubuntu 7.x

My desktop will not resolve local domain names.  It will do a dig fine but it can't ping or connect to any other local machine using the computer name.  Anyone have any clues?  Is it possible to have multiple search lines in the resolv.conf file?  Were there significant changes made between 6.x and 7.x in this area because I've got several other 6.x machines that can resolve the local domains fine.

Thanks.

---

### Post by Mr. C. on 2008-03-30
Are you both trying to use WAN IPs to access your LAN machines from within the LAN ?

If so, your router may not support this form of addressing, and you must use your LAN IPs from within the LAN.

Jwheel - you are using mail.xxx - do you have a DNS A record set up for mail.jwheelubuntu.mooo.com ?

---

### Post by HermanAB on 2008-03-30
For a mail server, you need to have the following things defined correctly, otherwise it won't work:

The hostname, must be a FQDN and it must resolve in DNS:
mail.example.com

DNS Records:
MX record
A record
PTR record

The following ports must be open to the world:
SMTP 25/TCP

Consequently, the only way to get it to work properly, is to get a 'Server Account' from your ISP, with 2 or more IP addresses.  This only costs about $10 per month more than a regular home account and is usually also accompanied by a higher bandwidth allocation.

Cheers,

Herman

---

