---
title: "my server is attempting to ssh brute force..."
date: 2012-12-07
forum: Security
---

### Post by weasle37 on 2012-12-07
soooo.

I just received notice from a sysadmin that my server was attempting some good ole brute force SSH attacks last night.  My question to you is how do I start looking into this to see what was happening?

I know how to check things out as the receiving end of one of these attacks, but never as the instigating machine. (obviously I was NOT attempting to brute force anyones network, this is malicious and done without my knowledge)

can you point me to any log files or specefic entries that i should be looking for?

Thanks,

Weasle

---

### Post by spynappels on 2012-12-07
First thing is to drop the box off the network if possible, so the attacks stop. 

I guess you'll not like this, but if (and this seems likely) your box has been cracked, a re-install is the only way to be sure it is clean. Time to break out the backups of the data you have on it...

---

### Post by 1clue on 2012-12-07
+1 on the reinstall.

Frankly this sort of thing rarely corrupts data files, so if you pull your drive out and put it in another fully functional box as a second drive you can probably get immediate data backups.

Usually what happens is either a rogue app is installed somewhere (including maybe your user directory) or an existing command is overwritten.  So if you get your data to some system that has reliable apps you might be able to save your data.

That said, you can never be 100% sure you got rid of the bad guy's code.

Start reading here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

IMO it's a much better starting point than the official docs.

Then get some really good passwords when you wipe your box clean, and don't let ANY password be trivial.  And turn off useless services once you made sure they're useless.

---

### Post by CharlesA on 2012-12-07
+2 to wiping the box and starting over. If someone was able to gain access to the machine they could be running a script either remotely or via cron but the main thing with any compromise, is you do not necessarily know what all was done to the machine.

A reinstall is the only way to be sure (unless you really need to nuke it from orbit...)

---

### Post by Ms. Daisy on 2012-12-07
Just to reiterate the obvious first step:

**Get the server off the network **(unplug ethernet, kill wireless).

You have two options: 
1. reimage it and move on with life, perhaps plan on reading the security stickies in this forum so that it doesn't happen again. (if you don't have backups now, make some with the server off the network)

2. If you're curious to see what's happening, then you can do some investigation. Use the "[Did I Just Get Owned]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned")" wiki to look at some logs, knowing that attackers often try to hide their activity by deleting/modifying logs. Look at netstat -antp to see where your server is trying to call. When you're done, reimage & restore the data from your backups.

---

### Post by unspawn on 2012-12-07
- Given how web stack exploits work these days a compromise *does not automagically mean a root compromise*,
- suggesting a box is thoroughly compromised *without actually investigating it* is rather inefficient IMNSHO,
- suggesting a restore from backup *without checking contents first or re-installing without investigating first* may easily expose the same loophole all over again.
Please think about the consequences of "advice".


> **weasle37 said:**
> can you point me to any log files or specefic entries that i should be looking for?
The main reason for web stack compromises is running outdated versions of software, third party plug-ins or not running software like it should be. The latter includes issues like running all web sites in the same shared hosting environment, web servers running default configurations, PHP configuration allowing dangerous HTTP methods, lax file access permissions, installers that aren't cleaned up, unrestricted access to management interfaces, leeched FTP credentials, compromised SSH accounts, no hardened PHP, web no application firewall, no testing whatsoever, etc, etc.

Most of the time you'll find a standardized kit containing a (PHP_based) backdoor, IRC bot and SSH scanner, rarely accompanied by a process hider, cronjob and other "goodies".

Best suggestion in short would be to run all (and I mean all) your logs through Logwatch as it is the quickest way I know to generate leads. Use the "*--detail High --service All --range All --archives --numeric*" args.


*While there's not much honor in "solving" these kinds of compromises, they do happen multiple times a day, I'm offering to help you with a more thorough investigation. You have to gather quite a lot of information, I won't guarantee any success but it'll be educating. If you're up for that please:
0. Read the [CERT Intruder Detection Checklist]("http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html"). While it's old it can still serve as guideline in case you don't know which core items to check,
1. Replace "/path/to/data.txt" with a suitable location like /dev/shm or /var/tmp and save the following information (attach as plain text or pastebin it):
```
( \ps axfwwwe -opid,ppid,gid,uid,cmd 2>&1; \lsof -Pwln 2>&1; \netstat -anTpe 2>&1; \lastlog 2>&1; \last -wai 2>&1; \who -a 2>&1 ) > /path/to/data.txt
```
*Note you should mitigate the situation (raise firewall to deny incoming connections, stop services, kill rogue processes) only after you saved this information.
2. Please post the following nfo:
- which basic services the machine provides like telnet, Vino, SSH, et, etc and any LAMP ones including web-based management panels, statistics, web log, forum, shopping cart, plugins and other software running on top of your web server,
- if software was kept up to date or not,
- which logging, access restrictions are in place and what hardening was performed (if any),
- if there have been earlier breaches or anomalies,
- if you've killed any processes or deleted anything,
- if there are any foreign objects in directories the web server user or unprivileged users can write to like /var/www, home, /tmp, /var/tmp,
- anything "odd" in user shell histories,
- scan the directories mentioned above with LMD ([http://www.rfxn.com/projects/linux-malware-detect/](http://www.rfxn.com/projects/linux-malware-detect/)) or the databases from clamav.securiteinfo.com.
* Please be verbose when posting and add any nfo you think may be useful.

---

### Post by Ms. Daisy on 2012-12-08
> **unspawn said:**
> - Given how web stack exploits work these days a compromise *does not automagically mean a root compromise*,
- suggesting a box is thoroughly compromised *without actually investigating it* is rather inefficient IMNSHO,
- suggesting a restore from backup *without checking contents first or re-installing without investigating first* may easily expose the same loophole all over again.
Please think about the consequences of "advice". Regardless of whether it's a root compromise (which no one suggested), something is amok on this server, that's indisputable.

FWIW, I agree with you- if it were my server I would want to know what happened and how to harden my new installation.  Perhaps I'm jaded but most people aren't interested in in-depth investigations, they just want it fixed quick, and that quick method is reinstallation.  Users will only learn how to prevent it in the future if they care enough to take the time and learn. I have come to expect that they usually don't. Hopefully I'm wrong.

---

### Post by Ms. Daisy on 2012-12-08
btw logwatch is very cool. I had never seen it before.  I highly recommend it for all servers.

---

### Post by cprofitt on 2012-12-08
I agree with both 'camps' here.

The only way to KNOW for sure that the box is clean is to reimage and restore the data from backup.

I would also want to know WHAT happened so I could harden my server.

-----
If you have the ability isolate the 'compromised' server from the network and build a new one to replace it; if you do not have the extra server you could always take an image of the compromised server and then load that in a VM to investigate. If you are really serious you might want to take a forensic image of the compromised box.

For forensics you would want to try [Sluethkit and Autopsy]("http://www.sleuthkit.org/"). 

Best of luck.

---

### Post by Soul-Sing on 2012-12-08
> I just received notice from a sysadmin that my server was attempting some good ole brute force SSH attacks last night. My question to you is how do I start looking into this to see what was happening?

Whats the content of the message? What information is given to you from the sysadmin?
I also would be interested in the information/anwers coming from the questions unspawn asked you.
How did/do you a priori secure your server? (pro-active) How do you monitor your server activities? (Apart from the information given to you by the sysadmin?)

---

### Post by unspawn on 2012-12-08
> **Ms. Daisy said:**
> most people aren't interested in in-depth investigations
Should it be a question to ask? I don't read that many threads but I see it's not uncommon for replies to just state "re-install from scratch" without asking any questions. So could it be in the approach as well? 


> **Ms. Daisy said:**
> Users will only learn how to prevent it in the future if they care enough to take the time and learn. I have come to expect that they usually don't. Hopefully I'm wrong.
Anyone who has dealt with a few cases knows you aren't. Still there are a few things I hope you and anyone else would consider: 
- One compromise is one too many. It reflects badly on Linux as a whole and unless dealt with properly it poses a risk (again) for other systems. 
- These are Ubuntu users coming to the Ubuntu forum for help. So what level of quality may they expect from advice here under the banner of the Ubuntu brand?
- Successfully wrapped-up cases become part of this forums "knowledge base" educating others and possibly serving as reference in new cases.

---

### Post by CharlesA on 2012-12-08
> **unspawn said:**
> Anyone who has dealt with a few cases knows you aren't. Still there are a few things I hope you and anyone else would consider: 
- One compromise is one too many. It reflects badly on Linux as a whole and unless dealt with properly it poses a risk (again) for other systems. 
- These are Ubuntu users coming to the Ubuntu forum for help. So what level of quality may they expect from advice here under the banner of the Ubuntu brand?
- Successfully wrapped-up cases become part of this forums "knowledge base" educating others and possibly serving as reference in new cases.

It really depends on how much time and effort a person has to seeing what logs and whatnot look like when their system in running correctly. If the compromise occured because of a software exploit, it should be shown in the logs unless the attacker was through enough to sanitize the logs.

There are a lot of questions posed on this located here:
[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

---

### Post by Ms. Daisy on 2012-12-08
> **unspawn said:**
> Should it be a question to ask? I don't read that many threads but I see it's not uncommon for replies to just state "re-install from scratch" without asking any questions. So could it be in the approach as well? 
That's why my first post in this thread includes a link to the "Did I Just Get Owned" wiki. IMO that wiki is the best place for someone to start investigating a potentially owned box.  If they have more questions or want to go deeper they'll come back and ask. I agree that we should have a knowledge base which includes said wiki.
> **unspawn said:**
> - One compromise is one too many. It reflects badly on Linux as a whole  and unless dealt with properly it poses a risk (again) for other  systems.  I disagree with you there. It doesn't reflect badly on Linux at all, it highlights the importance of security considerations on **all **operating systems.

---

### Post by chadk5utc on 2012-12-08
Here is a great article on the subject or maybe more so the switch from windows to linux :) PS. when in doubt back it up, lifes easier that way.
[http://www.zdnet.com/windows-security-breaches-on-the-rise-4010025280/](http://www.zdnet.com/windows-security-breaches-on-the-rise-4010025280/)

---

### Post by CharlesA on 2012-12-11
> **Ms. Daisy said:**
> btw logwatch is very cool. I had never seen it before.  I highly recommend it for all servers.

I installed in a couple days ago and I can say it is quite handy.

Thanks for suggesting it, unspawn.

---

### Post by Soul-Sing on 2012-12-11
I would like some information from the OP. Curious about his response on this. (That would make two beans on his/her account)

---

