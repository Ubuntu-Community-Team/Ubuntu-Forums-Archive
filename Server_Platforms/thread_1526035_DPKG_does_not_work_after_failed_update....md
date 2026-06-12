---
title: "DPKG does not work after failed update..."
date: 2010-07-07
forum: Server Platforms
---

### Post by rkolech on 2010-07-07
Hello, I was hoping to get some help with an issue I am having.  I am fairly new to Ubuntu and I am lost.

I am running Ubuntu Server 10.04 as a virtual machine in VirtualBox.  I have Webmin installed on the server as well.  A few days ago I was running some updates via the Webmin front end, and something went wrong with the update, the screen just said installing for a few hours, but nothing was happening.  I rebooted the virtual server.  

I though I would try the 'SUDO apt-get upgrade' command to retry the update, but now I just get an error.  Somehow I managed to mess up dpkg.

The Error I get is:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```When I run 'sudo dpkg --configure -a' I get this other error:
```
dpkg: parse error, in file '/var/lib/dpkg/status' near line 0:
 EOF after field name `'
```So there seems to be an issue with that 'status' file.  When I open it, I don't see anything so it seems empty.  I am not familiar with 'dpkg' at all so I am not sure what this file is.  Does anyone have any suggestions on how to get this going again?

Thanks!

---

### Post by upbeat.linux on 2010-07-07
You should have this file:

```
/var/lib/dpkg/status-old
```

Try

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

If that fails backups of status exist in */var/backupsdpkg.status.** you can try copying one of those over till it works.

---

### Post by rkolech on 2010-07-07
Thanks for your reply.  I was able to solve the issue.

In my case '/var/lib/dpkg/status-old' was corrupted/empty as well.  However, I take periodic backups of my virtual machine, I was able to load one of these older states and grab a copy of the '/var/lib/dpkg/status' file and replace my corrupted one.

I was then able to run the 'sudo dpkg --configure -a' command.  After that it has me re install the 'linux-firmware' package, this is the one it crashed on.

Now I am able to run the 'apt-get update' and 'apt-get upgrade' commands.  Thanks for your help.

---

### Post by upbeat.linux on 2010-07-08
Glad to hear everything worked out! :)

---

