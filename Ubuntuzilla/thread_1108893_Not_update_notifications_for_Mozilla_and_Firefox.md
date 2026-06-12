---
title: "Not update notifications for Mozilla and Firefox"
date: 2009-03-28
forum: Ubuntuzilla
---

### Post by MartijnNL on 2009-03-28
Hello,

I'm using Xubuntu Hardy with Ubuntuzilla 4.6.1.

I have enabled the update checker during install, and did get a few notifications at first but no more recently. Nowadays I just notice that Firefox and Thunderbird are update when the normal software update manager says so. Which make ubuntuzilla pretty useless.

I head the same problem on a previous installation of xubuntu and ubuntuzilla. No notifications after a while.

Any solutions for this?

Regards,

Martijn

---

### Post by nanotube on 2009-03-28
Hi
do you see any error messages in /var/log/user.log?

does the notification work if you do a manual update check? run "ubuntuzilla.py -p firefox -a checkforupdategui"

---

### Post by MartijnNL on 2009-03-30
The manual update check seems to run fine, except that I already updated firefox, so there's no new version at the moment.

When I look at the log it shows the ubuntuzilla notifications like

> Mar 24 09:40:00 ... UBUNTUZILLA: Ubuntuzilla is already the latest version...
Mar 24 12:00:01 ... UBUNTUZILLA: Retrieving the version of the latest release of Firefox from the Mozilla website...
Mar 24 12:00:01 ... UBUNTUZILLA: Latest release version of Firefox : 3.0.7
Mar 24 12:00:01 ... UBUNTUZILLA: Currently installed version of Firefox : 3.0.7
Mar 24 12:00:02 ... UBUNTUZILLA: Retrieving the version of the latest release of Thunderbird from the Mozilla website...
Mar 24 12:00:02 ... UBUNTUZILLA: Latest release version of Thunderbird : 2.0.0.21
Mar 24 12:00:02 ... UBUNTUZILLA: Currently installed version of Thunderbird : 2.0.0.21

However I notice that there are no line like these on last Friday, Saturday and on Sunday before 16:00. If the update script runs on cron and not on anacron, maybe I just wasn't online at the right times and the Ubuntu team updates TB and FF pretty fast when a new version comes out.

Do you know how I would go about adding the script to anacron? To make it run on startup if a cron moment has been missed.

Martijn

---

### Post by nanotube on 2009-03-30
Hi

indeed it runs with cron, every 4 hours, with the cron entries added to the user's crontab. (you can see them with "crontab -l")

feel free to add it to anacron using the same commands. "man anacron" for help on anacron...

---

### Post by MartijnNL on 2009-03-30
Ok, I tried adding it to anacron, will have to wait for the next update to see if it works.

Maybe it would be an idea for future versions of ubuntuzilla to add the update checks to cron.daily as well, instead of just to crontab, just like the check for ubuntuzilla updates is added to the daily cron. As cron.daily is executed by anacron by default.

Thanks for your help.

Martijn

---

### Post by nanotube on 2009-03-30
Hi
indeed, it seems like a decent idea. look for it in v 4.6.2 (whenever that happens :) ).
thanks for your feedback!

---

### Post by MartijnNL on 2009-04-23
OK, there was a firefox update and again I didn't get a reminder user.log says (and has been saying this for days):

> Apr 23 10:54:39 ... UBUNTUZILLA: libnotify-Message: Unable to get session bus: '=' character not found or has no value following it
Apr 23 10:54:39 ... UBUNTUZILLA: notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>3.0.8</b>. The new release available is <b>3.0.9</b>. Please refer to these <a href="http://ubuntuzilla.sourceforge.net/#updatefirefox">detailed update instructions</a>.'
Apr 23 10:54:39 ... UBUNTUZILLA: Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Apr 23 10:54:39 ... UBUNTUZILLA: Process returned code 1
Apr 23 10:54:40 ... UBUNTUZILLA: Retrieving the version of the latest release of Firefox from the Mozilla website
Apr 23 10:54:40 ... UBUNTUZILLA: Latest release version of Firefox : 3.0.9
Apr 23 10:54:40 ... UBUNTUZILLA: Currently installed version of Firefox : 3.0.8
Apr 23 10:54:40 ... UBUNTUZILLA: Traceback (most recent call last):
Apr 23 10:54:40 ... UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 1146, in <module>
Apr 23 10:54:40 ... UBUNTUZILLA:     bs.start()
Apr 23 10:54:40 ... UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 209, in start
Apr 23 10:54:40 ... UBUNTUZILLA:     fi.start()
Apr 23 10:54:40 ... UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 246, in start
Apr 23 10:54:40 ... UBUNTUZILLA:     self.checkforupdateGui()
Apr 23 10:54:40 ... UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 634, in checkforupdateGui
Apr 23 10:54:40 ... UBUNTUZILLA:     self.updateActionsGui()
Apr 23 10:54:40 ... UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 667, in updateActionsGui
Apr 23 10:54:40 ... UBUNTUZILLA:     self.util.execSystemCommand(executionstring="notify-send -i '" + iconPath + "' -t 14400000 'Ubuntuzilla: "+self.options.package.capitalize()+" Update Available.' 'A "+self.options.package.capitalize()+" Update is Available. The version you are running is <b>"+self.installedVersion+"</b>. The new release available is <b>"+self.releaseVersion+"</b>. Please refer to these <a href=\""+self.version.url+"#update" + self.options.package + "\">detailed update instructions</a>.'", errormessage="Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.")
Apr 23 10:54:40 ... UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
Apr 23 10:54:40 ... UBUNTUZILLA:     raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
Apr 23 10:54:40 ... UBUNTUZILLA: __main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by nanotube on 2009-04-23
Hi
Thanks for the detailed post

well, it seems there's something unusual going on with your session bus id...

does it work if you open a terminal and try to manually do a "notify-send" ? e.g., try running this command:

```

notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>3.0.8</b>. The new release available is <b>3.0.9</b>. Please refer to these <a href="http://ubuntuzilla.sourceforge.net/#updatefirefox">detailed update instructions</a>.'
```

or even something as simple as
```

notify-send 'bla'

```

and tell me if the message shows up. :)

---

### Post by MartijnNL on 2009-04-23
I tried your first suggestion and that shows as normal. So that does not seem to be the problem.

---

### Post by nanotube on 2009-04-23
hi,
hm, in that case, try running the following (assuming you haven't yet upgraded firefox):

```

ubuntuzilla.py -p firefox -a checkforupdategui -d

```

that will run the ubuntuzilla update check in debug mode, and should show what it is retrieving for the dbus session bus id.

paste the complete output here.

---

### Post by MartijnNL on 2009-04-23
The Output:

> Your commandline options:
{'mirrors': ['releases.mozilla.org/pub/mozilla.org/', 'mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.0.9
Currently installed version of Firefox : 3.0.8
PID used: 5995
'grep: /proc/5995/environ: Permission denied'
'g' 'r' 'e' 'p' ':' ' ' '/' 'p' 'r' 'o' 'c' '/' '5' '9' '9' '5' '/' 'e' 'n' 'v' 'i' 'r' 'o' 'n' ':' ' ' 'P' 'e' 'r' 'm' 'i' 's' 's' 'i' 'o' 'n' ' ' 'd' 'e' 'n' 'i' 'e' 'd'
'grep: /proc/5995/environ: Permission denied'
libnotify-Message: Unable to get session bus: '=' character not found or has no value following it
notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>3.0.8</b>. The new release available is <b>3.0.9</b>. Please refer to these <a href="http://ubuntuzilla.sourceforge.net/#updatefirefox">detailed update instructions</a>.'
Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Process returned code 1
'g' 'r' 'e' 'p' ':' ' ' '/' 'p' 'r' 'o' 'c' '/' '5' '9' '9' '5' '/' 'e' 'n' 'v' 'i' 'r' 'o' 'n' ':' ' ' 'P' 'e' 'r' 'm' 'i' 's' 's' 'i' 'o' 'n' ' ' 'd' 'e' 'n' 'i' 'e' 'd'
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1146, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 246, in start
    self.checkforupdateGui()
  File "/usr/local/bin/ubuntuzilla.py", line 634, in checkforupdateGui
    self.updateActionsGui()
  File "/usr/local/bin/ubuntuzilla.py", line 667, in updateActionsGui
    self.util.execSystemCommand(executionstring="notify-send -i '" + iconPath + "' -t 14400000 'Ubuntuzilla: "+self.options.package.capitalize()+" Update Available.' 'A "+self.options.package.capitalize()+" Update is Available. The version you are running is <b>"+self.installedVersion+"</b>. The new release available is <b>"+self.releaseVersion+"</b>. Please refer to these <a href=\""+self.version.url+"#update" + self.options.package + "\">detailed update instructions</a>.'", errormessage="Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.")
  File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)


I thought it might be usefull not to update yet. So didn't.

---

### Post by nanotube on 2009-04-23
Hi
indeed it is useful. we'll get to the bottom of this.

looks like we're getting somewhere. it appears that it is choosing some process which you have no permission to access, even though it is coded to look at only the list of processes that are owned by your username.

could you run that again, note the PID that it is using, and look in your system monitor (or use 'ps ax' or whatever method you prefer) and see what this process is, and whether it is owned by your user (or to be precise, by the user that is running ubuntuzilla).

---

### Post by MartijnNL on 2009-04-24
The Process is:

Process Name:
ssh-agent

User is my username (so same as running the command)

Command Line:
 /usr/bin/ssh-agent /usr/bin/seahorse-agent --execute /usr/bin/keytouchd-launch x-session-manager

If this is called everytime the Ubuntuzilla script runs it might also explain why I have so many processes running called seahorse-agent. This number just keeps on growing until I manually End the processes.

---

### Post by nanotube on 2009-04-24
Hi

ubuntuzilla is not running it. ubuntuzilla merely looks at all the processes that already are running under your username, picks one, and queries its environment for the dbus session information. it just happened to pick that one - next time it might be another.

that said, I don't know why access to that process's environment is denied, even though it is owned by your user.

i guess i'll just have to put in an extra test to skip over any processes where access is not allowed. give me a bit, and i'll post an updated ubuntuzilla version for you to try. :)

---

### Post by nanotube on 2009-04-24
Hi
OK, attaching a .deb of a [hopefully] fixed ubuntuzilla.
give it a shot please :)

---

### Post by MartijnNL on 2009-04-25
I'll try it tomorrow. Will be away a most of today.

Did you include my earlier suggestion about cron.daily as well?

> Maybe it would be an idea for future versions of ubuntuzilla to add the update checks to cron.daily as well, instead of just to crontab, just like the check for ubuntuzilla updates is added to the daily cron. As cron.daily is executed by anacron by default.

---

### Post by nanotube on 2009-04-25
Hi
no i haven't gotten to that.
i thought about the implementation details, and realized it won't be that simple.

all the scripts in cron.daily run as root. the ubuntuzilla updater task, however, needs to find your /user/ dbus session, and to do that it gets a list of all processes owned by the user who is running the ubuntuzilla process, picks on, scans its environment for the DBUS_... variable.

if i simply place an updater task into /etc/cron.daily/, it will run as root, and will attempt to get root's DBUS session info (which, in most cases, would simply not exist as root doesn't normally run an X session), and so would basically be useless for you as a user.

it /is/ possible to set up anacron to run a user's crontab job, but that requires creating an extra user anacrontab (not a big deal), and also creating an extra system group, changing ownership and permissions of /var/spool/anacron (by default users don't have access to that dir, which anacron must have). that's a bit too much system changes to be doing "automatically", it seems to me. 

(see [http://www.it.uc3m.es/marcos/doc/miniHOWTOs/miniHOWTO-Use_anacron_as_non-root_user.html](http://www.it.uc3m.es/marcos/doc/miniHOWTOs/miniHOWTO-Use_anacron_as_non-root_user.html) for details on changes required to enable anacron for user crontab)

what do you think?

---

### Post by MartijnNL on 2009-04-26
> **nanotube said:**
> Hi
OK, attaching a .deb of a [hopefully] fixed ubuntuzilla.
give it a shot please :)

Nope :(

After running the manual command with debug info:
> Your commandline options:
{'mirrors': ['releases.mozilla.org/pub/mozilla.org/', 'mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.0.9
Currently installed version of Firefox : 3.0.8
grep -z DBUS_SESSION_BUS_ADDRESS /proc/6383/environ
Previous command has failed to complete successfully. Exiting.
Process returned code 1
grep -z DBUS_SESSION_BUS_ADDRESS /proc/6439/environ
Previous command has failed to complete successfully. Exiting.
Process returned code 2
grep -z DBUS_SESSION_BUS_ADDRESS /proc/6441/environ
Previous command has failed to complete successfully. Exiting.
Process returned code 1

.... and so on ....

grep -z DBUS_SESSION_BUS_ADDRESS /proc/6920/environ
Previous command has failed to complete successfully. Exiting.
Process returned code 1
grep -z DBUS_SESSION_BUS_ADDRESS /proc/6946/environ
Previous command has failed to complete successfully. Exiting.
Process returned code 2
ERROR: could not get DBUS_SESSION_BUS_ADDRESS, notification cannot be shown.


Hmm that seems very complicated indeed. I guess the manual add to anacron I did a while ago is an easier solution. Asuming that works.

---

### Post by telmac on 2009-04-26
you need a special program to upgrade your web browser, you are better offf just getting it with the new os, cause it comes with the new one.

---

### Post by MartijnNL on 2009-04-26
> **telmac said:**
> you need a special program to upgrade your web browser, you are better offf just getting it with the new os, cause it comes with the new one.

There are 2 reasons I use Ubuntuzilla:
[LIST=1]
[*]I get security updates quicker then when waiting for the repositories to be updated.
[*]I prefer to use a LTS version of Xubuntu as I need the computer for my work and don't want to have to bother with the inevitable bugs you tend to get in a brand new xubuntu version. For example: I upgraded to Hardy in November or December and got occasional system crashes for 1 or 2 months after that, stopped after a later kernel update. What was more then 6 months after Hardy was released.
[/LIST]

And if you don't like a certain program or consider it useless, why do you bother posting in a support/bug related thread in a forum dedicated to that project?

---

### Post by MartijnNL on 2009-04-26
Oh, at 12:00 I got a normal update available message. So it does seem to be working.

A similar list of error messages as above can be found in user.log though.

---

### Post by nanotube on 2009-04-26
Hmm, there's definitely something a unusual going on with your process permissions, but I don't really know what it is.

What I did is simply have it try processes from the list until one works.

I'm glad it finally worked, though. :)

Please see if it keeps showing the update notification, and if it does, i suppose we can consider this problem "solved"...

---

### Post by MartijnNL on 2009-04-26
Got another message at 16:00, so going to update now.

I'll keep looking at this for further updates in the future. If I run into any problems again, I'll let you know.

Hmm, no idea about the permissions either. I don't run into any other practical problems during day to day operations. But I'm no expert.

Thanks anyway for helping me out!

Martijn

---

### Post by nanotube on 2009-04-26
Good to hear. :)

I'll make an official release shortly, then.

let me know if you run into any other problems in the future, i'm always happy to help. :)

---

### Post by MartijnNL on 2009-06-13
There we go again. No notification and and the update manager produces a new version.

Manual command produces a big list of items like:

> grep -z DBUS_SESSION_BUS_ADDRESS /proc/8291/environ
Previous command has failed to complete successfully. Exiting.
Process returned code 1
grep -z DBUS_SESSION_BUS_ADDRESS /proc/8317/environ
Previous command has failed to complete successfully. Exiting.
Process returned code 2


Followed by:

> ERROR: could not get DBUS_SESSION_BUS_ADDRESS, notification cannot be shown.

Sounds familiar?

I'm off for a week from Tuesday. So can't reply during that period.

Regards,

Martijn

---

### Post by MartijnNL on 2009-06-13
I got a notification in the end, at 20:00 (CET) today. So it seems the notification is working, it just has a very hard time finding the DBUS Session.

Going to update now.

---

### Post by nanotube on 2009-06-17
ok, thanks for the note. :)

getting the dbus session is never going to be an 'exact science' until they make some changes to the underlying architecture...

---

