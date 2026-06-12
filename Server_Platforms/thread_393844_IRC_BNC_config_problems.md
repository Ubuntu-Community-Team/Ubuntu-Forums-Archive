---
title: "IRC BNC config problems"
date: 2007-03-26
forum: Server Platforms
---

### Post by Aberrix on 2007-03-26
So I've downloaded and and configured BNC 2.9.4, I am new to this so I follow a guide I found [here]("http://www.webnos.net/members/knowledgebase.php?action=displayarticle&catid=2&id=4").

my configuration file looks like this;
```

listen 6667
adminpass +EXCRYPTED
password +EXCRYPTED
allow *
vhost **vhost.domain.com**
defaultvhost **WAN IP**
pidfile pid.bnc
motdfile motd
logfile bnc.log
```

so then I start it, I connect to the bnc and then to the irc server... however if I do a 'whois' on my nick I still see my WAN info (ie: @c-55-555-55-55.hsd1.mi.comcast.net) but of course the purpose of this is to make it '@vhost.domain.com' (where my actual vhost name is there)... I think I am doing something wrong with the defaultvhost or maybe the vhost? I use ISPConfig so I know there are DNS records in there for my vhost(s), although I am not sure if they are 'A' records or what... any help would be highly appreciated! thanks in advance.

p.s. I should also mention the bnc is on the same server as my shell account and the same place I connect to irc from, also the server is behind a router so it has a local ip (192.168.0.100) and is the DMZ for my router and also running a firewall, unsure if this matters but I thought I would add it.

---

### Post by Aberrix on 2007-03-27
bump?

---

### Post by MrHorus on 2007-03-27
> **Aberrix said:**
> 
p.s. I should also mention the bnc is on the same server as my shell account and the same place I connect to irc from, also the server is behind a router so it has a local ip (192.168.0.100) and is the DMZ for my router and also running a firewall, unsure if this matters but I thought I would add it.

I think you misunderstand what a bouncer does.

I have a home machine that I IRC from and I don't want that IP exposed for security reasons, so I run a bouncer on an server in the US.

I have a reverse DNS mapping for my server's IP so that I appear to be connecting from that - it has to be a seperate machine and it can't be on a local IP as that's not globally resolveable outside of my network.

Can you clarify what you want to do with the bouncer?

---

### Post by Aberrix on 2007-03-27
> **MrHorus said:**
> 
Can you clarify what you want to do with the bouncer?

well all I really want to do is be able to mask my ip (ie: [email]aberrix@mydomain.com[/email]) on IRC.

I cannot run the bouncer on the same box that I am connecting from?

---

### Post by Aberrix on 2007-03-29
anyone?

---

### Post by Aberrix on 2007-04-02
bump

---

