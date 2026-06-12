---
title: "Hackers vs Ubuntu Server?"
date: 2007-02-08
forum: Server Platforms
---

### Post by dupa on 2007-02-08
Hi all.
I would like to create a web-server with linux.
Ubuntu is really great and i would like to use it.

However when I use stuff such as Apache, Postgres and so on, in a machine used in a "production" web environment, I absolutely need to prevent any security problem to prevent hacker's breaking my system in any way.

So, is Ubuntu suitable to creare an auto-upgradable server system?

For example, in the ubuntu repositories, apache is a 2.0.55 version, but on apache.org it is at 2.0.59

So, the only way to have a secuirity bug (of apache, postgres, tomcat.. and so) fixed within few days... is to manually upgrade every server software, or is it possible to trust in the updates through apt-get ??

---

### Post by jtc on 2007-02-08
> **dupa said:**
> For example, in the ubuntu repositories, apache is a 2.0.55 version, but on apache.org it is at 2.0.59
Not entirely true :-) 

Ubuntus Apache2 version (in Dapper Daker) is 2.0.55-4ubuntu2.1  and not merely 2.0.55

That means it is based on the based 2.0.55, but with (primarily) security patches applied. Eventual new functions are not applied, so basically you have a 2.0.55 but up-do-date securitywise. This versioning is rather common among Linux distribuations and something to be aware of when you compare included version-number with the one from the original source.

---

### Post by esaym on 2007-02-08
Ubuntu is great

---

### Post by dupa on 2007-02-08
> **jtc said:**
> Not entirely true :-) 

Ubuntus Apache2 version (in Dapper Daker) is 2.0.55-4ubuntu2.1  and not merely 2.0.55

That means it is based on the based 2.0.55, but with (primarily) security patches applied. Eventual new functions are not applied, so basically you have a 2.0.55 but up-do-date securitywise. This versioning is rather common among Linux distribuations and something to be aware of when you compare included version-number with the one from the original source.


Thank you for our help.
So what do you think about having a server just made up with packages coming from "main" and "restricted" repositories?

It will be VERY safe if I will just use the automatic update with apt-get upgrade?

thanks

---

### Post by jtc on 2007-02-08
How safe a server is depends on lots of factors. What I believe I can say thought is that if you only use main and restricted you won't, as a general rule, have to worry about packages not being updated.

---

### Post by imagine on 2007-02-08
> **dupa said:**
> So what do you think about having a server just made up with packages coming from "main" and "restricted" repositories?

It will be VERY safe if I will just use the automatic update with apt-get upgrade?
Just that Apache isn't in main. Of course software in the universe repository is usually also patched, but there's no guarantee for it.

---

### Post by jtc on 2007-02-08
> **imagine said:**
> Just that Apache isn't in main.

No, Apache (1.3) isn't in main, but Apache2 (which dupa was refering to) is.

---

### Post by dupa on 2007-02-08
yes, right, 

apache2
and php5 and postgresql 8.1 are in main too

unluckily there is not "tomcat" in main :(

what do you suggest as ftp server in main repositories? (my priority is good security of the server)

Thanks!

---

### Post by jtc on 2007-02-08
> **dupa said:**
> what do you suggest as ftp server in main repositories? (my priority is good security of the server)
What is the purpose of the FTP-server? To allow users to login and upload files or to offer download through "anonymous FTP"?

---

### Post by dupa on 2007-02-08
> **jtc said:**
> What is the purpose of the FTP-server? To allow users to login and upload files or to offer download through "anonymous FTP"?

the server should be used as PHP & JSP server. (about JSP i still don't know what is better to use.. tomcat in the universe repository... or to use a full J2EE AS, such as Jboss that is totally NOT provided as a .deb package)

The ftp server should allow web-developers (as me :) ) to add/remove files from the apachea accessible directories.

I don't think that anonymous access will ever offered. Now I just need to give read/write access to the people who want to modify the web-sites in the apache directories :)

---

### Post by ZephyrXero on 2007-02-08
> The ftp server should allow web-developers (as me  ) to add/remove files from the apachea accessible directories.

I don't think that anonymous access will ever offered. Now I just need to give read/write access to the people who want to modify the web-sites in the apache directories
Then all you should need is SSH. install "openssh-server", and you will be able to transfer your files as well as have remote terminal access. SSH is far better than FTP because it is encrypted, and just generally more secure than regular FTP.

Also, if you have Windows users connecting to this machine, I'd highly recommend having them use [FileZilla](http://filezilla.sf.net) for doing your SSH (sometimes referred to as SFTP) transfers. And of course, if you're using Ubuntu (Gnome) just go to Places > Connect to Server and choose SSH ;)

---

### Post by JimTDI on 2007-02-08
I've used both ProFTPD and vsftpd.  vsftpd would work very well for what you want to do, and is easy to setup, and bullet fast!

ProFTPD is not a slouch either though...

---

### Post by dupa on 2007-02-09
> **ZephyrXero said:**
> Then all you should need is SSH. install "openssh-server", and you will be able to transfer your files as well as have remote terminal access. SSH is far better than FTP because it is encrypted, and just generally more secure than regular FTP.

Also, if you have Windows users connecting to this machine, I'd highly recommend having them use [FileZilla](http://filezilla.sf.net) for doing your SSH (sometimes referred to as SFTP) transfers. And of course, if you're using Ubuntu (Gnome) just go to Places > Connect to Server and choose SSH ;)

Wow!
I didn't know about this feature of OpenSSH (i already installed it as terminal server). it is really great! With Filezilla works great
Maybe Is there any software under windows to mount that SFTP as a remote shared folder?

The only problem is that with OpenSSH the user can browse all around the filesystem. (as he was connected to his shell... )
but on a classic scenario of FTP, some user should only a "virtual" root of the filesystem for example /home/limiteduser and cannot browse back to /home/

---

### Post by jtc on 2007-02-09
> **dupa said:**
> 
Maybe Is there any software under windows to mount that SFTP as a remote shared folder?

Yes, take a look at [SftpDrive]("http://www.sftpdrive.com/") or [WebDrive]("http://www.webdrive.com/products/webdrive/index.html"). I haven't found any free software for Windows doing the trick thought.

> **dupa said:**
> 
The only problem is that with OpenSSH the user can browse all around the filesystem. (as he was connected to his shell... )
but on a classic scenario of FTP, some user should only a "virtual" root of the filesystem for example /home/limiteduser and cannot browse back to /home/
Take a look at [rssh]("http://www.pizzashack.org/rssh/") or [scponly]("http://sublimation.org/scponly/") (both in universe).

---

### Post by firebadger on 2007-02-09
[EngInSite DataFreeway]("http://www.enginsite.com/ssh-webdav-ftp-sftp-client.htm") is free I think.

---

