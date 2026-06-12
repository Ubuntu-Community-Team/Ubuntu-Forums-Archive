---
title: "FTP Server for uploading to website"
date: 2008-07-20
forum: Server Platforms
---

### Post by ejpyle on 2008-07-20
Hey all I was wondering if anyone knew of a good FTP server program to run on my Ubuntu box so I can connect with a windows os (yuck) to make changes to my website. I am not really concerned with a GUI though it would be nice if I can have one. Security is not really an issue as I am only going to be making changes on the local network.

---

### Post by tamoneya on 2008-07-20
install vsftpd on the ubuntu box and then use something like filezilla on the windows box to connect:

[http://news.softpedia.com/news/How-to-Install-Vsftpd-in-Ubuntu-45753.shtml](http://news.softpedia.com/news/How-to-Install-Vsftpd-in-Ubuntu-45753.shtml)
[http://filezilla-project.org/](http://filezilla-project.org/)

---

### Post by neurostu on 2008-07-20
I don't know of any FTP stuff in ubuntu... but you can install openssh-server, then connect to it using WinSCP.  I really like using WinSCP as it allows for WinExpolorer like management and transfering of files.

[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)

WinSCP is a free tool that is really easy to use.

---

### Post by ejpyle on 2008-07-20
> **tamoneya said:**
> install vsftpd on the ubuntu box and then use something like filezilla on the windows box to connect:

[http://news.softpedia.com/news/How-to-Install-Vsftpd-in-Ubuntu-45753.shtml](http://news.softpedia.com/news/How-to-Install-Vsftpd-in-Ubuntu-45753.shtml)
[http://filezilla-project.org/](http://filezilla-project.org/)

I was playing with this earlier though I am not able to find any documentation on how to break away from the default directory....

my web server runs off of a secondary partition...

any ideas?

---

### Post by ejpyle on 2008-07-20
I am under the impression that nobody has a response to my riddle.

---

### Post by neurostu on 2008-07-21
> **ejpyle said:**
> I am under the impression that nobody has a response to my riddle.

I know its not FTP specifically but have you tried connecting over SSH from windows using SCP?  I'm pretty sure its what you're looking for.

---

### Post by Potatoj316 on 2008-07-21
Im pretty sure there is an ftp client already installed by default.  In the terminal try running ftp, it will then probably either ask for a server or complain that you didnt already give it one.  Or if you want a graphical ftp client I like to use FireFTP, it is a firefox plugin that you can get in the usual firefox plugin site.

---

### Post by bodhi.zazen on 2008-07-21
> **ejpyle said:**
> I was playing with this earlier though I am not able to find any documentation on how to break away from the default directory....

my web server runs off of a secondary partition...

any ideas?

Well, the "problem" with ftp is one of security. You will need to configure vsftp to allow you to browse outside you the secured directories.

The suggestion of using ssh (scp) is a good one.

---

### Post by tamoneya on 2008-07-21
> **ejpyle said:**
> I was playing with this earlier though I am not able to find any documentation on how to break away from the default directory....

my web server runs off of a secondary partition...

any ideas?

Cant you just set local_root to /var/www/ or whatever your web root is.

[http://ubuntuforums.org/archive/index.php/t-398150.html](http://ubuntuforums.org/archive/index.php/t-398150.html)

---

### Post by windependence on 2008-07-21
Yes, and you can change directories at will, you just need to give your user som juice to do it.

-Tim

---

