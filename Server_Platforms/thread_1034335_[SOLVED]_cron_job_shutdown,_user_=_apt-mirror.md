---
title: "[SOLVED] cron job shutdown, user = apt-mirror?"
date: 2009-01-08
forum: Server Platforms
---

### Post by soldersplash on 2009-01-08
Hello all,
I use cron to run apt-mirror over night and avoid upsetting my ISP. I can set my box to wake up on RTC in time for the cron job but I am having trouble getting it to shut itself down again after. I tried to use:

<File = /etc/cron.d/apt-mirror>
#
# Regular cron job for the apt-mirror package.
#
# Timed for 'Virgins' Traffic Management Policy. (sic.)
# Start mirroring after midnight...
5 0 * * * apt-mirror /etc/cron.d/apt-mirror-script start ; /etc/cron.d/apt-mirror-script clean ; shutdown -h -P now > /home/daniel/auto-shutdown.log
#00 12 * * *    apt-mirror      /etc/cron.d/apt-mirror-script start ; /etc/cron.d/apt-mirror-script clean
# Stop mirroring before 4pm....
55 15 * * *     apt-mirror      /etc/cron.d/apt-mirror-script stop ; /etc/cron.d/apt-mirror-script clean
<EOF>

The two apt-mirror scripts get run OK at 5mins past midnight but the box doesn't shut down.
The midday run is commented out on purpose at the mo'.

The cron job runs as user 'apt-mirror' so I tried the 'shutdown' command at the command line after switching user to 'apt-mirror'. I get a permissions error. You need root permission to run 'shutdown'.

Does anyone know how to give the user 'apt-mirror' root permissions for just the 'shutdown' command?

Thanks,
Soldersplash.

---

### Post by soldersplash on 2009-01-09
OK, I figured it out anyhow.
The shutdown command needs root permission so use sudo, see cron job below:-

<File = /etc/cron.d/apt-mirror>
#
# Regular cron job for the apt-mirror package.
#
# Timed for 'Virgins' Traffic Management Policy. (sic.)
# Start mirroring after midnight...
5 0 * * * apt-mirror /etc/cron.d/apt-mirror-script start ; /etc/cron.d/apt-mirror-script clean ; sudo shutdown -h -P now
#00 12 * * * apt-mirror /etc/cron.d/apt-mirror-script start ; /etc/cron.d/apt-mirror-script clean
# Stop mirroring before 4pm....
55 15 * * * apt-mirror /etc/cron.d/apt-mirror-script stop ; /etc/cron.d/apt-mirror-script clean
<EOF>

And the user "apt-mirror needed adding to the /etc/sudoers" file, one line for each command it needs permission for, the commands are aliased also, not sure if thats required but the example I found used this method:-

<File = /etc/sudoers>
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias SHUTDOWN = /sbin/shutdown
Cmnd_Alias SHELL = /bin/sh
# User privilege specification
root	ALL=(ALL) ALL
apt-mirror	ALL= NOPASSWD: SHUTDOWN
apt-mirror	ALL= NOPASSWD: SHELL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
<EOF>

My media server now gets up in the night, sync's with the mirror then goes back to sleep until breakfast! Do I get 'greenie' points?

Cheers,
Soldersplash.

---

