---
title: "Secure FTP"
date: 2007-10-07
forum: Server Platforms
---

### Post by muzza4 on 2007-10-07
Hi there,

I have a server running Ubuntu Feisty Fawn, and I want some users to be able to transfer files to their home directory, and other users to be able to transfer files from their home directory.

I need the transfer to be secure, but I don’t know if this means I want sFTP, or FTP over SSH or what. The ftp software on my server is ProFTPD 1.3.0.

My users could be using any ftp client and I am not in a position to tell them to change (unless it doesn’t come with the secure functionality required).

Can anyone guide me in the right direction?

Thanks
Muzza

---

### Post by p_quarles on 2007-10-07
The OpenSSH server package includes sftp by default, and this is the most secure way to do what you are looking for. 

Many ftp clients support sftp. For those users who don't already have a supported client app, you can recommend the free, cross-platform FileZilla.

---

