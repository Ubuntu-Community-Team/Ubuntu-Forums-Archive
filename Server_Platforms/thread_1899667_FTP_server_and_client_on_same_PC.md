---
title: "FTP server and client on same PC"
date: 2011-12-24
forum: Server Platforms
---

### Post by 333ameeth on 2011-12-24
I am new to ubuntu as well as server and client programming 
I want to send and receive files from/to server and client. But i have only on Computer, and i had installed proftpd server. i had created proftpd server now need to create client also, and i dont know how to create it.
Is it possible to create server as well as client on single Computer? and perform File transfer(FTP) operations.
while installing proftpd server i followed this link:[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
(from step-1 to step-4)

please help me.
thanks in advance.

---

### Post by Lars Noodén on 2011-12-24
> **333ameeth said:**
> 
I want to send and receive files from/to server and client.

Two things:

First, in that case it would be recommendable to [stop using FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) because [FTP is inherently insecure](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).  It is the protocol itself and not any of the programs that is the problem, so it's not something that is fixable.  In short, it would be  a good idea to uninstall the FTP server.

Second, fortunately FTP is replaceable by [SFTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SSH_File_Transfer_Protocol_.28SFTP.29), which is a newer protocol designed from the ground up to be secure.  It has the same functionality as FTP, but is very secure.  You can get it by installing the package OpenSSH-Server.  You can connect to it from your desktop using SFTP clients like Nautilus, Konqueror, Dolphin and FileZilla.

---

