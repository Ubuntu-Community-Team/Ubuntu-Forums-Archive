---
title: "Virtual Box and viruses/firewalls"
date: 2007-11-08
forum: Virtualisation
---

### Post by tchoklat on 2007-11-08
This is my issue. We all know that Windoze is prone to viruses and a firewall is required to deter hackers. We all rejoice that Linux is not.

I have A linux Box with XP as a guest. Do I need virus checkers and firewalls etc on it?

Also my dad has an XP box with Gutsy as a guest. Is accessing the internet from Gutsy virus/hacker free or is it prone as it is a Windoze box?

thoughts ...

---

### Post by gb64 on 2007-11-08
When within a regular VM,  especially Xp, do install a good firewall and anti-virus program, unless you do what I mention further below. You can download a free version of ZoneAlarm and a free version of Avast anti-virus. Install within the VM and keep them up-to-date.

Read page 33 of the latest Virtualbox user guide about snapshots. You can use that to discard changes.

And/Or, you can download the free personal version of Returnil and set it so all changes are discarded on shutdown.
[http://www.returnilvirtualsystem.com/](http://www.returnilvirtualsystem.com/)

---

### Post by tchoklat on 2007-11-08
thanks, I will read up on Returnil and see if that is what I need.

In an XP box with a Gutsy guest, is the PC at risk when accessing the internet with Gutsy as a normal XP installation is?

---

### Post by gb64 on 2007-11-08
> In an XP box with a Gutsy guest, is the PC at risk 

Any XP host exposed to a network would be at risk. Use a firewall and anti-virus on a XP host, even if you have a hardware router with built-in NAT firewall (Do not depend on XP Windows firewall ).

---

### Post by Kymus on 2007-11-08
> **gb64 said:**
> When within a regular VM,  especially Xp, do install a good firewall and anti-virus program, unless you do what I mention further below. You can download a free version of ZoneAlarm and a free version of Avast anti-virus. Install within the VM and keep them up-to-date.

I second the notion of an Avast!/Zone Alarm tag team. I used that for years when I was using windoze regularly and I had very few problems.

---

