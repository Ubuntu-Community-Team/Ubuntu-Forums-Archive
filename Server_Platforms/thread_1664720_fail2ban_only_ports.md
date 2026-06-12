---
title: "fail2ban only ports?"
date: 2011-01-11
forum: Server Platforms
---

### Post by Thirtysixway on 2011-01-11
I currently have fail2ban up and working on an amazon ec2 machine running ubuntu server 10.04.

Fail2ban is setup to ban ssh, ssh-dos, and a custom phpmyadmin jail.  But I was wondering if it's possible to have the ssh jail only drop users on port 22 instead of completely blocking them from accessing services such as apache.

It would be a temporary fix at the moment, we're migrating production servers so I need ssh access from anywhere while still blocking the bad guys.  But the way filtering is setup at some locations, if one person were to brute force and get banned, they'd block the websites for the whole network.  Eventually we will be moving to a better solution by dropping all connections on port 22 except allowed IP addresses. But until then I need to ban only port 22 with fail2ban. any ideas?

---

