---
title: "Server Process Created Files Permissions"
date: 2010-11-20
forum: Server Platforms
---

### Post by ks07 on 2010-11-20
Hey all,

Currently have access to a VPS where we are running a small game server on ubuntu - the problem is that it is a multi-user environment, so when one person restarts the server process, all files it creates are owned by that users name and group. I have created a group called 'game' and added both users to it, but I need to know how to make all files in the game server's directory to be r/w/x for the group 'game'. Currently, I have a script that chowns and chmods all files recursively on startup, but I'd prefer not having to do this. Any suggestions?

Thanks

---

### Post by Strega on 2010-11-20
Hi,

I'm pretty new to Ubuntu so I don't know if this is going to help, but do you have Root access? If so, try to do this command in the root of you gameserver```
chown -R :game /dir/to/gameserver/root/
``` If that doesn't work you might want to try```
chown -R game:game /dir/to/gameserver/root/
```Can I ask you what kind of gameserver you are running?

Regards,
Strega

---

### Post by ks07 on 2010-11-20
> **Strega said:**
> Hi,

I'm pretty new to Ubuntu so I don't know if this is going to help, but do you have Root access? If so, try to do this command in the root of you gameserver```
chown -R :game /dir/to/gameserver/root/
``` If that doesn't work you might want to try```
chown -R game:game /dir/to/gameserver/root/
```Can I ask you what kind of gameserver you are running?

Regards,
Strega
That is what I'm running currently - it's not a permanent fix though as it needs running whenever a different user needs to use the server files.

And it's a minecraft server (java).

---

### Post by Strega on 2010-11-21
> **ks07 said:**
> That is what I'm running currently - it's not a permanent fix though as it needs running whenever a different user needs to use the server files.

And it's a minecraft server (java).
Writing that code 1 time, doesn't that fix it, since your users are in the group game?

---

### Post by ks07 on 2010-11-21
> **Strega said:**
> Writing that code 1 time, doesn't that fix it, since your users are in the group game?
It does - but any new files created by the server process are owned by whoever started it - not by the game group. :/

E.g.:
Chown all files to UserA:Game
UserA logs in, starts server.
Server starts fine, all files owned by UserA:Game
---
User B logs in, wants to check server logs.
Server logs created after the chown -R, so they are owned by UserA:UserA

What I need is something that causes the process to create its files automatically owned by someuser:Game - Something similar to umask, although afaik that only works on a user not a process.

---

