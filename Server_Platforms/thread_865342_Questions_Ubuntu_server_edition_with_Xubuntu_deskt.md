---
title: "Questions: Ubuntu server edition with Xubuntu desktop"
date: 2008-07-20
forum: Server Platforms
---

### Post by UncleAelfrich on 2008-07-20
I have installed Ubuntu Server edition then installed Xubuntu desktop (sudo apt-get install xubuntu-desktop). [NOTE: Please, no flames re: GUI with server. I have built this as a home media server. Two users with perhaps enabling in the future ftp access.] [FURTHER NOTE: With the problems with Windows Media Server, I would think that a linux version would be ideal; however, MOST people will not want to undergo the literally HOURS of time learning linux and ubuntu to the point of building a media server from the command line.]

Everything seems to work now. I have access to the files. I can print from a windows client to a samba printer. I have "security = user" enabled, but not LDAP, or SAMBA as the PDC, or network logons, etc. Perhaps at some future date I might try to implement these.]

As way of added information, I have been using openSSH to work on the server using Putty from my Windows Vista machine.

Now for my TWO QUESTIONS:

ONE: I have seen discussions regarding increased security risks by running a GUI, in my case, Xubuntu, in a server. Considering mine is a home based server, what are the realistic security risks I have by running Xubuntu on top of my server install?

TWO: I intend to purchase a tape drive and do tape backups of my home network (server plus two windows clients) using Bacula. Will there be a conflict/difficulty between Bacula running at the same time as Xubuntu?

Thank you for your help.

---

### Post by sadara on 2008-07-20
1) Your server is no less secure than the millions of windows boxes out there, assuming that you have reasonable passwords and havn't enable any unneeded services. (That is with the understanding you are behind a firewall)

2) There will be no problem

---

### Post by UncleAelfrich on 2008-07-20
I am behind a router firewall along with NAT Mapped many one to one (Static IPs).

Thanks for your reply.

---

