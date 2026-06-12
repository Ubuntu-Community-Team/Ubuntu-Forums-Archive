---
title: "disabling Pure-ftpd banner"
date: 2007-09-18
forum: Server Platforms
---

### Post by dirac3000 on 2007-09-18
Hello,
I configured Pure-ftpd as a FTP server in my company site, as they needed an FTP server and this was quick and esay to configure. The only point they are not happy about now id the banner. After you connect, you see this message:

[FONT="Courier New"]
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-<<
220-*here my banner*
220->>
220-Local time is now 11:26. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Name (*here my login*): 
[/FONT]

I read the the only way to disable this banner should be to recompile the pure-ftpd wit the --without-banner option, and says that doing it it's useless for security. It doesn't matter much to me, the point is that I would like to put whatever banner my bosses want!
Is there any other way that you know without having to recompile it?

---

