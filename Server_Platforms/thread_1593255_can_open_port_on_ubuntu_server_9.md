---
title: "can open port on ubuntu server 9"
date: 2010-10-11
forum: Server Platforms
---

### Post by othermale on 2010-10-11
I can seem to open port 25565 for a java application (executable jar)
I'm running ubuntu server 9 thoroughly up to date

I have done 
sudo ufw allow 25565
sudo ufw allow out 25565
sudo ufw allow 25565/tcp
sudo ufw allow out 25565/tcp
sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 25565 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 25565 -j ACCEPT

and sudo ufw status verbose shows:

To                         Action      From
--                         ------      ----
22/tcp (OpenSSH)           ALLOW IN    Anywhere
25/tcp (Postfix)           ALLOW IN    Anywhere
80/tcp                     ALLOW IN    Anywhere
443                        ALLOW IN    Anywhere
25565                      ALLOW IN    Anywhere
25565/tcp                  ALLOW IN    Anywhere

25565                      ALLOW OUT   Anywhere
25565/tcp                  ALLOW OUT   Anywhere

Yet connections to port 25565 fail when I have the firewall enabled (sudo ufw enable)
For example canyouseeme.org says "Error: I could not see your service on port (25565) Reason: Connection timed out"

And connections to port 25565 _DO WORK_ when I disable the firewall (sudo ufw disable)
canyouseeme.org says "Success: I can see your service on port (25565)"

I'm obviously not hugely experienced with this so maybe I'm missing something really obvious. Any solution would be hugely appreciated.

---

### Post by arrrghhh on 2010-10-11
I wonder if your iptables command is bashing heads with UFW... I don't think you should be using both.

Either ipt & disable ufw, or ufw and don't touch ipt :D

I could be wrong tho :p

---

### Post by othermale on 2010-10-11
> **arrrghhh said:**
> I wonder if your iptables command is bashing heads with UFW... I don't think you should be using both.

Either ipt & disable ufw, or ufw and don't touch ipt :D

I could be wrong tho :p

yeah, I did the ufw commands first and when they did not work I did the iptable commands but, alack, to no avail.

---

### Post by arrrghhh on 2010-10-11
Ok can you clear out all the IPT stuff and just go with plain UFW?  Then we can try to narrow down the issue.

Also you say when you do "sudo ufw disable" that the port is then opened...?  Makes me wonder if in fact IPT is butting heads with UFW...

---

### Post by othermale on 2010-10-11
> **arrrghhh said:**
> Ok can you clear out all the IPT stuff and just go with plain UFW?  Then we can try to narrow down the issue.

Also you say when you do "sudo ufw disable" that the port is then opened...?  Makes me wonder if in fact IPT is butting heads with UFW...

It seems the problem was the order of the ufw rules: apparently there were some IP specific denials rules before the allow for port 25565. Exactly why this was causing a problem is not known to me but moving the allow up the rule list fixed the problem.

Thanks for answering my post, I do appreciate it. One question though: how would one clear out the iptable commands I listed above? They clearly do not help and may one day cause more confusion than I am already experiencing. ;)

---

