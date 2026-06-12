---
title: "FTPd with simple unix-user authentication"
date: 2008-01-17
forum: Server Platforms
---

### Post by art0rz on 2008-01-17
Hello,

I recently began setting up a box as an Ubuntu server, I've succesfully setup apache, mysql, etc etc. But now I've stumbled upon a problem with the FTP server.

I need users to simply be able to log into the FTP server with their normal unix username and password (the same they use to log into the shell) to their own /home/ directory, without me having to add their username and password to some configuration file.

I've tried numerous FTP servers, but none offer a simple way of doing this, or at least do not properly document this.

If anyone has any experience with this, I would love to hear from them.

Regards,
art0rz

---

### Post by Dr Small on 2008-01-17
I use ProFTPd, and it works great for me.

---

### Post by HermanAB on 2008-01-17
Both Proftpd and Vsftpd should work right out of the box.  So if you followed some demented guide that you got off a random web site to install your FTP server, re-install it using Synaptic and this time, don't change the configuration - it should work right away.  All you need to do is start the service and enable it in the firewall.

Cheers,

Herman

---

