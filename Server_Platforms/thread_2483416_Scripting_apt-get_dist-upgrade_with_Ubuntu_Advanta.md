---
title: "Scripting apt-get dist-upgrade with Ubuntu Advantage installed"
date: 2023-01-29
forum: Server Platforms
---

### Post by superian on 2023-01-29
I'm not sure if it is down to having activated Ubuntu Advantage or whether this is generally an issue with Ubuntu 22.04 on servers, but..

For many years, I have had a script that checks for and installs available updates.

```
#!/bin/bash
apt-get update
apt-get dist-upgrade -y
(clean cache, refresh evil snaps etc)
```

With the 22.04 servers, it happily updates and then does the upgrade without pausing to ask if I want to do it :) but it then checks to see if any services need restarting and if any *might do*, asks if I want to restart them and won't continue until I answer. :( :(

Typically some are preselected (if apache has been updated, then apache will be preselected, for example) and some are unselected (unattended-upgrades is the classic example). Sometimes, all are unselected meaning it doesn't think any do need restarting, but it will still stay waiting for my OK.

If I do ```
man apt-get
``` there is no indication that the behaviour has been changed like this: the bit about the -y command line option still says "run non-interactively", yet there it is waiting for interaction. There is also no indication of any new command line option to really be non-interactive.

I have not come across an instance where the suggestion about which services need restarting has been wrong, so I am happy to accept the recommendation and just restart/not restart as suggested. 

[B]How do I make it obey the -y command line option?

[/B]

---

### Post by TheFu on 2023-01-30
There is a Debian non-interactive environment variable that should deal with the issue.  However, I haven't tested it.
I find the new behavior offensive too.

Just prepend commands something like this:
```
DEBIAN_FRONTEND=noninteractive apt-get update
```

---

### Post by superian on 2023-01-30
Ah, the next time I get an email notification that there is an update likely to do this, I will give that a try.

(Ah ha, today's will do.)

Alas, it still stops to ask me.

On  the one hand, it's lovely that it thinks about what services do need  restarting (although I suspect some could just be reloaded) but on the  other, argh if I have asked it to JFDI non-interactively, it really  should not stop and wait for the interaction I have said I do not want.

---

### Post by TheFu on 2023-01-30
That environment variable is how the DEVOPS tools work, so if that doesn't handle it, Canonical has broken stuff for many enterprises too.

---

### Post by superian on 2023-01-31
It's needrestart that's being irritating and apparently - there hasn't been an update that triggers this since I edited the script - the full spell is longer.

```
$ DEBIAN_FRONTEND=noninteractive apt-get --assume-yes --allow-unauthenticated -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" dist-upgrade
```

[https://bugs.launchpad.net/ubuntu/+source/needrestart/+bug/2004203](https://bugs.launchpad.net/ubuntu/+source/needrestart/+bug/2004203)

---

