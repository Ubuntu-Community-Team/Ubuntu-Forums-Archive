---
title: "Firewall vs empathy for MSN"
date: 2011-11-30
forum: Security
---

### Post by MadsRC on 2011-11-30
I just configured my ufw, and now can't log into my msn account via Empathy. I can, however, log in if i run:
```
sudo ufw disable
```
So the problem is propably that I need to define the Empathy/msn port?

I've tried to find out which one I need to add, but can't figure it out :S

Can anyone help? my rules look like this:
```
Status: active

To                         Action      From
--                         ------      ----
53/udp                     ALLOW OUT   Anywhere
20,21,25,80,443,8001/tcp   ALLOW OUT   Anywhere
23399                      ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere
53/udp                     ALLOW OUT   Anywhere (v6)
20,21,25,80,443,8001/tcp   ALLOW OUT   Anywhere (v6)
23399                      ALLOW OUT   Anywhere (v6)
Anywhere (v6)              DENY OUT    Anywhere (v6)
```

---

### Post by Thewhistlingwind on 2011-11-30
[http://www.tomshardware.com/forum/95009-45-check-status-port-1863](http://www.tomshardware.com/forum/95009-45-check-status-port-1863)

Try port 1863?

---

### Post by MadsRC on 2011-12-01
I already tried that port, but as empathy still wouldn't log on i deleted the rule. (No need to have unused prots open?).
 
Now that I come to think of it... I didn't tried the port with UDP og TCP... Don't know if that would help.

---

### Post by OpSecShellshock on 2011-12-01
Next thing I would do is close any browser that's running, then fire up Empathy and try to connect to the MSN account with ufw enabled (in this case we want it to get blocked). Immediately afterwards, open a terminal and type this:

```
tail /var/log/ufw.log
```

With any luck the most recent results will be [UFW BLOCK] for what you were just trying to connect to. There will be a section that says "DPT=some number" and that will indicate the server-side port that it is trying and failing to connect to. Take that number and do:

```
sudo ufw allow out [that number]/tcp
```

Then open Empathy and try connecting again.

---

### Post by MadsRC on 2011-12-01
I tried what you said but didn't get much from the logs. This is my logfile:
```
REMOVED LOG
```The only port I can find there is 12805 TCP. I've tried adding that, but that doesn't help me.
I noticed, while I was doing this, that my Gmail in thunderbird (imap) can't connect either, and it tried to do that when I was testing Empathy. Besides, port 12805 only shows up in my logs, whne I'm browsing... So I'm pretty sure it doesn't have anything to do with Empathy or Thunderbird.

Here's my UFW Status
```
mads@mads-VPCF12M1E:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
53/udp                     ALLOW OUT   Anywhere
20,21,25,80,443,8001/tcp   ALLOW OUT   Anywhere
23399                      ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere
53/udp                     ALLOW OUT   Anywhere (v6)
20,21,25,80,443,8001/tcp   ALLOW OUT   Anywhere (v6)
23399                      ALLOW OUT   Anywhere (v6)
Anywhere (v6)              DENY OUT    Anywhere (v6)
```Hope you guys can help me out with both Empathy and Thunderbird(Gmail).

Took the liberty of editing out my WAN IP from the logs :)

---

### Post by MadsRC on 2011-12-01
I added port 465 and 993 and now I can send, recieve and store mails in the "Send folder" (Coouldn't do that unless I added the imap port 993) mails through Thunderbird.

Here's the updated UFW Status:
```
To                         Action      From
--                         ------      ----
53/udp                     ALLOW OUT   Anywhere
20,21,25,80,443,8001/tcp   ALLOW OUT   Anywhere
465                        ALLOW OUT   Anywhere
993                        ALLOW OUT   Anywhere
23399                      ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere
53/udp                     ALLOW OUT   Anywhere (v6)
20,21,25,80,443,8001/tcp   ALLOW OUT   Anywhere (v6)
465                        ALLOW OUT   Anywhere (v6)
993                        ALLOW OUT   Anywhere (v6)
23399                      ALLOW OUT   Anywhere (v6)
Anywhere (v6)              DENY OUT    Anywhere (v6)

```But I still can't get any further with empathy :(

---

### Post by MadsRC on 2011-12-01
I've fixed Empathy.

Seems like MSN uses port 1863/tcp. Adding that helped resolve the problem.

---

