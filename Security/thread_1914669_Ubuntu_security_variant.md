---
title: "Ubuntu security variant?"
date: 2012-01-24
forum: Security
---

### Post by rectec794613 on 2012-01-24
So I've noticed that there are quite a few distros dedicated to security and firewalls. Ubuntu has a variant for studio work, one for education, and a couple for low-resource. But what about security? Has anyone thought about having a security-oriented variant? There's much security software out there for Linux. Alpine has PaX and SSP for example. The downside for me with Alpine, though, is it isn't based on Ubuntu and doesn't have Ubuntu's repos. So why not get rid of that downside and have an Ubuntu security variant? It *is* possible, right? Just wanted to hear your thoughts.

---

### Post by raja.genupula on 2012-01-24
> **rectec794613 said:**
> So I've noticed that there are quite a few distros dedicated to security and firewalls. Ubuntu has a variant for studio work, one for education, and a couple for low-resource. But what about security? Has anyone thought about having a security-oriented variant? There's much security software out there for Linux. Alpine has PaX and SSP for example. The downside for me with Alpine, though, is it isn't based on Ubuntu and doesn't have Ubuntu's repos. So why not get rid of that downside and have an Ubuntu security variant? It *is* possible, right? Just wanted to hear your thoughts.

+1 I agree , we must have one for Security .I think if you mention this in Ubuntu brainstorm  then it will be fine and its good idea too . 

So please post your Idea here [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by Dangertux on 2012-01-24
Ubuntu is already the epitome of security. Kidding, however I'm fairly certain that the ubuntu kernel is compiled with PaX extensions. It already features fortify source via gcc, address space layout randomization and in supported processors can e configured with support for noexec. It features highly customizable mandatory access controls via apparmor and is compiled with support for SElinux. 

So what would you want a proposed Ubusec to include? Rbac with grsec? It's also relatively trivial to compile a kernel to support that as well. 

Hope this helps.

---

