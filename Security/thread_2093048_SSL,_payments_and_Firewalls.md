---
title: "SSL, payments and Firewalls"
date: 2012-12-09
forum: Security
---

### Post by GeordieJedi on 2012-12-09
Hi all, I hope you're all well.

I have a little concern I'd like some help with please.

I have just bought an item from a website (Bloomingdales in the USA)
The site was using SSL.

However I have just realised that I hadn't ran my firewall at startup
(like I almost always do !)

So I'm a little worried. (I am very cautious when it comes to security).
(I understand that Ubuntu usually doesn't run many/any services
unless I set up them myself. Unlike Windows. And I haven't set anything
up myself - to my knowledge)

So what do you think ? Am I safe ?


Info =
KUbuntu 12.04
Chromeium = Version 20.0.1132.47


TIA for any help or advice.

---

### Post by Cheesehead on 2012-12-09
I do not see how website+SSL is related to your firewall (or lack of firewall). Firewall generally prevents intrusion, SSL generally prevents several forms of hoaxing.

Which are you concerned about? 
Could you please explain your concern in more detail?

---

### Post by sandyd on 2012-12-09
**Welcome to the Security Discussions Forum**

---

### Post by Ms. Daisy on 2012-12-11
You would benefit immensely by reading the basic security wiki.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by JKyleOKC on 2012-12-11
Sites that deal with financial matters use SSL to prevent your credit card details from going over the internet in clear text; your browser encrypts its transmissions using a key that the site provides. I've never heard of any malware coming back into a system through a "Secure Socket Layer" connection, although there have been many cases of it coming in via browser vulnerabilities that have nothing at all to do with SSL.

And in the Linux kernel, the firewall is always turned on during the boot process, before connection to any network occurs. What your "firewall program" that you start really does is to configure the firewall rules. If you've set up UFW or GUFW, you only need do the program one time and it will do its thing automatically forever after, until you change it. Finally, just about all existing malware is Windows-specific and does nothing on a non-Windows system, so you're probably safe.

However, security is a process rather than a program. It's like driving a car or flying a plane; you have to always be on the alert for possible problems. As others have said, read up on some of the links to find out more about how you can harden your system against it, and what to look for in everyday actions...

---

### Post by DuckHook on 2012-12-13
Hi Jim,

Not to contradict, but Ubuntu firewall is actually *off* by default. I know--I was surprised when I first learned this too. However, you are correct when you say that turning it on the first time will keep it on thereafter. Best tool for new users is GUFW, available from the repositories.

...and I have no idea why Ubuntu would have it off by default. If it screws up the install process, then in my opinion, they should at least have a pop-up on first run that asks if you want to activate it.

---

### Post by JKyleOKC on 2012-12-13
Actually, "netfilter" which is the actual code that implements the firewall rules is part of the kernel and has no on-off switch. That was what I had in mind when saying the firewall is always on.

However, the default setting for the three chains of netfilter is to accept everything and reject nothing. While I considered that to be a firewall, it's a wall with all its gates wide open and doesn't keep anything out, so we're both correct from different perspectives.

The reason for defaulting to wide-open condition is simple: even the server editions don't activate any servers by default, so nothing is listening on any port and thus even though netfilter doesn't reject anything, nothing gets accepted either and the would-be invader simply times out eventually with no harm done. Since no rules are needed or defined in this case, there's no need to make UFW/GUFW active. Doing so by default would create a batch of rules and user-defined chains that would simply use resources to achieve the same result.

Once you explicitly add servers to the system, opening ports to the outside world, you need rules added to netfilter to specify how to deal with packets that may pass through those ports in either direction. That's when netfilter needs to be given rules for what to accept, and what to refuse.

All of the "firewall" programs such as Firestarter, UFW, GUFW, and so on simply set up such rules for netfilter, and modify the boot processes appropriately so that the rules are loaded into the system before the network interfaces become active. You could create your set of rules manually via a text editor, save them in the appropriate format, and make sure they load at the proper time. 

In fact, that's what I've done here to come up with a much simpler set than those generated by UFW/GUFW. The starter programs have to account for every possible condition a user might have; my custom rule set needs only consider my own specific needs. However for most users, and especially those not intimately familiar with the security process, the starter programs are much to be preferred. There's much less chance of leaving a vulnerability gaping for the bad guys to pour through!

---

### Post by haqking on 2012-12-13
> **DuckHook said:**
> Hi Jim,

Not to contradict, but Ubuntu firewall is actually *off* by default. I know--I was surprised when I first learned this too. However, you are correct when you say that turning it on the first time will keep it on thereafter. Best tool for new users is GUFW, available from the repositories.

...and I have no idea why Ubuntu would have it off by default. If it screws up the install process, then in my opinion, they should at least have a pop-up on first run that asks if you want to activate it.

Because IPTables/Netfilter is part of the kernel and already there, UFW is merely an interface to the firewall as is GUFW and others.

EDIT: Ninja'd above

---

### Post by teward on 2012-12-13
> **DuckHook said:**
> Hi Jim,

Not to contradict, but Ubuntu firewall is actually *off* by default.

Actually, the firewall *program *(iptabes/netfilter) is loaded by default.  It is the lack of *rules by default* that gives the *impression* of the firewall program not running.  Activating full firewall blocking rules by default isn't actually security, because "default" rules won't cover all use cases, and sometimes will break unrelated things.  In organizations, you can see this as a continually apparent issue for Security if they all use a default ruleset that's not tailored for individual use-case.

From what I understand, the requirements for each system in terms of port restriction, packet restriction, filtering, and other things the firewall maintains are different from system-to-system, and from deployment-to-deployment, such that, for Organization A, the ruleset for System A may differ from that of System B, while within Organization B, all systems use the same rulesets.  Which is why one set of "default" rules isn't exactly good practice.

As JKyleOKC said, Security is a process, not a program.  It is up to the end-user, or system administrators within an organization, to set up and establish what rulesets and security protections are necessary.  For individual server administrators, they should at least understand basic security to the point they know to check to see if a firewall is configured *as well as *installed.

And as haqking said, UFW is merely a frontend interface to the firewall - it in itself without the iptables/netfilter backends is nothing.

(yes, I may have been ninja'd while writing this, but... nevertheless, i actually incorportated haqking's statements in here :P)

---

### Post by teward on 2012-12-13
[COLOR=Gray]*Yes, this here is another post, don't go slapping me, the previous post was a small rant on why default rules are bad.*[/COLOR]

I've also made the mistake of not running my firewall (new installation) when making SSL-secured payments, your firewall is not required for SSL-secured payments to be fully secured.  Although not running a firewall long-term can cause issues ;)

---

### Post by JKyleOKC on 2012-12-13
Matter of fact, I get my email through a WinXP virtual machine that has no firewall at all active -- but that machine's traffic to the outside world passes through my customized iptables/netfilter setup on this actual machine, which in turn is behind a router that features SPI filtering itself, so I have a couple of layers of defense before getting to the XP system...

SSL makes use of "certificates" that are supposed to prove that the other end of the connection is exactly who it claims to be, and encrypts all the data to assure security. By far the biggest risks in the scenario of this thread are the possibility of phishing traffic and social engineering!

---

### Post by DuckHook on 2012-12-13
:redface:Thanks to all for avalanche of info. Ya learn something new every day.:biggrin:

---

