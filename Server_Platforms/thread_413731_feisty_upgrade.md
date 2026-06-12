---
title: "feisty upgrade"
date: 2007-04-19
forum: Server Platforms
---

### Post by -=Ghostlike=- on 2007-04-19
hi, I want to upgrade my server to feisty, it now runs on Edgy

I found the 'upgrade page' [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

and it says to install update-manager-core but that package doesn't exist, not even in the packagelist on packages.ubuntu.com

Is this package missing and should I do the manual upgrade, or will this package be available soon?

Thanks, Casper

---

### Post by pba on 2007-04-19
I am not sure if this is correct, but I found a package named unattended-upgrades.

I have installed it and is now running "unattended-upgrade -d". Wish me luck :-)

---

### Post by tla on 2007-04-19
It's in the feisty repository though :D

Tried editing sources.list to install it, but it seems to just hang at 0%

---

### Post by gnaunited on 2007-04-19
This may sound stupid, but you are running "apt-get update" right?

My server isn't booted up so I don't know.

---

### Post by tla on 2007-04-20
Tried both using the update manager and the usual apt-get way, they both "worked", but it just hangs during startup after running local boot scripts.

Edit: Oh, the actual login prompt appears before the startup sequence is done, so it's actually not slower it's just that i can't see the login prompt before i press enter or something.

---

### Post by mariuz on 2007-04-21
yes i have the same problem on 2-3 servers 
i have no login prompt  but the rest is ok 
i can log in with ssh and all is good

---

### Post by tla on 2007-04-21
> **mariuz said:**
> yes i have the same problem on 2-3 servers 
i have no login prompt  but the rest is ok 
i can log in with ssh and all is good

The login-prompt is there, it just appears before the startup sequence is complete.

If you press enter it'll print out the login prompt the real place.

---

### Post by mariuz on 2007-04-23
> **tla said:**
> The login-prompt is there, it just appears before the startup sequence is complete.

If you press enter it'll print out the login prompt the real place.

yes that is ok on 3 servers i have upgraded but i have 2 
who got this message at boot 
tty1 Unknown stanza
and after a that i got no login prompt:mad:

---

### Post by mariuz on 2007-04-23
i found it how to get my tty back 
here is the thread 

[http://ubuntuforums.org/showthread.php?p=2430369](http://ubuntuforums.org/showthread.php?p=2430369)

:guitar:

---

### Post by James Keating on 2007-04-30
The problem is in /etc/event.d/tty1 (and tty2 etc.)

The last two lines should be 
exec /sbin/getty 38400 tty1
respawn

not 
respawn
/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1

After fixing each of the tty files, my machine booted fine, though it needs a little push at the end by pressing enter.

---

