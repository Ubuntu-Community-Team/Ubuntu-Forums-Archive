---
title: "Unsafe machine - What can happen?"
date: 2008-11-16
forum: Security
---

### Post by jakupl on 2008-11-16
I am generally very paranoid when it comes to computers, I use Truecrypt for everything and 64 character random passwords for the most sensitive stuff. One day a friend of mine asked me: "why all this effort? what can happen? Even if a cracker gets to your computer, he will in the worst case delete my stuff (witch is no big deal, I would just reinstall.)", and it made me think about it.

I don't do online banking, I do have my passwords written in GPass on the computer, but for what... like Myspace, email and ubuntuforums, would it matter if someone got control of my e-mail, I would just get a new one right?

In short, what is the worst a cracker can do to my computer if he gets through, or if malicious code is executed?

---

### Post by Kinstonian on 2008-11-16
Well information security is about protecting the confidentiality, integrity, and availability information.  If your information isn't valuable to you and you don't care if you get hacked, then I guess you have a point.  But from you using TrueCrypt with long passphrases, it seems like you do have important data that you should protect.

However, if you don't want to maintain a secure computer for yourself, please be a good "netizen" and do it for other people.  Most of the time when someone gains unauthorized access to a computer it is used as a launching point to commit other crimes.  For example what if your computer was compromised and used for anything from storing and distributing contraband to running a phishing site to steal identities.  Not to mention if you're on a LAN it's very likely that if your computer is compromised it will be used to attack other computers on the network who are owned by people who do care about security, and you know personally.

---

### Post by lisati on 2008-11-16
The term "Computer Security" means different things to different people, and generally relates to either controlling access to your computer resources (who gets to see or use which part of your system), or protecting your computer resources against loss or damage (accidents happen)

I'm no expert on computer security, but can suggest a few basic precautions:
[LIST=1]
[*]Limit who has physical access to your gear
[*]Make backups and store them separately
[*]Limit who has electronic access to your machine (e.g. firewall, encrypted access to Wifi, limit by MAC address)
[/LIST]

---

### Post by sirjoebob on 2008-11-16
If someone gets into your machine, they could do illegal activities and it may be difficult to prove it was not you. Say they grab some child porn and the feds break down your door, burden of proof would be YOURS to show it was not you who accessed it which may be difficult or impossible if the attacker is good enough. 

You have more to lose than files, IMO. Plus think of what could happen if email is compromised. Mail your boss "F you I quit.." :lolflag:

---

### Post by randy78 on 2008-11-16
I would add that you should keep all of your software updated with the latest patches and versions.

That SMB bug that Microsoft just patched a couple of days ago was over 7 years old, and while it's impossible to guess at the number of PCs that were compromised due to that gaping flaw, it had been included in the Metasploit framework since 2007... so more than a few people knew about it.

Most compromised machines start new lives as soldiers in a bot army, used to perform large-scale distributed denial of service attacks.
Other times, attackers will install several pieces of Malware and sniff the logins for all of your online accounts, if for nothing more than to ruin your online reputation.

Stay vigilant, and even if you don't use your machine to do banking or any sensitive activities, it could still be used against you by a malicious attacker with a grudge against humanity.

---

### Post by bodhi.zazen on 2008-11-16
The other thing I would mention is that crackers can use your computer. They can install servers or even use your computer against others, for example see the "bot nets".

---

### Post by mflint on 2008-11-19
Yes... most of the time, speculative hacks are random in nature. Sorry to disappoint you, but usually *you* are not the target.

It's usually more to do with the *bandwidth* you have access to, for the purposes of mounting other attacks.

Example: my /var/log/auth.log reports that a machine at "92.50.193.94" tried (several times) to gain ssh access to my box. I'd guess that "92.50.193.94" is a compromised box, and its owner has no idea. It certainly won't be a machine belonging to the attacker.

---

### Post by scorp123 on 2008-11-20
> **jakupl said:**
> I am generally very paranoid when it comes to computers And so? I see absolutely nothing wrong with that. 8-)

---

### Post by scorp123 on 2008-11-20
> **mflint said:**
> I'd guess that "92.50.193.94" is a compromised box, and its owner has no idea. It certainly won't be a machine belonging to the attacker. Exactly! That's what they do in "Distributed Denial of Service" (DDOS) attacks ... they take over several machines and then attack the same target from different IP ranges ... 

@OP ... Imagine someone took over your machine and then mercilessly attacked a government target or e.g. a recording label? (basically someone who has an army of lawyers or even something like "Homeland Security" at their disposal and will _DEFINITELY_ hit back if you hit them!) .... Who do you think would get into trouble? .... You! Because it was your IP address. And your excuse "Ahemm ... a hacker took over my machine, wasn't me!!" most likely won't fly ...

You say you're "paranoid when it comes to computers". Make sure you stay that way ;)  Paranoia can proactively save you a ton of hassles.

---

