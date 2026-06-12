---
title: "Ubuntu Cleaner vs. Stacer"
date: 2019-07-15
forum: The Cafe
---

### Post by Shibblet on 2019-07-15
I have always used Ubuntu Cleaner for all of my Ubuntu cleaning needs...  But the current PPA isn't updated for Disco Dingo 19.04 as of yet.  So, I have added the PPA for Stacer, which is a similar utility for cleaning.

What I would like to know, do either of these utilities offer any cleaning options that are any better than "sudo apt-get clean."  At least as far as the cleaning options are concerned>?

Ubuntu Cleaner:
[https://launchpad.net/~gerardpuig/+archive/ubuntu/ppa]("https://launchpad.net/~gerardpuig/+archive/ubuntu/ppa")

Stacer:
[https://launchpad.net/~oguzhaninan/+archive/ubuntu/stacer]("https://launchpad.net/~oguzhaninan/+archive/ubuntu/stacer")

---

### Post by TheFu on 2019-07-16
Waited for others to respond. Appears nobody has.

I've never used any GUI for these things.  There are 2 sorts of things that I bother to clean up.  Personal stuff and system stuff. I have 2 desktops and 20+ servers, so leaning GUI tools is something I tend to avoid - there is no GUI on a server - they would be worthless.

System stuff is handled by **sudo apt autoclean** and **sudo apt autoremove**.  Years ago, this didn't handle cleaning up old kernels, but that hasn't been an issue for some time.  Log files should be managed by the rsyslog or systemd so they are rotated periodically and only a specific number or size is allowed to happen. I know how rsyslog does it via config files, but I haven't a clue how systemd does it. Hasn't been an issue that I notice, except that systemd doesn't retain boot logs beyond the current boot, so I've enabled that on my systems. Hard to troubleshoot reboot issues if the logs don't last from boot to boot.

Personal stuff is storage in each users' HOME. In theory, cache files for different tools, like adobe, browsers, email programs and some others should be self-limited.  I've never seen them go crazy.  Before I run daily backups, I delete "local objects" created by browsers and adobe stuff.  I also remove temporary files (*~ and [.]*~ are the patterns) that are at least 14 days old.  I wait to remove them in case it was a file I was editing and the temporary file is just there because of a lost remote connection.  In general, I edit files remotely.  This saves on having that data accidentally in the backups and makes my system appear as a new user when I re-visit those websites again.

---

### Post by uRock on 2019-07-16
I haven't used either of those. I use Bleachbit.

---

### Post by Frogs Hair on 2019-07-16
I use Beachbit , but I omit some options including memory and free disk space.

---

### Post by cruzer001 on 2019-07-16
Hello Shibblet

Another vote for BleachBit.  Been out for years and has a good track record, its in the repositories.

---

