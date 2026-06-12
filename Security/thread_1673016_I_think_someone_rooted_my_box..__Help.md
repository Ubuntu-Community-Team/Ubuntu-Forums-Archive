---
title: "I think someone rooted my box..  Help?"
date: 2011-01-21
forum: Security
---

### Post by SleepWalkerX on 2011-01-21
I run apache on a non standard port (82).  

I just installed unity to play around with it and while I was playing with it I installed prixfixe through software center to edit the menus.  While prixfixe was installing my computer was acting very slow which was odd, but not completely unusual.  During this time I ran ps aux which showed that my apache server was taking up most of the processing power.  I was about to stop my web server, but I waited just in case the web server was updating a few things (I run ampache).  

My computer finished installing the software and then I ran some command with sudo (I can't remember what the command was), but it threw back some message saying "setid blabla".  I restarted my computer and when I got to my gdm my normal user account did not show up.  There were no accounts and the restart/shutdown buttons didn't work.

Now I'm running on a livecd and checking out my apache access logs, apache error logs, and kernel logs, but nothing looks out of place..  Any ideas?

---

### Post by cariboo on 2011-01-21
Have a look at /var/log/auth.log to see if anyone you don't know has logged in. Also check who to see who is currently logged on, and last to see who else was logged in.

---

### Post by SleepWalkerX on 2011-01-21
Thank you.  I have the *******'s ip.  He's been trying to brute force me all afternoon.  I'm going to try to report him to his isp, but unfortunately my italian isn't that great..

---

### Post by CharlesA on 2011-01-21
Just block their IP and leave it at that.

---

### Post by sisco311 on 2011-01-21
> **SleepWalkerX said:**
> I restarted my computer and when I got to my gdm my normal user account did not show up.  There were no accounts and the restart/shutdown buttons didn't work.


This is a known issue:

[http://ubuntuforums.org/showthread.php?t=1672995](http://ubuntuforums.org/showthread.php?t=1672995)
[http://ubuntuforums.org/showthread.php?p=10379042](http://ubuntuforums.org/showthread.php?p=10379042)

---

### Post by SleepWalkerX on 2011-01-21
Thanks for the links.  I tried dpkg-reconfiguring and reinstalling gdm, but my user account still doesn't show up.  Also, there is no /usr/lib/dbus-1.0/dbus-daemon-launch-helper file.  I'll have to do some digging.

---

### Post by SleepWalkerX on 2011-01-21
Oh, and I also changed permissions on my /etc/sudoers file to get rid of my setid sudo problem.

---

### Post by SleepWalkerX on 2011-01-21
When I try to run startx in the console it says user is not authorized to run X.  It seems like all my permissions were fubared.  I added myself to the video group, but that didn't seem to help.

---

### Post by cariboo on 2011-01-21
You probably have to add yourself back to the admin group, start in recovery mode, then at the prompt type:

```
gpasswd -a admin <user> 
```

You may need to ad your user to the adm group too. You can check using the following command:

```
groups <user>
```

You should be a member of the following groups:

```
adm dialout fax cdrom floppy tape dip video plugdev fuse lpadmin admin
```

---

### Post by SleepWalkerX on 2011-01-21
Thanks, sudo is working.

It turns out I'm suffering from the same issue as the guy in the link you sent me sisco311.  I start console-kit-daemon and my account name appears when I restart gdm.  It sounds like a batch of ubuntu updates might've fubared my system.  I'll continue on that thread.

---

### Post by SleepWalkerX on 2011-01-22
Ah, now when launching chromium-browser I get the following:

[6699:6699:1001880858:FATAL:zygote_host_linux.cc(124)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /usr/lib/chromium-browser/chromium-browser-sandbox is mode 4755 and owned by root.
Aborted

So I chmod 4755 chromium-browser-sandbox and all is well.  It appears my permissions are fubared.  

Should I recursively chmod 4755 my /usr directory?

---

### Post by SleepWalkerX on 2011-01-22
I don't have permission to read my locate database.  Ugh, this is a nightmare.  Any ideas on how to get everything back in order?

---

### Post by CharlesA on 2011-01-22
I would say backup yer data and reinstall. It'll be too much work to try to get everything sorted out.

---

