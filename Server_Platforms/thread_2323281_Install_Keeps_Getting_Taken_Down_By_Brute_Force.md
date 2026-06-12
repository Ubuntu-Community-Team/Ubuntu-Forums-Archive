---
title: "Install Keeps Getting Taken Down By Brute Force"
date: 2016-05-04
forum: Server Platforms
---

### Post by silas2 on 2016-05-04
I've got an Ubuntu 15.04 and I've got the latest fail2ban installed. The server is running asterisk which makes it very attractive to brute force hackers...I've been seeing this pattern where fail2ban is repeatedly banning the same IP address, which of course should be in the jail after the first time, then the server falls over.
I feel there must be some new ruse to trip this setup up...any help anyone?

---

### Post by slickymaster on 2016-05-04
*Thread moved to **Server Platforms**.*

---

### Post by Habitual on 2016-05-04
> **silas2 said:**
> then the server falls over.
What does that  mean? Falls over?

---

### Post by silas2 on 2016-05-04
Errrr...I don't really know...I'm a bit of an Ubuntu newbie, but basically I see this pattern where the fail2ban is consistency banning the same IP address (my assumption is that it's from asterisk registration fails) so i know something is up, then, wham, i can't get on the server. Its at Rackspace and no amount of hard rebooting can pick it up again.

---

### Post by Habitual on 2016-05-04
You have remote access to the server? 
If so, login and issue these commands:

```
sudo fail2ban-client --version | head -1
sudo fail2ban-client status
```

and paste the results here please.
Thank you,

---

### Post by silas2 on 2016-05-04
Fail2ban v0.9.1
Status:
Number of jail: 2
Jail List: asterisk-iptables, ssh

---

### Post by Habitual on 2016-05-04
> **silas2 said:**
> Fail2ban v0.9.1
Status:
Number of jail: 2
Jail List: asterisk-iptables, ssh

Thanks.
How about issuing this command:
```
sudo fail2ban-client get asterisk-iptables bantime
``` 
and paste the result.

Thank you,

Subscribed with interest...

---

### Post by silas2 on 2016-05-04
86400

---

### Post by Habitual on 2016-05-04
> **silas2 said:**
> 86400
Thanks. So, they (the IP) should be banned for one 24 hour period.
You believe it is more frequent than that?

Can you post some of /var/log/fail2ban.log that shows one IP being banned more frequently?
Perhaps your /etc/fail2ban/filter.d/asterisk-iptables.conf needs "tuning"?

Have you manually run fail2ban-regex against the /var/log/asterisk.log (or where ever its location)?
Try this:
```
sudo fail2ban-regex /var/log/asterisk.log /etc/fail2ban/filter.d/asterisk-iptables.conf
```

I'm interested in seeing two things from this command:
```
Results
=======

Failregex: xx total
...
<list of hits and the RE they hit on>
```

and 
```
Success, the total number of match is xx
```

The next thing if the manual 'test' 'hits' is to examine the action for the asterisk-iptables jail if all these report favorably.

Thank you,

---

### Post by silas2 on 2016-05-04
[ATTACH=CONFIG]268838[/ATTACH][ATTACH=CONFIG]268839[/ATTACH]

Is this ok?

---

### Post by Habitual on 2016-05-04
> **silas2 said:**
> [ATTACH=CONFIG]268838[/ATTACH][ATTACH=CONFIG]268839[/ATTACH]

Is this ok?

sure.
Is there an /var/log/asterisk.log file?
fail2ban-regex is horribly incorrect and I have to grok that around for a minute.

Why is fail2ban restarting every minute?
That would account for rapid successive bans of the same IP.

iptables resides in memory.
Restarting fail2ban or iptables flushes out the firewall and has to be rebuilt.

Find out why the fail2ban service is restarting so often.
What's the first screenshot from exactly?

Try this also:
```
grep 142.0.41.234 /var/log/fail2ban.log | tail
```
and paste the results.

Thank you,

---

### Post by silas2 on 2016-05-04
I've just seen that regex throw an exception, something wrong with the formats?

---

### Post by Habitual on 2016-05-04
> **silas2 said:**
> I've just seen that regex throw an exception, something wrong with the formats?

Yes,
Can you grep say 25 lines from /var/log/asterisk.log and paste them at pastie.org and then post the link here?
```
tail -25 /var/log/asterisk.log
```
also paste your /etc/fail2ban/filter.d/asterisk-iptables.conf at the same site but a different post?
I'll need that link also.

Thanks.

---

### Post by silas2 on 2016-05-04
When I look for [COLOR=#000000]/var/log/asterisk.log, there is only /var/log/asterisk folder which is full of '.log' files - any idea which one is most useful to you?

When I look in [/COLOR][COLOR=#000000]etc/fail2ban/filter.d/ there is only asterisk.conf, no asterisk-iptables.conf....?[/COLOR]

---

### Post by Habitual on 2016-05-04
The command you should try is 
```
fail2ban-regex [COLOR=#000000]/var/log/asterisk/* [/COLOR]/[COLOR=#000000]etc/fail2ban/filter.d/[/COLOR]asterisk.conf
```
but I'm not sure how the wildcard works (if at all) from fail2ban-regex in c-line.

Do an 
```
ls -lFtr [COLOR=#000000]/var/log/asterisk/* | tail -5[/COLOR]
```
and paste the result.
We'll fail2ban-regex on one or more of those.

---

### Post by silas2 on 2016-05-04
btw I've just run [COLOR=#000000][FONT=Ubuntu Mono]grep 142.0.41.234 /var/log/fail2ban.log | tail , and it ran for 3mins listing a load of failed asterisk registrations - do you want to see those? 

[/FONT][/COLOR]

---

### Post by silas2 on 2016-05-04
Here's the [COLOR=#000000][FONT=Ubuntu Mono]ls -lFtr [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]/var/log/asterisk/* | tail -5[/FONT][/COLOR][/COLOR]
root@foxy:/etc/fail2ban/filter.d# ls -lFtr /var/log/asterisk/* | tail -5
total 0
 
/var/log/asterisk/cdr-csv:
total 8460
-rw-r--r-- 1 root root 8650303 May  4 14:02 Master.csv

---

### Post by Habitual on 2016-05-04
> **silas2 said:**
> btw I've just run [COLOR=#000000][FONT=Ubuntu Mono]grep 142.0.41.234 /var/log/fail2ban.log | tail , and it ran for 3mins listing a load of failed asterisk registrations - do you want to see those? 
[/FONT][/COLOR]

Sure, Here's what I want:
Output from ```
[COLOR=#000000][FONT=Ubuntu Mono]grep 142.0.41.234 /var/log/fail2ban.log[/FONT][/COLOR] | tail
```
should only show 10 records, or 'hits'. Post 'em.

The /etc/fail2ban/filter.d/asterisk.conf contents and 
25 lines from a recent asterisk log file in /var/log/asterisk/

```
ls -ltr /var/log/asterisk/
``` will show them in reverse order, so the most recent will show up
at the bottom or "end" of the command.
I need to see those files names to have you run ```
fail2ban-regex /var/log/asterisk/[COLOR=#ff0000]recent_file[/COLOR] /etc/fail2ban/filter.d/asterisk.conf
```

Your task to find out why the fail2ban service keeps getting restarted and possibly flushing your iptables every minute.

---

### Post by silas2 on 2016-05-04
That tail command is still producing a wodge of text, i guess must be the line delimiter is not working, but here's a sample:

```
<sip:999@162.13.4.246>\' failed for \'142.0.41.234:5580\' - Wrong pasword",EventTV="1462285045-854739",Severity="Error",Service="SIP",EventVersion="moteAddress="IPV4/UDP/142.0.41.234/5580",Challenge="0f254d69",ReceivedChallenge=764] chan_sip.c: Registration from \'"999" <sip:999@162.13.4.246>\' failed for \og.c: SecurityEvent="InvalidPassword",EventTV="1462285045-874209",Severity="Erro"IPV4/UDP/162.13.4.246/5060",RemoteAddress="IPV4/UDP/142.0.41.234/5580",Challengn[2016-05-03 14:17:25] NOTICE[1764] chan_sip.c: Registration from \'"999" <sip:9] SECURITY[1084] res_security_log.c: SecurityEvent="InvalidPassword",EventTV="14="0x7f1e195a2288",LocalAddress="IPV4/UDP/162.13.4.246/5060",RemoteAddress="IPV4/1d46296e80c367bdb58bac4f201b1"\n[2016-05-03 14:17:26] NOTICE[1764] chan_sip.c: R password\n[2016-05-03 14:17:26] SECURITY[1084] res_security_log.c: SecurityEven2",AccountID="999",SessionID="0x7f1e1ae21d78",LocalAddress="IPV4/UDP/162.13.4.24"479f70b2",ReceivedHash="488c0e26a1794a1ecd7afe3abfbc41b6"', 'ipfailures': 
```

---

### Post by silas2 on 2016-05-04
There is a /var/log/asterisk/cdr-csv/Master.csv file, that's full of normal phone calls from today. It seems only to get hit at certain times.

---

### Post by silas2 on 2016-05-04
The [COLOR=#000000] /etc/fail2ban/filter.d/asterisk.conf:
[/COLOR]```
# Fail2Ban filter for asterisk authentication failures
#


[INCLUDES]


# Read common prefixes. If any customizations available -- read them from
# common.local
before = common.conf


[Definition]


_daemon = asterisk


__pid_re = (?:\[\d+\])


# All Asterisk log messages begin like this:
log_prefix= (?:NOTICE|SECURITY)%(__pid_re)s:?(?:\[C-[\da-f]*\])? \S+:\d*( in \w+:)?


failregex = ^(%(__prefix_line)s|\[\]\s*)%(log_prefix)s Registration from '[^']*' failed for '<HOST>(:\d+)?' - (Wrong password|Username/auth name mismatch|No matching peer found|Not a local domain|Device does not match ACL|Peer is not supposed to register|ACL error \(permit/deny\)|Not a local domain)$
            ^(%(__prefix_line)s|\[\]\s*)%(log_prefix)s Call from '[^']*' \(<HOST>:\d+\) to extension '\d+' rejected because extension not found in context 'default'\.$
            ^(%(__prefix_line)s|\[\]\s*)%(log_prefix)s Host <HOST> failed to authenticate as '[^']*'$
            ^(%(__prefix_line)s|\[\]\s*)%(log_prefix)s No registration for peer '[^']*' \(from <HOST>\)$
            ^(%(__prefix_line)s|\[\]\s*)%(log_prefix)s Host <HOST> failed MD5 authentication for '[^']*' \([^)]+\)$
            ^(%(__prefix_line)s|\[\]\s*)%(log_prefix)s Failed to authenticate (user|device) [^@]+@<HOST>\S*$
            ^(%(__prefix_line)s|\[\]\s*)%(log_prefix)s (?:handle_request_subscribe: )?Sending fake auth rejection for (device|user) \d*<sip:[^@]+@<HOST>>;tag=\w+\S*$
            ^(%(__prefix_line)s|\[\]\s*)%(log_prefix)s SecurityEvent="(FailedACL|InvalidAccountID|ChallengeResponseFailed|InvalidPassword)",EventTV="[\d-]+",Severity="[\w]+",Service="[\w]+",EventVersion="\d+",AccountID="\d*",SessionID="0x[\da-f]+",LocalAddress="IPV[46]/(UD|TC)P/[\da-fA-F:.]+/\d+",RemoteAddress="IPV[46]/(UD|TC)P/<HOST>/\d+"(,Challenge="\w+",ReceivedChallenge="\w+")?(,ReceivedHash="[\da-f]+")?(,ACLName="\w+")?$
            ^(%(__prefix_line)s|\[\]\s*WARNING%(__pid_re)s:?(?:\[C-[\da-f]*\])? )Ext\. s: "Rejecting unknown SIP connection from <HOST>"$


ignoreregex =




# Author: Xavier Devlamynck / Daniel Black
#
# General log format - main/logger.c:ast_log
# Address format - ast_sockaddr_stringify
#
# First regex: channels/chan_sip.c
#
# main/logger.c:ast_log_vsyslog - "in {functionname}:" only occurs in syslog



```

---

### Post by Habitual on 2016-05-04
> **silas2 said:**
> There is a /var/log/asterisk/cdr-csv/Master.csv file, that's full of normal phone calls from today. It seems only to get hit at certain times.
We need to find the asterisk log file for attempts to use the asterisk server.

What is logpath for the asterisk jail, I wonder?
```
grep -A 8 asterisk-iptables /etc/fail2ban/jail.{local,conf}
``` output please.

---

### Post by Habitual on 2016-05-04
> **silas2 said:**
> That tail command is still producing a wodge of text, i guess must be the line delimiter is not working, but here's a sample:

You need to surround the output of long log file operations in what are called "code tags"
It's the "#" action button in this editor.
[noparse]```
huge paste of code
```[/noparse] 

None of this is usable without code tags:
```
<sip:999@162.13.4.246>\' failed for \'142.0.41.234:5580\' -  Wrong  pasword",EventTV="1462285045-854739",Severity="Error",Service="SIP",EventVersio    n="moteAddress="IPV4/UDP/142.0.41.234/5580",Challenge="0f254d69",ReceivedChallenge=764]  chan_sip.c: Registration from \'"999" <sip:999@162.13.4.246>\'  failed for \og.c: SecurityEvent="InvalidPassword",EventTV="146228504   5-874209",Severity="Erro"IPV4/UDP/162.13.4.246/5060",RemoteAddress="IPV4/UDP/142.0.41.234/5580",Challengn[2016-05-03  14:17:25] NOTICE[1764] chan_sip.c: Registration from \'"999" <sip:9]  SECURITY[1084] res_security_log.c:  SecurityEvent="InvalidPassword",EventTV="14="0x7f1   e195a2288",LocalAddress="IPV4/UDP/162.13.4.246/5060",RemoteAddress="IPV4/1d46296e80c367bdb58bac4f201b1"\n[2016-05-03  14:17:26] NOTICE[1764] chan_sip.c: R password\n[2016-05-03 14:17:26]  SECURITY[1084] res_security_log.c:  SecurityEven2",AccountID="999",SessionID="0x7f1e1a   e21d78",LocalAddress="IPV4/UDP/162.13.4.24"479f70b2",ReceivedHash="488c0e26a1794a   1ecd7afe3abfbc41b6"', 'ipfailures':
```

The Forum software got involved and the result is f-ugly.

Please see [http://www.fail2ban.org/wiki/index.php/Asterisk](http://www.fail2ban.org/wiki/index.php/Asterisk) also.
Stern warning there.

---

### Post by darkod on 2016-05-04
Sorry to interrupt, Habitual is already doing a good job helping you. I just want to drop in few ideas and questions... I have used asterisk few years back but it was on centos, not ubuntu.

1. Do you really need to have this machine public? I mean, do you use it from various dynamic public IPs? Otherwise use iptables and close it down only for you.
2. Can you maybe implement vpn and connect to it like that first, and then use the asterisk for calls? That would deny anyone else to misuse it...

It's good that you are troubleshooting but at the same time you need to think about closing it down fast...

Plus, you are using 15.04 which is non-LTS and also it is already out of support (it has only 9 months support). Never use non-LTS for production unless really, really necessary... IMHO...

---

### Post by Habitual on 2016-05-04
Thanks for the assist, Darko!

---

### Post by mastablasta on 2016-05-05
i used this guide: [http://stuffphilwrites.com/2013/03/permanently-ban-repeat-offenders-fail2ban/](http://stuffphilwrites.com/2013/03/permanently-ban-repeat-offenders-fail2ban/)

the way i setup it up is that if anyone has more than 3 tries they are banned permanently or should i say are banned for a really long time. connection is done mostly with keys, but i also use a few passwords (on Apache). the sites with passwords that have admin Access have a white list of IP's from where they can be accessed as well as fail2ban should work on them.

i get an increase of repeat offenders and bans during chinese holidays. it's been a while since i received any such request. hmm which in retrospect makes me wonder if setup is still holding. :-) i guess i will have to do a review in 3 weeks when i hopefully get some time off at home. although there were these kind of spells of no bans before...

---

### Post by silas2 on 2016-05-05
This is jail.conf:
```
[asterisk-iptables]
# if more than 4 attempts are made within 6 hours, ban for 24 hours
enabled  = true
filter   = asterisk
action   = iptables-allports[name=ASTERISK, protocol=all]
              sendmail[name=ASTERISK, dest=xxx@hotmail.com, sender=fail2ban@local.local]
logpath  = /var/log/asterisk/messages
maxretry = 4
findtime = 21600
```

Its still a mystery to me how fail2ban keeps getting knocked over...

---

### Post by lisati on 2016-05-05
Just a note:
[noparse]```
 and 
``` often preserves the formatting better than >  and  when posting configuration files and the output of commands.[/noparse]

---

### Post by Habitual on 2016-05-05
> **silas2 said:**
> This is jail.conf:
```
[asterisk-iptables]
# if more than 4 attempts are made within 6 hours, ban for 24 hours
enabled  = true
filter   = asterisk
action   = iptables-allports[name=ASTERISK, protocol=all]
              sendmail[name=ASTERISK, dest=xxx@hotmail.com, sender=fail2ban@local.local]
logpath  = /var/log/asterisk/messages
maxretry = 4
findtime = 21600
```

Its still a mystery to me how fail2ban keeps getting knocked over...

ok. so try this manual test:
```
fail2ban-regex [COLOR=#000000]/var/log/asterisk/messages [/COLOR]/[COLOR=#000000]etc/fail2ban/filter.d/[/COLOR]asterisk.conf
```
Did you change 21600 ? Because earlier a ```
fail2ban-client get asterisk-iptables bantime
``` reported 86400

Still looking for python errors first.

Thank you.

---

### Post by silas2 on 2016-05-05
```
 
Running tests
=============
 
Use   failregex file : /etc/fail2ban/filter.d/asterisk.conf
Use         log file : /var/log/asterisk/messages
Use         encoding : UTF-8
 
 
Results
=======
 
Failregex: 2548 total
|-  #) [# of hits] regular expression
|   1) [1274] ^(\s*(<[^.]+\.[^.]+>)?\s*(?:\S+ )?(?:kernel: \[ *\d+\.\d+\] )?(?:@vserver_\S+ )?(?:(?:\[\d+\])?:\s+[\[\(]?asterisk(?:\(\S+\))?[\]\)]?:?|[\[\(]?asterisk(?:\(\S+\))?[\]\)]?:?(?:\[\d+\])?:?)?\s(?:\[ID \d+ \S+\])?\s*|\[\]\s*)(?:NOTICE|SECURITY)(?:\[\d+\]):?(?:\[C-[\da-f]*\])? \S+:\d*( in \w+:)? Registration from '[^']*' failed for '<HOST>(:\d+)?' - (Wrong password|Username/auth name mismatch|No matching peer found|Not a local domain|Device does not match ACL|Peer is not supposed to register|ACL error \(permit/deny\)|Not a local domain)$
|   8) [1274] ^(\s*(<[^.]+\.[^.]+>)?\s*(?:\S+ )?(?:kernel: \[ *\d+\.\d+\] )?(?:@vserver_\S+ )?(?:(?:\[\d+\])?:\s+[\[\(]?asterisk(?:\(\S+\))?[\]\)]?:?|[\[\(]?asterisk(?:\(\S+\))?[\]\)]?:?(?:\[\d+\])?:?)?\s(?:\[ID \d+ \S+\])?\s*|\[\]\s*)(?:NOTICE|SECURITY)(?:\[\d+\]):?(?:\[C-[\da-f]*\])? \S+:\d*( in \w+:)? SecurityEvent="(FailedACL|InvalidAccountID|ChallengeResponseFailed|InvalidPassword)",EventTV="[\d-]+",Severity="[\w]+",Service="[\w]+",EventVersion="\d+",AccountID="\d*",SessionID="0x[\da-f]+",LocalAddress="IPV[46]/(UD|TC)P/[\da-fA-F:.]+/\d+",RemoteAddress="IPV[46]/(UD|TC)P/<HOST>/\d+"(,Challenge="\w+",ReceivedChallenge="\w+")?(,ReceivedHash="[\da-f]+")?(,ACLName="\w+")?$
`-
 
Ignoreregex: 0 total
 
Date template hits:
|- [# of hits] date format
|  [4197] Year(?P<_sep>[-/.])Month(?P=_sep)Day 24hour:Minute:Second(?:,Microseconds)?
`-
 
Lines: 4336 lines, 0 ignored, 2548 matched, 1788 missed [processed in 0.96 sec]
Missed line(s): too many to print.  Use --print-all-missed to print all 1788 lines
```

That 21K vs 86k question is a mystery to me as well.

---

### Post by Habitual on 2016-05-05
> **silas2 said:**
> That 21K vs 86k question is a mystery to me as well.
Now we are cooking with gas!

Now, about the 86400 value from
```
sudo fail2ban-client get asterisk-iptables bantime
```

Open up /etc/fail2ban/jail.conf (actually, you should edit a copy of /etc/fail2ban/jail.conf as /etc/fail2ban/jail.local, but that's another day)
and near the top of the file is a 
[DEFAULT] stanza
In it you should see a 
```
bantime = 
```
Does it read 86400?

Also in the same /etc/fail2ban/jail.conf or /etc/fail2ban/jail.local file
navigate to the [asterisk-iptables] jail and make 3 edits
```
**[COLOR=#ff0000]maxretry = 2[/COLOR]**
[COLOR=#ff0000]**findtime = 600**[/COLOR]
**[COLOR=#ff0000]bantime  = 43200[/COLOR]**
```

save and exit, or exit with save the /etc/fail2ban/jail.conf file.

Now we save our iptables since restarting flushes them out.
```
sudo iptables-save > /root/iptables.saved
```

Next, restart fail2ban-client with recent edits:
```
sudo fail2ban-client reload
```

Now, we restore our iptables backups using
```
sudo iptables-restore < /root/iptables.saved
```

The last thing to do is monitor the /var/log/fail2ban.log for repeat ban|unban messages for offending hosts.

I'm gonna suggest the following jail:
```
[asterisk-iptables]
# if more than 4 attempts are made within 6 hours, ban for 24 hours
enabled  = true
filter   = asterisk
action   = iptables-allports[name=ASTERISK, protocol=all]
              sendmail[name=ASTERISK, dest=xxx@hotmail.com, sender=fail2ban@local.local]
logpath  = /var/log/asterisk/messages
**[COLOR=#ff0000]maxretry = 2[/COLOR]**
[COLOR=#ff0000]**findtime = 600**[/COLOR]
**[COLOR=#ff0000]bantime  = 43200[/COLOR]**

```

Don't forget, any fail2ban or iptables restarts flushes your current ruleset:

Now we save our iptables since restarting flushes them out.
```
sudo iptables-save > /root/iptables.saved
```

Next, restart fail2ban-client with recent edits:
```
sudo fail2ban-client reload
```

Now, we restore our iptables backups using
```
sudo iptables-restore < /root/iptables.saved
```

Lastly: Check our new bantime using:
```
sudo fail2ban-client get asterisk-iptables bantime
``` should spit out 43200

---

### Post by silas2 on 2016-05-05
Right, changed all those settings and got the 43200 out  with [COLOR=#000000][FONT=Ubuntu Mono]fail2ban-client get asterisk-iptables bantime. Fingers crossed now? [/FONT][/COLOR]

---

### Post by Habitual on 2016-05-05
> **silas2 said:**
> Right, changed all those settings and got the 43200 out  with [COLOR=#000000][FONT=Ubuntu Mono]fail2ban-client get asterisk-iptables bantime. Fingers crossed now? [/FONT][/COLOR]

I hope so!
I think the findtime was a little "excessive", so I went with over-riding it to 600 # seconds
and maxretry = 2

If you wish to exclude problematic hosts, look into the "[ignoreip]("http://www.fail2ban.org/wiki/index.php/Whitelist")" option and you are deploying ssh too, so you may wish to consider
ignoreip = for ssh jail.

Good Luck. Keep an eye on /var/log/fail2ban.log
for the repeated ban|unban of offending hosts.

---

### Post by silas2 on 2016-05-06
Thanks for all your help. Last night (which seems to often be the worst time), all brute force attempts where fought off, maybe this new setting will cure it.

---

### Post by Habitual on 2016-05-06
You are very welcome.
On an LTS Release, I would advise
```
sudo apt-mark hold fail2ban
```

until such time you can make a copy of your important fail2ban files.
Why? Because if you don't, they'll get squashed during an upgrade of fail2ban

---

### Post by silas2 on 2016-05-09
Errr....sorry to reopen this, but this morning I was greeted with 800 failed attempts, 
> The IP 193.111.141.185 has just been banned by Fail2Ban after
134 attempts against ASTERISK.

Btw, if this gives you any clue...the time difference between consecutive bans (one of 800 examples) : ban 1= 09:51:31, ban 2= 09:53:37, same IP.

---

### Post by Habitual on 2016-05-09
Know anyone in Germany?
Is 193.111.141.185 actually banned?

---

### Post by silas2 on 2016-05-09
Defo attempted exploit - we only work mon-fri. Whoever it is, they must have a day job, it seems weekends is the favourite time. Surprised its not more automated.

---

### Post by Habitual on 2016-05-09
> **silas2 said:**
> Defo attempted exploit - we only work mon-fri. Whoever it is, they must have a day job, it seems weekends is the favourite time. Surprised its not more automated.
Stupid comes in waves. ;)
What I've suspected over the last few years, is things are slowing down and I believe that the results of one probe into the server are being targeted for exploit  by an associate of the probe at a later date.
My failregex is pretty huge and I examine my logs like a Religion.
A large filter seems to impact performance on the site, but I'd trade Security for Speed any day of the week.

---

### Post by silas2 on 2016-05-09
What i don't understand is somehow the exploit is managing to get fail2ban to stop and start repeatedly - how could that be?

---

### Post by Habitual on 2016-05-09
without logs, it's impossible to tell.

---

### Post by silas2 on 2016-05-09
Tell me what logs would help you and i'll set them up..

---

### Post by Habitual on 2016-05-09
> **silas2 said:**
> Tell me what logs would help you and i'll set them up..
Asterisk or ssh abuse from 193.111.141.185 ?

Paste the results of 
```
sudo grep 193.111.141.185 /var/log/fail2ban.log | tail 
```
and
```
sudo fail2ban-regex /var/log/asterisk/messages /etc/fail2ban/filter.d/asterisk.conf | grep 193.111.141.185 
```

---

### Post by silas2 on 2016-05-09
with 
```

fail2ban-regex /var/log/asterisk/messages /etc/fail2ban/filter.d/asterisk.conf | grep 193.111.141.185
```
I'm getting nothing back, the rkhunter.log file doesn't seem to exist, was that a typo?

---

### Post by Habitual on 2016-05-09
> **silas2 said:**
> with 
```

fail2ban-regex /var/log/asterisk/messages /etc/fail2ban/filter.d/asterisk.conf | grep 193.111.141.185
```
I'm getting nothing back, the rkhunter.log file doesn't seem to exist, was that a typo?
Then it's possibly **not banned. **

oops.
```
sudo grep 193.111.141.185 /var/log/fail2ban.log | tail 
```

---

### Post by silas2 on 2016-05-09
This is really spooky but that is showing nothing as well..

---

### Post by Habitual on 2016-05-09
Where did you get 193.111.141.185 from exactly?

---

### Post by Habitual on 2016-05-09
Ban that sucker now and all his neighbors using
```
sudo iptables -I INPUT -s 193.111.136.0/21 -j REJECT --reject-with icmp-host-unreachable
```

---

### Post by silas2 on 2016-05-09
Right, i've done that. Why oh why do you think its not logging the bans? Have i set the log levels wrongly?

---

### Post by Habitual on 2016-05-09
> **silas2 said:**
> Right, i've done that. Why oh why do you think its not logging the bans? Have i set the log levels wrongly?

logrotate, maybe...
Try
```
sudo grep 193.111.141.185 /var/log/fail2ban.log.1 | tail
```

---

### Post by silas2 on 2016-05-09
Oh yeah, its there now, 10 entries, maybe more in a previous rotated log. I think that ip was banned 400+ times.

---

### Post by Habitual on 2016-05-09
This should only show first 10 lines from /var/log/fail2ban.log.1
```
sudo grep 193.111.141.185 /var/log/fail2ban.log.1 | head 
```

Paste that output here, It should not be sensitive.

You're not answering my questions:
Asterisk or ssh abuse from 193.111.141.185 ?
Where did you get 193.111.141.185 from exactly?

---

### Post by silas2 on 2016-05-09
```

root@foxy:/var/log#  grep 193.111.141.185 /var/log/fail2ban.log.1 | tail
2016-05-07 08:51:00,733 fail2ban.actions        [1885]: NOTICE  [asterisk-iptables] Ban 193.111.141.185
2016-05-07 08:53:12,218 fail2ban.actions        [2078]: NOTICE  [asterisk-iptables] Ban 193.111.141.185
2016-05-07 08:55:29,946 fail2ban.actions        [2273]: NOTICE  [asterisk-iptables] Ban 193.111.141.185
2016-05-07 08:57:52,409 fail2ban.actions        [2476]: NOTICE  [asterisk-iptables] Ban 193.111.141.185
2016-05-07 09:00:00,663 fail2ban.actions        [2674]: NOTICE  [asterisk-iptables] Ban 193.111.141.185
2016-05-07 09:02:12,599 fail2ban.actions        [2868]: NOTICE  [asterisk-iptables] Ban 193.111.141.185
2016-05-07 09:04:21,874 fail2ban.actions        [3068]: NOTICE  [asterisk-iptables] Ban 193.111.141.185
2016-05-07 09:06:32,537 fail2ban.actions        [3259]: NOTICE  [asterisk-iptables] Ban 193.111.141.185
2016-05-07 09:08:58,169 fail2ban.actions        [3459]: NOTICE  [asterisk-iptables] Ban 193.111.141.185
2016-05-07 21:08:58,180 fail2ban.actions        [3459]: NOTICE  [asterisk-iptables] Unban 193.111.141.185

```
> 
[COLOR=#000000]Asterisk or ssh abuse from 193.111.141.185 ?[/COLOR]
[COLOR=#000000]Where did you get 193.111.141.185 from exactly?[/COLOR]

I've wired for an email notify only for asterisk so there may be ssh ones I haven't seen. The IP comes from the email message, e.g.:
> 
The IP 193.111.141.185 has just been banned by Fail2Ban after
120 attempts against ASTERISK.

---

### Post by Habitual on 2016-05-09
Great.
Your asterisk-iptables unban'd that IP.
I need you to do 2 things:

Check bantime for asterisk-iptables
```
sudo fail2ban-client get asterisk-iptables bantime
```

and post the result

Also, since the last edit, did you restart fail2ban-client with a "reload"?

This will tell you when the fail2ban-server process started:
```
ps -o lstart `cat /var/run/fail2ban/fail2ban.pid`
```
**Keep an eye on this.**

It should remain the same throughout the 'life' of the fail2ban-server process, AFAIK.

Also try:
```
sudo fail2ban-regex /var/log/asterisk/messages.1 /etc/fail2ban/filter.d/asterisk.conf | grep 193.111.141.185
```

---

### Post by silas2 on 2016-05-09
Bantime : 43200
```
ps -o lstart `cat /var/run/fail2ban/fail2ban.pid'
``` : May 7 09:08am which is about an hour BEFORE the last attack
```
fail2ban-regex /var/log/asterisk/messages.1 /etc/fail2ban/filter.d/asterisk.conf | grep 193.111.141.185
```: drew blank, i tried messages.# 1-8 and still nothing.

---

### Post by silas2 on 2016-05-09
PS No didn't do the reload, mind you the 43k bantime would indicate a reload had been done, I don't know if it reloads every time it restarts, but I can do a reload.

---

### Post by Habitual on 2016-05-09
> **silas2 said:**
> PS No didn't do the reload, mind you the 43k bantime would indicate a reload had been done, I don't know if it reloads every time it restarts, but I can do a reload.

Yes, 43200 would indicate a fail2ban-client reload had been accomplished, one way or another.
Every time it starts - **it should not be doing this**.
Compare [this]("http://ubuntuforums.org/attachment.php?attachmentid=268838&d=1462380359") to 
```
ps -o lstart `cat /var/run/fail2ban/fail2ban.pid'
``` "**Keep an eye on this."**???
Take Notes, write it down. 
When the server "falls over" again, or you suspect fail2ban has restarted, run it again and compare. Report here.

All restarts would also be logged in the /var/log/fail2ban.log also, so breeze through this output with some scrutiny:
```
zgrep -i started /var/log/fail2ban.log*
``` and examine the date|time stamps compare to the attachment from your first post.

---

### Post by mastablasta on 2016-05-10
> **silas2 said:**
>  mind you the 43k bantime would indicate a reload had been done

it would indicate you banned the attacker for 12 hours after which you gave them access again.

try bantime = 31536000 seconds (or even -1 which is forever) and make sure the IP is written down in a blacklist so that they can never again get access from that IP at all whil ethe ban is in effect. and that the ban stays after fail2ban reload (e.g. server reboot).


[http://serverfault.com/questions/415040/permanent-block-of-ip-after-n-retries-using-fail2ban](http://serverfault.com/questions/415040/permanent-block-of-ip-after-n-retries-using-fail2ban)


> This included: 

[LIST]
[*]separate ban list by jail (ip.blocklist.ssh, ip.blocklist.xxx)
[*]**ban lists autoloaded if service restart** (main advantage of this method imho)
[*]email notification if repeater engaged.
[/LIST]


[http://stuffphilwrites.com/2013/03/permanently-ban-repeat-offenders-fail2ban/](http://stuffphilwrites.com/2013/03/permanently-ban-repeat-offenders-fail2ban/)

---

### Post by silas2 on 2016-05-10
I can ban them for longer, but I still can't get round how its banning the SAME ip every 2mins, and restarting fail2ban each time?

---

### Post by silas2 on 2016-05-10
> [COLOR=#000000]All restarts would also be logged in the /var/log/fail2ban.log also, so breeze through this output with some scrutiny:[/COLOR]
I'll do this as soon as I can get back on the server, Rackspace has got some updates for my Ubuntu I'm applying...maybe that'll help..

---

### Post by Habitual on 2016-05-10
Thanks mastablasta:
```
bantime = -1
``` is what I also use, and recommend in severe situations.

I'd be inclined to
[LIST]
[*]save asterisk jail. 
[*]save iptables. 
[*]purge fail2ban. 
[*]re-install fail2ban. 
[/LIST]

when fail2ban-regex /var/log/asterisk/messages /etc/fail2ban/filter.d/asterisk.conf doesn't 'hit', I have to examine
my Regular Expression in my filter. And let's be clear, I edit mine. often. **So when all else fails**, I have seen a re-install
correct other troublesome issues. And **there's nothing wrong with defaults**. :)

We could also turn up loglevel in /etc/fail2ban/fail2ban.conf and bounce fail2ban or reload the client...?
loglevel = 4
After that, some very explicit information can be found in /var/log/fail2ban.log

Silas:
Set 
```
[B][COLOR=#ff0000]maxretry = 2
[/COLOR][/B][COLOR=#ff0000]**findtime = 600**[/COLOR]
**[COLOR=#ff0000]bantime  = -1[/COLOR]**
```
in your [asterisk-iptables] jail in /etc/fail2ban/jail.conf

Your "new normal" for working with fail2ban:
```
sudo iptables-save > /root/iptables.saved
sudo fail2ban-client reload
sudo iptables-restore < /root/iptables.saved
```

Any time you edit, you must restart either "sudo service fail2ban-server restart", or "sudo fail2ban-client reload"

Alternatively, **for fail2ban uptime**,  you can run
```
sudo fail2ban-server
``` and it will show you the uptime of the fail2ban service.
Easier than ```
ps -o lstart `cat /var/run/fail2ban/fail2ban.pid'
```

What a Thread!

---

### Post by silas2 on 2016-05-10
Just got back on the server for a mo, ran grep fail2ban.log* and got this:
```

/var/log/fail2ban.log.4.gz:2015-09-12 05:47:46,089 fail2ban.jail           [26437]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:55:50,060 fail2ban.jail           [26696]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:55:55,468 fail2ban.jail           [26696]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:57:53,532 fail2ban.jail           [26800]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:57:58,981 fail2ban.jail           [26800]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:59:10,870 fail2ban.jail           [26891]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:59:16,617 fail2ban.jail           [26891]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:00:44,947 fail2ban.jail           [26991]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:00:50,071 fail2ban.jail           [26991]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:08:44,050 fail2ban.jail           [27243]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:08:48,531 fail2ban.jail           [27243]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:12:09,190 fail2ban.jail           [27474]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:12:13,734 fail2ban.jail           [27474]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:14:16,410 fail2ban.jail           [27579]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:14:20,771 fail2ban.jail           [27579]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:15:36,728 fail2ban.jail           [27671]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:15:40,696 fail2ban.jail           [27671]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:25:29,907 fail2ban.jail           [27985]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:25:38,500 fail2ban.jail           [27985]: INFO    Jail 'asterisk-iptables' started

```
I suppose we could've guessed this, I just spooked by why its able to be pushed over..

---

### Post by silas2 on 2016-05-10
Just got back on the server for a mo, ran grep fail2ban.log* and got this:
```

/var/log/fail2ban.log.4.gz:2015-09-12 05:47:46,089 fail2ban.jail           [26437]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:55:50,060 fail2ban.jail           [26696]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:55:55,468 fail2ban.jail           [26696]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:57:53,532 fail2ban.jail           [26800]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:57:58,981 fail2ban.jail           [26800]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:59:10,870 fail2ban.jail           [26891]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 05:59:16,617 fail2ban.jail           [26891]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:00:44,947 fail2ban.jail           [26991]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:00:50,071 fail2ban.jail           [26991]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:08:44,050 fail2ban.jail           [27243]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:08:48,531 fail2ban.jail           [27243]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:12:09,190 fail2ban.jail           [27474]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:12:13,734 fail2ban.jail           [27474]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:14:16,410 fail2ban.jail           [27579]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:14:20,771 fail2ban.jail           [27579]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:15:36,728 fail2ban.jail           [27671]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:15:40,696 fail2ban.jail           [27671]: INFO    Jail 'asterisk-iptables' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:25:29,907 fail2ban.jail           [27985]: INFO    Jail 'ssh' started
/var/log/fail2ban.log.4.gz:2015-09-12 06:25:38,500 fail2ban.jail           [27985]: INFO    Jail 'asterisk-iptables' started

```
I suppose we could've guessed this, I'm just spooked by why its able to be pushed over..

---

### Post by silas2 on 2016-05-10
[[COLOR=#000000]Habitual[/COLOR]]("http://ubuntuforums.org/member.php?u=504341")[COLOR=#000000] : thanks for those suggestions. I'll try all those things you've suggested after this upgrade from Rackspace, who knows, maybe its a security patch..gotta be optimistic.[/COLOR]

---

### Post by mastablasta on 2016-05-10
are there any cron jobs running maybe? is fail2ban installed well?

did you increase the fail2ban log level ? 

is there any other errror reported?

is this a similar issue: [http://stackoverflow.com/questions/9836650/fail2ban-random-restarts-when-banning-ip](http://stackoverflow.com/questions/9836650/fail2ban-random-restarts-when-banning-ip)

troubleshooting section in fail2ban FAQ: [http://www.fail2ban.org/wiki/index.php/FAQ_english](http://www.fail2ban.org/wiki/index.php/FAQ_english)

also @habitual  -  shouldn't one edit jail.local not jail.conf?

---

### Post by Habitual on 2016-05-10
> **mastablasta said:**
> also @habitual  -  shouldn't one edit jail.local not jail.conf?

Told [him]("http://http://ubuntuforums.org/showthread.php?t=2323281&p=13483962#post13483962") but did not specify why, I don't think.

Why, they ask? Because if fail2ban gets upgraded, all your precious edits in /etc/fail2ban/jail.conf get overwritten.
Same for custom Filters and Actions, if any in /etc/fail2ban/action.d/ and /etc/fail2ban/filter.d/

Well documented at [http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page) and /etc/fail2ban/jail.conf
says 
```
# To avoid merges during upgrades DO NOT MODIFY THIS FILE
# and rather provide your changes in /etc/fail2ban/jail.local
```

I can't make them read it. :(

Tip for "the next guy" who lands here in 3.5 years...
**Put only your enabled jails in /etc/fail2ban/jail.local**

Enjoy the Goodness.

---

### Post by Habitual on 2016-05-24
> **silas2 said:**
> [[COLOR=#000000]Habitual[/COLOR]]("http://ubuntuforums.org/member.php?u=504341")[COLOR=#000000] : thanks for those suggestions. I'll try all those things you've suggested after this upgrade from Rackspace, who knows, maybe its a security patch..gotta be optimistic.[/COLOR]

Any update silas?

---

### Post by Habitual on 2016-07-18
> **silas2 said:**
> [[COLOR=#000000]Habitual[/COLOR]]("http://ubuntuforums.org/member.php?u=504341")[COLOR=#000000] : thanks for those suggestions. I'll try all those things you've suggested after this upgrade from Rackspace, who knows, maybe its a security patch..gotta be optimistic.[/COLOR]
I'm optimistic that weeks have gone by without a peep is a good sign.

Peace.

---

### Post by Habitual on 2016-09-13
No Gnews Is Good Gnews.

---

