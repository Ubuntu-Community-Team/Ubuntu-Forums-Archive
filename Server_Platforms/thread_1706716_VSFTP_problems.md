---
title: "VSFTP problems"
date: 2011-03-14
forum: Server Platforms
---

### Post by xendistar on 2011-03-14
I have a Ubuntu10.04 server with vsftp server installed (server is located on a 
private network not public facing at work). I have set vsftp to allow access to 
the web server root folder and set-up two users login that require usernames 
and password to gain access to the root of the web file system.

Now if try to ftp from my laptop (via VPN from home to work) using Filezilla, I enter the 
three required bits of info, host name, username and password, it allow me 
access to the root of the web file system all ok.

Now if I try to ftp to the server from my laptop via vpn but using Windows 
explorer, it again takes me to the root of the web server folder once I have 
submitted the username and password.

Now from my laptop if I login into the remote desktop (MS 2003 Terminal Server) 
via VPN from my laptop and then use windows explorer to ftp into the root of 
the web server, once I have given the username and password it reveals the 
entire root file system on the server and is accessible!!

Is this a vsftp problem?  I am not sure where or how to correct it. In 
the vsftp.conf I have set

local root=/var/www/asg

which is the root of the web server (or at least as far up the file system as I 
want ftp users to go.

Any thoughts

---

### Post by Lars Noodén on 2011-03-14
> **xendistar said:**
> 
Any thoughts

If you have access via SSH, then you already have SFTP capability available.  So my thoughts are that SFTP is worth a try.

If you need to [chroot SFTP](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-Only_Accounts) users to a specific directory, that too is very easy with SFTP.  Your sshd_config should have a section something like the following to do that:
```

Match Group webauthors
        ChrootDirectory /var/www/asg/
        ForceCommand internal-sftp

```

---

