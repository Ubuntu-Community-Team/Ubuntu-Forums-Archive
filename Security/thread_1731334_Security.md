---
title: "Security"
date: 2011-04-17
forum: Security
---

### Post by Quarkrad on 2011-04-17
This verse caught my eye:

[B]All Windows security is like Swiss cheese with bullet holes.
An insecure Linux installation is like cheddar cheese dipped is mutton steel.
A secure Linux installation is like solid titanium[/B].

In my windows days I was about reasonably secure but since adopting Ubuntu/Linux I haven't done anything as I accepted the OS dos not suffer from virus/spyware as per Windoz.  All I do is get the regular downloads from the Update Manager.  I am guessing that as I have a bog standard install I perhaps have a **insecure Linux installatio**n.  Is this the case and if so what should I do without going completely over the top?

---

### Post by yetiman64 on 2011-04-17
> **Quarkrad said:**
> This verse caught my eye:

[B]All Windows security is like Swiss cheese with bullet holes.
An insecure Linux installation is like cheddar cheese dipped is mutton steel.
A secure Linux installation is like solid titanium[/B].

In my windows days I was about reasonably secure but since adopting Ubuntu/Linux I haven't done anything as I accepted the OS dos not suffer from virus/spyware as per Windoz.  All I do is get the regular downloads from the Update Manager.  I am guessing that as I have a bog standard install I perhaps have a **insecure Linux installatio**n.  Is this the case and if so what should I do without going completely over the top?

Here is a good thread for you to check out [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812).

As a past user of Windows over ~16 years (till MS released their prices for 7), I would note that a stock install of Ubuntu is very secure. When I first setup Ubuntu I used grc.com to scan my address (a stock install doesn't even activate the OS firewall) with my machine placed in an Internet facing DMZ (otherwise my hardware firewall would have blocked them). **The result: not one port was found open even though they could be seen**. Do not drop the firewall on a Windows install and do the same, the number of ports open by default is scary to say the least.

Because of the file/folder permissions in use in Ubuntu and with a little user knowledge/commonsense Ubuntu is virtually immune from malware/viruses. Check out the above link for some good security info in Ubuntu.

---

### Post by dfreer on 2011-04-17
Ubuntu is actually pretty rare among the linux distros to do this, which I think is nice: By default, there is no firewall because no services are listening on the outside interface.

Debian, Freebsd, fedora, all as I recall generally have RPC and several other services running, depending on the installation type of course.

---

