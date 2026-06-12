---
title: "Encrypt FTP traffic"
date: 2009-12-04
forum: Server Platforms
---

### Post by Tsquad on 2009-12-04
Hello, i have an ftp server made with vsftpd on ubuntu 8.10 desktop version. Im wondering how i go about securing the traffic. Can anyone point me in the right direction please?

---

### Post by KiLaHuRtZ on 2009-12-04
Why not use SFTP?  Built right in with SSH.

---

### Post by Warren Watts on 2009-12-04
> **KiLaHuRtZ said:**
> Why not use SFTP?  Built right in with SSH.

That's what I use!  Works great for me!

---

### Post by Lars Noodén on 2009-12-04
> **Tsquad said:**
> Hello, i have an ftp server made with vsftpd on ubuntu 8.10 desktop version. Im wondering how i go about securing the traffic. Can anyone point me in the right direction please?

[openssh-server](http://packages.ubuntu.com/karmic/openssh-server) has a built-in sftp subsystem.  That will give you an encrypted way to transfer files easily.  SFTP is a new protocol, not FTP over SSL.  From a user perspective, it works like FTP with nice clients like filezilla, konqueror, dolphin, nautilus, cyberduck, or fugu.

OpenSSH is *very* flexible so if you need to work with keys, modify access for specific groups of users or other tricks, it can usually be done.

---

### Post by Tsquad on 2009-12-04
so vsftpd is not secure? iv read a few things that said it was and some say its not. If not ill have to switch it to sftp i guess.

---

### Post by falconindy on 2009-12-04
There's a big difference between using sftp and creating a secure ftp server.

OP, you may want to look at this:
[http://www.brennan.id.au/14-FTP_Server.html#secure](http://www.brennan.id.au/14-FTP_Server.html#secure)

---

### Post by zman121 on 2009-12-04
"secure" can mean different things.  The vsftp process is "secure" in that it's harder to penetrate your system if you use vsftp than if you use other ftp servers.  Last I knew, vsftp was the choice of many big ftp sites, like redhat.  As an application, vsftp  leaves Red Hat's servers less vulnerable than other ftp daemons.  That's the "Very Secure" part of it.


But that does NOT mean your data is secure from prying eyes while in transit.  For that, encrypted transmission (like sftp) are used.  

When you download an iso image from Red Hat, they don't care if someone sniffs the packets in transit.  What they want to prevent is someone using their ftp server process to execute malicious code on their server.

When a financial institution transmits a data file containing numbers, they DO care if someone sniffs the packets in transit and eavesdrops on the transmission.  So they use sftp or some other encryption method.

Hope this helps.

---

### Post by Lars Noodén on 2009-12-05
> **Tsquad said:**
> so vsftpd is not secure? iv read a few things that said it was and some say its not. If not ill have to switch it to sftp i guess.

As metioned by zman121, vsftpd is secure insofar as an ftp *server* goes.  In other words the program itself is fine.  

It is the protocol itself, FTP, which is the problem.  The data, passwords and username are all sent back and forth unencrypted by FTP.  Anyone on your subnet, the server's subnet or any subnet in between can 'sniff' the passwords and data when FTP is used.  

You can, with extra effort as falconindy pointed out, wrap FTP inside SSL or TLS, thus creating FTP**S**.  However, that is complex to do and far from an optimum solution. 

The **S**FTP protocol, in contrast, has been designed from the ground up to be as secure as possible for both login and data transfer.  

Unfortunately complex, nit-picky tasks, generate a lot of posts and then turn up in searches, whereas easy, relatively painless solutions vanish because it is rarely necessary to post how to do those.  Thus, IMHO, there is still talk about 'securing' FTP and little mention of using SFTP.  Pain == noise, noise == high Google ranking.  ;)



As mentioned, SFTP is built into openssh-server.  So for basic file transfer, you don't have to have anything more than an account on the machine with the ssh server.  

You can use GUI-based SFTP clients to transfer files: filezilla, konqueror, dolphin, nautilus, cyberduck, fugu, or fetch.  For example, in Konqueror, just type in the URL of the server.  
[indent]sftp://*xx.yy.zz.aa*[/indent]
where the server name or address is xx.yy...

Or you can use sshfs as an SFTP client.  It allows the other machine to be accessed via an open folder on your machine using any program you normally have to work with files, such as openoffice.org, inkscape or gimp.

---

