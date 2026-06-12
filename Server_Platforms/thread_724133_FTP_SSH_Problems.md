---
title: "FTP SSH Problems"
date: 2008-03-14
forum: Server Platforms
---

### Post by Jonamb on 2008-03-14
Hello, my Name is Jonathan, I'm now proud owner of a linux server (on an old pc though) and I got quite a few things working but I'm now stuck with FTP. I've tried several FTP programs but I havn't yet decided with which one to stick. So any suggestions on a verry basic, easy to configure FTP Server would be apreshiated. But my main problem is, whichever FTPD I install, if I try to open a connection all i get (at the client is):
```
SSH-2.0-OpenSSH_4.6p1 Debian-5ubuntu0.1
Unable to make a connection. Please try again.

```
I have installed OpenSSH to controll the server, but (to my knowledge) I havn't done anything regarding FTP. So any Ideas which ftpd to use and how to fix it would be greatly apreciated.
Thanks :)

---

### Post by SpaceTeddy on 2008-03-14
how exactly are you trying to connect the ftp server ?

the message you get is the standard message a ssh server generates when you connect to it. So either you are trying to use sftp (which is NOT ftp in any way) or there is something wrong with your listening ports...

---

### Post by seepage87 on 2008-03-14
You said you hadn't done any configuration for your FTP server?  if you have a gui for it you could try gproftpd.  Even if you don't, I used it on another computer and copied the conf file over.  you'll need to add any relevant users you made using it (it creates them automatically), but otherwise it's pretty simple.

---

### Post by tehnad on 2008-03-14
> **SpaceTeddy said:**
> how exactly are you trying to connect the ftp server ?

I agree, how are you trying to connect to the FTP server? Are you using the command line? If so, what is the connection string that you are using to try and login?

> I have installed OpenSSH to controll the server, but (to my knowledge) I havn't done anything regarding FTP. So any Ideas which ftpd to use and how to fix it would be greatly apreciated.

Is this saying that you have no FTP services installed on the machine your trying to use FTP with? You could try something like ```
ps aux | grep ftp
``` and see if there is some form of FTP service running as well.

---

### Post by Jonamb on 2008-03-14
Ok, I've figured out what whent wrong all the time, I wanted to acces my server from school, but they have firewalls and proxys and stuff, I thought if I put SSL on port 21 (FTP wasn't firewalled) it might work, I never came round to test it and forgot it, I put ssl back on port 22 and this message stopped apperaring. Also I've installed vsftpd again and I think I'll stick with it. 
Anyways, thanks for your kind replys, and sorry for that ;)

---

