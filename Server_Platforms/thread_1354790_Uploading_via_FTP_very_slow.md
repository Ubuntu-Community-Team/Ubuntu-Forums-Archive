---
title: "Uploading via FTP very slow"
date: 2009-12-14
forum: Server Platforms
---

### Post by Stan* on 2009-12-14
If I upload to my Ubuntu server at home via FTP (vsftpd), uploading is very slow. And with slow I mean 5 minutes to upload 1 file of 4 KB.
My server doesn't have a swap partition, I have to configure that. But when I check the performance of the server via SSH I see only 49% of a total of 512 MB memory.

What is the cause of the slow FTP transfers?

Thanks in advance.

---

### Post by Stan* on 2009-12-14
Hmm...It's the external route that slows down the transfer. When I connect locally (on the same network) to the server everything is going fine.

What could slow down the transfer? Maybe the firewall on the server, or is it the router? The firewall on the router is off though....

---

### Post by Fire_Chief on 2009-12-14
What is your up/down Internet bandwidth at home? Are you running any other services from your network or apps that would use bandwidth (file sharing, etc.)?

---

### Post by Stan* on 2009-12-14
The Internet speed  of the server is 8 megabit down and 1 megabit up. Should be fast enough, shouldn't it? No other computers are running, only the server is turned on. The server runs Apache, MySQL,  vsftpd and Open SSH. These are the only roles and I'm the only user.

---

### Post by Fire_Chief on 2009-12-15
Since you have SSH open, how fast does a SCP session go for the same file size?
Has the slowness always been happening or did it just start? Also, when you are uploading to your server from outside the local network, what is the upload speed where you are sending from?

Sorry to ask so many questions but there are a lot of variables at play here.

---

### Post by Stan* on 2009-12-15
I understand, thanks for your reply.

How can I test the speed of a SCP session? I don't even know what SCP is. The transfers always have been slow, since the beginning. The upload speed from outside the network is good: Around 1.5 - 2 megabyte per second.

---

### Post by Fire_Chief on 2009-12-15
SCP stands for Secure Copy and is another way to transfer files. The syntax looks like this:
From a local system to a remote system```
scp <filename or directory> user@RemoteSystemIP:/target/directory/path
```
If you are sending as a regular user, you will probably be restricted as to where you can save files (due to write permissions on directories). The easiest way is to save it in the home folder of the user you connect as or a subfolder there.
SCP should show you a transfer rate during and after the file transfer (unless I'm really not thinking straight).

FYI, you can use WinSCP [http://winscp.net/eng/index.php]("http://winscp.net/eng/index.php") to transfer using a GUI from Windows.

Cheers!

---

### Post by Stan* on 2009-12-15
Thanks for your reply.

I've tried it, but I'm at home now. Obviously, the transfer goes very fast at a average of 10 MB/s with a file of 50 MB. I'll try again tomorrow, when I'm at school. See what the speed is then. Thank you.

---

### Post by Stan* on 2009-12-23
Alright, I tried it outside the network. And it's still going fast. The SSH transfer ended with this message:

IES_Network.pdf                                                          100% 1298KB   1.3MB/s   00:00  

So I guess there's a problem with vsftpd, is'nt it?

Thanks for your reply.

---

### Post by hessiess on 2009-12-23
FTP is an old and weirdly designed(by modern standards) protocol which does not work well with modern networking infrastructure (NAT routers). As you can use SSH/SCP I would recommend dumping FTP completely and just using SCP/SFTP(SSH file transfer protocol) instead, they use a more modern design and are a lot more secure.

---

### Post by Stan* on 2009-12-23
Thanks for your reply. Do I need to install extra packages to be able to login with SFTP? Or can I just login via port 22 with my local account.

---

### Post by hessiess on 2009-12-23
> **Stan* said:**
> Thanks for your reply. Do I need to install extra packages to be able to login with SFTP? Or can I just login via port 22 with my local account.

The OpenSSH server includes an SFTP server, which you can use with your normal SSH login. Though you will need a SFTP client.

with the command line client you can use:
```

sftp <user>@<ip OR host name OR domain name>

```

---

### Post by Stan* on 2009-12-23
Nice! Thank you for your reply. It seems this works perfect! How can I configure SFTP? Can I limit the user to their own home-folder like I can do with vsftpd? Can I safely remove vsftpd now?

EDIT
I worked it out. SFTP-users are now limited to their own home folder. Is it safe to remove sftpd now?

EDIT 2
Hmm, no. Users are limited to their own home folder, but they can only read and modify existing files. They can't create new files or folders...

EDIT 3
WTH!!! All my files are gone....I just followed [these steps](http://ubuntuforums.org/showthread.php?t=1057657&highlight=chroot+sftp) for an existing user with an existing home folder...A home folder with files in it...All gone! Where could they be?

---

