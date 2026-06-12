---
title: "update manager/notifier"
date: 2005-10-20
forum: Repositories &amp; Backports
---

### Post by teaker1s on 2005-10-20
says there are updates and click install nothing happens goes grey and then back to normal
refresh button works and it downloads repositories again.

have reinstalled notifier and update manager and still i can see and select updates but they don't install

any idea's thanks

ps I have kubuntu splash screen with choice of kde or gnome login and both have same issue

seems it's a bug searching with synaptic it states the versions are the same as updates!!!

---

### Post by xristos on 2005-10-20
Maybe your user was not added to the sudoers file .
Try visudo and and him if he is not there

---

### Post by teaker1s on 2005-10-21
hi not sure what to do!!
 as login as admin and in admin group and it doesn't allow 
update manager to install
my normal user I have allowed to execute system administration tasks in user control panel and sudo command works and synaptic works to install anything but update notifier/manager just doesn't install updates


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL


thanks

---

### Post by teaker1s on 2005-10-28
for some reason my ubuntu with gnome and kde now doesn't work if I have it set to prefer breezy if set to highest as prefered it works in synaptic 

bizare but thank you for the suggestions

---

### Post by makhand on 2005-10-29
I have the same problem. Update Manager doesnt do anything. It looks like its going to, but doesnt. I can get all my updates through Synaptic just fine though. Its just a bit annoying. I dont have kubuntu. Thanks

---

### Post by towsonu2003 on 2005-10-29
[QUOTE=makhand]I have the same problem. Update Manager doesnt do anything. It looks like its going to, but doesnt. I can get all my updates through Synaptic just fine though. Its just a bit annoying. I dont have kubuntu. Thanks[/QUOTE]

the other day i noticed that apt was running (to be updated) as part of a cron I did not set up. I believe it is in the same place as the scheduled updatedb (which stalls my computer almost always). after running, the notifier (for the first time without running synaptic) popped out for updates. Unfortunately i don't kow how to tweak this cron... (not sudo crontab -e)

I don't now what criteria was given to apt to run in the background, but it seems problematic... well, windows xp's criteraia is problematic as well. i use the mailing list as a way to be sure that everything is uptodate and that update-notifier is not corrupted.

i have ubuntu.

---

