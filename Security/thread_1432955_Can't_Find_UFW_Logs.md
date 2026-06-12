---
title: "Can't Find UFW Logs"
date: 2010-03-18
forum: Security
---

### Post by caffeinated blood on 2010-03-18
I cannot find one single UFW event anywhere. I have researched this and see that others have trouble finding these logs too. I have looked in every /var/log there is and I can't find one event. I have UFW enabled, default deny and logging set to medium from a previous logging low(in hopes this would create more events to be seen). In terminal, UFW is shown as active. I have been using Ubuntu for more than a year now and I recall seeing UFW events with every session in some /var/logs in Ubuntu 9.04 - I'm running 9.10 now. I have also tried looking throughout the system files and have found nothing. Is UFW not working properly or could I just not be experiencing any firewall events(not likely)?

---

### Post by OpSecShellshock on 2010-03-18
Are you behind a hardware firewall with no ports forwarded? Any unsolicited ingress traffic might be getting dropped without hitting your computer at all, in which case there wouldn't be any events. It's also possible that unsolicited ingress traffic that gets dropped simply doesn't get logged at all, since it's not an issue.

---

### Post by bodhi.zazen on 2010-03-18
What are you expecting to see exactly ? What kind of events ?

See the man pages, logging section, for what the log levels mean exactly :

[http://manpages.ubuntu.com/manpages/lucid/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/ufw.8.html)

When setting the log level to medium, and the running ssh localhost,

I see an immediate log in /var/log/messages

Same with ping localhost ...

What traffic do you feel is not logged ?

---

### Post by caffeinated blood on 2010-03-18
I'm connected to a wireless router-bridge in a hotel(long-term stay). I do not have a laptop and I use my desktop which has no wireless card so I connect to this router via an ethernet cable. I get internet service by accepting a leased time-frame from the ISP. I have file sharing and remote services packages removed for security purposes, including openssh. It's just been recently that there are no logged events occurring. I used to see UFW BLOCK events in every session and now I can't find one event. These events would show UFW blocking other users on the network. I understand the logging levels. I normally set to LOW, but I only moved the setting up to MEDIUM to see if that would create an event. I just expect to see something logged that tells me UFW is doing what it's set to do.

---

### Post by bodhi.zazen on 2010-03-19
did you try ping localhost or ssh localhost ?

---

### Post by caffeinated blood on 2010-03-19
I just tried ping/ssh localhost and UFW is working as I figured, but nothing was logged. I moved the logging level to HIGH and am now getting a few events shown in /var/logs. I don't know if this solves my question and I'm not sure if I had UFW logging set to HIGH when I previously saw events with every session.

---

### Post by Quannah on 2010-05-09
I'm having the same issue. I know UFW is working (e.g. it denies ssh on port 22), but I used to have lots of log messages with BLOCKED etc. messages. This was about two weeks ago on a VPS with Ubuntu 8.04. I was actually surprised by the amount of intrusion attempts since it was a completely fresh VPS.

I decided to do a clean 10.04 install, and everything works fine. I installed UFW, with:
sudo ufw default deny
sudo ufw allow http
sudo ufw allow 12345/tcp # some port for SSH
sudo ufw enable
sudo ufw logging on

Before on 8.04, "sudo cat /var/log/messages | grep UFW" would give lots of UFW log entries (mostly BLOCKED connections). Now the exact same UFW setup gives zero log messages, even after a week at medium logging level. Running an nmap scan on my VPS with logging level 'full' produces no log messages.

I understand that log messages don't directly increase security, but something must have changed somewhere. A similar question is [here]("http://ubuntuforums.org/showthread.php?t=1431883"). Any ideas?

---

### Post by bodhi.zazen on 2010-05-09
> **Quannah said:**
> I'm having the same issue. I know UFW is working (e.g. it denies ssh on port 22), but I used to have lots of log messages with BLOCKED etc. messages. This was about two weeks ago on a VPS with Ubuntu 8.04. I was actually surprised by the amount of intrusion attempts since it was a completely fresh VPS.

I decided to do a clean 10.04 install, and everything works fine. I installed UFW, with:
sudo ufw default deny
sudo ufw allow http
sudo ufw allow 12345/tcp # some port for SSH
sudo ufw enable
sudo ufw logging on

Before on 8.04, "sudo cat /var/log/messages | grep UFW" would give lots of UFW log entries (mostly BLOCKED connections). Now the exact same UFW setup gives zero log messages, even after a week at medium logging level. Running an nmap scan on my VPS with logging level 'full' produces no log messages.

I understand that log messages don't directly increase security, but something must have changed somewhere. A similar question is [here]("http://ubuntuforums.org/showthread.php?t=1431883"). Any ideas?

Is this a VPS or Desktop ?

---

### Post by Quannah on 2010-05-09
This is on a VPS...

---

### Post by bodhi.zazen on 2010-05-09
Is your VPS configured to log ? 

I suggest you use syslog-ng to log kernel messages in a VPS.

```
sudo apt-get install syslog-ng
```

---

### Post by Quannah on 2010-05-09
Thanks for your reply, bodhi.zazen.

My system is using the default rsyslog, and events are being logged to /var/log/syslog. (e.g. I see page not found messages, cron runs...).

I should be able to just keep using rsyslog, right? I just read [here]("https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/555852") that with UFW 0.30 and rsyslog in 10.04, UFW automatically logs to /var/log/ufw.log.
But my ufw.log, although present, is 0 bytes. And I understand UFW messages should also still be sent to /var/log/messages, right?

I haven't changed rsyslog configuration options before, I'm not sure if I can do something useful there... Any tips?

---

### Post by bodhi.zazen on 2010-05-09
kernle logging in a VPS can be tricky or broken.

I have had the best success with syslog-ng

At least I know syslog-ng works with iptables ...

---

### Post by bodhi.zazen on 2010-05-11
OK, I found the issues with UFW in OpenVZ templates :

[http://blog.bodhizazen.net/uncategorized/how-to-use-ufw-in-openvz-templates/](http://blog.bodhizazen.net/uncategorized/how-to-use-ufw-in-openvz-templates/)

---

### Post by u1106 on 2010-06-04
> **Quannah said:**
> 
rsyslog in 10.04, UFW automatically logs to /var/log/ufw.log.


I have Kubuntu 10.04. The default configuration logs to both /var/log/ufw.log and /var/log/kern.log

> **Quannah said:**
> 
But my ufw.log, although present, is 0 bytes. 


Change the log level to high, and I'm sure it will start to grow

$ sudo ufw logging high


> **Quannah said:**
> 
And I understand UFW messages should also still be sent to /var/log/messages, right?


Not at least in the Kubuntu 10.04 default configuration.

> **Quannah said:**
> 
I haven't changed rsyslog configuration options before, I'm not sure if I can do something useful there... Any tips?

I don't think you have to do anything there. But if you are interested, you can install rsyslog-doc package 
and browse to [file:///usr/share/doc/rsyslog-doc/html/rsyslog_conf_examples.html](file:///usr/share/doc/rsyslog-doc/html/rsyslog_conf_examples.html). 
Under selector lines there are some useful examples. 
The full rules are under [file:///usr/share/doc/rsyslog-doc/html/rsyslog_conf_filter.html](file:///usr/share/doc/rsyslog-doc/html/rsyslog_conf_filter.html)

The filters are included from /etc/rsyslog.d/*

---

### Post by bodhi.zazen on 2010-06-04
> **u1106 said:**
> I have Kubuntu 10.04. The default configuration logs to both /var/log/ufw.log and /var/log/kern.log

Change the log level to high, and I'm sure it will start to grow

$ sudo ufw logging high

That (rsyslog) does not work in an OpenVZ VPS. You need to install syslog-ng, see the link I gave and/or the openvz mailing list.

[http://blog.bodhizazen.net/linux/how-to-use-ufw-in-openvz-templates/](http://blog.bodhizazen.net/linux/how-to-use-ufw-in-openvz-templates/)

---

### Post by caffeinated blood on 2010-06-20
Hi all! It's been awhile since I've looked at my post,but after installing and working with Lucid I've found another issue with the UFW logging. In previous Ubuntu distros I've always seen either a [UFW AUDIT] [UFW ALLOW] or [UFW BLOCK] in response to firewall events. Well in Lucid I only see [UFW AUDIT] on events that in previous distros would show as [UFW BLOCK] - So is a block the same as an audit(following input rules)?

---

### Post by Quannah on 2010-07-17
Thanks for the replies.
I sticked with rsyslog, and now after I upgraded the system, the ufw logs started to fill. There must have been something that prevented the logging. I didn't change any settings, only a "sudo aptitude full-upgrade".

Before doing the upgrades, even with ufw logging set to full nothing showed, now I'm back to 'sudo ufw logging low' and getting new log entries.

I also noticed [UFW AUDIT] entries, I can't tell you what the difference is, but I'm also seeing BLOCK and ALLOW entries, so they're not the same.

---

