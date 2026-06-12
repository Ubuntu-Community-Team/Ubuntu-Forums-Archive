---
title: "Help with virtualbox shared folder permissions for ldap users/groups"
date: 2013-05-09
forum: Virtualisation
---

### Post by BarryDocks on 2013-05-09
Really need some help to get the permissions sorted for ldap users on the guest OS to access the shared folders.

Here's the scenario:
Host: Ubuntu Server 10.04 LTS 64 bit with Virtual box 4.2.6
Guest: Ubuntu Server 10.04 LTS 32bit with Zentyal 2.2 & Guest Additions installed

I have a directory on the host shared with the guest.  I want to use the shared folder as a smb share for the guest users.  Permissions on the host directory are 777.  Permissions on the guest VB shared folder are 770, owned by user root and group vboxsf - I can't change this.     

The users on the guest are authenticated via ldap and all belong to the ldap group __USERS__

My question is, how do I add the ldap group __USERS__ to the local group vboxsf to allow them to access the shared directory?  Alternatively, is there an automagical way to add new ldap users to the vboxsf group?

Thanks

---

### Post by apos on 2013-05-31
I have exact the same problem.

I found two things: 

1. In the directory /media there are my shared folders listed with **sf_**shared_folder_name

2. I can mount my share manually with

share /data/share1 vboxsf uid=4,gid=1901,rw 0 0

where uid 4 = sync and gid 1901 = __USERS__

3. If I create a blank shared folder with zentyal, it gets the uid 4 and gid 1901 (sync, __USERS__).

The problem is that **/data** is a raid5 system on the host.
The zentyal machine is the guest.

Is this a general problem with mounted directories that are not part of the general filesystem?

What permissions do I need to handle shares? root?

Greets
Axel

---

