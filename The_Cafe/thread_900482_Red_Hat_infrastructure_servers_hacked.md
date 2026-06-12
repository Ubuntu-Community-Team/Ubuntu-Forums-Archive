---
title: "Red Hat infrastructure servers hacked"
date: 2008-08-25
forum: The Cafe
---

### Post by Sporkman on 2008-08-25
[http://www.pcworld.com/businesscenter/article/150212/hackers_crack_into_red_hat.html](http://www.pcworld.com/businesscenter/article/150212/hackers_crack_into_red_hat.html)

> 
**Hackers Crack into Red Hat**

John Fontana, Network World 
Saturday, August 23, 2008 5:35 AM PDT

Red Hat confirmed Friday that hackers compromised infrastructure servers belonging to the company and the Fedora Project, including systems used to sign Fedora packages.

In the Fedora breach, company officials said they had "high confidence" the hackers did not get the "passphrase used to secure the Fedora package signing key." Regardless, the company has converted to new Fedora signing keys.

Red Hat's Fedora project leader Paul Frields made the announcement Friday on the fedora-announce-list with the subject line "Infrastructure Report." When contacted, Red Hat officials pointed to Frields' announcements as the company's official statement.

In the Red Hat compromise, the intruder was able to sign a small number of OpenSSH packages relating to Red Hat Enterprise Linux 4 (i386 and x86_64 architectures only) and Red Hat Enterprise Linux 5 (x86_64 architecture only).

As a precaution, Red Hat released an updated version of those packages, a list of tampered packages and a script to check if any of the packages are installed on a user's system.

"This is a significant issue and they have to work to address it," says Jay Lyman, an open source analyst with The 451 Group. "These are some of the growing pains of a distribution becoming more complex. They are building more and more into their operating systems, and with that comes more complexity and more challenges. But what I think is most important here is the response."

Red Hat first hinted at a problem on Aug. 14, when Frields wrote that the Fedora infrastructure team was investigating an issue that could result in some service outages. The message was followed up on Aug. 16 saying the team was "continuing to work on the problem."

By that time, there were grumblings and rumors online and in discussion groups that internal systems may have been hacked, which indeed was the case, and was confirmed Friday by Red Hat.

In his announcement, Frields said changing the Fedora signing keys could require "affirmative steps" from every Fedora system owner or administrator, and said, if needed, those steps would be made public.

Frields also said that through checks of Fedora packages and source code that the company did not think packages had been compromised and said "at this time we are confident there is little risk to Fedora users who wish to install or upgrade signed Fedora packages."

The Fedora Project released alpha code for Fedora 10, its next version, earlier this month.

On the Red Hat side, the company issued an OpenSSH update and guidance on how users can protect themselves.

The company said it was "highly confident" that the Red Hat Network, an internal system that makes updates and patches available to its customers, was not compromised by the hacker.

The company, however, said it was issuing its alert for those who "may obtain Red Hat binary packages via channels other than those of official Red Hat subscribers."

Frields also made it clear that the affects of the intrusions on Fedora and Red Hat were not the same and that Fedora packages are signed with keys different from those used to sign Red Hat Enterprise Linux packages.

---

### Post by billgoldberg on 2008-08-25
> **Sporkman said:**
> [http://www.pcworld.com/businesscenter/article/150212/hackers_crack_into_red_hat.html](http://www.pcworld.com/businesscenter/article/150212/hackers_crack_into_red_hat.html)

That happens.

If memory serves me well, I believe the Ubuntu repository servers were hacked a year or so ago.

---

### Post by mips on 2008-08-25
So what? Nothing is 100% secure, the instances on linux are less than windows and openbsd probably beats them all.

---

### Post by aaaantoine on 2008-08-25
> **billgoldberg said:**
> That happens.

If memory serves me well, I believe the Ubuntu repository servers were hacked a year or so ago.

I remember Canonical changing their policies relating to LOCO servers.  Was that related in any way?

---

### Post by Nostrafus on 2008-08-25
Yeah, 1 hack is not so bad... as opposed to the Department of Defense where in 1995, I believe when they were still running on Windows based network, received 250,000 hacks, more than a few successful, and less than 3% traced...

---

### Post by yabbadabbadont on 2008-08-25
> **billgoldberg said:**
> That happens.

If memory serves me well, I believe the Ubuntu repository servers were hacked a year or so ago.

And the Debian ones not too much longer before that.

---

### Post by Dremora on 2008-08-25
> **Nostrafus said:**
> Yeah, 1 hack is not so bad... as opposed to the Department of Defense where in 1995, I believe when they were still running on Windows based network, received 250,000 hacks, more than a few successful, and less than 3% traced...

If the DoD gets hacked and the hacker makes off with any information of importance, it was probably planted there intentionally in order to trick the enemy.

In this case, you wouldn't want them to get it too easily, but you would want to leave maybe one or two ways in in such a way as to appear to be an honest mistake.

If something is really top secret, it will be heavily encrypted and certainly not on a machine that's connected to the internet, I also really doubt the US government uses Windows on anything other than relatively benign systems.

---

### Post by Dremora on 2008-08-25
I should also add that I would NEVER use Debian or Ubuntu on a server.

Red Hat, Fedora, and CentOS are much easier to secure.

---

