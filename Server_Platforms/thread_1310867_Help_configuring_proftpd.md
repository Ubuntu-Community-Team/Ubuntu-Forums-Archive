---
title: "Help configuring proftpd"
date: 2009-11-02
forum: Server Platforms
---

### Post by julifos on 2009-11-02
I've been two days reading tutorials but I'm still unable to do a very simple thing: deny connections to everybody, except for the users I choose with the permissions I wish.

I've changed the config file thousands of times, but I think I still don't understand the basics. I'm pretty new to Linux, too, and absolutely new to remote system admin (I'm configuring this FTP server for my new domain). I already installed a lot of stuff, but I'm stuck with the FTP server...

Any help is welcome!

---

### Post by royer10r on 2009-11-14
make sure you are restarting the ftp service after each time you edit the config file.
```
sudo /etc/init.d/proftpd restart
```

---

