---
title: "ftp many pasv commands?"
date: 2009-01-03
forum: Server Platforms
---

### Post by Shwick2 on 2009-01-03
I was monitoring some ftp browsing and noticed that for each directory I clicked a new pasv command was sent to the ftp server.  

This meant that a new tcp connection was created on a new port every time I requested a directory.

To ensure smooth browsing I have to allow a few new tcp connections per second in iptables.

Is this how the protocol was built, or do I have vsftpd set up wrong?

---

### Post by linux_tech on 2009-01-03
To make sure vsftp is running try this-
```
netstat -a | grep ftp
```

In vsftpd.conf you can restrict vsftpd data connections to a specific range of ports by using pasv_min_port and pasv_max_port.

---

### Post by Shwick2 on 2009-01-03
Yes thanks, I know that it is running.  I also restricted the port range from 55000 to 55100.

I'm just wondering why the client sends a new pasv command for each directory it browses?  Is the client supposed to do that?  It seems like a lot of new tcp connections.

---

### Post by linux_tech on 2009-01-03
These 2 articles help explain port usage for passive mode


[didactiekinf.uhasselt.be/cn/slides/activevspassiveFTP.pdf](didactiekinf.uhasselt.be/cn/slides/activevspassiveFTP.pdf)

[http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html)

---

### Post by Shwick2 on 2009-01-03
Thanks for those, but I had already read [http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html).

I guess that means that any time any command is sent from the client to the server, be it a request for a directory listing or to download a file, a new pasv command is sent from the client to the server.

---

