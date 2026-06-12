---
title: "How to not run vsftpd at boot time... ?!"
date: 2010-10-05
forum: Server Platforms
---

### Post by Xenus9898 on 2010-10-05
HI,

Im trying to prevent vsftpd to start at boot time and didnt find how until now...
Im using Ubuntu 10.04 LTS.
I have installing vfstpd via apt-get
I have removed the init script from init.d directory and did the following command :
"update-rc.d vsftp remove"
"update-rc.d vsftpd remove"

but vsftpd still run at boot time...

I would like to know how to prevent it to start at boot time and how to start it at boot time in case I change my mind.

thanks you all

---

### Post by lufte on 2010-10-07
I'm also looking for a answer to this. I've done this with other services such (as postgres and apache) by removing the links in rc.2 (the default runlevel), but theres no link for vsftpd in rc.2. Anyway, vsftpd seems to start somehow. I've also added a "K19vsftpd" link to kill the process but it doesn't work.

---

### Post by arrrghhh on 2010-10-07
> **lufte said:**
> I'm also looking for a answer to this. I've done this with other services such (as postgres and apache) by removing the links in rc.2 (the default runlevel), but theres no link for vsftpd in rc.2. Anyway, vsftpd seems to start somehow. I've also added a "K19vsftpd" link to kill the process but it doesn't work.

That's definitely not how to do it.

The OP was on the right path... you should be using update-rc.d.

Did the OP run it as sudo?  Also, have you tried 'purge' instead of 'remove'?

I'm not quite sure what else would need to be done, that should remove it from startup.

If you want to start it manually, ```
sudo service vsftpd start
``` would fire it up.

Let me know if it's still running after you try that other update-rc.d command.  BTW, did it put anything out when you did that?  It should've listed the stuff it removed...

---

### Post by lufte on 2010-10-07
I tried it with udpate-rc.d but nothing happens:

```
xavi@xavi-inspiron:~$ sudo update-rc.d -f vsftpd remove
 Removing any system startup links for /etc/init.d/vsftpd ...
xavi@xavi-inspiron:~$
```I restart the system and run:

```
xavi@xavi-inspiron:~$ sudo service vsftpd status
vsftpd start/running, process 1767
xavi@xavi-inspiron:~$ 

```So it never removed it. I've found that the init script (the one located in /etc/init.d) for vsftpd isn't actually a script, but a link to /lib/init/upstart-job. Does this have anything to do with the problem?

PD: what is "OP"?

---

### Post by Xenus9898 on 2010-10-08
The good answer is here. I 've found out. Vsftpd is started by another mecanism that is called upstart. You will find in /etc/init/ a file vsfptd.conf . You have to comment the lines :

start on (filesystem
 and net-device-up IFACE!=lo)
 [B]
[/B]

---

### Post by arrrghhh on 2010-10-08
> **lufte said:**
> PD: what is "OP"?

Original Poster or Original Post.  What does PD mean?  Did you mean PS?  :p

> **Xenus9898 said:**
> The good answer is here. I 've found out. Vsftpd is started by another mecanism that is called upstart. You will find in /etc/init/ a file vsfptd.conf . You have to comment the lines :

start on (filesystem
 and net-device-up IFACE!=lo)
 [B]
[/B]

So I'm glad you got it figured out, but that just seems wrong to me... Perhaps vsftp is different than 'typical' services?  Can a guru chime in here?

I just prefer to do things the 'recommended' way, and that doesn't seem like it should be recommended to anyone!  ;)

---

### Post by lufte on 2010-10-08
That worked for me. It seems like a dirty way to do it, but it doesn't work with the correct way. The script in /etc/init.d/vsftpd says "# Symlink target for initscripts that have been converted to Upstart.", so vsftpd is somehow different than typical services.

PD is posdata, I think is the same as PS. PD is used in spanish, I forgot I was (almost) speaking english :P

---

### Post by arrrghhh on 2010-10-08
Hrm.  Most stuff should have been converted to Upstart, and should still be able to be removed by that update-rc.d command..

If there's some different/new official way to do this in Lucid and beyond, I'd like to know!

---

### Post by Helixit on 2010-11-22
This is an old thread but maybe someone will pick this up.

I have similar problems.

the command /etc/init.d/vsftpd start generates the dialog "Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service vsftpd restart. Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the restart(8) utility, e.g. restart vsftpd
vsftpd start/running, process 991"

If I use the command service vsftpd start I get "vsftpd start/running, process 1022" and this is after runing the update-rd to remove vsftpd.

From everything I can tell (I'm a newbie) vsftpd is not running at all regardless of how I attempt to start it. 

Was there any more to this thread that might help me out?

Al

---

### Post by arrrghhh on 2010-11-22
> **Helixit said:**
> This is an old thread but maybe someone will pick this up.

I have similar problems.

the command /etc/init.d/vsftpd start generates the dialog "Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service vsftpd restart. Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the restart(8) utility, e.g. restart vsftpd
vsftpd start/running, process 991"

If I use the command service vsftpd start I get "vsftpd start/running, process 1022" and this is after runing the update-rd to remove vsftpd.

From everything I can tell (I'm a newbie) vsftpd is not running at all regardless of how I attempt to start it. 

Was there any more to this thread that might help me out?

Al

You tried this?

> **Xenus9898 said:**
> The good answer is here. I 've found out. Vsftpd is started by another mecanism that is called upstart. You will find in /etc/init/ a file vsfptd.conf . You have to comment the lines :

start on (filesystem
 and net-device-up IFACE!=lo)
 [B]
[/B]

---

### Post by slickvguy on 2012-01-03
If there is not a "listen=yes" or "listen_ipv6=yes" in your /etc/vsftpd.conf , then the service will not be started.

---

