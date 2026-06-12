---
title: "Port forwarding/firewall and ftp server (which ports to let through)"
date: 2007-10-28
forum: Server Platforms
---

### Post by kentl on 2007-10-28
I've [installed an FTP-server using pure-ftpd]("http://ubuntuforums.org/showthread.php?t=594335"), and it works great, internally. Now I want my users to be able to access it through internet, I've got a Linksys router with [dd-wrt]("http://ubuntuforums.org/showthread.php?t=569293").

I have set up port forwarding according to this figure:
```

router          servercomputer
 port              port
4521 ------------> 4521

```

I have my FTP server listen on port 4521 instead of the normal 21. This doesn't work. I need to forward something else. Any ideas?

---

### Post by MJN on 2007-10-29
FTP uses two ports - the data one of which depends on whether you're using passive or active connections. Check out [http://www.slacksite.com/other/ftp.html](http://www.slacksite.com/other/ftp.html) for an excellent overview of the issue you face.

Do you really need FTP? What is it you're trying to achieve?

Mathew

---

### Post by kentl on 2007-10-29
Thanks, I'll check out the link. I need FTP as I'll be using my computer as a file server for various clients. And FTP is widely supported, more so than SFTP or FTP over TLS/SSL.

---

### Post by kentl on 2007-10-29
I liked that page, thanks!

I'm half way there now! I've gotten ACTIVE ftp working, now **I'm looking into getting PASSIVE ftp working as well. As I need to support both.**

Here's what I've done.

To get ACTIVE ftp working I setup routing as follows:
```

*router*              *server*
4521:TCP -----------> 4521:TCP
4520:TCP -----------> 4520:TCP

```
It was enough to get it working, the page described it quite well.

To get PASSIVE ftp working, I've tried doing this without success:

I limit my FTP server to use port 40000--43000 for the passive connections. As I use pure-ftpd I used the -p 40000:43000 switch**[SIZE="4"]*[/SIZE]** for that (through the wrapper but it's unimportant).

I added some routing to forward these ports as well:
```

       *router*              *server*
       4521:TCP -----------> 4521:TCP
       4520:TCP -----------> 4520:TCP
40000-43000:TCP -----------> 40000-43000:TCP

```

What happens when I try to connect using a PASSIVE connection with  the FileZilla client is that it hangs after the LIST command:
```

Status:	Connecting to myowndomain.com:4521 ...
Status:	Connected with myowndomain.com:4521. Waiting for welcome message...
Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 1 of 10 allowed.
Response:	220-Local time is now 00:53. Server port: 4521.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER ftpuseraccount
Response:	331 User ftpuseraccount OK. Password required
Command:	PASS **********
Response:	230-User ftpuseraccount has group access to:  1001    
Response:	230-OK. Current directory is /
Response:	230 27414 Kbytes used (0%) - authorized: 307200000 Kb
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Extensions supported:
Response:	 EPRT
Response:	 IDLE
Response:	 MDTM
Response:	 SIZE
Response:	 REST STREAM
Response:	 MLST type*;size*;sizd*;modify*;UNIX.mode*;UNIX.uid*;UNIX.gid*;unique*;
Response:	 MLSD
Response:	 TVFS
Response:	 ESTP
Response:	 PASV
Response:	 EPSV
Response:	 SPSV
Response:	 ESTA
Response:	 AUTH TLS
Response:	 PBSZ
Response:	 PROT
Response:	 UTF8
Response:	211 End.
Command:	OPTS UTF8 ON
Response:	200 OK, UTF-8 enabled
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is your current location
Command:	TYPE A
Response:	200 TYPE is now ASCII
Command:	PASV
Response:	227 Entering Passive Mode (192,168,1,99,161,97)
Command:	LIST
          <!-- It hangs here and stays "forever". / Posters comment -->

```



**[SIZE="4"]*[/SIZE]** How the option is described in the [pure-ftpd README]("http://download.pureftpd.org/pub/pure-ftpd/doc/README"):
```
- '-p <first port>:<last port>': Use only ports in the range <first port>
to <last port> inclusive for passive-mode downloads. This is especially
useful if the server is behind a firewall without FTP connection tracking.
Use high ports (40000-50000 for instance), where no regular server should be
listening.
```

---

### Post by kentl on 2007-10-29
FileZilla were to blame! :lolflag: Turns out upgrading the FileZilla client to the latest version got rid of the problem.

---

