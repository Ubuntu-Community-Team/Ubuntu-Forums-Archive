---
title: "RSSH Lock users"
date: 2010-05-12
forum: Server Platforms
---

### Post by brunoskrebs on 2010-05-12
Hello there,

I've just installed RSSH on my server and I'm trying to keep my sftp as secure as possible, so I decided to lock users to their home. I found a few sites that teach how to do it but they are not very clear to me. The best one that I found was [this]("http://bryanfullerton.com/?p=250").

I have a few doubts about accomplishing this, and perhaps you guys could help me with it.

The first question is about the fourth step that says:
> Fourth, setup the chroot environment, which includes copying the following from the main system into your chroot directory:

Ok, I created a chroot directory at /home/sftp (guess this is fine right?), and then I started copying the files that it is telling me to copy. The questions is about those nested files, like ./etc/passwd, does it need to be copied to /home/sftp/etc/passwd or just /home/sftp/passwd?

Still on the fourth step it says:
> Additionally, setup these links, again copying what's setup in the main system.

Lammer question, do I need to execute the ln command and copy(link) it as what name? If is this the right command...

Now on the sixth step I have to:
> Sixth, edit /etc/default/syslogd and update the SYSLOGD="" line as follows.

But there is no /etc/default/syslogd on my server... What should I do?

And last question, if is not asking too much, if I do this my users will be locked to their home like /home/sftp/user_name right?

Hope someone can help me solve these questions.
Thanks in advance.

Bruno

---

### Post by cdenley on 2010-05-12
What version of ubuntu? If you want to restrict users to sftp chrooted to their home directory, this is much easier.
[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

### Post by JPorter on 2010-06-11
> **cdenley said:**
> What version of ubuntu? If you want to restrict users to sftp chrooted to their home directory, this is much easier.
[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

^^ What he said. The internal sftp server in OpenSSH has great chroot functionality with almost no configuration.

---

