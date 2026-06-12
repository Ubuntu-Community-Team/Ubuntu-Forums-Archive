---
title: "security tools for a server"
date: 2016-09-04
forum: Server Platforms
---

### Post by Vegan on 2016-09-04
so far i have one tool installed 

sudo apt-get install chkrootkit

so does this one need to be stuffed into chron?

I have discovered AVG is available but I am not sure if Ubuntu has that tool?

any other options for Linux server?

---

### Post by TheFu on 2016-09-04
There are IPS/IDS tools.  Firewall front-ends.  Dynamic firewall blockers like fail2ban.

I've never found any AV or root-kit tools to be useful. Too many false positives and the AV stuff just looks for Windows viruses. Pretty useless. If there were any Windows machines on the network, I suppose it would be good to be a "good neighbor" by running AV.  The rootkit stuff needs to be maintained and it is too verbose, by default, for my use.  Unix tools should be quiet, unless there is an issue.

Something like COPS (don't know if that tool is even maintained anymore) would be good to keep track of system changes, if you don't already use a DevOps tool like ansible, puppet, chef, etc...  for that.  

There are security addons that look for nasty connections on servers that must be running - apache has a security plugin. nginx has lots of settings to locate bad connections.  If you allow PHP (like wordpress), there are security addons for that. Don't know what they do. Sorry.

**Daily, versioned, backups are the primary tool I use for security needs.** By having 60-120 days of daily backups, there isn't really anything that can't be handled.  60 days for low-risk systems and 120 days for high risk boxes (like email and web servers).

I've been hacked 2 times since 1993. Last time was 2002.  Being hacked is a great teacher.

---

### Post by Vegan on 2016-09-04
I am more interested in protecting my server which I would rather not be hijacked for some illegal purpose

I use strong passwords, and I assume the salt used by Linux is fairly robust too

guess tar can be used to backup the home folder but restore and security issues are questions that need to be resolved

---

### Post by TheFu on 2016-09-04
Don't assume anything when it comes to security. That is the path to ruin.
I use strong passwords too, when key-based authentication isn't available. But with Linux stuff, keys are 
a) easier to use than passwords
b) 100x more secure than any password. A 4K key can't be compared to any password people *believe* to be strong.

Tar?  Haven't used tar in 15 yrs.  It is good to know about it, but nobody really uses that for backups anymore. It isn't efficient in many ways.

---

### Post by Vegan on 2016-09-04
tar now makes tar.gz files so while its still a tape archive, its compressed which is still a classic archive

---

### Post by TheFu on 2016-09-04
> **Vegan said:**
> tar now makes tar.gz files so while its still a tape archive, its compressed which is still a classic archive

Perhaps we have different use-cases?  

I'm backing up 10G-20G of data. Tar would be a terrible answer for that.

---

### Post by mastablasta on 2016-09-07
this page should provide some info: [SIZE=2]https://help.ubuntu.com/community/Security

then maybe something like this: 
[SIZE=2]https://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/
[/SIZE]
there used to be a nice website with steps easilly explained. i can't find it anymore for some reason.


[/SIZE]

---

### Post by ian-weisser on 2016-09-07
Good security is more of a mindset and good habits than merely picking tools.
Containers are useful...for many services.
Keys are useful...for many services.
Fail2ban and other applications are useful...for many services.

Good habits include regularly checking your logs, regularly auditing your open ports, regularly checking for unexpected logins or network activity or CPU load, keeping versioned backups, keeping good notes so you can wipe-and-restore at need, and more.

---

### Post by bob_jones2 on 2016-09-09
vegan,

Security tools are all well and good, but to be honest 95% of the tools you need are already there, i.e. :

- SSH should be key-based authentication with passwords disabled (*THERE ARE NO EXCUSES*)
- Actually monitor your logs (and no, running Fail2Ban to pick up on some pre-defined strings is not what I mean)
- Have a software update routine
- Consider running newer software (e.g. sometimes Ubuntu LTS only has old versions, but well-known developers will often have their own repositories, sometimes there are key security benefits to running newer versinos than available in the LTS repo).
- Choose your service software wisely to minimise security footprint (e.g. nginx vs apache, postfix vs sendmail)
- Configure your service software correctly (and no, I don't just mean googling "how to harden X" and then using some obsolete guide written 10 years ago by a total stranger, I mean RTFM and understand the config options !).
- Don't go asking for trouble (e.g. don't do stooopid stuff like opening up MySQL ports to the world, or leaving MySQLadmin PHP scripts out in the open).
- If you're running stuff like Joomla, for gods sake keep it and all its extensions updated AT ALL TIMES !!  Joomla is a prime target.
- The only thing worse than having to run Joomla is running a public SIP/VoIP service.  If you must do that, please,please, please do your homework !  Public SIP is target number one for miscreants!  You really *MUST* be on top of your game security wise if you are running public SIP.
- Run your service software chrooted 
- Use sudo
- Properly configure iptables
etc. etc. etc.

If all this is for a business, get your boss to approve funding for regular penetration tests.

If you can do the basics properly then you don't need to waste time and resources bloating your system with "security tools", the majority of which are of questionable usefulness.

---

