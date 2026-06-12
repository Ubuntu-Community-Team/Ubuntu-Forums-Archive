---
title: "transfer files to ubuntu 8.04 server (samba) from another ubuntu machine"
date: 2008-05-05
forum: Server Platforms
---

### Post by lasing all day on 2008-05-05
I installed ubuntu 8.04 server on my desktop computer and want to know how to put files onto it from other computers (another partition of that some computer and my laptop, and farther on down the line my father's windows computers). The posts I find are only about using Samba servers on the desktop setup, but I cannot find anything on transferring files from one ubuntu machine to an ubuntu server machine! I used this site to install my ubuntu 8.04 server: [http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/) and I referenced some stuff from this: [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html)

To sum up, how do I transfer files to the server?? This will be done from separate partitions on the same desktop computer (an AMD Athlon 64 processor, GeForce6100SM-M motherboard, ATI Radeon X1300 Pro graphics card thing I made) and also from my laptop (Dell Inspiron 6000). On down the line, this will be done from my Father's Windows machines. Music and video will be transferred to this server, if the purpose is desired. THANKS ubuntu community!

---

### Post by bluefrog on 2008-05-05
either configure samba shares on your ubuntu server and access them from windows, or share folders on windows and access them from ubuntu.

---

### Post by bwhaley on 2008-05-05
It really depends what your requirements are. Do you need:

[LIST]
[*]Simple interface for non-technical users?
[*]No-nonsense installation?
[*]Strong Security?
[/LIST]

If you need something that is easy for your average Windows user, Samba is the right answer. They will be able to map shares as if it's a Windows file share.

FTP is a protocol meant for file transfers. It might be ideal for an in-home network where security isn't important.

SSH is normally used as a remote shell protocol (i.e. remote access to your server), but it also has built-in file transfer methods. You can use SCP or SFTP to transfer files to and from the remote system, just like FTP but with high security. There is excellent windows support as well. WinSCP is one Windows-basednfile transfer client that works very well.

---

### Post by lasing all day on 2008-05-05
are you saying there is something easier than samba I should use? my father and sister would just be transferring their albums, and each is an average windows user. they live an hour away from me, so it is not in-home setup. do you recommend moving those files with samba or with scp/sftp or this hypothetical simpler thing? btw, i totally forgot about scp.

---

### Post by lasing all day on 2008-05-05
thanks bluefrog! "configure samba shares" was EXACTLY what i needed. somehow my googling overlooked it.

---

### Post by lasing all day on 2008-05-05
Okay, so after spending a day working on that I got to a point where the smbclient is fine and installed. I know how to actually move files to the server. I know that I just use ssh terminal commands to move the files. However, I cannot find the server! I should have realized I would need a router to get these files. Is that the only way?

Even then, I should at least be able to move files from another partition on the desktop computer. But do I have to go to System > Network and change Network settings to do that?

Basically, how do I find the server???

---

