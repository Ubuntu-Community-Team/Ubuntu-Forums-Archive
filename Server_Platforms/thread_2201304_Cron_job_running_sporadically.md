---
title: "Cron job running sporadically"
date: 2014-01-23
forum: Server Platforms
---

### Post by aysiu on 2014-01-23
I created a root-run cron job using ```
sudo crontab -e
``` This is roughly what it looks like ```
30 7,13 * * 1-5 /usr/bin/php /var/www/path/to/nameofscript.php > /dev/null
``` And when I check with ```
ps -ef|grep cron
``` it shows that cron is running: ```
root 975 1 0 Jan14 ? 00:00:01 cron
username 35075 34975 0 17:27 pts/0 00:00:00 grep --color=auto cron
``` Am I doing this wrong? I'm trying to have that PHP script run twice a day every weekday.

It seemed to go well the first day or so, but after that, I've had to run the script manually (by visiting it in a web browser).

Any tips? Thanks in advance.

---

### Post by ian-weisser on 2014-01-23
Well, could be a lot of possible problems:
Does the php script require a display? Root cron jobs wouldn't have one.
Is the machine shut down or suspended at either of those times?
Is the script or data encrypted?  Root cron jobs may not have the key to decrypt.
Could the permissions of the script or file have changed?

You can probably find out the problem if you redirect your output to a file instead of /dev/null.

---

### Post by SeijiSensei on 2014-01-24
Grep /var/log/syslog for "cron".  Do you see any errors?

I presume this script runs correctly from the command prompt as the root user.  However, if you can run the script from a browser, doesn't that mean it works as user "www-data," the user that owns the Apache process, rather than root?

I agree with Ian.  Replace "/dev/null" with "/var/log/nameofscript" and see what it reports.

---

### Post by aysiu on 2014-01-24
Thanks for the replies.

The PHP script does not require a display, and the machine is never shut down or suspended. Nothing encrypted. And I don't believe the permissions have changed. What's baffling to me is that it *sometimes* runs. So you'd think if it were a permissions issue (root doesn't have permission, which also makes no sense, since root always permission) that it would *never* run.

In the /var/log/syslog, I see ```
CRON[36922]: (root) MAIL (mailed 1 byte of output; but got status 0x0001, #012)
``` and then ```
CRON [36943]: (root) CMD ( [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5  $(/usr/lib/php5/maxlifetime))
``` Not sure if that's bad or not.

But I'll definitely take the suggestion of outputting to a file instead of /dev/null, just to see what happens.

---

### Post by aysiu on 2014-01-27
Unfortunately, I'm not really any closer to a solution. I did have it output to a text file instead of to /dev/null, but it's pretty clear it's just running whenever it feels like it. For example, it ran just fine this morning (at 7:30am) with no prompting. At 1:30pm, however, nothing... I had to run it manually.

Can I get confirmation from any cron experts that this first part of the line does what I think it does?
```
30 7,13 * * 1-5
``` If I understand this correctly, it will run the script at 7:30am and 1:30pm every weekday. Is that right?

---

### Post by The Cog on 2014-01-27
I would add 2>&1 to the end of the crontab line (when writing to a log file) in order to catch any error output as well. It may come up with something informative.

---

### Post by aysiu on 2014-01-27
Thanks for the suggestion. So if I tweak it, it'd be something like this? ```
30 7,13 * * 1-5 /usr/bin/php /var/www/path/to/nameofscript.php > /home/username/logfile.txt 2>&1
``` or more like this? ```
30 7,13 * * 1-5 /usr/bin/php /var/www/path/to/nameofscript.php 2>&1 /home/username/logfile.txt
``` I guess I'm not really sure where the **2>&1** goes...

---

### Post by The Cog on 2014-01-27
The first one. It redirects stdout to the logfile, and redirects stderr to the same place as stdout.

There is a shortcut notation that works with bash but not sh:
```
/usr/bin/php /var/www/path/to/nameofscript.php >& /home/username/logfile.txt
```

---

### Post by aysiu on 2014-01-28
Thanks. I'll give that a go.

---

### Post by aysiu on 2014-01-28
I think it may be something in the cron statement itself, because the 7:30am one seems to launch fine... it's just the 1:30pm one that doesn't launch and doesn't even seem to write anything to the log file.

Can someone verify that this is the best way to say "twice every weekday at 7:30am and 1:30pm"?

```
30 7,13 * * 1-5
``` Maybe it's not 13? I thought 13 meant 1pm...

---

### Post by koenn on 2014-01-28
yes, it looks OK to me.

One thing comes to mind : 
I usually do this kind of thing in /etc/crontab, not by running "crontab'.  maybe your way works slightly differently and  doesn't  handle the comma-separated list of hours ?

in /etc/crontab you need to specify a user account, so that would look like 
```
 30   7,13    *    *    1-5     root     /usr/bin/php /var/www/path/to/nameofscript.php 
```

maybe give it a try

---

### Post by Dave_L on 2014-01-28
I'm pretty sure the "7,13" is fine. You could verify it by adding another trivial cron task with the same scheduling:

```

30 7,13 * * 1-5 /usr/bin/php /var/www/path/to/nameofscript.php > /home/username/logfile.txt 2>&1
30 7,13 * * 1-5 /bin/date >>/tmp/date.log 2>&1

```

---

### Post by aysiu on 2014-01-28
Yeah, I was going with ```
sudo crontab -e
```, but I guess I could do /etc/crontab and specify the user.

---

### Post by aysiu on 2014-01-28
> **Dave_L said:**
> I'm pretty sure the "7,13" is fine. You could verify it by adding another trivial cron task with the same scheduling:

```

30 7,13 * * 1-5 /usr/bin/php /var/www/path/to/nameofscript.php > /home/username/logfile.txt 2>&1
30 7,13 * * 1-5 /bin/date >>/tmp/date.log 2>&1

``` Thanks, Dave_L. I'll try that as well.

---

### Post by SeijiSensei on 2014-01-29
> **aysiu said:**
> Yeah, I was going with ```
sudo crontab -e
```, but I guess I could do /etc/crontab and specify the user.

Since the job seems to work when accessed from a web browser, see if specifying www-data as the user rather than root in /etc/crontab helps.

You'll want to remove /var/spool/cron/root if you take the /etc/crontab path unless you have other cron jobs in that file.

---

### Post by aysiu on 2014-01-29
I was thinking that, too, except that it would be odd for it to be a permissions issue if it runs just fine at 7:30am (which it does).

That said, I checked the second cronjob output, and /tmp/date.log produced what it should have: ```
Wed Jan 29 07:30:01 EST 2014
Wed Jan 29 13:30:01 EST 2014
``` so the cronjob timing piece is correct.

This is a real head-scratcher, so I appreciate everyone's help and input so far.

---

### Post by The Cog on 2014-01-29
How about making a wrapper script something like this:
```
#!/bin/bash
d=$(/bin/date)
echo $d Starting >> /tmp/date.log
/usr/bin/php /var/www/path/to/nameofscript.php > /dev/null
echo $(/bin/date) From $d Finished >> /tmp/date.log
```
And running that twice daily from a single cron entry.
I just have a nagging feeling that maybe the php is being run but something else is mucking things up.
E.g. if the php takes 18 hours to finish, every other one may bomb out perhaps.

---

### Post by aysiu on 2014-01-29
That's a little above my head, but I like your thinking. What I may do for now is just run it once a day at 7:30am to see if there's any problem there. Maybe something is hanging over that doesn't resolve by 1:30.

---

### Post by SeijiSensei on 2014-01-30
I wrote a post the other day that shows how to [use a lock file]("http://ubuntuforums.org/showthread.php?t=2201208&p=12909106&viewfull=1#post12909106") to make sure one process is completed before the next begins.  Six hours seems like a very long time for a script to run though.

---

### Post by The Cog on 2014-01-31
I know, it's unlikely. But there's something odd going on, and running both scripts from the same wrapper would eliminate problems with cron itself.

---

### Post by koenn on 2014-01-31
yeah,  I was also thinking that the 6 AM script running too long could interfere with the  1PM script starting - but shouldn't cron throw an error then ? (IIRC Ubuntu server drops those in the root mailbox) 


Hunch: the 6PM script sets a lock on certain resources (eg files, or maybe  database tables), the 1 PM jobs fails because the resources are still in use and it can not access them; by the next day the locks are released or have timed out so the 6AM job starts again just fine.
The timings from the COg's wrapper should indicate whether  this is the case. ...

---

### Post by aysiu on 2014-02-01
Thanks, everyone, for your suggestions. I want to be as systematic as I can about this. Unfortunately, things have gotten a bit busy for me, so I haven't had a chance to properly isolate the problem yet.

---

### Post by aysiu on 2014-02-17
Right now I have it set to run once a day in the morning, and it seems to be good, so I may just stick with that for now.

---

### Post by SeijiSensei on 2014-02-17
Does the job write a log?  How long does it take to complete?

---

### Post by aysiu on 2014-02-17
It just send a PHP email. Takes less than a second to complete.

---

### Post by SeijiSensei on 2014-02-18
Then it's still puzzling why you seemingly cannot run another instance of the job six hours later.

---

### Post by aysiu on 2014-02-18
I know. Haven't had the time to devote to this to properly diagnose the issue yet.

---

