---
title: "Ubuntu - Firewall and Antivirus software"
date: 2013-04-24
forum: Security
---

### Post by carmen2012 on 2013-04-24
I've seen quite a few threads on this forum that say that Ubuntu and Linux in general are so safe that a firewall and antivirus software are not needed.

When I was looking at the features of Ubuntu 12.10 desktop, it says "You can surf in safety with Ubuntu — confident that your files and data will stay protected — thanks to the built-in firewall and virus protection."

What I'm wondering is:

1.  Why would Canonical add these pieces of software if Ubuntu is so safe, has something changed?

2.  Would anyone know what is the name of the firewall and antivirus software that Ubuntu has added in 12.10?

Thank you

---

### Post by Irihapeti on 2013-04-24
A firewall of some description has always (as far as I know) been there. It's just not activated by default. If you're behind a router, you may not need to activate it. In other circumstances, such as with a laptop in an internet cafe, it's a good idea to do so. There are threads about ufw (the current firewall software) on these forums.

There's no built-in antivirus software. You can install it, but it's mainly used for looking for Windows viruses, which might be important if you exchange files from Windows users. I think the statement might be a marketer's way of saying that the system is inherently resistant to viruses.

That said, there are other types of malware such as rootkits, flash/java vulnerabilities and browser attacks, so one still needs to be sensible online. No system is bulletproof.

---

### Post by Bucky Ball on 2013-04-24
*Thread moved to **Security Discussions**.*

---

### Post by PshhPshh on 2013-04-27
> **Irihapeti said:**
> I think the statement might be a marketer's way of saying that the system is inherently resistant to viruses.

Excuse me, but what do you mean by 'the system is inherently resistant to viruses' ? 
Let me please show you my fears:

1) when I type pmap -d PID, I see tons of memory SHARED at the last line of output. What does it mean ? Some other processes can access that ? But which ones ? Any ? Why not any ?

2) If somebody ever heard of freelance market oDesk, there's a simple application called Team, that sends screenshots of your system several times per hour. What does that say to me ? Nothing special, except that there's no real guarantee in the World, that any process, installed or updated with any package, doesn't do the same. I repeat myself: it is oh Jesus Crist so easy for information in my system to be leaked. Without even noticing me. And that makes me so sick and mad about.

---

### Post by lisati on 2013-04-27
> **PshhPshh said:**
> Excuse me, but what do you mean by 'the system is inherently resistant to viruses' 
You might want to take the time to have a look here: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Elfy on 2013-04-27
> **PshhPshh said:**
> Excuse me, but what do you mean by 'the system is inherently resistant to viruses' ? ...

That generally viruses are built for windows machines - so Ubuntu, like any other linux is a system inherently resistant to viruses.

1. Why would Canonical add these pieces of software if Ubuntu is so safe, has something changed?

Ubuntu added ufw some while ago - this is a graphical frontend to iptables.

There used to be other GUI's.

 2. Would anyone know what is the name of the firewall and antivirus software that Ubuntu has added in 12.10?

None that I know of.

Read this - then research some more, ask questions when you need information. 

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by HermanAB on 2013-04-28
Howdy,

You only need a firewall if you do not trust your system, so you put a firewall between the system and the network.  This is required when you run a Windows system, since it has many unknown and undocumented services running by default and it is easy for a user to start dangerous services, so you need a firewall, in a desperate attempt to keep a handle on the network accesses.

A Linux system doesn't do things behind your back.  You know when you start a service such as VNC.  Therefore, you do not need to run a firewall and if you don't know which services you are running, then a firewall application isn't going to keep you out of trouble either.

---

### Post by haqking on 2013-04-28
> **Elfy said:**
> 
Ubuntu added ufw some while ago - this is a graphical frontend to iptables.

There used to be other GUI's.

 

Small correction for clarity, UFW is an interface to IPTables from CLI, **G**UFW would be the GUI for UFW ;-)

Peace

---

