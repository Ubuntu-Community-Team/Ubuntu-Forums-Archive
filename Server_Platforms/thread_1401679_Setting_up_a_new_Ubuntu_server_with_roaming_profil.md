---
title: "Setting up a new Ubuntu server with roaming profile"
date: 2010-02-08
forum: Server Platforms
---

### Post by nandugopan on 2010-02-08
Dear all,

We are trying to set up a new Ubuntu server in our lab, with roaming profiles enabled. We have downloaded and installed Ubuntu 8.04 Server Edition (feeling it was more stable). 

There are 40 systems running Karmic and there is one server. The students are to login to the machines locally, but are to have access to a filesystem (which is on the server) that stores their personal files. The logic is that each time the same student may get different systems,but he/she must be able to access their files which is stored in the central file system.

Any ideas how to go about doing this.Currently, the lab uses Windows 2008 Server Edition and Windows XP client.

Thanks in advance

---

### Post by bluefrog on 2010-02-08
2 possibilities (at least)

set up an ltsp server: one big server serves thin clients.

or 
set up thick clients but the user's home are on NFS (on the server)

---

### Post by nandugopan on 2010-02-08
Thanks bluefrog..I think the second option is what we are looking for. Maybe have the home on the local machine, but have a file hosting directory on the server...Thanks again
:P

---

### Post by nandugopan on 2010-02-09
Okay, the NFS is setup and we are able to mount any individual directory. We are planning to have the students do user logons locally to the system. Then they need to be able to access their personal file accounts on the server. But, obviously this has to be done using some authentication. It should be that person A should not be able to delete person B's files.Any idea how we can go about doing this? I did some Googling and came up with the name Kerebros and some info on how to get it running. The students are not exactly linux buffs, so it would be nice if we could have a mount like a drive icon on the desktop, which they can mount with their password..Can any of you guys provide any guidelines on doing this?
Thanks in advance.

---

### Post by amac777 on 2010-02-09
One way is to create an LDAP server (installed on your server) to hold all the user information including their user number, groups, and password. Then configure all the client's to use this LDAP server for authentification at login and to mount the NFS file system in fstab. The result will be users can login with the same username/password at any computer in the lab and access their own files on the NFS directory. Also, you will only have to manage one copy of the username/passwords on the server.

Here's some information on setting up a LDAP server:
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

Here's some information on setting up clients to user LDAP:
[http://linuxadministration.us/2008/05/17/ubuntu-804-hardy-ldap-client/](http://linuxadministration.us/2008/05/17/ubuntu-804-hardy-ldap-client/)

I have done this before just as a learning excersise but found managing the usernames/passwords a bit awkward. I think there are some graphical tools to make it easier so maybe somebody with some more experience could help.

---

### Post by nandugopan on 2010-02-10
Thanks amac777...):P...The LDAP option looks good, but then the awkwardness is a cause of worry. For students who are making the transition from Windows to open source, this may prove to be a major problem.

---

### Post by bluefrog on 2010-02-10
authentication in windows or linux is still authentication.

If there was no authentication before they will have to learn. (anyway they would have to learn authentication with windows also, so...).

otherwise it is transparent for them, they enter a login/passwd and here they go

---

### Post by amac777 on 2010-02-10
> **nandugopan said:**
> Thanks amac777...):P...The LDAP option looks good, but then the awkwardness is a cause of worry. For students who are making the transition from Windows to open source, this may prove to be a major problem.

I meant it was a little awkward for the administrator to add new users and delete old ones. I was doing it manually and just assigning user numbers in order and never reusing old ones and that seemed to be working well. But I suspect if you poke around in the repositories you should be able find some really nice web or graphical based administrator tools for LDAP so you don't need to do everything manually.

---

### Post by nandugopan on 2010-02-11
Guys, thanks for the inputs.Yes there seems to be some good GUIs available..will check these out and get back to you.Cheers!

---

