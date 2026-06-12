---
title: "apparmor trampling on qemu in 9.10"
date: 2009-11-07
forum: Virtualisation
---

### Post by pootle1 on 2009-11-07
I'm having problems with apparmor since I built a new machine with 9.10 server (x64).  I can define VMs OK from the xml file exported from the old host (running 9.04), but I cannot start them.  I get rude messages about profiles.

After much messing about getting nowhere I removed apparmor (using apt ...   remove) and now everything is fine again.

I don't really want to run without apparmor, but I don't want to spend ages trying to find my way around apparmor - the few things I've found are rather impenetrable for my brain at least.  Is there a simple way around this?

---

