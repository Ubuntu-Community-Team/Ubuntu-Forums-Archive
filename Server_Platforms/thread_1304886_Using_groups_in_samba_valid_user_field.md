---
title: "Using groups in samba valid user field"
date: 2009-10-29
forum: Server Platforms
---

### Post by ToddDTaft on 2009-10-29
I'm trying to create a samba share that is only available to members of a UNIX group.

As I interpret the samba documentation, I should be able to specify something like this in my smb.conf file:

[FONT=Courier New]valid users = +grname[/FONT]

and all members of the Linux group grname should be able to access the share.  What I'm seeing is that no one can access this share.

I have my samba server configured using [FONT=Courier New]security = ads[/FONT]

User names are synchronized between my Linux systems and AD.  All users and groups are defined in the local /etc/passwd and /etc/group file.

Am I missing some obvious configuration, or is this a bug?

--Todd

---

