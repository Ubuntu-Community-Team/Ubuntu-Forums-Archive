---
title: "Unable to Install FTP Service"
date: 2012-04-16
forum: Server Platforms
---

### Post by jonedney on 2012-04-16
Hello Everyone,

I've been working on my VPS over the last week and was able to successfully get ISPConfig 3 (web site manager) installed on my Ubuntu 10.04 LTS server.  I was running into a problem with the FTP service (pure FTP), and was given some instruction on installing it fresh again, but it seems as if there is an error, and I'm unsure how to remedy.

```
root@server:~# apt-get source pure-ftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list
root@server:~#
```

Can anyone shine some light on this?

Thank you,
Jon

---

### Post by Lars Noodén on 2012-04-16
If you want to *securely* upload and download files, then turn to SFTP instead.  SFTP is built into the package openssh-server so if you can login via SSH, then you can already connect with SFTP.  

SFTP clients are built into Nautilus and Filezilla, to name two.

It's rare that FTP would be chosen over SFTP:
[list]
[*][http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*][http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[/list]

However, to answer your question, you'll have to have /etc/apt/sources.list contain references to source repositories.   They will look something like this:
```

deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

```

You can build a sources.list file with this generator and make sure the sources are selected:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Just remember to make a backup copy of the file before trying any manual changes.

---

### Post by jonedney on 2012-04-16
Hello Lars!

Thank you for that information.  I used SFTP to access the server, and while it wont work for the individual accounts I created within ISPConfig, it works with my root access (which is fine, it's only my sites on here anyways), so I uploaded test index.html files to their respected places.

It seems both domains on my server, are refecting the same information.

[http://www.jonedneycreative.com](http://www.jonedneycreative.com), according to ISPConfig has a path of var/www/clients/client1/web1

[http://www.jonedney.me](http://www.jonedney.me) has a path of var/www/clients/client2/web2

When you visit both sites, they both reflect content for web2.  Do you happen to be familiar with that problem?  I am going to check out the ISPConfig forums on the issue.

Thank you,
Jon

---

### Post by Lars Noodén on 2012-04-16
If you're having trouble writing to /var/www, then you might have a directory permission problem.  If you are the only user then you can simply change ownership of the directory and files to yourself.

```

sudo chown -R jonedney /var/www

```

That way you can avoid logging in as root.  Once you have that set up, it would be a good idea to turn off remote root access ASAP.  It is one less potential flaw in the system.

---

### Post by jonedney on 2012-04-16
Hello Lars!

Thank you for this information.  The server couldn't locate the user 'jonedney', so that may be the problem, I will do some looking around on that.

Additionally, I will do some looking around about disabling remote root and using sudo instead.

I will post my findings.

Thank you,
Jon

---

### Post by Lars Noodén on 2012-04-17
> **jonedney said:**
>  The server couldn't locate the user 'jonedney', ...

That was just a guess at the user name.  Use the output from [whoami](http://manpages.ubuntu.com/manpages/oneiric/en/man1/whoami.1.html) to be sure of how you are logged in.

---

### Post by jonedney on 2012-04-17
Hello Lars!

Actually, you were correct on the username, which is why I referenced it didn't work.  None the less, I ended up installing everything individually not using a control panel like ISPConfig, not installing an FTP server and just using SFTP.  With the exception of not getting the mail server set up correct yet, I'm excited of the progress.

Thank you,
Jon Edney

---

