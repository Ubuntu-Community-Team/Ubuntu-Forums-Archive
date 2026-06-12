---
title: "libpam-blue and encrypted home problems"
date: 2009-11-29
forum: Security
---

### Post by darkshadow on 2009-11-29
I tried setting up bluetooth authentication which worked with one exception when booting and getting logged in by my phone my encrypted home directory does not get mounted. How can I fix this?

Also if possible can I use some type of proximity checking like blueproximity so I have to basically wave my phone over the computer to unlock it and not just be in the room.

---

### Post by darkshadow on 2009-11-30
Well I have giving up hope of security and plan on doing a stupid thing and leaving my password in plain text unencrypted and just use security by obscurity. I am that tired of typing in my password and just don't care.

Any way I know the command to insert the key into the keyring, and adding it to the start of ecryptfs-mount-private works perfect when I manually run it.

But that script is not ran when logging in from gdm or a terminal (ctrl-alt-f*) so what file can I add it to so it is ran at the right time.

Has to be after username/libpam-blue so I need to know the first script ran the second you login. from either a terminal or via gdm.

---

