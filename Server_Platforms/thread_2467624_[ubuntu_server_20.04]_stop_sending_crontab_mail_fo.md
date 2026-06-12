---
title: "[ubuntu server 20.04] stop sending crontab mail for all users"
date: 2021-10-02
forum: Server Platforms
---

### Post by dj201d83r6 on 2021-10-02
Hello everyone,
I need some help.
I'm managing a company server that is used also to run some scripts using crontab with hundred of ldap users. This server have already configured postfix and some scripts sends mails usinig sendmail --> postfix --> company relay servers.
Every time that one script is runned crontab, that for my undestanding use sendmail, send a mail to "ldapusername"@"servername" than it is not a valid mailbox. Some script is runned 4 times per minute.
Recently the mail admin have notified this behaviur and the only way that I found is add to each user MAILTO="" in their crontab file.
As I said before, there are hundred of users and I don't want edit their own crontab file and check it every time.

There is some way to force crontab to don't send mail globally? 
Searching a bit it seems that CentOS/Fedora can set a flag -m off on crond service but what about Ubuntu server?

---

### Post by LHammonds on 2021-10-03
You might want to take one specific email and explain exactly how it is being sent.  What you described in general does not make any sense to me.  Is the server configured to run individual cronjobs that are fired off as soon as someone logs in or does it happen regardless of login?   Is it a single, global script that runs every minute or what?   What is the "event" that sends an email and does it only send for that one user or everyone?

LHammonds

---

### Post by TheFu on 2021-10-03
postfix has a sendmail interface for compatibility.  It is still postfix ... just with "sendmail" as the name of the program.

cron sends email, if there is any output to either stderr or stdout when jobs complete.  That is how it works.  If you don't want that, have the cron tasks redirect those 2 outputs somewhere else.  /dev/null is common.  What many admins setup is to allow errors to cause email (errors == bad), but stdout gets redirected to /dev/null.

I put this header in all my crontabs, as a reminder:
```
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command --arg1 --arg2 file1 file2  > /tmp/log.file  2>&1
```
The last line has an example that sends all stdout and stderr to a log file.  This won't prevent someone from going out of their way to email the world (all users) if they know how to do it.  Also, this is for the crontabs in /var/spool/, not the ones in /etc/crontab or there-abouts.

Cron doesn't directly support running a script more than once a minute. That is the resolution of the tool.  
However, if someone puts the same script 4 times into their crontab, it could be run 4 times, or 
if they have 4 user accounts and put it into 4 separate crontabs, then it will as well. Or 
if they make 1 script that runs the mail command 4 times. These are "features".  In some of my scripts, I have a 40 second delay so they do not start up exactly on the minute, but 40 seconds later, after other scripts for that same time are usually complete.

I can see where preventing cron from emailing  might be useful for very specialized situations.
[https://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/](https://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/)

Next option,  creating a script to modify hundreds of files isn't hard. Might take 10 minutes, if you want to be careful.  You can also disable access to cron for specific users using the cron.deny and cron.allow files.  [https://help.ubuntu.com/community/CronHowto#Allowing.2FDenying_User-Level_Cron](https://help.ubuntu.com/community/CronHowto#Allowing.2FDenying_User-Level_Cron) explains.  If you are the "admin from hell", like I was, you can just disable everyone and until they contacted me about some problem and got told specifically how to be a good cron user, cron was unavailable.  If they ever broke the rules, they'd be banned and get to figure out some other method.  There are many, but I'd warn them if they had a task running 24/7 with a 15 minute loop, they'd be kicked off the system.

Being an admin can be fun, but not always.  Could it be that this is 1 user abusing the system out of ignorance?  Certainly the userid involved is part of the email.

---

### Post by dj201d83r6 on 2021-10-04
Hello LHmmonds,
thanks for answare.
Every user can create / configure by himself how many cronjob him need, no restriction, no problem on this. The issue is that after each cronjob a mail sent by crontab and I don't want that happen.


MessageSubject : Cron <"user"@"servername"> (/path/to/script.sh "params")

I just want to stop this behaviour by default. Users that need to send some mail do that inside their own scripts.

---

### Post by dj201d83r6 on 2021-10-04
Hello TheFu,
thanks for answering.

It is very clear in my mind how to stop a cronjob redirecting stderr/out to /dev/null or setting MAILTO="" before the job itself but as I wrote to LHmmonds I want to stop this behavior by default without ask to each user to redirect the output.

Below an example of a user crontab:
```
*/1  * * * *    (sleep 00; /path/to/script.sh "target1" "[options]")
*/1  * * * *    (sleep 15; /path/to/script.sh "target1" "[options]")
*/1  * * * *    (sleep 30; /path/to/script.sh "target1" "[options]")
*/1  * * * *    (sleep 45; /path/to/script.sh "target1" "[options]")


*/1  * * * *    (sleep 00; /path/to/script.sh "target2" "[options]")
*/1  * * * *    (sleep 15; /path/to/script.sh "target2" "[options]")
*/1  * * * *    (sleep 30; /path/to/script.sh "target2" "[options]")
*/1  * * * *    (sleep 45; /path/to/script.sh "target2" "[options]")


*/1  * * * *    (sleep 00; /path/to/script.sh "target3" "[options]")
*/1  * * * *    (sleep 15; /path/to/script.sh "target3" "[options]")
*/1  * * * *    (sleep 30; /path/to/script.sh "target3" "[options]")
*/1  * * * *    (sleep 45; /path/to/script.sh "target3" "[options]")


```

This means that 12 mails will be sent every minute because the script has output.

I've already build a little script that change all crontab files to avoid it but it is not a real "solution" it is workaround. I would like to say to crontab "Please don't send mail" as a global configuration.

```

#!/usr/bin/env bash


FILEPATH='/var/spool/cron/crontabs/';
for FILENAME in $(ls ${FILEPATH} ); do
    STRING="$(cat ${FILEPATH}${FILENAME} | grep -Eo "^(MAILTO=\"\")$")";
    if [[ $STRING == "" ]]; then
        sed -e 's|# m h  dom mon dow   command|# m h  dom mon dow   command\nMAILTO=""|g' -i ${FILEPATH}${FILENAME};
    fi;
done

```

---

### Post by TheFu on 2021-10-04
If other versions of cron have a switch to disable sending any email by default, have you considered using that software instead?
cronie vs Vixie - is that the difference?  [https://github.com/cronie-crond/cronie](https://github.com/cronie-crond/cronie)

Seems you have a solution, though using 'ls' to create a list of files is a well-documented, bad idea.  Use file globbing that is built into bash.

No need to use "cat" either.  grep can read files directly.  Really wish training classes would stop showing 
```
$ cat $file |grep -c "MAIL"
```
as an example.  Use grep directly.  No need to waste an extra process.  I get more use from **tac** than I **cat**.

```
$ if [[ 0 -eq $(grep -Ec "MAILTO=" [COLOR="#FF0000"]$file)[/COLOR] ]] ; then
   sed ....
fi
```
I try to use numeric comparisons when possible. Didn't test that code. There's probably some tiny issue that I missed.
What's the harm in cron spamming the people who setup the cron tasks?  That gives them an incentive to to it smarter.  Let the email guys complain, if it is a problem.  It isn't like the email is going to the world, unless you have shared accounts or don't have the /etc/aliases setup.

If I had a system with hundreds of users and more than one person had setup running 4 tasks every minute, we'd have a chat about system efficiency with that person and their boss.  At a minimum, I'd teach them about this thing called a "loop".  I have one monitoring task that runs every 2 minutes. Only get email when there is an issue ... via stderr.  All stdout goes to /dev/null.   That's the way that cron has worked 40+ yrs.

---

### Post by dj201d83r6 on 2021-10-04
You are right at 100%, some things should be managed in other way.
However all the users are network engineers (like me) with different experiences with Linux. Someone have never used Linux before, some other known just something, someone else have programming background an so on.
I'm using Linux since 2006 but honestly I'm not an expert.
I built very complex scripts using my knowledge probably in the wrong way ignoring best practices. As I can say, they just works.


The company, was build using Microsoft only. This is my personal battle.
7 years ago, when I started working for them, there was 0 Linux servers and there was no way to have them. With hard work, today we can have on-demand Linux servers but is still missing a Linux system engineer.
So if the mail guys complain for something caused "by me" I have to try to fix in some way.


I've very appreciate your time and your explanations.
I'll try to use your suggestions as better that I can.

---

### Post by SeijiSensei on 2021-10-05
Do the users actually create a cron job from scratch, or do they use some kind of script or tool to generate the cron file? If you can somehow add

```
MAILTO=/dev/null
```

to the top of each script, that should stop the mail.

Perhaps a better solution is to redirect all the mail to an administrative account for later review if needed.

```
MAILTO=crons@server
```

with an entry in /etc/aliases that points the alias "crons" to some appropriate mailbox.

---

