---
title: "Want to change password to weak password"
date: 2010-01-13
forum: Security
---

### Post by rushinblue on 2010-01-13
How can I force passwd to use a simple password?

I want to change my passwd & delete passwd history (if stored)

I plan on creating a Virtual Appliance that uses another password besides my testing password.

---

### Post by Sarmacid on 2010-01-13
To assign a weak password to a user try this```
sudo passwd user
```You shouldn't be restricted now.

---

### Post by rushinblue on 2010-01-13
Awesome, I should have thought of that.

---

### Post by Raptor Ramjet on 2010-08-18
This should be *much simpler* to use.  It is no business of anyone other than myself how strong/weak a password I want to use.

If I want to use a password of "x" that's entirely my concern and it is not up to some random developer to try to force me to use what they consider a good password.

---

### Post by bodhi.zazen on 2010-08-18
> **Raptor Ramjet said:**
> This should be *much simpler* to use.  It is no business of anyone other than myself how strong/weak a password I want to use.

If I want to use a password of "x" that's entirely my concern and it is not up to some random developer to try to force me to use what they consider a good password.

While it is your business what you do with your computer, as soon as you connect to the internet it affects others.

As you disable security (weak passwords are a #1 contributing factor to cracking) affects many people when your are connected to "the internet".

Because of those reasons, IMO, it is reasonable to enforce strong passwords. The defaults on Ubuntu are a reasonable balance, certainly the system could be configured such that stronger passwords can be enforced.

---

### Post by anomie on 2010-08-18
[QUOTE=bodhi.zazen]While it is your business what you do with your computer, as soon as you connect to the internet it affects others.[/QUOTE]

+1 that. 

Like it or not, there are nasty people (scratch that -- nasty, enormous botnets) on the 'net that will exploit your decision, given the opportunity. 

Strong password enforcement protects everyone from you as much as it protects you from yourself.

---

### Post by shubes on 2012-06-07
> **Raptor Ramjet said:**
> This should be *much simpler* to use.  It is no business of anyone other than myself how strong/weak a password I want to use.

If I want to use a password of "x" that's entirely my concern and it is not up to some random developer to try to force me to use what they consider a good password.

+1
I don't want (or need) a fixed policy determined by anyone but myself. The policy should be able to be easily set by the system administrator. One size does not fit all situations.

Regarding affecting others by being connected to the internet, that's a naive viewpoint imo. While security needs to be taken into account (eg a firewall device that protects the LAN and WAN from each other), strong passwords are not always effective (nor desirable). For instance, a spambot could easily be running on a system with a perfectly strong password, still affecting others on the internet.

---

### Post by cariboo on 2012-06-08
> **shubes said:**
> +1
I don't want (or need) a fixed policy determined by anyone but myself. The policy should be able to be easily set by the system administrator. One size does not fit all situations.

Regarding affecting others by being connected to the internet, that's a naive viewpoint imo. While security needs to be taken into account (eg a firewall device that protects the LAN and WAN from each other), strong passwords are not always effective (nor desirable). For instance, a spambot could easily be running on a system with a perfectly strong password, still affecting others on the internet.

Can you show us some proof to backup your statement?

Ubuntu is designed for a specific audience, for the target user, the defaults are a reasonable mix of ease of use, and security, if you find the defaults to restrictive, Ubuntu may not be the best distribution for you.

---

