---
title: "SSH attacks &amp; IP lockdown"
date: 2007-03-30
forum: Server Platforms
---

### Post by zarg@henrikke on 2007-03-30
After running ubuntu & SSH a couple of days..

I can see robots trying to logon over SSH. nothing serious yet, just a few guesses on some standard accounts. Anyway, I want to address the problem now and be prepared.

After searching.. I couldn't locate a firewall installed, so I need to get one. :( 

Is there a tool that can be set up to watch 'auth.log', which trigger on e.g. "Illegal user" there and can add a fw rule to block attacker's IP on the fly?

---

### Post by az on 2007-03-30
Loads of stuff to look into:

[http://packages.ubuntu.com/edgy/net/denyhosts](http://packages.ubuntu.com/edgy/net/denyhosts)

[http://packages.ubuntu.com/edgy/net/fail2ban](http://packages.ubuntu.com/edgy/net/fail2ban)

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firewall&searchon=all&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firewall&searchon=all&subword=1&version=edgy&release=all)

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=intrusion&searchon=all&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=intrusion&searchon=all&subword=1&version=edgy&release=all)

---

### Post by zarg@henrikke on 2007-03-30
Thanks for the links!

However, I was not looking for a blooted python package... when this task can be done in a few lines of bash script or C program. 

My Ubuntu run on a box with only 150 Mb of RAM... :roll:

---

### Post by Mr. C. on 2007-03-30
Don't worry about the script kiddies - with strong pass phrases (instead of passwords) they will not be cracking your system via SSH.

Reactive firewalls are overkill in my opinion; the essentially just moving the logging from one location to another (eg. syslog to firewall's log).

The more complex your solution, the more likely there are chances for configuration errors.

If you only connect to SSH from known IPs, simply enable port forwarding to SSH from those IPs.

MrC

---

