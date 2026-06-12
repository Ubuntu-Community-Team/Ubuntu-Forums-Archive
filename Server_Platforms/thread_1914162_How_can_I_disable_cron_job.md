---
title: "How can I disable cron job?"
date: 2012-01-23
forum: Server Platforms
---

### Post by jocampo on 2012-01-23
Ok

It sounds like an easy question. I also know it "should be" via pound sign ... at the beginning of the lines, like this ...

```
#00 00 * * * sh /home/jocampo/.Scripts/iTunesBackup
```

However, for some reason does not work on my Ubuntu headless server.

That script used to copy my music library to a mounted external drive. But I no longer need that, moved my music to another server. So I decided to unmount the external drive and comment the line. But two times, early morning, I noticed that the server keeps executing that line and filling my / instead. Really, really weird.

Do I have to do something else in order to comment the line?

By the way ... the reason why I am not deleting the line is because I am planning to re-use the script later in time.

---

### Post by TheFu on 2012-01-23
That should work, if you are editing the correct crontab file i.e. it runs as your userid.
Is it possible that you needed to run as a different userid, perhaps root, and forgot that you'd put the script in that file too?

Are you using `crontab -e` - if not, you need to kill -HUP the crond process to force a re-read.

---

### Post by jocampo on 2012-01-23
> **TheFu said:**
> That should work, if you are editing the correct crontab file i.e. it runs as your userid.
Is it possible that you needed to run as a different userid, perhaps root, and forgot that you'd put the script in that file too?

Are you using `crontab -e` - if not, you need to kill -HUP the crond process to force a re-read.

1st, thanks for reply!

Now, how can I know I am editing the right one or the proper way? I basically invoke crontab using sudo. Also, when I use crontab -l it is listing the live above, commented.

Can you expand a bit on how to kill the crontab process and why? I have not reboot the server so I guess that could be the only explanation. How can I gracefully stop cron or kill it.

---

### Post by HugoSerrano on 2012-01-24
Hello!
There's more than one crontab.

check:
#crontab -e
#cat /etc/crontab
#ls /etc/cron.daily/
#ls /etc/cron.d/

Also, each user got a "crontab -e"

Regards!

---

### Post by jocampo on 2012-01-24
Ok

I am almost sure I used "crontab -e" the 1st time.

What I did though, was restart the whole server (yeah, maybe less dramatic option was restarting cron)

I wake up this morning and it looks the job did not start. So I'm guessing here, the 1st time the change was not taken. But I wonder why.

Anyway, it looks has been disabled now. :D

---

### Post by Ateo on 2012-01-25
I had an issue with cron executing defaults. There was a cron task that I just couldn't disable so to solve this, I deleted /var/spool/cron and then recreated my crontabs and restarted cron. Problem fixed.

---

