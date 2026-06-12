---
title: "Having troubles with my new linux server box, mainly along the lines of SSH?"
date: 2014-01-16
forum: Server Platforms
---

### Post by grady2 on 2014-01-16
So, I just got a linux server box running Ubuntu 12.04, and I'm using it (along with this tutorial: [https://gist.github.com/vemacs/5663144#prerequisites](https://gist.github.com/vemacs/5663144#prerequisites) ) to host a minecraft server. It doesn't have a graphics card, so I can only run console based linux.(I also used this tutorial to set up a static IP address: [http://draalin.com/setting-up-a-static-ip-address-in-ubuntu/](http://draalin.com/setting-up-a-static-ip-address-in-ubuntu/) As far as I can tell, it worked). My problem is that randomly, (I can't find a discernible pattern other than that it usually happens when I run the mc server) my server will stop the ssh, pause it, and afterwards I can't connect. I don't know what's wrong, so any advice is appreciated!

---

### Post by spencer the great on 2014-01-16
How do you get the server back working? Did you have a look at resources to check if the processes have enough memory to run? How often does it happen, when you're not running the mc server, and when you are? Can you post your "dmesg | tail" log when the server dies?
EDIT: Ah, stupid me, dmesg doesn't help if the server dies

---

### Post by bertan2 on 2014-01-16
Also, is there anything in /var/log/ files?

---

### Post by Jason_Gibson on 2014-01-17
why do you need to have an ssh tunnel in progress to run the server?

---

### Post by Bucky Ball on 2014-01-17
*Thread moved to **Server Platforms.** *

---

### Post by CharlesA on 2014-01-17
> **Jason_Gibson said:**
> why do you need to have an ssh tunnel in progress to run the server?

They manage it via SSH, so if SSH isn't working, they can't connect to it to do updates and whatnot.

@OP: Could the server be running out of memory? I know minecraft can be a bit of a memory hog.

Check the log files in /var/log if you are able to get console access to see if anything is amiss.

---

### Post by grady2 on 2014-01-18
Ok, I see a lot of posts about running out of memory, but usually at any time the server doesn't go over 20% usage, or at least it doesn't according to the program "mark2" that I'm using to control the server. I can do all of this at the actuall box, but it usually only disconnects me about 30 minutes into running the server, and it won't take any connections in (I.E. I can't get in through minecraft, the ssh console, the sftp client, and if I shake the mouse/type on the keyboard, nothing happens.). I have to turn it on and off again, usually.

---

### Post by grady2 on 2014-01-18
I don't see anything in the /var/log file. I used the following commands to get there:

ssh [email]admin@xxx.xxx.xxx.xxx[/email]
<password>
cd /var
nano log

---

### Post by bertan2 on 2014-01-18
Sorry, I meant the files inside the /var/log directory. For example:


```
cd /var/log
ls
tail secure
tail messages
tail auth.log

```

---

### Post by grady2 on 2014-01-23
Ok, here is the contents:

```
admin@OpteronX64-Server:/var/log$ ls
alternatives.log  dist-upgrade  dpkg.log   mail.err   syslog
apache2           dmesg         faillog    mail.log   tomcat6
apt               dmesg.0       fsck       mysql      udev
auth.log          dmesg.1.gz    installer  mysql.err  ufw.log
boot              dmesg.2.gz    kern.log   mysql.log  unattended-upgrades
boot.log          dmesg.3.gz    landscape  news       upstart
btmp              dmesg.4.gz    lastlog    samba      wtmp
```

---

### Post by CharlesA on 2014-01-23
Check auth.log and syslog to see what it says.

---

