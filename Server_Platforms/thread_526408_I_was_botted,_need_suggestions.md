---
title: "I was botted, need suggestions"
date: 2007-08-15
forum: Server Platforms
---

### Post by fogNL on 2007-08-15
I'm normally a pretty security-minded person.  I know the basics, ensure you have an active firewall with minimal ports open, only run services that are nessesary, etc.

I'll admit, I did something really stupid.  A friend of mine wanted an account on my server (Ubuntu Server 6.06 LTS) so he could host his website from there.  So, I created him a username/password and gave him a temporary (easy) password that I was about to message him so he could log in and change.  After this, I got side-tracked and never sent him the message.  About 3 or 4 days later, my internet connection got disconnected due to "IRC Bot activity".  Baffled by this, I looked through my logs and found someone access the username with the temp password (it wasn't hard to guess, i was really stupid). After finding this out, i spent time going through my server and attempting to remove anything that was added on such as the username, clearing /tmp and checking active processes, netstat, logs, etc. 

After a few days without internet access, I thought I had it all cleaned up and so I called my ISP back and told them everything was good.  A few weeks passed, and I popped onto my server to do my weekly updates when I noticed my load average was around 3.00 which is way higher then the usual 0.90.  I checked top and it showed 3 perl processes that were using 33.3% CPU each.  I ran ps aux and found an executed script "perl b.txt" under the uid of www-data.  There was also an execution of /usr/local/bin/apache which is no longer there (i'm assuming the attacker compiled it, ran it, then deleted it leaving the process going).  A quick google search revealed that it was indeed an IRC bot that was using my server to do portscans and probably more (such as DOS attacks) which would explain why my net connection has been slow for the last few days.  When I looked through my auth logs, I couldn't find any failed attempts to connect or even an ssh auth at the time, all that was showing was a succesful login of www-data.

I'm assuming that whoever it was didn't get into the system a second time, rather there is something else running somewhere that spawned this problem.

my questions are, what can I do to clean my system (short of a re-install)?  What can I do to try and prevent this in the future with heavier security? I know I am the cause of the issue and won't make this mistake again, but I would like to make the server a little more secure.

Any suggestions?

---

### Post by dscherry on 2007-08-15
Hi,
This page has several suggestions, with instructions.

[http://www.howtoforge.com/scan_linux_for_rootkits](http://www.howtoforge.com/scan_linux_for_rootkits)

hth,
Dan

---

### Post by koenn on 2007-08-15
> **cquilliam said:**
> 
my questions are, what can I do to clean my system 

reinstall. No matter how much you clean, you're never going to be sure you've found everything. Someone who was able to install and run software on your computer can do pretty much everything. 
Ive seen malware that, while running, occasionally checks if its executable still exists on disk, and creates a new file if it got deleted. And it's perfectly feasible that a program you commonly use got replaced by one that, to you, looks like and behaves just as you expect,  but does al sorts of nasty things on the side. 

Reinstall - you're gonna feel a whole lot better afterwards.

---

### Post by notwen on 2007-08-15
> reinstall. No matter how much you clean, you're never going to be sure you've found everything. Someone who was able to install and run software on your computer can do pretty much everything.

Once someone infiltrates your system, format and re-install.  It is way too difficult to try and think of the where and when of tracking any unknown activity on said machine.  Why risk it. =]  Back up your needed data and wipe it.

---

### Post by fogNL on 2007-08-15
Alright, thank you for your suggestions, I will probably just go ahead and re-install and be much more picky about users and access to the system.

Is there any software out there that monitors system activity and alert you in some way if files are changed?

---

### Post by koenn on 2007-08-15
intrusion detection systems and rootkit hunters. See the sticky security thread for links.

---

### Post by skillllllz on 2007-08-15
> **cquilliam said:**
> ...Is there any software out there that monitors system activity and alert you in some way if files are changed?

Look into tripwire and rkhunter

---

### Post by tr333 on 2007-08-19
Don't forget to install [fail2ban](http://www.fail2ban.org/).  This should stop random bots scanning your machine.  It works by blocking access for a limited time to computers who have failed login attempts a certain number of times.

---

