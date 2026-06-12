---
title: "suspicous entry in /var/log/auth.log"
date: 2009-10-30
forum: Security
---

### Post by fuzzy_4711 on 2009-10-30
Hi all.

I am using ubuntu 6.06.1 LTS on a server box.

By checking the /var/log/auth.log I found an entry which makes me a little nervous:
(I masked the hostname with xxx)
Oct 30 06:25:02 xxx su[13634]: + ??? root:nobody
Oct 30 06:25:02 xxx su[13634]: (pam_unix) session opened for user nobody by (uid=0)
Oct 30 06:25:02 xxx su[13634]: (pam_unix) session closed for user nobody
Oct 30 06:25:02 xxx su[13636]: + ??? root:nobody
Oct 30 06:25:02 xxx su[13636]: (pam_unix) session opened for user nobody by (uid=0)
Oct 30 06:25:02 xxx su[13636]: (pam_unix) session closed for user nobody
Oct 30 06:25:02 xxx su[13638]: + ??? root:nobody
Oct 30 06:25:02 xxx su[13638]: (pam_unix) session opened for user nobody by (uid=0)
Oct 30 06:25:31 xxx su[13638]: (pam_unix) session closed for user nobody

AFAIK this tells me that the su command for user nobody was invoked and a process i. e. with id 13638 was startet. Even it looks like it was closed pretty soon, it makes me nervous. I want to know what is going on.

On that system the root account was enabled for a while, so you could have used "su root" but I disabled it a few days ago using since I prefer using sudo when root access is needed.

Now, when I try to "su root" and provide the correct password, I get an:
su: Authentication failure
Sorry.

Could someone please enlight me with these entries and how I am able to trace them? I am interested to get an idea, what this process did or tried to do, where it comes from and if it was able to do something or not.

Thanks.

P.S.: Does someone know what is the meaning of "+ ???"?

Edit: Sorry, I pasted the line numbers in the log of my initial post - now deleted.

---

### Post by verv87 on 2009-10-30
Um, those logs don't make sense and you're trolling.

Even if they've been compromised and changed as a result -- the attacker would never leave a whoami=root.

---

### Post by fuzzy_4711 on 2009-10-30
I am not trolling - this is the output of auth.log

Thanks for serious comments.

---

### Post by Soul-Sing on 2009-10-30
> **verv87 said:**
> Um, those logs don't make sense and you're trolling.

Even if they've been compromised and changed as a result -- the attacker would never leave a whoami=root.

This log isn't that irrational or irrelevant, they appear.
If you think your server is "under attack" please install additional software to ban/ blacklist "hammering" ip's.
- failtoban/ etc.

---

### Post by QLee on 2009-10-30
[QUOTE=fuzzy_4711]Could someone please enlight me with these entries and how I am able to trace them? I am interested to get an idea, what this process did or tried to do, where it comes from and if it was able to do something or not.[/QUOTE]

It looks to me like user root su'd to user nobody, not that some user su'd to root.

I believe this can be normal behaviour. I think it happens when a database (like for find) is being updated, logrotate, and maybe also in the case of apache. Root has to start the service and then hands off to user nobody for it to run. Make sure user nobody doesn't have shell access on your system.

You might find something in cron (maybe cron.daily or monthly or...) that is happening at the timeslice of the log entry. At least, I think that would be worth checking.

I don't believe what you've shown is anything malicious but wait for others to evaluate this before you discount your log entries.

---

### Post by Soul-Sing on 2009-10-30
> i don't believe what you've shown is anything malicious
+1

---

### Post by fuzzy_4711 on 2009-10-30
> I don't believe what you've shown is anything malicious but wait for others to evaluate this before you discount your log entries.

I like your opinion which will save me a lot of work if you are right...

Nevertheless, did you see the "+ ???" before? Any idea what that means?


Thanks a lot.

---

### Post by wojox on 2009-10-30
It's your cron jobs.

---

### Post by fuzzy_4711 on 2009-10-30
> It's your cron jobs.

I grepped using:
```
sudo find /etc/cron* -exec grep -ir "nobody" {} \;
```

The output is:
1) /etc/cron.daily/find:LOCALUSER="nobody"

2) /etc/cron.weekly/popularity-contest:    HOME=/tmp su nobody -pc "sh -c /usr/sbin/popularity-contest"

It looks like the 2nd one causes the trouble. I'll deactivate it and see what will happen.

Is it confirmed - "+ ???" stands for cron?

Thanks.

---

