---
title: "UBUNTU Security Model - Risk Management"
date: 2007-08-27
forum: The Cafe
---

### Post by sncsafenet on 2007-08-27
If you are considering UBUNTU in an environment (like a BANK) that requires Internal Audit and Regulator examinations, you might want to consider how it should be implemented in your specific environment. This is not a complaint about the UBUNTU security model, but good questions for regulated businesses. Check out 

[http://sncsafenet.blogspot.com/2007/08/ubuntu-security-problem-or-solution.html](http://sncsafenet.blogspot.com/2007/08/ubuntu-security-problem-or-solution.html)   

for more details about making an informed decision. We would be interested in correspondence about how your organization might have handled these questions/issues.   Thank you

---

### Post by LaRoza on 2007-08-27
The article doesn't mention "sudo", which is used more than "su".

The article doesn't acknowledge that the root account is disabled by default in Ubuntu.

> 
Normal user access presents a risk to root access in the long run as the compromised user password can be used later for root access. This means an ordinary user account can be used with no need to do a root function and compromised on Thursday and the hacker can wait and use that same password the next Tuesday and then ascend to root.


Always remember that using the access of a normal user to climb the trust ladder and become a privileged user has long been a hacker tactic, and an effective tactic at that!


Using multiple trustees of root responsibility renders root access only as strong as the weakest of the normal user account passwords.
Not everyone is a sudoer, the root password is not the user password.

Social engineering is not a computer or OS security flaw, it is human.

A "normal" account cannot run things as root, even if they know the password.

---

### Post by PrimoTurbo on 2007-08-27
> **LaRoza said:**
> The article doesn't mention "sudo", which is used more than "su".

The article doesn't acknowledge that the root account is disabled by default in Ubuntu.


Not everyone is a sudoer, the root password is not the user password.

Social engineering is not a computer or OS security flaw, it is human.

A "normal" account cannot run things as root, even if they know the password.

It would be safe to assume that just about everyone uses sudo, because it's such an essential part of Ubuntu's design.

Also I think having too much security completely destroys the user experince. You are unable to do anything effectively, entering your password for every task is also dangerous especially in public.

---

### Post by LaRoza on 2007-08-27
> **PrimoTurbo said:**
> It would be safe to assume that just about everyone uses sudo, because it's such an essential part of Ubuntu's design.

Also I think having too much security completely destroys the user experince. You are unable to do anything effectively, entering your password for every task is also dangerous especially in public.

My comments are specific to the article, which critizes the Ubuntu security, but doesn't seem to be familiar with it.

---

### Post by az on 2007-08-27
I think it's a pretty naive article, really.  As mentioned, it seems unaware of the subject matter.

There is so much more to security than just how you handle password policies.  The article does not really cover privilege escalation in depth.  And BTW, lots of Unix systems use sudo, Mac OS being one that comes to mind.

And if you want to just focus on that one aspect, there is much much more to sudo than simply becoming root.  You can manage very fine-grained privilege escalation using sudo, something you cannot do wtih a root account.

It reads more like a high-school project than a whitepaper.

Sorry.


EDIT:
"When you have identified a risk, there are only three things you can do to that risk: avoid, assign, or accept.

You avoid a risk by placing a control to cancel or eliminate the risk. A firewall or antivirus program is intended to avoid risk by eliminating certain threats.

You assign a risk by placing a resource under the control and responsibility of another. This is what happens when we purchase insurance (e.g. business interruption insurance) or when we outsource, such as purchasing email service from a vendor."

Actually, scanning for viruses and running an applications-based firewall is *Assigning* the risk, not *Avoiding* it.  To Avoid it, you should run software that is not vulnerable to viruses or spyware.  How can you talk about IT security and ignore that point?

---

### Post by LaRoza on 2007-08-27
> **az said:**
> I think it's a pretty naive article, really.

It reads more like a high-school project than whitepaper.

Sorry.

My opinion also, the OP has the same name as the site, and that was the first post.

---

### Post by dca on 2007-08-27
He should've done a whitepaper on how to get Ubuntu into the US enterprises let alone security risks of running it at bank...

---

### Post by koenn on 2007-08-27
a bunch of generalities about security (" security does not exist in a vacuum") and risk management (" If we chose to do nothing, or if we aren’t aware of threats that pose risk, we are accepting that risk knowingly or otherwise.")

Then, the author reduces security to password policy, and goes on to compare the Ubuntu 'sudo' approach against the classic unix 'su" approach. Nothing new there. 

Conclusion : not worth the paper it's written on, and only absolute beginners might find it interesting. But then, they could just read  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and be better off.

---

### Post by TheCoffeePerson on 2007-08-27
I want to find out which bank is considering Ubuntu.

---

### Post by macogw on 2007-08-27
> **PrimoTurbo said:**
> It would be safe to assume that just about everyone uses sudo, because it's such an essential part of Ubuntu's design.

Also I think having too much security completely destroys the user experince. You are unable to do anything effectively, entering your password for every task is also dangerous especially in public.

Only the first user.  When adding other users, you can set "admin" (sudo) "desktop user" (no sudo) or "unpriveleged" (no thumb drives or cd drives or anything for a virus to get in)

---

### Post by sncsafenet on 2007-08-28
Good comments, everyone. I appreciate your opinions. Let me, however, clarify, that the article is not intended to offer 'command-level' advice, but advise for decision makers, particularly in organizations (like banks) where security is audited and examined by government agencies, etc.

Those users are a totally different population from you and I. Also, the article is not meant to criticize UBUNTU, merely invite an informed decision. Hopefully a system administrator in a bank will be better able to inform his/her upper management about why they should or should not deploy UBUNTU.

Again, thank you all for your discussion.

---

### Post by dca on 2007-08-28
Then I'm missing something, then.  Granted most of the hardware I play support for run RedHat, that aside, then the whitepaper should've been the pros & cons of running a su model versus sudo?  It's inconsequential really, I would rather read a whitepaper on, say, running CentOS versus RHEL in a data center.  You know, the benefits of hiring in-house Linux admins that can hopefully do the same thing RH wants w/o the $2500USD per server to do it...

---

### Post by sncsafenet on 2007-08-28
Hi DCA,
Most of my consulting clients are banks. Small to large, almost every bank eventually ends up with a Linux platform for some application or the other. All banks are subject to Examiners' and Internal Auditors' testing and these tests, while often technically limited, are 'politically' powerful (Yes, sometimes banks are virtually shut down by authorities). 

The entire aim of the article is not for the sys admin's decision, but the manager that might eveluate the sys admin's recommendation for this or that platform. Equiping the sys admin with the management perspective can help their recommendation be approved. 

It is a sad fact that most decisions are made by folks that can not understand the difference between "su" and "su -" or other technical elements of an operating system. It is equally true that many sys admins do not fully appreciate what the bank examiner or internal auditor are doing for (or TO) the organization.

---

### Post by az on 2007-08-28
Unfortunately, regardless for whom the article was written it completely misses the point.  It is a completely irrelevant text.  

> **sncsafenet said:**
> Hi DCA,
Most of my consulting clients are banks. Small to large, almost every bank eventually ends up with a Linux platform for some application or the other. All banks are subject to Examiners' and Internal Auditors' testing and these tests, while often technically limited, are 'politically' powerful (Yes, sometimes banks are virtually shut down by authorities). 

The entire aim of the article is not for the sys admin's decision, but the manager that might eveluate the sys admin's recommendation for this or that platform. Equiping the sys admin with the management perspective can help their recommendation be approved. 

It is a sad fact that most decisions are made by folks that can not understand the difference between "su" and "su -" or other technical elements of an operating system. It is equally true that many sys admins do not fully appreciate what the bank examiner or internal auditor are doing for (or TO) the organization.

That doesn't mean that your text shouldn't actually cover the topic.

Look, the article doesn't really touch on security.  It's a discussion about what password to type in and it makes some vague statements (like you need to set a root password), but it has no meaning and no relevance.

Security is a vast topic.  There are so many facets to it that a manager should not even have to think about sudo versus root versus su to make a decision about what platform offers the best security.  

Again, sorry.

---

### Post by aysiu on 2007-08-28
> **PrimoTurbo said:**
> It would be safe to assume that just about everyone uses sudo, because it's such an essential part of Ubuntu's design. For a single-member home user, yes.

For multi-member family homes or for businesses, no.

If four people in a family shared one Ubuntu computer, it would make sense for the first user (the most knowledgeable Ubuntu user) to have *sudo* access and then give the other three family members regular (non-*sudo*) accounts.

Likewise, in a business (like a bank), you wouldn't give *sudo* access to any of the employees except maybe a few people in tech support. And even then, *sudo* can be divvied up by task. It doesn't have to be an all-encompassing root or not-root situation. That's the beauty of *sudo*. If you give someone root access, she has access to everything until you change the root password. *sudo* allows you the possibility of allowing someone root access for only certain tasks.

By the way, the real article is here:
[http://www.sncsafenet.com/SNC_whitepaper_Aug07.htm](http://www.sncsafenet.com/SNC_whitepaper_Aug07.htm)

I don't know why the OP linked to a blog post that then links to an article. Just link directly to the article next time.

---

### Post by dca on 2007-08-28
> **sncsafenet said:**
> Hi DCA,
Most of my consulting clients are banks. Small to large, almost every bank eventually ends up with a Linux platform for some application or the other. All banks are subject to Examiners' and Internal Auditors' testing and these tests, while often technically limited, are 'politically' powerful (Yes, sometimes banks are virtually shut down by authorities). 

The entire aim of the article is not for the sys admin's decision, but the manager that might eveluate the sys admin's recommendation for this or that platform. Equiping the sys admin with the management perspective can help their recommendation be approved. 

It is a sad fact that most decisions are made by folks that can not understand the difference between "su" and "su -" or other technical elements of an operating system. It is equally true that many sys admins do not fully appreciate what the bank examiner or internal auditor are doing for (or TO) the organization.

ah, in that case:
 
install Ubuntu at Bank Of America instead of Sun Solaris and make sure they deactivate sudo?
 
Although banks or financial institutions are heavily scrutinized and audited by the government they are still for all intents and purposes a non-tech related industry a'la hospitals, government, retail, etc.  Tech-related would be like chip makers, PC manufacturers, telecoms, etc who rarely need consultant work done unless it's on some billing system or application related.  On the non-tech side of industry I've seen most decisions made on the TCO factor.   Security is relative, it starts as low as making sure each user at any location has a 5min timer for a screen-saver and set to ask for p/w on resume all the way to finding out what kind of information is leaving the facility on a company-authorized laptop and up to actual we'll say security of the infrastructure...  Security also sidelines into redundancy of systems.  
 
If any industry wants to use a Linux-based solution, I'm all for it.  In fact any solution that allows me to save money up front.  One of the greatest reasons I see Ubuntu gaining steam is the ability to d/l & install the same vers of Ubuntu that they support where as RH, you have to pay for support to get it or d/l & install CentOS...

---

### Post by koenn on 2007-08-28
> **sncsafenet said:**
> Let me, however, clarify, that the article is not intended to offer 'command-level' advice, but advise for decision makers, particularly in organizations (like banks) where security is audited and examined by government agencies, etc.

... 
 Hopefully a system administrator in a bank will be better able to inform his/her upper management about why they should or should not deploy UBUNTU.

Still, you reduce the whole security model to a su vs. sudo approach (and I still maintain that a sysadmin who wants to make an informed decision about it, or make up his mind on what to advise to management, is better of reading the RootSudo pahge I refered to).

And it's still a very, very weak article. i wouldn't even call it a whitepaper. 
I think in a real paper about Ubuntu' in terms of security and risk management, you might mention Ubuntu's release cycles / policy. Change managent has its place in risk management, so changes to the OS (either by patches/updates or by new releases) and migration paths are relevant. What does Ubuntu have to offer ? How does that compare with other Linuxes ? Unixes ? other OS'es ?

Software repositories. The software that will end up on your banks computer is taken from Ubuntu's software repositories. Who controls them. Who can upload to them ? what are the QA measures ? How is it secured ? Availability of its systems will matter to the bank's sysadmins and management, and is one of the 3 "CIA" pilars of information security, so reliabiliy of the software is something to look in to when you talk about the "security model" of an OS.

You make a rather weak point about privilegue escalation but completely overlook the point Aysiu made about the granularity that sudo provides in sysadmin tasks. For 1, it can be used to allow users limited admin tasks  - eg install updates such as security patches. Might be of interest for the sysadmins and management. Has downsides as well, so you could look in to possible trade-offs ...


lastly, you say you're primary target audience is corpoorations subject to Internal Audit and Regulator examinations, but the ONLY thing you say about it is "UBUNTU’s approach allows sufficient logging and support programs to satisfy an examination, though you will need to work to stay on top of things". Yeah right. What, in IT, does not need work to stay on top of things ? What sort of work ? How does Ubuntu makes these tasks easier  ? (or does it ?) nd Management is going to want to know about TCO. And how does that compare to other systems ? 

Maybe you don't have to touch all of these in depth (unless your whitepaper comes with a good Executive Summary), but to give at least an impression of knowing what you 're talking about, you'll have to do better than mentioning su dash and saying 'ubuntu has logs but you need to read them'.

---

### Post by saulgoode on 2007-08-29
> **sncsafenet said:**
> Good comments, everyone. I appreciate your opinions. Let me, however, clarify, that the article is not intended to offer 'command-level' advice, but advise for decision makers, particularly in organizations (like banks) where security is audited and examined by government agencies, etc.

Only a root account can assure that there is no tampering of audit information and no circumvention of security procedures.

A privileged account (i.e., a member of the 'admin' group) does not have complete control of the system; it only has the privileges authorized by the sudo utility. If a privileged account is ever compromised, or a pernicious employee is given access, then that account could be used to create a root account ("sudo passwd root"). Once a root account is created, it has the ability to control access to all logging of audit information and can hide its activities, even its existence, from members of the 'admin' group. It would not be possible to hide its activities from an operator logged into the same root account.

If you wish to have confidence in the integrity of your audit trail, it must be validated with the highest privileged access available on the system. On an Ubuntu system, a root account *is* available and its potential should not be neglected in an ultra-secure deployment.

---

