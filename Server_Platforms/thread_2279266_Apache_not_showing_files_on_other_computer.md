---
title: "Apache not showing files on other computer"
date: 2015-05-22
forum: Server Platforms
---

### Post by murdoch201 on 2015-05-22
Hi,

I'm having some difficulties with my Apache installation. I freshly installed both Apache and ProFTPd with Xampp, yet when i upload a file to the htdocs folder with ProFTPd it doesn't show up when browsing to the IP address of the server.
So:
- Files that are manually copy pasted on the Ubuntu server are shown when i browse from anywhere to it's IP.
- Files that are uploaded with ProFTPd (remote) can only be seen when i'm on the Ubuntu server, browsing to my own IP.

With IP i'm talking about local IP's, not external, so it's not a router firewall problem.
Theres no .htaccess file present in the htdocs folder.
ProFTPd is making use of virtual users (ftpasswd), files do upload sucessfully and also show up when browsing in-folder.

What am i doing wrong?

Thanks in advance,
Ben

---

### Post by bruce-hyatt on 2015-05-22
How are the permissions set on the files that you are having trouble accessing?

- Bruce

---

