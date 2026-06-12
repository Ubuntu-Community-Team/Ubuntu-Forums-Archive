---
title: "lot of kernel updates"
date: 2011-02-10
forum: Server Platforms
---

### Post by Vegan on 2011-02-10
I have noted this winter for 10.10 that there have been a significant number of kernel updates.

I like that updates are frequent when problems are found and fixed.

I wonder if there is anyway for my backup script to be able to notice if the machine needs to be rebooted after calling update/upgrade?

I prefer not to reboot unless necessary.

---

### Post by elico on 2011-02-10
well an effective kernel update is by rebooting.the main question is how are these updates realated to you and your usage.
if you dont get any problem wiht the kernel out of the box and there is no critical update just update the kernel once 2-3 weeks in a very specific time and test the kernel..

---

### Post by Vegan on 2011-02-15
I have my box on automatic update, this way I can ignore the problem

I simply note that when I log in with a terminal, it often asks to be rebooted

---

### Post by iissmart on 2011-02-15
I am unfamiliar with the new information they added when you log in via terminal in newer version of Ubuntu (I still use 8.04 which just takes you straight to a prompt), but I would check if there is a .profile or .login or .bashrc that has a command in there that checks if your computer updated the kernel and needs a reboot.

---

### Post by Vegan on 2011-02-15
I am using 10.10 which is more recent so it has more bell's and whistles.

I was hoping somebody could cough up with shell command to detect the situation so I could say, add it to my backup script which runs daily.

---

### Post by Thirtysixway on 2011-02-15
This doesn't exactly answer your question, but with something like a kernel upgrade you'll probably want to manually reboot it. That way if something goes wrong, you can fix it then instead of having it broken for two weeks.

A kernel upgrade won't add functionality to your server, and most times you'll be okay for a little while without rebooting.  I know you want to have it fully automated, but that piece shouldn't be automated.

Another option is you could schedule your backups once a week and just do a reboot. Then it would catch any kernel upgrades.


But here's one I found on google, not sure if it works still.
[http://ubuntuforums.org/showthread.php?t=559864](http://ubuntuforums.org/showthread.php?t=559864)

---

### Post by Vegan on 2011-02-16
At present I backup daily and have no desire to slow that down.

I was thinking of mechanizing update/upgrade with a script and then reboot after.

That could be linked /etc/cron.weekly easy enough I guess.

something like

apt-get update -y
apt-get upgrade -y
reboot


my box reboots relatively fast and the machine is responding to http requests inside 30 seconds so a reboot is not a big nuisance

---

### Post by James78 on 2011-02-16
I chased down some system files for you. You could check them out if you want. Here's how it works.

Your system requires a reboot, motd tells you. So how does it tell you? It's files are located in /etc/update-motd.d/. In there is "98-reboot-required", which lead me to "/usr/lib/update-notifier/update-motd-reboot-required", which led me to "/var/run/reboot-required"

So, when you require an upgrade, check the last 2 files, and maybe, just maybe, you might have a solution you can put into cron.

/usr/lib/update-notifier/update-motd-reboot-required
/var/run/reboot-required

An example solution could be...
```
#!/bin/bash

if [ -f /var/run/reboot-required ]; then
    reboot
fi
```

---

### Post by Vegan on 2011-02-19
Thanks, I added that to my backup script.

I implemented daily updates and now I can reboot only when needed

Seems my backup script is growing increasingly sophisticated

---

### Post by Vegan on 2011-03-05
I see there is yet another kernel update

2.6.35-27 is now released

---

