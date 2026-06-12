---
title: "sftp or ftps"
date: 2010-12-11
forum: Server Platforms
---

### Post by I8NY on 2010-12-11
Okay I want to share files over the web with only a few people and limiting them to certain folders.  I have been doing a remote access (ssh) to my server to access it from a pc on the local network.  I later found out the same program doing ssh (open_ssh) was also doing sftp, great I could do both with one system account.  Problem I couldn't find away to configure another user to go over the web with limited folder access without messing up my user to access the pc.  I tried ftps by using vsftpd, I couldn't get chroot set up correctly or even log in.  So my question is what program and/or protocol should I use to do secure ftp over the web?

OS: Ubuntu 64bit 10.04

---

### Post by papibe on 2010-12-12
You should be able to create a non administrator user with adduser. Then you put the files you want to share in that user's home. By default the new user will have access to both ssh and sftp.

In the client side, they can also access your files using sftp, or rsync over ssh. And even if they are in Windows by using  either WinSCP, Filezilla, or FireFTP(Firefox).

That has worked very well for me.

I hope it helps.

---

### Post by CharlesA on 2010-12-12
You can jail users with openssh, and make it so that a user can only use sftp.

See [here]("http://www.debian-administration.org/articles/590").

---

### Post by I8NY on 2010-12-14
thx for the replies.  CharlesA, the link was helpful on setting up the basics of what I wanted to do.  I never thought of looking up chroot sftp.  I did what the link said but it wasn't a full tutorial so I found one one [here]("http://ubuntuforums.org/showthread.php?t=858475") on the forums. :D I now have it all set up with both users using the correct settings.  Now I just need to see if I can see if I can configure the users to only listen on certain ip/ports.  Thanks for the help!

---

### Post by CharlesA on 2010-12-14
You'd have to set the openssh-server to listen on whatever port you want.

Do you want it to only allow access from one ip address, or do you want it to listen on a specific interface/ip address?

---

