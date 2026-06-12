---
title: "TCP/UDP ports"
date: 2010-03-04
forum: Security
---

### Post by e24ohm on 2010-03-04
Folks:
I am having a hard time understanding this concept, and need a little help.

I want to change a few applications to use different ports, not the default; however, what parts can I use?

I have the following documentation from iana, [http://www.iana.org/assignments/port-numbers]("http://www.iana.org/assignments/port-numbers"); however, which ones are open? Can I use any port that is not used by another application?

For example: I want to run SSH over a different port, along with a Jabber server on a different port.

---

### Post by rookcifer on 2010-03-04
Ports 0-1000 are usually considered "service ports" and should be left alone since many of them have already been "assigned" various services (in a general sense, but this doesn't mean your machine will have active services on all 1000 -- if you do, you have got problems).  Basically, if you interfere with these ports, you might break a current or future service that needs one of these ports.

It is generally recommended to use higher numbered ports.  Anything above 1000 should be OK, but you will still see ports with assigned services above 1000.  Therefore, ports in the 50000-65535 range are a good choice.

---

### Post by pricetech on 2010-03-04
If you check the documentation at IANA a little more closely you will find that 0 to 1023 are Well Known Ports,  1024 to 49151 are Registered Ports, and 49152 to 65535 are Dynamic / Private ports.

According to IANA, help yourself to any port in the Dynamic / Private range.

I'm running SSH in that range and it works just fine.

---

### Post by doas777 on 2010-03-04
just go through theports between 4000 and 48000 looking for "unreserved".

---

### Post by pricetech on 2010-03-04
> **doas777 said:**
> just go through theports between 4000 and 48000 looking for "unreserved".

Not according to IANA.

---

### Post by psusi on 2010-03-04
It is 1024 not 1000.  Anything under 1024 can only be used by root.  Aside from that restriction, you can use any port number you want.  You SHOULD avoid any ports assigned to anything else.

---

### Post by doas777 on 2010-03-04
> **pricetech said:**
> Not according to IANA.

many organizations (ISPs included) filter ports above 49000 incoming statefull (conn not established yet), so a number above the reserved range but below the dynamic range is recommended. they have the added benifet of being easier to remember than the the higher ones.

additionally, while i really respect Jon Postel and all his contributions, IANA is no longer really relevant, save for RFCs. most of their responsibility has been consumed by ICANN.

---

### Post by e24ohm on 2010-03-04
thanks folks...will take a closer look.

---

### Post by bodhi.zazen on 2010-03-04
[LEFT]Honestly, changing the port adds little to security and is a bit of a hassle.

Having to run ssh -p or change the port in putty ...

If your server is secure port does not matter. 

For example, with ssh, use keys, disable password logins, and use denyhosts / fail2ban/ or rules for iptables

Changing the port only helps with the script kiddies, but any port scanner will show the port.

Script kiddies are, IMO, best handled with denyhosts / fail2ban/ or rules for iptables , they go away fast with these tools.
[/LEFT]

---

### Post by e24ohm on 2010-03-04
> **bodhi.zazen said:**
> [LEFT]Honestly, changing the port adds little to security and is a bit of a hassle.

Having to run ssh -p or change the port in putty ...

If your server is secure port does not matter. 

For example, with ssh, use keys, disable password logins, and use denyhosts / fail2ban/ or rules for iptables

Changing the port only helps with the script kiddies, but any port scanner will show the port.

Script kiddies are, IMO, best handled with denyhosts / fail2ban/ or rules for iptables , they go away fast with these tools.
[/LEFT]

Ok understand...thanks.

---

### Post by e24ohm on 2010-03-04
> **bodhi.zazen said:**
> [LEFT]Honestly, changing the port adds little to security and is a bit of a hassle.

Having to run ssh -p or change the port in putty ...

If your server is secure port does not matter. 

For example, with ssh, use keys, disable password logins, and use denyhosts / fail2ban/ or rules for iptables

Changing the port only helps with the script kiddies, but any port scanner will show the port.

Script kiddies are, IMO, best handled with denyhosts / fail2ban/ or rules for iptables , they go away fast with these tools.
[/LEFT]
I'm sorry but what is "denyhosts / fail2ban/"?

---

### Post by bodhi.zazen on 2010-03-04
> **e24ohm said:**
> I'm sorry but what is "denyhosts / fail2ban/"?

They are services which will ban IP addresses after multiple failed attempts to connect to your server.

denyhosts is more specific to ssh, fail2ban covers additional services.

[http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/)

[http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)

They are in the repositories and can be installed with apt-get. You do not need both.

Personally, rather then installing a service, I use iptables. iptables has a steep learning curve.

---

### Post by pricetech on 2010-03-05
> **doas777 said:**
> many organizations (ISPs included) filter ports above 49000 incoming statefull (conn not established yet), so a number above the reserved range but below the dynamic range is recommended. they have the added benifet of being easier to remember than the the higher ones.

I haven't run into that, but certainly if I did I would use one of the ports in the Registered range.  I don't find a difference in my ability to remember them however.  Maybe just my OCD, but I use ports that I can remember based upon some "standard" I impose upon the scenario.

---

### Post by pricetech on 2010-03-05
> **bodhi.zazen said:**
> [LEFT]Honestly, changing the port adds little to security and is a bit of a hassle.[/LEFT]

I always looked at it this way;  You lock your door for security, but if you can hide the door altogether....

I wish I could do that in reality, not just analogy.  I hate salesmen.

But it may not be worth the hassle.  I routinely use ports in the dynamic range, but then I've been playing with this stuff for a while and can generally figure out how to make it work.  For someone who still has the learning curve in front of them it's probably best to stick with standard ports and secure with something like fail2ban which is a breeze to set up and pretty much maintains itself.

PS:  I like your new avatar better than your old one.

---

### Post by bodhi.zazen on 2010-03-05
> **pricetech said:**
> I always looked at it this way;  You lock your door for security, but if you can hide the door altogether....

Aye, the problem is changing the port from 22 only affects the automated script kiddies, but if you change to a non-default port it shows on a port scan (unless it is fire walled).

You might like "port knocking"

[https://help.ubuntu.com/community/PortKnocking](https://help.ubuntu.com/community/PortKnocking)

> PS:  I like your new avatar better than your old one.

Thanks ! :p

---

### Post by pricetech on 2010-03-05
> **bodhi.zazen said:**
> Aye, the problem is changing the port from 22 only affects the automated script kiddies, but if you change to a non-default port it shows on a port scan (unless it is fire walled).

I guess I just have this mindset that attackers are lazy and won't bother to scan all 65535 ports.

> **bodhi.zazen said:**
> You might like "port knocking"

[https://help.ubuntu.com/community/PortKnocking](https://help.ubuntu.com/community/PortKnocking)


Read about that a few times, been meaning to look into it.  I should make that my next "project".

---

### Post by doas777 on 2010-03-05
> **pricetech said:**
> I guess I just have this mindset that attackers are lazy and won't bother to scan all 65535 ports.

not the mention the time involved. the threading involved in scanning several million hosts for all ports would cripple even the fasted server in no time. 

if you have a worm scanning for new victims, it's going to scan for the protocol that has the hole it exploits, rather than testing every port for openness, and then trying to determine if it leads to the right service.

people may call them "script kiddies" but to be honest, that term was invented by security providers to make users feel more secure (since the attackers are just kiddies, obviously they can't hurt you, right?). 

yeah, an inexperienced attacker may not be able to write the framework for exploit development, but they can certainly harness one they purchased to steal your bank account info, if you don't take reasonable precautions. You can't keep a good attacker out if they really want in, but using derogatory terms to describe the vast majority of the computer crime industry, just to pretend that they are not dangerous, is pure hubris.
pride cometh before an intrusion...

---

### Post by bodhi.zazen on 2010-03-05
> **doas777 said:**
> people may call them "script kiddies" but to be honest, that term was invented by security providers to make users feel more secure (since the attackers are just kiddies, obviously they can't hurt you, right?). 

Thank you for that viewpoint of the term. I always viewed the term different. I agree these folks can cause pain, but I have considered them "kiddies" in that they are easily deterred by even the hint of security.

I am not as concerned about attempts to connect to port 22, it is locked down, I am more concerned with the other traffic I see, mysql injections, more persistent port scans, etc.

writing a script to hit port 22 with common user names and common passwords seems so trivial, thus my concept of "kiddies", I see them as looking for easy targets and easily deterred.

You are correct, they can punish you if you are lax.

In terms of the time it takes to port scan, some people have the resources to perform more distributed scans across distributed IP, and these are harder to detect.

---

### Post by Kinstonian on 2010-03-06
> **doas777 said:**
> 
...
people may call them "script kiddies" but to be honest, that term was invented by security providers to make users feel more secure (since the attackers are just kiddies, obviously they can't hurt you, right?). 
...


Actually, the term script kiddie was coined by Marcus Ranum to describe white hats who didn't know what they were doing.

> 
Ironically, I am the person who first coined the expression
"script kiddie" (back in 1994 I think it was...)  - but I originally
used the term not to apply to the ankle-biter cybercriminals,
I was using the term "script kiddy" to describe the first-generation
security auditors! Back in the early 90's, when the "big 6"
first got into the security audit game, they used to send these
ignorami right out of college, with checklists, who'd go around
customer sites looking to see if the /etc/passwd file on
Windows machines had the correct permissions - and they'd
write a report saying that the "passwd file is missing!"

In the sense that I originally coined the expression "script
kiddy" I was referring to those of you who now proudly call
yourselves "pentesters"

Ironic, huh?

mjr. 

[http://seclists.org/bugtraq/2006/Feb/265](http://seclists.org/bugtraq/2006/Feb/265)

Anyway, the overwhelming majority of "noise" on the Internet is from port sweeps, not port scans.  I fairly frequently hear people say once they've changed the port all of the password guessing attacks stopped and they haven't had a single one in years.

Yes, someone could still find the correct port through a port scan (unless you use something like [PSAD](http://cipherdyne.org/psad/docs/features.html)), however, I don't think those who recommend changing the port are saying that's the only thing you should, or the first thing to do, or that it's the best thing to do.  It's just one of the many layers...

---

### Post by OpSecShellshock on 2010-03-06
[I]Back in the early 90's, when the "big 6"
first got into the security audit game, they used to send these
ignorami right out of college, with checklists

[/I]Now that the field has become more sophisticated, they send 10-year industry veterans around, with basically the same checklists. Go team security!

---

### Post by doas777 on 2010-03-08
> **Kinstonian said:**
> Actually, the term script kiddie was coined by Marcus Ranum to describe white hats who didn't know what they were doing.


[http://seclists.org/bugtraq/2006/Feb/265](http://seclists.org/bugtraq/2006/Feb/265)

Anyway, the overwhelming majority of "noise" on the Internet is from port sweeps, not port scans.  I fairly frequently hear people say once they've changed the port all of the password guessing attacks stopped and they haven't had a single one in years.

Yes, someone could still find the correct port through a port scan (unless you use something like [PSAD]("http://cipherdyne.org/psad/docs/features.html")), however, I don't think those who recommend changing the port are saying that's the only thing you should, or the first thing to do, or that it's the best thing to do.  It's just one of the many layers...

Interesting. I recall the first time I heard it. the guy from the isp was trying to tell me that whatever intrusion logs i may have, that they were nothing to worry about, because it was just a "script kiddie". he kept repeating the term, over emphasizing it, in a misguided effort to get me off the phone (so his call times would look good to management).

yeah, I'm inclined to agree, changing ports is "obscurity" and as we all know, obscurity's only place is as part of a depth-of-defense strategy.

@bodhi, sry if I came off sounding harsh. perhaps I overstated my case...

---

### Post by bodhi.zazen on 2010-03-08
> **doas777 said:**
> @bodhi, sry if I came off sounding harsh. perhaps I overstated my case...

Not at all, I appreciated your insights. I believe you have a good point, "script kiddies" should not be dismissed as a non-issue, they can cause problems.

IMO, these types of attacks are to some extent automated and looking for easy targets. Heaven forbid you are an easy target, if you install a server (VNC , SSH) be sure you understand how to secure it.

---

