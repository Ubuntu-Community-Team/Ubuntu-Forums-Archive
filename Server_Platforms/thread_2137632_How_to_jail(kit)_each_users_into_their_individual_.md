---
title: "How to jail(kit) each users into their individual home directories using bash script?"
date: 2013-04-21
forum: Server Platforms
---

### Post by Messzir on 2013-04-21
[COLOR=#000000][FONT=Arial]I am using Ubuntu 12.10, Apache2.2, PHP-FPM. My aim is to set up a working (free) shared hosting system, that means I want to create new Linux users and jail (equals to chroot, I guess) them into their home directories so they absolutely won't have permission to touch the main file system or other users' files. I set each virtualhost's DocumentRoot to a public_html folder in the home directories.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have already done all of this, expect jailing. I looked after the topic and I found **Jailkit** that looked pretty easy, but unfortunately I couldn't get it worked. I followed [this]("http://www.marthijnvandenheuvel.com/2010/03/10/how-to-create-a-chroot-ssh-user-in-ubuntu/") tutorial but except /home/jail I used /home/tom (tom is the example user) but when I logged in as tom, I could go up to the root directory. Moreover, I set individual PHP-FPM pools to each virtualhosts for security so if you open tom.mywebsite.com and see who runs PHP ( echo `whoami`; ) it will print out tom. The other thing I set for them is open_basedir (of PHP). I don't really know what does it do and does it really counts (if I set chroot) or is it enough for now, but I set it. So the long and the short, problem is no matter if I set proftpd or other ftp programs to don't let USER going up in folders and browse, there will always be PHP where he can do it.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So the task: set chroot for each users (using Linux bash script) so **don't allow them to browse other users' files** and **don't let them to crash system**.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thank you for your constructing comment and help in advance.[/FONT][/COLOR]

---

### Post by kevdog on 2013-04-21
I remember playing with jailkit a long time ago and I think your directory structure is incorrect. I think it needs to be /home/tom/home/tom or something like that.  (Yes I know its redundant, however the jail can go cd higher than /home/tom.  Please re-read the jailkit instructions.  Although I did it a long time a go, the scripts worked as instructed, however it took a little bit of reading.  jailkit hasn't been updated a lot recently -- not that that is a bad thing -- it just means that I don't think they really changed their structure for setting up jails by adding new features.  Also the jailkit forums do get a reply if you post -- its just not as fast as the Ubuntu forums.  I still believe oliver (the maintainer of the scripts) still responds on a fairly regular basis.

---

### Post by Messzir on 2013-04-22
Firstly, thanks for your reply. I have also tried that, but it didn't work for me. However, the tutorial uses /home/jail as chroot directory so I don't undersand why is it wrong. Anyway, thanks for recommending Jailkit forums, I will definitely start a new topic there.

---

