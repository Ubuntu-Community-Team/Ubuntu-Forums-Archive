---
title: "Chrooted SCP/SFTP access"
date: 2006-05-11
forum: Server Platforms
---

### Post by el3ktro on 2006-05-11
Hello,

I'm running a virtual server which hosts a view websites for friends, family etc. They're all uploading their stuff with FTP right now, but I'd like to switch this to SCP/SFTP for the obvious reasons. Now I've read somewhere that you can restrict SCP/SFTP access to the user's home directory (which also contains the htdocs directory). I've already found scponly, a shell that provides only the commands necessary for SCP/SFTP access - but how do I do the chroot thing?

Tom

---

### Post by soce_32 on 2006-05-11
If you are talking about chrooting your users to their home directories, scponly takes care of this.  When you specify a users shell as scponly, they can only access their home dir.  If you are talking about chrooting your ssh daemon, here is the Debian manual for it:  [http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html)

which is a huge pain in the neck.

Read up on scponly, and try it out.  It does a great job as a secure FTP replacement without setting up all the chroot environment stuff.

---

### Post by el3ktro on 2006-05-12
This is wonderful! That's exactly what I want, chroot the users to their home dir. Didn't know scponly does that, too. So I just have to define scponly as the user's shell and thats it? Would they be able to log in via SSH and get a shell, or would they really only be able to do SCP/SFTP?

Tom

---

