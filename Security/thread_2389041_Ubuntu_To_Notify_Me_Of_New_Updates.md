---
title: "Ubuntu To Notify Me Of New Updates"
date: 2018-04-10
forum: Security
---

### Post by open4epl on 2018-04-10
Is there any way for Ubuntu to notify me of any new updates? I checked for new updates & there was some & it didn't notify me about them.

---

### Post by deadflowr on 2018-04-10
What are your settings in Software and Updates >> Updates?

---

### Post by open4epl on 2018-04-10
See Attachment Image. Those are the settings I set.

---

### Post by deadflowr on 2018-04-10
one of two things, maybe

1) The updates came after you booted ( or started) and are now newer than when the system ran the last check.


2) Check the no-show-notifications settings to see if it off (or on in this case
```
gsettings get com.ubuntu.update-notifier no-show-notifications
```
The default should be false.
if set to true then to change back run it with
```
gsettings reset com.ubuntu.update-notifier no-show-notifications
```
But in case that's not resetting it to false you can run
```
gsettings set com.ubuntu.update-notifier no-show-notifications false
```


Personally I would go with 1), since that's a more common reason.

---

### Post by open4epl on 2018-04-10
I'm currently from the installation media. I tried the code & got: 

```
ubuntu@ubuntu:~$ gsettings get com.ubuntu.update-notifier no-show-notifications
false
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ gsettings set com.ubuntu.update-notifier no-show-notifications falsegsett
unknown keyword:
  falsegsett
```
  ^^^^^^^^^^

What's that mean?

---

### Post by open4epl on 2018-04-10
Will the settings shown in the image have me notified of any new updates?

---

### Post by deadflowr on 2018-04-10
> **open4epl said:**
> I'm currently from the installation media. I tried the code & got: 

```
ubuntu@ubuntu:~$ gsettings get com.ubuntu.update-notifier no-show-notifications
false
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ gsettings set com.ubuntu.update-notifier no-show-notifications falsegsett
unknown keyword:
  falsegsett
```
  ^^^^^^^^^^

What's that mean?

Means what it says.
No word exists for falsesgsett.

Anyway, it's pointless to run it on a live session.
Are you trying to do this all on a live session?

---

### Post by open4epl on 2018-04-10
If live session is "running Ubuntu from installation media" yes. :) It won't work correctly unless I install it to the PC? :-k

---

### Post by deadflowr on 2018-04-11
> **open4epl said:**
> If live session is "running Ubuntu from installation media" yes. :) It won't work correctly unless I install it to the PC? :-k

Yes.
Live sessions aren't designed to be updated, as updates are lost at shutdown.

---

### Post by open4epl on 2018-04-11
I have Ubuntu to system. It's set to false:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.


eddie@eddie-HP-Notebook:~$ gsettings get com.ubuntu.update-notifier no-show-notifications
false

Does that mean I'll be notified of any new updates & the settings in my last picture, will those settings get me notified of any new updates too?

---

### Post by TheFu on 2018-04-11
I think the default action for all Ubuntu desktops is for update notifications to be provided once a day.
There is a tool, update-notifier, installed by default which controls updates.
It is run from anacron using the daily event whenever that happens on your system(s).  On mine, it happens at 6:25am.

My only knowledge about this is because I remove the notifications and don't wish to be nagged other times.

A system that isn't installed really shouldn't notify about updates, since there isn't anywhere for them to be stored.  It isn't like a read-only ISO can be modified.

---

### Post by open4epl on 2018-04-11
Is there a way to find out when it happens on mine?

---

### Post by TheFu on 2018-04-11
After you install, yes. Just look for when anacron runs the daily tasks.

It is in the /etc/crontab file.
```
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```

That shows 6:25am.

If you look in the /etc/cron.daily/ directory, there is an **update-notifier-common** script. That is what does the updates.

Then ... there is some GUI task, which is dependent on what GUI you run that decides what to do, if anything, with that information.  I don't use a DE, so can't suggest what the popular Ubuntu DEs might or might not do.

But ... those files and directories above work on Ubuntu servers and desktops.  If you want the updates to happen more often, there is a cron.hourly/ directory.  Mine is empty currently. According to my crontab file, it runs at 17 min after every hour.  There are cron.weekly/ and cron.monthly/ directories too.  On my system, these get notified about new releases as they become available ... so 14.04 --> 16.04 --> 18.04 reminders will happen on my systems. I only use LTS versions. There is a setting that controls which sorts of releases each system is notified about.  LTS, 6 month or development branches.

As you can see, this quickly becomes a rabbit hole.

---

### Post by open4epl on 2018-04-11
My daily file says:

#!/bin/sh


set -e


[ -x /usr/lib/update-notifier/package-data-downloader ] || exit 0


# Try to rerun any package data downloads that failed at package install time.
/usr/lib/update-notifier/package-data-downloader

---

### Post by TheFu on 2018-04-11
So you see it is a rabbit hole. Follow it if you like.  Be certain to read the manpage for every command to understand what they do along the way.

This is how Unix knowledge is gained, BTW.

---

