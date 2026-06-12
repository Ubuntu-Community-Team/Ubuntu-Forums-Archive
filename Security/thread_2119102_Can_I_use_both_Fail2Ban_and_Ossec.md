---
title: "Can I use both Fail2Ban and Ossec?"
date: 2013-02-23
forum: Security
---

### Post by Roskow on 2013-02-23
While I'm learning Ubuntu, I still have lingering influence from my time with Windows. From force of habit I'm used to the idea that security programs like AntiViruses can conflict if you put more than one in the same environment. 

I'm looking into Ubuntu security solutions and I've settled on Ossec. Mainly because I was actually able to get it installed and running. 

I'm interested in other tools like Fail2Ban or DenyHosts but I wasn't sure if some of these tools could conflict with eachother.

---

### Post by cariboo on 2013-02-24
A bump for the move.

---

### Post by unspawn on 2013-02-26
> **Roskow said:**
> While I'm learning Ubuntu, I still have lingering influence from my time with Windows. From force of habit I'm used to the idea that security programs like AntiViruses can conflict if you put more than one in the same environment.
Tools with the same or an overlapping purpose don't necessarily have to conflict. It's when they use the same methods that you may find yourself "living in interesting times" ;-p


> **Roskow said:**
> I'm looking into Ubuntu security solutions and I've settled on Ossec. Mainly because I was actually able to get it installed and running. 
While getting about anything to run is commendable, esp. for a new Linux user, it is and should not be a criterion for choosing an (any) application.


> **Roskow said:**
> I'm interested in other tools like Fail2Ban or DenyHosts but I wasn't sure if some of these tools could conflict with each other.
The purpose of both Fail2ban and Denyhosts is to block remote IP addresses. The difference is Fail2ban does this by default using your firewall and Denyhosts using tcp_wrappers (the /etc/hosts.{deny,allow} files). This difference is the deciding factor: using tcp_wrappers means a *networked application* (SSH daemon, web server, etc, etc) decides what connection to allow based on the contents of the /etc/hosts.deny and /etc/hosts.allow files while using the firewall means that if an IP address is blocked *no application is connected to, no files are consulted and no connection can be established at all*. It should be clear the latter is more secure and more efficient.

*BTW since you're implementing things try this exercise if you will: try thinking about *threats* you would want to defend against first. *Then* do research and match tools to use.

---

### Post by Roskow on 2013-03-02
Wasn't sure if this thread would get a response. Thanks for the feedback. 

I'll just say that in my situation I took the plunge into a college competition and I'm in over my head, but that's okay.  I'm running with Ossec because I'm on a time crunch. I just can't wrestle with Suricata anymore it's costing me time.  A week from today we're supposed to compete and each team gets hit with a hacker team. 

I am also looking into Bastille though and I will proceed with caution.  We're all on virtual machines so I'll take a snapshot before I run it.

---

