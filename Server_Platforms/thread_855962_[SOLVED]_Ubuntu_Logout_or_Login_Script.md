---
title: "[SOLVED] Ubuntu Logout or Login Script"
date: 2008-07-11
forum: Server Platforms
---

### Post by Benismyhorse on 2008-07-11
Hi, In my last post I was wanting to make a default desktop, people said Sabayon, I tried but in didn't work but then tried it again and in did, this brings me to my final question (I promise), I want the user's desktop to be reset to the sabayon desktop and after trying I found that if I delete there profile /home/USER then it resets it to the sabayon desktop.
The command I use is rm -r /home/USER, how/where would I put this to get it to run on login and/or logout, but it would be best for logout:confused:.
Please help

Thanks
Shane

---

### Post by cdenley on 2008-07-11
EDIT: koenn's idea is probably better, and a lot easier

I haven't tested this much. Use it at your own risk.

This python script should delete the home directory of any user not logged in every 5 seconds
```

#!/usr/bin/python
import os,time,shutil
while True:
    cmd="w -hs|cut -d \\  -f 1"
    users=[]
    for user in os.popen(cmd).readlines():
        users.append(user[:len(user)-1])
    for home in os.listdir("/home"):
        if users.count(home)==0:
            shutil.rmtree("/home/"+home,1);
    time.sleep(5)

```
Save it somewhere, make it executable by root, add "/path/to/thisscript.py&" to /etc/rc.local before "exit 0". Now it should run at boot time.

I can't think of a better way to do this.

---

### Post by koenn on 2008-07-11
Look in /etc/gdm. There are subdirectories in there, named Init, PostLogin, PreSession, PostSession. You probably want PreSession (before user is logged on) or PostSession (after user has logged out). There's a Default script in these directories that runs as root. It's meant to do sysadmin stuff each time a user logs on / off.

---

### Post by Benismyhorse on 2008-07-12
Thanks a lot everyone your answers really did the trick.

Thanks

---

