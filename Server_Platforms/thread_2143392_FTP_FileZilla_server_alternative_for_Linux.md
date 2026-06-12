---
title: "FTP FileZilla server alternative for Linux"
date: 2013-05-08
forum: Server Platforms
---

### Post by mbnoimi on 2013-05-08
I'm wondering is there any alternative to FileZilla server in Linux?
  PS
  
[LIST]
[*]I'm looking for a server with GUI manager which offers nearly zero  configuration I can run and manage FileZilla server within 5 min while  PureFTPd needs at least 2 hrs and managing users and groups really  painful specially from flat file 
[*]I tried to use PureAdmin (GTK manager for PureFTPd) and I found it really stupid by comparing to FileZilla GUI manager 
[/LIST]

---

### Post by Simon_WM on 2013-05-09
Have you looked at using proftpd? It Doesn't have a GUI, But creating users and such, is a simple job

---

### Post by d4m1r on 2013-05-09
> **Simon_WM said:**
> Have you looked at using proftpd? It Doesn't have a GUI, But creating users and such, is a simple job

Sounds like he has and is not impressed. Personally I use vsftpd, and managing things via command line is pretty simple. However, I have a fairly basic setup of it running at home only...

---

### Post by sandyd on 2013-05-09
> **mbnoimi said:**
> I'm wondering is there any alternative to FileZilla server in Linux?
  PS
  
[LIST]
[*]I'm looking for a server with GUI manager which offers nearly zero  configuration I can run and manage FileZilla server within 5 min while  PureFTPd needs at least 2 hrs and managing users and groups really  painful specially from flat file 
[*]I tried to use Pure-Admin (GTK manager for PureFTPd) and I found it really stupid by comparing to FileZilla GUI manager 
[/LIST]

Personally, pureftpd is very easy to manage in the command line, check it out

On a clean pure-ftpd install
```

sudo apt-get install pure-ftpd
cd /etc/pure-ftpd
sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/10_PureDB

```
Make sure the following file has "No" as its contents
```

sudo nano /etc/pure-ftpd/conf/PAMAuthentication
```
Once its changed, press control+x to save

Now, PureDB is setup. You dont need to run the above lines ever again.

Now, to add users, take a look at the following line (there are other options that can be exposed via pure-pw --help, but I am just trying to keep it simple here)
```

sudo pure-pw useradd *usernamehere* -u *useridhere* -g *groupidhere* -D */path/to/chroot*
```
Replace *usernamehere*, *useridhere*, *groupidhere*, and */path/to/chroot* with the correct info. To disable the chroot for that user, use a lower case D instead of an uppercase

After adding the account(s), run
```

sudo pure-pw mkdb
```
to save the accounts.

When you want to add more accounts in the future, just repeat the last two steps (you can run pure-pw as many times as you want before saving)

Now, restart Pure-FTPD (note that you only have to restart it once, the passwords will be added to PureDB on subsequent runs of mkdb, and you do not need to restart pure-ftpd for changes to take effect). You only have to do the adduser step each time you want a new user

---

### Post by mbnoimi on 2013-05-13
> **Simon_WM said:**
> Have you looked at using proftpd? It Doesn't have a GUI, But creating users and such, is a simple job

Thanks, I really don't interest in CLI solution for managing FTP server... I'm looking for GUI only

---

### Post by Lars Noodén on 2013-05-13
They're all going to be configured via the shell.  

If you're not tied to the FTP protocol, you could use SFTP instead.  And that comes built-in with the package OpenSSH-Server.  that is zero-config.  Just install it and you have SFTP access.  But if you want 'virtual' accounts or must have the old, insecure FTP, then that steers you back to pure-ftpd or vsftpd

---

### Post by mbnoimi on 2013-05-13
> **Lars Noodén said:**
> They're all going to be configured via the shell.
I don't think that so.

As long as Windows have GUI tools Linux must has GUI tools too, the only thing that I didn't find the perfect one (FileZilla server is perfect but works only under Windows)

---

### Post by Lars Noodén on 2013-05-13
But Windows is rather underpowered and weak, so it is expected that there be GUI tools.

On Linux, the GUIs are mostly just front-ends for a small subset of functionality.  If you want the full power and flexibility of the applications, the plain configuration files are the way to go.  I used to try to use the GUIs but once I found out what the regular UI could do, I made the transition.

That said, for pure-ftp there is a tool called 'pureadmin' and another 'PureUserAdmin'   The former seems not to have been maintained of late.  The latter is a web-based UI, but it will manage users which is what you expressed interest in.

---

### Post by DJ_Max on 2013-05-13
> **mbnoimi said:**
> 
As long as Windows have GUI tools Linux must has GUI tools too
That's one way to look at it, but it doesn't hold much water in reality. Windows has GUI tools as that is why people use Windows, for the user interface. When switching to Linux, you can't keep the same mentality you had when you used Windows.

---

### Post by mbnoimi on 2013-05-13
> **Lars Noodén said:**
> But Windows is rather underpowered and weak, so it is expected that there be GUI tools.

On Linux, the GUIs are mostly just front-ends for a small subset of functionality.  If you want the full power and flexibility of the applications, the plain configuration files are the way to go.  I used to try to use the GUIs but once I found out what the regular UI could do, I made the transition.
If your view point is correct, why Linux maintainers working on desktop environments (Unity, KDE, Gnome.. etc)?!!!

By the way, openSuSE offers super nice GUI tool for managing FTP & LDAP servers (I think through YaST) while in ubuntu I couldn't find alternative.

>  That said, for pure-ftp there is a tool called 'pureadmin' and another 'PureUserAdmin' The former seems not to have been maintained of late. The latter is a web-based UI, but it will manage users which is what you expressed interest in.
Actually the most important GUI thing is managing user & groups. The configuration of FTP server usually set once it doesn't need many modifications.

---

### Post by PowerBarry43 on 2013-05-13
Hi

I know this doesn't fully answer you're question but have you considered sftp. there is a windows client called winscp and linux can connect to it with nautilus or with the scp command line tool.

Hope this helps!

Barry

---

### Post by Paddy Landau on 2013-05-13
I was looking for a similar question, but CLI is fine for me. Sandyd, thank you, your method worked for me.

---

### Post by mbnoimi on 2013-05-26
Hey guys, I found a pretty solution.

[Alfresco](http://sourceforge.net/projects/alfresco/) suports FTP and manage groups/users/permissions thoguht rich web interface. It's too easy and flixable.

Thanks for you efforts.

---

### Post by rubylaser on 2013-05-26
Installing a full blown CMS just for FTP seems like massive overkill to me, but I'm glad that it works well for you.  I hope you are considering security as part of your solution (using SFTP vs. FTP).

+1 to sandyd for the nice clear directions.  I've always used vsftpd in the past, but PureFTP also appears to be very easy to configure and add users.

---

### Post by mbnoimi on 2013-05-26
> **rubylaser said:**
> Installing a full blown CMS just for FTP seems like massive overkill to me, but I'm glad that it works well for you.  I hope you are considering security as part of your solution (using SFTP vs. FTP).

Actually I'm already using CMS so Alfresco gives me all-in-one solution specially it supports FTPS which I consider it as a replacement to SFTP (although I always prefer PHP/APACHE based solutions)

> +1 to sandyd for the nice clear directions.  I've always used vsftpd in the past, but PureFTP also appears to be very easy to configure and add users.
Me too I put it in my consider but I stopped to use it because as I said to you I'm using CMS so I've to install LDAP server for unifying login authentication. Alfresco put all these together, fabulous webUI for DMS+CMS+FTP/FTPS+CIFS.... plaplapla

---

### Post by mbnoimi on 2013-05-29
I tried to use a more simple way for configure pureFtpd through:

```
mbnoimi-pc conf # apt-get install pure-ftpd
mbnoimi-pc conf # cd /etc/pure-ftpd/conf/
mbnoimi-pc conf # echo yes > ChrootEveryone
mbnoimi-pc conf # echo yes > CreateHomeDir
mbnoimi-pc conf # echo 10 > MaxClientsNumber
mbnoimi-pc conf # echo 3 > MaxClientsPerIP
mbnoimi-pc conf # echo yes > NoAnonymous
mbnoimi-pc conf # echo no > DisplayDotFiles
mbnoimi-pc conf # echo yes > DontResolve
mbnoimi-pc conf # echo 5 > MaxIdleTime
mbnoimi-pc conf # echo yes > PamAuthntication
mbnoimi-pc conf # echo no > AnonymousCanCreateDirs 
mbnoimi-pc conf # echo 007 007 > Umask
mbnoimi-pc conf # echo yes > ProhibitDotFilesWrite
mbnoimi-pc conf # echo yes > ProhibitDotFilesRead
mbnoimi-pc conf # echo no > AutoRename
mbnoimi-pc conf # echo yes > NoChmod
mbnoimi-pc conf # echo no > KeepAllFiles
mbnoimi-pc conf # echo 0 > TLS
```

But when I tried to make a restart it gave me this error:
```
mbnoimi-pc conf # /etc/init.d/pure-ftpd restart
Restarting ftp server: /usr/sbin/pure-ftpd-wrapper: Invalid configuration file /etc/pure-ftpd/conf/PamAuthntication: No corresponding directive
```

Do you know how to fix it?

---

### Post by mbnoimi on 2013-05-29
Oops... my mistake I've to use "PAMAuthentication"

---

