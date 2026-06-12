---
title: "Could SSH kill my vsftpd chroot?"
date: 2008-02-05
forum: Server Platforms
---

### Post by theox26 on 2008-02-05
I have a server set up with a vsftpd server and ssh access as well.

vsftpd is set to use local accounts for ftp login and has them chroot'ed except for one master account.  This works fine in all ftp clients I've tried except somehow, Filezilla gets past it and will give them access to EVERYTHING!:confused: the whole file system.

The only thing I can see is that filezilla logs on using sftp.  I know that is connected with ssh.  So, is there anyway to disable sftp or at least chroot my sftp users without chrooting at least one ssh user.

I've searched all over and haven't found anyone asking this, so I may be wrong with my assumptions.  Let me reiterate that ftp works as planned, the users are chrooted as planned and can't even see the other home directories.  My vsftpd.conf file is set up properly and how I want it.

Thanks in advance for any help figuring this out.

---

### Post by netscribe on 2008-02-05
Well, I'm not sure if we have the same issue or not.   I have recently allowed my users to have normal SSH access to the box.  When they use WinSCP or just SCP, they get access to the whole filesystem, which is not what I was looking for.

So, what I'm working on now is using[ Jailkit ]("http://olivier.sessink.nl/jailkit/") :KS and using its utilities to get people access to ONLY their chrooted shells, which only have jail-kitted apps they need:  like vi, nano, etc.

I'm not sure if that's what you're aiming for in the FTP world or not. . ?

---

### Post by theox26 on 2008-02-05
Thank you very much.  I had looked at Jailkit once but thought it was more than I needed, and I was right.  

After thinking it was a ftp problem and then realizsing it was sftp causing my headaches, I finally found what I needed.

[https://help.ubuntu.com/community/AdvancedOpenSSH#head-bb07462f59fb73d2b3e6b241672a0d09947e619b](https://help.ubuntu.com/community/AdvancedOpenSSH#head-bb07462f59fb73d2b3e6b241672a0d09947e619b)

This explains how to limit SSH to just one or two users, but still allow ftp access to everyone else who is supposed to have it.  That is exactly what I needed and it works perfectly.

Though thanks for posting what you found, I'm sure it could help someone else down the line.

---

