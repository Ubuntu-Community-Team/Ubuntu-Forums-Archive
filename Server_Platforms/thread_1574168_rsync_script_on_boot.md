---
title: "rsync script on boot"
date: 2010-09-13
forum: Server Platforms
---

### Post by xkaliburx on 2010-09-13
We are looking to centralize some code in a scalable environment.  So some servers may do other jobs, etc. doing other things, but the key element is when the server is booted, I want it to rsync some config files, scripts, etc. local to the box and I am having an issue as things are a bit different from an RHE server.

I have a test entry in the rc.local a simple touch testfile, then after that a restore.sh file.  I reboot the box, wait a minute then login.  I see hte testfile timestamp updated yet the rsync doesn't fire.  I can then manually run it and it works fine, but I need to have this go on boot.

Thanks,

---

### Post by CharlesA on 2010-09-13
Try adding it to a crontab using @reboot for the time.

---

### Post by BkkBonanza on 2010-09-13
You may have a problem where the interface isn't up yet at the time the rsync runs.

You could put a script in /etc/network/if-up.d/ directory and it will run upon interface being up. See if that works but also note that if the interface is taken down/up again after booting for some reason it would get run again. So you may need to code around that using an env var or something, 
eg. 
if [ $RSYNCDONE -ne 1 ]; then
...
fi
export RSYNCDONE=1

---

