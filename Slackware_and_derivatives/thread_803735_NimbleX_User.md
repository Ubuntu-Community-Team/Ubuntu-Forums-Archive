---
title: "NimbleX User?"
date: 2008-05-22
forum: Slackware and derivatives
---

### Post by NewDisciple on 2008-05-22
I have NimbleX which is based upon Slackware, installed on a 1GB USB flash drive.  This distribution is a lot of fun to use and extremely fast.  My one major concern is that it runs in root and apparently has no provision for a user.  When it starts up you are not asked for a name or password.
  It is my belief that there must be some kind of work around or script that can fix this problem.  Although I can get around in Linux pretty well, I just don't have the knowledge or skill for this task.
  Any thoughts on this?

---

### Post by garyedwardjohnston on 2008-05-22
Try disabling USB 2.0 (High Speed) in BIOS.

---

### Post by NewDisciple on 2008-05-22
I fail to see how that answers my question.  I want to be able to use Nimblex whenever & where ever.  In order to do this I need a secure work around as I also want to access the web.

---

### Post by NewDisciple on 2008-05-22
Found in the Nimblex Forums (Duh!)

Boot with "changes=/dev/hdaX" (where hdaX is a linux formatted partition on your harddisk) to command line, login as root and use

Code:
adduser


follow the menu and add a new user. Then copy all configuration files from /root to /home/new_user (where new_user is the name of your created user) in this way:

Code:
cd /root
cp -R * /home/new_user/
cp -R .??* /home/new_user/
chown -R new_user /home/new_user/


Then logout as root and login as new_user, cancel kmix and krandrtray question and start kmix and krandrtray again. Start kcontrol and change the login manager to autologin not root but your new_user.

Then make the changes permanent with

Code:
su -
toor
dir2lzm /mnt/live/memory/changes nimblexuser.lzm


Insert this module into your booting system (new ISO or copy it to harddisk or USB drive if you boot from harddisk or USB drive) and have it available at every reboot.

---

