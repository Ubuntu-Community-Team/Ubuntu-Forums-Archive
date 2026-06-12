---
title: "Monitoring Vino-server activity"
date: 2009-06-25
forum: Security
---

### Post by LutraMan on 2009-06-25
earlier today, I've noticed that the Vino-Server process was running. I've never used it, so it must be someone else. I also have cacti monitoring my system, and it shows that lately, there was more than 1 user on my system at the same time.

how can I monitor the Vino-Server to show me if somebody is logged in to it in the background?

and more than that, how can I find out how somebody even managed to log in to my computer in the first place???

thanks in advanced

---

### Post by lovinglinux on 2009-06-25
The vino-server is loaded at startup by default. I recommend disabling the Remote Desktop at "System >> Preferences >> Startup Applications (aka Session)".

Remote Desktop is not safe. If you need remote access, use ssh. 

You can check user authentication in the logs. Open "System >> Administration >> Log File Viewer" and browse the auth.log. 

You can also run the following command in the terminal [see footnote] to monitor user authentication:

```
tail -f /var/log/auth.log
```


> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

### Post by LutraMan on 2009-06-26
first of all, thanks for the quick response.

I just looked again in cacti, and saw that since last night at 10:00pm local time there are 2 users logged in.
this is what the auth.log have in that time:

Jun 25 22:00:59 lutra-desktop gnome-screensaver-dialog: pam_smbpass(gnome-screensaver:auth): unrecognized option [missingok]
Jun 25 22:00:59 lutra-desktop gnome-screensaver-dialog: pam_smbpass(gnome-screensaver:auth): Cannot access samba password database, not running as root.
Jun 25 22:01:04 lutra-desktop gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring

one more thing, I can't find the vino-server in startup sessions. and I don't see it in the GNOME-SYSTEM-MONITOR.

How can I see if that login is still logged in? and how can I close his session? last time I just terminated the vino-server process.

---

### Post by lovinglinux on 2009-06-26
> **LutraMan said:**
> first of all, thanks for the quick response.

I just looked again in cacti, and saw that since last night at 10:00pm local time there are 2 users logged in.
this is what the auth.log have in that time:

Jun 25 22:00:59 lutra-desktop gnome-screensaver-dialog: pam_smbpass(gnome-screensaver:auth): unrecognized option [missingok]
Jun 25 22:00:59 lutra-desktop gnome-screensaver-dialog: pam_smbpass(gnome-screensaver:auth): Cannot access samba password database, not running as root.
Jun 25 22:01:04 lutra-desktop gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring

If you are running a terminal, then it will be counted as another user. I'm not sure about the log tho.

> **LutraMan said:**
> 
one more thing, I can't find the vino-server in startup sessions. 

It is the "Remote Desktop" item.

> **LutraMan said:**
> and I don't see it in the GNOME-SYSTEM-MONITOR

Click "View >> All Processes"

> **LutraMan said:**
> How can I see if that login is still logged in?

Run the command *who* in the terminal [see footnote]

> **LutraMan said:**
> and how can I close his session? last time I just terminated the vino-server process.

Run the command below in the terminal [see footnote]

```
killall vino-server
```

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

### Post by Miguel Tavares on 2011-02-20
Hi all,
My approach to the absence of vino-server logs, we can do the following:

1- Stop all vino-server services as root user:
     $killall vino-server

2- Check if they are down:
root@ubuntu:/# nmap localhost|grep 5900|wc -l
0

 3- Go to root home and create a script for the vino-server logs upon startup as follows:

root@ubuntu:/# vi vino-server.sh

#!/bin/sh
killall vino-server
exec /usr/lib/vino/vino-server > $HOME/vino.log 2>&1

4- Permissions to execute:
root@ubuntu:/# chmod 755 vino-server.sh 

5- Run the Script and %bg it:
root@ubuntu:/# ./vino-server.sh &
[1] 16355

6- Check that the file exists:
root@ubuntu:~# ls -la|grep vino
-rw-r--r--  1 root root    422 2011-02-20 07:58 vino.log

7- Check the created log in real time. This will provide us a mean to Root Cause your issue in a  more logical approach since by default vino-server doesnt have any logs.
 
root@ubuntu:~# tail -f vino.log 
20/02/2011 07:58:11 Autoprobing TCP port in (all) network interface
20/02/2011 07:58:11 Listening IPv6://[::]:5900
20/02/2011 07:58:11 Listening IPv4://0.0.0.0:5900
20/02/2011 07:58:11 Autoprobing selected port 5900
20/02/2011 07:58:11 Advertising security type: 'TLS' (1:cool:
20/02/2011 07:58:11 Advertising authentication type: 'No Authentication' (1)
20/02/2011 07:58:11 Advertising security type: 'No Authentication' (1)

Now you'll be able to see who gets in or out :D 

Quote:
 	 	 		 			 				[COLOR=#cc0000]**How to run commands in a Terminal: **[/COLOR]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter*  again to run the command. Please do not run commands without knowing  what they do. If you do not understand what a command does, ask for  explanations. 			 		

Kindest Regards

Miguel Tavares
^_^

---

