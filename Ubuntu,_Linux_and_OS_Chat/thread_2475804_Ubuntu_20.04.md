---
title: "Ubuntu 20.04"
date: 2022-06-08
forum: Ubuntu, Linux and OS Chat
---

### Post by gordie692 on 2022-06-08
Hey guys I've ran Ubuntu for years love it but I've been hearing things on malware for linux getting worst is that just all talk I really would hate to go backto windows because I hatre windows 10 and 11 I've used Ubuntu since 6 ver

Thanks guys

---

### Post by mIk3_08 on 2022-06-09
> **gordie692 said:**
> Hey guys I've ran Ubuntu for years love it but I've been hearing things on malware for linux getting worst is that just all talk I really would hate to go backto windows because I hatre windows 10 and 11 I've used Ubuntu since 6 ver
Thanks guys
Have you experience this already? Maybe it was just a gossip then. I have used my Linux Ubuntu Operating System (Server and Desktop) for a quite long time now and I haven't experienced this one yet. So regards and cheers.

---

### Post by gordie692 on 2022-06-09
Thanks Mik3_08 I've used Ubuntu for long time myself hate when you see gossip crap so again no malware antivirus right

---

### Post by ajgreeny on 2022-06-09
Don't worry about these stories but just continue to use your system in a careful manner as I'm sure you already do, and you should be fine.

I've been using Ubuntu (now Xubuntu) exclusively since 2005 and never used any virus checker or anti-malware applications on it in all that time.  I investigated using clamav at one point and even installed it and looked at using it but realised that you had to actually scan files manually as it doesn't run in the background as Windows anti-virus does, so it was therefore not of any real value to me with only Linux running.

In all those 17 years I have never once had any malware on my machines and anything that has ever gone wrong has been mainly down to me personally making a mistake on the keyboard and wiping out something I shouldn't have.  I do, however, have very good backups of all my data, essential for peace of mind, though I don't bother backing up the OS itself as it is very quickly reinstalled if necessary.

---

### Post by #&amp;thj^% on 2022-06-09
> **ajgreeny said:**
> Don't worry about these stories but just continue to use your system in a careful manner as I'm sure you already do, and you should be fine.

+1
This should be monitored by the User on a bi-monthly basis.
[list]
[*]Look for failed log-in attempts across organizations or networks.(large numbers of failed attempts)
[*]Identify the source system isolate, continue the further investigations and find root causes.
[*]Monitor for the malicious file drops or creations through File Integrity Mentoring
[*]Monitor for any changes in "/etc/cron.hourly/gcc.sh", "/lib/libudev.so.6", "/lib/libudev.so" and "/var/run/gcc.pid"
[*]Monitor for unusual command executions such as cat resolve.conf or any other possible fake commands.
**More Advanced, **
[*]Use anomaly detector tools and algorithms to detect unusual behavior in command executions.
**Prevention Methods:**
[*] Use strong SSH passwords or use private keys for accessing remote servers.
[*]Deploy File Integrity Monitoring solutions, without FIM capability we won&#8217;t be able to tell the changes in sensitive configuration files, like crontab or init.d directories.: [https://www.dnsstuff.com/file-integrity-monitoring-software](https://www.dnsstuff.com/file-integrity-monitoring-software) 
[*]Deploy any network monitoring or visibility solutions.
I suggest we utilize all the tools we have at our disposal.
File Locations for Monitoring Changes:
[*]/usr/bin/
[*]/lib/
[*]/etc/init.d/
[*]/tmp/bin/
[/list]
IMHO: Security rests or works with the User....
Stay Safe enjoy.

---

### Post by grahammechanical on 2022-06-09
As a Ubuntu user you will know that it is important to keep the operating system up to date by running Software Updater. The Ubuntu Weekly Newsletter lists all the vulnerabilities that have been fixed week by week.

[https://ubuntuforums.org/showthread.php?t=2475527](https://ubuntuforums.org/showthread.php?t=2475527)

In Linux security vulnerabilities are often fixed before criminals can take advantage of them. Here is an example of an extreme vulnerability and the combined efforts that were taken to fix the flaw. 

[https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities](https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities)

It explains why many of us have confidence that we are using a very secure operating system. Perhaps the most secure.

Regards

---

### Post by gordie692 on 2022-06-09
I run updater every morning first thing

---

