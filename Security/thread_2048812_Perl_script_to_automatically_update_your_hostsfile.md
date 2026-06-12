---
title: "Perl script to automatically update your hostsfile"
date: 2012-08-27
forum: Security
---

### Post by Magnetizer on 2012-08-27
Hello Ubuntu lovers,

Some time ago, I wrote a Perl script to keep my hostsfile up to date in order to block nasty things on the internet. I think it works great and I would like to share it with you, so I attached the script to this post.

Here is what the script does:

This script downloads several hostsfile/blacklists. If any of those
files has changed since the last run the script merges the files,
unduplicates them, sorts them, optimizes them and installs a
new hostsfile on the system. It then reports the changes it made
to the hostsfile by e-mail.

There is also the possibility to add hosts to your own white- or
blacklist in order to overrule the downloaded hostsfiles.

The script comes with a README file to guide you during the install and setup process and it comes under the General Public License (GPL). So the script is free as in speech (and free as in beer, too ;-) ).

I hope it will be useful to some security/privacy aware people. If you have any questions, suggestions or corrections feel free to contact me.

Have fun and keep it safe!

PS: I wrote this script on an Ubuntu machine but I think it could work on other Linuxes as well.

---

### Post by Magnetizer on 2012-08-28
Dear Ubuntu lovers,

here's an update of the script with the following changes:

1) The script now tries to download a remote hostsfile 3 times before stopping.

2) Some minor changes in the manual.

---

### Post by Magnetizer on 2012-08-30
Hi everybody,

here is another little update.

You can now use the commandline option -w [time to wait in seconds].

It defines the minimum of time between two hostsfile updates which is a time consuming process.

With this option you can run the script by cron as often as you like but it will only update the hostsfile if the minimum wait time has passed.

It gives you more control than cron does by itself as running the script once a day by cron will only work if the computer is switched on at that time.

Have fun and take care.

---

### Post by Magnetizer on 2012-10-15
Hi everyone,

here is another little update of the script.

I have fixed a little bug that prevented the script to correctly report the addtitions to / removals from the total hostsfile.

It can happen that a host is reported as an addition / removal to one of the downloaded hostsfiles that is not reflected in the total hostsfile. This is perfectly fine because the same host could already have been inside one of the other downloaded hostsfiles aswell.

On the other hand all additions / removals to the total hostsfile should be reflected in one of the downloaded hostsfiles. This wasn't the case all the time due to a regular expression that was too restrictive. This has been fixed in this update.

The update is of a cosmetic nature, the script did the right thing all the time.

So, use the script and keep it safe!

Kind regards,

Magnetizer

---

