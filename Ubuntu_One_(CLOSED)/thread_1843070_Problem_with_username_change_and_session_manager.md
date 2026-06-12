---
title: "Problem with username change and session manager"
date: 2011-09-12
forum: Ubuntu One (CLOSED)
---

### Post by DCGU on 2011-09-12
Hi All!

I really needed to change my username and I used

usermod -l newuser -d /home/newuser -m old user

from the recovery console. As a result my username was changed but everything else got messed up. For example, the old user home directory was supposed to copy over to the
new user's (i found command in a thread and the thread-starter claimed it worked for him).
It didn't. As a matter of fact, the old user group remained the same, every file in the directory remained where it was and in the same group. It just changed ownership to the new username. As a result I cant access wifi, I cant open nautilus or almost any application without sudoing it and an annoying message to upgrade pops up every 30 seconds.

I created a new group named newuser. I added the new username there and I changed group for all the files. I managed to get firefox working. But nautilus and evince when started via console keep spewing:

EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported

Additionally:

cat /etc/network/interfaces

gives

auto lo
iface lo inet loopback

and no wlan0 which i suppose is my wireless netcard, nor localhost.
What should I do?? I desperately need to set this thing together since grad school starts in two weeks.

Thanks in advance.

---

### Post by stefanbehr on 2011-10-23
Hey, have you found a solution to this problem? I changed the username of my only account, and the same thing happened to me. The only difference was that I made the change through the system preferences gui.

---

