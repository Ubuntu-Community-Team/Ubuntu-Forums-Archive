---
title: "Botnet abuse"
date: 2009-11-02
forum: Security
---

### Post by asai on 2009-11-02
Hi,
Yesterday I found that one of my Ubuntu servers was being used as a node in a botnet. I have stopped this attack, but I am a little worried abaut new attacks.
I have another Ubuntu server working as a router. Is there any way I can set my router to monitor the traffic to find if the server is the only node or if there is another also sending?
And is there any way to block this kind of traffic on the router?

---

### Post by Lars Noodén on 2009-11-02
Prevention depends on which botnet, how did it get in, how was it detected, which ports or services it (ab)used.  Can you provide more details?

---

### Post by asai on 2009-11-02
Hi,
Thanks for your reply.
How can i determine which botnet it is?
It used port 22 and obtained a user-name and password from my system.
This user have now been deleted and prevented any new attacks for now.
However I see there is new attempts regularly.

---

### Post by unspawn on 2009-11-02
> **Lars Noodén said:**
> Prevention depends on which botnet, how did it get in, how was it detected, which ports or services it (ab)used.
If you would view it as a *breach of security* then prevention depends on the state of hardening, auditing (alerting), deterrents and misconfiguration, vulnerabilities of provided services and such. AFAIK *which botnet* it is does not matter.

---

### Post by unspawn on 2009-11-02
> **asai said:**
> I have another Ubuntu server working as a router. Is there any way I can set my router to monitor the traffic to find if the server is the only node or if there is another also sending? And is there any way to block this kind of traffic on the router?
Have a look at Snort? Next to the (VRT and) Community ruleset also see the emergingthreats.net ruleset.

---

### Post by unspawn on 2009-11-02
> **asai said:**
> How can i determine which botnet it is? It used port 22 and obtained a user-name and password from my system.
Unless there's a specific reason for needing to find out I'd rather suggest you invest time in properly hardening the machine. Any unprivileged user or root? If root is allowed access you have to configure sshd_config to **deny** that. Was the user using a weak password? Did you have any deterrents like iptables "-m recent" or fail2ban (better) installed? Attempts are logged but *do you actually read those logs* (Logwatch?) to adjust configuration or take measures?

---

### Post by asai on 2009-11-02
I have removed the user that was used and it had a weak password. The root user is untouched. How about changing the ssh port from 22 to another number? If this is a smart move, which port can/must be used?
I will have a look at Snort. Thanks so far.

---

### Post by Lars Noodén on 2009-11-02
> **asai said:**
> I have removed the user that was used and it had a weak password. The root user is untouched. How about changing the ssh port from 22 to another number? If this is a smart move, which port can/must be used?
I will have a look at Snort. Thanks so far.

Moving the port is not a net gain.  

Make sure that root cannot log in via ssh.  Set up sudo for specific tasks.  

You can use iptables or [tcpd](http://linux.die.net/man/5/hosts.allow) to ban the ip range that got in.
  You should also contact the network manager of the ISP that hosted the attack.  Look up the IP number in [whois](http://linux.die.net/man/1/whois) to get the contact info.  That will also give you the network range to block.

---

### Post by asai on 2009-11-04
I have sent mail to some of the ISP's to let them know about their accounts. I have also installed fail2ban and disabled root login on ssh on the server. So far it looks like there is still attacks, but no one gets through.

---

### Post by Chayak on 2009-11-04
Despite what previous posters have said moving your port is effective at reducing the number of attacks by bots.  It's not a magic solution but that in addition to other measures will keep the attacks to a minimum.

---

### Post by Sporkman on 2009-11-05
> **Chayak said:**
> Despite what previous posters have said moving your port is effective at reducing the number of attacks by bots.  It's not a magic solution but that in addition to other measures will keep the attacks to a minimum.

...and it will keep your logs cleaner & easier to spot who's really trying to hack you.

---

### Post by shel-hall on 2009-11-05
> **asai said:**
> I have sent mail to some of the ISP's to let them know about their accounts. I have also installed fail2ban and disabled root login on ssh on the server. So far it looks like there is still attacks, but no one gets through.
Over the years (more of them than I care to count), I've found the following very useful for preventing attacks:

1.  Ban (via firewall, iptables, whatever) those IP ranges from which you will never have legitimate access, or, conversely, ban the world, and only allow connections from known sources of legitimate connection requests.

2.  Use only SSH keys for access, never simple userID/Password access.

3.  Use some form of portknocking.  Even a simple scheme (attempted access on some high port opens the SSH port) will almost eliminate any attacks at all.

The first time I opened an SSH port to the world, it took less than one day for someone to mount an attack; he tried over 3500 account/password combinations before I even saw it in the logs.  

Once I implemented the three techniques above, I never had more than simple port 22 probes; no one could get enough "traction" to do anything more.

-Shel

---

