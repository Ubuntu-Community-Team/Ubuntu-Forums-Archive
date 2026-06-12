---
title: "Server FTP setup causes a timeout when connecting"
date: 2009-08-28
forum: Server Platforms
---

### Post by dougmorin on 2009-08-28
After configuring the server to accept FTP requests, after i try to connect via ftp with a valid username and password i get a server timed out when waiting for a directory listing.  I can guarantee it's something that i am doing, but i just don't know what i need to add to fix it.  I am using vsftpd.  I am also connecting to the server with FileZilla, and i have included the conversation with the server below.  Also, if you need me to display the vsftpd.conf file just let me know.

If anybody else knows any other ftp servers out there just let me know.

***** filezilla output *******
Status:	Resolving address of validurl.net
Status:	Connecting to xxx.xxx.xxx.xxx:21...
Status:	Connection established, waiting for welcome message...
Response:	220 Welcome to the Phoenix web server
Command:	USER validuser
Response:	331 Please specify the password.
Command:	PASS **********
Response:	230 Login successful.
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 EPRT
Response:	 EPSV
Response:	 MDTM
Response:	 PASV
Response:	 REST STREAM
Response:	 SIZE
Response:	 TVFS
Response:	 UTF8
Response:	211 End
Command:	OPTS UTF8 ON
Response:	200 Always in UTF8 mode.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/home/validuser"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (xxx,xxx,xxx,xxx,222,108)
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing
******************************

Thanks,

Doug

---

### Post by dougmorin on 2009-08-28
fyi, i removed ip's, url's, and usernames for obvious reasons

---

### Post by dougmorin on 2009-08-28
Nevermind, I was using the wrong level of IP address to connect to the server.  I changed it to the local 192.168 ip and it worked for me.

---

### Post by hessiess on 2009-08-29
Use SFTP inserted, Much more sccure and a better designed protocall which dousent require `jumping through hoops' to get it to work with modern networking technologies.

---

