---
title: "SSH + geoip"
date: 2013-05-07
forum: Server Platforms
---

### Post by corsairetc on 2013-05-07
Hello,
I am looking for some how to use geoip with ssh. I want block CN,IN... ssh attemps on my server. I was noticed the geoip is the part of ubuntu repositories, is any one hoave some how to or link for setup this.

---

### Post by Lars Noodén on 2013-05-07
I think the best approach would be to try to get geoip to work with IPTables and have IPTables block the connections.  However, it does not work without a bit of fiddling.  I'm also not sure how complete the database is and how up to date it really can ever be.

That said, the package to start with is 'xtables-addons-common' but from there it is unclear how to resolve the error with the missing files.

---

### Post by corsairetc on 2013-05-07
I was think it should be work with ssh allow and deny host.

---

### Post by miegiel on 2013-05-07
I guess you're getting poked a lot by machines from china and india, or machines pretending too.

I tried getting it to work myself in iptables (the firewall) with no success. Though it was more an exercise then a necessity. To be honest (and maybe paranoid) I'm not sure I trust the people who supply the geoip database. For one the practice is frowned upon as being racist and I noticed I was getting poked on my ssh port a lot more after looking on the web for info on how to set it up. Not that I think the people behind the geoip database are really on a mission to make servers racist, but it is a red flag. I'm pretty certain though that some of the sites giving info on how to set it up are collecting IP's of potential victims.

Instead I tightened the security of ssh by creating a public+private key pair and using the key to authenticate while disabling password login. Further I added 2 lines to my iptables to log active outgoing ssh connections in /var/log/syslog and limit how often a new ssh connection can be made. Note that before someone has logged in there's already ssh traffic going out that's part of the (failing) authentication.

My logging line (ppp0 is my network interface facing the internet):
```
-A OUTPUT -o ppp0 -p tcp -m tcp --sport 22 -m conntrack --ctstate ESTABLISHED -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "ssh " --log-level 7 
```
Needs to be put before the line that accepts established ssh connections ofc.

My limiting line:
```
-A INPUT -i ppp0 -p tcp -m tcp --dport 22 --tcp-flags FIN,SYN,RST,ACK SYN -m conntrack --ctstate NEW -m limit --limit 12/hour --limit-burst 2 -j ACCEPT 
```

Drawbacks are that you can get blocked from logging in yourself for 10 minutes if someone evil tried to login to your ssh twice in the past 10 min. This also doesn't work well on machines a lot of different people need to ssh too. And you'll need a key-pair on every machine you want to ssh from (or carry the keys with you on a USB stick or so). Every user will need his/her own key-pair setup too. Loosing your key means you need physical access or another user who has a key to login to create a new key pair.

And don't store the private part of the key pair on the server. ^_^

And finally, don't worry about being poked, if they can't get in they can't get in. Though it might keep you up at night when people are checking if you front door is really locked all the time, after a while you'll sleep fine. No worries, as long as they stay on the other side of the door.

---

