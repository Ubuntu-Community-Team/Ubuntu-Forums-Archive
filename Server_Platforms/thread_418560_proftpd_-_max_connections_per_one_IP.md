---
title: "proftpd - max connections per one IP?"
date: 2007-04-22
forum: Server Platforms
---

### Post by maksym on 2007-04-22
I need to have a limit of  2 connections to my proftpd ftp server per 1 ip to prevent one person connecting too many times with programs like Download Accelerator. (for all anonymous )

My config file contains the following directive for anonymous users:

MaxHostsPerUser			30
MaxClientsPerHost 		2

I understand that this should tell server to limit the number of all connections from anonymous users to 30 and not allow any IP to have more than 2 connections at a time. But still I see many simultaneous RETR from 1 IP.

What am I doing wrong?

Thanks!

---

