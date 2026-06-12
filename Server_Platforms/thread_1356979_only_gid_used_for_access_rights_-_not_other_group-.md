---
title: "only gid used for access rights - not other group-memberships (ldap/nfs)"
date: 2009-12-16
forum: Server Platforms
---

### Post by nikgid on 2009-12-16
Hello,

ich got problems trying to give access permissions for a directory to a group of users. I am using LDAP and have the homes mounted via NFS. The directory in question is inside the home-directory.

In LDAP I have established the group ("team", gid=1007) and have made the users belonging to the group members of the group (also via phpldapadmin).

When I check the group-membership of one of the users with "id", the group "team" (1007) is listed - rightly so:
```
ichnich@asterix:/home$ id
uid=1557(ichnich) gid=1000(dummy) Gruppen=1000(dummy),1001(audio),1002(video),
1003(plugdev),1004(cdrom),1005(floppy),1006(buero),1007(team)
```
("Gruppen" = german for "groups")

But still this user is not allowed to enter the desired directory, although the directory belongs to group "team" (1007) and has 770 as permissions (meaning full access for group members, right?)!
```
ichnich@asterix:/home$ ls -al | grep bilder
drwxrwx---   6 root        team   4096 2009-12-15 13:06 bilder
ichnich@asterix:/home$ cd bilder
bash: cd: bilder: Permission denied
```

Only after changing the gid of one of the groups members to gid=1007 (gid being the _main_ group of this user), that user is then allowed to enter the desired directory etc.
```
niklasg@asterix:/home$ id
uid=1001(niklasg) gid=1007(team) Gruppen=1001(audio),1002(video),
1003(plugdev),1004(cdrom),1005(floppy),1006(buero),1007(team)
niklasg@asterix:/home$ cd bilder
niklasg@asterix:/home/bilder$
```

Why and where is there a difference between gid and other groups that the users are members of?
What am I doing wrong?
What else information might you need to be able to help me?

I want all users who are members of the group "team" to be able to access directories that belong to the group "team". I can't change all of their gid's to "team" because some of them should also belong to sub-groups who then again have exclusive access to other directories etc.

I hope my gibberish makes sense :-)

Thanks a ton in advance for your help,
Niklas

---

### Post by nikgid on 2009-12-17
I try to add some more info in the hope that somebody has mercy and attemps to help me :-)

Here is the clients **/etc/nsswitch.conf**
```

passwd:         ldap files
group:          ldap files
shadow:         ldap files

hosts:          files dns mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

**/etc/exports** on the Server:
```

/nfs    *(rw,sync,no_root_squash)

```

**getent group** on the client first lists correctly all Groups from LDAP (including the group "team" (1007)) and all members and after that the contents of the clients /etc/group file.

Where could my mistake be? 
Please help!

---

### Post by nikgid on 2010-01-12
<bump>... three weeks and no reply at all :-(

Have I asked in a wrong way or in the wrong forum?

Can please someone answer in any way leading me a bit forward?

Thanks,
NIklas

---

### Post by volkswagner on 2010-01-12
This is way beyond my expertise, yet I feel your pain in silence.  

Perhaps you can chown the /home/bilder so owner and group are set to team.

What is the GiD of the actual share on the server?

---

### Post by Minarion on 2011-01-13
Having exactly the same issue as described above, only now with Lucid servers and hosts.

Does anyone know of any known fixes?

If not, what alternatives have you found?


Kind regards

---

### Post by efball3 on 2012-06-20
I have this problem also.  I can cd to the directory, but trying to read or write anything generates and error:

ls: reading directory .: Input/output error

Also in a directory that is world readable, I can not write to a file that has group write permissions (770) for a group that I am a member of.

Lucid, 64-bit using NIS.  RHEL 4 and 5 do not have this problem.

---

