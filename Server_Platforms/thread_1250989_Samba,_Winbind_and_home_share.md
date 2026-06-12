---
title: "Samba, Winbind and home share"
date: 2009-08-27
forum: Server Platforms
---

### Post by karneevor on 2009-08-27
Hi.

I just installed a server with samba and winbind, and integrated the server into my existing Windows AD. That worked quite well.

But how do I move my users home dir from the Windows Server 2003 over to my samba in a way so that the logon script works? If I run a logon script that wants to map a drive to the samba server home share, it prompts me for a username and a password on the specific server. All other shares are accessed as I expected.

Apparently, the samba server distinguish between an AD user and a local user.

I've tried to set up user syncronization through webmin, but it doesn't help much.

It could be a problem with the wrong syntax/method in the logon script.

Any help would mean a lot to me.

Kind regards.

Michael Sørensen
Denmark

---

