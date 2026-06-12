---
title: "Vsftpd not working over the internet"
date: 2006-03-27
forum: Server Platforms
---

### Post by Biffy on 2006-03-27
Im gonna try to explain this as good as i can. Ask questions if there is something you dont understand.

I am using vsftpd. Locally, i can connect to the server and transmit data. This is from my own computer. 

But when people on the internet is suppose to connect to it, nothing works. I want my friend to be able to connect to it via internet explorer. She connects, types in her username and password, and then, nothing happens. After a while the connection timeouts.

So i ask another friend, that is using a ftp-client. When he connects, he gets the following error message:

> 227 Entering Passive Mode (my ip,235)  Connecting data socket... ERROR:> Failed to establish data socket

I used google, and found this on the CuteFTP site:

> Failed to establish data socket 



This error usually occurs when trying to connect in Passive mode to a site that only accepts PORT mode connections. Change the connection type from Passive mode to Port mode to connect to the site.

All theese terms (passive, active, portmode and so on) makes me very confused and i actually dont know what to do. I just want my friends to be able to log in and upload/download som files without any trouble. 

I am using Breezy, and a Dlink 604 broadband router. Port 21 is portforwarded to my local IP.

Please help. It would be so great to have a own ftp-server that my friends can connect to.

---

### Post by colo on 2006-03-27
Don't use FTP over the internet. Use openssh's built-in sftp-subprotocol. Google is your friend.

There are clients for various Operating Systems, like gftp/konqueror/lftp/sftp for GNU/Linux, and winscp for MSFT Win32.

---

### Post by Biffy on 2006-03-27
[QUOTE=colo]Don't use FTP over the internet. Use openssh's built-in sftp-subprotocol. Google is your friend.

There are clients for various Operating Systems, like gftp/konqueror/lftp/sftp for GNU/Linux, and winscp for MSFT Win32.[/QUOTE]

Problem is that most people i know doesent know what ssh is, and they are seldom interested in installing software just to be able to connect to my server. Can someone connect to my sftp server via a webbrowser and transfer files via drag-n-drop or alike? If they can, then im interested. Would be nice if you could post a link to a how-to or something cause i have not done this before.

If only clients can do this, then ftp is the best option. Still, if i cant solve my problem, i might take a look at sftp.

---

### Post by colo on 2006-03-27
There's a windoze-client for sftp, as i mentioned.

FTP is ages old, insecure, and poorly designed for the heavily firewalled/masqueraded environment of today's internet.


Besides, is it YOU wanting them to connect at all cost, or THEM wanting to down/upload stuff to your server?

---

### Post by Jimmey on 2006-03-31
Probably:

You need to enable 'PASV'. To do this:

> sudo gedit /etc/vsftpd.conf
To the bottom of the file, type 
> PASV_ENABLE=YES

I'm doing this from memory, so that might not be correct.

Hope it helps.

---

### Post by MJN on 2006-03-31
< How do I delete a post on here? Clicking [IMG]http://ubuntuforums.org/images/lite/buttons/edit.gif[/IMG] just brings up the edit screen...? >

---

