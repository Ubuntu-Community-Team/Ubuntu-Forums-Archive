---
title: "Running a script as a different user"
date: 2006-04-26
forum: Server Platforms
---

### Post by hagen00 on 2006-04-26
Hi there

When I start my IRC server, I don't want it to run as root, but as a different user. 

I've tried the following commands at the beginning of the startup script, but both don't work, i.e. the IRC server still runs as root and not as unreal

```
su unreal
```

```
export USER="unreal"
export HOME="/home/unreal"
```

What is the right way to run a script as a user of your choice? 

Thanks!

---

### Post by LordHunter317 on 2006-04-26
Read the manpage for start-stop-daemon, which is what is used to start software on Ubuntu.  Post back if you get stuck.

---

