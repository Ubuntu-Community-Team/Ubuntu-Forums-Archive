---
title: "Attacker keeps trying to connect to port 135"
date: 2009-09-12
forum: Security
---

### Post by srudes2 on 2009-09-12
```
Sep 12 ##:##:## ##### kernel: [uptime] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=********************0 SRC=ATTACKERIP DST=MYIP LEN=48 TOS=0x00 PREC=0x00 TTL=122 ID=48645 DF PROTO=TCP SPT=1506 DPT=135 WINDOW=16384 RES=0x00 SYN URGP=0
```
This attacker keeps trying to connect to my ip on port 135 and probabaly wants to exploit some microsoft service(hehe i'm running ubuntu).
The attacker tries this about 80 times a day.
I already put the attacker in my blocklist, but even after a week he still keeps trying.
I did a whois lookup... and it turns out the attacker has the same isp as I do.
Should I contact my isp to get this resolved... or does this happen all the time?

---

### Post by __p1n__ on 2009-09-12
In my experience this happens all the time.  I don't even bother logging dropped packets because the firewall is doing it's job however this is only my personal preference.

Divining intent is something altogether different.  IMHO the better odds are that your ISP neighbor's computer is part of a botnet and is generating this background internet radiation without his or her's knowledge.  It's entirely your own decision whether you complain to your ISP or not.

---

### Post by srudes2 on 2009-09-12
Thank you for you opinion.
I won't report this 'background internet radiation', since it would probably be too much of a hastle. 
Thanks again :)

---

### Post by phillw on 2009-09-12
Sorry to differ, but if the computer is possibly part of a bot-net, the decent thing would be to make them aware of it. 

When their IP ends up on black-lists it can be a reet pain to get it removed.

Phill.

---

### Post by scorp123 on 2009-09-12
> **srudes2 said:**
>  This attacker keeps trying to connect to my ip on port 135 and probabaly wants to exploit some microsoft service(hehe i'm running ubuntu). The attacker tries this about 80 times a day. That by itself would indicate an automatically running bot or worm on an infected Windows-zombie PC and not a human sitting at a keyboard. The noob who owns that PC probably even doesn't know what's going on and/or doesn't really care (... if he did he would not be running an infected Windoze machine ...).

> **srudes2 said:**
>  I already put the attacker in my blocklist, but even after a week he still keeps trying. Well, the owner of that Windoze-zombie PC apparently doesn't care and probably hasn't updated their anti-something-this and anti-something-that and anti-something-whatever programs in a while. That's why the rest of us gets spam and what not all the time: thanks to such sloppy Windows users who have no clue what their PC is secretly doing behind their backs.

> **srudes2 said:**
>  happen all the time? Happens all the time. If you looked more closely you'd see that you most likely also get attacked _ALL THE TIME_ (yes, even right now!) on ports 136, 137, 138, 139, 144, 145 and so on.

These are TCP ports that Microsoft operating systems use for things such as sharing drives, authentication, sharing printers, and what not.

My advice: Don't bother. Just filter those ports. And you might even do yourself a favour by turning off the logging on those ports. There are too many infected Windows PC's out there ... filling your logs with their pathetic attempts to infect your Linux system is kind of pointless.

I have stopped logging those ports long ago. Why bother? The only traffic you can expect from those TCP ports over the Internet are connection attempts from infected Windoze PC's. Once you've seen one such log you've seen them all :)

However, by all means: Keep logging on more important ports (e.g. 22, 23, 25, 80, 110, etc.) turned on.

---

### Post by scorp123 on 2009-09-12
> **phillw said:**
> When their IP ends up on black-lists That's exactly where it belongs. If the owner/user of that Windows system is too stupid to take care of their own installation so that someone was able to turn the system into bot-net-Zombie ... then they are too stupid to use the Internet and should not be connecting to it at all. So IP blacklists are the right place for them.

And the rest of us can enjoy the freed-up bandwidth. :D

---

### Post by 78ufzniyE4 on 2009-09-13
mmh what vnc u using x11vnc or vanigar is so just search on how to change your port:)

---

### Post by scorp123 on 2009-09-14
> **linuxbrother11 said:**
> mmh what vnc u using x11vnc or vanigar is so just search on how to change your port:) VNC??? Did you actually read what this thread is about? #-o

---

