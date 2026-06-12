---
title: "Confusion about iptables configuration"
date: 2010-05-25
forum: Security
---

### Post by megajune on 2010-05-25
Ubuntu gurus, I need you! I'm trying to ensure that only the following two networks have access to my web server.  10.1.1.0/24  and  192.168.1.0/24  Could someone explain to me how this is done? Note, I've never successfully used IPtables before, so feel free to talk to me like an idiot. I've read the   If needed, my distro is Ubuntu Server 10.4

---

### Post by CharlesA on 2010-05-26
You could tell it to only allow access from those networks.

```
sudo iptables -A INPUT -p tcp -m tcp -s 10.1.1.0/24 --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 80 -j ACCEPT
```

Just be sure you have physical access to the machine if you are messing with iptables - I just locked myself out and needed to reboot it blindly, since the server was running headless. >.<

---

### Post by cdenley on 2010-05-26
If you never used iptables before, you might want to start with a front-end like ufw.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
```

sudo ufw allow proto tcp from 192.168.1.0/24 port 80
sudo ufw allow proto tcp from 10.1.1.0/24 port 80
sudo ufw enable
sudo ufw default deny

```

---

### Post by megajune on 2010-05-26
Thanks for the help! I'm sure I'll get it working now.

---

### Post by megajune on 2010-05-26
Thanks you both for your help.

ufw is great for beginners. I would suggest it to anyone reading this thread with the same problem.

---

### Post by bodhi.zazen on 2010-05-26
More on UFW :

	[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
	[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
	[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

As an aside, if you are using iptables, you can get locked out if you are not careful. A few tips on that :

1. Do not set the default policy to deny. If you do you can lock yourself out with iptables -F (IMO a common mistake).

2. Instead, make the last rule in the chain DROP (or REJECT).

allow rule 1
allow rule 2
limit rule 3
 ...

Last 

iptables -A INPUT -j DROP

3. On a Debian / Ubuntu system you can use iptables-save

```
iptables-save > /etc/iptables.save
```

Make edits to iptables-save

Apply those changes with iptables-apply

```
iptables-apply /etc/iptables.save
```

You will be asked to confirm you still have a connection, if not it will revert.

Example:

```
iptables-apply /etc/iptables.save
Applying new ruleset... done.
Can you establish NEW connections to the machine? (y/N)
Timeout. Something happened (or did not). Better play it safe...
Reverting to old ruleset... done.
```

With no "y" response (lock out), iptables-apply reverts the rules "automagically"

4. On a remote, headless server, after changing your iptables rule set, always open a NEW SSH SESSION before closing your current session.

Not that I have ***ever*** locked myself out of course =)

---

### Post by CharlesA on 2010-05-26
Thanks for the info about iptables-apply. :-)

---

### Post by bodhi.zazen on 2010-05-26
> **CharlesA said:**
> Thanks for the info about iptables-apply. :-)

Glad you liked that little tip :twisted:

---

### Post by CharlesA on 2010-05-26
You wouldn't happen to know how to do that sort of thing when using Webmin would you?

I might just use the terminal to edit iptables, since I've got a bit better grasp on how it works now. :-)

---

### Post by bodhi.zazen on 2010-05-26
Not with webmin, no.

Aye, although the learning curve is steep, once it "clicks" it is not all *that* bad managing iptables from the command line.

---

### Post by kevdog on 2010-05-28
"Learning Curve" very steep however.  I'm not sure if I still really get it -- good for my home use, however if I had to setup an enterprise iptable list, forget it!!

---

### Post by bodhi.zazen on 2010-05-28
> **kevdog said:**
> "Learning Curve" very steep however.  I'm not sure if I still really get it -- good for my home use, however if I had to setup an enterprise iptable list, forget it!!

Depends on the needs. If you need NAT and have multiple subnets, DMZ, use a firwall specific distro or something like shorewall.

---

