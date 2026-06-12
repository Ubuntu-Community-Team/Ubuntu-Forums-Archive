---
title: "lamp stack install"
date: 2006-09-10
forum: Server Platforms
---

### Post by chipyoung on 2006-09-10
My old web server just lost it's hard drive.  I have just replaced the hard drive and installed the Ubuntu 6.06 alternate -I386 ISO, like on my old hard drive.  I am now trying to install the LAMP stack (Apache, Mysql, PHP5.  I just ran a 

"sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server" 

which should of installed these items.  I am getting a message 

"the following packages have unmet dependencies: mysql-serer: Depends: mysql-server-5.0 but it is not going to be installed" E: Broken packages

Has the repository changed?

Help!

Thank you in advance,
CLY

---

### Post by BlueFusionX on 2006-09-10
Try running this:
```

sudo apt-get update

```

That should update your repositories if they have changed.

Cheers,
Sam

---

### Post by chipyoung on 2006-09-10
BlueFusionX,

I forgot to mention that I already did that.  It didn't help. I also did a sudo apt-get upgrade to my install.

CLY

---

### Post by BlueFusionX on 2006-09-10
What's your version of Ubuntu?

---

### Post by chipyoung on 2006-09-10
ubuntu 6.06 alternate I386.  My old hard drive used the same install iso and everything worked, about a month ago. 

CLY

---

### Post by az on 2006-09-10
Make sure that the security repository is enabled.  It should already be by default.  Everything is in main.  Somethings in main are put into security when there is a security update.

---

### Post by BlueFusionX on 2006-09-10
I suggest running ```
sudo apt-get upgrade
``` to ensure that you have no out of date packages.

I also suggest that you check your sources.list file to ensure that the repositories are okay.  Generate a new one at [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")
or try the one I am including below.   To change it you will need to do ```
sudo nano
```, then press Ctrl + X, and write to /etc/apt/sources.list.
[QUOTE=sources.list]# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse[/QUOTE]

Hope I helped, 
Sam

---

### Post by chipyoung on 2006-09-10
Thank you Sam,

I was able to fix my sources.list file.  The Dapper main restricted had been commented out by the installer.  I un-commented this line and ran apt-get update.  I then ran my lamp install line, it asked for the cd again and installed everything.

I had checked the sources.list file earlier and it looked okay.  Then I found that commented line.

Thank you
Sam

Everything is wonderful again.

---

### Post by BlueFusionX on 2006-09-10
Your welcome.

Glad you got it fixed :)

---

