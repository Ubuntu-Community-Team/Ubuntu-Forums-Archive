---
title: "anacron/crontab best practices?"
date: 2012-04-30
forum: Server Platforms
---

### Post by PhilipSemanchuk on 2012-04-30
Hi all,
At work our team has just received a shiny new Ubuntu 12.04 installation courtesy of the server admin. We are trying to figure out the best way to manage cron jobs which we (and the server admin) find are scheduled a little unexpectedly to do anacron trumping cron occasionally. 

We're trying to make our lives simpler and would like to (a) get rid of anacron and (b) edit /etc/crontab directly to schedule cron jobs. However, Ubuntu's Cron HowTo ([https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)) says, "it is not recommended that you add anything to /etc/crontab. Apart from anything else, this could cause problem if the /etc/crontab file is affected by updates!"

Questions -- 
1) Is it really true that /etc/crontab can get overwritten during an update and that customizations to it might get lost?
2) Is it acceptable practice to disable anacron with `chmod -x /usr/sbin/anacron`?

Thanks very much
Philip

---

### Post by CharlesA on 2012-04-30
You edit the crontab of a user by running:

```
sudo crontab -u username -e
```

What do you mean that anacron is trumping cron?

Note: From the cronhowto:

> In the system crontab (/etc/crontab), if anacron is not execuatable, run-parts is used to run the files in cron.daily, cron.weekly, and cron.monthly at 6:25 AM, 6:47 AM and 6:52 AM, respectively.

I haven't run into any problems with anacron interfering with my cronjobs.

EDIT: The file in /etc/crontab is the system-wide one and doesn't seem to be overwritten after you edit a crontab with crontab -e, because that only edits a user's crontab.

---

### Post by SeijiSensei on 2012-04-30
Running updates should leave /etc/crontab unchanged unless you install a distribution from scratch, in which case all of /etc will be overwritten.

For tasks that require root privileges and run on a standard schedule like hourly, daily, etc., the easiest solution is to put a script or a symlink to a script in one of /etc/cron.hourly, /etc/cron.daily, etc.  I generally put all my custom administrative scripts in /usr/local/sbin and create symlinks to them from /etc/cron.daily, etc.

For tasks that need to be run with root privileges on some other schedule, you can edit root's crontab with "sudo crontab -e".  If you have a preferred text editor, add an "EDITOR=programname" entry in /home/username/.bashrc and in /root/.bashrc.

I still put things in /etc/crontab from time to time, but it's generally better to use the existing structures like cron.daily and the user crontabs in /var/spool/cron.

---

### Post by PhilipSemanchuk on 2012-04-30
> **CharlesA said:**
> You edit the crontab of a user by running:

```
sudo crontab -u username -e
```


Thanks for the reply.

We're not trying to edit user crontabs, we're only concerned with the system crontab in /etc/crontab. 

The HowTo seems to imply that during an update (I assume the author means `apt-get upgrade` or `apt-get dist-upgrade`) that /etc/crontab could get overwritten, so any customizations we've applied would get lost. I'm trying to verify whether or not this is the case.

> **CharlesA said:**
> 
What do you mean that anacron is trumping cron?


I ran into two situations where cron didn't behave as we expected due to anacron. The first was when I was debugging the scripts I'd added to cron.daily. The debugging cycle I'm familiar with when debugging cron jobs is to edit my script, set /etc/crontab to re-run the script (or in this case, cron.daily) two minutes from the current time, and then sit back and read slashdot while waiting for cron to re-invoke the script. Repeat until debugged. 

What frustrated me (and the sysadmin) until we figured it out is that that cycle won't work when anacron is involved. Anacron steps in and says, "Whoa, you've already run cron.daily once today, I'll make sure it doesn't run again. You're welcome." Executing the command `anacron -fnd` forces cron.daily to run which enables the debugging cycle I described above, but it took me a little while to figure that out. The sysadmin wasn't aware of it either.

The second place where anacron trumps cron is for running cron.daily. There's an entry for cron.daily in /etc/crontab, but we wasted a lot of time figuring out that it's meaningless. We wanted to change the start time of cron.daily, but that's effectively controlled by /etc/cron.d/anacron. 

We're both familiar with plain ol' cron and /etc/crontab, and anacron is just getting in the way for us. That's why we'd like to disable it, hence my question about whether or not it is acceptable practice to disable anacron with `chmod -x /usr/sbin/anacron`.

---

### Post by PhilipSemanchuk on 2012-04-30
> **SeijiSensei said:**
> Running updates should leave /etc/crontab unchanged unless you install a distribution from scratch, in which case all of /etc will be overwritten.

Thanks for the reply. This makes intuitive sense to me and it is certainly what I want to hear, but it contradicts the warning in the crontab HowTo that I quoted above. Is there documentation that guarantees what you describe?

> **SeijiSensei said:**
> 
For tasks that require root privileges and run on a standard schedule like hourly, daily, etc., the easiest solution is to put a script or a symlink to a script in one of /etc/cron.hourly, /etc/cron.daily, etc.  I generally put all my custom administrative scripts in /usr/local/sbin and create symlinks to them from /etc/cron.daily, etc.

For tasks that need to be run with root privileges on some other schedule, you can edit root's crontab with "sudo crontab -e".  If you have a preferred text editor, add an "EDITOR=programname" entry in /home/username/.bashrc and in /root/.bashrc.

I still put things in /etc/crontab from time to time, but it's generally better to use the existing structures like cron.daily and the user crontabs in /var/spool/cron.

Thanks for that advice. It's more or less what we've done, and it's good to know that others are working the same way.

---

### Post by SeijiSensei on 2012-04-30
> **PhilipSemanchuk said:**
> hence my question about whether or not it is acceptable practice to disable anacron with `chmod -x /usr/sbin/anacron`.
I think you'd be better off removing anacron from /etc/crontab and use only
```
25 6    * * *   root run-parts /etc/cron.daily
```
That's how crontab looks on RedHat-flavored systems. (I use CentOS on servers.)  I found the use of anacron puzzling as well.

> **PhilipSemanchuk said:**
> Thanks for the reply. This makes intuitive sense to me and it is certainly what I want to hear, but it contradicts the warning in the crontab HowTo that I quoted above. Is there documentation that guarantees what you describe?
I don't know.  Upgrading doesn't usually overwrite other files in /etc.  If you really want to be sure, you can make /etc/crontab immutable with "sudo chattr +i /etc/crontab".

---

### Post by LHammonds on 2012-05-01
I also think you should only use crontab.  However, I do not recommend using the "crontab -e" to make changes.  Why?  Because you cannot "revert" back to the original if you make a mistake.

Here is what I do to minimize problems with crontab (human mistakes):

1. Save the current crontab to file where you want to keep it.

```
crontab -u root > /var/temp/crontab.root
```2. Once you have created the file, make sure appropriate permissions are set by typing the following:

```
chown root:root /var/temp/crontab.root
chmod 0600 /var/temp/crontab.root
```3. Make a copy to save as a backup.

```
cp /var/temp/crontab.root /var/temp/2012-04-29-crontab.root
```4. Make your changes to the file, save and exit.

```
vi /var/temp/crontab.root
```5. Load the changes into the crontab schedule.

```
crontab -u root /var/temp/crontab.root
```If you want to temporarily disable the schedule, make sure you have a backup of the schedule (see above, step 1) and type the following:

```
touch /tmp/deleteme
crontab -u root /tmp/deleteme
rm /tmp/deleteme
```------------------------------

If you or your team need to make changes to the schedule all the time, then I would suggest making a script that will do all of this for you to ensure backups are made that can be restored.  You can make a simple script called editcrontab.sh that does all of the above commands automatically using a timestamp variable for the crontab file that is created.  If you use different IDs, you could pass the ID to the script and reference it when running the crontab command.

EDIT: Here is an example of my crontab file which includes a header section for making comments such as what was changed and when:

```

########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2011-10-29 - LTH - Created schedule
# 2011-11-22 - LTH - Added shell and path
# 2012-01-30 - LTH - Added time adjustment
########################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow command

#
# Get date/time from network time server every hour
#
0 * * * * /etc/network/if-up.d/ntpdate
#
# Import Active Directory users (run every minute)
#
0-59 * * * * /var/scripts/prod/import-ad.sh > /dev/null 2>&1
#
# Update the Global Address List for iPhone usage.
#
0 23 * * * /var/scripts/prod/gal-sync.sh > /dev/null 2>&1
#
# Partial backup of Zimbra to a local folder without taking it offline.
#
0 8-18 * * * /var/scripts/prod/rsync-online.sh > /dev/null 2>&1
#
# Backup Zimbra to a local folder, archive and store offsite.
#
0 23 * * * /var/scripts/prod/rsync-offline.sh > /dev/null 2>&1
#
# Backup individual mailboxes to a local folder, archive and store offsite.
#
0 6,12,18 * * * /var/scripts/prod/mailbox-backup.sh > /dev/null 2>&1

```LHammonds

---

### Post by PhilipSemanchuk on 2012-05-01
Thanks again, all.

It sounds like it's OK to (a) ignore the warning in the community HowTo and (b) get rid of anacron. Doing both of those things will simplify life considerably.

@SeijiSensei: It's funny that you mentioned RH because that's what we were using before moving to Ubuntu. 

@LHammonds: Yes, whenever I edit files on the server I'm in the habit of copying to foo.YYMMDD before I start editing. I rarely need those older versions but it's really nice to know they're there.

In fact, we now keep many of our server config files and scripts in Subversion now. They're checked out to a directory on the server and we symlink to them from the appropriate directories on the server (/etc/cron.daily, /etc/apache2/conf.d, etc.). It requires a little more effort to manage but it's a more robust versioning system than file copies with timestamps in the name.

---

### Post by LHammonds on 2012-05-01
> **PhilipSemanchuk said:**
> 
In fact, we now keep many of our server config files and scripts in Subversion now. They're checked out to a directory on the server and we symlink to them from the appropriate directories on the server (/etc/cron.daily, /etc/apache2/conf.d, etc.). It requires a little more effort to manage but it's a more robust versioning system than file copies with timestamps in the name.
That is a really great idea.  Thanks for mentioning it.  I use quite a few scripts but once they are in place, they don't change so having copies in my backup repository is enough for my scenario...but in a more dynamic environment, subversioning sounds like an awesome idea.

Thanks,
LHammonds

---

