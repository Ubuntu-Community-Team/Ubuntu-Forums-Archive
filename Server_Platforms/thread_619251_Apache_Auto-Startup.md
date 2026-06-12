---
title: "Apache Auto-Startup?"
date: 2007-11-21
forum: Server Platforms
---

### Post by Starcraftmazter on 2007-11-21
Hey.

How would I get apache to start up automatically? I tried to put it into sessions, but   the command didn't work, and I assume it's because you need root privileges to execute apache2ctl.

Any tips?

Thanks!

---

### Post by Stemp on 2007-11-21
Hi, 

How did you install apache ? As far as I know when installing it via the repositories, it's start automaticaly on startup.

Anyway you should have a startup script  /etc/init.d/apache2 and you'll have to look at the update-rc.d command to call it automaticaly on startup/shutdown.

---

### Post by Starcraftmazter on 2007-11-21
Ahhh yes thanks.

Yeh, it was installed via the repos, but no auto-startup occured.

Edit: There was already an apache2 file in /etc/init.d/, but apache was still not running. I had a brief look through the script, consulted the log_daemon log, and saw no mention of apache.

Could this be some sort of a bug in the script?

---

### Post by conjur3r on 2007-11-22
What does the following give you?

# find /etc/rc* -name *apache*

If it doesn't bring back anything, issue the following to add apache to your boot up:

# sudo update-rc.d apache2 defaults

---

### Post by Starcraftmazter on 2007-11-24
Sorry for the late reply, I somehow didn't get a notification about this thread :S

```
root@moocow:~# find /etc/rc* -name *apache*
/etc/rc0.d/K09apache2
/etc/rc1.d/K09apache2
/etc/rc3.d/S91apache2
/etc/rc4.d/S91apache2
/etc/rc5.d/S91apache2
/etc/rc6.d/K09apache2
```

---

### Post by conjur3r on 2007-11-24
From those results, apache is supposed to start in run levels 3, 4 and 5.  Apache should already be running by the time you get to the login screen.

If it's not running, check your apache error logs /var/log/apache2/error.log.

---

### Post by Starcraftmazter on 2007-11-25
There are no erros in the error log,

[quote="/var/log/apache2/error.log"][Sun Nov 25 13:42:52 2007] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 configured -- resuming normal operations
[Sun Nov 25 13:42:55 2007] [error] [client 127.0.0.1] File does not exist: /home/max/webdesign/favicon.ico
[Sun Nov 25 13:48:40 2007] [error] [client 127.0.0.1] File does not exist: /home/max/webdesign/favicon.ico[/quote]

And apache is definately not running. If I point to any localhost location, I get a server now found message, and so I have to execute the command **apache2ctl start**, during any session, before I use apache.

---

### Post by gali98 on 2007-11-25
I guess you could always try installing it again. I installed it in Synaptic through the "Mark by task" and did the lamp server. Everything worked perfect. This is weird.
Kory

---

### Post by Stemp on 2007-11-25
> **Starcraftmazter said:**
> Sorry for the late reply, I somehow didn't get a notification about this thread :S

```
root@moocow:~# find /etc/rc* -name *apache*
/etc/rc0.d/K09apache2
/etc/rc1.d/K09apache2
/etc/rc3.d/S91apache2
/etc/rc4.d/S91apache2
/etc/rc5.d/S91apache2
/etc/rc6.d/K09apache2
```

Humm, no rc2.d ?

```
sudo update-rc.d   apache2 defaults 91
```

---

### Post by MJN on 2007-11-25
Indeed - that'll be it.

Runlevel 2 is the default multi-user level for Ubuntu hence it's entirely likely that's what level you're running in (strange that your don't have the startup script already in it).

Incidentally, you can check the current run-level by running **runlevel** - it'll show the previous (N if none) and current runlevels, and you can see what your default on boot is by looking in **/etc/inittab**). Both of these should, by default, read level 2.

Mathew

---

### Post by Starcraftmazter on 2007-11-27
> **Stemp said:**
> Humm, no rc2.d ?

```
sudo update-rc.d   apache2 defaults 91
```

Unfortunately that didn't make any changes,

```
max@moocow:~$ sudo update-rc.d   apache2 defaults 91
[sudo] password for max:
 System startup links for /etc/init.d/apache2 already exist.
```

> **MJN said:**
> Incidentally, you can check the current run-level by running **runlevel** - it'll show the previous (N if none) and current runlevels, and you can see what your default on boot is by looking in **/etc/inittab**). Both of these should, by default, read level 2.

Yep,

```
max@moocow:~$ runlevel
N 2
```


So now, how do I get apache to start on runlevel 2?


Thanks.

---

### Post by MJN on 2007-11-27
You could try forcing level 2 only with:
 
```
update-rc.d apache2 start 91 2
```
 
What is the current contents of /etc/rc2.d/ ?
 
Mathew

---

### Post by Stemp on 2007-11-27
```
sudo  ln -s /etc/init.d/apache2 /etc/rc2.d/S91apache2
```

---

### Post by Starcraftmazter on 2007-11-27
> **MJN said:**
> You could try forcing level 2 only with:
 
```
update-rc.d apache2 start 91 2
```
 
What is the current contents of /etc/rc2.d/ ?
 
Mathew

That returned an error.

```
root@moocow:~# update-rc.d apache2 start 91 2
update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)
```

The contents of rc2,

```
root@moocow:/etc/rc2.d# ls
README                       S19cupsys         S25bluetooth
S05vbesave                   S19mysql          S30gdm
S10acpid                     S20apmd           S89anacron
S10powernowd.early           S20apport         S89atd
S10sysklogd                  S20hotkey-setup   S89cron
S10xserver-xorg-input-wacom  S20makedev        S98usplash
S11klogd                     S20nvidia-kernel  S99acpi-support
S12dbus                      S20powernowd      S99laptop-mode
S12hal                       S20rsync          S99rc.local
S16ssh                       S22consolekit     S99rmnologin
S17mysql-ndb-mgm             S24avahi-daemon   S99stop-readahead
S18mysql-ndb                 S24dhcdbd
```

> **Stemp said:**
> ```
sudo  ln -s /etc/init.d/apache2 /etc/rc2.d/S91apache2
```

I have done that, and will test it momentarily.

---

### Post by MJN on 2007-11-27
Yes, I did forget the . (nice error!)
 
I'm curious as to why you don't already have the symlink in /etc/rc2.d/ - have you done anything that might even remotely be responsible for changing this default? I take it this is a standard Apache install from the repositories?
 
Mathew

---

### Post by Starcraftmazter on 2007-11-27
Firstly, creating the symlink did the job.

MJN, nope, I did absolutely nothing. Just installed Apache, PHP, MySQL and all the neccessary connector libraries from Synaptic, and it was like this.

---

### Post by MJN on 2007-11-27
How bizarre. Oh well, glad you're up-and-running.

Mathew

---

### Post by Starcraftmazter on 2007-11-27
Thanks Mate.

---

### Post by Stemp on 2007-11-27
> **MJN said:**
> How bizarre. Oh well, glad you're up-and-running.

Mathew

Yep bizarre, but well it's running :popcorn:

---

### Post by fujikofujio on 2007-12-29
Had the same exact problem, apache, cron, anacron and webmin would not start on startup. Their init.d scripts were already on the rc2.d directory.

They were S91apache, S99webmin, S89anacron and S99cron.

For some reason anything that was on S20 worked, liked vsftpd.

So I just renamed them all to S20apache, S20webmin and they all worked. This has never happened to me before on previous versions of ubuntu.

With regards to those S##'s can anyone explain what they mean? I presume they mean at what part of the boot process those scripts get executed, but I'd like to learn more.

---

### Post by MJN on 2007-12-29
The numbers do indeed just dictate the order - the directory is parsed in the order hence S1 runs, then S2, S3 and so on. Such ordering is required when, for example, a particular application needs the network stack to to be running before it can start - the network startup script would then be given a lower number than this app.

I cannot think of a reason why your S99 scripts would not work yet they did when changed to S20 - we would have investigate further with your original configuration.

Mathew

---

