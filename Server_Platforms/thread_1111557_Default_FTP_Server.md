---
title: "Default FTP Server?"
date: 2009-03-30
forum: Server Platforms
---

### Post by faustism on 2009-03-30
Hello,

As of now, I have installed Ubuntu server with LAMP and Joomla.  I now want to allow users to edit content in their individual folder.

I wanted to know what the default server that was installed so that I do not mess anything up by installing a gui(joomla asked for an ftp username and password) for the FTP server.

Also, I found [this thread]("http://ubuntuforums.org/showthread.php?t=51611") and thought that6 i could do something like this except one for each user.

Any comments/advice/answers will help. Thank you.

---

### Post by doogy2004 on 2009-03-30
I just use ssh to do sftp, this makes the traffic secure.  There you can also lock users into only being able to see certain directories.

[http://www.howtoforge.org/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.org/chrooted-ssh-sftp-tutorial-debian-lenny)

---

### Post by faustism on 2009-03-30
Thank you. I'll try that

---

