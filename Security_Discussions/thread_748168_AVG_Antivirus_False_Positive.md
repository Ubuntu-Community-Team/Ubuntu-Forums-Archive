---
title: "AVG Antivirus False Positive?"
date: 2008-04-07
forum: Security Discussions
---

### Post by Eric Boring on 2008-04-07
Hi,

I insalled AVG Antivirus 7.5 on Dapper a couple of days ago and set it up to scan each morning at 8 am. I have it scan the whole file system. After it runs the scheduled scan, when I open AVG, it says "Last test was performed on Mon Apr 7 .... **and virus was found**."

But when I look at the test results it says:
Scanned files: 11800
Scanned sectors: 0
**Infected Files: 0**
Infected sectors: 0
Objects Viewed: 30/30

If I rescan it does not give me the Virus was found message. 
The first time this happened I ran ClamAV and nothing came back as infected.

So do I have a virus (probably not, right?)? If not, what is wrong with my AVg installation?

Thanks very much for any help in advance.

-E

---

### Post by Crafty Kisses on 2008-04-07
Doesn't sound like you have a virus at all, Clam could have seen something suspicious, but from what it sounds like, you're just fine.

---

### Post by netlogic on 2008-04-07
> **Eric Boring said:**
> Hi,

I insalled AVG Antivirus 7.5 on Dapper a couple of days ago and set it up to scan each morning at 8 am. I have it scan the whole file system. After it runs the scheduled scan, when I open AVG, it says "Last test was performed on Mon Apr 7 .... **and virus was found**."

But when I look at the test results it says:
Scanned files: 11800
Scanned sectors: 0
**Infected Files: 0**
Infected sectors: 0
Objects Viewed: 30/30

If I rescan it does not give me the Virus was found message. 
The first time this happened I ran ClamAV and nothing came back as infected.

So do I have a virus (probably not, right?)? If not, what is wrong with my AVg installation?

Thanks very much for any help in advance.

-E

What is the name of the virus? I would like to know. It should be in your log file.

---

### Post by Eric Boring on 2008-04-14
> **netlogic said:**
> What is the name of the virus? I would like to know. It should be in your log file.

Hi, sorry that I let this slip for so long. Here is the results of the latest log file:
```
AVG  7.5
Copyright (c) GRISOFT,s.r.o. 2006
Program version 7.5.51  Engine: 442 database version 269.22.5/1357
Command line: [-report /home/josh/.avg7/testresults/testreport.1208005202 /]
"/etc/.pwd.lock"  Cannot open; not checked!
"/etc/at.deny"  Cannot open; not checked!
"/etc/dhclient-exit-hooks"  Cannot open; not checked!
"/etc/group-"  Cannot open; not checked!
"/etc/gshadow"  Cannot open; not checked!
"/etc/gshadow-"  Cannot open; not checked!
"/etc/passwd-"  Cannot open; not checked!
"/etc/shadow"  Cannot open; not checked!
"/etc/shadow-"  Cannot open; not checked!
"/etc/sudoers"  Cannot open; not checked!
"/etc/X11/Xwrapper.config"  Cannot open; not checked!
"/etc/apache2/httpd-passwords"  Cannot open; not checked!
"/etc/apt/secring.gpg"  Cannot open; not checked!
"/etc/apt/trustdb.gpg"  Cannot open; not checked!
"/etc/cups/classes.conf"  Cannot open; not checked!
"/etc/cups/printers.conf"  Cannot open; not checked!
"/etc/cups/printers.conf.O"  Cannot open; not checked!
"/etc/firestarter/configuration"  Cannot open; not checked!
"/etc/firestarter/events-filter-hosts"  Cannot open; not checked!
"/etc/firestarter/events-filter-ports"  Cannot open; not checked!
"/etc/firestarter/firestarter.sh"  Cannot open; not checked!
"/etc/firestarter/firewall"  Cannot open; not checked!
"/etc/firestarter/sysctl-tuning"  Cannot open; not checked!
"/etc/firestarter/user-post"  Cannot open; not checked!
"/etc/firestarter/user-pre"  Cannot open; not checked!
"/etc/logcheck/ignore.d.server/ssmtp"  Cannot open; not checked!
"/etc/lvm/.cache"  Cannot open; not checked!
"/etc/mysql/debian.cnf"  Cannot open; not checked!
"/etc/mythtv/mythweb-htaccess.conf"  Cannot open; not checked!
"/etc/mythtv/mythweb-settings.php"  Cannot open; not checked!
"/etc/phpmyadmin/blowfish_secret.inc.php"  Cannot open; not checked!
"/etc/phpmyadmin/htpasswd.setup"  Cannot open; not checked!
"/etc/ppp/chap-secrets"  Cannot open; not checked!
"/etc/ppp/pap-secrets"  Cannot open; not checked!
"/etc/qt3/.qtrc.lock"  Cannot open; not checked!
"/etc/ssh/ssh_host_dsa_key"  Cannot open; not checked!
"/etc/ssh/ssh_host_rsa_key"  Cannot open; not checked!
"/home/josh/.rnd"  Cannot open; not checked!
"/home/mythtv/.ICEauthority"  Cannot open; not checked!
"/home/mythtv/.bash_history"  Cannot open; not checked!
"/home/mythtv/.dmrc"  Cannot open; not checked!
"/home/mythtv/.qt/.qt_plugins_3.3rc.lock"  Cannot open; not checked!
"/"  Cannot open; not checked! Permission denied


------------------------------------------------------------
Test start Sat Apr 12 08:00:15 2008
 
Elapsed time 460 sec.
------------------------------------------------------------
Scanned         files      : 11875
Scanned         sectors    :    0
No viruses found.
------------------------------------------------------------

```

So it doesn't look like any of thode lines report a virus. But again, AVG says there is one, just on the main screen you get when you run the program. (I'd post a screenshot, but for some reason gone screen-shot isn't installed on this machine.) It's the screen with the three buttons for [Test] [Test Results] and [Update]

Thanks again for any advice (or just plain reassurance)!

-Eric

---

### Post by Duckyspetrie on 2008-04-15
What happens if you run a manual scan? Does it say the same thing, or was it a one time thing? Sounds like a glitch to me, or something of that ilk. Are you dual-booting Windows?

---

### Post by cammin on 2008-04-15
First, look at the log for April 7th since that will be the one that found the virus.
Second, check the virus vault, if it was cleaned, it will probably be in there. (If the linux version has that, I've only used the Windows version of AVG)

I think I had something like that happen before, "no" was at the start of a new line and was covered up by something else.

---

### Post by Eric Boring on 2008-04-15
> **cammin said:**
> First, look at the log for April 7th since that will be the one that found the virus.
Second, check the virus vault, if it was cleaned, it will probably be in there. (If the linux version has that, I've only used the Windows version of AVG)

I think I had something like that happen before, "no" was at the start of a new line and was covered up by something else.

The April 12 scheduled scan also claimed to find a virus. Only the interface said that "virus was found" the log came back as copied above. 

i don't think the Linux version has virus vault. We are supposed to manually delete virii, as I understand it.

> What happens if you run a manual scan? Does it say the same thing, or was it a one time thing? Sounds like a glitch to me, or something of that ilk. Are you dual-booting Windows?

If I run the scan manually, the log looks the same.  Interface does not say that "virus was found." No, I'm not dual booting Windows, but this machine runs Samba, which a use with two Windows machines.

Thanks for any other advice!

-E

---

### Post by nicedude on 2008-04-19
If you want reassurance then consider this - AVG is legendary for false positives, Just google "AVG false positive" (with the quotes as that will make google look for those words in that order - free google tip)and see how many hits there are, I did and found 740 with that exact phrase. So since you don't even have windows on this machine I would bet the farm that your all clear. You might think about using clam av instead as it doesn't have the same false possitive problems that AVG does and it has better detection rates for windows viruses as well.

Hope this reassures you.

---

