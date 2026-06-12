---
title: "[Webserver] How can i create a manually webserver?"
date: 2018-12-12
forum: Server Platforms
---

### Post by michaelanhvu on 2018-12-12
Hi. I just change from windows to linux. 
I want create a manually webserver in ubuntu.
How can i install from scratch.
1. Apache
2. Php 7.3
3. MySQL
4. phpMyadmin
Thanks.

---

### Post by QIII on 2018-12-13
Moved to Server Platforms.

Hello!

You are asking a question that is so involved that a "start to finish" list of things to do would not really be appropriate in a forum like this.

However, DigitalOcean has some of the best tutorials on this sort of thing, like [this one]("https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-18-04").

If you have trouble following that, we encourage you to come back to this thread and ask specific questions.

Cheers!

---

### Post by LHammonds on 2018-12-13
> **michaelanhvu said:**
> 
How can i install from scratch.

You can download source code and compile it yourself.

Or you can use standard repositories and issue install commands such as "apt install apache2"

Or you can use custom repositories for versions not in the standard repositories (but this not typical and not recommended unless you have no other option...such as needing PHP 5 on Ubuntu 18)

Or you can install collections all at once such as "apt install lamp-server^"

Or you can use droplets that make use of pre-installed/pre-configured virtual environments.

Since you are new to Linux, I will assume you do not mean "compile the code" when you mention "from scratch" but rather I guess you mean "how to install each individually"

Such as this command will install Apache (currently it is Apache version 2.4.29 on Ubuntu 18.04.1 LTS).
```
apt install apache2
```

The current stable release of PHP on official Ubuntu repositories is 7.2.  To get 7.3, you will need to add the "custom repository" like this:

```
add-apt-repository ppa:ondrej/php
apt update
apt install php7.3
```

Once you have PHP installed, you need to tie Apache and PHP together (unless it is already installed):

```
apt install libapache2-mod-php7.3
```

Since you are wanting the bleeding edge of PHP, I assume you want the bleeding edge of MySQL....which isn't MySQL anymore since that development has stagnated under Oracle's control.  The MySQL developers jumped ship and created MariaDB and it is getting a lot more tender-loving care than MySQL.  But to add the latest stable branch of MariaDB (v10.3) on Ubuntu 18.04.1 LTS, you need to add a custom repository like this (or you can [pick the version you want here]("https://downloads.mariadb.org/mariadb/repositories/")):

```

apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xF1656F24C74CD1D8
add-apt-repository 'deb [arch=amd64] http://mirror.nodesdirect.com/mariadb/repo/10.3/ubuntu bionic main'
apt update
apt install mariadb-server
mysql_secure_installation

```

Once you have the database installed, you need to tie it to Apache:

```
apt install php7.3-mysql
```

You might need to add other libraries such as php7.3-xml, php7.3-gd, php7.3-zip, etc. but that will be based on what you actually need.

But just installing the software is the easy part.  Configuring and securing it will take much longer.  You need to make sure the firewall is enabled but letting traffic through on ports such as 80 and 443.  You might need to setup SSL certificates.  You should setup fail2ban and have it monitor SSH and Apache web logs for failed login attempts if your app utilizes credentials.  The list can keep going but I think you get the point.  If this will be a public-facing server, you have a lot more to do.  If this is just a local access development server, you do not have to worry so much about it but still need to consider it for when you do run a public server.

I have not used phpmyadmin since Ubuntu 14 so I'm not familiar with how it is installed today.

The above is just a brief list of steps to point you in the right direction (maybe).  I obviously have left out a lot.  The links in my sig point to more robust installations of Ubuntu Server and MariaDB for production environments.

LHammonds

---

### Post by drvshrm on 2019-05-05
The simplest way to install web server (LAMP) in ubuntu is:

```
sudo apt-get install lamp-server^
```

---

### Post by SeijiSensei on 2019-05-06
> **drvshrm said:**
> The simplest way to install web server (LAMP) in ubuntu is:

```
sudo apt-get install lamp-server^
```

^This. You'll need to install phpmyadmin separately, though I recommend learning enough SQL to avoid the need for something like phpmyadmin.

---

### Post by LHammonds on 2019-05-06
> **drvshrm said:**
> The simplest way to install web server (LAMP) in ubuntu is:

```
sudo apt-get install lamp-server^
```
I already mentioned this but this does not solve #2 of his request.

---

### Post by SeijiSensei on 2019-05-07
And just why does he need PHP 7.3?  Is there a specific reason, like a newly-introduced function that his application demands, or just a desire to have the latest and greatest?

I just noticed that the OP is from last December and hasn't returned. Sorry!

---

### Post by LHammonds on 2019-05-09
> **SeijiSensei said:**
> And just why does he need PHP 7.3?
He didn't say but asking for a VERY specific version sounds like there is a need.

> **SeijiSensei said:**
> I just noticed that the OP is from last December and hasn't returned. Sorry!Yep, I think he got what he was looking for and moved on.

LHammonds

---

