---
title: "Getting Quota Information"
date: 2007-10-27
forum: Server Platforms
---

### Post by gdi2k on 2007-10-27
I have quotas set up and running successfully. However, I have stumbled across a problem due to the way I have set up accounts on the system: Rather than giving users named accounts (fred, john etc.), each user has a 6-digit numbered account (624472 for example). The reason is that this is a public facing system, and the accounts are associated to users anonymously, not by name. 

The problem with this setup is the following statement in the man page of setquota:
**Note that if a number is given in the place of a user/group name it is threated as an UID/GID.**

Here's a snip from the output of repquota: 
```
Block limits                File limits
User            used    soft    hard  grace    used  soft  hard  grace
----------------------------------------------------------------------
624472    --   13992       0  122880            261     0     0
```

Looks good. But if I run: 

```
# quota -u 624472
Disk quotas for user #624472 (uid 624472): none
```

That's because UID 624472 doesn't exist - it's the username, not UID (the UID is in fact 1047). 

The reason I need this to work is that I'm including this stuff in a script, and I need to be able to set and retrieve quotas from the command line. 

Any ideas as to how I might work around this issue?

---

### Post by MJN on 2007-10-27
How about something like:

**quota -u `id -u <username>`**

or

**echo "id -u <username>" |quota -u**

I don't use quotas so have not checked if either of these will work as intended.

Mathew

---

### Post by gdi2k on 2007-10-27
Excellent, works nicely. Many thanks!

---

