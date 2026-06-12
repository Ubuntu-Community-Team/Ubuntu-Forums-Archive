---
title: "Box rooted...Gaim responsible?"
date: 2006-04-22
forum: Server Platforms
---

### Post by trent dillman on 2006-04-22
Ok, I thought I had my Dapper install locked down. No errant services (no postfix or anything). nmap couldn't find anything. Firestarter was up and running. Portsentry was watching.

A friend of mine uses an old HP that wouldn't run a version of windows newer than ME, so I got him to use Linux a while back. This box had been running various incarnations of Mandriva. A week ago, he saw my Ubuntu box and asked if I'd help set him up. So, now he has Dapper running no errant services and Firestarter.

Now, just because he runs Linux doesn't mean he knows the ins and outs, regardless of the fact that he's been running Linux for almost 2 years. He needed some help installing something I had forgotten. He and I met on AIM.

This is where it goes to hell.

I logged on to gaim, as did he. As we were were chatting, I noticed some weird traffic on the list I had on the desktop (because conky is so very cool). There were 3 aol hostnames and an IP. The ip whois showed AOL, so I thought nothing of it. Then, after a few more minutes, I noticed my network traffic monitor was spiked all the way, which was odd considering the only thing running that I knew of was gaim. Out of curiosity, I did an nmap scan on my friend's box. He was loaded. I scanned mine. Loaded.

:-(

I disconnected immediately, booted into Knoppix and started searching my box. I found syslog entries from Portsentry, but nothing else that I could see. chkrootkit found nothing, and neither did rkhunter.

Anyways, my box is already reformatted, with only the / mounted (my old home and shared partitions are still intact, but no way am I mounting those yet!). I'm in the process of locking it down even tighter right now, but I'm not sure how much it's really worth.

So, my word of warning: someone's figured out a nasty exploit for either gaim (probably) or Dapper.

And if I get owned again...it's another distro for me...

---

### Post by RavenOfOdin on 2006-04-22
If that's true, you can bet I'm not using gaim again.

---

### Post by trent dillman on 2006-04-22
Argh, I'm an idiot.

Portsentry bound to many ports gave the illusion of open ports. I guess the portsentry logs in syslog were from my own damn scans!

Well, screw portsentry. All I have to say is

apt-get --purge remove

---

### Post by RavenOfOdin on 2006-04-22
[QUOTE=trent dillman]Argh, I'm an idiot.

Portsentry bound to many ports gave the illusion of open ports. I guess the portsentry logs in syslog were from my own damn scans!

Well, screw portsentry. All I have to say is

apt-get --purge remove[/QUOTE]

Lol :D

Don't worry, it happens to the best of us.

---

### Post by trent dillman on 2006-04-22
And to think...I formatted / because of that stupid mistake....

argh!

Sysadmin I ain't! :-P

---

### Post by h3llfyr3 on 2006-04-23
There is currently a private exploit in the wild for GAIM, at least I was offered a trade on it last week.
I'm told the source of the problem is the libgadu library, I can believe this as libgadu has a history of insecurity.

---

### Post by LordHunter317 on 2006-04-23
Which won't do a thing if you're not using Gadu-Gadu.  

People need to not panic and make sure to take careful and accurate measurments.  This is a perfect example of this.

---

### Post by nocturn on 2006-04-24
Indeed, remaining calm is the best thing to do.

But even in the event that such a thing were possible, it would have been a flaw in gaim, not Ubuntu and switching distro would not help.

Secondly, if you got hacked through gaim, the attacker would still be in your local account, not root.  So rebuilding your box shouldn't be needed in this case, fixing the flaw and changing your password would (restore home directory from backup).

---

### Post by beeldings on 2006-04-28
> 
Portsentry bound to many ports gave the illusion of open ports.


I find that if you set Portsentry to run in advanced mode, you will get let false-positives when running rkhunter or chkrootkit. In a terminal:
```

sudo nano /etc/default/portsentry

```
change the following lines:
```

TCP_MODE="tcp"
UDP_MODE="udp"

```
to:
```

TCP_MODE="atcp"
UDP_MODE="audp"

```
save the file and exit nano (CTRL+X).

This worked me for when rkhunter reported my machine was infected with the scalper and slammer worms. Now it reports that my machine is clean.

---

### Post by RavenOfOdin on 2006-04-30
[QUOTE=beeldings] you will get let false-positives when running rkhunter or chkrootkit. [/QUOTE]

You'll get false positives running those two apps at the same time, too.

---

