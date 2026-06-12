---
title: "Best Way to moutn NFS shares by LDAP Group"
date: 2010-02-27
forum: Server Platforms
---

### Post by gmjs on 2010-02-27
Hello,

I've been trying to set up a Linux-only network and currently have a working DHCP, DNS, LDAP and NFS server, with a client that can authenticate with the LDAP server and a central /home folder.

However, if I wanted to share folders on the NFS server, how would I make the share available to, for example, a particular group of users in the directory?

I've never used NIS(+) on a network, but believe you can add a 'group' of users in the /etc/exports file--simples!

Does anyone know of the best way to do it (even better anyone who is doing this in a production environment)?

Many thanks,

Graham

---

### Post by ICEB3AR on 2010-02-28
I think this should work fine with Kerberos. 

I've not tested it yet. ;)

---

### Post by gmjs on 2010-02-28
Thanks for the reply.

From what I've read, Kerberos authentication forces the host to be authorized before a share is mounted, which is good.  However, I can't see how this would allow you to mount particular shares based on the user's group.

Is it more usual to mount all shares (or automount) and then set permissions so that only the users that should be able to access them on that machine can?

Many thanks,

Graham

---

### Post by capscrew on 2010-02-28
> **gmjs said:**
> Hello,

I've been trying to set up a Linux-only network and currently have a working DHCP, DNS, LDAP and NFS server, with a client that can authenticate with the LDAP server and a central /home folder.

However, if I wanted to share folders on the NFS server, how would I make the share available to, for example, a particular group of users in the directory?

I've never used NIS(+) on a network, but believe you can add a 'group' of users in the /etc/exports file--simples!

Does anyone know of the best way to do it (even better anyone who is doing this in a production environment)?

Many thanks,

Graham

There is no need for NIS+.  You can use the "valid user" directive in the share stanza of the /[FONT="Courier New"]etc/samba/smb.conf[/FONT] file.  Names starting with '@', '+' and '&' are for interpreted as "all the users in the group".  The syntax is looks like this. 
```
valid users = greg, @pcusers 
```

Note this from the Samba documentation.
```
valid users (S)

    This is a list of users that should be allowed to login to this service. 
Names starting with '@', '+' and '&' are interpreted using the
same rules as described in the invalid users parameter. 
```

The relevant section is 
```
A name starting with a '@' is interpreted as an NIS 
netgroup first (if your system supports NIS), and then as a UNIX group 
if the name was not found in the NIS netgroup database.

A name starting with '+' is interpreted only by looking in the UNIX group 
database via the NSS getgrnam() interface. A name starting with '&' is interpreted only 
by looking in the NIS netgroup database (this requires NIS to be working on your system). 

[COLOR="Blue"]The characters '+' and '&' may be used at the start of the name in either order[/COLOR][I][COLOR="Navy"] so
the value +&group means check the UNIX group database, followed 
by the NIS netgroup database,[/COLOR][/I] and the value &+group 
means check the NIS netgroup database, followed by the UNIX group
database (the same as the '@' prefix).
```

---

### Post by gmjs on 2010-02-28
Thanks for the detailed reply.

However, as there will be no integration with any Windows machines or shares, I'm hoping not to use Samba at all for the network and use NFS only.  It looks like I can set up NFS share paths in LDAP, so I'll have a look at that.

Thanks,

Graham

---

### Post by capscrew on 2010-02-28
My mistake. Not enugh coffee yet.  I totally misread that you were using of NFS.  My bad.  :-(

Still, why do you need NIS?  As long as the GID is consistant from host to host you should have no problems.  LDAP should do that.  Both NIS and LDAP are for centralizing user and group data.

I believe that you can actually run NFS correctly if you manually keep the UID and GID numbers consistant.  NFS is only a method to use RPC to mount remote file systems to the local host.

---

