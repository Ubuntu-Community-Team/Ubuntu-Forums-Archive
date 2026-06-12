---
title: "Snort - empty logs - iptables problem?"
date: 2010-02-15
forum: Security
---

### Post by jacksmash on 2010-02-15
I installed Snort (without Base), and I followed the instructions and compiled from source, etc. It seems to run just fine, but is not logging anything. So I figure it's an iptables configuration problem on my part, but I'm not really sure where to start.

I made a passive tap, and two network cards are seeing the in/out traffic. I used a virtual interface to bond the two, and I'm collecting data with SiLK over port 18001, and so I opened that port in iptables and the collection process is working fine (with SiLK). I'm just new to Snort and not sure what I need to do so it can log alerts properly.

Thanks for any insight.

---

### Post by bodhi.zazen on 2010-02-15
Snort does not log all traffic, only suspicious traffic according to the rule set you are using.

There well may be no alerts. You can hit snort with something and see what happens.

[http://www.google.com/search?q=how+to+test+snort&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=how+to+test+snort&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by jacksmash on 2010-02-15
Hi,

Yeah - I've actually ran a couple of port scans... but no luck.

$ sudo ls -l /var/log/snort/
total 0
-rw------- 1 snort snort 0 2010-02-15 13:44 snort.log.1266255870
-rw------- 1 snort snort 0 2010-02-15 17:52 snort.log.1266270758

---

### Post by bodhi.zazen on 2010-02-15
Port scans alone will not necessarily trigger an alert in snort.

See the google search I gave you ;)

---

### Post by jacksmash on 2010-02-15
Ok, thanks. I'll check out the links.

In the meantime, I thought I'd post my iptables output in case I'm missing something.

I'll report on how I make out with your suggestion.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  localhost            anywhere            tcp dpt:18001 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by jacksmash on 2010-02-15
Ok, so I followed the instructions here:

[http://www.infosecprojects.net/en/linuxtutorials/test-snort.html]("http://www.infosecprojects.net/en/linuxtutorials/test-snort.html")

When I do the nmap port scan, I notice that now a log file actually has a size > 0. E.g:

-rw------- 1 root snort 1358 2010-02-15 21:13 snort.log.1266282590

But the tutorial suggests that an alert file should be made in the directory. But that doesn't happen. And the snort.log file is unreadable (I'm assuming that's supposed to be the case).

---

### Post by bodhi.zazen on 2010-02-15
Did you follow that tutorial ?

The tutorial explains how to configure snort for testing and then instructs you to log alerts to /var/log/snorttest/alert

```
snort -c /etc/snort/snorttest.conf -l /var/log/snorttest -g snort -D[FONT=monospace]
[/FONT]tail -f /var/log/snorttest/alert
```

So ...

```
tail /var/log/snorttest/alert
```

snort.log is not listed in the tutorial.

---

### Post by jacksmash on 2010-02-15
Yeah, that was my point. I installed snort and used the shell script you provided in your tutorial, so I'm not sure if that setup the log directory the way that other tutorial requires it or not. How do I get it to create alert files properly?

---

### Post by bodhi.zazen on 2010-02-15
Is there some reason you do not wish to use base ?

Did you start snort from the command line ? Are you getting any error messages ?

Did you configure snort ?

Did you make a log file ?

---

### Post by jacksmash on 2010-02-15
> **bodhi.zazen said:**
> Is there some reason you do not wish to use base ?

Only because I'm logging into the machine remotely. So no need for an interface.

> **bodhi.zazen said:**
> Did you start snort from the command line ? Are you getting any error messages ?

This is what I run:

```
sudo snort -i bond0 -c /etc/snort/snorttest.conf -l /var/log/snorttest -g snort -D

```

No errors at all.

> **bodhi.zazen said:**
> Did you configure snort ?

I followed the configuration instructions found here:

[http://ubuntuforums.org/showthread.php?t=919472]("http://ubuntuforums.org/showthread.php?t=919472")

> **bodhi.zazen said:**
> Did you make a log file ?

Do I manually add an alert file to the snorttest directory?

Thanks for your patience.

---

### Post by bodhi.zazen on 2010-02-15
Base is a web interface, so perfect for remote access. Base also give us something you can take a screen shot of and will show you an active sensor.

You need to follow the tutorial

[http://www.infosecprojects.net/en/linuxtutorials/test-snort.html](http://www.infosecprojects.net/en/linuxtutorials/test-snort.html)

In that tutorial it explains step-by-step how to configure snort and why :

> As you can see at the end of /etc/snort/snort.conf many of the rule sets  are disabled per default, e.g. shellcode.rules. In this test I want to  trigger an alert for a shellcode rule. So we have to include these rules  in snort.conf: 
include $RULE_PATH/shellcode.rulesYou can then make an alert file with:

```
mkdir /var/log/snorttest
touch /var/log/snorttest/alert
```

---

### Post by jacksmash on 2010-02-15
OK, but I have honestly followed every step of that tutorial. I'm really not sure what I'm missing. I've even created the alert file as you've mentioned, but when I run the snort test, it just creates a snort.log file right beside it.

---

### Post by jacksmash on 2010-02-15
Hmm... ok, so I just checked my log file again and it seems to have shown an event where I logged into my Google calendar.

---

### Post by jacksmash on 2010-02-15
Yeah, so obviously I'm not cut out for this... it's getting annoying (or maybe I just need to go to bed). I downloaded the snort start up script again, and this time left the whitelist blank. Set the necessary permissions (chown/chmod)... and now snort "failed to start..." each time.

---

### Post by bodhi.zazen on 2010-02-16
> **jacksmash said:**
> Yeah, so obviously I'm not cut out for this... it's getting annoying (or maybe I just need to go to bed). I downloaded the snort start up script again, and this time left the whitelist blank. Set the necessary permissions (chown/chmod)... and now snort "failed to start..." each time.

I think you basically have two problems:

1. You did not follow the tutorial. Once you decided not to install BASE you made things more complicated then they needed to be. Once you deviated from my tutorial you are on your own to figure out snort.

When following the second tutorial, I can not tell if you configured snort properly to generate an alert to a port scanner.

You changed the configuration file, and not snort does not start, so I have no idea what you did or how to fix your issues.

My impression is that you are taking short cuts with these tutorial, or that you are not taking the time to understand what you are doing, and thus ending if failure.

You would need to post configuration files, logs, and give us information on your rule set, give us information on your network configuration, whitelist, etc, etc and honestly, I am not sure anyone will have the patience to read all those files.

Again my advice is for you to find a tutorial on snort and follow it to the letter. If you get stuck at a certain step we at least know how things should work. But when you half follow tutorials who knows ?

2. I do not think you understand how SNORT works. As I indicated before, snort does NOT log all network traffic. It analyzes traffic and generates alerts. Most alerts are potentially serious cracking attempts, such as mysql injections and what not.

By default snort will not generate an alert when you hit it with a port scanner.

Assuming you are behind a router, it is perfectly normal to see no alerts what soever. 

Next you are wanting to "test" snort. No offense, but from your previous question about iptables you do not seem to understand basic networking concepts as you have no rules in the output of iptables you posted.

You also suggested you were using a white list ? Well, if you scan from a white listed box, no alerts will be generated no matter what you do.

My advice to you is that you go back to the start and install BASE. As I indicated earlier, BASE is a web based graphical interface.

If you want to test snort you need to put your box onto the public internet or forward ports from your router, possibly put it in a DMZ and either hit it with some more malicious traffic (which you probably do not know how to do and is beyond what we support on these forums) or wait until someone does it for you.

If you are not running a public ssh server, Apache, FTP, etc you may not see anything at all.

---

### Post by jacksmash on 2010-02-16
I wasn't so worried about the iptables at first because I'm simply collecting data off of an ethernet tap. I am well aware that snort is not a data collection utility (if I thought it was... why would I have installed SiLK in the first place?), but thought based on some of the rule files I saw that it could detect port scans. Please forgive me for not knowing better.

I am in the process of configuring BASE and will let you know how it goes.

---

### Post by jacksmash on 2010-02-16
Ok, snort is running and I have base installed and configured (see attached screenshot).

I'll keep reading and see why Sensors/Total is 0/1

Thanks.

---

### Post by bodhi.zazen on 2010-02-16
Snort can detect port scans, it is just by default it does not. Thus you need to configure it to detect such scans (as explained and outlined in the second tutorial you have been following).

---

### Post by bodhi.zazen on 2010-02-16
Perfect. From that screenshot snort is working.

On the sensors line, 0/1 ...

0 = the number of sensors that have generated an alert.
1 = the total number of sensors.

You would have a problem if that line read 0 / 0

Now all you need to do is either :

1. Open your server to the public, ie DMZ or forward ports from your router and wait.

2. Learn how to send malignant packets. This second step is beyond what the Ubutnu forums will support. I did give you links to several tutorials on testing snort and there are many cracking sites, and you can try the snort forms.

Again, by default, port scanning with nmap is not sufficient.

---

### Post by jacksmash on 2010-02-16
Excellent. I'm getting alerts now, after forwarding port 80 on my router.

I've been learning meta-sploit, so I'm sure there's some fun to be had there with testing snort :D

And I guess back to my very original question... iptables seems to have had nothing to do with not receiving alerts.

Thanks for your help, and sorry for the headaches.

---

### Post by bodhi.zazen on 2010-02-16
> **jacksmash said:**
> Excellent. I'm getting alerts now, after forwarding port 80 on my router.

I've been learning meta-sploit, so I'm sure there's some fun to be had there with testing snort :D

And I guess back to my very original question... iptables seems to have had nothing to do with not receiving alerts.

Thanks for your help, and sorry for the headaches.

Not a problem, glad you got it sorted.

Now if you wish you can do away with base and go for an alternate, but you might just find base is useful.

---

