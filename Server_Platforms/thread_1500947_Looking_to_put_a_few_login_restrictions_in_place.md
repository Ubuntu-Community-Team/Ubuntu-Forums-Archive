---
title: "Looking to put a few login restrictions in place"
date: 2010-06-03
forum: Server Platforms
---

### Post by derdud on 2010-06-03
Hey all. :)  I've got Ubuntu server 10.04 set up and I wanted to make a few restrictions. It's pretty much just acting as a VMware server at the moment, and there are some users I've created who I only want to be able to be able to log into the VMware infrastructure web interface. I want to make sure these users can't log in via SSH, FTP, or the console itself. I understand how to block them from logging in via SSH by using DenyUsers, and I added these users to the /etc/ftpusers file to lock them out of FTP, but how can I block them from logging in at the console itself?

I tried locking the user out by editing the /etc/passwd file, but the problem is that by doing this, it also prevents the user from being able to log into the VMware web interface.

The user's entry in /etc/passwd looks like this:

bsmith:*:1005:1005:Bob Smith,,,:/home/bsmith:/bin/bash

---

### Post by soltanis on 2010-06-03
```

sudo chsh -s /usr/sbin/nologin [user]

```

I have never tried this on an Ubuntu machine, but I have on a Fedora server. It displays a message to the user informing them they are not allowed to login and then exits non-zero, effectively preventing them from getting a shell via any normal login methods.

---

### Post by derdud on 2010-06-03
> **soltanis said:**
> ```

sudo chsh -s /usr/sbin/nologin [user]

```

I have never tried this on an Ubuntu machine, but I have on a Fedora server. It displays a message to the user informing them they are not allowed to login and then exits non-zero, effectively preventing them from getting a shell via any normal login methods.

Well that definitely works to prevent them from logging in, but I don't know its affect on VMware access yet. The weird thing is that VMware is now not working suddenly (it's obviously not related to this command). I rebooted after some system updates were applied, noticed VMware wasn't running... so I tried to manually start it and got an error saying it wasn't configured properly and that I had to run the configuration script again. Really odd because it was working perfectly prior to the reboot. I'll have to look into it more tomorrow. Bah.

---

### Post by derdud on 2010-06-03
Ok so I decided to stay a few minutes later than I've already stayed here at the office. heh. I reconfigured VMware (hopefully it stays this time) and tried logging in as one of the users disallowed from accessing the console. The users can successfully log into VMware so that's a perfect fix. Thank you.

---

