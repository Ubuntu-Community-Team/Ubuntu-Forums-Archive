---
title: "Can't connect to samba share"
date: 2015-02-17
forum: Server Platforms
---

### Post by parisv on 2015-02-17
I've setup samba (probably incorrectly) and I cannot map to it from a Windows machine (the windows machine is on an active directory domain)

I would like the user monitor to be able to edit the files as root or just map to it as root directly.

So my samba.conf has this:

[checks]
        path = /opt/omd/versions/1.20/share/check_mk/checks
        force user = root
        force group = root
        valid users = root,monitor
        writeable = yes
        write list = root,monitor
        browseable = yes
        create mask = 0775

In windows I try mapping a drive to \\server\checks

I've tried using servername\monitor servername\root WORKGROUP\monitor WORKGROUP\root


none of them work.

the checks dir has these permissions.

drwxrwxr-x 2 root root 20480 Jan 30 15:38 checks

---

### Post by darkod on 2015-02-17
Does the servername resolve in the AD? Can you ping the ubuntu server by name?

Have you tried \\ipaddress\checks?

Also, forcing user root is not a very good idea. But you can do it if you insist. Any special reason to force users to access the share as root?

---

### Post by parisv on 2015-02-17
Yes I can ping by name but tried using ip without any joy.

I did this at home and could not get it working till I had the windows machine in the same workgroup. I would prefer not to add this box to ad if I can do so.

The files in this directory need to be owned by root:root. So if I map as the user monitor create a new file won't it be owned by monitor?

---

### Post by volkswagner on 2015-02-17
It's a bit odd. I don't recall ever seeing anyone trying to share with root user on this forum.
Now twice in 24 hours I see this request.

I agree with bab1 in [this post]("http://ubuntuforums.org/showthread.php?t=2265554") from yesterday. Root user
has no place in a SAMBA config.  If root should be the owner and group, the file really shouldn't be shared on a network.

If you are not joining the SAMBA server to the domain, you'll need to add user/passwords to SAMBA server.

---

### Post by parisv on 2015-02-17
thanks very much, I didn't set the smb password for the user....  smbpasswd -a monitor

---

