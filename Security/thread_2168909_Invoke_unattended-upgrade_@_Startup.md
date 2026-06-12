---
title: "Invoke unattended-upgrade @ Startup?"
date: 2013-08-19
forum: Security
---

### Post by BuntuSeriously on 2013-08-19
Hello folks!

Have a simple (?) question for the community tonight; and hope there might be a solution hangin' around out there ;o)

Here 'tis:

Would like, in my significant ignorance, to create a simple startup script which will call "unattended-upgrade" located in /usr/bin for a quick run after each boot.

The problem which I'm wrestling with is the fact that

[INDENT]a) I can't nail down the basic syntax to call an inline sleep command ("sleep 600s") in conjunction with "unattended-upgrade" to allow the system to settle out & get a net connection before running the server check; and

b) I don't know what must be done to allow the "unattended-upgrade" script to execute @ startup without a system password...
[/INDENT]
 
For the record, I've also tried messing around cron/anacron as posted in the relevant snippet over here:

[http://www.richud.com/wiki/Ubuntu_Enable_Automatic_Updates#Forcing_a_rerun_to_test_cron_working](http://www.richud.com/wiki/Ubuntu_Enable_Automatic_Updates#Forcing_a_rerun_to_test_cron_working)

...but this approach requires root as well to get going; and seems to have a rather messy way of issuing the necessary "sleep" delay before firing off unattended-upgrade.

If this approach of mine is positively "Monty Python" in the final analysis, I'm all ears for the alternatives -- just thought it would be nifty to be able to make a quick autostart script which I could simply drop onto any of my machines and be done with it!


Thanks a bunch ;)

---

### Post by CharlesA on 2013-08-19
Why not just run:

```
/etc/cron.daily/apt
```

In a root crontab with @reboot?

If the machine is running 24/7, there is no need to check for updates after a reboot and if the machine is not on very often, checking for updates manually might be easier.

---

### Post by BuntuSeriously on 2013-08-19
Thanks for the tip here, CharlesA.

I'll give it a spin & get back ;)

---

### Post by TheFu on 2013-08-20
> **CharlesA said:**
> Why not just run:

```
/etc/cron.daily/apt
```

In a root crontab with @reboot?

If the machine is running 24/7, there is no need to check for updates after a reboot and if the machine is not on very often, checking for updates manually might be easier.

Very nice suggestion - probably better than mine. Here it is anyway ....
Edit the old-school /etc/rc.local file with your script. This runs as root at startup.  The common way to run this is:
```
/usr/bin/apt-get update && /usr/bin/apt-get dist-upgrade
```
This will only try to get the newest software is getting the package list updates worked.  I prefer dist-upgrade over "upgrade" to stay with a newer kernel, when possible.  On an LTS release, this has never caused any issues.  Might also want to check whether /var/run/reboot-required exists - if so, reboot.  That file gets created when a newly installed package needs a reboot to become active. 

Always fully specify the path to commands, since trusting the PATH is dangerous, especially for root. ;)

rc.local should run last or almost last in the bootup sequence.

---

### Post by BuntuSeriously on 2013-08-20
@TheFu:

Thanks for your help in working this thing through.

In addition to the suggestions which you and CharlesA have made here, it looks as though I might need to look at running "unattended-upgrade**_s_**" in this instance; as directly running the "non-plural" script seems to do nothing apart from making yet another bogus "No packages found that can be upgraded unattended" notation in "unattended-upgrades.log"

<sigh>

Thanks again.  I might be back with a couple of questions, if needed ;)

---

### Post by CharlesA on 2013-08-20
The unattended-upgrades script will only apply security updates by default. Also, keep in mind that updates aren't usually released every day.

---

### Post by cariboo on 2013-08-20
One addition to the command that TheFu gave us should be instead of:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

and a -y to automagically install the updated package without any user intervention:

```
sudo apt-get update && sudo apt-get -y dist-upgrade
```

---

### Post by BuntuSeriously on 2013-08-21
Awesome.

Putting it all together; feeling as though I'm geting a handle on things here.

Thanks again; and have a great day!

---

### Post by BuntuSeriously on 2013-10-19
Well, after two months of occasionally watching the behavior of my install (and several missed automatic updates), I finally took the bull by the horns and would like to pass along the following for anyone who may happen upon this thread:


[LIST=1]
[*]Calling " /usr/bin/apt-get update " LOADS the database which all actual system update applet ops scan for pending updates to be installed; and, therefore, 
[*]One then, thereafter, call anything like " /usr/bin/unattended-upgrade " or " /usr/bin/apt-get dist-upgrade " or whatever else may apply to the actual download and install processing on the target machine. 
[/LIST]

Simple note here; but hopefully handy for someone ;o)

---

