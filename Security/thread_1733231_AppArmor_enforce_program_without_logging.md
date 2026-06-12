---
title: "AppArmor enforce program without logging"
date: 2011-04-19
forum: Security
---

### Post by BkkBonanza on 2011-04-19
I have a program that generates large amounts of apparmor log messages. I'm happy to enforce restrictions on the program but I really don't want it to fill my log with messages every time it attempts to read a file.

Is there a way to let it enforce restrictions but not log denials?

There should be.

---

### Post by rookcifer on 2011-04-19
> **BkkBonanza said:**
> I have a program that generates large amounts of apparmor log messages. I'm happy to enforce restrictions on the program but I really don't want it to fill my log with messages every time it attempts to read a file.

Is there a way to let it enforce restrictions but not log denials?

There should be.

If it is logging denials then you have not setup the profile properly.  The denials mean the program is not being allowed to do something that it might need to do.  

Or, are you saying that the program works fine regardless of these denials? If so, then I can think of two things:

1) Install auditd.  It will keep all the apparmor logs in their own separate log file so they wont be filling up /var/log/messages.  You can achieve the same result by configuring your rsyslog config file, but it's more complicated.

2)You might be able to explicitly "deny" these operations within your apparmor profile.  If you do this, it shouldn't log it every time it denies it.

---

### Post by Rubi1200 on 2011-04-19
I know this sounds like a silly question and is probably stating the obvious, but is the profile in complain or enforce mode?

If the former, it is likely to produce a lot of messages depending on what you are trying to restrict.

---

### Post by BkkBonanza on 2011-04-19
It's in enforce mode. The app is actually working fine even though denied access to some things. The app is Skype - which likes to go on rampages reading stuff I don't want it to have access to. 

So I've explicitly denied certain things. It still works ok but it fills the log like you wouldn't believe. Basically entries every few seconds 24/7 and they seem to end up in 3 log files so it's a bit overdone really. 

I'll look into some rsyslog config to filter them out to another file. I've done that before so it shouldn't be too hard.

Thanks!

---

### Post by BkkBonanza on 2011-04-23
I got this set up and working so I'm going to post what I did here for others.
I just copied the same code as comes default with UFW and modified for apparmor. Now all my apparmor messages go into one log and don't polute the (3) others with junk.

I created a file /etc/rsyslog.d/30-apparmor.conf containing,

```
# Log kernel generated apparmor log messages to file
:msg,contains,"apparmor" /var/log/apparmor.log

# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated apparmor log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
& ~

```

That last line can be commented if you want the messages to flow as usual but I wanted it cut down to just the one log file. You have to restart rsyslog but I rebooted anyway since I had other changes pending.

---

### Post by Dave_L on 2011-04-23
Thanks for the information on apparmor logging.  I was planning on enabling some apparmor profiles, but didn't want the system logs to be cluttered with apparmor messages.

I have one question. There's a directory /var/log/apparmor/. Is that used for anything on Ubuntu?

----
Edit

I found that /var/log/apparmor/ is listed in the "installed files" for apparmor-utils. Maybe it's used by one or more of the programs in that package.

---

### Post by BkkBonanza on 2011-04-24
I noticed there was a /var/log/apparmor directory created but I've never seen anything in there. I prefer to keep my logs all in /var/log but I can see that when rotating occurs and there are multiple copies it's a bit cluttered. I think either way is good.

---

### Post by bodhi.zazen on 2011-04-25
It is a shame you need to disable logging to quiet apparmor.

IMO it would be nice if apparmor had a few more features and a few tools to help manage alerts.

Perhaps report it as a bug or feature request ?

---

### Post by BkkBonanza on 2011-04-26
Good idea. I added it in launchpad. I couldn't find a place for feature requests so I marked it as feature request and submitted it in bugs section. Maybe some day we'll have the option "per profile logging".

PS. I've already got 4.3MB in the apparmor log in 2 days...

---

### Post by Dave_L on 2011-04-26
In addition to the preceding, if log file rotation is desired, a file /etc/logrotate.d/apparmor with the following contents could be added:

```
/var/log/apparmor.log {
   rotate 4
   weekly
   compress
   missingok
}
```

The specific logging options could vary.

---

### Post by bodhi.zazen on 2011-04-26
> **BkkBonanza said:**
> Good idea. I added it in launchpad. I couldn't find a place for feature requests so I marked it as feature request and submitted it in bugs section. Maybe some day we'll have the option "per profile logging".

PS. I've already got 4.3MB in the apparmor log in 2 days...

I agree. Apparmor makes too much noise in the logs.

I think the strategy is to allow everything that is "normal" and thus make the logs as quiet as possible, but logs are still too noisy to be useful.

Perhaps a log level, similar to iptables, or a limit.

Do you have a link to your launchpad feature request ? I will add those two suggestions.

---

### Post by BkkBonanza on 2011-04-26
Here is the link.
[https://bugs.launchpad.net/apparmor/+bug/770671](https://bugs.launchpad.net/apparmor/+bug/770671)

Someone posted a comment that confuses me more about how rules affect logging. I thought my log messages were from denied activity but he suggests logging only occurs when "audit" is added to a deny rule. I don't know as I don't have "audit" anywhere in my rules but I get a lot of log messages that are tagged with "audit".

---

### Post by rookcifer on 2011-04-26
> **BkkBonanza said:**
> Here is the link.
[https://bugs.launchpad.net/apparmor/+bug/770671](https://bugs.launchpad.net/apparmor/+bug/770671)

Someone posted a comment that confuses me more about how rules affect logging. I thought my log messages were from denied activity but he suggests logging only occurs when "audit" is added to a deny rule. I don't know as I don't have "audit" anywhere in my rules but I get a lot of log messages that are tagged with "audit".

From the apparmor.d man page:
> 
       **deny** Specifies that permissions requests that match the rule should be denied without logging. Can be combined with 'audit' to enable logging.

So adding a specific "deny" rule for the error in question should make apparmor stop logging it.  You can also see this in action by looking at the included Firefox profile.  It has a section that looks like this:

```
**# noisy**
  deny /usr/lib/firefox-4.0/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,
  deny /usr/lib/xulrunner-*/components/*.tmp w,
  deny /.suspended r,
  deny /boot/initrd.img* r,
  deny /boot/vmlinuz* r,
  deny /var/cache/fontconfig/ w,
  deny @{HOME}/.local/share/recently-used.xbel r,

```

I presume "noisy" means these are errors that can be denied without any functionality issues and thus the author doesn't want them to be logged.

If you have specifically "denied" the errors in question in your profile and it still logs, you might have a legit bug report.

---

### Post by BkkBonanza on 2011-04-26
Perhaps I do. The log messages look like this, though they do vary sometimes.

Apr 27 04:23:48 localhost kernel: [231845.192108] type=1400 audit(1303853028.402:23373): apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/skype" name="/proc/1389/task/" pid=1390 comm="skype" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000

And doing a search of "audit" in my skype profile shows that the word isn't anywhere in the file. I didn't check the standard includes.

---

### Post by bodhi.zazen on 2011-04-26
I usually allow read only access to that kind of thing, to quiet the logs.

/proc/*/task/* r,

---

### Post by Dave_L on 2011-05-11
I've redirected apparmor messages to /var/log/apparmor.log, as described above.  (But I used the search string "audit(", since "apparmor" isn't present in my messages.)

I've also installed apparmor-notify to get popup notifications of denials. Since /usr/bin/apparmor_notify looks in /var/log/kern.log for the messages, I had to make the following change:

```
Edited /etc/X11/Xsession.d/90apparmor-notify and changed:
    /usr/bin/apparmor_notify -p -s 1 -w 60
to:
    /usr/bin/apparmor_notify -p -s 1 -w 60 -f /var/log/apparmor.log

```

Maybe all this stuff should be placed in a wiki.

---

