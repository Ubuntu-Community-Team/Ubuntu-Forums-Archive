---
title: "Nagios issues command but wont send email"
date: 2009-12-29
forum: Server Platforms
---

### Post by MMistro on 2009-12-29
So I have nagios set up and all configured. However it wont seem to send out any emails...

Checking the debug logs, the following command gets issued:

```

/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: RECOVERY\n\nService: Disk Space\nHost: localhost\nAddress: 127.0.0.1\nState: OK\n\nDate/Time: Tue Dec 29 21:26:32 EST 2009\n\nAdditional Info:\n\nDISK OK" | /usr/bin/mail -s "** RECOVERY Service Alert: localhost/Disk Space is OK **" myemail@gmail.com
```However, nothing gets sent out it seems according to the mail logs...

When I run the command manually by cutting and pasting the debug output in the command line, it works, and the appropriate message gets put in the mail logs.


EDIT: I'm using msmtp for my mailer. All other services going through the sendmail interface seem to work ok though...

EDIT2: I also noticed in the nagios debug log that this is there after the mail sending command:

```
Execution time=0.007 sec, early timeout=0, result=0, output=(null)
```so it seems to be executing properly too... very strange...

Any one have any ideas? :(




EDIT3: So tried putting in other commands in place of that email line... I just made a simple script which echo's "SUCESS"  and put that as the email command.

It seems to have run:
```
Execution time=0.005 sec, early timeout=0, result=0, output=SUCCESS
```

SO i guess the question is... why isn't the mail being sent? I can run the mail command it executes from the command line just fine.

Is it a permissions issue?

---

### Post by KiLaHuRtZ on 2009-12-29
Do you have MailX installed?  In short, that is the command '/usr/bin/mail' which is not installed by default nor automagically installed when installing nagios or an smtp service.

```
sudo apt-get install mailx
```

---

### Post by MMistro on 2009-12-30
Yup its installed and works from the command line. If I run the same command that the log says its running but from the command line, it works.

ie: this works from the command line 

```
/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: PROBLEM\n\nService: Disk Space\nHost: localhost\nAddress: 127.0.0.1\nState: WARNING\n\nDate/Time: Wed Dec 30 00:14:39 EST 2009\n\nAdditional Info:\n\nDISK WARNING - free space: /home/thivyan/C 33433 MB (17% inode=99%):" | /usr/bin/mailx -s "** PROBLEM Service Alert: localhost/Disk Space is WARNING **" myemail@gmail.com
```

This is just a copy and paste to the command line of what is in the debug log for nagios. It works from the command line.

I've tried both mailx and mail in the command line and the config file. Both work from the commandline, but not when invoked by the script.

Permissions all seem ok as well.

In fact, if I set the command to be something like just

```
 /usr/bin/mail -s "empty body" email@whatever.com 
```without the printf pipeing in... When I check the debug logs for nagios, I get the returned output as the normal "Empty body; hope that's ok" which means that sendmail is running...

Except nothing gets sent, and nothing shows up in the logs. Again, if I invoke the same script from command line, it seems to work, with the same "empty body" warning but still sends.

I've checked that everything has global execute permissions.

EDIT:

Just to be safe I tried apt-getting, and it is indeed installed:

```
mailx is already the newest version.
```

---

### Post by javahollic on 2010-01-29
Did you find a solution for this?  Am confronted with identical problem :/

---

### Post by MMistro on 2010-01-29
Yes I did. It had been a problem with the permisisons to the msmtprc file. See here for details:

[http://www.linuxquestions.org/questions/linux-newbie-8/nagios-issues-command-but-wont-send-email-778800/](http://www.linuxquestions.org/questions/linux-newbie-8/nagios-issues-command-but-wont-send-email-778800/)

---

