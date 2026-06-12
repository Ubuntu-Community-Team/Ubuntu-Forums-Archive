---
title: "Can a program in Linux gain root access without you giving it your password?"
date: 2009-11-08
forum: Security
---

### Post by beastrace91 on 2009-11-08
So the topic of security came out on another message board I am and one of the users there is an IT and brought up some points I was wondering if are really true...

> **"Errant"]Getting a root shell is fairly trivial once you get chance to run some code. The difficulty is in finding a method to insert your escalation code with a big enough memory footprint. If you don't have space to deploy your escalation package it's not going to work :)

Of course you can exploit several bugs in pieces of software to gain root privileges without having to run any extra code too said:**
> http://en.wikipedia.org/wiki/Buffer_overflow[/url]

All the things he mentions seem 100% reasonable - but I am not expert on the subject by any means. I guess my real question is this - can a piece of software really grant itself root access with out me entering my root password? And if this is the case doesn't it make having a root password/account kinda pointless if such exploits exist? I realize no system is flawless by any means but...

Also I know this is case on Windows - but if malware/viruses that can attack Linux as well really exist, can they executed on a system simply by clicking a web link or downloading a file like on Windows or would I need to explicitly run a package containing malicious code (but not necessarily give it my root password)

Just try to educate my system on how safe my system really is :) Any input or useful links are welcome.

Also if anyone cares the original thread on from my other forums can be found [here](http://forums.eventscripts.com/viewtopic.php?t=34390&postdays=0&postorder=asc&start=0).

~Jeff

---

### Post by movieman on 2009-11-08
> **beastrace91 said:**
> I guess my real question is this - can a piece of software really grant itself root access with out me entering my root password?

Yes, if:

1. It has the setuid bit set and is owned by root and/or
2. You ran sudo recently from the same terminal and/or
3. There's a directory permission problem allowing you to write to a directory that root will automatically run programs from (e.g. /etc/init.d during the boot process) and/or
4. If there's a kernel bug.

Otherwise, no method I can think of.

BTW, I don't understand the Emacs thing at all: the editor isn't responsible for checking file permissions, the kernel is.

---

### Post by Agent ME on 2009-11-08
Bugs that allow programs to escalate themselves to root are discovered occasionally, but are usually fixed within a few days in an autoupdate. Make sure to set your security updates to install automatically or make sure to run them yourself frequently.

---

### Post by beastrace91 on 2009-11-08
> **Agent ME said:**
> Bugs that allow programs to escalate themselves to root are discovered occasionally

Ok so this can happen is what your saying? I'm more interested in if a program that intentionally wanted to do this was run on my system - so it could gain access to my root files with out a password then?

~Jeff

---

### Post by movieman on 2009-11-08
> **beastrace91 said:**
> I'm more interested in if a program that intentionally wanted to do this was run on my system - so it could gain access to my root files with out a password then?

Only if you happen to run it from a terminal which has sudo authorisation (by default it's maintained for a few minutes after you type your password), or there's an exploitable bug in the kernel.

However, running a program as you can be even more harmful: I'm less concerned about programs getting root access through exploitable bugs than I am about a program installing an addon into Firefox to capture my online banking details.

---

### Post by Agent ME on 2009-11-09
> **movieman said:**
> However, running a program as you can be even more harmful: I'm less concerned about programs getting root access through exploitable bugs than I am about a program installing an addon into Firefox to capture my online banking details.
Right, programs don't need to get root in order to do damage.

However, they usually need root to be able to spread to other user accounts. As long as it doesn't get root, the virus is contained to the single user account, and could even be wiped out by simply erasing the user account and making a replacement account.

---

