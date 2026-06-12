---
title: "Server hangs on boot"
date: 2010-07-27
forum: Server Platforms
---

### Post by matthewboh on 2010-07-27
I'm trying to track down a problem with my server.  Basically, I can get it to boot with a LiveCD and do rescue stuff with it - I just can no longer get it to boot.

I've been slowly working my way through all of the error messages that come up during the boot process, and knocking them off one by one.  Right now, they're fairly minor.

I'm trying to find out what the big issue is by looking at the logs.  The last thing that it does is bring up apache2, says [OK] and then hangs.  I've tried to do ls -lustR on /var/log to see what's the last log touched, and that's syslog or boot.log, but the last entry says something along the lines of Apache2 is up and running.

Where else should I look?

---

### Post by wojox on 2010-07-27
Check Apache error logs.

---

### Post by Sporkman on 2010-07-27
Try looking at /var/log/messages .

If you're feeling ambitious, you could try adding

echo "Here I am in such-in-such init script" >> mylogfile
...
echo "Now leaving such-in-such init script" >> mylogfile

statements in the "start" sections of the init scripts in /etc/init.d to track down where the problem is happening...

---

### Post by matthewboh on 2010-07-27
That's one of the things I'm currently trying to do is figure out where those init scripts are - 

Should I be looking at all of the init.d scripts or is it in each of the rcx.d directories?

Sorry for the noob questions....

Figured that I need to look at rcS.d and rs2.d - and started to put in echoes - looks like it's the headless soffice install

---

### Post by BenWuan on 2010-07-27
Have you tried booting it up without the network cable plugged in. Might get you a little further, helped me once.

---

### Post by matthewboh on 2010-08-01
Woohoo!  Fixed it - thanks everyone!  I went into rc2.d and looked at all the jobs and started putting in echo statements for each one - found out that the problem was with the headless OpenOffice jobs - changed the ability for them to execute to off with chmod -x statement, and had to do a little fooling around with the /etc/network/interfaces file - eBox install apparently did something to it - and now I'm up and running.

---

