---
title: "[SOLVED] Don't run vsftpd at startup"
date: 2008-02-24
forum: Server Platforms
---

### Post by Meson on 2008-02-24
I just installed vsftpd but I don't want it to run automatically.  I know I can manually change all of the S20vsftpd to K80vsftpd in the rc directories, but I don't want to have to do it for every runlevel.

I thought the listen=YES option was suppose to facilitate this, and force it to run standalone, however I still see that vsftpd is a subordinate to init in my running processes.

What's the most efficient way to stop vsftpd from running at startup so that for the few times that I want to use it, I can run "service vsftpd start" or just execute the init script...

---

### Post by faulkes on 2008-02-24
> **Meson said:**
> I just installed vsftpd but I don't want it to run automatically.  I know I can manually change all of the S20vsftpd to K80vsftpd in the rc directories, but I don't want to have to do it for every runlevel.

I thought the listen=YES option was suppose to facilitate this, and force it to run standalone, however I still see that vsftpd is a subordinate to init in my running processes.

What's the most efficient way to stop vsftpd from running at startup so that for the few times that I want to use it, I can run "service vsftpd start" or just execute the init script...

```

sudo update-rc.d vsftpd 20 stop 2 3 4 5 .

```

Faulkes

---

### Post by Meson on 2008-02-24
I get this: ```
System startup links for /etc/init.d/vsftpd already exist.
```

However this worked:
```
sudo update-rc.d -f vsftp remove
```

---

