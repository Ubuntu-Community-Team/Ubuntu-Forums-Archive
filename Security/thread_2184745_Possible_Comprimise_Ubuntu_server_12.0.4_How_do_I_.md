---
title: "Possible Comprimise: Ubuntu server 12.0.4: How do I know? How to clean?"
date: 2013-10-30
forum: Security
---

### Post by MFI-Spencer on 2013-10-30
**12.04.3 LTS

Yesterday I went to login to my Ubuntu Server running on a Dell Poweredge, after being unable to login via ssh I posted a question [http://unix.stackexchange.com/questions/98115/unable-to-login-via-ssh-after-several-months](http://unix.stackexchange.com/questions/98115/unable-to-login-via-ssh-after-several-months) and today I hooked up a monitor and keyboard to attempt to login locally and ended up needing to run ```
passwd
```. Now that I have access I started looking at the log files and didn't see anything in my cursory overview that looked too odd, but then I installed rkhunter and chkrootkit each have odd results.

chrootkit finds a java directory with java 6.0 - This is odd because this server has no need for java and I did not install it.

rkhunter is running right now and I am going to post some of the output:

```
Checking the network...

  Performing checks on the network ports
    Checking for backdoor ports                              [ None found ]
    Checking for hidden ports                                [ Skipped ]


  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]


Checking the local host...


  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]


  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ Warning ]
    Checking for group file changes                          [ Warning ]
    Checking root account shell history files                [ None found ]


  Performing system configuration file checks
    Checking for SSH configuration file                      [ Found ]
    Checking if SSH root access is allowed                   [ Warning ]
    Checking if SSH protocol v1 is allowed                   [ Not allowed ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]


  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                [ Warning ]


[Press <ENTER> to continue]



``` 

```
System checks summary=====================


File properties checks...
    Files checked: 133
    Suspect files: 1


Rootkit checks...
    Rootkits checked : 245
    Possible rootkits: 0


Applications checks...
    All checks skipped


The system checks took: 12 minutes and 46 seconds


All results have been written to the log file (/var/log/rkhunter.log)


One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
```

The odd thing about these results is that root login should not be allowed, root account shouldn't even be activated except via sudo (is that what that result means?). I am not sure but I would think that the changes to groups is also a bad sign unless that happens when I run passwd. I should not expect to have hidden files as far as I know. Last I definitely should not have Java 6.0 (unless it ships standard with the server OS)!

I will of course be happy to post any other logs or information for review.

---

### Post by ian-weisser on 2013-10-30
So,
Your password was changed.
Root login was enabled
Java was installed.
Of course, verify those yourself. rkhunter is great, but not perfect.

Seems mighty suspicious.
I would take the system offline immediately, and reinstall. Restore data from backup.
I always recommend using keys instead of passwords for internet-facing servers. And several other protective measures.
If someone else is responsible for security on your LAN, let them know immediately.

---

### Post by cariboo on 2013-10-31
Check /var/log/auth.log, it should show you when the root password was added, and it may even show you the ip address of the attacker. Look for something similar to this:

```
Oct 29 10:56:21 willy sudo:  cariboo : TTY=pts/0 ; PWD=/home/cariboo ; USER=root ; COMMAND=/usr/bin/passwd root
```

Of course the server name and user name will be different.

---

### Post by MFI-Spencer on 2013-10-31
Thank you to ian-weisser and cariboo907.

@ian-weisser: while it's not how I wanted to spend the next few hours it does seem like the reasonable option. At least this time I do have the needed backups and such to make the experience easier than last time.

@cariboo907: I looked through the logs a bit, but the majority of them were put into a gz file. I've decided to just download them for later this afternoon when my server is back up and running.

---

### Post by cariboo on 2013-10-31
If you install and run mc, an ncurses based file manager, you can view .gz files without having to unzip them. mc is available in the repositories.

---

### Post by MFI-Spencer on 2013-11-06
Just as a quick update for those that might be curious. The log files were deleted from about 1 week after my previous login for a total of 3 weeks, some cron job was added that ran every 14min, but I had already previous cron jobs just nothing that ran that often. I still have not reformatted the system even though it is off, so I plan to see what kind of cron action was going on.

---

