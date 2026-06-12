---
title: "Security is Process but how often"
date: 2011-03-16
forum: Security
---

### Post by wdtd on 2011-03-16
How often do you review/check your security procedures, your logs, etc.?

---

### Post by uRock on 2011-03-16
I check my Snort log once or twice a week and my router's logs daily.

---

### Post by bodhi.zazen on 2011-03-16
> **wdtd said:**
> How often do you review/check your security procedures, your logs, etc.?

Depends on the system.

On my Desktop, at the moment, I am using selinux (fedora 14) and I review selinux alerts when they occur.

On my netbook I am using gentoo-hardened with pax/grsecurity and as I am new to pax/grsecurity I review it quite often. Once it is configured I probably will not feel the need to monitor it all that much as it is a fairly hardened system with (outside of the lo interface) no listening services.

On Ubuntu same would be true, but I use apparmor with a profile for all network aware applications. I modify the profiles so that I minimize any "false alarms".

Server side, it depends on the server and if the server is public (ie apache, ssh) or private (a dhcp or samba/nfs server behind a hardware firewall).

---

### Post by bodhi.zazen on 2011-03-16
> **uRock said:**
> I check my Snort log once or twice a week and my router's logs daily.

That will certainly instill a healthy dose of paranoia.

---

### Post by uRock on 2011-03-16
> **bodhi.zazen said:**
> That will certainly instill a healthy dose of paranoia.

I only do it out of boredom.8) I like watching my router logs to see if anyone is trying to connect to it. I have had no violations listed in Snort nor my router logs. I have had some Snort alerts, but they came from a bad set of rules.

---

### Post by bodhi.zazen on 2011-03-16
> **uRock said:**
> I only do it out of boredom.8) I like watching my router logs to see if anyone is trying to connect to it. I have had no violations listed in Snort nor my router logs. I have had some Snort alerts, but they came from a bad set of rules.

Ah, sounds fairly typical for a home setup.

Try putting snort on the other side of your router =)

---

### Post by uRock on 2011-03-16
> **bodhi.zazen said:**
> Ah, sounds fairly typical for a home setup.

Try putting snort on the other side of your router =)

I have been debating it. Turn off file sharing, remove the router and connect to the modem and see how long it takes to catch a port scan. It'll be fun.:P

---

