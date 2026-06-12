---
title: "How do I secure a Webserver?"
date: 2015-02-23
forum: Security
---

### Post by Harley_Frank on 2015-02-23
I am totally new to the whole Ubuntu server. I started using DigitalOcean.com to host my website, but now I think someone has gained access to my server and messed around in there. I read online that the server is bare and that I need to install security packages to secure it. I don't know what to install or what not. I want to make it secure, but I don't know how.

---

### Post by TheFu on 2015-02-24
Asking how to secure a web server without any additional information provided is like asking someone how to best raise a child but not telling us anything about the child.

Security is hard. Security needs to be layered. Don't trust 1 tool.

And security isn't 1 checkbox to be selected and you are done.  The attacks change daily, so your security will need to cover every possible attack.

So .... a few questions:
* Which OS are you running? Version?
* Which web server?
* Any reverse proxy?
* static files or is there a webapp?
* what webapp? language? toolkits?
* Is there a DBMS?  Which one?
* Are the users of this web server only coming from specific networks or are users world-wide?
* What is your Linux skill level?  The instructions for experts are much easier (and I can help) than the hand-holding needed for beginners (I cannot help). 

Of course, if you use an application stack that is inherently non-secure - nobody can help. Or if you use a stack that we don't use much, we can't really help beyond generalized ideas.

Start by answering the questions above and reading the sticky threads here [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)  The Ubuntu Basic Security Guide is good.  If you are serious about learning this stuff - O'Reilly has a few books on Network security, Application security and every DBMS has best practices for security.  Also review the OWASP guides for your stack: [https://www.owasp.org/index.php/OWASP_Guide_Project](https://www.owasp.org/index.php/OWASP_Guide_Project)

That will keep you busy for a few months AND get you started towards securing your webserver.

---

### Post by Harley_Frank on 2015-02-24
Ok to answer your questions, I am not new to Ubuntu Server, but I am new with security. I'm using the latest 14.04 LTS with Apache using PHP and MySQL. No reverse proxy installed as I know of. Static files. Its only me using the thing, but general viewers to the website is what is going to be based on. I can't say I'm advanced, but I'm not a beginner. In fact, I have taken several UNIX courses, but never in security.

The big things that I am concerned is SSH, MySQL, HTTP, and FTP. Most of the main PHP and MySQL functions are going to be initiated from inside the machine so I really don't want access from the outside. They way I learned about securing Windows is that you change all well-known ports (by change I mean the port numbers and block the originals from access in firewall) maybe its the same concept or I could be totally wrong.

Im an using Windows 8.1 on 64bit machine. How I communicate is through Putty and I tried to generate an RSA key but failed to configure it right. However, I did lock out the root and only my profile is what I use.

I also forgot to mention that the first thing I did was enable a firewall. I set default settings to deny, but I allowed in/out 20,21,22,25,80,139,143,443/tcp which doesn't seem to have hindered the server at all.

---

### Post by sandyd on 2015-02-24
> **Harley_Frank said:**
> Ok to answer your questions, I am not new to Ubuntu Server, but I am new with security. I'm using the latest 14.04 LTS with Apache using PHP and MySQL. No reverse proxy installed as I know of. Static files. Its only me using the thing, but general viewers to the website is what is going to be based on. I can't say I'm advanced, but I'm not a beginner. In fact, I have taken several UNIX courses, but never in security.

The big things that I am concerned is SSH, MySQL, HTTP, and FTP. Most of the main PHP and MySQL functions are going to be initiated from inside the machine so I really don't want access from the outside. They way I learned about securing Windows is that you change all well-known ports (by change I mean the port numbers and block the originals from access in firewall) maybe its the same concept or I could be totally wrong.

Im an using Windows 8.1 on 64bit machine. How I communicate is through Putty and I tried to generate an RSA key but failed to configure it right. However, I did lock out the root and only my profile is what I use.

Few recs for what your worried about:
[LIST]
[*]SSH & FTP Brute Force Protection (CSF/LFD or fail2ban)
[*]Changing port numbers is security through obscurity and can easily be bypassed by port scanner
[*]If your doing file uploads, make sure that the files being uploaded are the files that should be uploaded (user can upload a CGI script/etc if you allow them and execute it if enabled by server)
[*]If no mysql access is needed outside of the server and you are only serving static files, make sure mysql is kept bound to localhost
[*]If you eventually intend to make the php files accessable by public, use mysql prepared statements/etc to make sure mysql injection capability is lowered
[*]FTP has no encryption unless your using FTP with SSL/TLS. Use filezilla with SFTP, which uses SCP to send files safely
[*]Keep system updated. If your lazy and want to chance it, use unattended-upgrades. It will automatically install security updates daily at the risk if an update breaking your system.
```
sudo apt-get install unattended-upgrades && sudo dpkg-reconfigure unattended-upgrades
```
[/LIST]

---

### Post by Harley_Frank on 2015-02-24
```
sudo apt-get install unattended-upgrades && sudo dpkg-reconfigure unattended-upgrades
```

Yes I am familiar with that. I use it everyday to check and double check. So I should deny ports 20,21/tcp and just use 22? Would that work or does it need FTP to run?

My server is going to be running WordPress so I know CGI can be harmful, but I honestly don't know if I should disable it because I don't know what WordPress uses. I am going to be using PHP all the time, so It is going to be accessed by users. Thank you for the reply back.

---

### Post by sandyd on 2015-02-25
> **Harley_Frank said:**
> ```
sudo apt-get install unattended-upgrades && sudo dpkg-reconfigure unattended-upgrades
```

Yes I am familiar with that. I use it everyday to check and double check. So I should deny ports 20,21/tcp and just use 22? Would that work or does it need FTP to run?

My server is going to be running WordPress so I know CGI can be harmful, but I honestly don't know if I should disable it because I don't know what WordPress uses. I am going to be using PHP all the time, so It is going to be accessed by users. Thank you for the reply back.

By default, ports on Ubuntu are closed unless something is listening on them. That being said, I still recommend a firewall

For your setup, just block everything and 
[LIST]
[*]Open ports 80,22
[*]Open port 443 if using ssl
[/LIST]

If you are worried about DDOS attacks and such, place cloudflare in front. Note that cloudflare will only filter attacks up to a certain amount before switching to directly accessing your IP. They do not block L7 attacks well either.

If your using Wordpress, you don't need CGI.
Please also ensure that your wordpress installation is up to date, along with plugins. There have been many many break-ins and site defacements caused by out of date, insecure, or no longer maintained wordpress plugins. Some plugin creators have even neglected to prevent direct web access to the plugin files ](*,)

---

### Post by TheFu on 2015-02-25
Thanks for the answers. We all *don't know what we don't know.*  Came across a 20 yr sys admin who didn't know about the ~/.ssh/config file. Changed his life, it has.

How are your backups?  Versioned backups can solve things that nothing else can - especially related to security. The first question you are going to ask after a hack against your server happens is "what did they change?"  Without backups from before the successful hack, how will you know?  Being able to compare all critical files for changes later is important.

How is your monitoring?  Will you be alerted if someone is attacking the box?  If the machine becomes busy, will you know? Having 4+ months of performance monitoring is the most likely way you'll see "something changed" which will uncover the hack(s). Or your site could be used for phishing and you won't notice for months.

Lots of folks here asking for help to recover their wordpress sites after being hacked. Best to review those theads **before it happens** to your machine. Be proactive. Have a plan.  When we setup a corporate website, the CEO paid his brother to develop it. Php was selected because that was the language his brother used. No fancy management system, nothing too complex. In fact, everything on the site should have been developed with static files and CSS, but ... politics.  The CSO and I had to sit down with the CEO and explain that we didn't think our site was secure, but that we had a plan for after the attack.  He wasn't happy.  Every website can be hacked by a determined attacker.  That is what we explained.  Our goal was to be harder than most other websites and to not have anything of value on the public server. So far, this has been working. We do have versioned backups.

Php is a dangerous language. Be certain to carefully review the OWASP security list for it. About once a quarter, there's an issue connected to wordpress in some way. [Todays announcement.]("http://arstechnica.com/security/2015/02/more-than-1-million-wordpress-websites-imperiled-by-critical-plugin-bug/"). This really applies to any web-app, so plan to stay informed, regardless of which language is involved. Perl, Python, Ruby all have their issues too. Running any webapp means staying up on attacks for the entire software stack, daily.

Good for disabling FTP and switching to sftp.  Don't use passwords, only use keys and running something like fail2ban is good. I use port translation at the router to avoid automatic attacks filling the logs. There aren't many reasons to run on port 22 anymore, at least on the public-facing ports. A few yrs ago, I was seeing over 1,000 attempts against ssh daily. Then noticed that and moved that listener to a random high port. Zero attempts for months. Sure, the other port can be found, but unless you are a target, nobody will look and cleaner logs make it more likely we will see something important.  Whatever you do to block attempts, be certain to test it.  fail2ban wasn't working for a few months last fall - then it started working again after an update.  I wasn't the only person impacted.  If you travel and need access, putting ssh on 443 may be necessary to get through highly limiting hotel proxy servers. A few years ago on a business trip across Europe, only 50% of the hotel internet let me connect to my server with ssh on a random high port.

There are a few different system security scanners. Might be good to find some that are currently updated and run them. Then work your way through all the issues. I understand there are wordpress and php scanners too.

If you care about politics there are many other things to consider - s/mysql/mariaDB/  stuff like that.

Don't forget - this stuff is fun!

---

### Post by Harley_Frank on 2015-02-25
> **TheFu said:**
> Thanks for the answers. We all *don't know what we don't know.*  Came across a 20 yr sys admin who didn't know about the ~/.ssh/config file. Changed his life, it has.

How are your backups?  Versioned backups can solve things that nothing else can - especially related to security. The first question you are going to ask after a hack against your server happens is "what did they change?"  Without backups from before the successful hack, how will you know?  Being able to compare all critical files for changes later is important.

How is your monitoring?  Will you be alerted if someone is attacking the box?  If the machine becomes busy, will you know? Having 4+ months of performance monitoring is the most likely way you'll see "something changed" which will uncover the hack(s). Or your site could be used for phishing and you won't notice for months.

Lots of folks here asking for help to recover their wordpress sites after being hacked. Best to review those theads **before it happens** to your machine. Be proactive. Have a plan.  When we setup a corporate website, the CEO paid his brother to develop it. Php was selected because that was the language his brother used. No fancy management system, nothing too complex. In fact, everything on the site should have been developed with static files and CSS, but ... politics.  The CSO and I had to sit down with the CEO and explain that we didn't think our site was secure, but that we had a plan for after the attack.  He wasn't happy.  Every website can be hacked by a determined attacker.  That is what we explained.  Our goal was to be harder than most other websites and to not have anything of value on the public server. So far, this has been working. We do have versioned backups.

Php is a dangerous language. Be certain to carefully review the OWASP security list for it. About once a quarter, there's an issue connected to wordpress in some way. [Todays announcement.]("http://arstechnica.com/security/2015/02/more-than-1-million-wordpress-websites-imperiled-by-critical-plugin-bug/"). This really applies to any web-app, so plan to stay informed, regardless of which language is involved. Perl, Python, Ruby all have their issues too. Running any webapp means staying up on attacks for the entire software stack, daily.

Good for disabling FTP and switching to sftp.  Don't use passwords, only use keys and running something like fail2ban is good. I use port translation at the router to avoid automatic attacks filling the logs. There aren't many reasons to run on port 22 anymore, at least on the public-facing ports. A few yrs ago, I was seeing over 1,000 attempts against ssh daily. Then noticed that and moved that listener to a random high port. Zero attempts for months. Sure, the other port can be found, but unless you are a target, nobody will look and cleaner logs make it more likely we will see something important.  Whatever you do to block attempts, be certain to test it.  fail2ban wasn't working for a few months last fall - then it started working again after an update.  I wasn't the only person impacted.  If you travel and need access, putting ssh on 443 may be necessary to get through highly limiting hotel proxy servers. A few years ago on a business trip across Europe, only 50% of the hotel internet let me connect to my server with ssh on a random high port.

There are a few different system security scanners. Might be good to find some that are currently updated and run them. Then work your way through all the issues. I understand there are wordpress and php scanners too.

If you care about politics there are many other things to consider - s/mysql/mariaDB/  stuff like that.

Don't forget - this stuff is fun!

I don't doubt this is fun. I like doing this. Backups are what I was looking into. Is there a specific way I can create system images that can be restored if critical data was changed?

---

### Post by TheFu on 2015-02-26
There are many different ways to create *imaged based backups*. I don't use those much - just for migrating between physical systems, not for backups. Linux isn't windows - image-based backs are so 1992 and aren't needed, IMHO.  But if that is what you want, ddrescu, dd, partimage, clonezilla, fsarchive are each capable tools.

I use rdiff-backup and keep 30-120 days of backups for my systems. For some servers, the backup is 70MB for 120 days, since I don't backup everything, just the settings, installed packages and data. If a system doesn't hold data - like an email gateway - then those backups become tiny. I can recreate the email gateway in about 30 min from those things.  The same idea goes for webservers, blogs, desktops, email servers, redmine servers, .... CRM, DMS, and file servers. The only difference is how much data in the backups and whether I need to dump a DB before doing the backup or not.  Of course, for file servers or email servers or desktops, I can't keep 120 days of versioned backups. The storage requirements would be too large, but for 1.2x the original storage, I can keep 30-60 days. rdiff-backup is very storage, backup time and network efficient.  Plus if you don't need encrypted backup storage, it is a great tool. If you need to encrypt everything before transmission - duplicity is the too - but it stores backups in those god-awful chunks that can't be read easily using normal tools. The last rdiff-backup looks like a mirror, it is only the older versions that need just a little extra help - they use gz of any changes - so not that much extra help. A file is still a file. Permissions are retained unlike the simple file mirroring solutions - permission changes cannot be seen when there's only the last mirror like with straight rsync backups.

But only you can decide which backup method fits the needs.

---

### Post by Harley_Frank on 2015-02-26
Sorry, I work on Windows servers all the time and we use image backups of the main configuration so we can drop in a new drive if need be so that's why I asked about image backups. I don't care much for the data because I have local backups made. I'm implementing it right now. I noticed that it a few years old, is that a security risk?

Also is it possible to be missing the authorized_keys file after generating an rsa key?

---

### Post by TheFu on 2015-02-26
> **Harley_Frank said:**
> Sorry, I work on Windows servers all the time and we use image backups of the main configuration so we can drop in a new drive if need be so that's why I asked about image backups. I don't care much for the data because I have local backups made. I'm implementing it right now. I noticed that it a few years old, is that a security risk?

Also is it possible to be missing the authorized_keys file after generating an rsa key?

Security risk? Depends.
* is it a supported release?
* is it currently patched?

Key generation isn't part of updating an authorized_keys file on a remote host.  More practice with ssh-keygen and ssh-copy-id will help you become more comfortable with that.

We are way off the original topic.

---

### Post by Harley_Frank on 2015-02-27
Well Why I mentioned it is because when I installed the rdiff-backup my SSH quit working, now I am getting Server Refused our Key and now its allowing access via the password without an RSA key. It was working perfectly before and I just tried another instance and made sure it worked and then installed rdiff-backup and its removing the authorized_keys file every time the machine reboots.

---

### Post by Habitual on 2015-02-27
> **Harley_Frank said:**
> its removing the authorized_keys file every time the machine reboots.This may be DigitalOcean "thing" to preserve access to deployed droplets.
I'd make my key additions to ~/.ssh/authorized_keys2 and reboot and see if it keeps.

---

### Post by Harley_Frank on 2015-02-27
Well I tried that and still doesn't work. Weird. I'll look for another backup program to run that may not conflict with ssh. I do appreciate all the help guys!

---

