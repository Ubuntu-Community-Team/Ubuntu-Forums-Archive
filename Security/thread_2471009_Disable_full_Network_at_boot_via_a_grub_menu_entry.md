---
title: "Disable full Network at boot via a grub menu entry"
date: 2022-01-19
forum: Security
---

### Post by sandman872 on 2022-01-19
Hi @all!

I have a problem which i cannot get solved.
Basically I would like to create a second grub menu entry which, after i choose that one all network interfaces are disabled/firewall blocks all traffic.
Let's call it "Ubuntu Offline Mode".

I read about using rc.local etc. but this would make it permanent.
I'd like to be able to choose from the Grub Bootmanager if i boot into Ubuntu with Networking enabled, or Offline.

I know i could just disable networking after i log in but this should be a security thing and also only one normal account and one with sudo rights should be present.

Grub would look like this:
1. menu entry with enabled networking which is password protected (I got that working)
2. menu entry with no networking which is not password protected (that one gives me a headach)

I tried to find a Kernel parameter but only found sth. for ipv6
I could not find a grub command for it
I tried using runlevel 2 but then the GUI does not really work

Can i somehow add a line to grub where it runs a script that contains terminal commands or is there any other way for it to solve this ??
Any help would be appreciated!

---

