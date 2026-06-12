---
title: "Setting up CrushFTP as Service (daemon)"
date: 2012-03-01
forum: Server Platforms
---

### Post by sonofpelican on 2012-03-01
Hello - please excuse a rookie question here but it seems that CrushFTP is lacking in the Linux documentation department.
 
I am running 10.11 and would like to know how to setup CrushFTP to run as a background service @ startup.
 
Many Thanks
 
-SOP-

---

### Post by Lars Noodén on 2012-03-01
I'd rethink the FTP part.  Unless there is some very specific and clear reasons to use FTP, I would go with SFTP instead.  If you can connect to the machine with SSH then you already have SFTP available and configured and don't need to do anything more. You can connect to SFTP via Nautilus, Dolphin and FileZilla. 

Here is some background reading on the issue, if that helps:

[list]
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*] [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[/list]

Unlike FTP, which is insecure and cannot be secured, SFTP is designed from the ground up to provide a secure connection.

---

### Post by sonofpelican on 2012-03-01
Thanks Lars, actually I am using SFTP/HTTPS on the server (including going so far as to use non-standard ports) which was fairly easy to setup. It's this whole starting up CrushFTP on bootup is what's driving me batty.
 
-SOP-

---

### Post by Lars Noodén on 2012-03-02
If you have SFTP can I ask why you would need FTP in addition?

---

