---
title: "Stop lauching Samba server at startup"
date: 2010-05-07
forum: Server Platforms
---

### Post by just_another_user on 2010-05-07
Hi

I want to stop my Samba server process to start at system startup. There is no such script at /etc/rc[2-5].d folders. And in /etc/init.d/ I have a symbolic link 
```
lrwxrwxrwx 1 root root 21 2010-05-04 13:53 smbd -> /lib/init/upstart-job*

```
When I'm using commands /etc/init.d/smbd start|stop|restart, I've got a message 
```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop smbd
smbd stop/waiting

```

What is an 'Upstart job' and where I can learn more about it?
I'm using Ubuntu Desktop 10.04

Thanks

---

### Post by oblib on 2010-05-07
Search for upstart and ubuntu on Google and you'll find it. 

Upstart init scripts live in /etc/init/ and all end in .conf. You'll find /etc/init/smbd.conf starts samba. I'm not sure what the correct way to remove it would be other then deleting (or preferably moving) it from the /etc/init directory.

---

### Post by just_another_user on 2010-05-07
Yes, you are right. But I sought, that startup scripts are in /etc/rc[2-5].d (or, more correctly symbolic links to scripts in /etc/init.d). So if I want to pretend launching some server, I just have to change S with K at the beginning of symbolic link name, as I did with dhcp3-server

```

lrwxrwxrwx 1 root root  22 2010-05-06 00:06 K40dhcp3-server -> ../init.d/dhcp3-server*
lrwxrwxrwx 1 root root  19 2010-04-28 23:47 K74bluetooth -> ../init.d/bluetooth*
lrwxrwxrwx 1 root root  15 2010-05-03 13:21 S19slapd -> ../init.d/slapd*


```

Are there two methods of startup programs at system boot in Ubuntu?

---

### Post by Iowan on 2010-05-07
> **just_another_user said:**
> ...I just have to change S with K at the beginning of symbolic link name, as I did with dhcp3-server A lowercase "s" *might* have the same effect...

---

### Post by just_another_user on 2010-05-07
A problem is that I don't have symbolic link in /etc/rc[2-5].d/ for smbd. So I move smbd.conf from /etc/init/ and it does not start at boot, neither I can launch samba manually using 
```
sudo /etc/init.d/smbd start
```
or
```
sudo service smbd start
```

I just want smbd does not starts at boot, but still be able to launch it manually

---

### Post by Vegan on 2010-05-07
Daemons are not intended to be run as convenient. They are mean to run all the time.

Using SAMBA on your desktop is not the best choice, its best on a beheaded server.

---

### Post by TAcadia on 2011-08-01
Hey, I just bumped into the same problem as you had. This is how I got it to work only when I wanted smbd to run:

1) remove smbd.conf from /etc/init and place it somewhere that you'll be able to reference int.

2) when you want to run the smbd just issue: sudo /usr/sbin/smbd -s ~/smbd.conf

That's assuming that you have placed smbd.conf into your home directory. 

Now that'll prevent samba from starting up on boot and allowing you to start it at will. Hope it helps!

---

### Post by SaturnusDJ on 2012-06-06
This worked for me:

Edit /etc/init/smbd.conf

**Remove** the "**!**" in ```
stop on runleven [**!**2345]
```

---

