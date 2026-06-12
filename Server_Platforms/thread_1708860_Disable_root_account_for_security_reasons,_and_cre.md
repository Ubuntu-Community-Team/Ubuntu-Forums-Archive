---
title: "Disable root account for security reasons, and create an admin account?"
date: 2011-03-17
forum: Server Platforms
---

### Post by Tumex on 2011-03-17
Hey there everybody!

I am pretty new at administrating a Ubuntu server but I have so far read that the 'root' account is quite risky to use in a production environment and it is therefore highly recommended to use another account, preferably one that has administrator rights but not necessarily "super admin" rights.

Now, while I certainly see the logic behind it, how would I go about attributing all the folders and files to the newly created administrator user, so that I don't have to have to deal with permission issues?

In other words, what I mean is how would I go about transferring every right/permission from root to the new user, without that new user necessarily becoming the new 'root' . For instance, I would like to be able to access the 'root' folder on the new user without being given a "denied" error.

I hope that you can understand what I mean and I would like to thank you very much for your help!

Tumex

---

### Post by vanadium on 2011-03-17
Don't. Use "sudo" instead. You can have a command line with permanent root permissions with "sudo -i" without having a root account enabled.

---

### Post by jerome1232 on 2011-03-17
Have a read


About Sudo and Ubuntu's locked root account
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

General Ubuntu Security
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Creating Apparmor profiles for your services
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by 1clue on 2011-03-17
Actually I think you should install a non-critical box once and try what you're talking about, just so you can see how totally messed up a system can get.  I did and never did figure out how to fix it, it's much easier to reinstall from scratch.

I'm being serious.  New UN*X people don't seem to have an appreciation of file and directory permissions.  If you can get it out of your system in a way that doesn't hurt anything that's necessary you can learn the easy way, rather than making a blunder when everyone depends on your system being up.

Personally, I did it in about as stupid a way as possible.  It was a production system, it was the peak load period of the day, and it was the most critical server in the company at the time.  Talk about high profile blunders.

---

### Post by jmacgowan on 2011-03-17
I agree with the replies before mine.
 
The task that you've asked the community to help you with is a most dangerous game.  Especially since you (and most people, including myself will never become experts on this so don't take offense) don't have an understanding of what *nix permissions really mean or how to exectue the proper commands, it would be irresponsible for us to give you copy & paste code of what you're asking for.  In the long run, it's just better.

---

