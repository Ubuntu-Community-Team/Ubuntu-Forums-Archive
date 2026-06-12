---
title: "How do I monitor who is loading files on my server ? (Apache PHP)"
date: 2020-04-01
forum: Server Platforms
---

### Post by cyprusspirit on 2020-04-01
Hello my friends. I am using Ubuntu to run a web server with Apache, PHP and MySQL.

How can I monitor who is loading files on my server and which files are opened in PHP? 

Do you have any answers?

Thank you !

---

### Post by TheFu on 2020-04-01
IF they go through apache, then the apache logs.  There are lots of different "analytics" tools, but they require a little effort to install and configure.  I use awstats, but that's because I care about the privacy of my visitors.  There are external companies happy to make it easier, for you selling out your visitors privacy.  Up to you.
[https://help.ubuntu.com/community/AWStats](https://help.ubuntu.com/community/AWStats)

As for people using other methods like plain FTP or scp or sftp or rsync, each of those should have log files.
There are 50+ other "back door" techniques commonly used by crackers. Those won't show up in a log, so only a network packet sniffer will catch them but every packet needs to be analyzed. That is usually a heavy process/effort so most people use network port mirroring to send all the packets multiple places for IDS processing.  Snort is popular.

Just depends on what you need.

OTOH, if crackers have access to the system already, at this point it is too late. The only purpse for that system is to learn what happened, figure out how to secure it better, then blow the box away an of thed restore from a backup made that you are 100% positive happened before any cracker gained access.  If you have versioned backups, say 180 days worth, then looking through the different version differences could help to figure out exactly when the crack happened.

---

### Post by cyprusspirit on 2020-04-01
Thank you for your answer. I will have a look at that [AWStats]("https://help.ubuntu.com/community/AWStats"). 

But I mostly want to monitor PHP. Which files PHP opened, which files it closed and make sure that there were no dead loops in the code. 

Thanks

---

### Post by TheFu on 2020-04-01
> **cyprusspirit said:**
>  But I mostly want to monitor PHP. Which files PHP opened, which files it closed and make sure that there were no dead loops in the code. 

Thanks

Well, then you'll need to modify the code to generate any logs you want.  I don't touch php, but in the other 20+ languages I know, there are many techniques to handle logging at whatever level you seek.  They all require code changes.  A common method is to have a logging class that gets used for every entrance into every subroutine/method and every exit from every  subroutine/method.  Those loggers usually have 5 levels of logging and each call is specifically set to one of those levels so that 
0 - no logging
1 - Critical errors
2 - all errors
3 - warnings
4 - information
5 - everything, more than anyone wants

So, with logging level set to 5, every entrance/return for every call coded by the develop is logged. In C/C++, it is common to use macros __FILE__:__LINE__ so that every line can be traced.  We used this for our production code, so developers never had access to any production systems. The clients could change the log level in the startup config file and that would get re-read, immediately changing the logging level. They'd reproduce the issue, we'd get a copy of the logs and that would tell us exactly which code paths were used to cause it.  Made fixing any customer issues pretty trivial almost always.  Some multi-threaded code would be a little harder to figure out.  A good, dynamic, logging, system for all code is mandatory, IMHO.

---

### Post by cyprusspirit on 2020-04-01
__FILE__:__LINE__ is the same for php too!  Thanks for your post and information.

---

