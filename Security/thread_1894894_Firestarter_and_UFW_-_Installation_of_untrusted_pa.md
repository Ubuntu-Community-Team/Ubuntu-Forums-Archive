---
title: "Firestarter and UFW - Installation of untrusted packages?"
date: 2011-12-13
forum: Security
---

### Post by Hadeda on 2011-12-13
I want to install software from the Ubuntu Software center in 10.04.3

Starting with Firestarter and "Firewall Configuration" (ufw) a warning pops up:

Quote
[INDENT]Requires Installation of untrusted packages.
The action would require the installation of packages from not authorized sources.
Details  "menu"
[/INDENT]Unquote

Being connected to Ubuntu (I hope) I accepted the installation, but nothing happened and there is no evidence of a download in the "installed software " list.

To make sure, I also tried the terminal:

quote
[INDENT]sudo apt-get install firestarter
WARNING: The following packages cannot be authenticated!
  menu firestarter
Install these packages without verification [y/N]?
[/INDENT]unquote

I spot checked other applications and they came up with the same authentication issue, even when choosing from "Get Software" - "Provided by Ubuntu"

What could be the cause - and remedy?

Many thanks

---

### Post by BigCityCat on 2011-12-13
This doesn't apply to your question but Firestarter is crap and shouldn't be used. It's way out of date. Install GUFW and follow the tutorial in the security section on how to use it. [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

---

### Post by DogMatix on 2011-12-13
> **BigCityCat said:**
> This doesn't apply to your question but Firestarter is crap and shouldn't be used. It's way out of date. Install GUFW and follow the tutorial in the security section on how to use it. [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

+1 I have ditched Firestarter for GUFW and won't be going back

---

### Post by haqking on 2011-12-13
Firestarter is an out of date and buggy project.

use UFW or its graphical front end GUFW

Regardless they all are just front ends for IPTables which you can do from CLI without any front end at all.

The simplest config for ufw is

```
sudo ufw default deny
```

```
sudo ufw enable
```

However this is minimal you will want to enforce tight outbound and inbound rules for your own configuration.

I suggest you read here [https://wiki.ubuntu.com/BasicSecurity#Firewall](https://wiki.ubuntu.com/BasicSecurity#Firewall) and follow the 2 links to help you configure your firewall.

Cheers

---

### Post by Hadeda on 2011-12-13
Thanks to all for the great feedback.
I now understand the issue regarding the outdated Firestarter.

The main issue at the time was that all downloads gave me the message about an untrusted package, Firestarter was simply one example.

Is it possible that I was diverted to some rogue site at the time?
I have now managed to install gufw without an warning but am concerned that accepting the 'untrusted package' yesterday could have installed rogue software?

Have run chkrootkit and it reverted with a line which I do not understand:

Quote
Checking `z2'...  user NAME1 deleted or never logged from lastlog!
user NAME2 deleted or never logged from lastlog!
user root deleted or never logged from lastlog!
Unquote

NAME1 and NAME2 are the 2 users on the system I know of.

What does this mean and should I run other tests?  - Many thanks!

---

### Post by BigCityCat on 2011-12-14
No that is not whats happening. You have to understand that the repos are filled with a lot of software that applies to older systems and severs. Things that really don't apply to your current distribution. If your trying to install outdated software your going to get some of those warnings because the software is untrusted because it's out of date and could pose a security risk as a result.

Be careful what your installing from the repos.

---

### Post by oldos2er on 2011-12-15
> **Hadeda said:**
> The main issue at the time was that all downloads gave me the message about an untrusted package, Firestarter was simply one example.

Sometimes the error can be cleared with a simple ```
sudo apt-get update
``` Or you could be missing a gpg key for one or more repositories.

---

### Post by Hadeda on 2011-12-22
Thank you all!

 The reason for my silence was that we had no Internet for a few days: Spoofed IP and router/FW flooding. 

It is not clear yet, but it is possible that the router was hijacked too. 

Is it it possible that above problems could have been a result of IP spoofing and the spoofer sent me trash?  

If not, where do I find the gpg keys oldos2er is referring to?

---

### Post by oldos2er on 2011-12-23
> **Hadeda said:**
> If not, where do I find the gpg keys oldos2er is referring to?

```
sudo apt-get update
``` will show you which repositories, if any, are missing their keys. If you need help finding them, just post back here.

---

### Post by Hadeda on 2012-01-11
It is increasingly highly likely that the problems were due to DNS spoofing and possibly due to dns backdoors such as this one

 [http://www.techrepublic.com/blog/networking/dns-changer-trojan-latest-variant-is-certainly-unique/774](http://www.techrepublic.com/blog/networking/dns-changer-trojan-latest-variant-is-certainly-unique/774)


Your suggestions are all great for non-compromised computers. I would like to add that if others have the same problems in future they should, after your suggestions do not bring results, focus on learning how to deal with DNS spoofing. I am still doing it myself so at this stage can't give advice :-(

---

### Post by haqking on 2012-01-12
> **Hadeda said:**
> **It is increasingly highly likely** that the problems were due to DNS spoofing and possibly due to dns backdoors such as this one

 (

Edit: reread the OP

---

