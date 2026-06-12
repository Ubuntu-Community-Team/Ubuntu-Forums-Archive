---
title: "How do I securely setup SFTP?"
date: 2015-08-22
forum: Security
---

### Post by Harley_Frank on 2015-08-22
I am trying to setup SFTP, but I can't login FTP with my credentials. I get a 530 auth error. So I create a new user with sudo rights, but I can't go into any other directory except the home folder of that user. How do I get the ssh keys?

I am running a Digital Ocean VPS. It has Ubuntu LEMP 14.04 LTS 2GB RAM | 40GB SSD. Current users are root and ftpuser.

Additional Packages include Ajenti and Ajenti-V, SpamAssassin, mail server through Ajenti, RainLoop, and Composer.

---

### Post by TheFu on 2015-08-23
**ssh-keygen** are made on the client, then use the **ssh-copy-id** tool to push the public key to the remote server.  Then you can ssh and sftp from the client to the server. The server must have the openssh-server package installed and the ssh service running.  If connections are prevented ... by default they are not ... lets just hope it isn't an issue today.

As to securing sftp - normal ssh security techniques are sufficient. 
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

---

### Post by Harley_Frank on 2015-08-23
That would be awesome if I had another server I could send it to. My only option is to download it straight from the server via FTP. Is there a way to get root access and get the file I need?

---

### Post by TheFu on 2015-08-23
The client is your machine at home.
The other questions seem specific to the VPS company. Ask them.

---

