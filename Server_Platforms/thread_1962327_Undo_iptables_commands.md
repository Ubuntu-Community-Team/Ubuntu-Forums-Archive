---
title: "Undo iptables commands?"
date: 2012-04-20
forum: Server Platforms
---

### Post by d4m1r on 2012-04-20
Hey guys, I have a virtual private server running 11.10 that I use as a VPN server (OpenVPN) and to get it to route network traffic I had to enter:

```
iptables -A FORWARD -m state &#8211;state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -s 10.8.0.0/24 -j ACCEPT
iptables -A FORWARD -j REJECT
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -j SNAT &#8211;to-source MYIPHERE
```However, the server IP recently changed and my VPN server will no longer connect....I am guessing it is because of the last line of commands. How can I undo it or will just using the same command with my new IP overwrite the old one? :confused:

---

### Post by Doug S on 2012-04-20
You can delete the rule. Delete can be done a few ways, by rule number (which I can not recall how to get the rule numbers at the moment), or by rule specification (the opposite of how it was added).
So for this:```
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -j SNAT –to-source MYIPHERE
```you would enter this (I think):```
sudo iptables -t nat -D POSTROUTING -s 10.8.0.0/24 -j SNAT –to-source MYIPHERE
```

---

### Post by newbie-user on 2012-04-21
If you save your ruleset in a file using iptables-save, you could delete the lines you don't want, then reload the edited file using iptables-restore. That way you don't have to worry about what line number a certain rule is or whatever.

---

### Post by d4m1r on 2012-04-21
> **newbie-user said:**
> If you save your ruleset in a file using iptables-save, you could delete the lines you don't want, then reload the edited file using iptables-restore. That way you don't have to worry about what line number a certain rule is or whatever.


Using -D seems even easier than that or remembering line numbers though, no? ;)

---

### Post by newbie-user on 2012-04-21
> **d4m1r said:**
> Using -D seems even easier than that or remembering line numbers though, no? ;)

Yeah, I suppose in this case it would be easier. For me, though, I run multiple firewalls on my network and I don't always remember which rules are on which server, so it's convenient for me just to check the saved rules file and edit that. But it's all personal preference.

---

### Post by d4m1r on 2012-04-21
> **newbie-user said:**
>  But it's all personal preference.

Agreed. Thanks for the tips guys, I'll be giving this a go over the weekend and will report back :D

---

### Post by SeijiSensei on 2012-04-21
You can also start over by flushing all the rules with 

```
sudo iptables -F
```

---

### Post by d4m1r on 2012-04-26
Thanks guys! -D worked....I was able to shutdown the openvpn process, remove the iptables reference to the old IP, add the new one, and started the service.

Everything worked like a charm on my Ubuntu 11.04 VPS :)

---

