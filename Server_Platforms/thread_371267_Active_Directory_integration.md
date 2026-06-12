---
title: "Active Directory integration"
date: 2007-02-26
forum: Server Platforms
---

### Post by mahohmei on 2007-02-26
I just installed 6.06 Server, and then ran the commands to install Squid, sshd, and samba. This box is intended to be nothing but a Squid caching server--normal users will not be logging into it, and for that matter, won't even know it exists.

I installed sshd so I can ssh into it and work on it without making the trek to the server room--cool.

Our school district has a districtwide Windows Server 2003 domain I'd like to integrate it with in such a manner:

- Give AD groups (for example, "SCHOOLS\Domain Admins" and "SCHOOLS\LEONNetAdmins") permission to log onto that server and be sudoers.

- Allow no other users to log on.

This way, if a domain admin at the district office needs to do something to my server, I can just say "ssh to 10.20.5.250 and use your domain credentials"

Can someone point me the right way with this?

Thanks!

Matt Hohmeister
Technology Coordinator
Leon High School
Tallahassee, FL

---

### Post by jonathan.lees on 2007-02-27
You can join your Ubuntu Server as a member server to your active directory domain, this will allow your AD users to sign on to the Ubuntu server. Personally I've not configured security on Ubuntu using AD groups, but the following thread states:

Once an Ubuntu Samba server is integrated with Active Directory, share level and file level permissions can be set using the AD users and groups without requiring local account mapping.

See this thread on joining your Ubuntu server to your AD domain:

[http://www.ubuntuforums.org/showthread.php?t=280702](http://www.ubuntuforums.org/showthread.php?t=280702)

---

