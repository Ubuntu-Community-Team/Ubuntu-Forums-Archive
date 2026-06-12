---
title: "[SOLVED] Bind9 won't start"
date: 2008-05-19
forum: Server Platforms
---

### Post by NateMan on 2008-05-19
I'm setting up a server using the ubuntu 8.04 perfect server guide, and I got to the section where you start bind9 after stopping it. I'm getting errors in my syslog. Here's the section with the errors. I believe it is something to do with permissions, but not sure why. Any help would be greatly appreciated.

May 19 20:36:36 atlas named[6398]: starting BIND 9.4.2 -u bind -t /var/lib/named
May 19 20:36:36 atlas named[6398]: found 1 CPU, using 1 worker thread
May 19 20:36:36 atlas named[6398]: loading configuration from '/etc/bind/named.conf'
May 19 20:36:36 atlas named[6398]: none:0: open: /etc/bind/named.conf: permission denied
May 19 20:36:36 atlas named[6398]: loading configuration: permission denied
May 19 20:36:36 atlas named[6398]: exiting (due to fatal error)
May 19 20:36:36 atlas kernel: [38722.446742] audit(1211247396.427:2): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/var/lib/named/etc/bind/named.conf" pid=6399 profile="/usr/sbin/named" namespace="default"

---

### Post by bluefrog on 2008-05-21
silly question but have you checked /etc/bind/named.conf ownership and permissions?

---

### Post by NateMan on 2008-05-21
I have, it seems that everyone should be able to read the file, does it need to have write/execute privileges as well? Here's the ls -la for that:

-rw-r--r-- 1 bind bind 907 2008-04-09 14:42 /etc/bind/named.conf

I'm afraid this is the first time bind9 has actually given me a problem.

---

### Post by bluefrog on 2008-05-21
mine is 
-rw-r--r-- 1 root bind /etc/bind/named.conf

user not being root is not your problem though. Sorry I am at a loss here.

---

### Post by NateMan on 2008-05-21
Perhaps I should clear it off the machine and reinstall it from there?

---

### Post by Dr Small on 2008-05-21
It is worth a shot. But, try changing ownership first and check the rest of the files in there also. If you need to change ownership, use:
```
sudo chown root:bind /etc/bind/named.conf
```

---

### Post by volkswagner on 2008-05-21
I am in the middle of following the perfect setup myself.  It has the user modify some things.

> Edit the file /etc/default/bind9 so that the daemon will run as the unprivileged user bind, chrooted to /var/lib/named. Modify the line: OPTIONS="-u bind" so that it reads OPTIONS="-u bind -t /var/lib/named":



Create the necessary directories under /var/lib:

```
mkdir -p /var/lib/named/etc
mkdir /var/lib/named/dev
mkdir -p /var/lib/named/var/cache/bind
mkdir -p /var/lib/named/var/run/bind/run
```

Then move the config directory from /etc to /var/lib/named/etc:

```
mv /etc/bind /var/lib/named/etc
```

Create a symlink to the new config directory from the old location (to avoid problems when bind gets updated in the future):

```
ln -s /var/lib/named/etc/bind /etc/bind

```
Make null and random devices, and fix permissions of the directories:
```

mknod /var/lib/named/dev/null c 1 3
mknod /var/lib/named/dev/random c 1 8
chmod 666 /var/lib/named/dev/null /var/lib/named/dev/random
chown -R bind:bind /var/lib/named/var/*
chown -R bind:bind /var/lib/named/etc/bind
```


Here is the error I get.

 ```
/etc/init.d/bind9 restart
 * Stopping domain name service... bind                                         rndc: connect failed: 127.0.0.1#953: connection refused

```

/var/log/syslog
```
found 1 CPU, using 1 worker thread
May 21 18:38:25 Gail named[5359]: loading configuration from '/etc/bind/named.conf'
May 21 18:38:25 Gail named[5359]: none:0: open: /etc/bind/named.conf: permission denied
May 21 18:38:25 Gail named[5359]: loading configuration: permission denied
May 21 18:38:25 Gail named[5359]: exiting (due to fatal error)
May 21 18:38:25 Gail kernel: [ 2999.652630] audit(1211409505.327:2): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/var/lib/named/etc/bind/named.conf" pid=5512 profile="/usr/sbin/named" namespace="default"
May 21 18:41:09 Gail named[5415]: starting BIND 9.4.2 -u bind -t /var/lib/named
```


Here are some of my permissions

```
ls -alt /etc/bind/named.conf
-rw-r--r-- 1 bind bind 907 2008-04-09 15:42 /etc/bind/named.conf
ls -alt /var/lib/named/etc/bind/named.conf
-rw-r--r-- 1 bind bind 907 2008-04-09 15:42 /var/lib/named/etc/bind/named.conf
```

---

### Post by volkswagner on 2008-05-22
It is working now.  I am not sure if it was fixed simply by restarting the pc.  I did make one change to the system.  I am not sure how this would affect it.  I had an error during earlier config.  I have two sites I am working on.  One is a test site, the other is currently hosted outside my lan.

I used in in my /etc/host the test site.  When I ran 

```
echo server1.example.com > /etc/hostname
```

I incorrectly inserted the wrong host name (my other site, hosted outside my lan).

So now I continue the install/config.

---

### Post by NateMan on 2008-05-22
Sounds like a restart would be worth a shot. I'm rebooting it now. Unfortunatly, I'm not near it so hopefully it will go well... (crosses fingers). My permissions are almost identical to yours. I'm not going to change it to root, as I think that would probably break it even more. It is fully setup to be run as bind.

---

### Post by NateMan on 2008-05-22
Restart fixed the problem just fine! Thanks for the advice.

---

### Post by Ignite_nz on 2008-05-27
I just wanted to say thanks heaps for this thread. All I had to do was reboot my server and bind started properly! :)

---

### Post by NateMan on 2008-05-27
almost seems stupidly easy huh? imagine how I felt, having it be mine.

---

### Post by davidshere on 2008-07-13
I have followed the directions on that page three times on a virtual machine.  I have changed permissions in /etc and /var and all subdirectories to 777.  I have rebooted.  I still have the problem:
```
root@thunderbolt:/home/david# tail -f /var/log/syslog
Jul 13 14:10:19 thunderbolt /usr/sbin/cron[4516]: (CRON) INFO (pidfile fd = 3)
Jul 13 14:10:19 thunderbolt /usr/sbin/cron[4517]: (CRON) STARTUP (fork ok)
Jul 13 14:10:19 thunderbolt /usr/sbin/cron[4517]: (CRON) INFO (Running @reboot jobs)
Jul 13 14:15:41 thunderbolt named[4605]: starting BIND 9.4.2 -u bind -t /var/lib/named
Jul 13 14:15:41 thunderbolt named[4605]: found 1 CPU, using 1 worker thread
Jul 13 14:15:41 thunderbolt named[4605]: loading configuration from '/etc/bind/named.conf'
Jul 13 14:15:41 thunderbolt named[4605]: none:0: open: /etc/bind/named.conf: permission denied
Jul 13 14:15:41 thunderbolt named[4605]: loading configuration: permission denied
Jul 13 14:15:41 thunderbolt named[4605]: exiting (due to fatal error)
Jul 13 14:15:41 thunderbolt kernel: [ 1744.019281] audit(1215972941.472:3): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/var/lib/named/etc/bind/named.conf" pid=4606 profile="/usr/sbin/named" namespace="default"

```
The funny part is that when I simply install bind and modify named.conf.local and named.conf.options to set up my zones, it works perfectly.

EDIT: Umm... think I found what was wrong.  I wasn't disabling apparmor.

---

### Post by Pacendrix on 2008-08-21
Here is The easiest way to SOLVE THE PROBLEM.

1.BIND9 failed to start with the following reason
 ---> "/etc/bind/named.conf: permission denied"

Here is the syslog


Aug 21 21:12:10 pacendrix named[19340]: starting BIND 9.4.2-P1 -u bind
Aug 21 21:12:10 pacendrix named[19340]: found 1 CPU, using 1 worker thread
Aug 21 21:12:10 pacendrix named[19340]: loading configuration from '/etc/bind/named.conf'
Aug 21 21:12:10 pacendrix named[19340]: none:0: open: /etc/bind/named.conf: permission denied
Aug 21 21:12:10 pacendrix named[19340]: loading configuration: permission denied


2.The problem is that bind is trying to start as USER (maybe for security reasons which we will pass :P )

 " starting BIND 9.4.2-P1 -u bind "

 Unfortunately,the -u option only works when NAMED is run on some definite Kernel versions ... probably not your :)

3.THE SOLUTION :P

We just may to change this -u option  with  
-c that enables to use named.conf as the configuration file instead of the default.

Here is the CODE:

Open the bind9 default file with you favorite editor.
```

nano /etc/default/bind9

```

Result :
```

OPTIONS="-u bind"
# Set RESOLVCONF=no to not run resolvconf
RESOLVCONF=yes

```

and replace "-u bind" with "-c /etc/bind/named.conf"
to looks like:
```

OPTIONS="-c /etc/bind/named.conf"
# Set RESOLVCONF=no to not run resolvconf
RESOLVCONF=yes

```

It's Done.

Save the file and restart bind.

I hope I have helped you.
Best regards Pacendrix

---

### Post by Pacendrix on 2008-08-21
Here is The easiest way to SOLVE THE PROBLEM.

1.BIND9 failed to start with the following reason
 ---> "/etc/bind/named.conf: permission denied"

Here is the syslog


Aug 21 21:12:10 pacendrix named[19340]: starting BIND 9.4.2-P1 -u bind
Aug 21 21:12:10 pacendrix named[19340]: found 1 CPU, using 1 worker thread
Aug 21 21:12:10 pacendrix named[19340]: loading configuration from '/etc/bind/named.conf'
Aug 21 21:12:10 pacendrix named[19340]: none:0: open: /etc/bind/named.conf: permission denied
Aug 21 21:12:10 pacendrix named[19340]: loading configuration: permission denied


2.The problem is that bind is trying to start as USER (maybe for security reasons which we will pass :P )

 " starting BIND 9.4.2-P1 -u bind "

 Unfortunately,the -u option only works when NAMED is run on some definite Kernel versions ... probably not your :)

3.THE SOLUTION :P

We just may to change this -u option  with  
-c that enables to use named.conf as the configuration file instead of the default.

Here is the CODE:

Open the bind9 default file with the favorite editor.
```

nano /etc/default/bind9

```

Result :
```

OPTIONS="-u bind"
# Set RESOLVCONF=no to not run resolvconf
RESOLVCONF=yes

```

and replace "-u bind" with "-c /etc/bind/named.conf"
to looks like:
```

OPTIONS="-c /etc/bind/named.conf"
# Set RESOLVCONF=no to not run resolvconf
RESOLVCONF=yes

```

It's Done.

Save the file and restart bind.

I hope I have helped you.
Best regards Pacendrix[/QUOTE]

---

### Post by Ken Iovino on 2008-08-24
Make sure you at least attemp to change the permissions before going through all this.

```

chmod -rw-r--r-- /etc/bind/named.conf

```

I think that was my problem, because after going through this thread and the few others out there with this issue, I was still getting the same error. Then I ran the above command and it restarted without errors.

Hope this helps others who experiance this.

---

### Post by hhhrespect on 2008-09-21
I was seeing the same error that you guys are/were seeing:

[FONT="Courier New"]Sep 20 22:11:00 gaia kernel: [341408.785412] audit(1221973860.689:5): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/named/etc/named.conf" pid=5263 profile="/usr/sbin/named" namespace="default"[/FONT]

It turns out to be caused by AppArmor.

AppArmor seems to be in "enforcing" mode (rather than "complain" mode or off) by default in Ubuntu Server 8.04.

To get bind to work in an arbitrary chroot jail location you have to modify /etc/apparmor.d/usr.sbin.named to allow bind access to all the relevant files in the chroot jail.

I personally like to chroot named to /var/named (old school, I know). I use the following layout:

[FONT="Courier New"]/var/named
[INDENT]db.*    (zone files)
etc
dev
slave    (dir for slave zones)
var/run[/INDENT][/FONT]

To get bind to work with that I had to change my /etc/apparmor.d/usr.sbin.named file to say:

[FONT="Courier New"][...]
/var/named/db.* r,
/var/named/etc/** r,
/var/named/dev/log w,
/var/named/dev/null rw,
/var/named/dev/random r,
/var/named/slave/** rw,
/var/named/var/run/named.pid w,
# support for resolvconf
/var/named/var/run/named.options r,
[...][/FONT]

Normally, bind would create the named.pid file in [/var/named]/var/run/bind/run but I'm telling it to put it into [/var/named]/var/run in my named.conf:

[FONT="Courier New"][...]
pid-file "/var/run/named.pid";
[...][/FONT]

Remember: bind thinks that /var/named is the root whereas AppArmor does not. So what's /var/run/named.pid to bind is /var/named/var/run/named.pid to AppArmor.

I also like to put my named config into /var/named/etc, not /var/named/etc/bind.

...anyway, you get the idea.

So if you insist on getting bind running in a chroot jail you can simply configure AppArmor to work with that. Another alternative would be to disable AppArmor altogether.

However, since you already have AppArmor doing all the restricting that a chroot jail would do you might want to consider using bind as is. Check out this link:

[[COLOR="Blue"]How is AppArmor different from chroot?[/COLOR]]("http://developer.novell.com/wiki/index.php/Apparmor_FAQ#How_is_AppArmor_different_from_chroot.3F_Will_it_work_with_chroot.3F")

Hope this helps.

- Simon

---

