---
title: "Problem installing LAMP"
date: 2012-09-28
forum: Server Platforms
---

### Post by kedar5 on 2012-09-28
Hello,

I am installing LAMP server using the following page.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I have installed tasksel.
But when I try to install lamp-server using tasksel, I get the following error - 
```

#sudo tasksel install lamp-server
tasksel: aptitude failed (100)

```
Kindly help. Thanks.

---

### Post by Lars Noodén on 2012-09-28
You can take a shortcut with [apt-get](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html)

```

sudo apt-get update
sudo apt-get install lamp-server^ 

```

---

### Post by mujahied on 2012-10-21
sometimes u cannot find the lamp server aswel in the rep

---

