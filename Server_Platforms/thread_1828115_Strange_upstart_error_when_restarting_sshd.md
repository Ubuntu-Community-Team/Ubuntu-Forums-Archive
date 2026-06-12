---
title: "Strange upstart error when restarting sshd"
date: 2011-08-18
forum: Server Platforms
---

### Post by ~K~ on 2011-08-18
Hello ubuntu,

For the last umpteen years of my life, I've restarted the ssh daemon using:
```
sudo /etc/init.d/ssh restart
```

Just today, I got this error message:
```
Rather than invoking init scripts through /etc/init.d/, use the service utility, e.g. service ssh restart

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the restart utility, e.g. restart ssh
```

... ok ...

So now I type:
```
sudo service ssh restart
```

and get:
```
restart: Unknown instance:
```

... ok ...

So now I type:
```
sudo restart ssh
```

and get:
```
restart: Unknown instance:
```

Can someone please tell me how to restart sshd now?

BTW, I'm running Ubuntu 10.04.

Thanks, K

---

### Post by SeijiSensei on 2011-08-18
That's a stupid bug.

I installed openssh-server whereupon it naturally started up upon installation.  If I type "sudo service ssh restart" I get the message "ssh start/running, process 8663".  If I then stop the server with "sudo service ssh stop" and re-enter "sudo service ssh restart", as you did, I get the same "unknown instance" error that you report.

Try "sudo service ssh start" and see if that fixes your problem.

As someone with a long history using RedHat-flavored machines, running "service abcd restart" will start the service even if it's not already running.  Apparently the upstart implementation of this command generates an "unknown instance" error, presumably because it can't identify the pid of the supposedly running ssh process.  

I see this as a bug.  I'll take a look at the upstart bug list and see if it's been reported; if not, I'll be happy to do so.

---

### Post by ~K~ on 2011-08-18
> **SeijiSensei said:**
> 
Try "sudo service ssh start" and see if that fixes your problem.


Nope.  Doesn't do jack.

> **SeijiSensei said:**
> 
I see this as a bug. I'll take a look at the upstart bug list and see if it's been reported; if not, I'll be happy to do so. 


I'm not familiar with the Upstart bug list.  If you could handle this, I would appreciate it.

Anyone other suggestions?

Thanks.

- K

---

### Post by SeijiSensei on 2011-08-18
Does "ps ax | grep ssh" show a running server?  Does "sudo service ssh stop" bring it down?  Try stopping it manually, using kill if necessary, then try starting it manually again.

---

### Post by ~K~ on 2011-08-18
> **SeijiSensei said:**
> Does "ps ax | grep ssh" show a running server?  Does "sudo service ssh stop" bring it down?  Try stopping it manually, using kill if necessary, then try starting it manually again.

Yes. "ps aux" shows a running server.  In fact, this is a remote server that I am administering via ssh.

I haven't tried to stop the service, because I do not want to be kicked off permanently, which would require a reboot to get ssh back.

---

### Post by ~K~ on 2011-08-18
After scratching my head all afternoon and reading every know post about Upstart, I figured that I'd have to bite the bullet and reboot my server.  It has uptime currently listed at 110 days, so I figure it may have some old configuration stuck in memory that doesn't jive with the new upstart service.

So I did the reboot.  Luckily, that went smoothly.

And now "sudo restart ssh" works just fine.

I hope this is able to help the others out there with this same problem.

---

### Post by tcsmith1978 on 2011-08-19
Just thought I'd chime in here - I had the same issue with dovecot. Restarting through init.d seemed fine but still have no idea why I can't restart dovecot the normal way!

---

### Post by SeijiSensei on 2011-08-19
I'll hazard a guess that it has to do with different methods of creating lock files based on the process's pid.  Perhaps /etc/init.d methods put the file somewhere where upstart isn't looking.  That's why I suggested to ~K~ that he use ps to see if there was a running ssh instance.  Apparently upstart couldn't determine that the process was already running and failed as a result.

Upstart seems to me to still be "not ready for prime time."  It's one of the reasons why I've hesitated to shift my servers from CentOS to Ubuntu.

---

