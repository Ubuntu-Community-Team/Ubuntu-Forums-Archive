---
title: "PHP Not working"
date: 2018-06-08
forum: Ubuntu, Linux and OS Chat
---

### Post by gtdinosaur on 2018-06-08
The php websites on my personal apache2 server are not working (I am trying to access PHPMyAdmin) and it shows up text. When I try to access php on this website, it works just fine. Can anyone help?

---

### Post by SeijiSensei on 2018-06-08
Check to make sure libapache2-mod-phpN is installed on the server.  The "N" depends on the version of PHP installed.  What version of Ubuntu are you running?  

The [simplest and most reliable way]("https://help.ubuntu.com/community/ApacheMySQLPHP") to install Apache and PHP, and to get MySQL as an extra bonus, is to use

```

sudo apt update
sudo apt install lamp-server^

```

which will install all three applications and the various necessary packages that link them together. Make sure to include the tilde ("^") at the end.  Try running that.  It will upgrade apache and PHP if needed and install everything else in the package.

---

