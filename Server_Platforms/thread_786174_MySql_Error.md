---
title: "MySql Error"
date: 2008-05-07
forum: Server Platforms
---

### Post by NLFSoftware on 2008-05-07
Hello all,

Yesterday I have installed Ubuntu 8.04, and everything works Like a charm, until today I turn on the machine and the nigthmare begins...

After a lot of reading and googlelazing I found the information that the MySql is having some issues with ubuntu and others Linux distros, the big issue is related with the socket, that should be on the /tmp/ folder but it isn't.

The way I found to know if the problem is really related with the socket and not with is:

1º install mysql administration tool
2º try to connect with mysql, for some reason Mysql Administration tool use the real path of the socket and works.
3º if you are able to connect to your MySql then copy the path to the socket
4º open the shell and type:
 
```
sudo ln -s /var/run/mysqld/mysqld.sock /tmp/mysql.sock
```

in this case /var/run/mysqld/ is the correct path to the socket that is displayed on Mysql Administration Tool

And its done, well almost, the true is that you will need to do that every time you start Ubuntu.

I not a Linux Guru, and this code I fond it somewhere on the netosphere, thanks for the guy that wrote that and sorry for don't mention where and who did it, but I really don't remember where I saw it.

Well for issue be resolved for good, I ask for you guys how I add that line to the boot sequence?

Thanks in advance and I hope my contribution can help someone.

---

### Post by cdtech on 2008-05-07
Just add the script to your /etc/rc.local file less the sudo part.

---

### Post by NLFSoftware on 2008-05-08
Thanks cdtech!

I do that and is working!

Now I can sleep in peace again :)

Thanks a lot

---

