---
title: "unable to connect to system bus"
date: 2010-10-08
forum: Server Platforms
---

### Post by tomtetlaw on 2010-10-08
I am running Ubuntu Server 10.04.01. When I try to start the MySQL service with ```
sudo start mysql
```, I get this error:

```
start: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
```What could I do to fix it?

---

### Post by jonathonbyrd on 2010-10-08
I just ran into that same error as well.

I read somewhere else that people where getting this same error, but when running a different command. They used the following to solve this problem:

```
dhclient
apt-get update
apt-get install upstart
```

---

### Post by jonathonbyrd on 2010-10-08
I'm just compiling a list of resources to help locate this issue:

The command I'm running:
[http://abbysays.wordpress.com/2008/05/20/how-to-startstop-mysql-server-on-ubuntu-804/](http://abbysays.wordpress.com/2008/05/20/how-to-startstop-mysql-server-on-ubuntu-804/)


Forums that also have this question:
[http://www.daniweb.com/forums/thread316360.html](http://www.daniweb.com/forums/thread316360.html)

[http://www.linuxforums.org/forum/ubuntu-linux/163177-unable-connect-system-bus-failed-connect-socket-var-run-system_bus_sock.html](http://www.linuxforums.org/forum/ubuntu-linux/163177-unable-connect-system-bus-failed-connect-socket-var-run-system_bus_sock.html)

[http://ubuntuforums.org/showthread.php?t=1458906](http://ubuntuforums.org/showthread.php?t=1458906)

[http://www.linuxforums.org/forum/servers/163187-mysql-socket-does-not-exist.html](http://www.linuxforums.org/forum/servers/163187-mysql-socket-does-not-exist.html)



And I found a solution: Sweet!

[http://gutsywww.ubuntuforums.org/showthread.php?p=9912680](http://gutsywww.ubuntuforums.org/showthread.php?p=9912680)

You will need root rights. 

Try: ```
sudo service mysql start
```

---

### Post by linis_australis on 2011-07-28
I'm having this same error, but I don't use (or have installed) mysql. is this more generally related to dbus?  Any hints as to where to start would be great.  I'm getting no hints from the syslog or the boot.log.

Thanks

---

### Post by auftable on 2011-08-08
I have the same error when trying to shutdown with natty. In oneric it seems to be a bug: [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441) . But is it the same in natty?

---

### Post by daemonrebel on 2011-10-14
> **tomtetlaw said:**
> I am running Ubuntu Server 10.04.01. When I try to start the MySQL service with ```
sudo start mysql
```, I get this error:

```
start: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
```What could I do to fix it?

Hi. I have the same error, and now after upgrading from 11.4 to 11.10, the upgrade went fine and then i shut down. Now it won't boot into the gnome. I get the same error and it says waiting to connect to network, cannot connect to system bus. 

People say I should just remove dbus directory. I tried and it didn't work, it says directory is read only and is not empty. I tried deleting the file "pid  system_bus_socket". It wouldn't let me delete it. 

I'm new to Ubuntu, so I have no idea how to migrate the files of /var/run to /run, via the command line. 

However, I did try "sudo rm -r /run/*" which I saw as a solution on another site. That command completed correctly, but still problem is not fixed. 

It's finals this week and i downloaded files last night I don't want to loose. I encrypted my main hard drive, so reinstalling Ubuntu is not a preferred option. Please help me so I can boot into the gnome.

This bug was also reported here: Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused (oneiric) [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)

I've made additional, but not duplicate posts there.

---

### Post by Doduren on 2011-10-18
Hey buddy,

Same problem here, removing pid & system_bus_socket worked for me. To migrate/move those files use "sudo mv /var/run/dbus/pid /". This will copy it to your root folder, or you can replace / with whatever you want /user/Desktop, etc.

---

### Post by daemonrebel on 2011-10-19
> **Doduren said:**
> Hey buddy,

Same problem here, removing pid & system_bus_socket worked for me. To migrate/move those files use "sudo mv /var/run/dbus/pid /". This will copy it to your root folder, or you can replace / with whatever you want /user/Desktop, etc.

It wouldn't let me deleted anything related to removing this bug, only copy and make links. I eventually scrapped the install and reverted to 11.4 installation. I consider 11.4 a stable installation and I never have any problems with it, but it's incredibly difficult to run pc games in it. 

Eventually, I decided that it's more performance efficient to run ubuntu inside of windows 7, instead of windows xp instead of ubuntu. Ubuntu just can't keep up with directx 11, it just runs games at an alarming speed. >:-)

---

### Post by alex.milla on 2011-10-26
I have deleted the entire contents of /var/run/sbus and I returned to work. ;)

---

