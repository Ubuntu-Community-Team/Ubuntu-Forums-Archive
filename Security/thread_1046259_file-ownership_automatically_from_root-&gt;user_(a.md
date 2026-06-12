---
title: "file-ownership automatically from root-&gt;user (audacious, pulseaudio, root)"
date: 2009-01-21
forum: Security
---

### Post by boerhave on 2009-01-21
Problem: 

Ownership and file permissions of a user config file were somehow automatically altered from root:root -r--r--r-- to <username>:<username> -rw-r--r--. Furthermore the contents of the file were changed.

Root-owned files having their contents automatically wiped and the file-ownership changed scares me _quite a lot_.


Background:

A recent dist upgrade to 8.10 resulted in sound problems originating in pulseaudio. I removed it as completely as I could (purge + config + init.d scripts that did _not_ get purged (which was annoying)).

After the upgrade the desktop audio application audacious had its output set to pulseaudio. Changing the config back to alsa worked, but was not remembered between closing and opening of audacious. The config file (/home/<username>/.config/audacious/config) _was_ altered but apparently automatically reverted at the moment audacious was closed.

Assuming this was something audacious did itself, and not having the time to look in audacious itself, I first changed permissions on the config to readonly (after applying the change to alsa). 

This had no effect, the file was still altered, and the file permissions were reset to rw. This annoyed and amazed me.

I changed ownership of the config file to root and again changed permissions on the config to readonly (after applying the change to alsa). 

This had no effect, the file was still altered, root ownership was reverted to user ownership and the file permissions were reset to rw. This annoyed, amazed and scared me.

I downgraded the distribution and pinned everything related to sound, under the working assumption this problem is somehow related. The system is a home desktop so I can afford to block everything incoming for now, but long-term it seems I have a security problem. To be quite honest I am paranoid enough that this problem makes me consider switching distributions (given lack of time to figure out exactly what is going on myself).


Question:

Can anybody replicate this problem and/or know its specific cause and/or solution?

---

### Post by pdtpatrick on 2009-01-21
from just glancing and recent update .. i would say the file permissions altered during the migration.

---

### Post by boerhave on 2009-01-22
Nope, _after_ the migration I first changed the config of audacious to revert to alsa use.

When this config change didn't stick I altered the file permissions manually to read-only.

When this change didn't stick I altered the ownership of the file to root.

When this change didn't stick _without migrating anything_ I got really upset. 

To be clear: ownership of the config file was altered from root to user at the moment audacious was closed. Nothing any root-powered user should have anything to do with. I repeatedly saw this on my system (the first few times I could not believe it).

And this was without pulseaudio running, which I might conceive to need some root-like power to access the hardware....

After this I downgraded the distribution, and am still wondering what the best course of action to take is.

---

