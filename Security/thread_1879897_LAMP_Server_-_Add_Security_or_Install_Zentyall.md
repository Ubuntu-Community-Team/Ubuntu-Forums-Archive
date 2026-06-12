---
title: "LAMP Server - Add Security or Install Zentyall?"
date: 2011-11-12
forum: Security
---

### Post by fullmoonguru on 2011-11-12
I have a small business/home data & LAMP server using Ubuntu 11.04.  We also have 3 'buntu  & 1 Windows box on the network, behind a D-Ling DIR-655 router & a network switch.  I have Remastersys backups of all machines & all the data is backed up continuously online with Crashplan.  We have a couple of web apps that I'd like to have semi-regular remote access to.  Right now there are just two of us, but I could foresee a need for up to 6 or so people needing outside access.  I'm leaving our website, for public consumption, on our web host providers server, and plan on staying with that approach.

Reading the security stickies makes it sound like a miracle that I haven't been attacked over the years.  I don't know if I'm just lucky, or if things really aren't as dangerous as they sound.  Until a couple of years ago we had a Windows network with regular updates, anti-virus, and anti-malware running and the only problem I ever had was a worm that got in through IE.

Anyway, reading the stickies kind of makes it sound like I'm about to venture down another Linux rabbit hole that's going to lead to all kinds of unexpected problems and eat entire weekends in front of the server, to the continuing frustration of my wife.

Do I really need the triple-layer, multi-configuration, complicated system that I'm reading about for this purpose?  Is it really not as complicated as it sounds (for a reasonably competent Linux admin)?  Should I just run something like Zentyal instead, with it's packaged security features?

---

### Post by Dangertux on 2011-11-12
> **fullmoonguru said:**
> I have a small business/home data & LAMP server using Ubuntu 11.04.  We also have 3 'buntu  & 1 Windows box on the network, behind a D-Ling DIR-655 router & a network switch.  I have Remastersys backups of all machines & all the data is backed up continuously online with Crashplan.  We have a couple of web apps that I'd like to have semi-regular remote access to.  Right now there are just two of us, but I could foresee a need for up to 6 or so people needing outside access.  I'm leaving our website, for public consumption, on our web host providers server, and plan on staying with that approach.

Reading the security stickies makes it sound like a miracle that I haven't been attacked over the years.  I don't know if I'm just lucky, or if things really aren't as dangerous as they sound.  Until a couple of years ago we had a Windows network with regular updates, anti-virus, and anti-malware running and the only problem I ever had was a worm that got in through IE.

Anyway, reading the stickies kind of makes it sound like I'm about to venture down another Linux rabbit hole that's going to lead to all kinds of unexpected problems and eat entire weekends in front of the server, to the continuing frustration of my wife.

Do I really need the triple-layer, multi-configuration, complicated system that I'm reading about for this purpose?  Is it really not as complicated as it sounds (for a reasonably competent Linux admin)?  Should I just run something like Zentyal instead, with it's packaged security features?

Honestly for what you're doing it shouldn't take more than 5-6 hours to secure it. 

Border router config (not much you can do with that router)

Server config : iptables config, rate limiting etc , apparmor on missions critical apps. mod-security for your web apps (10 minutes and maybe an additional 2-3 hours if your web apps are custom and popping 501's in apache)

Workstations : firewall (you can use one script for all of them likely), apparmor for browsers, noscript for browsers.

Windows : the standard slew of apps and keep it updated. 

So no I don't think it would really be that bad. Zentyal might eat up more time, since there are probably a bunch of goodies to configure on that.

---

