---
title: "failed to get lockfile for logcheck?"
date: 2007-02-12
forum: Server Platforms
---

### Post by dannyboy79 on 2007-02-12
I have received this error twice now on 2 different occasions after my machine has been up and running for a long time. (more than a week)

Warning: If you are seeing this message, your log files may not have been
checked!

Details:
Failed to get lockfile: /var/lock/logcheck/logcheck.lock

Check temporary directory: 

declare -x HOME="/home/logcheck"
declare -x LANG="en_US.UTF-8"
declare -x LANGUAGE="en"
declare -x LOGNAME="logcheck"
declare -x MAILTO="root"
declare -x OLDPWD
declare -x PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"
declare -x PWD="/var/spool/cron"
declare -x SHELL="/bin/sh"
declare -x SHLVL="2"

What does this mean and why is it happening?

edit: I think the last time this happened to me all I did was make sure that no old lockfile was left behind within /var/lock/logcheck/ and I also restarted and I think logcheck started working again.

---

