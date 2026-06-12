---
title: "ftp server refusing connections"
date: 2006-09-24
forum: Server Platforms
---

### Post by dkline on 2006-09-24
I am using ProFTP on a LAMP server with Webmin to admin the server.  When I try to connect to the server I get a connection refused message on the client side.  How do I troubleshoot this?  I created an ftp user and group, but the client is never prompted for username and password, just the connection refused message.

---

### Post by kidders on 2006-09-24
Hi there,

"Connection refused" really only ever means one thing. The computer you are trying to connect to is not listening on the applicable port.

Things to check:

[LIST]
[*]Is your FTP server running at all?
[*]Is it bound to a network interface with external access?
[*]Is your firewall blocking incoming connections?
[/LIST]

---

### Post by dkline on 2006-09-25
yes it was a networking issue.  I have my client and server running in as VM workstations and they were sharing an IP address.  I took me disabling VMwares DHCP server and setting up a static address for each system. Once that was done it worked like a charm.  Thanks for the help.

---

