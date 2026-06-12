---
title: "questions about add root user into ldap groups"
date: 2014-03-03
forum: Server Platforms
---

### Post by zhangr on 2014-03-03
hi,

I'm an newbie on openldap.
My OS is "Percise Pangolin" server platform. 
I followed some articles and get suceed setup and NT4 PDC with samba using slapd as backend.
[http://raerek.blogspot.com/2012/05/openldap-user-auth-in-ubuntu-1204.html](http://raerek.blogspot.com/2012/05/openldap-user-auth-in-ubuntu-1204.html)
[http://raerek.blogspot.com/2012/05/samba-pdc-on-ubuntu-1204-using-ldap.html](http://raerek.blogspot.com/2012/05/samba-pdc-on-ubuntu-1204-using-ldap.html)
[http://raerek.blogspot.com/2012/05/samba-pdc-on-ubuntu-1204-using-ldap_28.html](http://raerek.blogspot.com/2012/05/samba-pdc-on-ubuntu-1204-using-ldap_28.html)
Now I'm able to make windows join my domain.
But I still have some problem looking for solutions:
1) How to add root user into Administrators group and Domain\ Admins group?
I've added an ldap user with smbldap-useradd, and I'm able to add the user into Domain\ Admins group.
When I query the user's info with id, it returns me something like this:
```
root@hostname:~# id simon
uid=simon(1000) gid=513(Domain Users) groups=513(Domain Users),512(Domain Admins),544(Administrators)
```
However when I query the root's info:
```
root@hostname:~# id
uid=root(0) gid=root(0) groups=root(0)
```
This makes the root user does not have the Domain Admins role after I login Windows.

I've tried to add root user into Administrators group and Domain\ Admins group,
however althrough "usermod" or "smbldap-usermod" does not return any error,
 but after I execute those commands, id command still return root only belongs to root group.

The group IDs 513 512 and 544 are ldap groups,
those group actually does not exist in /etc/group,
 and the user ID 1000 actually is also an ldap user which does not exist in /etc/passwd either.

I have enabled unix auth, winbind auth, ldap auth, smb password auth,
 however even I disables other authentication method except ldap, 
when I query root users group info with id command, the root user still only belongs root group.
I'm sure that Administrators group and Domain\ Admins group has root as their membership:
```
root@hostname:~#smbldap-groupshow Domain\ Admins
...
memberUid: simon,root
```
But seems the slapd & samba can not return the correct root groups info back to clients.
Do you have any ideas about this issue?

2) Another question is how to add an objectClass and attributes to an existing ldap group?
Well, my PDC sever actually is a part of VMware vSphere environment, the later requires an MS domain.
Since I already have a iSCSI target running on ubuntu server, to save the resource, I decide make it emulate an NT4 domain.
However, after I add my ubuntu server as an identity source for vCenter, I found it can only identify users but no groups.
After doing some search, I found this KB: [http://kb.vmware.com/kb/2064977](http://kb.vmware.com/kb/2064977)
which says the group schema must have:
```
All groups have an objectClass of groupOfUniqueNames. 
All groups have a group membership attribute of uniqueMember.
```
But, as I already finishes ldap database populate, and the schema is provided by samba,
 I don't now how to add additional attributes to an existing dn, and more important I don't know the data to those attributes looks like.
Could you please teach me how to add them?
Thanks in advance.

---

### Post by zhangr on 2014-03-05
no one know anything about my questions?

---

### Post by zhangr on 2014-03-07
Ok, for Q1, I found the solution, just change order to group in /etc/nsswitch.conf
after I make it look for groups in ldap first, id can now show all groups that root user belongs to.
And after I switch the root user to Administrators group, the root user grant the administrator privilege in Windows now.
Stupid Windows..., it just check the SID number.
To the 2nd issue, I also heard some of my classmates meet the same problem on RHEL6.
Could you please provide some suggestions or directions?

---

