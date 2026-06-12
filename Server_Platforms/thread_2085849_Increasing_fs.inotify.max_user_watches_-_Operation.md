---
title: "Increasing fs.inotify.max_user_watches - Operation not permitted"
date: 2012-11-19
forum: Server Platforms
---

### Post by Cruize on 2012-11-19
Hi, I need to increase fs.inotify.max_user_watches (it's currently at 8192) but I'm running into permission issues. I'm root, running Ubuntu 10.04.3 LTS and /proc/sys/fs/inotify/max_user_watches exists and is chmoded 644

I've tried the following;

sysctl fs.inotify.max_user_watches=20000 (**error: "Operation not permitted" setting key "fs.inotify.max_user_watches"**)

echo 20000 | tee /proc/sys/fs/inotify/max_user_watches (**tee: /proc/sys/fs/inotify/max_user_watches: Operation not permitted**)

echo fs.inotify.max_user_watches=20000 >> /etc/sysctl.conf; sysctl -p (**error: "Operation not permitted" setting key "fs.inotify.max_user_watches"**) 

Any suggestions? Thanks in advance!

---

### Post by littlegreiger on 2012-11-19
Are you sure you are running those commands as root? I tried the first command you posted on a newly installed 12.04 (should work the same for 10.04) and it worked fine. The exact command I ran was ```
sudo sysctl fs.inotify.max_user_watches=20000
```

---

### Post by Cruize on 2012-11-20
Yeah it's a server install, no normal users set up :/

---

### Post by littlegreiger on 2012-11-20
> **Cruize said:**
> Yeah it's a server install, no normal users set up :/

A server install still sets up a normal user, it just gives them sudo privileges. When it asks for your username when you login do you type 'root' or a different name?

---

### Post by Cruize on 2012-11-20
Root, userid 0, no other users setup :/

---

### Post by Cruize on 2012-11-21
I've just heard back from the hosting company that own the VPS, there aren't any restrictions in place so it should work (but most definitely doesn't).

*EDIT* I don't actually believe them, a bit of digging has found that sysctl isn't usable with OpenVZ linux installs. I've asked if they're using OpenVZ, will see what the response is and update accordingly.

The reason I'm trying to do this is because I have a free 50gb Dropbox account and have been using it to backup certain parts of the server. I've hit a limit in the number of directories and the only fix is changing the value for max_user_watches.

---

### Post by littlegreiger on 2012-11-21
Yeah, some quick googling shows that it's a problem with OpenVZ, hopefully your provider can figure out how to change it for you.

---

