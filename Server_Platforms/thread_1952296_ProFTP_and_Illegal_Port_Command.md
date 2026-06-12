---
title: "ProFTP and Illegal Port Command"
date: 2012-04-04
forum: Server Platforms
---

### Post by ernieg92 on 2012-04-04
I'm running Ubuntu Server 10.04.1 and ProFTP 1.32 with a basic configuration.  My server sits behind a DSL modem that is NOT running a firewall.  The server has a real IP address and is not NAT'd.  My home network sits behind a Linux firewall (IPFire) which also has a real IP address; workstations have private IP addresses.

I can use either the CLI or a GUI to log into the server.  However, when I try to get a directory listing via CLI, I receive a "500 Illegal PORT command ftp: bind: Address already in use" error.  On the GUI, as soon as the directory command is sent (MDLS) after login the connection is closed.

I've tried both enabling and disabling ephemeral ports to bypass any firewall issues, but that doesn't help.

Any insight on where the problem may be?  Thanks.

---

### Post by arrrghhh on 2012-04-04
a) Are you sure your DSL provider allows traffic inbound to port 21?
b) How are you hitting this server?  You say CLI and GUI, but does that mean from the local machine, from a machine on your LAN, over the WAN...?  I'm leaning towards the WAN since you mention the DSL at all.  If that's the case, does the FTP server work locally?  Are you hitting it via IP or DNS friendly name?
c) I assume the server is behind the IPFire h/w firewall?  Have you tried placing the server outside of this firewall?

---

### Post by ernieg92 on 2012-04-04
> **arrrghhh said:**
> a) Are you sure your DSL provider allows traffic inbound to port 21?
b) How are you hitting this server?  You say CLI and GUI, but does that mean from the local machine, from a machine on your LAN, over the WAN...?  I'm leaning towards the WAN since you mention the DSL at all.  If that's the case, does the FTP server work locally?  Are you hitting it via IP or DNS friendly name?
c) I assume the server is behind the IPFire h/w firewall?  Have you tried placing the server outside of this firewall?

Thanks for the quick reply! To answer your questions,

a) Yes port 21 traffic is allowed 
b) I'm hitting the server from both the LAN and the WAN, via DNS
c) The server is NOT behind the h/w firewall. The server and the firewall sit parallel to each other behind the modem (LAN I'm configuring/testing server from is behind firewall).

After a little more troubleshooting, I've determined the problem is with the Ubuntu Linux implementation of ftp.

Originally, on the server I had set the "TLSRequired" option to "yes" but for the sake of troubleshooting I changed it to "no".  Now, I can use a Windows GUI FTP client either unsecure or via SSL (client connects using the AUTH TLS request) and all works as expected.  I can use the Windows CLI to FTP unsecure and it works fine.

However, when I try and use the Linux CLI (either ftp or ftp-ssl), I cannot pull a directory listing.  I then noticed that, despite using the ftp command, there is an ftp package in the repository.  I install that and now I can pull a directory listing via CLI.  However, this particular package conflicts with and removed ftp-ssl package.  So, from the CLI, I'm operating unsecure (which is fine).  I've tried a couple of Linux FTP GUI (Filezilla & kFTP) and neither one can connect AUTH TLS (or explicit SSL).  Both work fine with unsecure (plain) FTP.  First time I've ever seen Windows do a basic function better than Linux!

---

### Post by arrrghhh on 2012-04-05
FTP isn't secure.  You need FTPS or SFTP.  FTPS is difficult to setup, SFTP is pretty simple.

Please use the "Thread Tools" drop-down menu and mark this thread [SOLVED] if you feel it is ;).

---

### Post by ernieg92 on 2012-04-05
> **arrrghhh said:**
> FTP isn't secure.  You need FTPS or SFTP.  FTPS is difficult to setup, SFTP is pretty simple.

Please use the "Thread Tools" drop-down menu and mark this thread [SOLVED] if you feel it is ;).

I found the problem.  The Linux FTP clients (at least FileZilla and kFTP) use client-initiated SSL renegotiations.  The TLS module within ProFTPd does not allow those (though an admin can overide) due to vulnerabilities with that process.

FTP **can** be made secure with SSL, but there are better choices (like SSH). I guess for my anonymous FTP I'll leave well enough alone and use SSH when secure file transfers need to be made.

Thanks for your help!

---

### Post by arrrghhh on 2012-04-05
> **ernieg92 said:**
> FTP **can** be made secure with SSL, but there are better choices (like SSH). I guess for my anonymous FTP I'll leave well enough alone and use SSH when secure file transfers need to be made.

Yup, I said FTPS (SSL over FTP) or SFTP (SSH really).

Glad you got it sorted out.

---

### Post by ernieg92 on 2012-12-08
> **ernieg92 said:**
> I found the problem.  The Linux FTP clients (at least FileZilla and kFTP) use client-initiated SSL renegotiations.  The TLS module within ProFTPd does not allow those (though an admin can overide) due to vulnerabilities with that process.


Although this was marked Solved, I'm adding an update as it was originally only ½ solved (by using my ftp server only for simple anonymous connections). 

I now have solved it fully.  After connecting via TLS, I must switch to passive mode (thought originally that was automatic).  I can now connect via TLS to my /home directory on the server, when necessary.

Don't know if that helps anyone else (I seem to create my own problems) but it solved my problem.

---

