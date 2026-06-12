---
title: "Deluge Daemon Web UI No Longer Starting"
date: 2014-07-19
forum: Server Platforms
---

### Post by nuttboxer2 on 2014-07-19
Environment:
Ubuntu 14.04 headless server
deluge 1.3.6
libtorrent 0.16.16.0

This setup was running fine until recently.  I updated my sudo password, and installed OpenVPN as I've had a few emails from my ISP.  I can get the console to start successfully, and when I start the daemon and web-ui from command line I get a successful message, but when I check through Webmin, they are not running, and of course I cannot access the web UI.  It either spins forever or immediately says it can't connect in fireofox.  I didn't think it was the VPN as I can access Mediatomb and Webmin just fine, but I tested with VPN off to confirm.

Could changing my sudo password somehow have blocked deluge from starting?  The logs tell me nothing, unless I have the wrong logging setup.

Ok, checked the daemon log and found this:
Error common:167 Unable to use default config directory, exiting... ([Errno 13] Permission denied: '/home/~/.config/deluge')

I'm guessing that password change may have caused an issue somewhere in deluge.  I'll search this error and see what I find if I don't get a response sooner.

---

### Post by ubudog on 2014-07-19
How are you running deluge (which user)?

---

### Post by nuttboxer2 on 2014-07-19
I'm attempting to start the daemon using my sudo user, who is also the user I have listed in my init scripts.  I have added this user to the deluge group as well.  Is that what you're asking?

---

### Post by ubudog on 2014-07-19
Looks like you don't own the config directory for some reason, probably because of running deluge as root at one point.

Try this:
```

chown -R username:username /home/username/.config/deluge

```

---

### Post by nuttboxer2 on 2014-07-19
I tried that, same error.  Not sure what the permissions on this folder were originally, but when I check they were root:root.

---

### Post by ubudog on 2014-07-19
Weird... try backing up your config and having Deluge make a new one.

```
mv .config/deluge .config/delugebak
```

You might have to run that as root (or sudo).

---

### Post by nuttboxer2 on 2014-07-19
How do I recreate the /deluge folder?  Also, noticed I have a user and group named debian-deluged that did not exist before, at least not when I originally set this up.

---

### Post by ubudog on 2014-07-19
If you mean restoring it to like it was, you can just move it back:
```
mv .config/delugebak .config/deluge
```

---

### Post by nuttboxer2 on 2014-07-19
Sorry, not restoring, the having deluge make a new one part.  I only know how to do this by re-installing.

---

### Post by ubudog on 2014-07-19
I believe Deluge will do this automatically whenever you restart it.

---

### Post by nuttboxer2 on 2014-07-19
Ok, got it restarted, and folder recreated, but still same error.

---

### Post by ubudog on 2014-07-19
Make sure Deluge is not running.  Then, run this again:
```
sudo chown -R username:username /home/username/.config/deluge
```

Now try running everything as your regular, non-root user and see if that works.

---

### Post by nuttboxer2 on 2014-07-19
I tried changing permissions and re-starting Ubuntu, still same result.  I'm not sure deluge daemon is every actually running, and that's all I'm using(plus webUI if daemon ever works again).

---

### Post by ubudog on 2014-07-19
Sorry for my lack of assistance with this.

Only thing I could suggest would be creating a Deluge user and updating your init scripts:
```
sudo adduser --disabled-password --system --home /var/lib/deluge --group deluge && sudo chown deluge:deluge /var/log/deluge*
```

You could also try removing it and start over:
[http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient](http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient)

---

### Post by nuttboxer2 on 2014-07-19
Thanks for trying, I appreciate it.

I have a deluge user added as part of the setup.  Thin client is only for accessing the server from other computers right?  If I'm just running webui for access, doesn't seem like I'd need that.  At least I don't remember setting it up in the past.

So when I'm trying to start the daemon, like now, I plug in a monitor, and do it directly on the server.

> **ubudog said:**
> Looks like you don't own the config directory for some reason, probably because of running deluge as root at one point.  Try this: ```
 chown -R username:username /home/username/.config/deluge 
```


This was exactly right I think.  I never changed owner of any of the deluge config files or folders, but today I tried again to chown -R user:deluge /home/user/.config, reboot, and init script started for daemon and web no problem.  Maybe changing the password for the primary user disassociated me from sudo somehow and blocked access to root:root folder I previously had permission for?

Thanks, and sorry I didn't pay closer attention, I think I just didn't reboot after trying this yesterday.

---

