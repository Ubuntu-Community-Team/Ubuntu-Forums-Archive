---
title: "Turn off services"
date: 2010-08-16
forum: Server Platforms
---

### Post by borobudur on 2010-08-16
Hi, how can I totally turn off some services on my server? I'd like to clean it up a bit...

With apt-get remove I made bad experience because it removed also other packages which other program needed. With the --purge argument I just remove the one package and lots of other stuff is left there. 

What about removing the /etc/init.d/XY script? The the service doesn't get started, right?

---

### Post by arrrghhh on 2010-08-16
Well, with the new systemV calls, I don't know that removing it from init.d is the best method - it wasn't before either.  The old way was to do the update-rc.d command.  For example: ```
sudo update-rc.d sshd remove
``` replace sshd with whatever service you don't want running on startup.  This method may still be valid, I'm not sure...

Plus, the service is still installed on your server.  It'd probably be best to remove it.  Any services in particular that concern you?

---

### Post by LightningCrash on 2010-08-16
Upstart jobs will still be in /etc/init

ie disabling SSH:
mv /etc/init/ssh.conf /etc/init/ssh.conf.disable

---

### Post by borobudur on 2010-08-17
> **arrrghhh said:**
> Well, with the new systemV calls, I don't know that removing it from init.d is the best method - it wasn't before either.  The old way was to do the update-rc.d command.  For example: ```
sudo update-rc.d sshd remove
``` replace sshd with whatever service you don't want running on startup.  This method may still be valid, I'm not sure...

Plus, the service is still installed on your server.  It'd probably be best to remove it.  Any services in particular that concern you?
I used update-rc.d, looks fine to me. 
Thanks!

---

### Post by borobudur on 2010-08-17
> **LightningCrash said:**
> Upstart jobs will still be in /etc/init

ie disabling SSH:
mv /etc/init/ssh.conf /etc/init/ssh.conf.disable
There is no /etc/init/ directory.

---

### Post by arrrghhh on 2010-08-17
> **borobudur said:**
> There is no /etc/init/ directory.

It's /etc/init.d... not sure what that guy was talking about, it's NOT a good practice to mv the init scripts.  Please use the update-rc.d command as you mentioned you did previously ;)

Also, if you feel the thread has been resolved, please use the "Thread Tools" drop-down menu to mark the thread [SOLVED].  Thanks!

---

