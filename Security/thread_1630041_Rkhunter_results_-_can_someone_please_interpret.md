---
title: "Rkhunter results - can someone please interpret?"
date: 2010-11-24
forum: Security
---

### Post by zozza on 2010-11-24
Could a kind soul please explain what the following rkhunter results indicate?

These were the only "warnings" I received - everything else was fine: 0 possible rootkits; 0 suspected files.

Thanks. 

[19:59:34] Performing filesystem checks
[19:59:34] Info: Starting test name 'filesystem'
[19:59:34] Info: SCAN_MODE_DEV set to 'THOROUGH'
[19:59:34]   Checking /dev for suspicious file types         [ Warning ]
[19:59:34] Warning: Suspicious file types found in /dev:
[19:59:35]          /dev/shm/pulse-shm-732499774: data
[19:59:35]          /dev/shm/pulse-shm-807387275: data
[19:59:35]          /dev/shm/pulse-shm-3004618893: data
[19:59:35]   Checking for hidden files and directories       [ Warning ]
[19:59:35] Warning: Hidden directory found: /dev/.udev
[19:59:35] Warning: Hidden directory found: /dev/.initramfs

---

### Post by cariboo on 2010-11-24
A quick search of this sub-forum, would show you that almost every question about rkhunter asks the same question. Those are false positives, there is nothing to worry about.

Was there a particular reason for running rkhunter?

---

### Post by zozza on 2010-11-25
> Was there a particular reason for running rkhunter?

No, and frankly, I rather suspect that 99% of home users like me who use rkhunter and tiger really don't need to.

I think that we think that we should run all these security tools and then we have no idea what the results mean.

---

### Post by HermanAB on 2010-11-25
Rkhunter is a quite useless waste of time...

---

### Post by zozza on 2010-11-25
Because....

---

### Post by OpSecShellshock on 2010-11-25
Because it's most likely to display false positives in its results (as you've witnessed), because it needs to be run once on a fresh installation in order to have a decent baseline but even then will alert on files that should be expected to change, because it needs to be recalibrated after every software update, and mostly because anyone who is inclined to write and deploy a rootkit on a system will have already tested it against the most commonly used detection utilities before it's ever been introduced.

---

### Post by Rubi1200 on 2010-11-25
> **OpSecShellshock said:**
> Because it's most likely to display false positives in its results (as you've witnessed), because it needs to be run once on a fresh installation in order to have a decent baseline but even then will alert on files that should be expected to change, because it needs to be recalibrated after every software update, and mostly because anyone who is inclined to write and deploy a rootkit on a system will have already tested it against the most commonly used detection utilities before it's ever been introduced.
+1

If you are concerned about security, read the stickies kindly put together by bodhi.zazen:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by brian_p on 2010-11-25
> **zozza said:**
> Because....

. . . . . any evidence supporting much of what it checks for is nonexistent. Try getting any information on, for example, the portacelo and devil rootkits. The web is full of reports of rkhunter searching for them and never finding them but nothing is written about what they are supposed to do. Why base any security on a questionable reality?

Other malware checked comes from the ark. What possible danger is there to the Slapper Worm?

---

### Post by Kinstonian on 2010-11-25
I'm not sure it's fair to pick on rkhunter.  Can and does it fail to detect some rootkits?  Of course.  Just like any IDS, or any form of detection can fail; just like any form of prevention can fail.  No one would say firewalls are useless just because they can't prevent all attacks.

Yes, the majority of the time you run rkhunter you're not going to detect a rootkit.  In that way, it's similar to backups.  You may spend a lot of time and resources backing up data and feel that you're wasting your time (I know I do).  However, it's not until you need a backup that you realize it was worth all your effort.

Rkhunter is great for post incident analysis by running it on a mounted dd image of the victim hard drive, and for instances where a full HIDS like OSSEC isn't appropriate.  Rkhunter or any anti-malware software may not be the best form of detection, but it's definitely not useless.

---

### Post by HermanAB on 2010-11-25
No, the problem is not that it fails to detect a rootkit the majority of the time.  

The problem is that it never detects anything of consequence, while it always raises alarms about nonsense.

---

### Post by cariboo on 2010-11-25
For most new users that just blindly run programs like rkhunter/chkrootkit, it is virtually useless. After they've run it the first time, they run to the forums and ask about the files it has found. 

Unfortunately most ex-windows users are used to running anti-malware programs without having to know anything about them, and excepting the results they get. It has been often said that Linux expects you to know what you are doing, These anti-rootkit programs are a prime example of that. 

I would be far happier about them if they popped up a dialogue box, explaining what the program does, what should be expected from the first run, and what to do about the results.

---

### Post by Kinstonian on 2010-11-25
> **cariboo907 said:**
> For most new users that just blindly run programs like rkhunter/chkrootkit, it is virtually useless. After they've run it the first time, they run to the forums and ask about the files it has found. 

Unfortunately most ex-windows users are used to running anti-malware programs without having to know anything about them, and excepting the results they get. It has been often said that Linux expects you to know what you are doing, These anti-rootkit programs are a prime example of that. 

I would be far happier about them if they popped up a dialogue box, explaining what the program does, what should be expected from the first run, and what to do about the results.

Yes, but it's not just an anti-malware problem or a Windows problem.  The problem is the average user doesn't know how to respond to any alerts they get.  Whether it's an alert from UAC on Windows, or an invalid SSL cert or rkhunter warning on Ubuntu.

It's more the responsibility of the individual user to educate himself than the responsibility of the software developers.  There is plenty of information already out there, so I don't blame rkhunter developers, I blame the user.

If someone can figure out how to get average people to know how to respond to security messages, it would be an important step in making them more secure.

---

### Post by brian_p on 2010-11-25
> **Kinstonian said:**
> I'm not sure it's fair to pick on rkhunter.

Well, we could throw chkrootkit into the mix as well.:D

> Can and does it fail to detect some rootkits?  Of course.  Just like any IDS, or any form of detection can fail; just like any form of prevention can fail.  No one would say firewalls are useless just because they can't prevent all attacks.

This comparison isn't valid. A firewall filters packets in real time according to rules. The rules can be guaranteed to work. A defective firewall would be due to the lack of a particular rule. rkhunter is an after-the-event application which looks at the before and after state of a system and not a preventative measure. It has rules aplenty. The question might be whether the rules apply to something real in the same way as a firewall rule.

> Yes, the majority of the time you run rkhunter you're not going to detect a rootkit.

Has it ever detected a rootkit? As far as I can see, part of its function is the the equivalent of looking for hairs on the palm of your hand everyday and the other part is similar to screening the population of China for smallpox regularly.

---

### Post by Kinstonian on 2010-11-25
> **brian_p said:**
> Well, we could throw chkrootkit into the mix as well.:D



This comparison isn't valid. A firewall filters packets in real time according to rules. The rules can be guaranteed to work. A defective firewall would be due to the lack of a particular rule. rkhunter is an after-the-event application which looks at the before and after state of a system and not a preventative measure. It has rules aplenty. The question might be whether the rules apply to something real in the same way as a firewall rule.



Has it ever detected a rootkit? As far as I can see, part of its function is the the equivalent of looking for hairs on the palm of your hand everyday and the other part is similar to screening the population of China for smallpox regularly.


The job of a firewall is to filter communication in order to prevent attacks.  A "defective firewall" would be due to misconfiguration, or lack of capabilities.

1.  Even if the firewall is configured correctly, it can still fail when an attack is allowed to a service that needs to be exposed.

2.  Even if the firewall is configured correctly, it can still fail when a user goes to a malicious website.

3.  Even if the firewall is configured correctly, it can still fail by allowing traffic to be tunneled through HTTP.

Whether it fails because of a lack of rules or a lack of capabilities, what I said was true.  They can fail, and they are still useful.  It's common knowledge in security that there is no silver bullet when it comes to prevention, and the same is true with detection.

Just like no one relies on only a firewall to prevent all attacks, no one should rely on simply rkhunter or any anti-malware software to detect all attacks.  Just because some software fails to detect every attack doesn't mean it's useless.  That's the point I was trying to make.

---

### Post by cariboo on 2010-11-26
Relying on the software to detect malware/rookits is wrong too. Of the few rootkits I've played with, they have hidden themselves from rkhunter/chkrootkit, but netstat showed a couple of ports open that shouldn't be.

The only thing to solve the problem of new users assuming they've been cracked/hacked every time something weird happens is education, and unfortunately most users don't want to learn anything new, they just want to get things done.

---

