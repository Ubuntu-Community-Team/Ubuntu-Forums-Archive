---
title: "Anti-virus"
date: 2008-11-05
forum: Security
---

### Post by dtommy79 on 2008-11-05
Hi,

If I use ubuntu, do I need any antivirus or antispyware software like for windows?

Thanks

---

### Post by linkmaster03 on 2008-11-05
No, you don't. Viruses on Linux are very rare.

---

### Post by crazypenguin2008 on 2008-11-05
your protected by iptables

---

### Post by WRDN on 2008-11-05
Short Answer : No.

Longer Answer : You don't need antivirus/ other such software because, viruses rely on administrative access to damage a system. However, in Ubuntu, you do not have root access by default, so a virus would not damage the system. Also take into account there are very very few viruses (if any) in 'the wild' for Linux, and if you got a Windows virus, it would not run- though it could run in WINE, it is still extremely unlikely it would cause any problems.
The only possible reason I can see to have antivirus is to scan files before sending them to Windows users to ensure they are not affected. Also, if you have a Windows virus, it is good practice to get rid of it anyway, even though it won't harm your system.

---

### Post by Paqman on 2008-11-05
No, protection from viruses is a built-in feature of Linux. You don't need to install extra software to be protected. Just make sure you install all the latest security updates.

---

### Post by pi.boy.travis on 2008-11-05
Ubuntu is inherently more secure than Windows, so you shouldn't need antivirus.  However, I would recommend using the Firestarter package to set up a firewall.  Install it with Add/Remove software or Synapic

Hope this helps!

---

### Post by bodhi.zazen on 2008-11-05
Security on Linux is not the same as windows.

See these links :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by Paqman on 2008-11-05
> **pi.boy.travis said:**
> I would recommend using the Firestarter package to set up a firewall.

Firestarter is no longer being maintained. If you want a nice GUI for configuring iptables I recommend gufw.

---

### Post by hyper_ch on 2008-11-06
> **crazypenguin2008 said:**
> your protected by iptables
Not really...

> **pi.boy.travis said:**
> However, I would recommend using the Firestarter package to set up a firewall.
Firestarter is not really needed and neither is messing around with iptables at all.

---

### Post by persistentstubborn on 2008-11-06
> **hyper_ch said:**
> Not really...


Firestarter is not really needed and neither is messing around with iptables at all.

Huh?

I can't see how else to understand your advice but as misleading.

Although iptables/packet filtering isn't a single point of security, it's still an important piece of it, along with proper configuration of the entire OS, selection of software to be installed, logging and some additional measure of caution, such as privoxy.

---

### Post by bodhi.zazen on 2008-11-06
> **persistentstubborn said:**
> Huh?

I can't see how else to understand your advice but as misleading.

Although iptables/packet filtering isn't a single point of security, it's still an important piece of it, along with proper configuration of the entire OS, selection of software to be installed, logging and some additional measure of caution, such as privoxy.

The use of firewalls has at times been a hot topic on these forums.

When people claim a firewall is not needed they *usually* are saying that you should be using a router (which has a firewall built in) and they assume you are running a default desktop installation (in which case there are no open ports).

Then there is the other camp who feel a firewall is needed on all installations, desktop or otherwise.

I think uses need to understand how to secure severs / desktops and understand what a firewall will and will not do for you rather then perpetuate these endless vague arguments on the general merits of a firewall.

---

### Post by persistentstubborn on 2008-11-06
> **bodhi.zazen said:**
> ...

I think uses need to understand how to secure severs / desktops and understand what a firewall will and will not do for you rather then perpetuate these endless vague arguments on the general merits of a firewall.

Well said.

I didn't want to start a debate, than just to point to what seemed misleading to me.

I think Ubuntu community needs to pay more attention to improving documentation and howto's, such as your excellent & comprehensive howto above. It seems users aren't growing up in skills and these fora take the shape of answering the same trivial questions a number of times.

---

### Post by brian_p on 2008-11-06
> **bodhi.zazen said:**
> 

When people claim a firewall is not needed they *usually* are saying that you should be using a router (which has a firewall built in) . . . . 

Sometimes that is what they are saying but it is not a stance I would adopt.

>  . . . . . and they assume you are running a default desktop installation (in which case there are no open ports).

A firewall with a default installation is perverse. With a non-default installation there is a strong argument for it being superfluous in the vast majority of cases.  

> Then there is the other camp who feel a firewall is needed on all installations, desktop or otherwise.

Try arguing for not using a firewall in a Windows forum - you'll be assailed from all sides. Part of the problem is the concept of what a firewall is and a lack of appreciation of the control Linux gives you over the OS.

> I think uses need to understand how to secure severs / desktops and understand what a firewall will and will not do for you rather then perpetuate these endless vague arguments on the general merits of a firewall.

I'd not disagree with that.

---

### Post by brian_p on 2008-11-06
> **persistentstubborn said:**
> 

I didn't want to start a debate, . . . . .

Debate is good.

>  . . . . . than just to point to what seemed misleading to me.

A word or two on how firestarter and specific iptables rules increase security would bolster your claim and help dtommy79.

---

### Post by bodhi.zazen on 2008-11-06
> **brian_p said:**
> Debate is good.

Yes it is. We ask you keep it off the support threads though.

If you wish to debate the issue , please use the "Recurring discussions" section rather then the support sections. I think you will find more then enough debate here :

[Recurring Discussions](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by hyper_ch on 2008-11-06
the "not really" comment was directed at crazypenguin2008 comment, that you are protected by iptables.

This is not the case. by default, iptables lets pass everything and filters nothing and that is good. It is good because by default there is nothing running that needed to be tightened down.

---

### Post by persistentstubborn on 2008-11-07
> **hyper_ch said:**
> the "not really" comment was directed at crazypenguin2008 comment, that you are protected by iptables.

This is not the case. by default, iptables lets pass everything and filters nothing and that is good. It is good because by default there is nothing running that needed to be tightened down.

It was actually me misreading the true intent of your message. You are right, iptables won't protect anything unless rules are set.

Cheers.

---

### Post by Karilex on 2008-11-07
[http://ubuntuforums.org/showthread.php?t=968831](http://ubuntuforums.org/showthread.php?t=968831)

---

### Post by togo59 on 2008-11-07
Hi,

I hope you don't think this is a thread hi-jack because it genuinely isn't. I have been advised in [[COLOR="Blue"]this thread [/COLOR]]("http://ubuntuforums.org/showthread.php?t=972056")that I may have inadvertently loaded some malware. (The thread is actually about my difficulty upgrading to 8.10.)

My question to you is: If I do have malware, how can I detect it? (Which is more-or-less what the original poster of this thread asked.)

[If you have any advice related to my own particular issue, raised in the other thread, perhaps you could add it to that thread and then I won't have inadvertently forked this one.]

EDIT: Sorry, the info I need is at the bottom of [ [COLOR="Blue"]here [/COLOR] ]("http://ubuntuforums.org/showthread.php?t=510812"). I missed it the first time.

---

### Post by cariboo on 2008-11-07
It is always better to start a new thread, than asking a question in an existing thread, unless you are the OP.

Jim

---

