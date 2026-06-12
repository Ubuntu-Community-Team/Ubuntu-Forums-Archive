---
title: "antivirus and firewall"
date: 2010-11-20
forum: Security
---

### Post by kokoman on 2010-11-20
Hey guys I'm new to Ubuntu,
just installed it for the first time.
since I'm coming from Windows I wanted to ask if in the Ubuntu world
I also need to install anti virus and firewall programs?

and if I do need to install them which programs do you recommend installing?

---

### Post by ironic.demise on 2010-11-20
Ubuntu needs no AntiVirus and has a firewall installed by default.
open a terminal and type ```
ufw status
```... that's your firewall.

There are already several topics on this, use the search function.

Only need antivirus if you are sending files to windows users and don't want them to catch a virus that maybe you were immune to, in which case I suggest clamav.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by lol768 on 2010-11-20
I have just installed ubuntu 10.10. Is the case below normal?

I can't run that command unless I do:
```
sudo ufw status
```

and then it tells me:
Status: inactive

How do I enable the firewall?

---

### Post by ironic.demise on 2010-11-20
> **lol768 said:**
> I have just installed ubuntu 10.10. Is the case below normal?

I can't run that command unless I do:
```
sudo ufw status
```

and then it tells me:
Status: inactive

How do I enable the firewall?

```
sudo ufw enable
```
disable is just sudo ufw disable...

Are you a target subject to attack or do you run a company network? Because many Ubuntu users don't need a firewall and that's why it's diabled by default. Aswell as that if you NEED a firewall, you might want to get something better than ufw... ufw is just an ip table really.

---

### Post by 3rdalbum on 2010-11-20
You **don't** need a personal firewall running on your computer. A default install of Ubuntu does not listen for incoming connections. You'd only need a firewall if you installed some software that listens (or if you enabled Remote Desktop) and DIDN'T want anyone to be able to connect outside your own computer.

Besides, your broadband modem probably already has a NAT firewall built-in anyway.

Windows requires firewalling because it ships with services enabled that listen for incoming connections, and attackers can take over those services and use them to get access to your computer. Ubuntu doesn't come with any gaping security holes like that, so you don't need the firewall.

---

### Post by matt_symes on 2010-11-20
Hi

The default firewall in Ubuntu is net filter. It is configured by creating rules in iptables using ufw. You dont really need one on a desktop

[http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html)

Kind regards

---

### Post by Verbeck on 2010-11-20
> **kokoman said:**
> 
 and if I do need to install them which programs do you recommend installing?
 
 reasons you might need an anti-virus software is outlined in this link. there's some suggestions too
 [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
 its mostly for the benefit of windows users you interact with
 
 more info on linux viruses, trojans and others
 [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

---

### Post by uRock on 2010-11-20
I recommend reading the [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") thread. Is has a very good explanation of how security works in ubuntu.

Moved to Security Discussions.

---

### Post by ayenack on 2010-11-20
Take a look at this also.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

