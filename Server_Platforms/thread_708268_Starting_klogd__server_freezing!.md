---
title: "Starting klogd : server freezing!"
date: 2008-02-26
forum: Server Platforms
---

### Post by akall on 2008-02-26
Hi everybody!
I installed Gutsy (server edition) on a P4 M, 3ghz, 512mb ram, togheter with gnome desktop, webmin (1.390), nfs, lvm, slapd, apache2, bacula and others.
Kernel is 2.6.22-14
Everything was ok until yesterday: as soon as the system is loading klogd, well, it freezes unexpectedly!
In the sense that the last comment I can see during boot up is
*Starting kernel log deamon

There is no completion for this action (i.e. [OK]) and even if I can start the system in recovery mode, I do not know what to do.
I also uninstalled webmin, but nothing changed.

Could you please help me?
Do you need any other kind of information?

Thanks a lot!!!!
Akall

---

### Post by faulkes on 2008-02-26
Boot into recovery mode and then manually start klogd to see what happens.

```

/etc/init.d/klogd start

```

Faulkes

---

### Post by akall on 2008-02-26
Thanks Faulkes!
I ran it as you told me and launched that command: the daemon started without any problems.

After restart (normal startup) the system is still hanging....:-(((

---

### Post by faulkes on 2008-02-26
> **akall said:**
> Thanks Faulkes!
I ran it as you told me and launched that command: the daemon started without any problems.

After restart (normal startup) the system is still hanging....:-(((

Well, the next step is to determine what starts after klogd as that sounds like
where the issue may be.

However, I would also suggest that you once again go into recovery mode
and do the command I originally listed below and check the logs in /var/log
(/var/log/kern.log iirc) for any unusual messages.

IIRC it is dbus which starts up after klogd, so after executing the above command try 

```

/etc/init.d/dbus start

```

and see if the system freezes.  If it does, restart in recovery mode and 
immediately begin looking at the log files in /var/log (messages, syslog,
daemon).

Faulkes

---

### Post by faulkes on 2008-02-26
After a bit of searching on other bugs, I came across the following which
appears to directly relate to your problem.

Please see the workarounds in the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/openldap2/+bug/150006](https://bugs.launchpad.net/ubuntu/+source/openldap2/+bug/150006)

Faulkes

---

### Post by akall on 2008-02-27
Thanks again!
I will read it carefully and do what they suggests.
Just a question on the first answer by Alexander Nofftz (that seems the way to correct the problem): how do I move" slapd from S19slapd to S10slapd"? Is it something in init.d?
Sorry, I an absolute beginner with sysadmin;-)

bye!
Akall

---

### Post by faulkes on 2008-02-27
If i recall correctly, you must manually rename / relink or move the files.

/etc/init.d are the base startup files, you should never touch these, instead look to
the /etc/rcX.d (where X is a number) directory, within those directories you will
find symbolic links which point back to /etc/init.d/<script name>

```

cd /etc/rc2.d
mv S19slapd S10slapd

```

You may wish to check the other /etc/rcX.d directories to ensure any other links
to S19slapd are changed as well to S10slapd.

Note: Remember, whenever you make a system change like this, write it down 
somewhere so you can refer back to it later if you need to.

Faulkes

---

