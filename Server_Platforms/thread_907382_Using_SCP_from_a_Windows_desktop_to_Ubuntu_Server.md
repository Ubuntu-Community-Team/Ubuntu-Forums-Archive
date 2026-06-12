---
title: "Using SCP from a Windows desktop to Ubuntu Server"
date: 2008-09-01
forum: Server Platforms
---

### Post by not28 on 2008-09-01
Hi guys,

I'm working on an Ubuntu Server (my first time working on any type of server--I'm a rookie), and I haven't bothered with setting up FTP yet but I can SSH remotely. I'm sitting at a Windows XP box and I'd like to copy a folder from my desktop to the server using SCP. I'm not sure how the syntax would be done, though. I've tried this
```
sudo scp -r c:\foldername username@ip.add.res.s:/path/to/newfolder
```
And the response I get is
```
ssh: c: name or service not known
```
Clearly there is another way to point to my local Windows C: drive, but I can't seem to figure it out. Any thoughts?

---

### Post by in-dust-rial on 2008-09-01
just for quick,...
change into the folder to cope and say from this folder:
```

sudo scp -r * username@ip.add.res.s:/path/to/newfolder
```
but it would be interesting to know where you enter the command ;D

p.s.: * is the kleeny and matches alle possible patterns.
that is he copies all files in the directory you are in!

---

### Post by moonpup on 2008-09-01
If I understand you correctly, you are going about this the wrong way. Windows has no built in ssh or secure copy/transfer utilities by default. What you need is either winscp, putty or something like filezilla.

Anyway, head over to [http://www.winscp.net](http://www.winscp.net) and grab that. It's a gui ftp client that can also be used for ssh/sftp/scp.

Try moving your files that way...

---

### Post by not28 on 2008-09-01
> **moonpup said:**
> If I understand you correctly, you are going about this the wrong way. Windows has no built in ssh or secure copy/transfer utilities by default. What you need is either winscp, putty or something like filezilla.

Anyway, head over to [http://www.winscp.net](http://www.winscp.net) and grab that. It's a gui ftp client that can also be used for ssh/sftp/scp.

Try moving your files that way...

Oops, forgot to mention that I am using Putty on the Windows box. But I'll try winscp. thanks :)

---

