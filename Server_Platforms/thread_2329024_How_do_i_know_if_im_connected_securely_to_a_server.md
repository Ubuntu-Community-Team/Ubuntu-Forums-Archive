---
title: "How do i know if im connected securely to a server running vsftpd?"
date: 2016-06-27
forum: Server Platforms
---

### Post by Pandee on 2016-06-27
Hello~

I'm setting up an Ubuntu server running 14.04  LTS  and i just recently added vsftpd.

How do i know if I'm connected securely to my server when using filezilla?

---

### Post by howefield on 2016-06-27
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by Pandee on 2016-06-27
> **howefield said:**
> Thread moved to the "*Server Platforms*" forum for a better fit.

Thank! (Sorry about the bad placement)

---

### Post by Pandee on 2016-06-27
Hello, I restarted the server and when i try to log back in via PuTTY it gives me a "Network error: Connection timed out" - The last i changed was vsftpd settings.

Steps to troubleshoot?

---

### Post by Habitual on 2016-06-27
"Securely", I believe it going to use the sftp protocol.
ftp and secure and telnet-server are not words that go together.

How are you connecting? Passwords over ftp are insecure.

Please see
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) and 
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Pandee on 2016-06-27
Hello!

I have a putty client that connects to me via tightVNC.

---

### Post by steeldriver on 2016-06-27
What vsftpd settings did you change, and how?

Do you have physical access to the server? if so you can log in locally and check what's listening on what ports and on what interfaces using

```

sudo netstat -nlpt | grep LISTEN

```

or for sshd specifically

```

sudo netstat -nlpt | grep sshd

```
or
```

sudo lsof -i :22

```
(replace :22 with the actual port, if you are using a non-default port).

---

### Post by nerdtron on 2016-06-27
If you are using putty, then you're most likely using SSH to connect to the server. SSH is pretty secure. As for vsftpd, what do you use to connect? Filezilla? What protocol does it show on the connection log when you try to connect?

---

### Post by Habitual on 2016-06-27
You can use the netstat command to check if you are connected...
From the desktop you VNC ***into***, open a terminal and issue:
```
netstat -atn | grep :21
```

or 
```
lsof -i | grep ESTABLISHED
```

There are dozens of methods to determine if the connection is "there".
Have a look at [http://stackoverflow.com/questions/106234/lsof-survival-guide](http://stackoverflow.com/questions/106234/lsof-survival-guide)

That's where those 2 gems came from.

---

### Post by Habitual on 2016-06-27
I reported this post as [duplicate.]("http://ubuntuforums.org/showthread.php?t=2329038")
Hopefully, they'll get merged. :)

---

### Post by slickymaster on 2016-06-27
> **Habitual said:**
> I reported this post as [duplicate.]("http://ubuntuforums.org/showthread.php?t=2329038")
Hopefully, they'll get merged. :)

Threads merged.

---

### Post by Pandee on 2016-06-28
Ah I see, thankyou for the merge! Thanks everyone, I now can see that the vsftpd  service and such is actually working with those commands! I also didn't realize i had to connect to sftp in filezilla with port 22! Thank you very much once again!

Last questions! Now that i know that I'm connecting securely with filezilla, how do i go on about disabling the normal ftp (or is it the default one?), that is the one using port 21 -20 ?

---

### Post by steeldriver on 2016-06-28
Confusingly, v**s**ftp **isn't** sftp - it's ftp**s**

Unless you need to support legacy ftp/ftps clients, I'd simply remove (uninstall) vsftp and continue to use the sftp that's provided via the default openssh-server

See for example [https://www.eldos.com/security/articles/4672.php?page=all](https://www.eldos.com/security/articles/4672.php?page=all)

---

