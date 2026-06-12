---
title: "I need a script to run at startup"
date: 2009-07-07
forum: Server Platforms
---

### Post by theozzlives on 2009-07-07
Instead of Apache, I'm using a different web server software. I need a root terminal to run startup.sh, and I want it to run automatically. Currently, I bring up a terminal, do sudo su, change directories to the server, then startup.sh.

---

### Post by Thirtysixway on 2009-07-07
[http://ubuntuforums.org/showthread.php?t=571322](http://ubuntuforums.org/showthread.php?t=571322)

---

### Post by theozzlives on 2009-07-09
I've never written a script before (pretty good at batch files).```
#!/bin/bash
sudo -u ozzie su 
cd /usr/local/server/storesonlinepro
./startup.sh
```This looks more like a batch file, anyhoo it don't work and can I put it in "Startup Applications"? HELP Please!

EDIT: Just so you know, I have to use "sudo su" to activate root's .bashrc cause I have an environment variable in there.

---

### Post by kemra on 2009-07-09
I believe if you either move the script or make a link to it in **/etc/init.d** then it should be loaded at system boot up as the root user.

So either move startup.sh to **/etc/init.d** or

```
ln -s /usr/local/server/storesonlinepro/startup.sh /etc/init.d/webstartup.sh
```

The above code will make a symbolic link that should make it start OK. Also note I've renamed the script as it appears in **/etc/init.d** just so it doesn't interfere with any startup scripts that are already in place.

Does this help?

---

### Post by CSandman on 2009-07-09
If all you need is an environment variable from root's .bashrc file you could always just export the variable in the script itself.

```
export VARNAME=value
```

That gets you around needing sudo su if thats all you need it for.  

Then either /etc/init.d or having gnome/kde/xfce's session manager run the script at startup.  The main difference being /etc/init.d is run before a bunch of things.  So if your script depends on certain daemons being active you should use the session manager or add a "sleep x" to the script in /etc/init.d to make sure everything works.

Cheers

---

