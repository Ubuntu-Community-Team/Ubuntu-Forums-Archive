---
title: "security information only partially logged and not with logwatch / OSSEC"
date: 2013-05-07
forum: Security
---

### Post by clearski on 2013-05-07
I've got two problems. That is with regards to some local access logs. I thought it was only a *logwatch* problem, but it's the same with *ossec-hids*.

If I am trying to open an encrypted container somewhere on the machine  and I provide a wrong password, I receive an email (I just don't know who sends it, it is just delivered into my local mailbox in /var/mail), which says:

```
Message  1:
From [removed] Tue May 07 17:33:00 2013
Return-path: <[removed]>
Envelope-to: root@[removed]
Delivery-date: Tue, 07 May 2013 17:33:00 +0300
To: root@[removed]
Auto-Submitted: auto-generated
Subject: *** SECURITY information for [removed] ***
From: <removed>
Date: Tue, 07 May 2013 17:33:00 +0300
Status: R

[removed] : May  7 17:33:00 : [removed] : 1 incorrect password attempt ; TTY=unknown ; PWD=/home/[removed] ; USER=root ; COMMAND=/usr/bin/truecrypt --core-service
```

That is actually great, because I want to be informed of any attempt of using wrong logins or passwords on my system.

My first question is who's this friend that's sending this kind of message? I am not talking about the address it's coming from, as this address appears to be my personal address at localhost, but what service is behind this nice and friendly warning?

The second question comes from this fact: it is strage, but other failed attempts to provide a password **are not signaled**. If I'm trying to *unlock* the User Accounts settings in System Settings and I provide a wrong credential, there's **no** **security warning** in my local inbox. How does it come that I only receive warning for the TrueCrypt application, but not for the User unlock option, which could be as serious as the first one? Not to say that I don't receive any warning for a more serious attempt, like a *su root* command. Neither the first sender (I don't know who it is, as I said before), nor OSSEC do in any way provide information about unsuccessful attempts to login as root or using other name at shell prompt or using greeter login window. Why aren't these failed logins memorized and annouced? How could it be done?

---

### Post by unspawn on 2013-05-09
> **clearski said:**
> My first question is who's this friend that's sending this kind of message?
IIRC that's Sudo.


> **clearski said:**
> The second question (..) How does it come that I only receive warning for the TrueCrypt application, but not for the User unlock option, (..) Not to say that I don't receive any warning for a more serious attempt, like a *su root* command. Neither the first sender (I don't know who it is, as I said before), nor OSSEC do in any way provide information about unsuccessful attempts to login as root or using other name at shell prompt or using greeter login window. Why aren't these failed logins memorized and annouced? How could it be done?
For (nearly all) Linux distributions the generic, basic authentication framework is PAM aka "Pluggable Authentication Modules for Linux". (There appear to be plans to centralize authentication in ^.*[whatever]kit$ though.) PAM covers (or should cover) about anything that requires authentication like logging in at the console, transitioning using 'su', logging in through services like SSH and use of those system tools that require elevated privileges: see 'man pam', /etc/pam.d/ and /etc/security/. PAM logs through syslog, so policy violations should end up in whatever log file your Syslog daemon writes to by default. On top of that your DE (Desktop Environment, think GNOME, KDE, etc, etc) may come with a DM (Desktop Manager aka "greeter", think KDM, GDM, etc, etc) and authentication tools (like KDE's Kcheckpass) or an authentication agent (think polkit-%{whatever-DE}-authentication-agent) which may all log to one or more log files that reside in the users home or /var. 

IMHO the most distro-agnostic way to find out (let's assert here the logs reside in /var and the DE used is GNOME) which files are opened for writing to is to use something like ```
lsof -Pwln -a +D/var -a -d w,0-255|egrep "(gd|gnome)"
```
For OSSEC HIDS I don't know but for Logwatch you then should check the (/wherever/its/installed/share/logwatch/scripts/services/) pam_unix and secure files for any missing lines that should be parsed. Adding any log files can then be done in for example (/wherever/its/installed/share/logwatch/conf/logfiles/)secure.conf.


HTH

---

### Post by clearski on 2013-05-09
I thought it was a little bit easier.

This PAM framework is beyond my understanding right now. I'll probably take a look at how it works in a few weeks. This applies to how Linux runs and keeps the logs, because I didn't have time to go through these until now. The log system is important and should work perfectly, so I'm waiting for a book in order to have a clearer picture of it.

Thank you!

ps: I don't know if it should, but the command

```
lsof -Pwln -a +D/var -a -d w,0-255|egrep "(gd|gnome)"
```

did not return any result. I am using Gnome. I also tried to pointo to */var/log*

---

### Post by clearski on 2013-05-09
**UPDATE 1:** All failed and successful logins with greeter are saved in */var/log/lightdm.log*

A failed attempt:

```
[+9.97s] DEBUG: Session 1812 authentication complete with return value 7: Authentication failure
[+9.97s] DEBUG: Authenticate result for user root12345: Authentication failure
[+9.97s] DEBUG: Session 1812 exited with return value 1
```

A successful attempt:

```
[+14.34s] DEBUG: Session 1962 authentication complete with return value 0: Success
[+14.34s] DEBUG: Authenticate result for user [removed]: Success
[+14.35s] DEBUG: User [removed] authorized
[+14.35s] DEBUG: Greeter requests default session
```

I'll try to add this log file to OSSEC's config. Still don't know where successful and failed login attempts via shell command are saved...

**UPDATE 2:** 

Due to a permission problem (root:root), my auth.log file hasn't been recording anything, though rsyslogd was running. Not anymore. I chowned the file to syslog:adm and it instantly started to record shell login activity. As a result, OSSEC started to send instant notifications when failed logins occured:

```
OSSEC HIDS Notification.
2013 May 09 21:57:03

Received From: [remove]->/var/log/auth.log
Rule: 5503 fired (level 5) -> "User login failed."
Portion of the log(s):

May  9 21:57:02 [removed] su[5357]: pam_unix(su:auth): authentication failure; logname=[removed] uid=1000 euid=0 tty=/dev/pts/0 ruser=[removed] rhost=  user=root

OSSEC HIDS Notification.
2013 May 09 21:57:05

Received From: [removed]->/var/log/auth.log
Rule: 5301 fired (level 5) -> "User missed the password to change UID (user id)."
Portion of the log(s):

May  9 21:57:04 [removed] su[5357]: FAILED su for root by [removed]

OSSEC HIDS Notification.
2013 May 09 21:57:05

Received From: [removed]->/var/log/auth.log
Rule: 5302 fired (level 9) -> "User missed the password to change UID to root."
Portion of the log(s):

May  9 21:57:04 [removed] su[5357]: - /dev/pts/0 [removed]:root


```

That's half of a victory. 

I still don't receive notifications for greeter failed logins, I think that OSSEC needs a rule in order to process the lightdm.log file and send the warning when it encounters some keywords...

---

### Post by clearski on 2013-05-10
I finally have a solution for greeter logins with OSSEC:

```
sudo pico /var/ossec/etc/ossec.conf
```

I added the following lines:

```
<localfile>
    <log_format>syslog</log_format>
    <location>/var/log/lightdm/lightdm.log</location>
  </localfile>
```

to the list with locations, just before the place where */var/log/auth.log* was mentioned. 

At the next reboot, when I had to provide credentials, I used a wrong username: **root222 **(it could have been *root* or whatever unexisting or unaccepted user).

Then I logged in using an accepted username and OSSEC immediately sent an email about the unsuccessful attempt, based on a rule (2501) it had in* /var/ossec/rules/syslog_rules.xml*

```
OSSEC HIDS Notification.
2013 May 10 22:11:57

Received From: [removed]->/var/log/lightdm/lightdm.log
Rule: 2501 fired (level 9) -> "User authentication failure."
Portion of the log(s):

[+10.22s] DEBUG: Session 1835 authentication complete with return value 7: Authentication failure

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2013 May 10 22:11:57

Received From: [removed]->/var/log/lightdm/lightdm.log
Rule: 2501 fired (level 9) -> "User authentication failure."
Portion of the log(s):

[+10.22s] DEBUG: Authenticate result for user** root222**: Authentication failure

 --END OF NOTIFICATION
```

OSSEC also sends a notification about a recording of the same incident that was written to /log/auth.log, but in general terms (failed login), so I am only posting these lines, because they include the username that was used by the perpetrator.

I am quite happy with the results and I think that I can mark this thread as solved.

---

