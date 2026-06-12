---
title: "Help with firewall?!"
date: 2008-12-04
forum: Security
---

### Post by rollyah on 2008-12-04
Hi All,

i have a specific goal in mind, and thats to deny all access to the internet both incoming and outgoing except 4 Public ips.
these ips are related to callcentric.com
the reason am doing this, is i want to make sure nothing uses my bandwidth except for these destinations..
i've tried with UFW. but seems its user's defined rules are only set for incoming traffic.
as i noticed theres a preceeding rules that allow all outgoing trraffic.
am obviously a newbie so i dont know how to proceed from there!

i gave firestarter a try as well, even though i add the destined public ips, and set the policy to restrictive by default for outgoing usage. i still can browse to everything i desire. and all incoming traffic is denied even though i defined the services i want to allow for incoming access..


any help would be appreciated.. :)

---

### Post by cdenley on 2008-12-04
You can do something like this:

/etc/network/if-pre-up.d/iptables
```

#!/bin/sh
iptables -F
iptables -P INPUT DROP
iptables -A INPUT -s ip1.xxx.xxx.xxx -j ACCEPT
iptables -A INPUT -s ip2.xxx.xxx.xxx -j ACCEPT
iptables -A INPUT -s ip3.xxx.xxx.xxx -j ACCEPT
iptables -A INPUT -s ip4.xxx.xxx.xxx -j ACCEPT
iptables -P OUTPUT DROP
iptables -A OUTPUT -d ip1.xxx.xxx.xxx -j ACCEPT
iptables -A OUTPUT -d ip2.xxx.xxx.xxx -j ACCEPT
iptables -A OUTPUT -d ip3.xxx.xxx.xxx -j ACCEPT
iptables -A OUTPUT -d ip4.xxx.xxx.xxx -j ACCEPT

```
You will need to add rules if you want to allow DNS queries or LAN traffic.

then make the script executable, and run it
```

sudo chmod +x /etc/network/if-pre-up.d/iptables
sudo /etc/network/if-pre-up.d/iptables

```

---

### Post by lovinglinux on 2008-12-04
> **rollyah said:**
> i gave firestarter a try as well, even though i add the destined public ips, and set the policy to restrictive by default for outgoing usage. i still can browse to everything i desire. and all incoming traffic is denied even though i defined the services i want to allow for incoming access..

Did you disable UFW first? If you don't, then it could overwrite Firestarter rules.

Despite some issues Firestarter might have, that has been already debated extensively in the forums, it works like a charm for both outgoing and incoming connections. So check your iptables rules for conflicts.

I'm currently using custom iptables rules, but I used Firestarter for some time and it works great.

---

### Post by rollyah on 2008-12-05
Hello,

thanks for the help appreciated:)

this is the output of wht i've done:

iptables -F
iptables -P INPUT DROP
#PUBLIC IPS THAT I NEED TO ACCESS MY PC
iptables -A INPUT -s X.X.X.35 -j ACCEPT
iptables -A INPUT -s  X.X.X.36 -j ACCEPT
iptables -A INPUT -s X.X.X.22 -j ACCEPT
iptables -A INPUT -s X.X.X.31 -j ACCEPT
iptables -A INPUT -s  X.X.X.37 -j ACCEPT
iptables -A INPUT -s  X.X.X.34 -j ACCEPT
iptables -A INPUT -s  X.X.X.23 -j ACCEPT
iptables -A INPUT -s  192.168.0.0/24 -j ACCEPT
iptables -P OUTPUT DROP
#PUBLIC IPS THAT I NEED THE PC TO EXPLICITLY ACCESS THEM
iptables -A OUTPUT -d X.X.X.23 -j ACCEPT
iptables -A OUTPUT -d X.X.X.34 -j ACCEPT
iptables -A OUTPUT -d X.X.X.37 -j ACCEPT
iptables -A OUTPUT -d X.X.X.31 -j ACCEPT
iptables -A OUTPUT -d X.X.X.22 -j ACCEPT
iptables -A OUTPUT -d X.X.X.36 -j ACCEPT
iptables -A OUTPUT -d X.X.X.35 -j ACCEPT
#MY DNS
iptables -A OUTPUT -d 4.2.2.2 -j ACCEPT
#MY LAN
iptables -A OUTPUT -d 192.168.0.0/24 -j ACCEPT
#ALLOWING DNS
iptables -A INPUT -p udp -i eth0 --destination-port 53 -j ACCEPT

but the prob remains, i cant ping these destinations nor reach them through my browser.

any advice on what im doing wrong?

> **cdenley said:**
> You can do something like this:

/etc/network/if-pre-up.d/iptables
```

#!/bin/sh
iptables -F
iptables -P INPUT DROP
iptables -A INPUT -s ip1.xxx.xxx.xxx -j ACCEPT
iptables -A INPUT -s ip2.xxx.xxx.xxx -j ACCEPT
iptables -A INPUT -s ip3.xxx.xxx.xxx -j ACCEPT
iptables -A INPUT -s ip4.xxx.xxx.xxx -j ACCEPT
iptables -P OUTPUT DROP
iptables -A OUTPUT -d ip1.xxx.xxx.xxx -j ACCEPT
iptables -A OUTPUT -d ip2.xxx.xxx.xxx -j ACCEPT
iptables -A OUTPUT -d ip3.xxx.xxx.xxx -j ACCEPT
iptables -A OUTPUT -d ip4.xxx.xxx.xxx -j ACCEPT

```
You will need to add rules if you want to allow DNS queries or LAN traffic.

then make the script executable, and run it
```

sudo chmod +x /etc/network/if-pre-up.d/iptables
sudo /etc/network/if-pre-up.d/iptables

```

---

### Post by pg-rugby on 2008-12-05
what is the output of:

'sudo iptables -L'

---

### Post by Valtiel on 2008-12-05
Is there a GUI for iptables?

---

### Post by MarblePanther on 2008-12-05
gufw works nicely

---

### Post by rollyah on 2008-12-06
this is the output:


root@roland:~# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


i've disabled the firewall at the moment..

ps: i used gufw, as well as cli's ufw.. it only allows u to add rules AFTER the "outgoing" accept default rule.
so it doesnt do me good to use it..
the best way is i guess wht i got advised to do in the previous post through a script, but seems theres something am doing wrong ..

> **pg-rugby said:**
> what is the output of:

'sudo iptables -L'

---

### Post by lovinglinux on 2008-12-06
> **rollyah said:**
> this is the output:


root@roland:~# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


i've disabled the firewall at the moment..

These rules means that you are allowing all traffic.

> **rollyah said:**
> i've disabled the firewall at the moment..

I guess you mean "firewall manager" otherwise, doesn't make sense to post the output of "iptables -L" command. Anyway, if you inserted your custom rules after disabling ufw, then something is wrong. If the last thing you did before running the "iptables -L" command that generated the output above was disabling ufw, then you should add your custom rules again. As far as I recall, when you disable ufw it flushes the iptables rules, so you get the output above.

---

### Post by petunya on 2008-12-11
> **lovinglinux said:**
> These rules means that you are allowing all traffic.



I guess you mean "firewall manager" otherwise, doesn't make sense to post the output of "iptables -L" command. Anyway, if you inserted your custom rules after disabling ufw, then something is wrong. If the last thing you did before running the "iptables -L" command that generated the output above was disabling ufw, then you should add your custom rules again. As far as I recall, when you disable ufw it flushes the iptables rules, so you get the output above.
[COLOR="Black"]
if i stop the fire wall it will really damage my computer [jammer]("http://www.phantom.co.il") ? i read all the answers but its to hart for me to anderstend[/COLOR]

---

### Post by cdenley on 2008-12-11
You can't resolve any domain names because you don't allow DNS responses to come in.
```

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 

```
If you have more problems, then post the output of this command, substituting a domain/port you are trying to allow.
```

nc -z -v callcentric.com 80

```

---

