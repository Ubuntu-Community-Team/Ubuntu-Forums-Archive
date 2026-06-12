---
title: "Runaway Outgoing port 123 connections"
date: 2012-04-03
forum: Security
---

### Post by starz677 on 2012-04-03
I have a server running 10.04 LTS and there has been a very long ongoing problem with outgoing packets on port 123.

There was a very good thread on this but it was closed.

[http://ubuntuforums.org/showthread.php?t=1145095](http://ubuntuforums.org/showthread.php?t=1145095)

What's been tried...
**[COLOR=SeaGreen]sudo watch -n .5 lsof -i :123[/COLOR]**

**[COLOR=SeaGreen]'lsof -i :123 >> ~/Desktop/lsof_123'[/COLOR]**

[COLOR=SeaGreen][B]sudo -i
while true  ; do netstat -nalutp | grep ':123 ' ; sleep 1 ; done[/B][/COLOR]


One problem is that the source port seems to be random while the destination port is always 123.  I'm not sure if the commands above monitor the Source or Destination port.

Any suggestions are appreciated.

---

### Post by Doug S on 2012-04-03
I saw your other posting, in the thread that got closed. I searched and found this one.
 
It makes sense that the source port would be changing. It sounds as though you have ntpd running. Is it?```
ps aux | grep ntp
```
 
Edit: I realize that on the other post you said the service was not running, but it would be called ntpd and that thread referred to ntp and ntpdate.

---

### Post by bab1 on 2012-04-03
> **starz677 said:**
> I have a server running 10.04 LTS and there has been a very long ongoing problem with outgoing packets on port 123.

There was a very good thread on this but it was closed.

[http://ubuntuforums.org/showthread.php?t=1145095](http://ubuntuforums.org/showthread.php?t=1145095)

What's been tried...
**[COLOR=SeaGreen]sudo watch -n .5 lsof -i :123[/COLOR]**

**[COLOR=SeaGreen]'lsof -i :123 >> ~/Desktop/lsof_123'[/COLOR]**

[COLOR=SeaGreen][B]sudo -i
while true  ; do netstat -nalutp | grep ':123 ' ; sleep 1 ; done[/B][/COLOR]


One problem is that the source port seems to be random while the destination port is always 123.  I'm not sure if the commands above monitor the Source or Destination port.

Any suggestions are appreciated.
I run 10.04 servers and have not seen this as a long standing problem.  The thread you refer to never established that there really was a problem.  The OP was repeatedly asked to show the logs that show the problem.  None were forthcoming.


I have problems with your description.  At first you say you have traffic leaving your host using port 123> problem with *outgoing* packets on port 123

But then you seem to say differently> One problem is that the source port seems to be random while the destination port is always 123

So the question(s) seem to be.  Could it be that the remote host initiates this?  When you mean destination, do you mean the remote host or your host (local)?  What logs to you have that show the traffic (how did you discover this)? 

To answer your question(s): 
Netstat shows both the remote and the local host ports (and IP address)

lsof doesn't relate to TCP ports at all.  From the man pages ```
lsof lists all open **files** belonging to all active processes...
```

What is the problem you are seeing?  What logs can you show us to verify this really is a problem?  What apps have you installed that did not come from the repos?

---

### Post by starz677 on 2012-04-03
I was able to determine tonight that Java was the source of the outgoing calls.

Also, the NTP outgoing requests were all ipv6.   Nothing else was using ipv6.

I disabled ipv6 and for the first time in a long time, the outgoing ntp requests have ceased.


This seems to have put a band aid on the problem.   But, I'm still not sure WHY those outbound requests were being generated.

---

### Post by starz677 on 2012-04-03
> **Doug S said:**
> I saw your other posting, in the thread that got closed. I searched and found this one.
 
It makes sense that the source port would be changing. It sounds as though you have ntpd running. Is it?```
ps aux | grep ntp
```Edit: I realize that on the other post you said the service was not running, but it would be called ntpd and that thread referred to ntp and ntpdate.

Maybe in my case, unlike the OP, I DID have an ntp service running ?

1000      5143  0.0  0.0   3320   800 pts/0    S+   22:48   0:00 grep --color=auto ntp

---

### Post by uRock on 2012-04-03
Moved to *Security Discussions*

---

### Post by Doug S on 2012-04-04
Glad you got it sorted out.
 
For this:> Maybe in my case, unlike the OP, I DID have an ntp service running ?
 
1000 5143 0.0 0.0 3320 800 pts/0 S+ 22:48 0:00 grep --color=auto ntp
That is just the grep command seeing itself in the list of processes. There would have been another entry if ntpd had been running.
 
By the way, I run with ipv6 disabled also (disabled right in the grub file).

---

### Post by bab1 on 2012-04-04
> **starz677 said:**
> Maybe in my case, unlike the OP, I DID have an ntp service running ?

1000      5143  0.0  0.0   3320   800 pts/0    S+   22:48   0:00 **[COLOR="Red"]grep[/COLOR]** --color=auto ntp
;-)

This is just you using grep to look for ntp.  To suppress this you can use grep -x as in ```
ps aux|grep -x ntp
```

---

### Post by Doug S on 2012-04-04
> **bab1 said:**
> ;-)
 
This is just you using grep to look for ntp. To suppress this you can use grep -x as in ```
ps aux|grep -x ntp
```
bab1: wouldn't your suggestion supress the desired output also? Example (using cron, because I am not running ntpd):```
doug@s15:~$ ps aux | grep cron
root      9406  0.0  0.0  19104  1040 ?        Ss   Apr02   0:00 cron
doug     19048  0.0  0.0   9376   936 pts/3    S+   21:12   0:00 grep --color=auto cron
doug@s15:~$ ps aux | grep -x cron

```

---

### Post by bab1 on 2012-04-04
> **Doug S said:**
> bab1: wouldn't your suggestion supress the desired output also? Example (using cron, because I am not running ntpd):```
doug@s15:~$ ps aux | grep cron
root      9406  0.0  0.0  19104  1040 ?        Ss   Apr02   0:00 cron
doug     19048  0.0  0.0   9376   936 pts/3    S+   21:12   0:00 grep --color=auto cron
doug@s15:~$ ps aux | grep -x cron

```

Yes you're correct.  it's been awhile.  I used to do something like this ```
bruce@malibu:~$ ps aux | grep bash |grep -v color
bruce     4559  0.0  0.0  21436  4248 pts/0    Ss   21:27   0:00 bash

```

I remember someone mentioning a switch that would suppress the greping itself.  I did a quick look and thought it was -x.  I must have remembered wrong.  :-(  My bad.

---

### Post by dfreer on 2012-04-04
You can do this:
```
ps aux | grep cron | grep -v grep
```
And it will show lines that have cron in them but omit lines that also contain grep.

EDIT: Nevermind I see I was too late to the party.

---

### Post by starz677 on 2012-04-21
> **bab1 said:**
>  Could it be that the remote host initiates this?

[COLOR=Red]I disconnected ipv6, disabled (completely UN installed) the ntpd service and yet these outgoing packets persist.[/COLOR]

Remote host as in a distant server not part of my network?

I was thinking about this.   I was thinking maybe there is a file that was uploaded to my www folder and it could be triggered remotely simply by accessing the URL to the file?

The majority of the outbound port 123 packets wee going to PROXY servers.

---

### Post by Ms. Daisy on 2012-04-22
Can you post the lines from your firewall (ufw?) log that show this behavior? 

Your comment in the other thread said > It also appears a cron job has been created because it occurs like clockwork at a specific time every hour.
I looked through the cron jobs but didn't see anything.   A hidden cron job maybe? I tend to be pretty paranoid, but it looks fishy to me. Maybe the "[Did I Just Get Owned]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned")" wiki would help you.

---

