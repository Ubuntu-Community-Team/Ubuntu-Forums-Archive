---
title: "Active Directory Setup"
date: 2008-09-17
forum: Server Platforms
---

### Post by gary.hook on 2008-09-17
Can someone point me in a direction to find a good HOW-TO guide for setting up a Ubuntu server in an active directory domain using Samba?

I've installed Ubuntu, Likewise, and joined the domain but I can't get Samba set up properly to authenticate and allow Windows users in the domain access to the Ubuntu shares?

I've googled and searched the forums but can't seem to correct the problem.  Not sure if it's a winbind issue (likewise) or not?

I can log into the domain from the Ubuntu machine using \DOMAIN\uname so I know the authentication is working in 1 direction.

Any help would be appreciated!

Using Ubuntu 8.04 LTS in a Win2003 domain environment.

---

### Post by trmentry on 2008-09-17
> **gary.hook said:**
> Can someone point me in a direction to find a good HOW-TO guide for setting up a Ubuntu server in an active directory domain using Samba?

I've installed Ubuntu, Likewise, and joined the domain but I can't get Samba set up properly to authenticate and allow Windows users in the domain access to the Ubuntu shares?

I've googled and searched the forums but can't seem to correct the problem.  Not sure if it's a winbind issue (likewise) or not?

I can log into the domain from the Ubuntu machine using \DOMAIN\uname so I know the authentication is working in 1 direction.

Any help would be appreciated!

Using Ubuntu 8.04 LTS in a Win2003 domain environment.

I don't have a how-to to point you to... but I had setup a 8.04 server in AD and gotten it to auth groups to sudo.  Maybe the same type of thing for samba.

in my sudo config i had for a group done the following:

%domain\\group-name

the \\ was needed.   The group name though was a bit more tricky... on 2003 AD if it was a group created in 2003, it was the literal name of the group.
However there were legacy groups from 2000, and I had to use the DG name.

%domain\\group-name-dg etc.  It was a lot of trial and error.

As to using this in Samba.  I use local groups on my samba server to see who has access to read/write, etc.

```

[fileserv]
        path = /shares/fileserv
        valid users = @users
        admin users = @admin
        write list = @admin

```


the group 'users' has access to the share (read-only).  'admin' as write access.

You maybe able to translate the domain group to these.

valid users = @domain\\group-name

But again, may take some trial and error.

---

