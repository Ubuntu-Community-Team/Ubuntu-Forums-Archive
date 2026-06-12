---
title: "Is Ubuntu Secure &amp; Safe?"
date: 2009-07-24
forum: Security
---

### Post by adscnet on 2009-07-24
Hi All,

Security is something everyone thinks & dreams about it nowadays ... am I secure ... what should I install to protect my privacy? which anti-virus, which anti-spy ware, trojans ..? 
Which software is better than the other one ? God .. its total mess... 
This specially for people who access there bank accounts - credit cards and purchase online.

And my fears increased when I visited one of IT companies here & guise what they are selling .. a Flash Stick with some programs to breach any PC security ... you by this Flash Stick & give it to anyone for ex. to copy some files for you ... & as soon as he inserts the flash in his computer the programs inside the flash start working & gathering any password been typed or stored in that computer ... wireless keys, messengers ids & passwords, email accounts & passwords and more than that it installs a small remote control software, so the hacker can control that PC ... this Flash Stick been tested in many anti-virus & spy ware systems & was --- undetectable !!!! God how technology is scary .

All this leads me to think in another way another OS like Unix/Linux, I used Unix 15 years ago .. but at that time technology & security was really different .. I wish I continue using it.

So, now I am like a beginner :sad:

My question is, after a fresh installation of ubuntu side-by-side with Windows OS with infected PC (maybe), & after enabling "ufw" firewall does ubuntu still secure?
I have installed ubuntu on a portable HDD & can used it on any PC with preinstalled windows.. usually I access very sensitive data & bank accounts. 

What do you think ubuntu experts? ... thanks for the advise.

Any really apologize for this long message.
Regards.

---

### Post by XCan on 2009-07-24
From the Flash stick thingy it sounds like Windows autorun + administrator priviledges fails it again? Have you tried that stick on a *nix machine, I bet the trojan won't even run.

In what way are you asking if Ubuntu is secure? There are no Virii in the wild. Ubuntu would require a user action to get infected, i.e., installing a trojan authorized by the user. Your infected Windows partition won't affect Ubuntu, if you don't start to try and run infected programs there through Wine.

---

### Post by Kinstonian on 2009-07-24
Security is the continual process of mitigating risk to an acceptable level.  It's a journey, not an end.  It includes people, policies and products, so it's more than what OS or product you use.

The security of an operating system may start with the people who create it, but it ends with the people who use it.  You would be more secure using whatever modern OS you are more familiar with.  However, with that said, if you know both Windows and Linux equally, most people would agree that Linux is more secure.  Where they often disagree is why, so I won't get into that.

---

### Post by adscnet on 2009-07-24
> **XCan said:**
> From the Flash stick thingy it sounds like Windows autorun + administrator priviledges fails it again? Have you tried that stick on a *nix machine, I bet the trojan won't even run.

In what way are you asking if Ubuntu is secure? There are no Virii in the wild. Ubuntu would require a user action to get infected, i.e., installing a trojan authorized by the user. Your infected Windows partition won't affect Ubuntu, if you don't start to try and run infected programs there through Wine.

No I didn't use that stick on any *nix machine coz its not designed for *nix systems, even I didn't try it on any win machines .. & why should I go into this trouble ?!

My question is about .. installing ubuntu or Linux from the box, then running the system updates, enable the firewall is enough where I can say now my system is safe & can access any online banking or access xx data. On windows the process is different starting from installing the OS, system updates, anti-virus, anti-spam, installing firewall, test your system, then we can say now the system is ready to go ..

---

### Post by Kinstonian on 2009-07-24
While operating systems are much more secure by default than in the past, every OS could still benefit from further hardening.  For some tips on hardening Ubuntu check out:

1.  [Ubuntu Hardening Guide](http://www.matthewlye.com/index.php/ubuntu-sec)

2.  [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421)

After system hardening, and understanding the threats you face, then yes, I think the average Joe should feel safe against the average threats.  However, in the end, as you've probably heard-- no one can achieve 100% security.

---

### Post by Cheesemill on 2009-07-24
You don't usually even need a firewall on a desktop Ubuntu machine because there are no open ports by default.
Only when you start installing servers on your machine do you need to think about a firewall.

---

### Post by bodhi.zazen on 2009-07-24
> **adscnet said:**
> Hi All,

Security is something everyone thinks & dreams about it nowadays ... am I secure ... what should I install to protect my privacy? which anti-virus, which anti-spy ware, trojans ..? 
Which software is better than the other one ? God .. its total mess... 
This specially for people who access there bank accounts - credit cards and purchase online.

And my fears increased when I visited one of IT companies here & guise what they are selling .. a Flash Stick with some programs to breach any PC security ... you by this Flash Stick & give it to anyone for ex. to copy some files for you ... & as soon as he inserts the flash in his computer the programs inside the flash start working & gathering any password been typed or stored in that computer ... wireless keys, messengers ids & passwords, email accounts & passwords and more than that it installs a small remote control software, so the hacker can control that PC ... this Flash Stick been tested in many anti-virus & spy ware systems & was --- undetectable !!!! God how technology is scary .

All this leads me to think in another way another OS like Unix/Linux, I used Unix 15 years ago .. but at that time technology & security was really different .. I wish I continue using it.

So, now I am like a beginner :sad:

My question is, after a fresh installation of ubuntu side-by-side with Windows OS with infected PC (maybe), & after enabling "ufw" firewall does ubuntu still secure?
I have installed ubuntu on a portable HDD & can used it on any PC with preinstalled windows.. usually I access very sensitive data & bank accounts. 

What do you think ubuntu experts? ... thanks for the advise.

Any really apologize for this long message.
Regards.

In addition to the advice you have been given, physical security is also a problem. IMO removable devices should be mounted noexec.

But really, physical access = pwned

---

### Post by upapilot on 2009-07-26
Ubuntu is VERY safe as compared to Windows as hackers dont usually make malicious software for Linus OS......but you could make it even more safe by using firewalls or by creating your own security softwares (that's if you are smart enought of course ;)!

---

