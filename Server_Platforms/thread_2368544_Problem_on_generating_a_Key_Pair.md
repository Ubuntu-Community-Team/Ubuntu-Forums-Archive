---
title: "Problem on generating a Key Pair"
date: 2017-08-12
forum: Server Platforms
---

### Post by satimis on 2017-08-12
Hi all,

Ubuntu 16.04 servr

Add Public Key Authentication:

# ssh-keygen```

Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): /home/satimis/.ssh/id_ras
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Saving key "/home/satimis/.ssh/id_ras" failed: No such file or directory

```

Whether I need to create /home/satimis/.ssh directory manually?

# ls -a```

.  ..  .bash_history  .bashrc  .nano  .profile  .ssh

```

# ls -al /home/satimis/```

total 28
drwxr-xr-x 3 satimis satimis 4096 Aug  4 18:19 .
drwxr-xr-x 3 root    root    4096 Aug  4 15:58 ..
-rw------- 1 satimis satimis  721 Aug 12 13:38 .bash_history
-rw-r--r-- 1 satimis satimis  220 Aug  4 15:58 .bash_logout
-rw-r--r-- 1 satimis satimis 3771 Aug  4 15:58 .bashrc
drwx------ 2 satimis satimis 4096 Aug  4 15:59 .cache
-rw-r--r-- 1 satimis satimis  655 Aug  4 15:58 .profile
-rw-r--r-- 1 satimis satimis    0 Aug  4 16:00 .sudo_as_admin_successful

```

Please advise.  Thanks

Regards
satimis

---

### Post by darkod on 2017-08-12
I always accept the suggested default location (I never enter a file name and path manually) and it works great. When you are creating a private key with ssh-keygen it suggest the default location for the file (inside the home folder of the user running the command).

SSH is very sensitive about correct permissions and you might have problems later if trying to save files elsewhere and don't get it right.

According to the output you are logged in as root but trying to put the key in satimis home folder. Why? Simply log in as satimis and run the command, it will create the key correctly in that users home folder. Don't complicate something that is very simple.

---

### Post by satimis on 2017-08-12
> **darkod said:**
> I always accept the suggested default location (I never enter a file name and path manually) and it works great. When you are creating a private key with ssh-keygen it suggest the default location for the file (inside the home folder of the user running the command).

SSH is very sensitive about correct permissions and you might have problems later if trying to save files elsewhere and don't get it right.

According to the output you are logged in as root but trying to put the key in satimis home folder. Why? Simply log in as satimis and run the command, it will create the key correctly in that users home folder. Don't complicate something that is very simple.
Hi,

Thanks for your advice.

Hi,

I followed below document to perform an initial server setup;

Initial Server Setup with Ubuntu 16.04
[https://shiftnrg.nl/docs/delegate/linux/initial-server-setup-with-ubuntu-16-04](https://shiftnrg.nl/docs/delegate/linux/initial-server-setup-with-ubuntu-16-04)

According to;
Step Four — Add Public Key Authentication (Recommended)

the defaut is root (/root/.ssh/id_rsa)
(/root/.ssh/id_rsa)

The localuser is satimis

Ubuntu 16.04 server was installed on ubuntu-16.04.3-server-amd64.iso
with only standard system utilities installed.

I'm prepare to install LAMP stack on it.  The document to follow will be;
How to Install a LAMP Stack on Ubuntu 16.04
[https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-16-04](https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-16-04)

Regards
satimis

---

### Post by QIII on 2017-08-12
Hello!

I would steer very clear of the instructions you used for the initial setup.  There are some strikingly bad recommendations there, not limited to creating a sudoer requiring no password and logging into the remote machine as root.  Those are absolute security no-nos.

---

### Post by satimis on 2017-08-12
> **QIII said:**
> Hello!

I would steer very clear of the instructions you used for the initial setup.  There are some strikingly bad recommendations there, not limited to creating a sudoer requiring no password and logging into the remote machine as root.  Those are absolute security no-nos.
Hi,

Thanks for your advice.

Can I install LAMP server direct on ubuntu-16.04.3-server-amd64.iso?  If YES which options I need to select during installation.

I'm prepared to make a new installation rather than adding LAMP stack on the running Ubuntu 16.04 server with standard system utilities installed only.

I'm testing it on a VM of Oracle VirtualBox.

Thanks

Regards
satimis

---

### Post by QIII on 2017-08-12
The LAMP components (Linux, Apache, MySQL and PHP) are all available when you install Ubuntu Server.  So you should be able to construct your LAMP server with the parts already in the box.  Just watch the options you are given very carefully and select the packages you need at the point where you are asked about what components to install.  If I recall correctly, Ubuntu Server should at some point in the installation process should give you a menu of things you want installed.  Otherwise, you can install them after installing the OS.  Some assembly required for setting up the functioning LAMP server after OS installation.

I use LEMP on my servers, so I have to install Nginx, but the processes are very similar in most regards.

You might want to start [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") and [here]("https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04").  The second resource, from Digital Ocean, is well thought-out and has some helpful detail.  I have found that Digital Ocean has some of the best server tutorials out there.

For the SSH setup, have a look [here]("https://help.ubuntu.com/community/SSH").

And ...  As I'm sure you know, we are always here to help!

---

### Post by satimis on 2017-08-12
> **QIII said:**
> The LAMP components (Linux, Apache, MySQL and PHP) are all available when you install Ubuntu Server.  So you should be able to construct your LAMP server with the parts already in the box.  Just watch the options you are given very carefully and select the packages you need at the point where you are asked about what components to install.  If I recall correctly, Ubuntu Server should at some point in the installation process should give you a menu of things you want installed.  Otherwise, you can install them after installing the OS.  Some assembly required for setting up the functioning LAMP server after OS installation.

I use LEMP on my servers, so I have to install Nginx, but the processes are very similar in most regards.

You might want to start [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") and [here]("https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04").  The second resource, from Digital Ocean, is well thought-out and has some helpful detail.  I have found that Digital Ocean has some of the best server tutorials out there.

Hi,

Thanks for your advice and links.

I prefer to have a new installation on Ubuntu 16.04 server ISO.   I have following document here;
Ubuntu 14.04 Server Installation Guide and Setup LAMP (Linux, Apache, MySQL, PHP)
[https://www.tecmint.com/ubuntu-14-04-server-installation-guide-and-lamp-setup/](https://www.tecmint.com/ubuntu-14-04-server-installation-guide-and-lamp-setup/)

I suppose it also works on Ubuntu 16.04 server ISO?  On software selection (please refers to upload photo), apart from selecting "LAMP server" any other software I need to install?

Thanks

Regards
satimis

---

### Post by QIII on 2017-08-12
Selecting LAMP server should get you what you need, but you might want to check after install just to be sure.

---

### Post by satimis on 2017-08-12
> **QIII said:**
> Selecting LAMP server should get you what you need, but you might want to check after install just to be sure.

Sure.  Thanks

After successful installation I would mark this thread "SOLVED"

Regards
satimis

---

### Post by satimis on 2017-08-12
Hi all,

LAMP server installed on ubuntu-16.04.3-server-amd64.iso

On a VM of Oracle VirtualBox.

Document to follow:
Ubuntu 14.04 Server Installation Guide and Setup LAMP (Linux, Apache, MySQL, PHP)
[https://www.tecmint.com/ubuntu-14-04-server-installation-guide-and-lamp-setup/](https://www.tecmint.com/ubuntu-14-04-server-installation-guide-and-lamp-setup/)

Guided - use entire disk and set up LVM

Software section:
[check] LAMP server
[check] standard system utilities

After installation completed ran;
$ sudo apt-update ; sudo apt upgrade
$ sudo apt-update ; sudo apt dist-upgrade

$ sudo apt install bridge-utils ssh

$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig

$ sudo nano /etc/network/interfaces```

iface lo inet loopback
dns-nameservers  218.xxx.xxx.xxx 219.xxx.xxx.xxx

# The primary network interface
auto enp0s3
iface enp0s3 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.xxx.xxx.xxx
        network         192.xxx.xxx.xxx
        netmask         255.255.255.0
        broadcast       192.xxx.xxx.xxx
        gateway         192.xxx.xxx.xxx
        bridge_ports    enp0s3
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

$ sudo reboot


$ apt-cache policy apache2 php7.0 php7.0-mysql mysql-client mysql-server phpmyadmin```

apache2:
  Installed: 2.4.18-2ubuntu3.4
  Candidate: 2.4.18-2ubuntu3.4
  Version table:
 *** 2.4.18-2ubuntu3.4 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.4.18-2ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
php7.0:
  Installed: (none)
  Candidate: 7.0.22-0ubuntu0.16.04.1
  Version table:
     7.0.22-0ubuntu0.16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
     7.0.4-7ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
php7.0-mysql:
  Installed: 7.0.22-0ubuntu0.16.04.1
  Candidate: 7.0.22-0ubuntu0.16.04.1
  Version table:
 *** 7.0.22-0ubuntu0.16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     7.0.4-7ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
mysql-client:
  Installed: (none)
  Candidate: 5.7.19-0ubuntu0.16.04.1
  Version table:
     5.7.19-0ubuntu0.16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
     5.7.11-0ubuntu6 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
mysql-server:
  Installed: 5.7.19-0ubuntu0.16.04.1
  Candidate: 5.7.19-0ubuntu0.16.04.1
  Version table:
 *** 5.7.19-0ubuntu0.16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
        100 /var/lib/dpkg/status
     5.7.11-0ubuntu6 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
phpmyadmin:
  Installed: (none)
  Candidate: 4:4.5.4.1-2ubuntu2
  Version table:
     4:4.5.4.1-2ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
     4:4.5.4.1-2ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages

```


$ sudo apt install php7.0 php7.0-mysql mysql-client phpmyadmin

phpmyadmin
[check] Apache2
Configure database for phpmyadmin with dbconfig-common?   
[Yes]


$ apt-cache policy php7.0 php7.0-mysql mysql-client phpmyadmin```

php7.0:
  Installed: 7.0.22-0ubuntu0.16.04.1
  Candidate: 7.0.22-0ubuntu0.16.04.1
  Version table:
 *** 7.0.22-0ubuntu0.16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
        100 /var/lib/dpkg/status
     7.0.4-7ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
php7.0-mysql:
  Installed: 7.0.22-0ubuntu0.16.04.1
  Candidate: 7.0.22-0ubuntu0.16.04.1
  Version table:
 *** 7.0.22-0ubuntu0.16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     7.0.4-7ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
mysql-client:
  Installed: 5.7.19-0ubuntu0.16.04.1
  Candidate: 5.7.19-0ubuntu0.16.04.1
  Version table:
 *** 5.7.19-0ubuntu0.16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
        100 /var/lib/dpkg/status
     5.7.11-0ubuntu6 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
phpmyadmin:
  Installed: 4:4.5.4.1-2ubuntu2
  Candidate: 4:4.5.4.1-2ubuntu2
  Version table:
 *** 4:4.5.4.1-2ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     4:4.5.4.1-2ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages

```

$ sudo reboot


To enable or disable init daemons on run-levels install and run &#8216;sysv-rc-conf&#8216; utility which replaces chkconfig package

$ sudo apt-get install sysv-rc-conf
$ sudo sysv-rc-conf
see;
screenshot_sysv-rc-conf.png


To confirm php status create a &#8216;info.php&#8216; file in &#8216;/var/www/html&#8217; server path with the following content;
<?php phpinfo(); ?>

On Host browser run;
[http://ip-address](http://ip-address)
starts Apache2 default page

[http://ip-address/info.php](http://ip-address/info.php)
starts PHP

[http://ip-address/phpmyadmin/](http://ip-address/phpmyadmin/)
starts phpMyAdmin


Anything missed here?  Please advise.  Thanks

Regards
satimis

---

### Post by darkod on 2017-08-12
The LAMP components seem to be working fine so I would say all is good. I would like to point out two things:

1. You used the guided LVM method during installation. That can sometimes created very small /boot partition, so watch out not to fill it 100% by installing too many kernels without removing the older ones.

2. Your original question about the ssh keys. You create the private key on the client computer (the one you will be connecting from), and then copy it to the server with ssh-copy-id. You don't need to create any key pair on the server itself unless you plan to connectfrom it to other computers. Just to make that clear...

---

### Post by satimis on 2017-08-12
> **darkod said:**
> The LAMP components seem to be working fine so I would say all is good. I would like to point out two things:

1. You used the guided LVM method during installation. That can sometimes created very small /boot partition, so watch out not to fill it 100% by installing too many kernels without removing the older ones.
I have encountered such a problem before.  Thanks

> 
2. Your original question about the ssh keys. You create the private key on the client computer (the one you will be connecting from), and then copy it to the server with ssh-copy-id. You don't need to create any key pair on the server itself unless you plan to connectfrom it to other computers. Just to make that clear...
Advice noted and thanks

Regards
satimis

---

