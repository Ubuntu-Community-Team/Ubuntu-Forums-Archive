---
title: "RHEL vs Ubuntu Server"
date: 2007-06-28
forum: Server Platforms
---

### Post by natetrumpet on 2007-06-28
This isn't a support question, so I hope it's in an OK place.  But here's the deal.  I just started a new job as the director of technology services at a small company.  While small, we have and maintain 8 collocated servers with future additions planned. We currently use Red Hat Enterprise Linux as our OS.  I just found out today that it's going to cost at least $350/server/year.  With 8 servers that's a ridiculous amount of money for support we never use and to get up to date packages.  All my previous admin experience has been with Debian and more recently Ubuntu.  

So this is where I need your help.  I want to switch to ubuntu to get the stability of debian and the community support of ubuntu, but that's not enough to convince the boss to switch.  Besides ubuntu having thousands more packages than Red Hat and not charging for up to date packages, what other things could convince a small business owner to switch?  I threw out the fact that we'd save thousands of dollars a year for support we don't use and that if I can't fix something in the promised two day turn around that Red Hat has for support tickets, that I should be fired.  What else might help?  I don't want to be stuck administering Red Hat and dealing with subscription renewals and sales people just to add a new server to our "Red Hat Network" account.  You shouldn't have to pay to get up to date stable server packages, as Ubuntu has demonstrated.

Thanks!

Edit:  Any articles or editorials would be extremely helpful too.  I googled but didn't find a lot of comparisons on the server-side of things, just mostly Fedora vs. Ubuntu.

---

### Post by PilotJLR on 2007-06-28
Ubuntu server is awesome... BUT there are very few hardware compatibility lists (as of now) that you will see it on.
$350 per server is pretty cheap (do you have basic only support??), but you get all the warm fuzzies with having a company to push hardware vendors and support items.

Although the forums are great, it's not a substitute for paid support. This is why Canonical sells support for both server and desktop products.

My advice: stick with RHEL and keep paying the subscription. You truly are betting your job on it... and NO ONE can fix everything. Sometimes, you gotta have a support center to call.

Or... switch to Ubuntu and BUY support from Canonical.  :-)

---

### Post by sgla1 on 2007-06-28
You might want to consider the cost of downtime on your servers.  If they go down, would it impede the company's ability to conduct business and make money?

Imho, Ubuntu doesn't QA their packages carefully enough to be an enterprise-grade server o/s.  For example, a recent upgrade to samba on 6.06 (and that's the 'server' version) borked the start-up scripts, costing me several hours of digging around for the problem.

RedHat is pretty careful and conservative with RHEL.  If they do bork something, the service contract allows you to get help quickly.  If you're dead set against RHEL, at least stick with Debian.

Cheers

---

### Post by dj 2501 on 2007-06-28
why not go with centos? its enterprise class and is the exact same thing as RHEL but no need to buy support to use it.

---

### Post by Bachstelze on 2007-06-28
RHEL is ridiculously overpriced. Go with a BSD :) If you really need a Linux, I'd recommend Slackware for servers.

---

### Post by joe.turion64x2 on 2007-06-28
You may want to keep your RHEL, it is not just some bucks, it is your job and the security & reliability it provides (plus the support). Are you aware RHEL is the only Linux that has reached the level of security Solaris provides?
[http://www.internetnews.com/dev-news/article.php/3683701](http://www.internetnews.com/dev-news/article.php/3683701)

---

### Post by Bachstelze on 2007-06-28
[http://en.wikipedia.org/wiki/Evaluation_Assurance_Level](http://en.wikipedia.org/wiki/Evaluation_Assurance_Level)

You must check your sources more carefully, even Win 2000 Server is evaluated at this level. Personnally, I just wouldn't trust any Linux for security-critical systems, and go with OpenBSD.

---

### Post by joe.turion64x2 on 2007-06-28
> **HymnToLife said:**
> [http://en.wikipedia.org/wiki/Evaluation_Assurance_Level](http://en.wikipedia.org/wiki/Evaluation_Assurance_Level)

You must check your sources more carefully, even Win 2000 Server is evaluated at this level. Personnally, I just wouldn't trust any Linux for security-critical systems, and go with OpenBSD.
Considering Ubuntu has not reached that level it would be sort of a risky downgrade. Absolutely agree about OpenBSD being a better option that either RH and Ubuntu. (That is the one with only one security risk in its whole history, isn't it?)

---

### Post by Bachstelze on 2007-06-28
> **joe.turion64x2 said:**
> Absolutely agree about OpenBSD being a better option that either RH and Ubuntu. (That is the one with only one security risk in its whole history, isn't it?)

Two, actually ;)

---

### Post by PilotJLR on 2007-06-28
> **HymnToLife said:**
> [http://en.wikipedia.org/wiki/Evaluation_Assurance_Level](http://en.wikipedia.org/wiki/Evaluation_Assurance_Level)

You must check your sources more carefully, even Win 2000 Server is evaluated at this level. Personnally, I just wouldn't trust any Linux for security-critical systems, and go with OpenBSD.

This is not entirely true... there are multiple types of EAL4 certification.

Windows 2003 (with NO services like IIS running) is EAL4 CAPP.

RHEL5 is EAL4 CAPP, RBAC, and LSPP.

The only other OS I'm aware of that has this level of certification is Trusted Solaris (not vanilla Solaris). This basically means RHEL5 can do the same things as Trusted Solaris... such as control our nuclear weapons (seriously).

---

### Post by chris.zeman on 2007-06-28
I love Ubuntu and use it for my servers. That said...

Is the only reason you want to switch from RHEL is because of the money? You're subscribing to their support services. I wouldn't switch to anything else unless you feel confident enough to handle all support and downtime issues yourself. I'm not saying that trying to save money is a bad thing, but don't ever get to the point where you're acting like it's coming out of YOUR pocket. Expenses are part of doing business. I've seen everything from months of downtime to nearly fatal incidents happen because of management trying to save a few bucks. You won't see any industrial accidents occur from using Ubuntu over RHEL, but I think it illustrates what I'm trying to say.

Chris

---

### Post by darkog on 2007-06-28
> **natetrumpet said:**
> ... it's going to cost at least $350/server/year.  With 8 servers that's a ridiculous amount of money for support .....

Support from Canonical.
> 
Desktop support 	$250 (USD)* 	 $900 (USD)*
Server support 	$750 (USD)* 	$2750 (USD)*
Thin client and cluster support 	$1200 (USD)* 	$4000 (USD)*


The Ubuntu community and Google is great and all -- but is doesn't beat having the real paid support.

> an increase of 42 percent from the year ago quarter and up 7 percent from the prior quarter, Red Hat is back to kicking rump and taking names in business Linux. taken from [here]("http://www.eweek.com/article2/0,1895,2151918,00.asp").

Despite all the new Linux interest and activity -- you still won't get fired for buying red*.

[i]* note: this is a variant on the old saying of, "No one ever got fired for buying blue", back when IBM where king. And then was changed to, "No one ever got fired for buying Microsoft", back when Microsoft where king. [\i]

---

