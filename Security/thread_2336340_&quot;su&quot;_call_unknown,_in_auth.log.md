---
title: "&quot;su&quot; call unknown, in auth.log"
date: 2016-09-07
forum: Security
---

### Post by davidgv on 2016-09-07
Hi.


In the auth.log of my server, I found this entry repeat (one entry for second aprox.):


[INDENT]Sep  6 12:30:53 yogui su[7875]: No passwd entry for user 'killingfloor2'[/INDENT]
[INDENT]Sep  6 12:30:53 yogui su[7875]: FAILED su for killingfloor2 by root[/INDENT]
[INDENT]Sep  6 12:30:53 yogui su[7875]: - ??? root:killingfloor2[/INDENT]


The "root" user tries to do login to "killingfloor2" user (that not exists) without password.


I have been searching this call, but I have not found it. How could I find the origin of this command "su"?

---

### Post by SeijiSensei on 2016-09-07
"su" is the "superuser" command.  The root user can use it to become another user.  In this case, auth.log is telling you that some process is trying to become the user killingfloor2.  Do you recognize this username?

Does this entry appear periodically in the logs like once per hour or per day?  If so, it is likely the result of a "cron" job.  Use the command "grep CRON /var/log/syslog*" to search through the logs and see what processes are running periodically.  Anything associated with killingfloor2?  If not, compare the timestamps in the auth.log with the ones in syslog to see if you can find the process involved.

If you cannot find what is generating this error, and especially if you don't recognize the "killingfloor2" name, I'd be suspicious and reinstall the operating system.

BTW, the first source of documentation for any Linux command like su is its manual page.  Type the command "man su" at the prompt to get details.

---

### Post by davidgv on 2016-09-07
> "su" is the "superuser" command.  The root user can use it to become another user.  In this case, auth.log is telling you that some process is trying to become the user killingfloor2.  Do you recognize this username?

Yes, "killingfloor2" is an user account that I created to install a gameserver for the game "Killing Floor 2". But I removed the gameserver (the app) and the "killingfloor2" account.

> Does this entry appear periodically in the logs like once per hour or per day?  If so, it is likely the result of a "cron" job.  Use the command "grep CRON /var/log/syslog*" to search through the logs and see what processes are running periodically.  Anything associated with killingfloor2?  If not, compare the timestamps in the auth.log with the ones in syslog to see if you can find the process involved.

Not. It's not a CRON job.

Also, this stamp in auth.log is generated twice for second.

I have searched, with the "find" command, any file or directory with any relation with "killingfloor2", but nothing...

If I could find from where are been generated this calls, I might do something.

---

### Post by SeijiSensei on 2016-09-07
Have you tried "grep killingfloor /var/log/* | more"?

---

### Post by davidgv on 2016-09-07
> **SeijiSensei said:**
> Have you tried "grep killingfloor /var/log/* | more"?

With 2 calls/second, I don't ending never...

I tried this:

```
sudo find /var/log/* -type f -not -path "/var/log/auth*" -exec grep -H "killingfloor2" {} \;
```

... for find some entry in /var/log/ with "killingfloor2"... but nothing of nothing. The only entries with "killingfloor2" that appear in /var/log is in auth.log

I would like to know from where is called this "su" command.

---

### Post by steeldriver on 2016-09-07
I've noticed that people running gameserver type applications often seem to throw startup commands for them in /etc/rc.local - perhaps have a look there?

---

### Post by &amp;KyT$0P# on 2016-09-07
See if this sheds any light?
```
ps auxf
```
Pipe that command's output into [FONT=Courier New]less -S[/FONT] or redirect it to a file.  Search through that lot for this [FONT=Courier New]su[/FONT] process, maybe knowing its parent process will help?

---

### Post by davidgv on 2016-09-07
> **steeldriver said:**
> I've noticed that people running gameserver type applications often seem to throw startup commands for them in /etc/rc.local - perhaps have a look there?

Nothing in /etc/rc.local

---

### Post by davidgv on 2016-09-07
> **halogen2 said:**
> See if this sheds any light?
```
ps auxf
```
Pipe that command's output into [FONT=Courier New]less -S[/FONT] or redirect it to a file.  Search through that lot for this [FONT=Courier New]su[/FONT] process, maybe knowing its parent process will help?

```
ps > fileps
grep killingfloor2 fileps
```

... not show nothing.

---

### Post by &amp;KyT$0P# on 2016-09-07
Er, the "auxf" wasn't a typo, it's a necessary part of the command...

---

### Post by davidgv on 2016-09-07
> **halogen2 said:**
> Er, the "auxf" wasn't a typo, it's a necessary part of the command...

It's the same, don't shows nothing.

---

### Post by davidgv on 2016-09-07
I have run the **htop** command and, searching with F3 key, searching by "killingfloor2", this show me the proccess **/usr/lib/rtkit/rtkit-daemon**

Then, how can I stop these calls from rtkit-daemon ?

---

### Post by davidgv on 2016-09-07
> **davidgv said:**
> I have run the **htop** command and, searching with F3 key, searching by "killingfloor2", this show me the proccess **/usr/lib/rtkit/rtkit-daemon**

Then, how can I stop these calls from rtkit-daemon ?

Not, I think that it's an error, and **htop** show **rtkit-daemon** because it's the only command in run with "ki" letters, the most similar I think.

---

### Post by #&amp;thj^% on 2016-09-07
Out of curiosity what dose this show from the terminal
```
cd /lib/systemd/system
ls

```

---

### Post by davidgv on 2016-09-08
> **1fallen said:**
> Out of curiosity what dose this show from the terminal
```
cd /lib/systemd/system
ls

```

Contains some files, and none of those contain nothing related to user "killingfloor2".

---

### Post by davidgv on 2016-09-12
nobody knows what can be generating this calls ?

---

### Post by deadflowr on 2016-09-12
What method of install the killingfloor2 server did you use?
Perhaps something else got pulled in that you were not awares of.

---

### Post by davidgv on 2016-09-13
> **deadflowr said:**
> What method of install the killingfloor2 server did you use?
Perhaps something else got pulled in that you were not awares of.

I installed it with the **SteamCmd **tool, an app to install this apps class:
[http://wiki.tripwireinteractive.com/index.php?title=Dedicated_Server_(Killing_Floor_2)](http://wiki.tripwireinteractive.com/index.php?title=Dedicated_Server_(Killing_Floor_2))

---

