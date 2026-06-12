---
title: "passwords for some keys for others - SSH"
date: 2011-04-07
forum: Server Platforms
---

### Post by Ceiber Boy on 2011-04-07
I have a ubuntu server that is open to the internet that people log onto remotely using an sftp client, now each person has their own account ans is able to access their folder, they are restricted from root powers and shell.

the main account however is unrestricted, which i have set a reasonably secure password for, but i would like to use keys instead of a password to have access to help protect against bruit force attacks.

in the /etc/ssh/sshd_config file ive set the "passwordauthentication =no" and im able to login with my key but my friends can't login to their accounts using their sftp clients.

so here is the question:
is their a way of restricting my account to key logins only and allowing my users password logins?

many thanks

---

### Post by BkkBonanza on 2011-04-07
I believe that setting is global for all access. So to do this you would have to run 2 sshd daemons, the second one with a different sshd_config. The config path can be set on the command line with -f paramter. It would have to use a different port as well (not 22). (Most of the memory usage would be shared so it's not so bad that way).

The upside is that on the client end you can create a .ssh/config file on your system that automates the login with non-standard port so you don't ahve to manually do it. You just put in a couple lines like,

Host myhost.com
Port 2222

(assuming using 2222 for non-standard port).

Another option is to just leave passwords enabled and put on a really long and secure password that you don't intend to use anyway except as a backup.

---

### Post by mazato on 2011-04-08
Ceiber Boy, you have changed a global setting like BkkBonanza mentioned, you should do that in the user's config file, you are editing the daemon config file, it should be in 
/.ssh/config
I would also install and run these 2 programs:

[http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)
[http://www.techfinesse.com/sshutout/sshutout.html](http://www.techfinesse.com/sshutout/sshutout.html)

P.S. Be careful you have local acces to the box, otherwise you might lock out yourself.

Good luck!

---

### Post by Ceiber Boy on 2011-04-08
> **mazato said:**
> Ceiber Boy, you have changed a global setting like BkkBonanza mentioned, you should do that in the user's config file, you are editing the daemon config file, it should be in 
/.ssh/config
I would also install and run these 2 programs:

[http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)
[http://www.techfinesse.com/sshutout/sshutout.html](http://www.techfinesse.com/sshutout/sshutout.html)

P.S. Be careful you have local acces to the box, otherwise you might lock out yourself.

Good luck!

Many Thanks for the advice, my .ssh file dose not contain a file called config, what is in the file is listed below:

/home/***/.ssh# ls -la
total 16
drwx------ 2 *** *** 4096 2011-04-06 00:56 .
drwx------ 4 *** *** 4096 2011-04-06 08:54 ..
-rw------- 1 *** ***  736 2011-04-06 00:36 authorized_keys
-rw-r--r-- 1 *** ***  442 2011-04-06 00:56 known_hosts

am i missing something obvious? :(

---

### Post by BkkBonanza on 2011-04-08
You can create a config file there to control how the client connects but it has no bearing on the sshd server settings. For that you edit the /etc/ssh/sshd_config file only. However, if you create a config on the client it can make unusual connection settings easier. It won't help you for what you want as any user can always edit their own .ssh/config and they can override it on the cmd line.

---

