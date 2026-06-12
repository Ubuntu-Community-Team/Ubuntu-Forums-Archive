---
title: "Curious SSH behaviour"
date: 2011-02-19
forum: Server Platforms
---

### Post by PaulWhipp on 2011-02-19
Hi there,

I hope this is a good spot for this question.

I have a server running ubuntu 10.04 and another running Centos 5. The two systems have similar configurations and run a few dozen websites each (I have been experimenting to see which OS I prefer for production servers - ubuntu wins for utility).

Among other things, I use SSH with public key encryption to manage them (e.g. ssh <server url>) from my desktop PC (Ubuntu 10.04 LTS).

Sometimes I use ssh on my ubuntu 10.10 laptop to open a shell on my desktop PC (via password as its local network access only).

In the desktop shell on my laptop I can ssh to the Centos server but not to the ubuntu one. It gives the error "Permission denied (publickey)" even though the identical command works fine in a local shell on the actual desktop PC.

Why don't they both work? I'll happily accept an RTFM response for what is happening so long as someone will tell me which manual I should read.

---

### Post by hawkmage on 2011-02-19
Try running the failing ssh command with the option -vvv to get very verbose debugging info and post it here and we may be able to help you.

---

### Post by joberly on 2011-02-19
> **PaulWhipp said:**
> 
In the desktop shell on my laptop I can ssh to the Centos server but not to the ubuntu one. It gives the error "Permission denied (publickey)" even though the identical command works fine in a local shell on the actual desktop PC.

Compare the /etc/ssh/sshd_config files and make sure the one that is *not* working, does not have the PasswordAuthentication no and also PubKeyAuthentication lines are correct.

---

