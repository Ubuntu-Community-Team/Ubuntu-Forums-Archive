---
title: "installing apache on ubuntu 12.04"
date: 2013-01-12
forum: Server Platforms
---

### Post by ubto66 on 2013-01-12
I want to install wordpress 3.5 on my computer.
I do not want the local host to be a website server for the internet.
I want to use the server to develop wordpress websites locally on my computer.

I found this probably outdated  website
[http://gerry.ws/2008/12/436/how-to-install-apache-mysql-php-on-ubuntu-linux-desktop.html](http://gerry.ws/2008/12/436/how-to-install-apache-mysql-php-on-ubuntu-linux-desktop.html)
I could not find a lamp in synaptic package manager.
How can I install apache mysql and php using synaptic package manager?
If you know how, is there any security settings I should make?

Thanks.

---

### Post by chadk5utc on 2013-01-12
This should install everything your looking for if your installing into an existing OS
> sudo apt-get install php5 mysql-server apache2
And to secure things I suggest using UFW or directly configure iptables for local only access
[http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)
Or the preferred method would be to download the server iso and install it from CDROM

---

### Post by mörgæs on 2013-01-12
```
sudo apt-get install lamp-server^
```

Remember the hat at the end of the command.

---

### Post by Cheesemill on 2013-01-12
> **mörgæs said:**
> ```
sudo apt-get install lamp-server^
```Remember the hat at the end of the command.
I think you'll find it's called a caret :)

For more information read the relevant sections in the official server documentation...
[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

---

### Post by mörgæs on 2013-01-12
Indeed it does:
[http://en.wikipedia.org/wiki/Caret](http://en.wikipedia.org/wiki/Caret)

Thanks for pointing put.

---

### Post by ubto66 on 2013-01-13
Thank you for the answers.

I used this instruction
[http://tuxtweaks.com/2012/04/installing-lamp-on-ubuntu-12-04-precise-pangolin/](http://tuxtweaks.com/2012/04/installing-lamp-on-ubuntu-12-04-precise-pangolin/)
Testing phpMyAdmin
it says
log in with the username **root** and the root password that you created earlier.
Q what is the username root or where do I find it?

If I want to remove lamp how do I do it?

Thanks.

---

### Post by Cheesemill on 2013-01-13
When you installed mysql you were asked for a password for the mysql root user.

---

### Post by ubto66 on 2013-01-13
cheesemill
thank you for answering. The psswd I knew, and I figured out, 
that user name was root.

Do you know how to remove lamp?

---

### Post by sandyd on 2013-01-13
moved so server platforms

---

