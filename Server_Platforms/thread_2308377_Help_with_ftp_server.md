---
title: "Help with ftp server"
date: 2016-01-02
forum: Server Platforms
---

### Post by VanillaMozilla on 2016-01-02
I have vsftpd on Ubuntu 14.04 LTS.  I have an anonymous ftp outgoing set up in the /srv/ftp directory.  That's easy enough, but I need a little more.  I have read the documentation here:  [https://help.ubuntu.com/lts/serverguide/ftp-server.html](https://help.ubuntu.com/lts/serverguide/ftp-server.html) and in the config file, but the correct method is eluding me.  I need to keep this simple.  I don't need high security.

I want to do this in two stages.  For now I need
(1) Outgoing ftp (anonymous is fine for now).  (Files can be read by anyone)
(2) Incoming ftp (anonymous is still OK).  (Set up so incoming files can only be read locally)
For security, outgoing and incoming files need to be in separate directories, so bad guys can't use my computer as a porn server.


At a later stage I will need to protect outgoing (downloaded) files with a password.  (Incoming password protection is all right but not required.)  The documentation shows how to limit users to home directories (which presumably implies password protection).  However, I still want uploaded files to be remotely inaccessible.  Is this possible?

---

### Post by Elishasmantle on 2016-01-03
Hello,

Try this link. They have many step-by-step instructions. I've used a few and had no headache after following doc. :)
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by VanillaMozilla on 2016-01-03
Thank you.  Time for Downton Abbey now.  :)

---

