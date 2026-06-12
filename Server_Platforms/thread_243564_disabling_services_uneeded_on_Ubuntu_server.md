---
title: "disabling services uneeded on Ubuntu server"
date: 2006-08-25
forum: Server Platforms
---

### Post by larka06 on 2006-08-25
I am running a ubuntu dns server. I recently decided to disable the unneeded services since it will never do anything but DNS.  I have read through the forums and was unable to find anything that would help me.  I am running 6.06 LTS server.  I did come accross an article that said to use sysv-rc-conf.  I tried that and recieved and error messagae that said no such command.  If anyone out there can help me I sure would appreciate it.
Thanks](*,)

---

### Post by Uluen on 2006-08-25
sudo apt-get install sysv-rc-conf?

---

### Post by Woei on 2006-08-25
> **larka06 said:**
> I am running a ubuntu dns server. I recently decided to disable the unneeded services since it will never do anything but DNS.  I have read through the forums and was unable to find anything that would help me.  I am running 6.06 LTS server.  I did come accross an article that said to use sysv-rc-conf.  I tried that and recieved and error messagae that said no such command.  If anyone out there can help me I sure would appreciate it.
Thanks](*,)

```

sudo apt-get install sysv-rc
man update-rc.d
sudo update-rc.d -f servicename remove

```

Alternatively, although it's already good you're disabling unneeded services, why don't you simply uninstall these pieces of software ? The less software, the less loopholes.

---

### Post by harisund on 2006-08-25
Basically every running service is initiated from a script in /etc/init.d. Fnd out what service is running, look for the script that is closest to that in /etc/init.d/ and execute 'sudo /etc/init.d/service_name stop' and the service will stop. 

To ensure the service doesn't start again next time you boot, 'sudo update-rc.d -f service_name remove'

---

### Post by larka06 on 2006-08-28
Thank you.  I have been go for a few days so, I am slow to respond.

---

### Post by larka06 on 2006-08-28
Thank you all of you for your help.  I have been go for a few days so, I am slow to respond. Now all I need to do is to figure out what to get remove.  Last time I did that I lost everything cause some things had depents

---

