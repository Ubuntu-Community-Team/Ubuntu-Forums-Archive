---
title: "[SOLVED] Questions from another Rookie?"
date: 2008-06-17
forum: Security
---

### Post by De Rookie on 2008-06-17
My apologies to all those tired of the newbies asking redundant questions that have already been answered on the boards. Believe me I've read and read but the answers I've seen weren't really applicable to my concerns. Please take pity on a Microsoft Escapee full of Anexiety.

1. How do I make a still functional User Account to use for general browsing, that cannot access the powerful SUDO command and should this be a concern anyway?

2. If I enable seLinux, have I actually helped to harden the system from internet exploits and hackers? 

3. As far as security is concerned; What exactly is a service, and How do I know if a service is opening a port to the internet and making my computer less secure? 

4. I know Java is a service (I'm reasonably sure it's not safe anywhere) but are programs like Pidgin, Opera Browser, Evolution, Firefox, adobe Flash? Can they be ran securely, do they open ports or allow exploits? 

5. What is Synoptic? How do I use it and are the available plugins considered secure?  

6. What if I install Wine and run my old windows games can I do so without fear of opening exploits via those .dll files 

7. Metadata??? Do plug-ins contain metadata streams? in Ubunutu or Linux should I even be concerned? 

8. Administrative privileges?  Since I am the administrator is there an Administrators guide designed for Rookies? What books are out there for Debian or Ubuntu that will overall get me up to speed? With 

9. I would like to use a Web-Cam capable messenger program that has some privacy features, anyone know of an open source or GPL liscensed one?

After the install of 8.04 is there any immediate steps I should take for keeping this desktop safe or making it safer?
I saw a thread in Security that concerned me called "hack me" it was suspended 2 weeks ago, although the overall thread was encouraging, it referred to opening ports and running services which caused me some alarm. I'm not running a server, I don't even use an email client. I'm just the guy who got sick of Microsoft's devotion to spying (one of my hopes is to eventually ban Microsoft, Google, Yahoo, and adobe as well as their partners permanently from my desktop) and escalating my computing costs and decided it was time for a change, only problem is now I'm in unfamiliar waters.

---

### Post by HermanAB on 2008-06-17
1. Don't bother
2. SE Linux doesn't do what you think it does.  It is mainly useful to separate classified information on a single machine, so its main purpose is for use in military installations.
3. The command 'ps -e' lists all running processes.  You can scan your machine from another machine using 'nmap -sT -P0 -v -F 1.2.3.4' to see what is listening.  In general though, don't worry too much about it.
4. Don't worry about it.
5. Synaptic is the software install utility - it is in a menu somewhere.
6. Wine is secure, since it is different from Windows.  It breaks all known viruses.
7. Don't worry about it.
8. The first user account defined in Ubuntu has administrator privileges through sudo.
9. Don't know any.  Skype works.

Last: Don't fix it if it ain't broke.  Newbies tend to break their systems when they do updates, so don't do that.  Wait till the next Ubuntu release in 6 months and install from scratch.

---

### Post by The Cog on 2008-06-19
HermanAB knows what he's talking about, but I have a few slightly different opinions:

1: Only users who belong to the group **admin** can use sudo. By default, only the first user created when installing belongs to admin but your users and groups config can add/remove others. I wouldn't bother to make a separate account for my own browsing (which is what I think HermanAB meant) but I do for other other family members, especially a curious and over-confident son.

3: A service is a long-running Windiws process that exists to do work for other processes on request. It is architecturally different to normal Windows user processes. Normal Windows user processes always have to have a Window in order to work and therefore cannot run unless the user is currently logged in. The Unix equivalent would be a daemon, which would be any process that runs continuously regardless of who happens to log in and out. Users can leave processes running on Unix so there is no need for a special work-round.
**sudo netstat -plat**
will list the open TCP ports and processes that own them.

4: Java is a programming language and an interpreter. It is no more/less dangerous than Python, Perl, flash etc although MS would like you to think different of course. It is of course a lot safer than Active-X, which allows wholesale re-writing of the operating system through the browser.

5:

---

### Post by gaten on 2008-06-19
The above posts had some really good info, so I'm going to throw in my 2 cents.

First, I'd like to mention that your Ubuntu system, as it is installed, is quite secure. But like anything else, the security can be improved, so here are some of my suggestions on doing so. You do not have to follow this advice to have a secure system, but it can help. For right now I would suggest you learn as much as possible before you start tinkering.

1) I personally do make a different user account for web browsing. I do this because the web browser is the most common internet facing program we use, and there are exploits discovered *all the time*. For instance, Firefox 3 was released yesterday, and there are already a vulnerability reported ([http://dvlabs.tippingpoint.com/blog/2008/06/18/vulnerability-in-mozilla-firefox-30](http://dvlabs.tippingpoint.com/blog/2008/06/18/vulnerability-in-mozilla-firefox-30)). And many Linux users point to the Linux system model of user and system separation. But my point is this: if you web browser gets owned, all of your personal files are owned. 

2) SELinux is a very powerful tool for system security, and as such it's quite complicated. If you would like to play with it, I would recommend you do not install it on your main machine, but instead in a VM somewhere. I believe SELinux to be a great resource, but for a new Linux user, it's a little too daunting a task. 

3) Once you start running servers (such as SSH or Apache), you start opening up ports and you should worry about those things. Combine the answers of the posters above and you will be able to draw a nice map of what your system looks like to the outside world. Google for things like "nmap scanning" or "port scans" and read about it.

4) I disable all Java and Javascript through my browser, but I'm a little paranoid (if you haven't guessed). I use the NoScript add-on for Firefox, and I believe it's the most important add-on you can have for Firefox. Any program that's connected to the internet is a potential danger, so keep that in mind.

8) There are *tons* of guides out there for people like you. Some of my favorites sites for tutorials:
[http://www.howtoforge.com/](http://www.howtoforge.com/)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://vntutor.blogspot.com/2007/06/free-online-ubuntu-linux-books.html](http://vntutor.blogspot.com/2007/06/free-online-ubuntu-linux-books.html)
[http://tuxtraining.com/](http://tuxtraining.com/)

Enjoy!

Welcome to the wonderful world of Linux, I hope you enjoy your stay. The road is long and often bumpy, but it's wonderful journey. Be ready to learn, to fail, and to suceed.

---

### Post by De Rookie on 2008-06-19
Thanks for the quick and especially for the more informative responses.  Like I probably said I read a lot. I've discovered Bastille to help lock out things like FTP and UDP packets etc...I guess seLinux wasn't what I was looking for but it looks like Bastille may be the hardening tool I wanted to turn off things like FTP and UDP packets and other things I don't think I use as well as helping to limit user accounts. It also has password protection for things like Grub on startup. Bastille seems to have applied seemlessly (only 4 or 5 errors I'll have to resolve). Got any better utilities I haven't read about yet? 

So far so good, I've installed something actually used it to give a better sense of and the computer still works

I expect while I'm learning I will probably accidentally crash this OS a few times but hopefully, it'll be my error and not someone elses malicious intent. 

(slightly off subject and thinking of messing things up) After upgrading from Fiesty Fawn 7.04 via the link in upgrade manager. I downloaded and the 8.04 LTS image burned it to CD and tried a cd install from bootup. It booted up with overlapping displays or a fuzzy ghosting pattern. I wiped the hard drive and tried it again only to get the same bad display. Finally I wiped again and installed 7.04 upgraded all the way with the Upgrade Manager and everything seems fine. With the garbled display was the disk no good or did I just install over the previous OS leaving both trying to run? 

Being a windows escapee and therefore a script kiddie by default, I'm use to having memory eater programs Antivirus, firewalls, anti-malware, privacy, cache and registry cleaners as well as tools like HJT and later the Opera Browser (no active-X and, on demand ad-blocking) I am encouraged again, like if I learn enough about Debian, maybe I might actually be able to control my computer again for the first time since 1999. Thanks for the info.

---

### Post by gaten on 2008-06-19
Bastille is awesome, that's about the best system hardening script I've used. For system monitoring, look into OSSEC. 

> I expect while I'm learning I will probably accidentally crash this OS a few times but hopefully, it'll be my error and not someone elses malicious intent.

I can't tell you how many times I've screwed up my own system- it's all part of the learning process!

> (slightly off subject and thinking of messing things up) After upgrading from Fiesty Fawn 7.04 via the link in upgrade manager. I downloaded and the 8.04 LTS image burned it to CD and tried a cd install from bootup. It booted up with overlapping displays or a fuzzy ghosting pattern. I wiped the hard drive and tried it again only to get the same bad display. Finally I wiped again and installed 7.04 upgraded all the way with the Upgrade Manager and everything seems fine. With the garbled display was the disk no good or did I just install over the previous OS leaving both trying to run?

That's a video card problem. Try "Safe Graphics Mode" or the alternate CD. I always use the alternate CD because the Ubuntu installer does not like my dual nVidia graphics cards for some reason.

> Being a windows escapee and therefore a script kiddie by default, I'm use to having memory eater programs Antivirus, firewalls, anti-malware, privacy, cache and registry cleaners as well as tools like HJT and later the Opera Browser (no active-X and, on demand ad-blocking)

That's my favorite part about moving from Windows to Linux- I don't need to spend hours each week cleaning, scanning, and disinfecting my machine. Enjoy the ride!

---

