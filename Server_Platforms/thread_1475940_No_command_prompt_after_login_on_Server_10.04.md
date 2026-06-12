---
title: "No command prompt after login on Server 10.04"
date: 2010-05-07
forum: Server Platforms
---

### Post by jenx2seven on 2010-05-07
Hi,

I have upgraded my ubuntu server install from 9.10 to 10.04 with no problems.  

Now when I boot up I am presented with the login prompt where I put my username and password in.  I am told when I last logged in and then nothing - just a flashing cursor.  No prompt to enter any commands.  I can type at the cursor but nothing happens.

Any ideas?


Apart from this the server appears to be running fine - MySQL/Apache are doing their stuff.

---

### Post by whoop on 2010-05-07
Do you have ssh service running? Does that work?
Does any other tty work (for example Ctlr+Alt+F3)?

---

### Post by sylvester_0 on 2010-05-07
Try pressing Ctrl-C. It sounds like one of the "pretty" login scripts (X updates available etc) is getting hung up. Are you able to login with another user?

---

### Post by jenx2seven on 2010-05-07
> **sylvester_0 said:**
> Try pressing Ctrl-C. It sounds like one of the "pretty" login scripts (X updates available etc) is getting hung up. Are you able to login with another user?

Excellent.  Pressing Ctrl-C a few times got me to a prompt.  Thanks for that.  

Now - any clue how I go about fixing this? How do I find what's hanging?   Can you tell I'm a little green to this ;)

---

### Post by sylvester_0 on 2010-05-07
It appears that the MOTD is generated from the scripts in /etc/update-motd.d I'd recommend going into that directory and running them one by one to see which one is breaking and debug from there. Good luck!

```
user@netbook:~$ cd /etc/update-motd.d/
user@netbook:/etc/update-motd.d$ ls
00-header     20-cpu-checker        91-release-upgrade  99-footer
10-help-text  90-updates-available  98-reboot-required
user@netbook:/etc/update-motd.d$ ./00-header 
Linux netbook 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS
user@netbook:/etc/update-motd.d$ ./10-help-text 

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/
user@netbook:/etc/update-motd.d$
etc...
```

---

### Post by tgalati4 on 2010-05-07
From the command line while logged in:

sudo apt-get update

Then try ssh and see if it takes longer.  Take a stopwatch and time it.  We need some data.

---

### Post by jenx2seven on 2010-05-17
Back again,

It appears that its the **90-updates-available** motd script that is hanging.  Anyone have any ideas as to why?

Thanks

---

### Post by davidshere on 2010-05-24
Wow... this has made my lucid box a hockey puck.  Control-C doesn't do anything -- I don't even get a login screen.  I can't load in safe mode because grub doesn't give me a menu.  Yay.

---

### Post by MianoSM on 2010-07-07
Not sure if this is a help at all, but I recently did a minimal install and found that the landscape-client and landscape-common packages were not included.

Perhaps that might be a more preferred route to take in the future (sorry it doesn't help at the moment, I would suggest modifying the directory/files so that they don't get modified, or removing the above packages).

---

