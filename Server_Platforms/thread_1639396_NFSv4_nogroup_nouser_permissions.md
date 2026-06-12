---
title: "NFSv4 nogroup nouser permissions?"
date: 2010-12-06
forum: Server Platforms
---

### Post by bertmanphx on 2010-12-06
Hello,
I've used the NFS how to on the Ubuntu Community wiki [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo") to setup a shared directory between my Ubuntu 10.10 server, and two clients, one running 10.04, another 10.10.    I can create and read files from both machines just fine but cannot modify a file created by the other machine.
when viewing the permissions on machine A, that was created by machine B, the permissions say "nogroup, nouser".  
Both users are setup on the server with the same UID, and GID's.  Also, both machines are setup to create files that by default are read/write possible for user and group, per the link [here.]("http://ubuntuforums.org/archive/index.php/t-738099.html")

This worked well with NFSv3.


Any thoughts on what I'm doing wrong?

bertmanphx

---

### Post by bodhi.zazen on 2010-12-07
The users and groups must be the same on both server and client, both in terms of the actual name and the uid and gid (numbers) listed in /etc/passwd and /etc/group

---

### Post by bertmanphx on 2010-12-07
Hello,
I double checked, and they do match.  user #1 is uid 1000 on both their client and the server.  user #2 is UID 1001 on their client and the server.  They both are members of GID 100 "Users".
I wonder if it has to do with the domain name that network manager is putting into /etc/reslolv.conf?  It's picking up ph.cox.net, but the domain listed in idmap is localdomain....?

bertman

---

### Post by bodhi.zazen on 2010-12-07
> **bertmanphx said:**
> Hello,
I double checked, and they do match.  user #1 is uid 1000 on both their client and the server.  user #2 is UID 1001 on their client and the server.  They both are members of GID 100 "Users".
I wonder if it has to do with the domain name that network manager is putting into /etc/reslolv.conf?  It's picking up ph.cox.net, but the domain listed in idmap is localdomain....?

bertman

If the user names and UID / gid are the same, then yes it is lilkely a DNS problem.

You could try installing dnsmasq on the server and using it as the first name server on both server and client.

---

### Post by bertmanphx on 2010-12-10
I thought I should update this.
I still have the no group, no user issue.  However, I found that by default, a user is member of the same group, not "users".  In other words, the user "alison" has a main group setting of "alison", not "users".  Once I changed both person's main group to be the same, the permissions were no longer a problem.

bermanphx

---

