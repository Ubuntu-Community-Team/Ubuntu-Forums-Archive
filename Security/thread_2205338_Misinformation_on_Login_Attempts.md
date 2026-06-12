---
title: "Misinformation on Login Attempts"
date: 2014-02-13
forum: Security
---

### Post by richard30 on 2014-02-13
I'm running Ubuntu Server (Lucid). I found this manpage: [http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html). It lies to me.

I'm trying to limit the number of login attempts (and add a one-minute delay). The manpage says "**ufw**[COLOR=#333333][FONT=inherit] will deny connections if  an  IP [/FONT][/COLOR][COLOR=#333333][FONT=inherit]address  has attempted to initiate 6 or more connections in the last 30 [/FONT][/COLOR][COLOR=#333333][FONT=inherit]seconds.[/FONT][/COLOR][FONT=inherit]" However, after 3 attempts, my connection is dropped AND I can try again immediately--there is no 30-second delay.

The manpage also redirects me elsewhere for more detailed information: "[/FONT][COLOR=#333333][FONT=inherit]See  [/FONT][/COLOR][http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)[COLOR=#333333][FONT=inherit]   for [/FONT][/COLOR][COLOR=#333333][FONT=inherit]details.[/FONT][/COLOR][FONT=inherit]" When I follow *their* instructions...
[INDENT]iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent \
  --set

iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent \
  --update --seconds 60 --hitcount 4 -j DROP[/INDENT]
...and reboot, I **still** get the same behaviour (ie, [/FONT]after 3 attempts, my connection is dropped AND I can try again immediately). Nothing I do seems to work.
[FONT=inherit]
I can find no definitive information on how to solve this. Ubuntu's documentation is sadly lacking--or worse, misleading--in this regard.


[/FONT]

---

### Post by sandyd on 2014-02-13
> **richard30 said:**
> I'm running Ubuntu Server (Lucid). I found this manpage: [http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html). It lies to me.

I'm trying to limit the number of login attempts (and add a one-minute delay). The manpage says "**ufw**[COLOR=#333333][FONT=inherit] will deny connections if  an  IP [/FONT][/COLOR][COLOR=#333333][FONT=inherit]address  has attempted to initiate 6 or more connections in the last 30 [/FONT][/COLOR][COLOR=#333333][FONT=inherit]seconds.[/FONT][/COLOR][FONT=inherit]" However, after 3 attempts, my connection is dropped AND I can try again immediately--there is no 30-second delay.

The manpage also redirects me elsewhere for more detailed information: "[/FONT][COLOR=#333333][FONT=inherit]See  [/FONT][/COLOR][http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)[COLOR=#333333][FONT=inherit]   for [/FONT][/COLOR][COLOR=#333333][FONT=inherit]details.[/FONT][/COLOR][FONT=inherit]" When I follow *their* instructions...
[INDENT]iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent \
  --set

iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent \
  --update --seconds 60 --hitcount 4 -j DROP[/INDENT]
...and reboot, I **still** get the same behaviour (ie, [/FONT]after 3 attempts, my connection is dropped AND I can try again immediately). Nothing I do seems to work.
[FONT=inherit]
I can find no definitive information on how to solve this. Ubuntu's documentation is sadly lacking--or worse, misleading--in this regard.


[/FONT]

You need to save the iptables rules and restore them on boot - because iptables rules - though they take effect immediately,  are lost on a reboot.

---

### Post by richard30 on 2014-02-13
Thanks! It works now.

---

### Post by thnewguy on 2014-02-13
> **richard30 said:**
> I'm running Ubuntu Server (Lucid). I found this manpage: [http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html). It lies to me.

I'm trying to limit the number of login attempts (and add a one-minute delay). The manpage says "**ufw**[COLOR=#333333][FONT=inherit] will deny connections if  an  IP [/FONT][/COLOR][COLOR=#333333][FONT=inherit]address  has attempted to initiate 6 or more connections in the last 30 [/FONT][/COLOR][COLOR=#333333][FONT=inherit]seconds.[/FONT][/COLOR][FONT=inherit]" However, after 3 attempts, my connection is dropped AND I can try again immediately--there is no 30-second delay.

[/FONT]
The man page is not lying to you, the man page is correct. You just are not understanding what it says. When ufw is set to limit connections it makes sure that only six connection attempts can be made to a single port within a 30 second window. That means if six connections happen from one IP address within 25 seconds of each other, the seventh connection will be blocked from connecting for 5 seconds. There is no 30 second delay because there isn't supposed to be one (unless all six connections happen within one second of each other).

It helps to think of ufw's filter as a moving bracket. If three connections happen within 15 seconds, then you can have another three connections for the next 15 seconds. The bracket keeps moving forward in time "forgetting" old connections and opening up free slots for new connections, up to six within 30 seconds.

---

### Post by raja.genupula on 2014-02-13
Hi

Have you heard about Artillery ? Its exactly does what you want and more than that. 
[https://www.trustedsec.com/october-2011/new-tool-release-artillery-for-linux-protection/](https://www.trustedsec.com/october-2011/new-tool-release-artillery-for-linux-protection/)

---

