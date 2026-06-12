---
title: "Samba + Active Directory -&gt; Groups not refreshed"
date: 2015-09-08
forum: Server Platforms
---

### Post by Romu on 2015-09-08
Hello all,
My company network is made of a domain controller (Windows Server 2003 + Active Directory) and a nas (Ubuntu 12.04 + Samba 3.6.3). The nas is registered within the DOMAIN thanks to Pbis Open Broker. This nas exposes some shared folders of which the access is controlled on a group basis. Here is an extract of the /etc/samba/smb.conf file:

```
[boxes]
comment = Development boxes
valid users = @"DOMAIN\dev"
writable = yes
path = /media/raid/boxes
write list = @"DOMAIN\dev"

```

This extract shows the **/media/raid/boxes** folder is shared to any user member of the **DOMAIN\dev** group. And this perfectly works. The only issue (but an important one) is the group ownership is not refreshed at all on the nas. Here are 2 examples, first with my own login:

```
id #my login#
uid=76547207(#my login#) gid=76546561(domain^users) groups=76546561(domain^users),76548718(#a group#)
```

This seems nice, but it's wrong because my own account is member of 3 specific groups (not "domain users") and only one is returned by the ```
id
``` command.

Another example, I've seen someone was in the "dev" group and should not, so I removed this account from the "dev" group on the server, and on the nas, I ran the **id** command for this account:

```
id #another login#
uid=76547181(#another login#) gid=76546561(domain^users) groups=76546561(domain^users),76547165(#group 1#),76548718(#group 2#),76548790(#group 3#),76547162(dev)
```

And this also wrong because if the groups would have bee correctly refreshed on the nas, the "dev" group would not appear here. How can I get this to work as expected?

Thanks.

---

### Post by Romu on 2015-09-08
I've a small workaround, while connected to the nas through ssh (with a local account), if I run:

```
su - #a domain login#
```

Then, I'm asked to give this domain login password, I'm getting connected and the group membership is refreshed. But this is still not satisfying, because I need this to be automatically refreshed, for all domain user accounts and group membership.

---

### Post by darkod on 2015-09-09
I am not familiar with Pbis Open Broker. Is it used only to register the server in the AD or also integrates fully into the AD?

I am asking because I believe the correct package to use for AD integration of samba is winbind. It should be getting the correct list of users and groups from the AD DC.

PS. One example: [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

### Post by bab1 on 2015-09-09
> **Romu said:**
> Hello all,
My company network is made of a domain controller (Windows Server 2003 + Active Directory) and a nas (Ubuntu 12.04 + Samba 3.6.3). The nas is registered within the DOMAIN thanks to Pbis Open Broker. This nas exposes some shared folders of which the access is controlled on a group basis. Here is an extract of the /etc/samba/smb.conf file:

```
[boxes]
comment = Development boxes
valid users = @"DOMAIN\dev"
writable = yes
path = /media/raid/boxes
write list = @"DOMAIN\dev"

```

This extract shows the **/media/raid/boxes** folder is shared to any user member of the **DOMAIN\dev** group. And this perfectly works. The only issue (but an important one) is the group ownership is not refreshed at all on the nas. Here are 2 examples, first with my own login:

```
id #my login#
uid=76547207(#my login#) gid=76546561(domain^users) groups=76546561(domain^users),76548718(#a group#)
```...
Do you have a problem with file and directory group ownership or with specific users and their group membership?  We don't need any ***id*** info, If you have a problem with the file system directory and file ownership.  The user-group ownership can be set to inherit the group of the directory you are working in and/or you can use force=<group> in the share parameters to accomplish user-group inheritance.

Maybe you have 2 problems?

---

### Post by Romu on 2015-09-10
@darkod: you can use Samba + Winbind or Samba + Pbis Open Broker, but both are not compliant from what I know. And Pbis Open Broker is sooo much easier to use imho.

@bab1, it's not a problem of file and directory ownership, this is correctly configured and works as expected. It's really an issue about users group membership which are not refreshed when changes are made on the AD server.

Thanks for your help.

---

### Post by darkod on 2015-09-10
So that would mean that Pbis even though easier to use is not configured well??? The first test after integration with AD is to check if the users and groups show up correctly. If they don't (or in this case don't refresh), something is wrong, no?

---

### Post by Romu on 2015-09-10
The above workaround has made the trick one time, but it doesn't work anymore to refresh group membership, at least for the login I use to make those testing.

---

### Post by Romu on 2015-09-10
Of course, but that's the problem, everything is correct the nas is well registered, I can browse users and groups. The only, little, thing which doesn't work very well is group membership.

---

### Post by Kiart_P on 2016-01-25
> **Romu said:**
> Of course, but that's the problem, everything is correct the nas is well registered, I can browse users and groups. The only, little, thing which doesn't work very well is group membership.

Same Issue , Need help too

---

