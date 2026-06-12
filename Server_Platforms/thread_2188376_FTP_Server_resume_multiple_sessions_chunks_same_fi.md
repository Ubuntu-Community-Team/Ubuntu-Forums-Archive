---
title: "FTP Server resume multiple sessions chunks same file download"
date: 2013-11-16
forum: Server Platforms
---

### Post by MurphyMt on 2013-11-16
Hi Guys,

I have been trying to find a solution on how to copy big files from my hosted server in Germany to Australia.
I'm running an ubuntu server and have tried both vsftpd and proftpd and I only seem to be able to get my download tool to open 1 session or chunk to the file.

example. I'm trying to download a 1gb file from the server to my pc as fast as possible. So I want an ftp server that can host the file but allow for multiple chunks eg 5 sessions of 200mb each or more. In that way I will be getting 5 tcp sessions of 200 to 400 kb each thus getting the file downloaded 5 times faster.

I have done this in the past with an http server on ubuntu hosting the file from the ftp folder and then using getright to download the file and then telling getright to pulling multiple sessions of the file and that works but is quite a painful to setup.

Current testing I'm trying is with ubuntu server vsftpd or proftpd with jdownloader client or filezilla client.

Another idea I'm thinking on is a folder replication from my ubuntu ftp folder to a folder on my pc hopefully supporting multiple sessions copy of the same file but different segments. ie Repliweb ([http://en.wikipedia.org/wiki/RepliWeb](http://en.wikipedia.org/wiki/RepliWeb)) but free and for ubuntu to windows.

Thanks looking forward to your positive feedback.

---

### Post by nerdtron on 2013-11-17
I believe jdownloader or the "DownThemAll" extension for firefox will be able to open multiple segments to help you download faster.

---

### Post by Lars Noodén on 2013-11-18
I would use rsync for large files and especially for anything that is likely to get interrupted and need resuming.  Since it only transfers the differences, it automatically picks up where it left off if resumed after being interrupted. 

```

rsync -av user2@remote.server.org:/path/to/files/ /local/path/to/files/

```

Also, because it uses SSH, the login and transfer are secure.  I would definitely say to [avoid FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).

---

### Post by MurphyMt on 2013-11-19
Hi Guys,

thanks for your feedback, greatly appreciated. I will give them both a try.

Regards Warren Murphy

---

### Post by MurphyMt on 2013-11-19
Thanks mate [COLOR=#000000]DownThemAll rocks !!! thanks for that tip :)[/COLOR]

---

