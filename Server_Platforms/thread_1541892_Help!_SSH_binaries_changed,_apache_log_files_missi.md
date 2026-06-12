---
title: "Help! SSH binaries changed, apache log files missing - stumped"
date: 2010-07-29
forum: Server Platforms
---

### Post by phlipdascrip on 2010-07-29
Help! Something happened on my server and I just can't figure out what (2 people searched the system for over a day to no avail).

System: 8.04 Hardy with ISPconfig 3

The following symptoms all occured around the same time (at around 11:10am PT on Jul 27) in this order:
[LIST]
[*] ssh and sshd binaries changed (modified date: Jul 27 11:10)
[*] ssh and sshd config files changed (modified date: Jul 27 11:11); sshd config file is emptied, only contains the Port directive.
[*] sshd restarts (at 11:11)
[*] all apache log files of the main vhost at /mnt/www/web1/log are removed (at 11:15)
[/LIST]

Looking at my Munin graphs I also see that around the same time:
[LIST]
[*] filesystem usage drops (concurring with removed log files)
[*] eth0 traffic has an incoming spike
[*] inode table usage breaks its pattern and has been above normal ever since
[*] memory usage breaks its pattern; initally drops, active memory now constantly above normal
[*] mysql SELECT queries spike
[*] mysql receive throughput has a smaller spike
[*] IOstat breaks its pattern (no more consistent daily spikes in sdf reads)
[*] swap in/out breaks its pattern (no more consistent daily spikes)
[/LIST]

We went through everything we could come up with but still have no idea what may have caused all this:
[LIST]
[*] no signs of intrusion (auth.log)
[*] no indicators of automatic updates (checked /etc/apt/apt.conf.d/, /etc/cron.daily, and crontabs; /var/log/apt/term.log, /var/log/aptitude, and /var/log/dpkg.log are empty) with the exception of metapackages in /etc/apt/apt.conf.d/01ubuntu
[*] no indicators of automated log file removal in the /mnt/www/ realm (checked ISPconfig scripts and logrotate config)
[/LIST]

Anyone have any clues or ideas what has happened?
Did we miss anything?
Does this look like an intrusion of someone who knows how to clean up after himself?

Any pointers are highly appreciated!
Thanks, Phil


//EDIT: also good to note are probably the current ssh(d) versions:

$ ssh -V
ssh: OpenSSH_4.3p2-5, SSH protocols 1.5/2.0, OpenSSL 0x0090703f

$ dpkg -l | grep ssh
openssh-client   1:4.7p1-8ubuntu1.2
openssh-server   1:4.7p1-8ubuntu1.2

---

### Post by CharlesA on 2010-07-29
Were there any failed login attempts in the /var/log/auth.log ?

It sounds like the box might have been compromised.

---

### Post by iponeverything on 2010-07-29
+1 for possible compromise. They would have had to have been pretty sloppy to leave something behind in auth.log 

install and run debsums check for rootkits.

---

### Post by wirelessmonkey on 2010-07-29
Everything about this screams compromise. Wipe and restore.

---

### Post by phlipdascrip on 2010-07-30
Thanks for the replies; I'm now convinced the server was hacked into and I got a new one up and running already.

> **CharlesA said:**
> Were there any failed login attempts in the /var/log/auth.log ?
Yes plenty, a couple of brute force attacks for root (which is disallowed) and random user names. I would be surprised though if any of those worked.

Now how would I go about analyzing how they got in? I kept the compromised instance running (not publicly available) for analyzation as I really want to know how they did it so that I can pay extra attention to securing it properly.
There's a file /dev/devno that contains user names with passwords from every login it seems.

This is not something I do every day and I'm by no means a linux pro, so again any pointers are highly appreciated!

Thanks, Phil

---

### Post by CharlesA on 2010-07-30
My machine doesn't have a file called /dev/devno. Regardless there shouldn't be any recording of username -and- password going on.

The auth.log records login names of users that are successfully logged in as well as failed attempts.

I don't really know how you can find out how it was compromised, unfortunately. If it was, wipe and reinstall is the best way to recover.

Was the machine open to physical access or was it managed by remote?

---

### Post by phlipdascrip on 2010-07-30
No physical access, it's a virtual server.
One assumption is that they put modified ssh and sshd binaries in place that records usernames and passwords in the /dev/devno file. I'm pretty sure no system has such a file and that it's been named like this to not cause much suspicion. rkhunter picked up on it though.

---

### Post by CharlesA on 2010-07-30
Yah, it was definitely compromised. Guessing more then likely compromised via SSH or maybe even apache, if it wasn't up-to-date.

---

### Post by phlipdascrip on 2010-08-23
As a wrap-up for anyone who's interested, I was able to figure out that the server was compromised through a known XML-RPC vulnerability (CVE-2005-1921, CVE-2005-2116) of a painfully outdated version of the PHP tool "phpAdsNew" (that I didn't even know existed on the server...), in the file adxmlrpc.php - which after the attack was renamed to abxmlrpc.php!

I was able to reproduce part of the attack by running an XML-RPC command against the file via HTTP POST and could easily wget a file into /tmp

Running the strings command against the ssh and sshd libraries also showed the path /dev/devno in both files which pretty much confirms that the modified binaries put all credentials into that file upon authentication.

Savages...

Cheers

---

