---
title: "Accessing MySql in Ubuntu Virtual Server from Windows"
date: 2007-10-09
forum: Server Platforms
---

### Post by albrad84 on 2007-10-09
I have an Ubuntu Server Virtual Machine installed on my Windows computer using MS Virtual PC and I am trying to access MySql on the virtual machine from Windows.  I am able to access apache, etc from the web browser and also share files using samba, but I cannot get MySql to work (it works fine from within the ubuntu VM).

Any suggestions?

Thanks in advance

---

### Post by fallingleaf on 2007-10-09
What exactly happens when you try to access?  My first thought is the you have to grant permission for the Windows machine's domain to access the MySql server.  For example, on a default install of MySQL, only the user root@localhost has permission, so root can't login from another host.  You'll have to check the MySQL docs for how to do it because I don't remember the syntax.

---

### Post by primski on 2007-10-10
You can do a 'rename' on the user, to change to localhost to any host with
```

 RENAME USER 'root'@'localhost' TO 'root'@'%'

```

or you can add a new user with
```

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%'
IDENTIFIED BY 'some_pass' WITH GRANT OPTION;

```

---

