---
title: "Different User Accounts for security, Worth it ?"
date: 2009-04-11
forum: Security
---

### Post by loudog23 on 2009-04-11
Hello Everyone,

A pologize in adavance for my poor english, i hope i will be clear in my question.

Doing research on security issues, i saw Somewhere that, it could be good to have a "daily" useraccount without root previledge for everyday use when running servers.

 I also found this thread [http://ubuntuforums.org/showthread.php?t=236834](http://ubuntuforums.org/showthread.php?t=236834) that says > for secuity reasons you should not run - under no circumstances, not even to test it - the teamspeak server binary as root. so lets create an user who will run our daemon.


I guess this has something to do with limiting the operation and file access to the user running the servers. And running yourself and restricted user for everyday use prevent someone from using your session to run malicious command.

Im my case, i've set up myself an apache server and proftpd server on my home machine (same as i use for music, browsing and torrent downloading. 

So what could be the safest setup for a system with Ubuntu hardy 8.10, dsl internet connection through a router (24/7) and servers (proftpd, apache) running almost all the time

a)
-set a crazy 20 digit password for the main user (created at installation) to run the servers.
-Create myself a 2nd restricted user account for my everyday use (browsing, music, torrent). 
-At boot, start the server under main account and then switch user
The main flaw i see here is keeping the server (main user) session active. Can someone use this session to run codes?

b)
-Use the main user (created at installation) for administration only
-Create a rescricted user account for the servers
-Create a resricted user account for myself
-At boot, start the server under main account and then switch user
In this case, the problem i can see is the not-sudoing user account for the servers, as they need root previelege to be started and stopped.

c)
-Im way to paranoid about it, just install everything on 1 account and set an 10 digit password. Keep all the port closed in my firewall (im concern about these passive ports) and router.

d)... [your input here] ;)

I would like to have some input as i'm re-installing fresh and was wondering what user to create a installation.
Thanks in advance.

EDIT: i just found this: [http://ubuntuforums.org/showthread.php?t=1122162](http://ubuntuforums.org/showthread.php?t=1122162)
So option b) could work if i specify use visudo?

---

### Post by bodhi.zazen on 2009-04-11
I would start with this thread :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

The first user is NOT root.

See : [RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

A second user can increase security, especially if restricted by AppArmor

See : [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

You can then restrict what the second user has access to.

Or not use apparmor and su to the first use to sysadim

Only you can decide how to configure your security, but my impression from your post is that you need to start with education.

---

### Post by loudog23 on 2009-04-29
Well, You gave me the best advise someone could gave me :P Education!

During the last 2 weeks, I've learn so much, ive done a fews fresh installation, tweaking, And securing. Now i have my own servers at home working smooth and fine. I had a few hack attemps according to my logs but no damage or succesfull attack so far. (as i know of)
> 
If you give a man a fish, he will eat for a days, If you teach a man how to fish, he will eat his whole life. 
It repesent the way i see my own security now, thank to your advise and education

So Thank so much for the reply :D
lou

---

