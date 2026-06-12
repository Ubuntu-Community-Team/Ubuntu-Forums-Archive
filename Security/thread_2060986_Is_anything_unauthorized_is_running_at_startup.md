---
title: "Is anything unauthorized is running at startup"
date: 2012-09-21
forum: Security
---

### Post by Kissell on 2012-09-21
I powered up some old hardware that was running Ubuntu 10.04 and plugged it in and forgot about it for a few months, got busy doing other things, then one day it started sending out a bunch of DoS attacks, so many that it ate all my bandwidth and I couldn't get to the internet.

Internet is back now that I shut the server down.  ^phew^

But how can I see what was going on with it?  

When I boot it up without a network connection I can't login, it must be constantly running a process that makes it too busy to respond to my login request.  So I signed on in single user mode and got access to the system.

I checked sshd_config and root logins were permitted, but root should never have had a password configured for it, and root hadn't logged in according to /var/log/auth.log.

I'd like to know what it was running, and what account was compromised, and if it was out of date on security patches or not.

---

### Post by Kissell on 2012-09-21
A Ubuntu 10.04 box was hacked.  

The network cable was pulled because it was eating all the bandwidth on the network.

I wasn't able to login anymore, so I started single user mode and changed the root password, and still can't login normally.  

I suspect something is running that shouldn't be.  

How can I find this rogue process and remove it from starting up?

nothing unusual is in cron or /etc/rc.local

---

### Post by oldos2er on 2012-09-21
Moved to Security Discussions.

---

### Post by irv on 2012-09-21
If you run
```
top
```
in a terminal it would tell you what is running and what is using CPU, Memory, and swap.

---

### Post by wacky_sung on 2012-09-21
If nothing is important down there. Format it is a quick way to your solution,otherwise it will consume lot of your time doing your forensic and troubleshooting.

---

### Post by tubbygweilo on 2012-09-21
Slash and burn,slash and burn.
Install a clean operating system then add in backups, you are then ready to go. may well be fastest, surest way to up and running.

---

### Post by rookcifer on 2012-09-21
> **Kissell said:**
> How can I find this rogue process and remove it from starting up?

If the attacker has root, you can't do anything.  There could be a rootkit, etc.  It will take *far* more time to forensically analyze it than it's worth.

Is this a desktop box or a server?  You should attempt to figure out *how* you got hacked so you will learn a lesson for next time.  But regardless, you need to format and reinstall fresh.

---

### Post by Kissell on 2012-09-21
"top" won't work, cause I can't get into the server except in single user mode, and then it's clean at that point.

I already copied the data off to another disk and built a new server, just messing with this old one to try to find out how it was compromised.  

I'd like to be able to prove either an account had a weak password that was brute forced, or a security exploit was taken advantage of, some solid evidence other than "i don't know, it just got owned"

---

### Post by CharlesA on 2012-09-21
> **rookcifer said:**
> If the attacker has root, you can't do anything.  There could be a rootkit, etc.  It will take *far* more time to forensically analyze it than it's worth.

Is this a desktop box or a server?  You should attempt to figure out *how* you got hacked so you will learn a lesson for next time.  But regardless, you need to format and reinstall fresh.

Agreed. Just wipe the box and go on with your life.

> **Kissell said:**
> "top" won't work, cause I can't get into the server except in single user mode, and then it's clean at that point.

I already copied the data off to another disk and built a new server, just messing with this old one to try to find out how it was compromised.  

I'd like to be able to prove either an account had a weak password that was brute forced, or a security exploit was taken advantage of, some solid evidence other than "i don't know, it just got owned"

top should run fine even in single user mode. As for seeing what happened, check here [https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

---

### Post by Ms. Daisy on 2012-09-21
> **Kissell said:**
> I'd like to be able to prove either an account had a weak password that was brute forced, or a security exploit was taken advantage of, some solid evidence other than "i don't know, it just got owned" Can you answer some of those questions right now? Someone knows the usernames & passwords existing on the server, right? And someone knows if and how it got patched regularly, right?  You know what services were running & on what ports, right?  Who had access? What were they allowed to run?  You'll probably uncover several security holes if you answer all those questions. That's what you present as the reason.

If you can't answer these questions based on the existing documentation of the server, then that was your problem.  Lesson = document everything, set policies & enforce them.

IMO that will be a far quicker way to find out what went wrong then analyzing the box forensically.

---

### Post by CharlesA on 2012-09-21
> **Ms. Daisy said:**
> Can you answer some of those questions right now? Someone knows the usernames & passwords existing on the server, right? And someone knows if and how it got patched regularly, right?  You know what services were running & on what ports, right?  Who had access? What were they allowed to run?  You'll probably uncover several security holes if you answer all those questions. That's what you present as the reason.

If you can't answer these questions based on the existing documentation of the server, then that was your problem.  Lesson = document everything, set policies & enforce them.

+9000. Excellent post.

---

### Post by cariboo on 2012-09-22
Moved to Security Discussions, and merged with an existing thread.

---

