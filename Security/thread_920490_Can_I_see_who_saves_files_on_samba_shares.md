---
title: "Can I see who saves files on samba shares?"
date: 2008-09-15
forum: Security
---

### Post by xyrer on 2008-09-15
Hi, I need to know the ip of the machines that save files on my samba shares, is that possible? there's some viruses on the xp machines on the network and these viruses look for any shares and save copies of it, I want to track it down and it occurred to me that maybe my unbuntu can log the ips of those machines.

Please tell me if it is possible. Thanks.

---

### Post by cdenley on 2008-09-15
> **xyrer said:**
> Hi, I need to know the ip of the machines that save files on my samba shares, is that possible? there's some viruses on the xp machines on the network and these viruses look for any shares and save copies of it, I want to track it down and it occurred to me that maybe my unbuntu can log the ips of those machines.

Please tell me if it is possible. Thanks.

You can use a line like this in your share's configuration
```

vfs objects = extd_audit

```
You might have to play around with the log level settings. I have "log level = 0 vfs:2" in my smb.conf. It seems to log deleted files in the samba logs, but for new files it only gets logged to syslog.

---

### Post by xyrer on 2008-09-17
You say it gets logged to syslog, do you know where exactly can I see that? and why is it a problem?

---

### Post by cdenley on 2008-09-17
> **xyrer said:**
> You say it gets logged to syslog, do you know where exactly can I see that? and why is it a problem?

It gets logged to /var/log/syslog, along with a bunch of other stuff.
```

less /var/log/syslog
less /var/log/syslog.0
zcat /var/log/syslog.1.gz|less

```
It doesn't say which user is performing the function, only the PID of the samba process. It it were logged through samba, I think you can configure samba to create separate log files for each user, so the extd_audit stuff would be easy to look up and match to a specific user.

---

### Post by xyrer on 2008-09-17
With "users", you mean system users or any user on network? because I only need the ip.
Anyway I'll test with the samba logs.
Could you give me an example of where should I put that code?

---

### Post by cdenley on 2008-09-17
> **xyrer said:**
> With "users", you mean system users or any user on network? because I only need the ip.
Anyway I'll test with the samba logs.
Could you give me an example of where should I put that code?

Here is an example of a log entry
```

Sep 17 12:15:33 www smbd_audit[22662]: open path/to/myfile (fd 31)

```

But I just noticed that opening connections are logged, too.
```

cdenley@www:~$ grep 22662 /var/log/syslog|less
Sep 17 10:23:08 www smbd_audit[22662]: connect to service myshare by user myusername

```

So you could trace it back to the user, but not the ip. Anyway, to enable this, you need to edit /etc/samba/smb.conf
```

[global]
...
log level = 0 vfs:2
...
[myshare]
...
vfs objects = extd_audit
...

```
then restart samba
```
sudo /etc/init.d/samba restart
```

---

### Post by xyrer on 2008-09-17
so... if I want lo log the session creation, the users would have to be on my system? because that would be a no go for me, I have a lot of users and new ones every day, that's why I'm more interested on ip.
You were impling that maybe with a differentent log level I could do it?

---

### Post by cdenley on 2008-09-17
> **xyrer said:**
> so... if I want lo log the session creation, the users would have to be on my system? because that would be a no go for me, I have a lot of users and new ones every day, that's why I'm more interested on ip.
You were impling that maybe with a differentent log level I could do it?

Yeah, maybe. I gave up on trying something like this before. I can't play around with the server because it is being used, and I don't feel like setting up a server to test it. Let me know if you get it working.

---

### Post by megerdin on 2008-09-18
thanks **cdenley**

i had same questionsI just add this in my smb.conf

> vfs objects = extd_audit


Now its working excellent, I can trace everything.....

---

### Post by xyrer on 2008-09-28
> **megerdin said:**
> thanks **cdenley**
Now its working excellent, I can trace everything.....

You mean you can trace the ip of the machine that saved files?

---

