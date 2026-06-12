---
title: "Problem with VSFTP"
date: 2017-02-05
forum: Server Platforms
---

### Post by lochness123 on 2017-02-05
[SIZE=2][FONT=arial][COLOR=#111111]I'm working on FTP server(Ubuntu). According to a video on the Internet I configured it[/COLOR]
(sudo apt-get install vsftpd etc)
[COLOR=#111111]And joined FTP to localhost ```
ftp localhost
``` - everything worked.[/COLOR]
[COLOR=#111111]After a while, I came to a point where it was necessary to add users ```
groupadd SEECS mkdir /home/peter 
``` ```
 chmod 770/home/peter
``` ```
 chown root:SEECS /home/peter 
``` ```
useradd -g SEECS -d /home/peter
``````
 useradd -g SEECS -d /home/peter user1 
```and when I enter command: ```
psswd user1 
``` it shows me an error about permissions.[/COLOR]
[COLOR=#111111]Following another video ([/COLOR][/FONT][/SIZE]https://www.youtube.com/watch?v=uDhZOy1DrDo&t=1s) [SIZE=2][FONT=arial][COLOR=#111111]I changed my permissions to root permissions. I rebooted FTP and when I tried to connect FTP to localhost,[/COLOR]
[COLOR=#111111]It shows an error FTP: connect: connection refused.[/COLOR]
[COLOR=#111111]How to solve this problem?[/COLOR][/FONT][/SIZE]

---

### Post by TheFu on 2017-02-05
Use **sftp**, not plain FTP.  Much easier to setup and secure.  sftp is included in openssh-server, so you get it for free. After all, every Linux system needs an ssh-server, right?

If you agree and don't have one of the 0.0000001% good reasons to run plain FTP, it doesn't put your credentials at risk as plain text for anyone to view like a postcard.

---

### Post by lochness123 on 2017-02-05
What is the difference between VSFTPD and SFTP?

---

### Post by TheFu on 2017-02-05
> **lochness123 said:**
> What is the difference between VSFTPD and SFTP?

sftp is a protocol, secure, based on ssh. If you come from Windows, you may never have heard of ssh. ssh is how Unix systems have been managed for over 20+ years.  sftp is an interface compatible version of FTP, just using ssh for the security. scp is similarly an interface compatible drop in of rcp that uses ssh for security.  ssh supports key-based authentication and multiple different types of encryption.  Every Unix/Linux server really needs ssh running (unless it is a container, but that is a different thing) to provide secure remote administration, secure remote access, secure remote file transfer.  The openssh-server package provides ssh, sftp and scp all in one.

vsftpd is a package that is primarily used for plain FTP, though it supports other FTP-like protocols like *sftp* and *ftps*.  Since that package doesn't support ssh, you'll need the other ssh package anyway, so why have 2 different cooks fighting over the soup (sftp) in the same kitchen?  Plus having plain FTP is a security liability these days as is FTPS (which allows the client to decide if encryption is used or not).

I can't come up with more than 1 or 2 good reasons to use Plain FTP these days out of 900+ reasons to use sftp.  
[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) explains more.  You can check out other articles about why plain FTP should have been killed off around 1995, when telnet was effectively killed, too. Please do.

Most Linux file managers support sftp out of the box.  Every OS I know that supports networking supports sftp and even Windows has a few good alternative clients.

IMHO.  Hope this helps.

---

### Post by lochness123 on 2017-02-06
Thanks for help.

---

### Post by wildmanne39 on 2017-02-06
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2017-02-06
> **lochness123 said:**
> Thanks for help.

A few comments about the commands entered above.

* groups and userids should be lower-case. Don't know that it matters or not. The OS actually only uses the numbers (gid) internally.
* There appear to be a few typos in the first post.  I see at least 2.  "psswd" is wrong.  **passwd** is the correct command.  Changing the password for another userid requires elevated privileges (sudo).   Is user1 the main userid?

At this point, it isn't clear if you
a) copy/pasted the commands and they were originally typed incorrectly or 
b) if they were entered into the computer incorrectly.

So the first question is do you intend to use vsftp or openssh's version of sftp?  Others here can probably help with vsftp, if that is your choice. It is your choice 100%.

Next, what is the goal for allowing the 2nd userid access?  
How much do you want to limit their access?  Upload only? Upload and download? Download only?  Should they have access on the entire system or is a **chroot** setup planned?

---

