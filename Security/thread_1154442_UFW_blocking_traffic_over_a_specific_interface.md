---
title: "UFW blocking traffic over a specific interface"
date: 2009-05-09
forum: Security
---

### Post by Oz0n3 on 2009-05-09
I recently installed Ubuntu for the first time and I am coming back to linux after spending the last few years exclusively using OS X.  The box I built has a single purpose and that is to run and download bittorrents over a vpn connection.  My question is, can ufw block traffic over a specific interface?  I want to block all bittorrent traffic going over eth0 but allow bittorrent traffic going over ppp0.  I am pretty sure I can do this in iptables, but thought I would see if ufw was capable of setting this up before figuring out the iptables command. 

Thanks for any help

---

### Post by spasticfraggle on 2009-09-10
Did you ever find a solution? I am looking for exactly the same thing

---

### Post by tryinghard on 2009-10-27
so am I but since iptables and ufw works oin the same things there nust be a way. :) I hope.:)

---

### Post by The Cog on 2009-10-28
I'm not familiar with ufw/gufw, but I do know they are just front-ends to simplify configuring iptables. It may well be that the stuff you want to do cannot be done in ufw, and that you may have to bite the bullet and use iptables commands directly with scripts. Trouble is, once you manually modify the iptables rules, you cannot go back to the higher-lever confgiuration utilities because they will overwrite all your work again. 

If you google for linux iptables configuration script, you will find many examples.

---

### Post by nathan726 on 2011-05-27
I know this is an old topic, but just wanted to share a solution:

By default, ufw applies rules to all available interfaces. To
limit this, specify DIRECTION on INTERFACE (interface aliases 
are not supported). For example:

sudo ufw allow in on eth0
sudo ufw deny out on eth0
sudo ufw deny in on eth0 to any from any port 80 proto tcp

---

### Post by conquerorodueko on 2013-02-25
Alright fellas,... here is what you seek
I am going with the assumption that you know where in your [before.rules] to insert this giving preference to hierarchy. The rule above the other takes precedence.

-A ufw before-input -i eth+ -p tcp --sport 444:65535 -j DROP
-A ufw before-input -i eth+ -p udp --sport 444:65535 -j DROP
-A ufw before-output -o eth+ -p tcp --dport 444:65535 -j DROP
-A ufw before-output -o eth+ -p udp --dport 444:65535 -j DROP

-A ufw before-input -i wlan+ -p tcp --sport 444:65535 -j DROP
-A ufw before-input -i wlan+ -p udp --sport 444:65535 -j DROP
-A ufw before-output -o wlan+ -p tcp --dport 444:65535 -j DROP
-A ufw before-output -o wlan+ -p udp --dport 444:65535 -j DROP

-A ufw before-output -i ppp+ -p tcp --sport 444:65535 -j ACCEPT
-A ufw before-output -i ppp+ -p udp --sport 444:65535 -j ACCEPT
-A ufw before-output -o ppp+ -p tcp --dport 444:65535 -j ACCEPT
-A ufw before-output -o ppp+ -p udp --dport 444:65535 -j ACCEPT

What i am trying to figure now is how to do an interface bypass. That is have tcp port 80 via ppp and tcp 443 via eth and use them simultaneously. If anyone knows how, please be kind to share the knowledge

---

### Post by codemaniac on 2013-02-25
Old thread closed.

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

It is always better to start a fresh thread instead of posting in older threads of others.

Thanks!

---

