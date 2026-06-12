---
title: "Looking for an advanced FTP client software"
date: 2008-02-15
forum: Security Discussions
---

### Post by norha_king on 2008-02-15
Hi all,
I want to upload some files to my website. So I am looking for an advanced FTP client software solution designed for ease of use by both novices and professionals. It should be powerful and secure file transfer solution. It should also have total control, security, efficiency, and simplicity. If you people have any idea then please let me know.
Thanks in advance!

---

### Post by kesman on 2008-02-15
sudo apt-get install gftp

---

### Post by TheApe on 2008-02-15
FireFTP is an extension for firefox. It works perfectly. Give it a try
[http://fireftp.mozdev.org/]("http://fireftp.mozdev.org/")

I don't know if you're looking for a GUI software. I was used to use GUI softwares before came to Ubuntu, then I found lftp
```
sudo apt-get install lftp
```
It's an awsome text-based ftp client, with bookmarks, syncronization, etc.
The best feature for me is the command "mirror" witch uploads/downloads an entire folder, with or withouth it's subfolders, and with lot's of filters.

Hope to be helpfull.


:)

---

### Post by grokwik on 2008-02-15
Maybe it's a stupid question but what do you mean by advance ftp client ?? (Personnaly I use Filezilla)

---

### Post by stevejesus on 2008-02-15
Definitely voting for gFTP.  have used it for 5 years now.  Its quick, fast, and NEVER changes.

---

### Post by HermanAB on 2008-02-15
Only one problem with your requirements:
By its design, FTP isn't secure.

If you want security, use SSH.

---

### Post by kevdog on 2008-02-15
> If you want security, use SSH.

But doesnt this just introduce more complexity?  If you wanted just basic ftp functionality with an ssh setup (for example just the ability to copy and put files, change/list directories, make directories, etc -- just basic ftp functionality but with ssh (so the analogous copy command would be scp)), wouldn't you really need to run ssh inside a jail?  I know jails are not 100% secure, however if you just allow the user a basic set of commands, isnt the jail very hard to break out of? 

Again ssh my nature presents the user with a shell.  Is there a way to copy/paste/list/create directories without presenting the user with a full blown shell? A jailkit is the only thing I can come up with.

**Think this discussion should be moved to the servers thread!

---

### Post by p_quarles on 2008-02-15
Moved to Server Platforms. EDIT: On second though, moving to Security, as the OP asked for client software in this case. 

Yeah, SSH/SFTP adds apparent complexity to the setup, but this just highlights the insecurity of FTP itself. It's not advanced enough to be secure. 

I don't think you'd need a jail to set up a secure SSH server, you would just need the system locked down. This is necessary for security regardless of which client software is used.

---

### Post by honeydew on 2008-02-15
yah ftp is not a secure way of transfering files it would be best to go with sftp nautilus supports this  also nautilus should support basic ftp connections (Places > Connect to server).  However If your site does not provide sftp(ssh access)  I would suggest using ncftp it is command line.. but is very very powerful(well documented).  I have found with gftp I can lock it up pretty easily, which sucks when file transferring is half of what I do.  Granted I may be jaded I switched to ncftp a few years ago.. gftp may have come a long way since.

---

### Post by HermanAB on 2008-02-15
SSH also provides something called SFTP.  Gftp can do that - select a protocol like 'FTP over SSH2'.

If you use FTP, your user name and password is transferred in plain text over the wire.  With SSH, everything is encrypted - including the login process.

---

### Post by kevdog on 2008-02-15
Locking down the system as you propose -- that is a topic of another thread.  The jail was one way of locking down the system.  I'm not promoting that as the only way, however its one easy method that could be employed rather quickly.

---

### Post by jennet_fleaming on 2008-02-16
Hi, I use AnyClient when I need file transfer. It is a free platform independent file transfer application that supports all major file transfer protocols including FTP/S, SFTP and WebDAV/S. AnyClient is available both as a web based service requiring no software installation, and as a downloadable application that you can install locally. Please visit this link [www.anyclient.com](www.anyclient.com) . Hope this will help you.
All the best!

---

### Post by euler_fan on 2008-02-16
I'd like to make the note that the version of gFTP avaliable in Gusty though Add/Remove wouldn't connect to an https:// fileshare I use because SSH was not compiled in.

> HTTPS Support unavailable since SSL support was not compiled in. Aborting connection.

I'll be looking around for a workaround (maybe in synaptic?) but thought I would point it out.

---

### Post by p_quarles on 2008-02-16
> **euler_fan said:**
> I'd like to make the note that the version of gFTP avaliable in Gusty though Add/Remove wouldn't connect to an https:// fileshare I use because SSH was not compiled in.



I'll be looking around for a workaround (maybe in synaptic?) but thought I would point it out.
HTTPS uses SSL, which is unrelated to SSH.

---

### Post by euler_fan on 2008-02-16
> **p_quarles said:**
> HTTPS uses SSL, which is unrelated to SSH.

Dumb me. Thanks.

---

