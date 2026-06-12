---
title: "Ubuntu Server Install issues"
date: 2016-01-10
forum: Ubuntu, Linux and OS Chat
---

### Post by tbd2 on 2016-01-10
I don't know who did the Ubuntu Server install routine (especially the software install section) but they need to be pulled from the project because it is off the chart horrible. The software install section provides this extremely intuitive and confusing "GUI" that provides ZERO guidance on what is going on, what needs to be done, and if something fails how to fix it. This software install section is completely disjointed in look and feel from the rest of the install process. Making this more cohesive and intuitive would be a huge help.

---

### Post by TheFu on 2016-01-10
Thanks for the feedback.

"Server" is not targeted for new users, especially not for new-to-linux users. After all, how many Windows users will ever install Windows on their PCs? 3%? When they want a new version, they buy a new computer with the OS pre-installed.   Linux servers have thousands of possible configurations, perhaps millions. The intuitive setup is "next, next, next, next", but will likely fail on any odd hardware or end up with an undesired setup if there are multiple HDDs involved.  Plus, the "server" install has to work on any system from a 128MB RAM system to 256+GB RAM systems with any amount of storage available from ZERO (SAN connected storage) to googlebytes available. Some servers only have a console connection, others have GPUs meant to be used for scientific number crunching.  Basically, the admin and the installer has to have enough knowledge to understand the options. There are 50+ file systems available for Linux systems to use, add in LVM or not, any of the different encryption methods available, different cyphers, and things get complicated quickly.  Some level of skill is required from the administrator.

I find the Ubuntu Server installer extremely intuitive. We only run LTS releases, so haven't seen any since 14.04.x. We have different standards for how physical and virtual servers are installed.  Physical servers **always** use LVM, but virtual servers NEVER use it.  We always do a basic install, ssh-server only, then use a devops tool like ansible to setup and maintain the "snowflake" parts of the server. This makes managing and rebuilding our tiny number of virtual machines pretty easy. That isn't an excuse. The installation process should work for the intended people.

What other Linux "Server" distros have you tried?  6 months ago, I got into a loop with CentOS v7 installer over their LVM setup. It was confused that I wanted to wipe all partitions and start fresh, so it wouldn't let me do that inside the installer. Had to boot off alternate media, wipe the partitions and restart the CentOS installer - then it wasn't bad and worked great. Try the Arch or Slackware installers if you think Ubuntu Server is less than easy. ;)  I recall when the Slackware installer was considered the easiest by far - and it was, compared to SLS.

I don't have any idea how to provide guidance for *any level of user* to understand *what is going on, what needs to be done, and if something fails how to fix it.* There are just too many possibilities. My stance would be to remove all those other SW options and only allow an ssh-server to be installed. People who want a LAMP, VM, Print, DBMS, (or whatever else is shown) server should be able to install and configure those packages post-install. There are other opinions on this. ;)

Regardless, thanks for posting, style and cohesive considerations DO MATTER. There are always ways to improve.  IMHO, LVM setup can certainly use some improvement and more complex encryption options would be nice too. I know a few people are working on tools for that make a GUI LVM manager, but those are outside the installation.  Won't help me on servers, but perhaps the curses version would be able to mirror that tool?  Certainly patches to address the installation issues would be appreciated. 

I just re-read your post and can't say I understand what the issue really is.  How can it be both "extremely intuitive" and "confusing"? I'm confused.

The Ubuntu Server Admin documentation:  [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) is a good place to start, but there are many others. [https://debian-handbook.info/](https://debian-handbook.info/)  Ubuntu is based off Debian, so most things translate from 1 to the other.

Welcome to the forums. Hopefully, you'll hang out enough to aid the community too.

Update: In the world of commercial software, demanding that every feature work perfectly is expected.  In the world of volunteer-built software where few people actually get paid, it is best to use the software in the same way that most users do and avoid seldom used parts.  I install servers about 20 times a year, but **never** add extra software during the installation. I suspect many other people are like me and only install the base stuff too. Staying on well-worn use-paths is the safest way to avoid surprises. Not ideal, since things should work, however, I learned long ago that often the way I think something should work isn't always the smartest way for everyone or perhaps I just didn't have the background to understand everything the tool was trying to accomplish - basically, I was confused.  As the year pass and I become more attuned with a program, often the brilliance of the implementation becomes clearer. Not always, but sometimes.

The Ubuntu Forums aren't usually watched by developers, so posting here isn't going to get anyone to do anything.  If you really want to have someone take a look, there is a bug reporting system for that. This [https://help.ubuntu.com/lts/serverguide/reporting-bugs.html](https://help.ubuntu.com/lts/serverguide/reporting-bugs.html) and [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) seems to be the Ubuntu server bug reporting methods. Cumbersome? Perhaps.

---

### Post by deadflowr on 2016-01-10
No help asks for, so
Moved to Ubuntu Linux and Os Chat

---

### Post by tbd2 on 2016-01-10
I think my issues were relegated to the point where you pick to 'manage packages separately'. The rest of the install wasn't bad at all (I re-ran the install) but that section was so unbelievably confusing that it was unreal. Not only that I was completely unable to get any of the packages installed. It just could not find them for some reason. You guys need to look at this.

---

### Post by QIII on 2016-01-10
"Us guys"?  You mean those of us who are Canonical employees?

As this is a Forum of volunteer users and we aren't Canonical employees, this is likely the wrong tree you are barking up.

---

### Post by CharlesA on 2016-01-10
> **tbd2 said:**
> I think my issues were relegated to the point where you pick to 'manage packages separately'. The rest of the install wasn't bad at all (I re-ran the install) but that section was so unbelievably confusing that it was unreal. Not only that I was completely unable to get any of the packages installed. It just could not find them for some reason. You guys need to look at this.

Are you talking about this screen?

[ATTACH=CONFIG]266655[/ATTACH]

If that is the case, all the installer is doing is calling aptitude so you can pick which packages you want to install. What problem are you having with it?

This might help:
[https://help.ubuntu.com/lts/serverguide/aptitude.html](https://help.ubuntu.com/lts/serverguide/aptitude.html)

---

### Post by mastablasta on 2016-01-11
or use Zentyal - they have GUI installer and will also install a GUI by default (non expert mode)

wasn't tasksel called before? then you sleected what kind of server you want and it would install it. best to go with SSH only and add other stuff later on.

---

