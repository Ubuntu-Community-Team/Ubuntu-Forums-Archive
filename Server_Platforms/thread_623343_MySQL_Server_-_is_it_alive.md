---
title: "MySQL Server - is it alive?"
date: 2007-11-25
forum: Server Platforms
---

### Post by miltonr on 2007-11-25
I'm new at Linux and my goal is to connect to the MySQL already installed on my Ubuntu 7.10 and create a simple one table database.
I don't know the name of the local host name, but do know the user ID and password.

For those poor mere mortals lost in Linuxland, I solved my problem as follows:
I followed miss FoxyLad suggestion to find out if MySQL was running; it was running (if your is not running, from the System/Admin/Synaptic Package Manager select Not Installed from the list on left column, and select MySQL-server from the list on the right; click apply and let it do its thing. While at it, also select MySQL-Admin. This will give a GUI to admin tasks such as adding users, etc.)
Once installed, from the Applications/Programming select MySQL Administrator and enter LocalHost for server name, root for user ID and your password.

---

### Post by foxylad on 2007-11-26
If you have it, look at the processes in System/Administration/System Monitor to see if MySQL is running. If you are on the command line try "ps -aux | grep mysql".

If it is running, you should be able to login from the console with "mysql -u username -p" it will ask the password. It assumes the host name is localhost, i.e. the machine itself.

---

### Post by miltonr on 2007-11-26
Thanks for your help. I tried what you suggested, and the server is still not running, and I just spent over an hour trying to decipher, from many websites, how to get the server running, but all I get is the following error message when I try "mysql -u username -p" :
ERROR 1045 (28000): Access denied for user 'root'@'localhost

---

### Post by mustang357 on 2007-11-26
Are you sure the server is not running?  It seems like you have it running, you just do not have the right username/password.

To confirm that it is running, type:

```
sudo /etc/init.d/mysql status
```

It will tell you if the server is running or not.  It will explicitly state that it is stopped if it is not running, and provide version information, uptime, and query information if it is running.

If the server is indeed running, your password is incorrect.  Try removing the -p flag to see if no password exists.

I'm afraid I'm at a loss as to how to reset the MySQL password if you do not have the root password.

---

### Post by koenn on 2007-11-26
I agree with mustang 357 & it's unlike that a service that is not running could send you an error message telling you you're not alllowed to log in. 

besides omitting the -p, you can also try
```
mysql -u root  -p
```
note that the root user here is the mysql system administrator account, not the linux root user. 

It is possible to reset this root password - it's documented in the mysql admin manual  (RTFM !  :) ) [http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

---

### Post by miltonr on 2007-11-26
Thanks a lot to all of you who posted answers. It's good to know that there are people like you out ther in cyberspace.

---

