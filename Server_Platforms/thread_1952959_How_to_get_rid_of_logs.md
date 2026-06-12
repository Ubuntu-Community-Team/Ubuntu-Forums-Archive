---
title: "How to get rid of logs?"
date: 2012-04-05
forum: Server Platforms
---

### Post by Nailox on 2012-04-05
Hi, Im getting huge log files in my /var/log which are taking too much space on the HDD. I need to stop the proceses which are creating them and to make sure they dont start after reboot. The log files are:
xconsole.log
syslog
mail.warn
mail.info
mail.err
daemon.log
auth.log

Can you pls tell me how to stop those files from being created?

---

### Post by 2F4U on 2012-04-05
There is usually a reason when log files are growing huge and you should check what could be the reason.

The general settings of the logrotate daemon, which is responsible for rotating and deleting log files can be found in /etc/logrotate.conf. Application specific settings are in seperate files in /etc/logrotate.d.

Here are two tutorials on how to configure log rotation:

[http://lifeonubuntu.com/configuring-log-rotation-of-apache2-and-other-logs/](http://lifeonubuntu.com/configuring-log-rotation-of-apache2-and-other-logs/)
[http://www.watchingthenet.com/how-to-manage-log-file-size-archive-deletion.html](http://www.watchingthenet.com/how-to-manage-log-file-size-archive-deletion.html)

---

### Post by Nailox on 2012-04-05
I prefer disabling syslogd instead of using logroatate. how can disable it so it wont run on startup?

---

### Post by 2F4U on 2012-04-05
I don't think that it makes sense to remove syslog, since it has valuable information in it when it comes to issues. However, it should be simple to remove the package:

[http://ubuntuforums.org/showthread.php?t=1273413](http://ubuntuforums.org/showthread.php?t=1273413)

You could also move you log and temp files to RAM, so that they are not kept when the machine is shutdown or rebooted:

[http://www.fewt.com/2010/07/move-your-logs-and-temp-files-to-ram.html](http://www.fewt.com/2010/07/move-your-logs-and-temp-files-to-ram.html)

---

### Post by CharlesA on 2012-04-05
> **2F4U said:**
> There is usually a reason when log files are growing huge and you should check what could be the reason.


+1

> **2F4U said:**
> I don't think that it makes sense to remove syslog, since it has valuable information in it when it comes to issues.

+1 as well.

Logs are there for a reason and if they are growing to enormous sizes, you should check them out and see what the problem is and fix the underlying cause.

---

### Post by QIII on 2012-04-05
Take a look at the "Did I just get owned" link in the security guide CharlesA links to.

If you remove those logging features you will never know.

---

### Post by SeijiSensei on 2012-04-05
I also wonder what would happen to all the requests the various services make if there's no syslog daemon available to handle them.  Disabling syslog doesn't mean the server daemons won't be trying to communicate with the syslog daemon.

By default logrotate rotates the main logs like messages, syslog, and mail.log on a weekly basis.  You can tell it to keep fewer copies if you want by changing the "rotate N" directive.  But if you have a log that's growing rapidly, chances are good there's some serious problem you need to fix.  

Which logs are so large as to be problematic?

---

### Post by |{urse on 2012-04-05
sudo apt-get install toilet :lolflag:

---

### Post by khelben1979 on 2012-04-05
If the log files have grown too big and you just want to get rid of them, you can always manually just delete them.

Other than that I agree on the previous posters, I would never want to clean the hard discs of log files, better get a bigger hard drive instead, problem solved.

Also, from personal experience, I would recommend a /var partition at between 7 - 10 gigabyte. Times have changed, and some applications can spit out a lot of log files, especially segmentation faults if your Ubuntu system suffers from instability.

---

### Post by Nailox on 2012-04-12
ok so the right way is to rotate the logs. But the logs Im talking about are system generated logs like mail.info, syslog, etc. So they are not rotated with logrotate but with syslog. So from what I read I have to edit /etc/cron.daily/sysklogd because its handling the daily rotation of the system logs. I want to make it rotate all logs daily. in it i found this: > # sysklogd      Cron script to rotate system log files daily.
#
#               If you want to rotate other logfiles daily, edit
#               this script.  An easy way is to add files manually,
#               to add -a (for all log files) to syslogd-listfiles and
#               add some grep stuff, or use the -s pattern argument to
#               specify files that must not be listed.


So I have to add -a to syslogd-listfiles ? How exactly to do this ?

---

### Post by SeijiSensei on 2012-04-12
On my system log rotation is handled by the logrotate program.  To change the frequency from weekly to daily, edit /etc/logrotate.d/rsyslog and replace the keyword "weekly" with "daily" in the second stanza of that file.

---

### Post by Nailox on 2012-04-12
Yes but isn't the logrotate program only for application and utilities logs ? I need to rotate system generated logs.

---

### Post by SeijiSensei on 2012-04-12
No, it rotates anything for which a definition exists in /etc/logrotate.d/.  By default all the system logs are rotated in accordance with the rsyslog file in that directory.

I sometimes create custom definitions for things like my mail folders so they don't get unreasonably large.

---

### Post by bubylou on 2012-04-13
I would strongly urge that you do not get rid of any log files. You should look and see what is filling them up and how to correct it. Logging is an essential part of any server.

---

### Post by webservervideos on 2012-04-13
you can enable logrotation on a daily basis. you can also make logs be forced to rotate after a certain size is reached. and you can limit the number of old logs kept to one or two...  thus you will have all your logs for issues, but keep them small.

---

### Post by Nailox on 2012-04-30
> **SeijiSensei said:**
> No, it rotates anything for which a definition exists in /etc/logrotate.d/.  By default all the system logs are rotated in accordance with the rsyslog file in that directory.

I sometimes create custom definitions for things like my mail folders so they don't get unreasonably large.

YOu mean the mail.log, mail.info and the others mail related logs? I need to rotate them too. Can you tell me how do you create custom definitions for them ? thanks

---

### Post by Jonathan L on 2012-04-30
Hi Nailox

> YOu mean the mail.log, mail.info and the others mail related logs? I need to rotate them too. Can you tell me how do you create custom definitions for them ? thanks

The file /etc/rsyslog.d/rsyslog.conf contains by default (10.04 server) the following which clearly shows the log files it works on.  If you want them smaller, you could simply change "weekly" to "daily" or the number of files to keep.  Make sure you have compress, by the way.

Unsurprisingly, I'm with the others about about keeping logs.  On my systems I like to keep compressed logs for several years: if you have a security incident or a fault, there's nothing like being able to go back and find out when it started.

You say it's filling up your drive.  How big are your logs?  If they're getting too big, my guess is there's something wrong.  I certainly wouldn't shoot the messenger.

```
/var/log/syslog
{
    rotate [COLOR=Red]7[/COLOR]
    daily
    missingok
    notifempty
    delaycompress
    [COLOR=Lime]compress[/COLOR]
    postrotate
        reload rsyslog >/dev/null 2>&1 || true
    endscript
}

/var/log/mail.info
/var/log/mail.warn
/var/log/mail.err
/var/log/mail.log
/var/log/daemon.log
/var/log/kern.log
/var/log/auth.log
/var/log/user.log
/var/log/lpr.log
/var/log/cron.log
/var/log/debug
/var/log/messages
{
    rotate [COLOR=Red]4[/COLOR]
    [COLOR=Red]weekly[/COLOR]
    missingok
    notifempty
    [COLOR=Lime]compress[/COLOR]
    delaycompress
    sharedscripts
    postrotate
        reload rsyslog >/dev/null 2>&1 || true
    endscript
}
```

Hope that helps.

Kind regards,
Jonathan.

---

### Post by SeijiSensei on 2012-04-30
> **Nailox said:**
> YOu mean the mail.log, mail.info and the others mail related logs? I need to rotate them too. Can you tell me how do you create custom definitions for them ? thanks

No, as Jonathan says, mail.log and the others are rotated by default with logrotate.

I was talking about things like my personal mail folders which can get quite large.  I keep an archive copy of every message I receive and put them in /home/seiji/mail/archive on my IMAP server.  I use logrotate on the server to rotate that file monthly with a simple configuration like

```

/home/seiji/mail/archive {
     rotate 48
     monthly
}

```

which creates monthly backups and keeps them for four years.

If you haven't yet done so, you should browse the files in /etc/logrotate.d/ to see what logs are rotated by default.

---

