---
title: "setup apache for home folders for http upload/download"
date: 2016-09-04
forum: Server Platforms
---

### Post by Vegan on 2016-09-04
I was wondering if ftp is not working then why not http, always an alternative

apache is the usual suspect

later i can modify it for web hosting but that is for later

---

### Post by TheFu on 2016-09-04
Apache is a web server, not an upload server.  

To support uploads, a web-app needs to be installed, configured, setup and secured.

---

### Post by Vegan on 2016-09-05
any suggests for uploads?

---

### Post by TheFu on 2016-09-05
> **Vegan said:**
> any suggests for uploads?

sftp.  ;)  Any Linux file manager will support it, just use sftp:// or ssh:// in the URL.
If you are coming from Windows, WinSCP or Filezilla can work too.  Or use the Putty sftp/scp client(s).  Or load cygwin and use the sftp/scp client that comes with it.

Lots-o-options.  sftp is extremely cross-platform.  Don't think there is a networked OS that doesn't have a good sftp client.

---

### Post by SeijiSensei on 2016-09-05
My preferred choice is sshfs whenever available.  The Dolphin file manager in KDE supports fish://server/share names and sets up an SSHFS connection to the server.  I use this to upload files to my remote web server all the time by dragging and dropping between Dolphin windows.

Another alternative is to set up a full-time SSHFS mount at boot.  I run commands like these in /etc/rc.local:
```
sshfs -o allow_other,nonempty ip.addr.of.server:/some/shared/directory   /some/local/mountpoint
```

I also have a server in my office that maintains a full-time[ OpenVPN static tunnel]("http://openvpn.net/static.html") to my remote servers.  Anything sent over these tunnels is automatically encrypted, even FTP :D

Uploading files is possible with Apache but not without additional software like [PHP's file uploading features]("http://php.net/manual/en/features.file-upload.php").  To make that secure, you need to use HTTPS.  In this case a self-signed certificate would be fine.

---

