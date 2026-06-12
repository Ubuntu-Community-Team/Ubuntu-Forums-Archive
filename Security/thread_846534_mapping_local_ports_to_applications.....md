---
title: "mapping local ports to applications...."
date: 2008-07-01
forum: Security
---

### Post by Mia_tech on 2008-07-01
is there a way to know what connections or ports are related to what application....let me explain, for example when I use netstat to find out my open connections.

```
jorge@ubuntu-box:~$ netstat | grep tcp
tcp        0      0 ubuntu-box.lakesh:56229 2k3server-:microsoft-ds ESTABLISHED
tcp        0      0 localhost:4443          localhost:35543         ESTABLISHED
tcp        0      0 localhost:35543         localhost:4443          ESTABLISHED

```

I know that everything that has "www" is web app usually connection to the browser, or pop3 email, but there are cases where it doesn't indicate an application just the port number and I would like to find a way to map that port to the application that is using it... of course without having to search google for ports ;0)

any help appreciated

thanks

---

### Post by weresheep on 2008-07-01
Hello,

netstat offers a -p argument to print process ID and name along with the port number. You need to have root privileges to see non user processes. So try...

```
sudo netstat -p
```

See the man page for more options/information...

```
man netstat
```

-weresheep

---

### Post by brian_p on 2008-07-01
> **Mia_tech said:**
> is there a way to know what connections or ports are related to what application....

e.g.

```
sudo lsof -i :631
```

---

