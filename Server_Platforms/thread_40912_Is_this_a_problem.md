---
title: "Is this a problem"
date: 2005-06-11
forum: Server Platforms
---

### Post by brickbat on 2005-06-11
Hi, I have this in my auth.log file

Jun  7 19:52:12 localhost sshd[8415]: Received signal 15; terminating.
Jun  7 19:54:09 localhost sshd[8407]: Server listening on :: port 22.

I never started it and I never killed it. I don't use it.  Now I looked in etc/init.d/ and SSH is running as a server.  I never started that either.

Also, what is this all about.  It is filling my auth.log file

Jun 10 01:17:01 localhost CRON[13545]: (pam_unix) session opened for user root by (uid=0)
Jun 10 01:17:01 localhost CRON[13545]: (pam_unix) session closed for user root
Jun 10 02:17:01 localhost CRON[16609]: (pam_unix) session opened for user root by (uid=0)
Jun 10 02:17:01 localhost CRON[16609]: (pam_unix) session closed for user root
Jun 10 03:17:02 localhost CRON[19669]: (pam_unix) session opened for user root by (uid=0)
Jun 10 03:17:02 localhost CRON[19669]: (pam_unix) session closed for user root

ciao
bb

---

### Post by FLeiXiuS on 2005-06-11
You may want to check the last logged on users, and see if anything looks suspicious...
```
sudo lastlogin
sudo last
```
Check the man pages for parameters and filtering.

Another ideal would be to disable the root account.  You don't need it with complete sudo access.
```
sudo passwd -l root
```


Also, this activity is usually normal if you have certain things such a mounted network drive using NFS or SAMBA.

---

### Post by brickbat on 2005-06-11
ok, I tried sudo last and nothing looks suspicious.

I thought the root account was disabled by default.  I never enabled it!

Anyway, I did what you said. I'll see what happens now,

ciao
bb

---

### Post by dmccarney on 2005-06-11
> Jun 10 01:17:01 localhost CRON[13545]: (pam_unix) session opened for user root by (uid=0) 

I was under the impression that is normal because it is just Cron running all the jobs that need root permission. I could be terribly wrong, I'm new to the whole linux paradigm.

---

### Post by LordHunter317 on 2005-06-11
> **brickbat]I never started it and I never killed it. I don't use it.  Now I looked in etc/init.d/ and SSH is running as a server.  I never started that either.[/quote]You probably installed when if you installed the master 'ssh' package, which installs both server and client.  You have mistakenly enabled the server, which would cause it to be running.  Use update-rc.d to disable it.

> Also, what is this all about.  It is filling my auth.log fileThis is perfectly normal.  Your system has lots of cron jobs that mus run as root, every nite.

[quote=FLeiXiuS]Another ideal would be to disable the root account. You don't need it with complete sudo access.[/quote]He never enabled it.  The root account isn't truly disabled on Ubuntu said:**
> Also, this activity is usually normal if you have certain things such a mounted network drive using NFS or SAMBA.Cron jobs have absolutely nothing to do with mounted network shares.  He'll see those lines every nite the box is running, period.

---

### Post by jdong on 2005-06-11
No, this is NOT normal. SSHd is starting and stopping for some reason, which causes PAM to reopen a root session every restart....

Signal 15 is a standard sigterm.... don't know why that'd be issued.

---

### Post by LordHunter317 on 2005-06-11
[QUOTE=jdong]No, this is NOT normal.[/quote]Yes, both sets of messages are.  You're confusing the two sets of error messages.  The first set related to SSH is not related to set on the bottom.

> Signal 15 is a standard sigterm.... don't know why that'd be issued.It was sent to stop sshd.

---

### Post by kvidell on 2005-06-11
[QUOTE=LordHunter317]Yes, both sets of messages are.  You're confusing the two sets of error messages.  The first set related to SSH is not related to set on the bottom.

It was sent to stop sshd.[/QUOTE]
 That's what he said.
The question is WHY is the SSHD restarting without prompting?
- Kev

---

### Post by LordHunter317 on 2005-06-11
[QUOTE=kvidell]That's what he said.[/quote]No, it really isn't.  Least, I certainly didn't interpret it that way.

> The question is WHY is the SSHD restarting without prompting?You can't discern that it is restarting without prompting.  

My guess, based on the times is that it was told to stop during a package upgrade and then was automatically started at the end of it, as is normal for daemon upgrades.  

But it's just that, a guess.  You can't discern the cause from information given.  I suspect it was for normal reasons.  If it was encountering a problem, it should be reporting other things.

---

### Post by desdinova on 2005-06-11
I run SSH server and client and even with my cron jobs I do not see these messages.... (The ssh one that is) - did it crash and restart itself? Is it just a one off

I'm reasonably knew to Ubunto (But not LInux) - is the ubuntu SSH compiled with tcp-wrappers - if you want to open SSH to the world it would be good practice to lock it down ...

I do have the cron ones though

---

### Post by LordHunter317 on 2005-06-11
[QUOTE=desdinova]I run SSH server and client and even with my cron jobs I do not see these messages....[/quote]Run /etc/init.d/ssh restart.  You should see those two messages in the daemon log.  

>  (The ssh one that is) - did it crash and restart itself?It can't restart itself if it crashes, so no.

> I'm reasonably knew to Ubunto (But not LInux) - is the ubuntu SSH compiled with tcp-wrappersI don't know if it is, but host access can be limited by sshd proper.

---

### Post by desdinova on 2005-06-11
[QUOTE=LordHunter317]Run /etc/init.d/ssh restart.  You should see those two messages in the daemon log.  

It can't restart itself if it crashes, so no.

I don't know if it is, but host access can be limited by sshd proper.[/QUOTE]
 I know you'll see them if you restart - but he says he didn't restart - and the signal 15 is  symptomatic of something......

---

### Post by LordHunter317 on 2005-06-11
[QUOTE=desdinova] but he says he didn't restart[/quote]He said he didn't even know it was running or that at was installed. 

> and the signal 15 is  symptomatic of something......Yeah, sshd being stopped.  SIGTERM only gets sent if something stopped it.  What stopped it, we don't know, nor can we tell.   But I don't see any reason to suspect bad behavior on the part of anything.

---

### Post by brickbat on 2005-06-12
Thanks for all the comments but I'm more confused now than before!

Ok, assuming I do not use the client or the server for anything knowingly, am I losing anything by uninstalling it?

Do any programs refer to it?

Will I break anything by uninstalling it and what do I need to uninstall to get rid of it completely.

update:

I tried unistalling it and it uninstals Kubuntu desktop and lots of other stuff.

What exactly are the commands to kill it and to stop it starting up automatically.

thanks
bb

---

### Post by LordHunter317 on 2005-06-12
[QUOTE=brickbat]Thanks for all the comments but I'm more confused now than before!

Ok, assuming I do not use the client or the server for anything knowingly, am I losing anything by uninstalling it?

Do any programs refer to it?

Will I break anything by uninstalling it and what do I need to uninstall to get rid of it completely.

update:

I tried unistalling it and it uninstals Kubuntu desktop and lots of other stuff.

What exactly are the commands to kill it and to stop it starting up automatically.

thanks
bb[/QUOTE]
 Removing the server portion of ssh should be as simple as running:```
sudo apt-get uninstall openssh-server
```.  This may want to remove other packages, including 'ssh' and 'kubuntu-desktop'.   This is OK, as both of them are virtual packages, and you don't lose anything if they are removed.

---

### Post by jdong on 2005-06-12
[QUOTE=LordHunter317]Removing the server portion of ssh should be as simple as running:```
sudo apt-get uninstall openssh-server
```.  This may want to remove other packages, including 'ssh' and 'kubuntu-desktop'.   This is OK, as both of them are virtual packages, and you don't lose anything if they are removed.[/QUOTE]
that's **apt-get remove**, not uninstall.

---

### Post by LordHunter317 on 2005-06-12
Yeah, yeah, my apologies. :) 'Tis what happens when I post right after waking up.

---

### Post by brickbat on 2005-06-13
Done. thanks.  I think it is wrong to install ssh server automatically with kubuntu desktop.

---

