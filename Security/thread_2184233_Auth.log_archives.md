---
title: "Auth.log archives"
date: 2013-10-28
forum: Security
---

### Post by flejusia on 2013-10-28
Hi,

I'm a complete beginner and even though I know that I can find the answer to my question on the internet, I'd struggle to apply it.

I would like to check whether anyone has logged into my laptop over the summer, when I was away. As far as I understand, the auth.log files should allow me to do so, but I can't find any data from earlier than a week ago. How do I access older logs (I assume they are stored somewhere?) and how do I find the ones from a particular period, say 'before 1st September' or 'in August'? I should also mention that the person I suspect of having logged into my computer knew my password (yes, I learnt my lesson...)

If the person deleted the relevant log files soon after they used my laptop would there be any other way of finding out whether it has indeed taken place? Is there a log of loggin off or something?

Thank you very much for your help.

---

### Post by Lars Noodén on 2013-10-28
Well, with a compromised machine, the only thing you can do to be sure it is clean is to back up the data, wipe it, and install a fresh system.  

If they had access to root, then there was in principle access to edit the logs.  There is no tracking or auditing to expose when or if they were edited.

But on the off chance that the logs were not edited, you could check in the old logs -- if they are still there.  The system utility "logrotate" packs up the older log files and compresses them.  The oldest ones are deleted to make room for the next.   The file /etc/logrotate.conf sets the defaults for rotation and  /etc/logrotate.d/rsyslog  covers auth.log specifically.  In short, it gets rotated weekly with only 4 weeks being kept, so in all likelihood you only have log data going back four or five weeks.  See "man logrotate.conf" in the terminal for details.  

Of the files you do have you can use zcat and [awk](http://www.grymoire.com/Unix/Awk.html) to rummage through them for a specific date.

```

sudo zcat /var/log/auth.log.*.gz | awk '$1 == "Oct" { print }'
sudo zcat /var/log/auth.log.*.gz | awk '$1 == "Oct" && $2 == "24" { print }'

```

The first goes through all compressed auth.log files (using [globbing](http://manpages.ubuntu.com/manpages/raring/en/man7/glob.7.html)) and looks for ones from October.  The second one goes through the same files but looks for those that are from only October 24th.

---

### Post by Lars Noodén on 2013-10-28
Also, if you just want to browse through the compressed files, you can use "less" It will page through both regular and compressed files.  

It can also search forwards / and backwards ? for regex patterns.

---

