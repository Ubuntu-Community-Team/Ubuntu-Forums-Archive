---
title: "FTP website files to dedicated Web server"
date: 2012-01-20
forum: Server Platforms
---

### Post by TFroehlich3 on 2012-01-20
Hello Everyone,
    I have my web server all set up and running, I set up a FTP server within that server as well to transfer the website files to the server where ever I am (local or over the internet). I got the local to work just fine, but I can't seem to figure out how to get it to connect via internet (non-local), I opened up port 21 on my router (port forward) and no luck yet. 
 
Anyother thing, is the FTP is only letting transfer files into the "home" folder and not into the "/var/www" folder where the files need to go, how can I get the permissions figured out on how to let me do that?
 
Thanks for everything in advance!
 
   -Theodore

---

### Post by CharlesA on 2012-01-20
You need both port 20 and 21 open IIRC. Make sure that your ISP isn't blocking those ports.

A better idea is to just use SFTP if you can get SSH access.

---

### Post by TFroehlich3 on 2012-01-20
> **CharlesA said:**
> You need both port 20 and 21 open IIRC. Make sure that your ISP isn't blocking those ports.
 
A better idea is to just use SFTP if you can get SSH access.
 
 
So I just need to open port 20 on my router as well? and IIRC? What is that setting consist of?

---

### Post by CharlesA on 2012-01-20
> **TFroehlich3 said:**
> So I just need to open port 20 on my router as well? and IIRC? What is that setting consist of?
IIRC = if I recall correctly.

You can try opening port 20, but You would be better off using SFTP instead of FTP if you have a choice, since SFTP is encrypted, and FTP is not.

---

