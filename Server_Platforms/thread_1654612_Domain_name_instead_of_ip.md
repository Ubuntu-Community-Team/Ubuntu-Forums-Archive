---
title: "Domain name instead of ip?"
date: 2010-12-28
forum: Server Platforms
---

### Post by Bluesplayer on 2010-12-28
Hi

Ok I have the lastest version of ubuntu server up and running along with a website shopping script working perfectly.  Now I need to change the url in the address bar so that it stops displaying my ip address and shows instead my choice of domain name for whatever page has been opened.  I have a number of domains available and each are redirecting traffic to my home server, but the address bar url alters to my ip address whichever I use.  How then do I go about this change?   Obviously this is to do with dns resolving stuff which I have no experience of.  Can someone put down in as few steps as possible what I need to do?

Thanks in advance
Bluesplayer

---

### Post by WinstonChurchill on 2010-12-29
> **Bluesplayer said:**
> Hi

Ok I have the lastest version of ubuntu server up and running along with a website shopping script working perfectly.  Now I need to change the url in the address bar so that it stops displaying my ip address and shows instead my choice of domain name for whatever page has been opened.  I have a number of domains available and each are redirecting traffic to my home server, but the address bar url alters to my ip address whichever I use.  How then do I go about this change?   Obviously this is to do with dns resolving stuff which I have no experience of.  Can someone put down in as few steps as possible what I need to do?

Thanks in advance
Bluesplayer
Post the output of:
```
dig [yourdomainname]
```

---

### Post by Bluesplayer on 2010-12-29
I did as requested:

> Question Section
shops4u-online.co.uk        IN             A

Answer Section 
shops4u-online.co.uk        86400        IN     A       94.134.40.82

Query Time   59  msec

Serve: 192.168.1.254#53(192.168.1.254)

---

### Post by Ryan Dwyer on 2010-12-29
It looks like your domain name is resolving to someone else's server which then redirects to your IP address. You need to change the A record for your domain so it resolves to your IP address.

---

### Post by Bluesplayer on 2010-12-29
> It looks like your domain name is resolving to someone else's server  which then redirects to your IP address. You need to change the A record  for your domain so it resolves to your IP address.

Ah right.  I think I understand that.  Thanks.  Will give that a try now.

---

### Post by Bluesplayer on 2010-12-29
I removed the webforwarding that was in place and altered the dns setting regarding www A to my own ip address.  The domain isn't connecting to my ip now though.  Is this just a propagation issue as these changes take time to work don't they?  Should I have also altered the @ setting to my ip address?

---

### Post by Ryan Dwyer on 2010-12-29
If 81.174.251.67 is actually your IP address then it's connecting properly. Your config (or /var/www/index.php) is making it redirect to the IP address.

```

ryan@laptop:~$ telnet 81.174.251.67 80
Trying 81.174.251.67...
Connected to 81.174.251.67.
Escape character is '^]'.
GET / HTTP/1.1
Host: shops4u-online.co.uk

HTTP/1.1 302 Found
Date: Wed, 29 Dec 2010 11:32:58 GMT
Server: Apache/2.2.16 (Ubuntu)
Location: http://81.174.251.67/electronics/tvs/
Vary: Accept-Encoding
Content-Length: 43
Content-Type: text/html


The file /var/www/index.php is corrupted.
Connection closed by foreign host.
```

I've never seen that corruption message before.

EDIT: Please post the contents of /var/www/index.php.

---

### Post by Bluesplayer on 2010-12-29
Blast.  I forgot about that redirection I had put in the index file.  I have been experimenting with various scripts which meant that the index file in the root belonged to a script I no longer wanted to use.  I had placed a php redirection code snippet in it but had left the rest of the code alone.  That is why you were getting that corruption message.  I should be able to make sense of this now and get the domain to work properly - I think!

Edit:

What program or command did you use to get the above info?

---

