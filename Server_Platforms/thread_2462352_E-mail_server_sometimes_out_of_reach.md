---
title: "E-mail server sometimes out of reach"
date: 2021-05-19
forum: Server Platforms
---

### Post by af-crm on 2021-05-19
The server we have sometimes don't serve the clients. ... "The SMTP server is out of reach". It's been a problem for quite some time and I'm keen to fix it permanently...!

$ Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-142-generic x86_64)


I believe we're using out of the box e-mail server software...  But what to type to be certain!?

Maybe my questions seems silly... but it's a headache getting these sporadic error messages and when the mail is not working I'm responsible for it to work!

```
Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-142-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Wed May 19 09:17:51 UTC 2021

  System load:  0.18               Processes:           350
  Usage of /:   16.9% of 14.70GB   Users logged in:     0
  Memory usage: 15%                IP address for ens8: 81.172.214.161
  Swap usage:   0%

  => /var is using 89.1% of 97.93GB

 * Pure upstream Kubernetes 1.21, smallest, simplest cluster ops!

     https://microk8s.io/

 * Canonical Livepatch is available for installation.
   - Reduce system reboots and improve kernel security. Activate at:
     https://ubuntu.com/livepatch

29 packages can be updated.
1 of these updates is a security update.
To see these additional updates run: apt list --upgradable

New release '20.04.2 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


*** System restart required ***
Last login: Tue May 18 09:50:53 2021 from 172.10.242.63
```

---

### Post by TheFu on 2021-05-19
Well, which SMTP server and IMAP/POP3 server software is being used?  There are multiple choices and most people running email servers only know the one they use, not all of them.

BTW, that system needs to be rebooted. Probably want to do a complete patch cycle before hand.  Do that first.

---

### Post by LHammonds on 2021-05-19
And by patch cycle, he is referring to "apt update" and then "apt upgrade" which will update 18.04.05.....not upgrade to 20.04 which may break the app(s) you have installed.

Also make sure you have a backup that can be restored before doing ANYTHING.  If you are unsure about backup status, make yourself sure first thing.   Then start addressing the problem by identifying what you are using.

This command might help you identify what mail server you are running:
```
apt list --installed
```

If that still does not make it clear, you probably know what port the mail clients are using to connect to the server.  Use a command to reveal what service is listening to that port.  Then look into the service that is running.

You might also be able to tell what is running by looking at the logs.  There might be mail logs directly in /var/log/*.log but more likely, there will be a sub-folder under /var/log that is related to the mail server and inside that, you will be able to look through those logs and tell what mail server is running and what version it is.

LHammonds

---

### Post by TheFu on 2021-05-19
The most commonly used SMTP servers are:  postfix, sendmail, exim, but there are a few others.

For IMAP, I'm thinking **courier** or **dovecot**, but don't really know. I switched to something else in 2008 and never looked back. If you were running what I do, you'd 100% know it and so would all your clients.

If manpages are installed for all packages, which would be expected, you could search the installed manpages on the system for imap and smtp.
```
$ apropos smtp
access (5)           - Postfix SMTP server access table
lmtp (8postfix)      - Postfix SMTP+LMTP client
Net::SMTP::SSL (3pm) - SSL support for Net::SMTP
posttls-finger (1)   - Probe the TLS properties of an ESMTP or LMTP server.
smtp (8postfix)      - Postfix SMTP+LMTP client
smtp-sink (1)        - parallelized SMTP/LMTP test server
smtp-source (1)      - parallelized SMTP/LMTP test generator
smtpd (8postfix)     - Postfix SMTP server
```

So, my system is running postfix.
```
$ apropos imap
git-imap-send (1)    - Send a collection of patches from stdin to an IMAP folder
loadunimap (8)       - load the kernel unicode-to-font mapping table
```
Well, that system doesn't run any imap server, so the results aren't helpful. Looked on my email server where imap client requests are handled and there's nothing there specific to imap. If I was using courier or dovecot, those would certainly show up in the process table.

Can also ask the daemon 'service' handler what's running:
```
sudo service --status-all
```
I suppose there's a systemctl method - I just don't recall it off the top of my head.
```
sudo service --status-all |egrep -v  '\[ \- \]'
```
will show only running services.

---

### Post by af-crm on 2021-05-19
Spamassasin didn't start att reboot... 
This is the headache for me! So much software in that computer! Eventually, I'll just look at it and know what's wrong... like I just did with spamassasin. I'm getting there!

---

### Post by TheFu on 2021-05-19
> **af-crm said:**
> Spamassasin didn't start att reboot... 
This is the headache for me! So much software in that computer! Eventually, I'll just look at it and know what's wrong... like I just did with spamassasin. I'm getting there!

The worse post:
(Please let me know if there's an issue posting the entire log...! Don't ban me! I'll remove the log!)
...
Can't post 'em all! Too long post...


Well, YOU, not us, need to read through those logs.  We already stated the most common programs for SMTP and IMAP. **LOOK for those!**  Then you can troubleshoot.

And please don't post junk, just to post junk.  We don't need to see the login header for the system - ever.

---

### Post by af-crm on 2021-05-20
Excuse me for stirring  up your emotions. My bad. I can read. It's not  the problem. The problem is that I don't know what to look for and what  software is used for what purpose...

I'm fairly new to these things and plenty of people depend on working  e-mail. I was aiming and hoping for guide and assistance filling the  obvious gaps... Maybe it will come! :smile:

---

### Post by TheFu on 2021-05-20
> **af-crm said:**
> Excuse me for stirring  up your emotions. My bad. I can read. It's not  the problem. The problem is that I don't know what to look for and what  software is used for what purpose...

I'm fairly new to these things and plenty of people depend on working  e-mail. I was aiming and hoping for guide and assistance filling the  obvious gaps... Maybe it will come! :smile:

Did you read post #4 above?  There are 2 lists.  Being detailed oriented is critical to being an admin.

---

