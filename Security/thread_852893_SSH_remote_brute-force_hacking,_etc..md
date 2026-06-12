---
title: "SSH remote brute-force hacking, etc."
date: 2008-07-08
forum: Security
---

### Post by mike503 on 2008-07-08
I have a handful of clients I host, and currently I use iptables to block all connections to ports 1-1024, besides for the ones I whitelist.

It's starting to become a hassle, when people's IPs change at home, or when they're traveling, etc. I usually give them /24, sometimes /16 for those DHCP blocks and other ISPs that can change a lot.

However, I know there's probably a smarter solution, and wonder if something packaged with Ubuntu (in a repository) is recommended, perhaps something that will block an IP (or the /24) for a certain amount of time after a certain threshhold of bad password attempts (or even better - completely invalid username attempts) instead of having to update my iptables rules every time someone has a new IP block?

I believe my friend was using APF, but I thought I'd ask it here and see if people have any good ideas, and something that's in the Ubuntu repository and hopefully easy to configure/logs when things happen so I know what's going on...

It seems like when I open up my SSH, I am getting thousands of attempts per day, filling up my logfiles, and I swear sometimes it even starts choking sshd... so if there is a way to open it up but close it down for bad behavior from certain netblocks for a certain amount of time that'd be perfect (unless you guys have any other ideas)

I've thought about port knocking, or just having it listen on an alternate port, but at work our proxy only allows port 22; so I'd actually be locking myself out by doing that.

Thanks in advance...

---

### Post by hyper_ch on 2008-07-08
have a look at denyhosts

it will auto-blacklist IP after X unsuccessful tries in a given amount of time... you can select to (a) block only ssh access or (b) block all access from that ip and you can automatically remove the aver Y days.

You'll just need to edit the config file accordingly.

---

### Post by mike503 on 2008-07-08
> **hyper_ch said:**
> have a look at denyhosts

it will auto-blacklist IP after X unsuccessful tries in a given amount of time... you can select to (a) block only ssh access or (b) block all access from that ip and you can automatically remove the aver Y days.

You'll just need to edit the config file accordingly.

that says it uses hosts.deny; are tcp wrappers effective enough? i'd love to just block the ips using iptables...

I'm searching the repo right now (apt-cache search firewall) and these look possible too:

fail2ban - bans IPs that cause multiple authentication errors

sshguard - protects from brute force attacks against ssh

Anyone used any of them?

---

### Post by hyper_ch on 2008-07-08
I think fail2ban will put rules into iptables... but sofar denyhosts works wonderful on my servers

---

### Post by mike503 on 2008-07-08
> **hyper_ch said:**
> I think fail2ban will put rules into iptables... but sofar denyhosts works wonderful on my servers

do tcp wrappers work when ssh runs standalone? i believe they do. i thought it used to only work if the program was launched through xinetd/inetd/tcpd...

also - do you get logfile noise from it when a host is blocked? i want to keep my logfiles from filling up and also reduce the load on sshd/other daemons if possible. so if tcp wrappers will stop it before it has to go into the authentication process and such, that might work good enough.

---

### Post by hyper_ch on 2008-07-08
the single most effective method to reduce noise it to move ssh to a different port (although I don't like doing that - as I don't see any real advantage).

But I'm not sure if there will be attempts or not.... just try it outl

---

### Post by csm888 on 2008-07-08
I used to get thousands of hack attempts on my sshd each day. Moving it to a different port solved my problem.

I also got a list of Chinese, Hong Kong, Korean (etc) IP's,  and use  iptables to block them all. (luckily my sites are not relevant to that part of the world). That also cuts out a load of junk.

---

### Post by mike503 on 2008-07-08
I guess it would help to know how much resources it takes for a hosts.deny entry to occur.

i.e. does it actually hit the daemon, or is it denied before it goes into authentication/sshd/etc.

if it doesn't hit the daemon that might work just fine and the simpler denyhosts program might work well enough.

---

### Post by brian_p on 2008-07-08
> **mike503 said:**
> i.e. does it actually hit the daemon, or is it denied before it goes into authentication/sshd/etc.

A connection is made on port 22. sshd sends the IP to tcp wrappers asking 'what do think of this?'. tcp wrappers consults hosts.allow and hosts.deny and says 'no way!'. ssh denies the attempted authentication.

---

### Post by mazato on 2008-07-17
Have you guys looked at Port-knocking:
[http://www.portknocking.org/](http://www.portknocking.org/)
Unless your clients don not compromise their clients.
You can also disable password authentication and use PKI.
You can also try rate-limiting SYN packets on your sshd port.

---

### Post by mike503 on 2008-07-17
> **mazato said:**
> Have you guys looked at Port-knocking:
[http://www.portknocking.org/](http://www.portknocking.org/)
Unless your clients don not compromise their clients.
You can also disable password authentication and use PKI.
You can also try rate-limiting SYN packets on your sshd port.

i said i didn't want port knocking, and changing the authentication method won't help. it's choking up my sshd and wasting resources being flooded with requests.

the best bet is an iptables/pure firewall solution that will allow me to open up sshd, but block invalid passwords/etc. after $x attempts for at least a period of $y

(i already have a synflood rule to prevent normal synfloods as well)

---

### Post by Keeters on 2008-07-17
This should do what you're looking for. I originally found it on [http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1274148,00.html](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1274148,00.html)

I've used this or varients of this for a while and it works just fine.
It allows 2 connections per host per 60second time periods. I hope this is what you were looking for.

iptables -N SSH_RECENT
iptables -A INPUT -m state --state NEW -p tcp --dport 22 -j SSH_RECENT
iptables -A SSH_RECENT -m recent --set --name SSH
iptables -A SSH_RECENT -m recent --update --seconds 60 --hitcount 2 --name SSH -j DROP

---

### Post by Rhubarb on 2008-07-17
I'm using sshguard here, it works very well.  Just have a config file to setup which gives good flexibility.
Banned IPs are stored in /etc/hosts.deny
As my server is not up 24/7 I don't get that many people trying to hack in, but on average I get ~ 2 or 3 tries a day.

I've setup sshguard to ban IP addresses upon unsuccessful login on 1 attempt for root, and 2 attempts for general users indefinitely.
It is possible to use sshguard to download an updated list of IP addresses that are reported by various sshguard users around the world.

If I wanted to be more security conscious, I'd move my ssh port much higher for starters.

Hope this helps, I do recommend sshguard.
I did read somewhere that fail2ban is somewhat broken in hardy.

---

### Post by The Cog on 2008-07-18
I read recently about a distributed brute force network that uses a botnet, and only ever makes two login attempts from any one compromised host. This avoids triggering most brute force protection systems. Probably the only protection against this is good passwords or better still, using certificates.

---

### Post by kevdog on 2008-07-18
Where did you read fail2ban is broken in Hardy?  I don't use this but haven't seen this anywhere.

---

### Post by Oldsoldier2003 on 2008-07-20
> **The Cog said:**
> I read recently about a distributed brute force network that uses a botnet, and only ever makes two login attempts from any one compromised host. This avoids triggering most brute force protection systems. Probably the only protection against this is good passwords or better still, using certificates.

ssh certs and configuring ssh to only allow specified accounts FTW. Deny hosts works pretty good but is really redundant if you use certs and restrict ssh to authorized accounts.

---

