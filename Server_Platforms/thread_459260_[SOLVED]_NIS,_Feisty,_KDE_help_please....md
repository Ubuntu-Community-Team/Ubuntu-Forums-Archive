---
title: "[SOLVED] NIS, Feisty, KDE help please..."
date: 2007-05-30
forum: Server Platforms
---

### Post by knichel on 2007-05-30
I am a teacher and fairly new to ubuntu (linux in general).  I have been using NIS for student logins just fine until recently.  I have been building the "perfect student compuer" and preparing to use it to image all the rest.  

After an update on Tuesday May 29 around 8:30 am, NIS logins were fine.  Now they are not.  None of my server created accounts can log in.  I see all the accounts from the server in the list on the login screen (kubuntu-feisty-list theme), but none of them can log in.  All of these accounts can log in on the other machines (6.10) but not the new one (7.04).

There was also a bug with kde-guidance.  The +:::::: required in /etc/passwd was causing userconfig to fail.  I have reported this to the developers.

If there is a better (simple) way for me to handle the user log in's other than NIS, please let me know.

Any help is appreciated.

--
MIKE

---

### Post by craigp84 on 2007-05-31
Hi knichel,

I'm not familiar with the bug, however, assuming it's a real bug there's possibly a couple of work arounds until it's fixed:

1. Try a theme without the user list, does that make any difference?
2. Switch from KDM to GDM (or vice versa if you're already using GDM)

NIS should normally work ok. There are alternatives, and if you've got a small userbase (less than 500 users) then having a central /etc/passwd, /etc/group, /etc/shadow and /etc/gshadow which you push out using rdist or rsync every X hours or so via cron (stagger each machine, don't do them all at once) is a simple, workable solution.

It shouldn't take you more than 2 hours to migrate from your current situation to this, including reading time etc. it's fairly trivial.

The other burning question is - is there a real need to go 7.04? If this one box is your acceptance testing (which it sounds like - good approach) then test failed :)

Hope this helps,

-c

---

### Post by knichel on 2007-05-31
Thanks for the input.  I do have a small userbase.  I have less than 20 students/workstations (currently 6 but going up next year).  Normally I would agree with you that the test failed, however, everything was working fine until recently.  I had the NIS logins working just fine last week.  The only thing that I can thing of that I installed were a few updates via adept updater (not sure what it is called -  the auto updater notifier) and the list theme.  I have disabled the theme and tried the default and same problem.  

Funny thing is that part of NIS is working.  The workstation retrieves the list of available users from the server.  The passwords just seem to fail.  

Do you know where I might get more support with NIS?

Thanks again,
Mike

---

### Post by craigp84 on 2007-05-31
If the bug that's broken it is in KDM/GDM you need help with those, not NIS.

Quick test - can you login at the command line?

If yes, chase a fix on the bug.

If no, can you "ypcat passwd" and see the entries you'd expect?

-c

---

### Post by knichel on 2007-05-31
Thanks again.  I can not login via console.  However, I can ypcat passwd and see what I expect to see.

Mike

---

### Post by craigp84 on 2007-05-31
Oh in that case you could be looking at a pam or nsswitch funny. Is your /etc/nsswitch.conf ok?

What about /etc/pam.d/login and anything else relevant in there?

-c

---

### Post by knichel on 2007-06-01
I don't see anything unusual...

Here is my pam.d/login file...
```
#
# The PAM configuration file for the Shadow `login' service
#

# Outputs an issue file prior to each login prompt (Replaces the
# ISSUE_FILE option from login.defs). Uncomment for use
# auth       required   pam_issue.so issue=/etc/issue

# Disallows root logins except on tty's listed in /etc/securetty
# (Replaces the `CONSOLE' setting from login.defs)
auth       requisite  pam_securetty.so

# Disallows other than root logins when /etc/nologin exists
# (Replaces the `NOLOGINS_FILE' option from login.defs)
auth       requisite  pam_nologin.so

# This module parses environment configuration file(s)
# and also allows you to use an extended config
# file /etc/security/pam_env.conf.
# 
# parsing /etc/environment needs "readenv=1"
session       required   pam_env.so readenv=1
# locale variables are also kept into /etc/default/locale in etch
# reading this file *in addition to /etc/environment* does not hurt
session       required   pam_env.so readenv=1 envfile=/etc/default/locale

# Standard Un*x authentication.
@include common-auth

# This allows certain extra groups to be granted to a user
# based on things like time of day, tty, service, and user.
# Please edit /etc/security/group.conf to fit your needs
# (Replaces the `CONSOLE_GROUPS' option in login.defs)
auth       optional   pam_group.so

# Uncomment and edit /etc/security/time.conf if you need to set
# time restrainst on logins.
# (Replaces the `PORTTIME_CHECKS_ENAB' option from login.defs
# as well as /etc/porttime)
# account    requisite  pam_time.so

# Uncomment and edit /etc/security/access.conf if you need to
# set access limits.
# (Replaces /etc/login.access file)
# account  required       pam_access.so

# Sets up user limits according to /etc/security/limits.conf
# (Replaces the use of /etc/limits in old login)
session    required   pam_limits.so

# Prints the last login info upon succesful login
# (Replaces the `LASTLOG_ENAB' option from login.defs)
session    optional   pam_lastlog.so

# Prints the motd upon succesful login
# (Replaces the `MOTD_FILE' option in login.defs)
session    optional   pam_motd.so

# Prints the status of the user's mailbox upon succesful login
# (Replaces the `MAIL_CHECK_ENAB' option from login.defs). 
#
# This also defines the MAIL environment variable
# However, userdel also needs MAIL_DIR and MAIL_FILE variables
# in /etc/login.defs to make sure that removing a user 
# also removes the user's mail spool file.
# See comments in /etc/login.defs
session    optional   pam_mail.so standard

# SELinux needs to intervene at login time to ensure that the process
# starts in the proper default security context.
# Uncomment the following line to enable SELinux
# session required pam_selinux.so multiple

# Standard Un*x account and session
@include common-account
@include common-session
@include common-password
```

and...

Here is my nsswitch.conf...
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

---

