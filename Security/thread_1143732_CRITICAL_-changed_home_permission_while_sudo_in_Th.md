---
title: "CRITICAL -changed home permission while sudo in Thunar (yes, it was stupid)"
date: 2009-04-30
forum: Security
---

### Post by rlb.contact on 2009-04-30
***
Please understand that this is **critical** . I have copies, **[COLOR=black]much[/COLOR]** needed copies, of tax documents and legal postings. Otherwise I'd just wipe the drive and start over again.
***
Orignally posted in General, but couldn't figure out how to cross post:

Run Xubuntu 8.10, but doubt it makes a difference.


I know it was stupid, but it was the easy way to go. 

Scenario:

I have three users under home file

home/user1
home/user2
home/user3

User1 is the only sudo approved user.

I want to secure all of the home folders from each other. User3 is particularly nosy. User2 is me for everyday life. I keep User1 for sudo tasks.

the whole chroot command line seems a bit convulted. 
I logged in as User1.

As User1 I started up Thunar with Sudo and changed the persmission on User2 and User3 with no problems. I decided to change permission on User1 as well. I completed the process, and all of my toolbars disappeared. I was forced to shut down via the power button.

Went to boot up and all I got to was a command line for the name of my computer and request for a user and password. I tried logging in as all possible users with no luck. I need to undo damage to home directories.

I DO NOT HAVE Xubuntu LIVECD.

That said, I do have a Xubuntu 8.10 install CD, which allows you to run Xubuntu from the CD (I have yet to figure out the difference.)
I only have CD Rescue. 

Can not find the actual directories on the hard drive. it shows an icon for the directory, but it only allows you to explore within the structure of the CD Rescue via bash or midnight commander. On Xubuntu Thunar shows the same problem. No matter where I looked, I couldn't find it.

Went to Xubuntu 8.10 CD.  Same problem. It's as if the hard drive never existed and everything was run from RAM/CD.

Questions:
1) How do I get to actual files on the harddrive?
Assumption:
I will only have the command line to work with.
2)Once there, how do I change the permissions with chroot or whatever.

Please help,
Thanks
Lee

---

### Post by bodhi.zazen on 2009-04-30
I closed this thread as first it belongs in general help and not security and second it is a duplicate of your first.

Please do not start multiple threads on the same topic, it causes confusion and duplication of effort.

I posted a solution in your original thread.

---

