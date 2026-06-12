---
title: "Moving from V210 to V20z"
date: 2006-12-18
forum: Sun Sparc Users
---

### Post by petef on 2006-12-18
Hi guys,

We are currently looking at moving one of our machines which runs ubuntu, exim, spamassassin, clamav for email and dns from a V210 Sparc to a V20z with twin AMD opteron's. Im looking at installing the x86 version of ubuntu then tarring up the V210 and restoring over the top of the newly installed machine, then configuring the network cards etc one problem I can see is that Im going to be going from the sparc version of ubuntu to the x86 version. Can anyone see any other problems with this ? 

Cheers

Pete

---

### Post by netztier on 2006-12-19
> **petef said:**
> tarring up the V210 and restoring over the top of the newly installed machine

... thus replacing a whole lot of x86 or x64 binaries and libraries with SPARC binaires? Not a good idea!

> **petef said:**
>  Can anyone see any other problems with this ? 

It might work if you restrict your tarball to configuration and spool directories, provided that:

[LIST]
[*]they don't contain any architecture-specific binaries and libraries
[*]you are using exactly the same (or at least compatible) versions of your tools on both machines
[*] directory structures match on both platforms
[*]you make sure that libraries and stuff is all present as x86 or x64 versions on the new machines.
[*]that UIDs and GIDs for your deamons match on the old and new machine, or you'll probably run into file permission problems on your new machine.
[*]a load of other problems...
[/LIST]

I'd rather suggest to 
[LIST]
[*]build the new machine from scratch, 
[*]install all services and deamons 
[*]with their UIDs and GIDs, and if possible make sure they match 
[*]and then migrate the application-specific configuration and  spool directories to the new machine - a tarball might be good here.
[/LIST]
best regards

Marc

---

### Post by petef on 2006-12-19
Thanks Marc, this is the route Im going gona build it from scratch. Oh what fun.

Cheers for the reply 

Pete

---

