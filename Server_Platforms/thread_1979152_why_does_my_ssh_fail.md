---
title: "why does my ssh fail"
date: 2012-05-12
forum: Server Platforms
---

### Post by silverfox983 on 2012-05-12
I have ssh setup for pub key authentication and works password-less via LAN without a problem, but over the interwebz i get this. help is very much appreciated i have been wanting to get this working for too long.      
```
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009 
debug1: Reading configuration data /etc/ssh/ssh_config 
debug1: Applying options for * 
debug2: ssh_connect: needpriv 0 
debug1: Connecting to 173.230.155.164 [173.230.155.164] port 22.  
debug1: Connection established.  
debug1: permanently_set_uid: 0/0  
debug1: identity file /root/.ssh/identity type -1  
debug3: Not a RSA1 key file /root/.ssh/id_rsa.  
debug2: key_type_from_name: unknown key type '-----BEGIN' 
debug3: key_read: missing keytype 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace  
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace  
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace  
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace 
debug3: key_read: missing whitespace  
debug3: key_read: missing whitespace  
debug3: key_read: missing whitespace  
debug3: key_read: missing whitespace  
debug3: key_read: missing whitespace  
debug3: key_read: missing whitespace  
debug3: key_read: missing whitespace  
debug3: key_read: missing whitespace  
debug2: key_type_from_name: unknown key type '-----END'  
debug3: key_read: missing keytype  
debug1: identity file /root/.ssh/id_rsa type 1  
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048  
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048  
debug1: identity file /root/.ssh/id_dsa type -1 ssh_exchange_identification: Connection closed by remote host 
```

---

### Post by Ashtray2 on 2012-05-13
Judging from that message it looks like your RSA is not set up properly.  

I made a video a while back that walks you through OpenSSH server configuration for RSA.  Make sure HD is enabled so you can read the text.

[http://www.youtube.com/watch?v=l3RsKHdu260](http://www.youtube.com/watch?v=l3RsKHdu260)

edit:  blah, edited out irrelevant stuff due to my inability to read.

---

### Post by Ashtray2 on 2012-05-13
What command are you entering into the terminal to connect?

---

### Post by silverfox983 on 2012-05-13
Thanks for your replies I was doing ssh -vvv root@192.168.1.12 but I finally figured it out after hours of intense research jacked on caffein  i had to setup http proxy on ssh client side. *some side notes* I got ssh-copy-id to work by pointing to root@whatever not username silly me,  this was a must because cat rsa_key.pub >> authorizedkeys alone wasn't working as it should.  I have finally achieved what I have been after for months, thanks again for your replies. Man this is powerful technology ..access my 2TB from my phone anywhere.. run commands as if I'm at the computer.. simply amazing. :)

---

