---
title: "Unattended MySQL Install?"
date: 2008-12-02
forum: Server Platforms
---

### Post by ShakataGaNai on 2008-12-02
I would like to create a script to install MySQL (unattended, or non-interactive or what ever you'd like to call it).  The problem is right now if I enter "apt-get -y install mysql-server-5.0" I get the whiptail (blue) configuration screen asking for my desired password.  I've dug through the man pages on apt-get, dpkg (and family) and wajig, I've also spent a few hours googling. I simply can't find any directions on how to get rid of this configuration question, or "pre-fill" it.

Any suggestions?  Thanks...

---

### Post by Philio on 2008-12-03
As an alternative you could download the packages from MySQL and quite easily script the installation.

I have a script that downloads, compiles and installs MySQL Cluster releases. There is more reason for this than simply doing it unattended though. Latest version is 6.3.19, latest available pre-compiled is 6.3.17 and there is no 64 bit package, so I have to compile from source to have the latest patches.

You could write a script that downloads the latest MySQL packages and installs them. It's a very simple process doing a manual install using the pre-compiled packages. Plus you can use the latest version (5.1.30 is current GA version vs 5.0.67 which is in the Ubuntu repos).

The process would be:

wget the package
tar to extract
copy files to /usr/local/mysql
groupadd mysql
useradd -g mysql mysql
chown the files
run the database installer script (can't remember the name)
copy the mysql.server init script to /etc/init.d/
update-rc.d mysql.server defaults

---

### Post by ShakataGaNai on 2008-12-06
The answer is:

# export DEBIAN_FRONTEND=noninteractive

---

### Post by canuckistani on 2010-04-29
I've been trying to script a non-interactive install of MySQL, and the above environment variable has no affect on suppressing whiptail. What you really need to do is:

[http://serverfault.com/questions/19367/scripted-install-of-mysql-on-ubuntu](http://serverfault.com/questions/19367/scripted-install-of-mysql-on-ubuntu)

```

echo mysql-server-5.0 mysql-server/root_password password PASSWORD | debconf-set-selections
echo mysql-server-5.0 mysql-server/root_password_again password PASSWORD | debconf-set-selections

```

This is a bit hacky but works well for me, even via a capistrano script.

---

