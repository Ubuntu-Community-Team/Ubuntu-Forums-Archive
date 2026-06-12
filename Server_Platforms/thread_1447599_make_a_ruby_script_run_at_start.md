---
title: "make a ruby script run at start"
date: 2010-04-05
forum: Server Platforms
---

### Post by Tompalaz on 2010-04-05
Hi.

I have set up a subversion server and on top of that redmine which is a webinterface sort of like trac.

For every boot I have to run a script so that redmine will listen to port 8080. I have tried to make the system run this script by it self at start using 
```
# update-rc.d -f start_servers start 99 2 3 4 5 .
```
using this guide [http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)


This is my script
> #!/bin/sh

# Go to redmine directory
cd /var/www/redmine/

sleep 1

# Start Redmine on port 8080
ruby script/server -e production -p 8080

permissions:
> -rwxr-xr-x 1 root root 141 2010-04-05 21:12 /etc/init.d/start_servers

Please help me get this running!

ubuntu server 9.10 x86_64

---

### Post by ajgreeny on 2010-04-05
Try adding the contents of the script to /etc/init.d/rc.local.  If the script runs as expected from terminal, it should run at boot if included as an entry in that file.

---

### Post by Tompalaz on 2010-04-06
Can I just add this part?

> cd /var/www/redmine/
# Start Redmine on port 8080
ruby script/server -e production -p 8080

or should it integrate somehow with the script in the rc.local file?

---

### Post by ajgreeny on 2010-04-06
I think that's right, ie, you don't need the **#!/bin/bash** line, because if you look, it is already in the rc.local file.

You may still need the **sleep** line, depending on why it's there in the first place.

Try it out, it can't really do any harm, assuming the script, when run normally doesn't.

---

