---
title: "is there a way to monitor use of rm commands"
date: 2011-03-09
forum: Security
---

### Post by newsman on 2011-03-09
is there a way to monitor use of rm, cp and mv commands? (other than in history)... i would prefer if it were logged in /var/log directory with time and command (with its arguments).

Is there anyway to do this.

---

### Post by coffee412 on 2011-03-09
> **newsman said:**
> is there a way to monitor use of rm, cp and mv commands? (other than in history)... i would prefer if it were logged in /var/log directory with time and command (with its arguments).

Is there anyway to do this.

There is a way to replace the rm command with a script that would log every time you do a rm I think. You will have to googlel it as I have not done this in a long time. 

In a nutshell, Create a script that sends the command line to your log or to a created log file. Example would be /var/log/RM.log 

You have to alias the script in your personal settings so that when you login it take effect. 

Im sorry I cannot really give you more information but as I said I cannot remember without googling a while to fit it all together. But it is possible.

PS - See this link ---> [http://www.linfo.org/alias.html](http://www.linfo.org/alias.html)

Then research on how to send the command line output to a log file and run the command at same time I think would be the answer. You will probably use the 'tee' command in a bash shell script as starters.

---

### Post by skraps on 2011-03-09
Here a high end solution [http://www.quest.com/Privilege-Manager-for-Unix/](http://www.quest.com/Privilege-Manager-for-Unix/)

---

### Post by skraps on 2011-03-09
but if you were to replace rm with a script . 

I guess you could rename the rm binary to rm-original and use a script maybe like below and save it in the priginal spot as rm with the same permissions.

psuedo code-

```

#!/bin/bash
date=`date '+%m/%d/%y - %H'`
echo "rm being used [ $1 $2 $3 $4 ] $date" >> /somefile/to/log/too
rm-original $1 $2 $3 $4

```

---

### Post by coffee412 on 2011-03-09
Thats the beauty of linux. MOre than one way to do something!

I suggested the 'tee' command as then in the logs you get the actual rm command that was typed in thats all. Of course you can also probably scrub the command line history file too I think <grin>.

Have a great one.

---

### Post by unspawn on 2011-03-10
> **newsman said:**
> is there a way to monitor use of rm, cp and mv commands? (other than in history)... i would prefer if it were logged in /var/log directory with time and command (with its arguments).
There's different ways each with their own pros and cons. Central to knowing what logging can do for you is 0) understanding how userland "commands" travel via libraries to the kernel where system calls are executed, 1) that *proper hardening of accounts and services beforehand* is vital and that any *userland* solution may seem less invasive and more convenient but at the same time is less tamper-resistant than any kernel-based solution. Finally 2) realize that no solution protects against *root* changing things. Mitigating that by remote logging to an otherwise inaccessible remote syslog host would be suggested where required.

The auditd subsystem allows you to watch system calls (for example: '-a exit,always -S unlink -S unlinkat -S rename -S renameat -S truncate -S ftruncate -k RM') with which to watch any invocation of the (here) unlink, truncate and rename system calls. Auditd also allows you to create "watches", reasonably simple rules, with which to monitor file access (like '-a always,exit -F path=/bin/rm -F perm=x -k RM'). Both these and syscall rules log time stamp, Ids, command and arguments to /var/log/audit/audit.log and rules can be limited to one or more users (say UID >= 500). 

A shell wrapper like 'rootsh' can log complete CLI shell sessions (and via syslog to remote as well).

Again, while a scripted kludge may seem convenient, do realize that for instance an update of binaries requires you to restore that kludge, offering a window of opportunity, making it less standards compliant and more of a hassle to get right (if you must I certainly would replace 'bash' and 'echo' with 'ash' or 'dash' and 'logger') and maintain than any other solution IMHO...

---

