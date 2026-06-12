---
title: "Security Issues Regarding Wordpress"
date: 2010-02-05
forum: Server Platforms
---

### Post by marty1011 on 2010-02-05
Hello everyone,

I am interested in creating a photoblog on **Wordpress.** Before I jump in I thought it would be wise to ask a few questions here first rather than getting into trouble and then firing absurd questions left and right. **I am not very experienced regarding servers but not afraid either**:D  I was reading How-to's online reagarding installing Wordpress on Linux [https://help.ubuntu.com/community/WordPress]("https://help.ubuntu.com/community/WordPress") and few questions came to mind :

**1) Like any other server, does the computer that will run Wordpress have to be up and running for 24/7?**

**2) Since I will install Wordpress on a desktop, should I be concerned about my machine being compromised? I am not an expert on internet security so this is a big concern of mine.**

[B]3) Is it a good idea to install Wordpress on a personal desktop at all? Does running Wordpress from a different partition of the hard drive (if it is possible) help at all.
[/B]
**Thank you for reading my poor English. Any replies will be greatly appreciated.** Links to any additional How-to's are also appreciated.

Regards
marty

---

### Post by FuturePilot on 2010-02-05
1. Yes

2. Yes you should be concerned about that, perhaps even more so being on a desktop machine.

3. There's no reason you couldn't install it on a desktop machine, but there's a number of reasons why you shouldn't (IMO). As mentioned before; security reasons. Also, performance reasons. In addition, if this is a home connection you should be aware of your upload speed as getting a lot of traffic will kill your internet connection. Installing Wordpress on a separate partition won't matter at all.

---

### Post by marty1011 on 2010-02-05
Thanks for your reply FuturePilot. I guess it would be better to search for an alternative. Does anyone have any idea or suggestions regarding the alternative to using Wordpress.

Many Thanks in advance.

Regards,

marty

---

### Post by hessiess on 2010-02-05
Wp is just a CMS, you would also be running Apache/PHP/Mysql as well. Yes it is posable to make such a setup very secure but not without using php as a cgi/fastcgi application with suexec, or creating a chroot jail or a virtual machine. Which means that you need a decent understanding of UNIX permissions and editing Apache configuration files.

Hosting anything, besides a personal webdev server off a home connection is a non starter because it will be extremely slow. Instead look into getting a shared hosting solution with an ISP, personally [one.com](http://www.one.com) have bean OK for me.

---

### Post by marty1011 on 2010-02-06
Thank You everyone for you informative replies. I think I will use Wordpress.com for now. Again Thanks a lot.

marty

---

