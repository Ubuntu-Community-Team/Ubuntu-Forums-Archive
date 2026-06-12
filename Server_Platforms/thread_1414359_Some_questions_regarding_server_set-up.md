---
title: "Some questions regarding server set-up"
date: 2010-02-23
forum: Server Platforms
---

### Post by Avarus on 2010-02-23
Hello everyone,

Currently I'm trying to set-up an Ubuntu (v9.10) based server, and I'm running into a few issues I can't solve by myself. I have installed Ubuntu along with LAMP, phpmyadmin, vsftpd, openssh-server and some more. I got the stuff up and running, I got a bit into the commands and I can see the index file I created. But....


- I can only successfully connect through the firewall when in active mode using FileZilla

- The FTP client can only access folders when their rights are set 777, though 644 should do in my opinion

- When I upload a file, its rights are 600 by default, while I've set the upload folder to 777. I have to change that manually for each file I upload


I've got Apache (port 80) and vsftpd (port 20-21) forwarded on my router, I believe that was ok. Also ufw is configured to allow connections on several default port like 80, 20, 21 etc.

I hope someone could be as kind to help me out with this...
Thanks in advance

---

### Post by tlsarles on 2010-02-23
Havn't done much with the FTP server, so I can't help you there. Personally, I always use SFTP, which is integrated with SSH. Try using FileZilla with SFTP, and make sure you have a port forward on the SSH port.

As for rights... Maybe this is review, but...

Lets break down 644 as you are saying.

6 = Gives Read / Write rights to the file owner
4 = Gives Read Only Access to the group
4 = Gives Read Only Access to everyone else

So, if you can't write a file, you are probably not logging in as the owner. You may check this with an 'ls -l', and use chown to set ownership. If you are the owner, and it still won't write, it probably has something to do with the FTP service. Again, I recommend just doing file transfer through SSH, as it works as expected, and is greatly more secure.

---

### Post by Avarus on 2010-02-24
Thanks for the tip for using SFTP, but I'm trying to configure the server in such a way as most hosting providers have done it, so I'd like to get FTP working. I've got the upload directory chowned to the FTP user, so that user should be able to read and write, while everyone else only needs to read those files (why allowing to let them write into your webpages?)

---

### Post by Avarus on 2010-02-25
Ok I'm using proftpd now, which solved most of the issues, but now I'm experiencing a very slow login. It seems to get stuck on the welcome message for like 10 seconds (and it doesn't display the welcome message either). I've tried to add 

```

IdentLookups off
UseReverseDNS off
```

but that didn't help much either. Any ideas?

---

