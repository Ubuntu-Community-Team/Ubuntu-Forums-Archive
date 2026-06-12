---
title: "Users and Group"
date: 2007-06-12
forum: Server Platforms
---

### Post by Unknowndeepness on 2007-06-12
Hi there.

I've been trying to clean out my server a bit now, and I've seen alot of users and groups that I myself didnt add. They were there from the start or were later added when installing some software.

I've searching through my computer with "find / -gid <gid>" and "find / -uid <uid>" for files and / or folders in this user / groups ownership, with zero output.

So, how many of these are really needed? Is there some which is required for the system to start?

I really just want to know which are crucial, so i know which i cant delete without the system breaking, forcing me to reinstall the system. I'm guessing just a service fails, which i can fix quite easily, eather by searching for the service configfiles, or simply readding the user / group.

Thanks in advance.

---

### Post by elst on 2007-06-12
Network services often use a dedicated account that won't have a home directory.  Obviously you can remove specialized accounts and groups for network software that you installed and de-installed later. It isn't really a good idea to delete built-in system groups, because future software installations may rely on a group that you removed. There isn't a security or performance benefit to removing built-in groups, so you don't gain anything by it.

---

