---
title: "FTP and Apache problems"
date: 2011-05-07
forum: Server Platforms
---

### Post by Qzen on 2011-05-07
Hello.

Since i upgraded to 11.04 on my Server edition i have been experiencing some problems with my FTP-server and Apache.

Apache just says that the page is "forbidden" if I'm not logged in on the server, which means i need to go to the server and physically log in or i can do it trough ssh but then when i close my ssh client on my work computer the page is "forbidden" again.

And i cant seem to reach the FTP-server from an external address so i need to be in the network to access it.

It says something like:
```
An error occurred opening that folder on the FTP Server. Make sure you have permission to access that folder.

200 Switching to ASCII mode.
227 Entering Passive Mode (192,168,0,194,233,166)
```

So i need some assistance to get my system running again, thanks in advance.

/Adam

---

### Post by Lars Noodén on 2011-05-07
Since you have SSH running it is possible to turn off FTP and use [SFTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols) instead.  Can you give that a try?  You also have [SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP) already installed.

---

### Post by Qzen on 2011-05-13
Sorry for my inactivity, but I've been away.

I'll try using the SFTP, after i read the wiki about it and then ill report back.

---

### Post by Qzen on 2011-05-13
Thanks, the SFTP worked fine.

Now there's just the problem with the webserver.
It's almost certainly a problem regarding the permissions set for the user on the system, but i dont know how i can correct it.

Any ideas?

---

