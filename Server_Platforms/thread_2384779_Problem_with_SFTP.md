---
title: "Problem with SFTP"
date: 2018-02-12
forum: Server Platforms
---

### Post by am.steen on 2018-02-12
I trying To install SFTP server on ubuntu but it gives me 
an error when connect

I follow this link to install **[COLOR=#ff0000][FONT=Arimo]mysecureshell[/FONT][/COLOR]**
[http://www.ubuntugeek.com/install-and-configure-sftp-server-on-ubuntu-16-04-xenial-xerus-server.html](http://www.ubuntugeek.com/install-and-configure-sftp-server-on-ubuntu-16-04-xenial-xerus-server.html)

But when I try to connect from my switch for config backup
I get the following error:-

[COLOR=#0000ff]configFabric1:admin> configupload[/COLOR]
Protocol (scp, ftp, sftp, local) [ftp]: sftp
Server Name or IP Address [host]: 172.30.7.148
User Name [user]: steen
Path/Filename [<home dir>/config.txt]:
Section (all|chassis|switch [all]):
**[COLOR=#ff0000]configUpload not permitted (sftp failed).[/COLOR]**
**[COLOR=#ff0000]Terminated[/COLOR]**
[COLOR=#0000ff]Fabric1:admin>

[/COLOR][COLOR=#000000]My device is hp fabric switch[/COLOR][COLOR=#0000ff]

[/COLOR][COLOR=#000000]I try to use windows sftp client and it connects after 
giving an error about key and I click update[/COLOR][COLOR=#0000ff]

[/COLOR][COLOR=#000000]Can you help please ??[/COLOR][COLOR=#0000ff][/COLOR]

---

### Post by wildmanne39 on 2018-02-12
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by LHammonds on 2018-02-12
I have not used SecureMyShell so I don't have practical knowledge for your situation.

When I researched FTP options long ago, I ended up going with a package that has a long history.  Very Secure FTP Daemon (vsftpd).  I then wrote down [how I implement vsftpd on Ubuntu Server 16.04]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=228"). 

If you cannot get SecureMyShell to work, give vsftpd a try.

LHammonds

---

### Post by am.steen on 2018-02-12
Thanks very much for your concern but I check your link it is for
FTP server there is nothing about SFTP Server

---

### Post by LHammonds on 2018-02-12
> **am.steen said:**
> Thanks very much for your concern but I check your link it is for
FTP server there is nothing about SFTP Server
It is FTP over SSL known as FTPS.  The other secure FTP option is SSH FTP (SFTP).  Mine covers SSL variation.

---

### Post by am.steen on 2018-02-12
Ok Thanks I will try it 

One note when I try to connect to [COLOR=#000000]SecureMyShell  server that I made before 
[/COLOR]With WinSCP from windows machine it connects good and I can transfere 
Files.

But the problem with the swtich - I think it is a finger print key

---

### Post by TheFu on 2018-02-12
Remove whatever you have. That link seems like the hard way to me.

```
sudo apt install openssh-server fail2ban
```

That enables ssh, scp, sftp using the default version included with openssh.  No other packages necessary.  Config options are nearly endless in /etc/ssh/ and ~/.ssh/ but the defaults aren't too bad.
Installing fail2ban stops brute force attacks on port 22/tcp for 5-10 minutes. It is configurable - I think I block for 7-30 days, since I use ssh-keys for everything, mistyping passwords just doesn't happen.

Use **ssh-keygen** to make client keys.
Use **ssh-copy-id** to push public keys to the remote systems you want to access.

I've never understood why people use some other tool when we all need ssh anyways.  Every FTP project team has had security issues that lasted months in the past.  Reading a little on the differences between sftp vs ftps convinced me to always use sftp instead.  

Your requirements might not be the same as mine. They might align more with LHammons is is highly respected around here, BTW.

---

