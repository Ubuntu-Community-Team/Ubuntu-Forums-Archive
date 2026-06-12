---
title: "Adding uptime to login screen in 9.04"
date: 2009-05-21
forum: Server Platforms
---

### Post by Vegan on 2009-05-21
WHen I log in on the Linux box. I see:

Last login: Wed May 20 21:54:10 PDT 2009 from 192.168.7.104 on pts/0
Linux ubuntu 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

  System information as of Thu May 21 08:30:02 PDT 2009

  System load: 0.0               Memory usage: 19%   Processes:       82
  Usage of /:  19.2% of 5.39GB   Swap usage:   0%    Users logged in: 0

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Can I add "uptime" to this display so I can see if the server has rebooted of late.

---

### Post by cdenley on 2009-05-21
Add this command to /etc/update-motd.d/50-landscape-sysinfo:
```

/usr/bin/uptime

```

---

### Post by Vegan on 2009-05-22
tried that, does not seem to work

---

### Post by cdenley on 2009-05-22
> **Vegan said:**
> tried that, does not seem to work

It gets updated every 10 minutes? How long did you wait?

---

### Post by Alekz_ on 2009-05-22
Do you want the uptime message to appear when system starts OR when you login?

If it's on login, just put this line into your /etc/profile:

```
echo `uptime`
```

and everytime you login it'll display the system uptime..

---

### Post by cdenley on 2009-05-22
> **Alekz_ said:**
> Do you want the uptime message to appear when system starts OR when you login?

If it's on login, just put this line into your /etc/profile:

```
echo `uptime`
```

and everytime you login it'll display the system uptime..

That will run uptime every time you start a shell, not just every time you login. That might be an alternative, though, but my method works if you wait for /etc/motd to be updated.

---

### Post by Vegan on 2009-05-22
> **cdenley said:**
> It gets updated every 10 minutes? How long did you wait?

It shows now, so I can see a tad more info. Thanks for clarifying that.

---

