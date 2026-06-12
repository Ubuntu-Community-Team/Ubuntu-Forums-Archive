---
title: "Ubuntu auto patching + reboot"
date: 2023-01-18
forum: Server Platforms
---

### Post by dansss on 2023-01-18
Hi,

I've got a few instances of Ubuntu 22.04 which i'd like to have automatically patched at a specific time (eg Thursdays 10pm) and reboot if needed.

The problem is i've literally no idea what to do as my linux skills arn't the best, so I was wondering if you could do like a step by step which I can follow.

I believe my requirement will need to be a cronjob? 

current i'm doing it manually by logging into the server and running "sudo apt update" then "sudo apt upgrade", but if I can have this running automatically at Thursday 10pm and then reboot if needed, that'll be great :). Sometimes when running those commands I get a pink screen which needs a service stopped/restarted, is it possible to have that do it at the same time too?

Thank you

---

### Post by TheFu on 2023-01-18
Automatic system patching is full of possible errors.  Every few years, there's a problem that can leave a system unable to boot.
I have about 20 systems that I patch on the weekends, when a little downtime isn't bad.  

Also, having daily, automatic, versioned, backups means that if a system does not come up, I can get back to the prior state in 30-45 minutes.  There are a few different techniques to accomplish this, but those are not for people unsure of their scripting skills.

To create a script, put the commands you'd type into a file.  1 command per line.  Be certain to check for errors. Test it by running the script manually. Does it work?  Beware that the normal "session" for a user is heavy on environment variables which won't be setup under the cron environment.  Also, running cron tasks as root is easy, whereas in a terminal session, we use 'sudo -i' to run things as root with root's limited environment.  Under cron, root's environment is even less.

Don't use 'apt' in your script.  The command says you shouldn't and you shouldn't.  Use 'apt-get'.  apt-get has a batch mode, so that questions aren't asked.  Additionally, if you will be rebooting the system, then you don't need to stop/restart any network daemons. The reboot will handle that.  

Putting sudo into a script is bad form. Under cron, just run the script as root.

Ask specific questions and someone can probably provide specific answers.  As with most things Unixy, there are 500 different ways to do something.

As I said, I patch weekly, usually on Saturday mornings, using a script that I watch for the 5 minutes it takes to patch all my systems. When that script finishes, I run another script to see which systems need to be rebooted.  These scripts are based on ssh to connect to the different systems 'deployment' userid, which is setup to allow a few specific commands without a password prompt.  I suppose I could use ansible for this and it would be a little cleaner.

Almost anything can be scripted in Unix. You just need to determine how.

---

### Post by dansss on 2023-01-18
Thanks for the reply, but I should have been clearer when I went my linux skills arn't the best, I mean they're non existent for this.

Where would I put such a script etc? I know i'm asking a lot but if you could write a mini how-to which a monkey (me) could just follow, that would be awesome.  When it's written down with steps i'll be able to see whats going on and learn too rather than be confused haha

---

### Post by TheFu on 2023-01-18
You are asking a lot, especially for something that is a bad idea, when there are 1000 how-tos that already exist.
[https://tldp.org/LDP/abs/html/](https://tldp.org/LDP/abs/html/)
[https://www.howtogeek.com/101288/how-to-schedule-tasks-on-linux-an-introduction-to-crontab-files/](https://www.howtogeek.com/101288/how-to-schedule-tasks-on-linux-an-introduction-to-crontab-files/)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
 
> Where would I put such a script etc?
Anywhere you like.  There are 500+ different ways.  Whatever you pick will probably be fine.  I like to put system-level stuff in ~root/bin/ or /usr/local/bin/, but that's me. You do you.

If you just want to pay someone to do this for you, might I suggest [https://www.fiverr.com/](https://www.fiverr.com/) .  But if you want to learn, those links above are a starting place.  You might find a LUG with people to help you learn scripting too.  There is probably at least one 1-2 hr intro to shell scripting presentation happening each week. Plus there are hundreds of presentations on youtube for the same topic.  Yep, I'm seeing a bunch there, which is a more efficient method than these forums for larger topics.

---

### Post by dansss on 2023-01-18
Thanks i'll get them a read.  It's just a hardle i'm facing where there isn't as much openess to knowledge sharing as Windows community, but part of the fun I guess :)

---

### Post by TheFu on 2023-01-18
> **dansss said:**
> Thanks i'll get them a read.  It's just a hardle i'm facing where there isn't as much openess to knowledge sharing as Windows community, but part of the fun I guess :)

If you post your script, someone can make suggestions.  Around this time of year, lots of students post homework assignments, looking for someone else to do their work.  Hence the caution on my side. I don't want to break any forum rules.

---

### Post by LHammonds on 2023-01-18
Here is my incarnation of my update script for Ubuntu Server 22.04 LTS - [apt-upgrade.sh](https://github.com/LHammonds/ubuntu-bash/blob/22.04/apt-upgrade.sh)

It references a separate file ([standard.conf](https://github.com/LHammonds/ubuntu-bash/blob/22.04/standard.conf)) which is covered more in detail on my [Ubuntu Server install](https://hammondslegacy.com/forum/viewtopic.php?p=1009#p1009) page.

A crontab schedule to run it daily at 3am would look something like this:
```

0 3 * * * /var/scripts/prod/apt-upgrade.sh > /dev/null 2>&1

```

Of course, you don't have to have such a complicated script.  You could just have the following lines:

```

apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get autoremove
apt-get autoclean

```

However, when commands are run by humans, we can see when there are problems and take corrective actions....that is not so when you schedule commands to run without humans watching.

You should test the return code of each command for any errors and figure out what you want to do if you run into an error.

Sending an error report by email is nice but what if the email does not work?  You should probably log the results to a file as well so you can look at the history of these automated commands to see when it first had a problem, etc.

LHammonds

---

### Post by MAFoElffen on 2023-01-19
Such as (suggestions)
```

exit_code=0
# pre-code... check if you have an internet connection with DNS, otherwise all else is futile
# on-error set $exit_code to something I can recognize as connection related, then exit with that exit code (see below for idea)
if [ ! $Connection ] # requires other code to determine. Here for summarized example.
then 
   exit_code=404
   exit $exit_code
fi

# other code

apt-get dist-upgrade
exit_code=$?
if [ $exit_code -ne 0 ]
then
  ## Do something, because there was an error
  # ...
  ## Then exit script, bypassing any other execution
  exit $exit_code
fi

# other code
exit $exit_code

```
I believe in checking exit codes, and generating exit codes that actually mean something to me, when possible...

---

### Post by TheFu on 2023-01-19
**Updated:**

Ooops, below doesn't do what I thought it did when posting.  .....
> 
Unimportant changes, but ....
```
OUT=$(/usr/bin/apt-get dist-upgrade)
if [ $?  -ne 0 ] ; then 
 .....  do something about non-zero returns.
fi
```

Definitely need to check $? for the RC/return code.

I try to always specify the full path to any command to avoid issues/crackers.  I remember when Unix systems had both BSD and SysV commands and getting the wrong command version was common because different systems could have different PATH orders.

I'd rather see a "file not found" error in the output than get the wrong version of a command.

But automatic patching that isn't just security will eventually lead to a system that won't boot. I'm done warning.

As for the crontab, it is common to redirect stdout to /dev/null, but allow stderr to be emailed.  In this method, commands that don't have errors don't create needless email, but any errors would.  That's part of the Unix Philosophy.  Quiet for doing what is expected.  Complain loudly when any error occurs.
I never run commands from a crontab on any half hour.  I tend to use 3 or 7 min increments, avoiding :00 and :30 so a system doesn't get overloaded with too many cron tasks at once.  Learned that decades ago. Perhaps it isn't so important these days, but I still patch systems in sequence, not all at the same time, so my local apt-cacher-ng only has to pull each package once and virtual machines running on the same physical hardware don't all try to run concurrently.

Lots of other tiny things for cront and scripting learned over decades exist, but throwing them all out there at once would be overwhelming.

---

### Post by mIk3_08 on 2023-01-20
> **MAFoElffen said:**
> Such as (suggestions)
```

exit_code=0
# pre-code... check if you have an internet connection with DNS, otherwise all else is futile
# on-error set $exit_code to something I can recognize as connection related, then exit with that exit code (see below for idea)
if [ ! $Connection ] # requires other code to determine. Here for summarized example.
then 
   exit_code=404
   exit $exit_code
fi

# other code

apt-get dist-upgrade
exit_code=$?
if [ $exit_code -ne 0 ]
then
  ## Do something, because there was an error
  # ...
  ## Then exit script, bypassing any other execution
  exit $exit_code
fi

# other code
exit $exit_code

```
I believe in checking exit codes, and generating exit codes that actually mean something to me, when possible... Thanks a lot MAFoElffen. This can be helpful to me in the future. Regards and cheers.

---

