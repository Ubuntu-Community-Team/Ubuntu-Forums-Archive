---
title: "upstart problem!"
date: 2009-11-29
forum: Server Platforms
---

### Post by Muttley99 on 2009-11-29
Can someone lead me to a good upstart how to?
I want to run a script at boot. I've tried the old update-rc.d & setting up cron @reboot, but nothing works! After googling around; I realise now upstart is the way to go.
How do I get upstart to run a script at startup? It seems I place the script in /etc/init/?
BTW. I'm using ubuntu-server 9.10

I tried (in detail) to use rc-update.d again. No errors! But still not working! Is there an expert here with knowledge of this? I've searched throughout the net without finding much detail about 'upstart'. It seems to have been slowly integrated into Ubuntu base from around 2006 so I would have thought there was more documentation.
Thanks in advance!

---

### Post by Muttley99 on 2009-11-29
Well, Here's what I've pieced together;

Upstart jobs are placed in the /etc/init/ directory.
They are plain txt and not executable.
They are run based on event listed in the opening header in the file. i.e. start on runlevel 2.

To test the the file;
initctl emit <filename>

Tried all that and no output! 
Tried a 'test' file which just - echo "upstart check" > /tmp/upstart.txt

Any ideas?

---

### Post by sisco311 on 2009-11-29
Well, the documentation is still poor.

[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

[http://upstart.ubuntu.com/wiki/]("http://upstart.ubuntu.com/wiki/")

A skeleton of the file looks like this,
/etc/init/skeleton**.conf**:
```
description     "my daemon"
author          "/me"

start on runlevel [2345]

stop on runlevel [016]

script
  echo testing my upstart job
  commands...
end script
#console output #uncomment it to redirect the output of the script to /dev/console
``` 

to start it:
```
sudo initctl start skeleton
```

BTW, Upstart is backward compatible with the sysv style init scripts(/etc/init.d).

What exactly are you trying to start?

---

### Post by Muttley99 on 2009-11-29
Thanks sisco!

I'm trying to start mediatomb on startup from my NAS using ubuntu-server!

I can start the mediatomb daemon from the command line okay under my login 'david' so I know mediatomb is working okay. I set a script similar to yours to start at runlevel 2 and 

[HTML]mediatomb -d --user david[/HTML]

I've checked 

[HTML]initctl list[/HTML]

It is listed as a waiting/stop process. But mediatomb does not start! I've tried update-rc.d and removing mediatomb then loading it back at 99 as mediatomb needs networking up before it can start. Maybe I can specify 'start on networking' in the conf file? is this the correct event name?

What am I doing wrong?

BTW. I set a check file in /etc/init 'upstart_check.conf' to output to a txt file in /tmp. This works ok!

---

### Post by sisco311 on 2009-11-30
try:
```
description     "my daemon"
author          "/me"

start on started network-manager

stop on stopping network-manager

expect fork
respawn

exec mediatomb -d --user david

```

---

### Post by Muttley99 on 2009-11-30
Tried it and nothing! 

This is very frustrating! I can easily start mediatomb at command line through ssh.

---

### Post by sisco311 on 2009-11-30
Don't start it as daemon, Upstart already starts it in a sub-shell :
```
exec mediatomb -u user
```

---

### Post by Muttley99 on 2009-11-30
It's fixed! I read through an old post. The poster had a similar problem. Edit the /etc/network/interfaces file and add eth1 etc. Initially my NAS refused to start propely, but after removing the lines I added, mediatomb starts at bootup. Weird!! 
Now what's executing this? I had set cron @reboot + update-rc.d or is it upstart?
Anyway, with your help, I've learnt a little bit more about Linux.

Thanks for your time!

---

