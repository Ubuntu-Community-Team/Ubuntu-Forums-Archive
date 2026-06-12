---
title: "Ubuntu 9.04 Server problem with FTP/SSL/TLS"
date: 2009-11-05
forum: Server Platforms
---

### Post by ac14112 on 2009-11-05
I'm kinda new to linux and really new at setting up a server. I've been learning stuff as I go along. I've run into a problem with setting up my FTP server. I'm using vsftpd and I got it working fine without SSL encryption and using local accounts to log in. When I enable SSL however, I'm able to login, but it won't even show a directory listing.

I've tried this with the firewall on both the server and client machines disabled.

These are the options I enabled in my /etc/vsftpd.conf file

```
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
debug_ssl=YES
rsa_cert_file=/etc/vsftpd2.pem
rsa_private_key_file=/etc/vsftpd2.pem
```


I created my certificate with this command:

```
openssl req -x509 -nodes -days 7300 -newkey rsa:2048 -keyout /etc/vsftpd2.pem -out /etc/vsftpd2.pem
```

These are some errors I'm getting in the log file (/var/log/vsftpd.log):

```
Thu Nov  5 14:07:13 2009 [pid 5678] [username] DEBUG: Client "X.X.X.X", "SSL shutdown state is: NONE"

Thu Nov  5 14:07:13 2009 [pid 5678] [username] DEBUG: Client "X.X.X.X", "SSL shutdown state is: SSL_SENT_SHUTDOWN"

Thu Nov  5 14:07:14 2009 [pid 5678] [username] DEBUG: Client "X.X.X.X", "SSL version: TLSv1/SSLv3, SSL cipher: DES-CBC3-SHA, not reused, no cert"

Thu Nov  5 14:07:14 2009 [pid 5678] [username] DEBUG: Client "X.X.X.X", "SSL ret: 0, SSL error: error:00000000:lib(0):func(0):reason(0), errno: 104"

Thu Nov  5 14:07:14 2009 [pid 5678] [username] DEBUG: Client "X.X.X.X", "SSL_accept failed: error:00000000:lib(0):func(0):reason(0)"
```


I've tried connecting using FireFTP (a Firefox addon) and Filezilla.


Log from FireFTP:

```
220 Welcome to My FTP service.
       AUTH TLS
234 Proceed with negotiation.
       PBSZ 0
200 PBSZ set to 0.
       USER username
331 Please specify the password.
       PASS (password not shown)
230 Login successful.
       CWD /
250 Directory successfully changed.
       TYPE A
200 Switching to ASCII mode.
       PASV
227 Entering Passive Mode (X,X,X,X,114,242)
       LIST
```

Log from Filezilla:

```
Status:	Connecting to X.X.X.X:21...
Status:	Connection established, waiting for welcome message...
Response:	220 Welcome to My FTP service.
Command:	AUTH TLS
Response:	234 Proceed with negotiation.
Status:	Initializing TLS...
Status:	Verifying certificate...
Command:	USER username
Status:	TLS/SSL connection established.
Response:	331 Please specify the password.
Command:	PASS *********
Response:	230 Login successful.
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 AUTH SSL
Response:	 AUTH TLS
Response:	 EPRT
Response:	 EPSV
Response:	 MDTM
Response:	 PASV
Response:	 PBSZ
Response:	 PROT
Response:	 REST STREAM
Response:	 SIZE
Response:	 TVFS
Response:	 UTF8
Response:	211 End
Command:	OPTS UTF8 ON
Response:	200 Always in UTF8 mode.
Command:	PBSZ 0
Response:	200 PBSZ set to 0.
Command:	PROT P
Response:	200 PROT now Private.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (X,X,X,X,86,4)
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```


If any more info is required, let me know.

---

### Post by awclemen on 2009-11-05
You might need to adjust your vsftpd.conf to contain only this:

```
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=YES

ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

rsa_cert_file=/etc/vsftpd2.pem
```

remember to restart:
```
/etc/init.d/vsftpd restart
```

I got this from here:
[http://www.brennan.id.au/14-FTP_Server.html](http://www.brennan.id.au/14-FTP_Server.html)

hope it helps!

---

### Post by ac14112 on 2009-11-06
Thanks for the suggestion, but that didn't work. I still can't connect with TLS.

Anyone else have any suggestions or know anything more about SSL?

Any help would be greatly appreciated.

---

### Post by Lars Noodén on 2009-11-07
Why FTP/SSL/TLS and not SFTP/SSH ?

---

### Post by ac14112 on 2009-11-10
Like I said, I'm kinda new at this, but what's the difference? 

I'm not trying to SSH into the server at this point, I just want the SSL that I set up on the FTP server to work.

If there is a better way to do secure FTP, I'd be willing to try it.

---

### Post by ac14112 on 2009-11-12
I decided to just use SSH/SFTP. Thanks for the help though. If anyone else is having similar problems, feel free to continue the thread.

---

### Post by Lars Noodén on 2009-11-17
> **ac14112 said:**
> 
If there is a better way to do secure FTP, I'd be willing to try it.

FTP over SSL is known as FTPS and that's about as close as you will get to securing it.  
[http://searchsecurity.techtarget.com/news/article/0,289142,sid14_gci1363108,00.html](http://searchsecurity.techtarget.com/news/article/0,289142,sid14_gci1363108,00.html)

Plain FTP is very good for public, read-only downloads, aka Anonymous FTP.  

If you want uploads, then SFTP is not only far easier to set up but much more secure.

---

### Post by ac14112 on 2009-11-17
Thanks for the info. I don't need public ftp, just private upload and download for a few people, so I'll use SFTP.

---

