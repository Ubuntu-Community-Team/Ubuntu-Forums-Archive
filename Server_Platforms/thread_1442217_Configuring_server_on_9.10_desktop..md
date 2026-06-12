---
title: "Configuring server on 9.10 desktop."
date: 2010-03-29
forum: Server Platforms
---

### Post by ArtemNY on 2010-03-29
Ok I'm ready to make the next step.

I'm a Linux user for just 24 hours and already installed and tuned the OS for work.
All needed plug-ins are installed, everything works perfectly well. (honestly I'm already in love with Linux and I'm not afraid of small bugs and break downs)

The only reason I chose Ubuntu over all other Linux based OS's is because I was wondering what is the easiest way to run a server and from many ppl I've heard that Ubuntu is perfect choice. However I installed not a server version, but desktop version.

[B]So the question is where can I find understandable (for a Linux newbie like myself) documentation on the easiest and the most stable way to run a small server on Ubuntu 9.10 desktop?

I need standard options like PHP, MySQL, phpMyAdmin, Apache etc well you know, for running a small server and connecting it to my domain with DNS.[/B]

The only irregular thing I need is a ffmpeg installed on the server, but well, I'll worry about it after all server parts will be brought together and work stable.

---

### Post by johngreth on 2010-03-29
The easiest way to install a server on desktop edition is to use:
```
sudo tasksel
```
and install "LAMP Server" (Linux, Apache, MySql, PHP).
You may also need "DNS Server", but you should check with your domain registrar because they may have their own name servers in which case you wouldn't need it.

To install PhpMyAdmin
```
sudo apt-get install phpmyadmin
```

ffmpeg:
```
sudo apt-get install ffmpeg
```

You can also get Webmin from [http://www.webmin.com/](http://www.webmin.com/). Get and run the .deb file (debian package)

Ubuntu Server Documentation: [https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)

General Documentation: [https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)

More Community documentation: [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Seeing as you are new to Linux, I agree that it was a good idea to use Ubuntu desktop as Ubuntu server edition is command prompt only, but Server edition is faster and more efficient so that may be something to look into as you become more familiar with Linux.

Welcome to the Linux community. I hope you like it here.

---

### Post by ArtemNY on 2010-03-29
Yeah already found all the info online. And already installed it.
But big THANKS anyway!

I didn't know I'll be so exited to do all this crap! This is really really interesting to learn.


BUT now I get 401 error and it doesn't want to let me in myphpadmin so learning is in a progress! ;)

---

### Post by johngreth on 2010-03-30
It is exciting, isn't it? The first time I installed Ubuntu Server Edition with just a command prompt I felt like I just took the training wheels of, but I was successful. It is a great feeling.

As for PhpMyAdmin, it is probably that /etc/apache2/apache2.conf only allows access from 127.0.0.1 or localhost, but I'm no expert in that.

Anyway, I wish you the best of luck in your adventure.

---

### Post by s_ø on 2010-03-30
You get the 401 error on every page? or just on [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

401 is unauthorized.
What is the full error text?
Have you enabled mod_auth?

---

