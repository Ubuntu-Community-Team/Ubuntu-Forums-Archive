---
title: "Vsftpd PASV problem."
date: 2012-02-06
forum: Server Platforms
---

### Post by P.T. on 2012-02-06
Hello,

I have a problem with a passive FTP server. When I connect, it goes all the way through to the PASV command which looks like this in the terminal:
---> PASV

Usually, there comes a line after that one with 227: ip.port. But it doesn't. Not in Filezilla, not in the terminal.
When I look in Wireshark however, the 227 does reach me and contains the right information. How is this possible? There is no firewall blocking that I'm aware of. Server side, the port does open up (checked with netstat and nmap). Client side, I receive the right information, although none of the FTP clients shows the response.
Can this have any to do with the fact that the server is virtual or with the provider blocking something?

By the way, the IP address returned by the server is correct, not an internal one.

---

