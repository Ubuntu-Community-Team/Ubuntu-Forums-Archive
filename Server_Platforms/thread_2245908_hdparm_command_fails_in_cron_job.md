---
title: "hdparm command fails in cron job"
date: 2014-09-27
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2014-09-27
Hi all

Trying to run the following code as a cron job

```
@midnight root /sbin/hdparm -y /dev/sdb1 >> /home/chris/Desktop/bin/zoneedit.log
```

The emailed error message is:-> /bin/sh: 1: root: not found

Ideas, workarounds, please?

TIA

---

### Post by TheFu on 2014-09-27
delete "root" from the line?  
**man crontab**

---

### Post by steeldriver on 2014-09-27
... in particular, it looks like you've used the /etc/crontab format instead of the regular user-crontab format

```

       cron also reads /etc/crontab, **which is in a slightly different  format**
       (see  crontab(5)).   In  Debian, the content of /etc/crontab is prede&#8208;
       fined  to  run  programs  under   /etc/cron.hourly,   /etc/cron.daily,
       /etc/cron.weekly and /etc/cron.monthly. This configuration is specific
       to Debian, see the note under DEBIAN SPECIFIC below.

```

---

### Post by ChrisRChamberlain on 2014-09-27
TheFu, steeldriver

Thanks for your replies.

Have removed 'root' as suggested and will await result tomorrow.

Have always used ''@midnight ..." but will change if it's that causing the problem.

---

### Post by TheFu on 2014-09-27
Perhaps an example will help?

```
$ crontab -l
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command to be executed

10 1 * * * /home/thefu/bin/push_keepass_db.sh
# 31 4 * * * /home/thefu/bin/backup_to_rom.sh  - now down using root crontab
31 6 * * * /home/thefu/bin/chk-fail2ban.sh 

#    grab ManifestInvesting data every Friday at 18:45
45 18 * * 5 /home/thefu/bin/grab-mi.pl

# Run BeanCounter on Weekdays
22 16 * * 1-5 /home/thefu/bin/Stock-Report.sh 

22 16 * * 1-5 /home/thefu/bin/Stock-Report.sh 

```
Of course, if you want to run something as root, then put it into the root crontab. Above is my normal user account crontab.

---

### Post by ChrisRChamberlain on 2014-09-27
TheFu

Many thanks for the examples.

Code now reads:-
```
59 23 * * * /sbin/hdparm -y /dev/sdb1 >> /home/chris/Desktop/bin/zoneedit.log
```

---

### Post by TheFu on 2014-09-27
So .... er .... if you want to run this as root, it needs to be in the root crontab.    And ... er .... it is a bad idea to write output from root cron jobs to /home - for many reasons.  Why not /var/log?  then you can have logwatch look for issues and logrotate ... er .. deal with it getting too big automatically.

---

### Post by tgalati4 on 2014-09-28
*hdparm* requires root privileges.  Understand that manually putting a drive to sleep can have issues if there is activity on that drive.  A better way would be to set the power management features of the drive to put it sleep automatically when not used for an hour.

Some examples:

```
cat /etc/hdparm.conf
```

What is the Use Case?  What exactly are you trying to accomplish?

---

### Post by ChrisRChamberlain on 2014-09-28
tgalati4

Thanks for your reply and comments.

The reason for wishing to put the drive(s) to standby is that they are mainly used for archive purposes and so are accessed infrequently, maybe not for days or weeks.

Midnight is the time least likely to have drive activity and was trying to avoid the use of a script to perform, hopefully, a simple task.

Afraid don't understand your example.

---

### Post by tgalati4 on 2014-09-28
Open a terminal and type in the above command.  You will see a list of commented hdparm settings.  Uncomment the one that you think is appropriate for your Use Case.  You will have to reboot for them to take effect.

Most modern drives will go to sleep when not used.  If there are any system files on the drive, then the drive will get spun up frequently.  Including a dedicated mount in /etc/fstab.

To learn more about hdparm:

```
man hdparm
```

---

### Post by ChrisRChamberlain on 2014-09-29
Many thanks to all who replied.

The issue of the failing command has been resolved by the use of the root crontab, the existence of which I was unaware.

The path to the log has also been changed and alternative uses of hdparm are now under consideration.

---

