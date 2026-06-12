---
title: "Making my FTP server safe! (vsftpd)"
date: 2013-09-09
forum: Security
---

### Post by Tobias_Brodersen on 2013-09-09
Hello Ubuntu guys :)
Just recently i began using Ubuntu, mostly because IT and network always been one of my great interests, so the thought of running a server, only using unix commands would be fun and interesting.
I got my teamspeak server running, except for the server query part, which dosen't make any sense to me (will look into that later)
I installed and got Apache running, so that i can host my own newbie website.
And i just installed vsftpd, because the server is placed at my work, so i needed some way, i could move files from my home desktop to the which work fine my user, i can get around anywhere i want.

But my brother would like to join, so that he would have a place where he can store all of his website design, that no problem, he got another user, i made some time ago, the problem is that, he is also able to go into every folder on the server, which is not good, since he is also scaring those project with some of his colleges. 

So if a create a dir for all of his project, how can I be sure, that it is the only place that he can open, save and/or delete files?

Best Regards 
Toby!

---

### Post by Lars Noodén on 2013-09-09
> **Tobias_Brodersen said:**
> And i just installed vsftpd, because the server is placed at my work, so i needed some way, i could move files from my home desktop to the which work fine my user, i can get around anywhere i want.


You might look at SFTP instead.  Unlike FTP, it is secure.  There is an SFTP server built into the package openssh-server and it requires no additional configuration to use.  There is an SFTP client built into your file manager or you can use a dedicated client like FileZilla.  If you use those, you can then uninstall vsftp.

FTP is something different and is insecure.  Unless you are offering anonymous downloads (without login), you probably don't need FTP.  In general it is time to [stop using FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) and use SFTP instead.

---

### Post by Nil_Pointer on 2013-09-09
Yes, FTP is just not safe. Although, you can run your server over non-standard port (in range 10000-65535) and limit bruteforce attempts with Fail2Ban. But it still wouldn't be very secure, since passwords and data are transmitted in plaintext and can be easily sniffed on any router.

As for SFTP, it's cool, but you need to lock users to their home directories and lock them out from using shell commands. In fact, I'd be interested in doing that to replace FTP.

---

### Post by Lars Noodén on 2013-09-09
> **Nil_Pointer said:**
> As for SFTP, it's cool, but you need to lock users to their home directories and lock them out from using shell commands. In fact, I'd be interested in doing that to replace FTP.

You don't need to do that but it is very, very easy if you decide you want to.  It's a matter of changing a few lines in the configuration file for openssh-server.

Set the sftp subsystem to use the built-in one.

```

Subsystem sftp internal-sftp

```

Then specify a group of users to restrict to sftp

```

Match group sftponly
          ForceCommand internal-sftp

```

That locks any users in the group *sftponly* into only being able to use SFTP and not the shell.  Usually this is enough to make everyone happy.  Make sure you are not in the group or you will get locked out of the shell.

If you want to chroot, that's two more lines to the config file, but then there is one gotcha: the chroot target has to be owned by root.

---

