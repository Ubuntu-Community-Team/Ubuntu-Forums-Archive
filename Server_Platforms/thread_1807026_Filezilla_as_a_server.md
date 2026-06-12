---
title: "Filezilla as a server"
date: 2011-07-18
forum: Server Platforms
---

### Post by brainard52 on 2011-07-18
I am completely incompetent at things like this, and I need help setting it up.

---

### Post by Dry Lips on 2011-07-19
I suppose you're referring to this:
 [http://filezilla-project.org/download.php?type=server](http://filezilla-project.org/download.php?type=server)
>  &#8220;XP and Vista and 7 are supported, each both 32 and 64 bit.&#8221;
 In other words what your asking for help with is an a FTP server for *Windows*.  
 In Linux you would use other programs, such as OpenSSH or vsftpd.
 

 [https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)
 [https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)


Personally I wouldn't dream of running a FTP-service on my computer
unless I knew what I was doing... Being hacked isn't fun at all. ;)

---

### Post by Lars Noodén on 2011-07-19
You can do it the easy way and install the package OpenSSH-server.  That will give you the SFTP protocol and you can connect using the FileZilla client.

---

### Post by Wim Sturkenboom on 2011-07-19
Personally I don't like sftp; unless things have changed, it's far to complicated to jail users to their home directory.
Therefore I prefer vsftpd (configured to use ssl); others might do the trick easily as well.

---

### Post by Lars Noodén on 2011-07-19
> **Wim Sturkenboom said:**
> Personally I don't like sftp; unless things have changed...

It's nearly effortless to [setup chrooted SFTP](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads) nowadays.

---

### Post by brainard52 on 2011-07-19
> **Dry Lips said:**
> I suppose you're referring to this:
 [http://filezilla-project.org/download.php?type=server](http://filezilla-project.org/download.php?type=server)
 In other words what your asking for help with is an a FTP server for *Windows*.  
 In Linux you would use other programs, such as OpenSSH or vsftpd.
 

 [https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)
 [https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)


Personally I wouldn't dream of running a FTP-service on my computer
unless I knew what I was doing... Being hacked isn't fun at all. ;)
All I need it for is to back up some games :/ I won't actually let anybody else onto it. As for getting hacked... meh. I don't have anything anybody would want.

---

### Post by Dry Lips on 2011-07-19
> **brainard52 said:**
> All I need it for is to back up some games :/ I won't actually let anybody else onto it. As for getting hacked... meh. I don't have anything anybody would want.
 
That your games would be copied don't worry me. What is worse is that
someone could upload a malicious script to your server or something.

---

### Post by Lars Noodén on 2011-07-20
> **brainard52 said:**
> All I need it for is to back up some games :/ I won't actually let anybody else onto it. As for getting hacked... meh. I don't have anything anybody would want.

You have a computer connected to the Internet.  That's an item in high demand, regardless of what may or may not be on it.

---

### Post by Wim Sturkenboom on 2011-07-20
> **Lars Noodén said:**
> It's nearly effortless to [setup chrooted SFTP](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads) nowadays.

Thanks for that link; is it equally easy way to jail users to their home directory with SSH?

---

### Post by Lars Noodén on 2011-07-20
> **Wim Sturkenboom said:**
> Thanks for that link; is it equally easy way to jail users to their home directory with SSH?

Almost as easy.  In that case you still need to populate the chroot jail with the devices and applications needed for them to run a shell.

---

### Post by Wim Sturkenboom on 2011-07-20
Yeah, just figured that out :(

---

