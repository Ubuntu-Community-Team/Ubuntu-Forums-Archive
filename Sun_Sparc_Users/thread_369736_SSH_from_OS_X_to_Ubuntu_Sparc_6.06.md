---
title: "SSH from OS X to Ubuntu Sparc 6.06"
date: 2007-02-24
forum: Sun Sparc Users
---

### Post by whitebunnyflock on 2007-02-24
Hey all,

Have a rather strange problem ssh'ing from OS X 10.4.8 into my Ultra 5 running 6.06.  I am able to ssh into my AMD64 running 6.10 without any problems but when it comes to ssh'ing into my Sparc box I get "Connection closed by <remote host>".  I should mention I am doing this through my wireless connection (have not tried through the wire).

I have tried adding references in my /etc/hosts.allow with reference to my iBook's IP address as well as allowing any IP address to ssh into the box but still the same error message.

I have also tried ssh'ing from OS X into my AMD64 6.10 box and then ssh'ing into the Sparc box and it works just fine.

What do you guys think?

---

### Post by Delta_Farce on 2007-02-25
Are you trying to ssh into the sparc box as root? It's just a guess, but maybe this is disabled somehow? It might also see your wireless network as external, so may not allow you to ssh as root.

---

### Post by whitebunnyflock on 2007-02-25
no I have been specifying the user name so it shouldnt be a problem

i thought about it seeing my wireless as an external network but then you would think I woulndt be able to get into my AMD64 box either?

---

### Post by netztier on 2007-02-26
> **whitebunnyflock said:**
> i thought about it seeing my wireless as an external network but then you would think I woulndt be able to get into my AMD64 box either?

A few basic networking questions:
[LIST]
[*] what does the underlying network topology look like? please describe your network (LAN, WLAN and AccessPoint(s), DSL router, DHCP service etc.)
[*] are all systems on the same LAN/WLAN?
[*] IP adresses and subnet masks are set correctly for the involved systems?
[*] can all systems ping each other?
[*] do some of these boxen have multiple interfaces (because you mentionned "external network")?
[*] if yes, are static routes etc all set correctly?
[/LIST]

best regards

Marc

---

### Post by saneone on 2007-03-13
try:
$ssh user@IP
pass: pass for that user

i have ubuntu x64 running on one computer and FreeBSD on the second...
when i run "$ssh IP" it doesn't work... moreover login as "root" also doesn't work...

---

### Post by whitebunnyflock on 2007-03-13
thx for your replies guys.  I had the same Ubuntu on both Sparc boxes and one I could ssh into with no problem and the other I couldnt.

so i think the first one I loaded Ubuntu onto just had some issues as I reloaded it and it works fine now.

---

