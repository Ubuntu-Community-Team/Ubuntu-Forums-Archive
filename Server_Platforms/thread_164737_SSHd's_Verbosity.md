---
title: "SSHd's Verbosity"
date: 2006-04-23
forum: Server Platforms
---

### Post by OwlManAtt on 2006-04-23
Howdy,

I'm trying to not give away much information about my machine. I've got tcp_timestamps off, some funny stateful filtering stuff going on, and I've played with a few other sysctl settings to make its fingerprint look different.

So I've got nmap thinking I'm running Windows NT based off of my fingerprints. Unfortunately, if someone does an -sV with nmap, you see:

xxxxx/tcp open ssh OpenSSH 4.1p1 Debian-7ubuntu4.1 (protocol 2)

Which is, um, a dead giveaway. I know sshd has to reveal its protocol version to clients, but is there any way to *not* have it say Debian-Ubuntu in its version string, short of recompiling it?

And dare I ask - why do the Debian & Ubuntu developers need to put their names into something /anybody/ can grab from your sshd?

---

### Post by LordHunter317 on 2006-04-23
[QUOTE=OwlManAtt]I'm trying to not give away much information about my machine.[/quote]Why?  There's rarely a point.

> I've got tcp_timestamps off,Questionable security gain.

>  some funny stateful filtering stuff going on,Questionable, and downright bad if you broke the way Internet works. 

> and I've played with a few other sysctl settings to make its fingerprint look different.Questionable gain.

> Which is, um, a dead giveaway. I know sshd has to reveal its protocol version to clients, but is there any way to *not* have it say Debian-Ubuntu in its version string, short of recompiling it?Not that I'm aware of.

> And dare I ask - why do the Debian & Ubuntu developers need to put their names into something /anybody/ can grab from your sshd?Because it doesn't matter one lick to security, that's why.

---

