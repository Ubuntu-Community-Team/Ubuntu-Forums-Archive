---
title: "Fixing hosting provider's 10.04 preload, put back system stats on ssh login banner"
date: 2012-06-14
forum: Server Platforms
---

### Post by mdlueck on 2012-06-14
I am fixing up a hosting provider's Ubuntu 10.04 preload. Hosting provider decided to put on samba for a webserver, ouch!

The login screen is very plain compared to stock Ubuntu Server 10.04.

I discovered package update-motd missing, so added that back. That was not enough to get back the usual host stats and also how many updates are needed.

All I receive when I login to this new hosted server is:

```
Ubuntu 10.04.4 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/
Last login: Thu Jun 14 21:57:17 2012 from somehost...
```

I am used to seeing:

```
Ubuntu 10.04.4 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Thu Jun 14 23:09:53 EDT 2012

  System load:    0.33              Processes:           130
  Usage of /home: 59.8% of 1.85GB   Users logged in:     0
  Memory usage:   6%                IP address for eth0: 10.10.10.10
  Swap usage:     0%

  Graph this data and manage this system at https://landscape.canonical.com/

0 packages can be updated.
0 updates are security updates.

Last login: Thu Jun 14 22:56:34 2012 from somehost...
```

Any suggestions which package(s) might be responsible for the rest of the usual Ubuntu ssh welcome screen? TIA!

---

### Post by mdlueck on 2012-06-29
Bump... anyone with a suggestion?

---

### Post by CharlesA on 2012-06-29
Check what package landscape-sysinfo is in. It's probably landscape-common.

Also the update check thing is part of update-notifier-common

---

### Post by mdlueck on 2012-06-29
> **CharlesA said:**
> Check what package landscape-sysinfo is in. It's probably landscape-common.

Can't be, that is not a package on my server installations, which I grabbed that screen scrape from.


> **CharlesA said:**
> Also the update check thing is part of update-notifier-common

Hurray, adding that package (which was on a stock install of server 10.04) yielded:

```
Ubuntu 10.04.4 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Last login: Fri Jun 29 22:43:33 2012 from
```

Making progress restoring Ubuntu! Thanks! :-)

---

### Post by CharlesA on 2012-06-29
Try just running landscape-sysinfo and it should tell you what package it is in, if it isn't installed.

---

### Post by mdlueck on 2012-06-29
> **CharlesA said:**
> landscape-sysinfo and it should tell you what package it is in, if it isn't installed.

Aaaahhh, I asked packaged.ubuntu.org where that is:
landscape-common

And that was on our stock installations. So off to add that package, and if needed the update-motd package perhaps since that is part of a stock installation and not the VPS image. Anyway, thanks very much! :-)

---

### Post by mdlueck on 2012-06-29
> **mdlueck said:**
> Aaaahhh, I asked packaged.ubuntu.org where that is:
landscape-common

Those two packages, and the dependencies that the landscape-common pulled along were all that were needed. Logged in and got the system stats right away. Thank you so much! :-)

---

### Post by cryptotheslow on 2012-06-29
OK this turned into a bit of an essay as it is something I always meant to work out so made notes along the way.

That message comes from /etc/motd. Looking at that file on my standard 10.04 server install it is populated with:

```

Linux ubuserver 2.6.32-41-server #90-Ubuntu SMP Tue May 22 12:41:40 UTC 2012 x86_64 GNU/Linux
Ubuntu 10.04.4 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Sat Jun 30 03:40:01 BST 2012

  System load:  0.08                Processes:           83
  Usage of /:   73.5% of 452.84GB   Users logged in:     0
  Memory usage: 7%                  IP address for eth0: 192.168.1.67
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

5 packages can be updated.
5 updates are security updates.

```

So clearly something is updating it.

A little digging suggests this used to be updated by the update-motd package but that seems to have been superceded by pam_motd in libpam-modules.

As far as I can tell that derives its login message from the /etc/pam.d/login file. Relevant sections in **bold** I think :)

```

crypto@ubuserver:/etc/pam.d$ cat login
#
# The PAM configuration file for the Shadow `login' service
#

# Enforce a minimal delay in case of failure (in microseconds).
# (Replaces the `FAIL_DELAY' setting from login.defs)
# Note that other modules may require another minimal delay. (for example,
# to disable any delay, you should add the nodelay option to pam_unix)
auth       optional   pam_faildelay.so  delay=3000000

# Outputs an issue file prior to each login prompt (Replaces the
# ISSUE_FILE option from login.defs). Uncomment for use
# auth       required   pam_issue.so issue=/etc/issue

# Disallows root logins except on tty's listed in /etc/securetty
# (Replaces the `CONSOLE' setting from login.defs)
# Note that it is included as a "required" module. root will be
# prompted for a password on insecure ttys.
# If you change it to a "requisite" module, make sure this does not leak
# user name information.
auth       required  pam_securetty.so

# Disallows other than root logins when /etc/nologin exists
# (Replaces the `NOLOGINS_FILE' option from login.defs)
auth       requisite  pam_nologin.so

# SELinux needs to be the first session rule. This ensures that any 
# lingering context has been cleared. Without out this it is possible 
# that a module could execute code in the wrong domain.
# When the module is present, "required" would be sufficient (When SELinux
# is disabled, this returns success.)
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close

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

[B]# Prints the last login info upon succesful login
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
session    optional   pam_mail.so standard[/B]

# Standard Un*x account and session
@include common-account
@include common-session
@include common-password

# SELinux needs to intervene at login time to ensure that the process
# starts in the proper default security context. Only sessions which are
# intended to run in the user's context should be run after this.
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
# When the module is present, "required" would be sufficient (When SELinux
# is disabled, this returns success.)

```


**But** that doesn't make sense as it appears to print the last login info before the MOTD - whereas on a standard login it is displayed the other way around.

So then we end up here for 10.04 at least:
[https://help.ubuntu.com/10.04/serverguide/pam_motd.html](https://help.ubuntu.com/10.04/serverguide/pam_motd.html)

Which states:
[I]"update-notifier-common: is used to automatically update the MOTD via pam_motd module.

pam_motd executes the scripts in /etc/update-motd.d in order based on the number prepended to the script. The output of the scripts is written to /var/run/motd, keeping the numerical order, then concatenated with /etc/motd.tail."[/I]

So let's see what is in /etc/update-motd.d/........

```
crypto@ubuserver:~$ cd /etc/update-motd.d/
crypto@ubuserver:/etc/update-motd.d$ ls
00-header     20-cpu-checker        90-updates-available  98-reboot-required
10-help-text  50-landscape-sysinfo  91-release-upgrade    99-footer
```
So now you need to know what each of those files contains:
```

crypto@ubuserver:/etc/update-motd.d$ cat ./00-header
#!/bin/sh

uname -a
printf "%s\n" "$(lsb_release -s -d)"

``````

crypto@ubuserver:/etc/update-motd.d$ cat ./10-help-text
#!/bin/sh

if uname -r | grep -qs "\-server"; then
    echo
    echo "Welcome to the Ubuntu Server!"
    echo " * Documentation:  http://www.ubuntu.com/server/doc"
else
    echo
    echo "Welcome to Ubuntu!"
    echo " * Documentation:  https://help.ubuntu.com/"
fi

``````

crypto@ubuserver:/etc/update-motd.d$ cat ./20-cpu-checker
#!/bin/sh

exec /usr/lib/update-notifier/update-motd-cpu-checker

``````

crypto@ubuserver:/etc/update-motd.d$ cat ./50-landscape-sysinfo
#!/bin/sh
cores=$(grep -c ^processor /proc/cpuinfo 2>/dev/null)
[ "$cores" -eq "0" ] && cores=1
threshold="${cores:-1}.0"
if [ $(echo "`cut -f1 -d ' ' /proc/loadavg` < $threshold" | bc) -eq 1 ]; then
    echo
    echo -n "  System information as of "
    /bin/date
    echo
    /usr/bin/landscape-sysinfo
else
    echo
    echo " System information disabled due to load higher than $threshold"
fi

``````

crypto@ubuserver:/etc/update-motd.d$ cat ./90-updates-available
#!/bin/sh

exec /usr/lib/update-notifier/update-motd-updates-available

``````

crypto@ubuserver:/etc/update-motd.d$ cat ./91-release-upgrade
#!/bin/sh

exec /usr/lib/update-manager/release-upgrade-motd

``````

crypto@ubuserver:/etc/update-motd.d$ cat ./98-reboot-required
#!/bin/sh

exec /usr/lib/update-notifier/update-motd-reboot-required

``````

crypto@ubuserver:/etc/update-motd.d$ cat ./99-footer
#!/bin/sh

# motd.tail is reserved for the admin to append static
# trailing information to a dynamically generated
# /etc/motd.
#
# To add dynamic information, add a numbered
# script to /etc/update-motd.d/

[ -f /etc/motd.tail ] && cat /etc/motd.tail || true

```
Now all the above is assuming that your hosting provider hasn't done some custom funkery with the login authentication process - which would not be surprising if they are centrally managing servers and automating login creation etc.

I suspect you have a complex path ahead - perhaps dropping the hosting provider a quick question on this before spending hours on it would be a wise first step.

Any way - hope some of that helps - I certainly learnt something :D

---

### Post by cryptotheslow on 2012-06-29
AARGH Ninja'd by CharlesA after all that :rolleyes:

---

### Post by mdlueck on 2012-06-29
LOL cryptotheslow... I had just noticed that getting the banner stats working had killed the package update check. So yes I think a bit more digging and documenting is still needed.

The hosting provider image is configured with only a root account. So I needed to do various undoings to get sudo working, re-disable root, etc... All of that the same as I needed to do for their 8.04 preload.

Only 8.04 never had this banner server stats nor available update notification. So that was the new twist for 10.04.

No central account management or the like. I had full root access, changed the pwd, we are on our own.

Then I ran the debsums package and fixed most tweaks they had done to the image. All I skipped there was fixing the removed tty symlinks as I do not need any ttys on a vps.

They even had samba packages loaded in their preload!!!! aaakkk!!! PURGE!!!

---

### Post by cryptotheslow on 2012-06-29
:rolleyes:

Hosting providers do some truely odd things with their preloads. Or maybe they just get sick and tired of answering questions like "Why is root disabled? I pay for this server I demandz root!" :D As for samba - umm really - why not roll in a DE and vino just to be sure :D

Anyway, glad you got it more or less sorted. ):P

---

### Post by CharlesA on 2012-06-29
Wow. Do you have the option to load your own OS on the VPS? I'd do that. Heh.

---

### Post by mdlueck on 2012-06-29
Here are found some more details...
[https://wiki.ubuntu.com/UpdateMotd](https://wiki.ubuntu.com/UpdateMotd)

---

### Post by mdlueck on 2012-06-29
> **CharlesA said:**
> Wow. Do you have the option to load your own OS on the VPS? I'd do that. Heh.

Nope, not for $30 per month. Have to accept one of their available preloads.

---

### Post by cryptotheslow on 2012-06-30
> **mdlueck said:**
> Here are found some more details...
[https://wiki.ubuntu.com/UpdateMotd](https://wiki.ubuntu.com/UpdateMotd)

Run away - it appears out of date from 2008 and refers to update-motd.

**Bolded** bit of interest:

```

crypto@ubuserver:/etc/update-motd.d$ sudo apt-cache show update-motd
Package: update-motd
Priority: optional
Section: admin
Installed-Size: 56
Maintainer: Dustin Kirkland <kirkland@ubuntu.com>
Architecture: all
Version: 3.5-0ubuntu1
Depends: libpam-modules (>= 1.0.1-9ubuntu3)
Filename: pool/main/u/update-motd/update-motd_3.5-0ubuntu1_all.deb
Size: 5910
MD5sum: b9d88387900ed306fbb0cb28d9bf0941
SHA1: 5fccdf16abd306728a45b8650f098f44cdd9cae1
SHA256: a1e1442797bf4dcdcaad183b267afcb9667a2642391e1a03c60350f3627a0d98
Description: superceded by pam_motd in libpam-modules
 .
 This package installs a script in /etc/profile.d that dynamically generates
 a message-of-the-day by running scripts installed in /etc/update-motd.d,
 in lexical order.
 .
 Other packages, or system administrators should symlink scripts into
 /etc/update-motd.d, pre-pending a 2-digit number to handle ordering.
 .
 [b]The functionality formerly provided by this package is now integrated into
 pam_motd, in libpam-modules.[/b]

Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: uec

```

Seems to suggest it is superceded.

Maybe I should head back to absolute beginners where I rightly belong and leave you sysadmin types to make sense to each other :D

---

### Post by mdlueck on 2012-06-30
> **mdlueck said:**
> LOL cryptotheslow... I had just noticed that getting the banner stats working had killed the package update check. So yes I think a bit more digging and documenting is still needed.


I had forgotten this logic:

```
# check time when we did the last udpate check
stamp="/var/lib/update-notifier/updates-available"
if [ -e "$stamp" ]; then
    stampt=$(stat -c %Y $stamp)
else
    stampt=0
fi
```

So since it had been run it decded at subsequent logins it did not need to provide an update. Clearing the flag and logging in fully populated the initial login screen. fffeeewww... case closed I call it. Thanks! ):P

---

### Post by mdlueck on 2012-06-30
> **cryptotheslow said:**
> Maybe I should head back to absolute beginners where I rightly belong and leave you sysadmin types to make sense to each other :D

*"May it never be!" the words of the Apostle Paul according to Dan Bowman's Bible.* I am please you were in this group this evening... when I remembered I had not gotten any response to my OP. ;)

---

### Post by cryptotheslow on 2012-06-30
Glad to have helped if only to provide a LOL along the way by furtling down rabbit holes instead of suggesting "install package ~bleh~". :D Still I learnt something so all is good.

Thankfully no-one relies on me to look after their systems, I just poke around on my own.

---

### Post by mdlueck on 2012-06-30
> **cryptotheslow said:**
> Thankfully no-one relies on me to look after their systems, I just poke around on my own.

The first time I experienced a VPS rather than a true SERVER SERVER, Oy! About maybe a month after production cut-over to it, my security scan went NUTS and told me about every file on the box failed!!! I thought we had been hacked, so I powered down the server AT ONCE!!!!

Turns out, when the hosting provider updates the shared kernel and does an IPL, doing so changes the Inode number of MANY files. I got the understanding that unlike desktop VM products, such server based VM (VPS) technologies leave the VM files loose and floating around on the host OS disk. It is not a single file virtual hard drive image file. Thus when I dut into what the security scan was saying, turned out THAT is what caused the major scare.

Now I have a script which logs the kernel version at each IPL, and simply check that when I receive an out of control security scan alert. All times it has been at a kernel upgrade / IPL point in time. ffffeeewwww!!!! ):P

---

