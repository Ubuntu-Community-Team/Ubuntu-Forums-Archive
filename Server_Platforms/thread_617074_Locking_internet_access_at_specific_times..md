---
title: "Locking internet access at specific times."
date: 2007-11-19
forum: Server Platforms
---

### Post by LRC on 2007-11-19
I know that there are programs for Windows that enable you to lock out access to the internet at desired times of the day based upon the day of the week. For filtering I am using Dansguardian very successfully. The question I have is is there something I can add to the conf file, the firewall (using firehol) or iptables that could serve that purpose? Or is there some other apt that can do that?

---

### Post by HermanAB on 2007-11-19
If you wish to stop network connectivity for all users, then you can simply use cron to take the ethernet port up/down with "ifconfig eth0 down" for example.

However, Dansguardian should be able to do it on a per user basis.  Go to the Dan's Guardian web site and read some.

Cheers,

Herman

---

### Post by LRC on 2007-11-23
I'm a noobie where it comes to manipulating linux. Where would I find a simple straight forward page discribing how to setup such a cron? I find that most pages go into stuff that is way beyond anything I need or want and just confuse me to no end usually landing me into major trouble.

---

### Post by UbuWu on 2007-11-24
Iptables can do that for you:

[http://www.google.com/search?q=cache:U3FqdUI4hfYJ:www.cyberguard.info/snapgear/cgi-bin/fom%3Ffile%3D314+iptables+filter+timestart&hl=en&ct=clnk&cd=1&client=firefox-a](http://www.google.com/search?q=cache:U3FqdUI4hfYJ:www.cyberguard.info/snapgear/cgi-bin/fom%3Ffile%3D314+iptables+filter+timestart&hl=en&ct=clnk&cd=1&client=firefox-a)

---

### Post by LRC on 2007-12-02
That link didn't work, but I figure since I am using dansguardian, the simplest way would be to kill DG and then start it up again at a specific time. I did try '0 11 * * 1-5 /etc/init.d/dansguardian stop', but that didn't work either. I then came to a possible solution of  '0 11 * * 1-5 /etc/init.d/dansguardian -KILL -u bryan'. Now I haven't found if that works, but I do see a possible problem in that if the computer is off during that time span would not the internet become available at bootup? A work around might be a script that could do the work,but I would not know how to be gin doing that.

---

