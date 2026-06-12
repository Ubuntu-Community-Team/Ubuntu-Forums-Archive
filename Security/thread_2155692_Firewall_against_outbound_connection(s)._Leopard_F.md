---
title: "Firewall against outbound connection(s). Leopard Flower compatibility with 12.04?"
date: 2013-06-19
forum: Security
---

### Post by The Phone on 2013-06-19
Hi there!


I'm planning on installing Ubuntu 12.04 after a year  of computer crashes, hard disk crashes and such. I have pretty long  experiences of Ubuntu and Linux in general, so I'm not a real noob. ;)


Anyway,  before this "long" break I used Leopard Flower, a firewall against  outbound connection. Now I see that it hasn't been updated seen  2012-11-30. My question is simple. Is it compatible with 12.04? If not, can it be fixed on a "easy" way?
BTW: Does someone have some experience in other software that does pretty the same job?

Regards

The Phone

---

### Post by TheFu on 2013-06-19
iptables is the built-in firewall for all Linux systems.  There a bunch of different GUIs that just tell iptables what you want.  I don't think iptables has changed that much the last few years, so you could export/save the current firewall settings before you update, then restore them on the 12.04 system after.  The iptables man page explains everything.  Run  **man iptables** to learn everything.

BTW, never heard of "leopard flower."  It definitely is not one of the more popular firewall GUIs.  Those are usually, ufw or firestarter.  I googled and found that project on sourceforge ... seems the developer lost 6 months of work to a single HDD crash.  Scary. No backups in 6 months?  Seriously?!!!!   I won't be using anything from that guy - ever.

---

### Post by Cheesehead on 2013-06-19
Quite a few recommendations popped up when this question was asked at at [http://askubuntu.com/questions/135135/alternative-to-little-snitch-app-firewall](http://askubuntu.com/questions/135135/alternative-to-little-snitch-app-firewall)

The answer seems to be: Yes it works, but you must compile it form source. Other software has come...and gone (abandoned).

---

### Post by Hungry Man on 2013-06-20
I wouldn't take that much time to deal with an outbound Firewall, especially a per-application one. Not unless you're willing to take the time to isolate every application from every other, which is what it would take to make the Firewall effective. I'm not as familiar with Linux APIs or the specifics of bypassing them, but the concepts are the same as on Windows, and it's very easy.

Take the 5 minutes it takes to use GUFW to configure IPTables and then don't spend any more time on an endeavor that won't provide a ton of security to begin with.

---

### Post by TheFu on 2013-06-20
Blocking outbound connections might not help the current systems' security, but it is definitely being a good neighbor.  

It is common in businesses to block all outbound traffic from desktops and force those through proxies and/or gateway systems.  I've deployed firewall rules on routers that block outbound SMTP from desktops after a clients network was overrun with SMTP spamming bots.  If everyone there had been running an outbound blocking firewall filter, they'd have never had that issue.

Another option is to create separate user accounts for every application - this is sorta what Android does.  I've only done this for testing new versions of software like browsers and email programs when I didn't want to risk my main userid/setup.  It worked, but was a pain to remember to use.

Another option is to enable and use the SE-Linux or Apparmor tools.

If I were doing risky things at home, I would probably run a transparent proxy with lots of filtering.  I already block outbound SMTP except to the appropriate email server on the LAN. Of course that server **can** send SMTP anywhere in the world, but it doesn't accept any inbound email except from the LAN - an email gateway handles that.

Anyway, just a few other options.  You'll have to pick the best for your situation and I need to do some reading on these application firewalls and the security concerns around running them. Still, very interesting and thanks for the question and follow ups from others.

---

### Post by The Phone on 2013-06-22
Hi again!

Thanks for all the answers I have gotten! I will return with the result soon! :D

---

