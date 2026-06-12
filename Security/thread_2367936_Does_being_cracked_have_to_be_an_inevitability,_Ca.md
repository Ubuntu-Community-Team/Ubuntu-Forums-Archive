---
title: "Does being cracked have to be an inevitability, Can due vigilance forestall cracking"
date: 2017-08-04
forum: Security
---

### Post by MechaMechanism on 2017-08-04
The subject line says it all.  For myself, constant updating and using security tools like AppArmor and careful editing of config files and sending system audits to another system have enabled me to being avoid being cracked.  It's very common for my Postfix and Dovecott email system to be attacked more than 10,000 times in a several hour period (this count is on the very low end of email systems on the internet, other systems see millions of attacks per hour).  I see the attacks in my system logs as well as AppArmor logging.  I also send all administrative actions and some logs to my Gmail account.  Every time time AppArmor does something it gets logged and all sudo attempts are sent to my Gmail account.  I can see patterns to this and use knowledge to stay ahead of attackers.

BUT and BUTT, is this a losing game?  Will any system on the Internet eventually be cracked?  So far I have seen Google, Facebook and others avoid being compromised on a large scale as other companies have.  Facebook and Google are so far staying ahead of attackers.  Both have bug bounties and both have had major bugs be discovered.  So far they have not had press releases saying 500 million or 1 billion users details have been stolen (Fact Check Please).  Perhaps on a small scale.  It is impressive what one can do when you can afford a large security team.  Many companies have large security teams and yet have been cracked.

Does knowledge and due diligence and careful planning continue to forestall the inevitable or will the bad guys eventually overtake the good guys.  I don't think I'm really in a position to say one way or another.  I don't have a degree in computer science or information systems.  I only know my own system and I do the best I can.  I'm interested in hearing from smarter people than me and hearing from people who have first hand accounts of running systems exposed to the Internet.  If you've been cracked, are you more secure today thanks to that experience?

Lets keep it civil and non-partisan and OS neutral.  There are no right or wrong answers.  Where not here to place blame or tell someone their doing it wrong.  We lead by example and first hand experience and that is the best way to teach.

Your thoughts?

---

### Post by TheFu on 2017-08-05
No.

With every client, I always sat down and slowly went over our plans for what would be done WHEN we were hacked, not if.  Any sufficiently motivated attacker will find a way in, eventually.  We need a plan to minimize the impact, minimize the risks, but being defensive will never be the only solution.

Both facebook and google have been hacked, BTW. They weren't complete take overs, but enough that they spend a huge amount to avoid those prior issues.

Security comes from careful network architecture, careful systems architecture, careful deployment methods, and constant vigilance.  Google has published an overview of their security - makes for interesting reading. They encrypt everything and assume their internal network is compromised, for example.

Security also comes from outside testing of the most common techniques used against your systems.  Hack your own systems first is a mantra for data security professionals.  Data security has so many different specializations today, that it is impossible for a small team to have expertise in all of them.  Just trying to stay informed of current attack techniques is very hard if it isn't your full-time job.

Having a degree doesn't matter so much that I can see.  Data security needs to be a passion, not just a job.

I've been hacked 3 times (1996, 2002, 2014).  2 times over the internet, 1 time at a security conference while running a NetKoTH contest.  My machine was NOT the approved target at the conference.  These experiences AND the follow-up learning about what actually happened has been training like no classroom could provide. When you systems are impacted, your mind changes completely from the calm, confident, security or systems management professional.

My number 1 security tool is  ... 









Automatic, versioned, daily, backups.

---

### Post by QIII on 2017-08-05
> **MechaMechanism said:**
> For myself, constant updating and using security tools like AppArmor and careful editing of config files and sending system audits to another system have enabled me to being avoid being cracked.


... so far.

:)

---

### Post by MechaMechanism on 2017-08-05
> **TheFu said:**
> Having a degree doesn't matter so much that I can see.  Data security needs to be a passion, not just a job.

It definitely needs to be a passion I would agree with that, I'm pretty paranoid.  Then again the paranoid get hacked too.

---

### Post by MechaMechanism on 2017-08-05
> **QIII said:**
> ... so far.

:)

Lol, hopefully I can keep pushing so far out into the future and not make hacked the present, if I'm lucky.

---

### Post by HermanAB on 2017-08-05
Basically, things like users, groups, permissions, Apparmor and SELinux are preventative medicine.

MS ignores most of that with Windows and therefore reap the consequences in spades.

The first and last time one of my machines was cracked was about 1990 - when I was a little know it all, who knew nothing...

---

### Post by Habitual on 2017-08-05
> **MechaMechanism said:**
> I can see patterns to this and use knowledge to stay ahead of attackers.This statement caught my eye.

found in **2015**

```
http://margaretguttshall.org/cata.txt
http://ubimed.com/cata.txt
http://202.191.121.230/ou.pl
http://31.184.194.114/gnu-perl
http://202.191.121.230/stufa.pl
http://23.229.121.186/paf 
```

> I fear not the man who has practiced 10,000 kicks once, but I fear the man who has practiced one kick 10,000 times.

Bruce Lee

Irony: AntiTrust is on TV.

Subscribed with interest...

---

### Post by MechaMechanism on 2017-08-05
> **Habitual said:**
> This statement caught my eye.

found in **2015**

[CODEhttp:]http://margaretguttshall.org/cata.txt
//ubimed.com/cata.txt
[http://202.191.121.230/ou.pl](http://202.191.121.230/ou.pl)
[http://31.184.194.114/gnu-perl](http://31.184.194.114/gnu-perl)
[http://202.191.121.230/stufa.pl](http://202.191.121.230/stufa.pl)
[http://23.229.121.186/paf](http://23.229.121.186/paf) [/CODE]



Irony: AntiTrust is on TV.

Subscribed with interest...
Well, I'm sure that I am on the bottom rung of the totem pole when it comes to security knowledge.  Smarter people than me get some bad medicine on a regular basis.  Bruce lee said it right.  Love that guy's movies.

I do make use of Nmap, Shodan etc.  But nothing may be enough.  We'll see.

---

### Post by Habitual on 2017-08-05
I generally agree with TheFu and I assume every ip is nefarious.
"The bottom rung" ? 
Bottom is is actually a position of great importance. On totems.

"Microsoft/Jorgee" THE most polite abuser I've seen recently.
Constant State of Ready Alertness. Assume the worst, or "What's Plan B?"

Peace.

Good judgment comes from experience, and a lot of that comes from bad judgment. - Will Rogers

---

