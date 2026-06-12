---
title: "Samba+ACL+Active Directory"
date: 2009-08-04
forum: Server Platforms
---

### Post by raleighb on 2009-08-04
I'm so close to my goal that I can taste it, however there is 1 thing that is getting it the way.

What I am trying to accomplish is this:
1.  Have a share that is administered by an active directory account.
2.  set default permissions on all new folders that inherites the permissions from the parent.
3.  Domain Admins should always have rwx
4.  Domain Users should always have rx (unless I take it away) on a per folder basis.
5.  Be able to add groups with rx and more groups with rwx and still have domain users have rx (or rwx if I granted as such).


I have Ubuntu Server 8.04LTS installed on a server and I am attempting to setup a new file server.  Samba, Krb5, Winbind have all be setup and seem to be working properly.  I have set the permissions at the root level of my share as follows

setfacl -m g:domain\ admins:rwx /home/share
setfacl -m g:domain\ users:rx /home/share
setfacl -m default: g:domain\ admins:rwx /home/share
setfacl -m default:g:domain\ users:rx /home/share

Please not that I have also tried the above with the -R switch to no affect.

Everything starts out ok with these permissions.  When I create a new folder those permissions are carried over.  The problem that I am having starts when I explicitly add a group or user to the newly created folder.  When I add a new user or group it automatically adds the rw permissions for that group (which I change to rwx most of the time) but at the same time removes the default permissions from the Domain Users group.  If I try to add those permissions back the Domain Users it just wipes them out again.


Any help would be appreciated.

Thank you,
Raleigh

---

### Post by wbrb on 2009-08-04
How are you going about explicitly adding users or groups to the new folder?

---

### Post by raleighb on 2009-08-04
> **wbrb said:**
> How are you going about explicitly adding users or groups to the new folder?

Within the windows security dialog.  I am in the Domain Admin group.

---

### Post by HermanAB on 2009-08-04
ADS may be confused.

In general, don't *ever* change a record in Active Directory.  Create a new record and then delete the old one.

Also bear in mind that most features of ADS do not work with Linux.  You can authenticate and get back a list of groups that the user is a member of.  That is about it.  Everything else is cheerfully ignored.

---

### Post by koenn on 2009-08-04
tricky.

Windows ACLs are not 100% POSIX compliant (what did you expect ...) so trying to set POSIX ACL from Windows sometimes gives weird results.

Look i the 'Advanced' view of the Security Dialog. There you usually have a better view on what you're setting. It also helps to set the security in 'Advanced', and ignore what it looks like in the basic view.

Also, use getfacl to see what the actual result is on the fileserver.

---

### Post by raleighb on 2009-08-05
> **koenn said:**
> tricky.

Windows ACLs are not 100% POSIX compliant (what did you expect ...) so trying to set POSIX ACL from Windows sometimes gives weird results.

Look i the 'Advanced' view of the Security Dialog. There you usually have a better view on what you're setting. It also helps to set the security in 'Advanced', and ignore what it looks like in the basic view.

Also, use getfacl to see what the actual result is on the fileserver.


What I am trying to do has already been done by my predicessor.  I'm just missing something and I dont know what it is.  Everything seems to be setup the same.  The only exception is he setup on Ubuntu 6.XX LTS and I'm 8.04 LTS.  So Samba versions are likely different.  But that would indicate a regression to me.

---

