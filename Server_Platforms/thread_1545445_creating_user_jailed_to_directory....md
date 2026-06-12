---
title: "creating user jailed to directory..."
date: 2010-08-03
forum: Server Platforms
---

### Post by MyBIOS on 2010-08-03
I am trying to set up a directory on my external that is connected to my server that my friends ( who are in a band ) can upload files and download to, but to which they're jailed.  I want them to be able to read and write and create more directories if needed.  Any pointers or links?

---

### Post by Bachstelze on 2010-08-03
> **MyBIOS said:**
> I am trying to set up a directory on my external that is connected to my server that my friends ( who are in a band ) can upload files and download to, but to which they're jailed.  I want them to be able to read and write and create more directories if needed.  Any pointers or links?

Either FTP or SFTP would work.  SFTP is generally easier to set up, but would also allow them to log in (unless you use something like rssh).  FTP doesn't have that "problem" sine its sole purpose is to transfer files, but it's a bit more complicated to set up, especially if you're behind a router.

---

### Post by MyBIOS on 2010-08-03
I'm sorry, I should have been more thorough :)

I have sftp set up and running perfectly through my admin account, and I've attempted to create a share like the one I was talking about, but when I try to connect through Filezilla it connects, sends the password and then then an error message:

Status:	Connecting to 75xx.xx.xx...
Response:	fzSftp started
Command:	open "tptp@75.xx.xx.xx" 22
Command:	Pass: **********
Error:	Connection reset by peer
Error:	Could not connect to server

I have made sure that the password and everything is correct and it seems to me like it is accepting it but getting booted by my server right after login. 

In the process of doing this I made a username called 'tptp' but can't remember what I had instantiated in the configuration file.  I fear that I'll have to wipe my ssh drivers and reinstall and reconfigure everything again

---

### Post by MyBIOS on 2010-08-03
I am using Filezilla 3.3.3 and I've read that v.3 has problems with this but v.2 does not.  Suggest I use it?  Or any other advice?

---

### Post by MyBIOS on 2010-08-04
Also, I am logged on as the admin on the server constantly, would that be why it's not letting me acces the server through another local username while it's logged in as the admin username?

---

### Post by MyBIOS on 2010-08-04
I guess a better desription is...

I have a server for my home, I have Samba up and running so I can access it on my home network and VSFTP so I can remotely access it through Filezilla.  I wanted to make a directory on the external that is connected to my server that my friends can access to download and upload files of their music and make other directories inside as well.  Would I have to jail a user for that at all?  Or is there someway I can have a separate VSFTP username and password for them that is restricted to reading and writing to the directory and all of the subdirectories of a specified path?

---

### Post by MyBIOS on 2010-08-04
Bump yo

---

### Post by Bachstelze on 2010-08-04
Does it work if you just do

```
sftp tptp@...
```

from a terminal?

---

### Post by MyBIOS on 2010-08-04
Nope :'(  I tried with a wrong password also to make sure I had the right one and this is what I got


user-macbook:~ user$ sftp [email]tptp@75.xx.xx.xx[/email]
Connecting to 75.xx.xx.xx...
[email]tptp@75.xx.xx.xx[/email]'s password: 
Connection closed
user-macbook:~ user$ sftp [email]tptp@75.xx.xx.xx[/email]
Connecting to 75.xx.xx.xx...
[email]tptp@75.xx.xx.xx[/email]'s password: 
Permission denied, please try again.
[email]tptp@75.xx.xx.xx[/email]'s password: 
Permission denied, please try again.
[email]tptp@75.xx.xx.xx[/email]'s password: 
Permission denied (publickey,password).
Connection closed
user-macbook:~ user$ 

I can still connect using my admin username through terminal and filezilla.  When trying to connect with filezilla under 'tptp', I get exitcode 255 and CSftpControlSocket::ResetOperation(66), here's the log...

Status:	Connecting to 75.xx.xx.xx...
Trace:	Going to execute /Applications/FileZilla.app/Contents/MacOS/fzsftp
Response:	fzSftp started
Trace:	CSftpControlSocket::ConnectParseResponse(fzSftp started)
Trace:	CSftpControlSocket::SendNextCommand()
Trace:	CSftpControlSocket::ConnectSend()
Command:	open "tptp@75.xx.xx.xx" 22
Trace:	Server version: SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
Trace:	Using SSH protocol version 2
Trace:	We claim version: SSH-2.0-PuTTY_Local:_Jun_13_2010_23:25:08
Trace:	Doing Diffie-Hellman group exchange
Trace:	Doing Diffie-Hellman key exchange with hash SHA-256
Trace:	Host key fingerprint is:
Trace:	ssh-rsa 2048 xx:xx:xx:xx:xx:xx:xx:xx:xx
Trace:	Initialised AES-256 SDCTR client->server encryption
Trace:	Initialised HMAC-SHA1 client->server MAC algorithm
Trace:	Initialised AES-256 SDCTR server->client encryption
Trace:	Initialised HMAC-SHA1 server->client MAC algorithm
Trace:	Pageant is running. Requesting keys.
Trace:	Pageant has 0 SSH-2 keys
Command:	Pass: **********
Trace:	Sent password
Trace:	Access granted
Trace:	Opened channel for session
Trace:	Started a shell/command
Status:	Connected to 75.xx.xx.xx
Trace:	Server sent command exit status 255
Error:	Connection closed by server with exitcode 255
Trace:	CSftpControlSocket::ResetOperation(66)
Trace:	CControlSocket::ResetOperation(66)
Error:	Could not connect to server

I have checked the Filezilla forums and was going to post there, but they wouldn't let me use my Google account and they were abdicating responsibility for similar problems to pUTTY without trying to give insight or much help at all.  In short I didn't feel like registering and dealing with **** faces there, the help here is much better!

I am still dumb founded at why this is not working for me!

---

### Post by Vegan on 2010-08-05
I use vsftp which has been no problem for me.

---

### Post by MyBIOS on 2010-08-05
That's what I've been using and I finally got it able to connect!  Now the problem is that the user isn't chrooted to the directory that I specified, they have access to '/' on the whole server.  Any suggestions with that?

---

### Post by MyBIOS on 2010-08-05
So I have the user rooted to /home/TPTP.  I wanted to make it so they have read and write access to a directory on an external hdd that I have connected to my server.  I went into System>Administration>Users and Groups and set the TPTP users home directory to /media/swag/Bands/TPTP and also made the chroot directory in the sshd_config file to /media/swag/Bands/TPTP.  It still only allows the user to read and write from their /home directory.  How can I change that?

---

