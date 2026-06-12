---
title: "System Clock Runs Slow"
date: 2008-01-20
forum: System76 Support
---

### Post by DomIncollingo on 2008-01-20
I'm running Gutsy on a Serval serp3.  The system clock (the time that displays in the panel) is running slow.  I can adjust the system clock settings so that the clock keeps very accurate time by using a command like:   sudo adjtimex --tick 10001 --frequency -3306000

The problem is that whenever I reboot, the clock adjustments are lost, and I have to run the above command again.  Is there a recommended way that I can have this setting applied automatically whenever the laptop is rebooted?

Thanks for your help.

Dom

---

### Post by Z_o-s-o on 2008-01-21
It seemed like my laptop (not a system 76) was loosing time until I told it to sync to the internet servers.

You can make sure its doing this correctly by:

1) Right clicking the time/date thing up on the top right bar.

2) Clicking adjust date and time.

3) Select the correct time zone, tell it to sync with internet servers, and choose a few servers from its list.

After that, mine has kept time perfectly.

- Z_o-s-o

---

### Post by DomIncollingo on 2008-01-21
Z_o-s-o,

Thanks for the suggestion.  Synching up to an NTP server would probably solve the problem, but I was hoping to use adjtimex so that the time would stay correct even when I do not have an internet connection.

However,  think I have stumbled upon the answer to my own question.   /etc/init.d/ contains a startup script called adjtimex, which sets the adjtimex settings to values stored in the file /etc/default/adtimex.  So by updating file /etc/default/adjtimex to contain the desired adjtimex settings, those settings can be applied every time the laptop is rebooted.  I think.....   :)

Dom

---

### Post by banewman on 2008-01-21
It could be the motherboard battery - since it looses time after shutting down - is it old?
You could write a script and make it executable and add it to the startup using those commands.
:)

---

### Post by DomIncollingo on 2008-01-21
No, the laptop is quite new - only about 7 weeks old.  So I wouldn't expect the motherboard battery to be weak.  Plus, the laptop was losing time when it was running, so I think the system clock was the culprit.

However, when made the change (described in previous post) to file /etc/default/adtimex, I noticed that the default value for adtimex tick was something like 7979.  (Can't imagine how that happened!)  I would have expected tick to be set to something like 10000, since I thought that in the pre-tickless kernel there were 10000 ticks per second.  So that might explain why the clock was running so slow.  I set ticks to 10001, and frequency to -3306000, both in the /etc/default/adtimex file and by running sudo adjtimex.   So hopefully the clock will keep fairly accurate time now.

Dom

---

### Post by thomasaaron on 2008-01-21
Are you running 64-bit Ubuntu or 32-bit? I've heard there is also a hardware clock bug with 64-bit. I've not heard if it has been fixed.

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/158849](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/158849)

You might also have a look here:
[http://locoteam.ubuntuforums.org/showthread.php?t=619927](http://locoteam.ubuntuforums.org/showthread.php?t=619927)

---

### Post by DomIncollingo on 2008-01-21
Thanks for the links.  I'll have a look at them.  But I am running the 32-bit version of Gutsy - the one that was installed on the laptop by System 76.  I didn't make any changes to the OS after I purchased the laptop, other than to install additional software from the repositories.

---

