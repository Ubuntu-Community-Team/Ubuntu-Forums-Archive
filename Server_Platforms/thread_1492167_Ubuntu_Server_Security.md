---
title: "Ubuntu Server Security"
date: 2010-05-24
forum: Server Platforms
---

### Post by kevin11951 on 2010-05-24
Ok, i have recently become obsessed with servers.  I have learned to setup and admin each segment of the LAMP stack.  I have learned DNS (bind9), and setup a firewall (using ufw)

Anyway, with all this, i have never learned about security... but,  I have mysql setup for localhost only, and a separate username/database combo for each site.  SSH is only accessible by rsa keys, and the keys have passwords.  my email server is also only accessible by secure ports with ssl.

But this is not what most people mean by security... so are there any other things i need to do for security?

Also, these are my firewall settings (how secure is UFW?):
```
root@######:~# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
22                         LIMIT IN    Anywhere
80/tcp                     ALLOW IN    Anywhere
25/tcp                     ALLOW IN    Anywhere
10000/tcp                  ALLOW IN    Anywhere
8080                       ALLOW IN    Anywhere
465/tcp                    ALLOW IN    Anywhere
993                        ALLOW IN    Anywhere
995                        ALLOW IN    Anywhere

```

---

### Post by CharlesA on 2010-05-24
It looks fine, as long as you have no ports forwarded at the router.

---

### Post by kevin11951 on 2010-05-24
> **CharlesA said:**
> It looks fine, as long as you have no ports forwarded at the router.

Um... this is a server, connected directly to the Internet... what router?

---

### Post by Agent ME on 2010-05-24
> **CharlesA said:**
> It looks fine, as long as you have no ports forwarded at the router.
He's running a webserver. If he has a router, then he *needs* certain ports open to let people connect.


What do you have running on ports 8080, 10000, 993, and 995 out of curiosity?

Also, another aspect of security is to make sure whatever websites you're hosting have secure code. If you're using a common CMS like WordPress, make sure you keep it up to date. If you're writing your own code, make sure you sanitize your input and output to prevent XSS or SQL injection attacks.

---

### Post by CharlesA on 2010-05-24
> **kevin11951 said:**
> Um... this is a server, connected directly to the Internet... what router?

In that case, you should lock everything down further.

The only port that needs unrestricted access is port 80 and port 25 if you are running a mail server.

There is no reason for port 8080, 10000 (webmin?) and the others being allowed to have unrestricted access from the internet. If you need to, connect via SSH and access them thru SSH tunnels.

22 - ssh              
80/tcp - http
25/tcp - smtp
10000/tcp - webmin?
8080 - ?
465/tcp - ?
993 - ?
995 - email?

---

### Post by kevin11951 on 2010-05-24
> **CharlesA said:**
> In that case, you should lock everything down further.

The only port that needs unrestricted access is port 80 and port 25 if you are running a mail server.

There is no reason for port 8080, 10000 (webmin?) and the others being allowed to have unrestricted access from the internet. If you need to, connect via SSH and access them thru SSH tunnels.

22 - ssh              
80/tcp - http
25/tcp - smtp
10000/tcp - **webmin**
8080 - **Citadel Web Mail GUI**
465/tcp - **Secure SMTP**
993 - **Secure Imap**
995 - **Secure POP**

Filled that out for everyone... only needed port are open...

---

### Post by CharlesA on 2010-05-24
In that case, I would have everything except port 10000 open and use a SSH tunnel to access Webmin. It would be a bit more secure that way.

---

### Post by kevin11951 on 2010-05-24
> **CharlesA said:**
> In that case, I would have everything except port 10000 open and use a SSH tunnel to access Webmin. It would be a bit more secure that way.

done, and done.  webmin is now only accessible from within the LAN.

---

### Post by CharlesA on 2010-05-24
> **kevin11951 said:**
> done, and done.  webmin is now only accessible from within the LAN.

Should be good now. I don't recall any specific attacks that are directed at mail servers, the only one I can recall are attacks on servers running SSH that isn't locked down.

Generally, if you have the services secured, you should be fine.

---

### Post by kevin11951 on 2010-05-24
Isnt there more to security than this?  What about [http://www.snort.org/](http://www.snort.org/), and others like it?

---

### Post by CharlesA on 2010-05-24
That would be used for Intrusion Detection. There is a sticky in the security forum.

---

