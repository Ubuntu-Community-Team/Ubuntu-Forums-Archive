---
title: "RKhunter"
date: 2009-03-05
forum: Security
---

### Post by boha on 2009-03-05
hi to all,

i have installed RKhunter from the repo, but i m unable to added it to a cron

rkhunter --cronjob do nothing!

and rkhunter --skip-keypress don t work either (for adding it myself to crontab)

in the config file no such option exists

rkhunter was last time in 2006 updated so does help at all (tough the creating  Hash feature for system files is quite cool) 

so at the end i added chkrootkit( an ohter tool) to crontab

so the question is the following: should i bother at all ? or does love and peace will triumph anyway :-\"





thanks for little advice

boha

---

### Post by HermanAB on 2009-03-05
No need to be so paranoid.  :)

I have never encountered a root kit and I have been using/administering Unix systems since about 1985.

Cheers,

Herman

---

### Post by bodhi.zazen on 2009-03-05
I suggest you start with this thread :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

The most common problem with cron jobs is that they run in a limited shell with a limited path.

So use the full path to rkhunter

/sbin/rkhunter (I do not know the path so you will have to check it).

---

### Post by hictio on 2009-03-05
Personally, I preffer to be paranoid, and have a working RKH on every Linux box I administer :D
IT runs via cronjob everyday, and besides the security measures/ checks, it also servers as a -somehow crude compared to Tripwire, for instance- data integrity tool and alert file changes.

Take a look here [Installing Rootkit Hunter on CentOS 5](http://oesediez.blogspot.com/2008/06/installing-rootkit-hunter-on-centos-5.html), it says CentOS, but for what you want -automatic execution via cronjob- towards the bottom of the page you'll find a one line script with email report to be executed by a daily cron.

---

### Post by csm888 on 2009-07-09
Well I got a rootkit that rkhunter picked up last week on one of my old servers (fyi: it was the t0rn v8 rootkit).
Since then I've installed rkhunter and tripwire on all my servers. 

To get error messages from cron add 
MAILTO=your_emailaddress

at the top of cron, you may see that the app your are trying to use isn't in the path, as crontab runs with a different environment. 
use 
whereis rkhunter
and then put the path into cron such as 
45 4 * * * /usr/bin/rkhunter --checkall --sk --nocolors

---

