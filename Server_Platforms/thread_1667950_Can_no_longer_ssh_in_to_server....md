---
title: "Can no longer ssh in to server..."
date: 2011-01-15
forum: Server Platforms
---

### Post by kpm on 2011-01-15
I usually ssh into my Ubuntu 9.10 LAMP server using shell, but just installed the mac version of Filezilla and was going to connect using sftp.  I wasn't able to connect, so I went back to my shell, and saw it's connection dropped, and on attempts to ssh back into the server, I just keep getting time outs.
Is there a security setting that I possibly triggered on  an Ubuntu 9.10 LAMP server installation that locks a user or IP out after a certain number of attempts to log in?  I'm guessing that is what has locked me out...

---

### Post by kpm on 2011-01-15
actually, i just remoted into another computer and was able to ssh into the server from it, so I must have some security settings set up to kill access from an offending IP attempting multiple times to gain access... Now to think back to whether I did that or if it is a default security setting... hmmm.

---

### Post by kpm on 2011-01-15
I fell victim to my own security settings... I had set up fail2ban, and it did what it was supposed to do after the failed sftp attempts by filezilla... back in now.

---

