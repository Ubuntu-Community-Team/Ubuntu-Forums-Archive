---
title: "Server startup?  How do scripts get executed?"
date: 2010-02-14
forum: Server Platforms
---

### Post by wgregori on 2010-02-14
Can someone direct me to an explanation of how Ubuntu 9.10 ultimately executes startup scripts... I've read a bunch of old web post that talk about number of approaches... rc.local being one of them.  But it appears that the startup process has been revamped and I can't find much info about it.

Thanks for any resources that you might be able to direct me to.

Wayne

---

### Post by joberly on 2010-02-14
Well, the new process is called [Upstart]("http://upstart.ubuntu.com/"), however, there is still support for the "runlevel" method because many programs are still using this way of execution. Scripts get executed based upon what runlevel they are to be started in. Take a look in your /etc/rc*.d directories. Each number after rc represents what runlevel it belongs to. Normally, Runlevel 0 is used for shutdown, 1 is for single user mode (rescue), 3 is multi-user, networking, no X, 5 is the normal state with X, 6 is for shutdown. 2 and 4 were normally not used and the default was 5, however the default is now 2. (check with the runlevel command in a terminal). You can see that the same scripts get executed in runlevels 2,3,4,5.

rc.local is designed for user-generated scripts that you'd like to be executed at startup. rc.local gets run last after all other scripts have been executed.

---

### Post by Satoru-san on 2010-02-14
The actual programs are ini.d's in the /etc/init.d/ directory.

They can be added and removed from boot by doing:

```
update-rc.d blah defaults
```
for example

```
man update-rc.d
```

---

### Post by bab1 on 2010-02-14
Upstart is ultimatly the init system that is replacing the System V style [FONT="Courier New"]/sbin/init [/FONT].  It has been a part of Ubuntu since Edgy Eft (6.10).  A very good description can be found [**_[COLOR="Navy"]here[/COLOR]_**]("http://www.linux.com/archive/feed/57213").  This is the official website for Upstart: [**_[COLOR="Navy"]http://upstart.ubuntu.com/[/COLOR]_**]("http://upstart.ubuntu.com/").

---

