---
title: "Handle Light DDoS Attacks Programatically"
date: 2016-07-03
forum: Security
---

### Post by RaJiska on 2016-07-03
Hello,

I am hosting game servers on my Linux Ubuntu servers, and these have been subject to DoS attack, the box itself isn't targetted, but the service is; 
it basically floods the UDP protocol and prevent players from having a correct ping.

To this, I have been able to create a script running in background which basically gets a portion lf the traffic on a given port, 
in this portion takes all the IP, and if an IP appears more than X% of the total portion, then is blocked.

Now, the problem is it is no more a DoS attack, but a DDoS one, 
in other words, many IPs are attacking this service making it lag just as it used to with DoS attacks.

These attacks are not powerful enough to fall in the host DDoS mitigation, 
and the server traffic load is far from the maximum it can handle, as I said, the service network itself is flooded.

My question would then be: how would I be able to solve this issue ? (Programatically I guess).

Thanks !

---

### Post by deadflowr on 2016-07-03
*Thread moved to **Security**.*

---

### Post by Doug S on 2016-07-03
It might be possible to do what you want using iptables. However, more information is needed, as it currently is not clear to me if or how to separate real valid traffic from bad guy traffic. Obviously it is desirable to avoid falsely putting a good guy on the bad guy list, yet also desirable to identify bad guys as soon as reasonable. It might be that some packets per unit time can be used, or maybe there is some unique thing in the bad guy packets that can be used to identify them. Can you provide some example packets, perhaps caught with tcpdump, and tell us the port?

---

### Post by Habitual on 2016-07-04
Are there logs are involved in any way?  wink_wink-nudge_nudge
fail2ban.
nuff said.
ipset, denyhosts, others...
Good job on the script. bash? python? How's that working out?
I like fail2ban, it reads the logs and allows what I tell it, and disallows
what I tell it.

I don't "do games" nor are any allowed on my networks, but I tend to
deny all, allow ${shortlist} and ask questions of the living later.

[Ubuntu Documentation on fail2ban]("https://help.ubuntu.com/community/Fail2ban")
[fail2ban.org]("http://www.fail2ban.org/wiki/index.php/Main_Page") is Home.
[DigitialOcean]("https://www.digitalocean.com/community/tutorials/?q=fail2ban") has some good tutorials for the basics (no offense)

Let's say fail2ban does what you need it to, and you decide to start implementing 
it, have you considered using non-standard ports for these games venues, (after
installing and liking fail2ban, that is)?

Good Luck...

---

