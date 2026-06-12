---
title: "Domain server problem"
date: 2008-07-23
forum: Server Platforms
---

### Post by fira on 2008-07-23
Hello

I have a problem setting up my home server. I have exactly followed tutorial [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760) (I have only changed domain name, passwords,...).
Files on server will be accessed mostly by windows XP clients. But when I want to join domain (and I provide username and password which exist in OpenLDAP user data base) I get error message:

<quote>
The following error occured attempting to join domain "server":
The network path was not found
<\quote>

If I want to access network workgroup (named "Server") I get:

<quote>
Server is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found.
<\quote>

I can access my server if I type in address bar:

\\servers_ip              or
\\fira.server.local      (hostname)

Command "net use ..." also works.

nslookup fira.server.local gives me:

*** Can't find server name for address 192.168.13.32: Non-existent domain
*** Default servers are not available
Server:  UnKnown
Address:  192.168.13.32

Name:    fira.server.local
Address:  192.168.13.32

I have tried many solutions to the similar problems given on this forum but none have worked.

Thank you

---

### Post by freebeer on 2008-07-23
Are these clients XP Pro, or XP Home Edition?  I know that the Home version has been hobbled by MS so that it can't join a domain.  There's a work-around for it, I believe.

---

### Post by fira on 2008-07-24
All clients are XP Pro.

---

