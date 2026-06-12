---
title: "Uploading files from a Windows"
date: 2007-08-27
forum: Server Platforms
---

### Post by Kinboi on 2007-08-27
I am a complete nub here.. I installed the LAMP server and I have setup access to MYSQL from Win machine. 

I need to upload 2 PHP pages to Apache server and I am thinking what would be the easiesr way so I do not have to install a lot of software.. do I need to install FTP server for that?  I think Samba might be overkill.. I have no Floppy drive only CD.. 
 
what would be the simplest way to do it?

thank you

---

### Post by koenn on 2007-08-27
> **Kinboi said:**
> 
I need to upload 2 PHP pages to Apache server and I am thinking what would be the easiesr way so.. 
 
what would be the simplest way to do it?
carry them over on a USB stick

---

### Post by freebeer on 2007-08-27
In the long term, you'll probably want an FTP server.  That's the easiest way to repeatedly update pages to a remote machine.  Web authoring tools expect (generally) to use FTP to update pages.

---

### Post by nix4me on 2007-08-27
A more secure alternative to FTP is using SSH.  Install an SSH server and just access and transfer.

nix4me

---

