---
title: "Specific user in hosts.deny"
date: 2007-03-14
forum: Server Platforms
---

### Post by LotsOfPhil on 2007-03-14
I want to ban a specific username from accessing my computer. I was going to do this in hosts.deny but can't figure out the syntax. Nor am I sure that it is possible.

The username is potato

I have tried putting 
ALL: potato@ALL
-or-
ALL: potato ALL
-or-
ALL: ALL potato

In the /etc/hosts.deny file. None of these work. Can someone help?

---

### Post by Strider on 2007-03-14
Haven't tried this myself but take a look at the man pages for hosts.deny ("man hosts.deny").  It specifies you can do something like:

daemon: user@host (daemon is the service, i.e. tftp, ftp, http, etc)

And you may need to restart the inet.d process.  Not sure.

-Mike

---

### Post by LotsOfPhil on 2007-03-14
You don't need to restart anything in inet.d. If you put ALL: randomhost and try and ssh in from randomhost, you get denied.

I looked in man hosts.deny and couldn't find what I am looking for. It made me think it could be done, but I couldn't figure it out. The man page is where I got my failed attempts from.

---

### Post by MJN on 2007-03-14
Why not just remove the users' account? Or am I missing something? (quite likely!)

Mathew

---

### Post by LotsOfPhil on 2007-03-14
Why not just remove the user? I can ban him from my computer but I am just one node in the network. He is welcome to the rest of it.

The user accounts are on a central server.

---

### Post by MJN on 2007-03-14
I'm probably being a little slow here so bear with me....

What is it you're trying to do? That is, what is your situation/setup and what problem is blocking a particular user attempting to solve?

Mathew

---

### Post by LotsOfPhil on 2007-03-14
We have 20 machines. Any user can access any machine. I want to make it so a certain user cannot access a specific machine.

Deleting the user is not an option, unfortunately. I thought I'd be able to do it through hosts.deny
Currently I'm doing it with a DenyUsers entry in sshd_config, but I'd like to block all services.
I just can't figure out the syntax for this, if it is even possible.

BTW, I don't think you're being slow. I am very happy you're trying to help. Thank you.

---

### Post by MJN on 2007-03-14
Okay, pam_access could be what you're after. This common authentication is (can be) used by all manner of services and allows simple user-based access control.

Check out [http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html) (at the time of writing connectivity to the site was a bit flaky so try again later if it's down) or [http://www.informit.com/articles/article.asp?p=165226&seqNum=12&rl=1](http://www.informit.com/articles/article.asp?p=165226&seqNum=12&rl=1) and this should give you a heads up on what's required. You're basically after a 'allow ALL except POTATO from ANYWHERE' kind of rule.

Mathew

---

### Post by Mr. C. on 2007-03-16
There is no reliable way to enforce username lookups via tcpwrappers.   Search for and read the section CLIENT USERNAME LOOKUP in :

```
man host_access
```

MrC

---

