---
title: "Process mdxfs sending out spam email on Ubuntu 14.04 server"
date: 2018-01-21
forum: Security
---

### Post by highlysceptical on 2018-01-21
I have spent several days trying to get to find the source of the spam emails that keep getting sent out from our Ubuntu 14.04 server.

I am not a Linux expert, but I have managed to establish that the spam is being sent by a process called mdxfs to /usr/bin/perl and thence to random servers on port 25.

I ran maldetect which found a number of hits and cleaned (quarantined) them.  I then ran it again and it reported no hits, and certainly, there were no more spam emails being sent - for the moment at least.

However, later in the day, i found that they had started up again, and when I ran maldetct again, it reported one hit:-

[I]{YARA}Safe0ver_Shell_Safe_Mod_Bypass_Evilc0der_php : ./.bash_history

[/I]This same entry featured several times in the original scan report, so I am assuming that this (whatever it is) is somehow getting through the firewall and implanting itself on our server whenever it gets the chance.

The simple answer would be to close port 25, but I need it for another reason, so that is not an option.  I have managed to create some complicated firewall rules to allow my essential SMTP (25) traffic whilst blocking the spam.  But I really want to get to the bottom of this - what is causing it, and how to stop it permanently.

I have scoured the internet and can find no relevant references to a process called mdxfs, so I am really struggling.  But surely, I cannot be the first person to be plagued by this particular process?

Any suggestions or help would be most gratefully received.

---

### Post by TheFu on 2018-01-22
Nuke it from orbit. That's the only way to be sure.

Seriously, a compromised system is always compromised going forward. You cannot trust it.  Wipe it, completely and start over from prior backups (before anything bad happened (45 days ago?), but this time, follow security best practices for each part of the system. OS, remote connections, DBMS, webserver, reverse proxy, and MTA. How much you can do will completely depend on the type of server and services it runs.  

Limit access to each tiny part to only those systems that actually need access. If ssh always comes from 3 subnets, don't allow more than those 3 subnets access.  If there is a DBMS that 1 part of the system needs, don't allow other parts or outside access to it.  If the MTA should only send emails to 5 people, don't let emails be sent elsewhere.  If you are using passwords for access, don't. Switch to key-based authentication.  If there's a webapp that should only be available to people in a certain country, block all other countries.

None of these things are perfect.  It is about risk management.  Php is generally a high risk webapp.  There are millions (probably more) php-based webapps compromised right now.  Follow the OWASP top-10 list for whatever languages that are used.

Stay patched. If this is a high risk system, patch daily.  Might want a reverse proxy on the front end to add a layer of protection. Use read-only mounts for all static areas of the system.  Block all outbound connections (commonly used by "bad guys") to unknown locations.  If the only traffic out should be HTTPS and SMTPS, then don't allow anything else out.

Versioned backups are my #1 security technique.  The higher risk systems have more, daily, automatic, versioned backups.  Low risk systems only get 60 days, but high risk one get 120+ days.  Those are helpful for many reasons.  It is nice to see which day new files were added/modified. Versioned backups will show that.  In a few minutes, determining exactly when the breach happened would be known.  Just be smart about the backups - don't use mounted storage for backups. Use a client/server model and "PULL" the data, never "push" it.  Another system needs to GET the data. That other system shouldn't be directly on the internet.

The script/program name means ZERO.  It could be anything.  That isn't the point.  Unix security isn't like Windows where billions of computers all run the same program with the same name.  Making a random name for malware is trivial.  There are 100-1000 different places to put the startup or make it restart after a reboot or every 13 minutes or every 3.65467 hrs.  Linux is very flexible.

Nuke it.

---

### Post by QIII on 2018-01-22
If TheFu's suggestion seems drastic, it is.

It is also the only option you have.

---

### Post by highlysceptical on 2018-01-22
Thanks very much.  Coming from a Windows background, this is all rather new to me.  But I will act on your advice and start again.  But at least I have managed to contain the threat for the moment.

---

