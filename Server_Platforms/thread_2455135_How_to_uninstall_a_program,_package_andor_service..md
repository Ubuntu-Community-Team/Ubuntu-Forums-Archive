---
title: "How to uninstall a program, package and/or service."
date: 2020-12-13
forum: Server Platforms
---

### Post by serviteccom on 2020-12-13
Im a beginner about server topic, I install the last version of Ubuntu Server 20.04.1 and when the installation ended it showed a list of services or packages and without thinking what I was doing I checked every one of them.

Now I noted the system is consuming lot of resources (the fun speed is at high)

How can I check what services or packages I have and can I uninstalled those I think I wont use.

THANK YOU

---

### Post by SeijiSensei on 2020-12-13
If you haven't made many customizations, I suggest you just reinstall the OS and pay more attention at the end. Easier and faster than trying to diagnose where the problems are.

---

### Post by TheFu on 2020-12-13
> **serviteccom said:**
> Im a beginner about server topic, I install the last version of Ubuntu Server 20.04.1 and when the installation ended it showed a list of services or packages and without thinking what I was doing I checked every one of them.

Now I noted the system is consuming lot of resources (the fun speed is at high)

How can I check what services or packages I have and can I uninstalled those I think I wont use.

THANK YOU

As stated above, best not to install stuff on a whim because stuff-A will have dependencies on stuff-B, C, D, E, F and get those installed too.  The Unix philosophy isn't like Windows.  It is common to built stuff-A making use of excellent stuff from other projects and the package management system knows about dependencies, so it pulls those in automatically.  Some of those dependencies are just libraries - not actual programs that servers run.  Then you install thingy-Z and it depends on stuff-C, but not E, F, or B. Now stuff-C has multiple dependencies which are being tracked by the package management system for us. That's fine too.

Where people new-to-linux get into trouble is when they decide to install random package from outside the Canonical Repos using a .deb file directly.  To their minds, a .deb file is the same as a setup.exe - IT IS NOT.  .deb files are not usually standalone. They have dependencies and depending on who made the .deb package file, it could lock specific versions of those dependencies. This is common enough that in a few months, a new-to-linux person will end up with a system that cannot be updated/patched anymore due to a few random .deb file packages installed months ago which are holding back some dependencies which 50 other system packages need to patch.  

Ok ... so ... what should you do around package management when you are new-to-linux?
[LIST]
[*]Only install packages already listed in the package manager repos. Don't download .deb files directly.
[*]Pick one package manager and become familiar with that tool. They all use the same back-end libraries, but some have slightly different, useful, capabilities.  99% of the time, I use 'apt' as opposed to apt-get or aptitude or any GUI.  'apt' almost always does what I need and keeps me/us from getting into trouble.
[*]I avoid snap packages. Some of the GUI package managers will show snap packages but not clearly say what repercussions that choice forces.
[*]Bad things can happen, but the first thing you should do when you have a system even close to what you like is to begin making daily, automatic, versioned, backups.  Linux doesn't have anything like a "restore point" - well, it does - they are called _backups_.  Having backups that have been tested to restore and knowing you can restore to yesterday or last week or 7 weeks ago successfully is a good thing.  Most people need about 5 attempts to get backups working correctly AND to have the necessary restore steps down.  Until you actually do a restore, you don't know and will likely fail at restore time.
[/LIST]

If I don't show a sudo, then you don't need that.

How can you get a list of packages?
```
dpkg -l | egrep '^ii'
```
I doubt that is really very useful to you.

How can you get a list of running daemons?  Well, there is the 'good enough' answer and there is the 100% correct answer. Depending on what you've installed, the 'good enough' answer may have little bearing on some daemons.
```
systemctl status
```
You'll probably want to use redirection or a "pager" to see all the output.  A 'pager' shows stuff 1 page at a time. There are a few different ones - more and less are popular and each has uses.  'less' supports scrolling backwards in the buffer, which can be very handy, but it doesn't automatically move onto new files like 'more' does, which is also handy if looking through multiple files.

Unix is designed as a text processing/finding OS. It is freakin' amazing what can be accomplished with text input and output.  Having a list of installed packages can be a great help at restore time, BTW.  But with a little smart filtering so only the specific packages that I manually installed, not any automatic dependencies or any files installed as part of the OS install is really helpful. After all, package dependencies can change over time.
A few references for people running 'server' systems - i.e. non-GUIs.
[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

My base server install includes only the openssh packages from that list of extra things (mysql/apache/wormhole ....) to install.  All my systems run ssh, period. More details: [https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) Hopefuly, this is helpful - or just ignore if not.

---

### Post by serviteccom on 2020-12-14
Guys you just don't know how useful Is this info for me, Ill start over reinstalling the server, thank you very much!

---

### Post by Doug S on 2020-12-14
> **serviteccom said:**
> Now I noted the system is consuming lot of resources (the fun speed is at high)There is a lot of good information in this thread. Myself, I don't think it'll make any difference to your root issue. Anyway, if you still have high fan speed after you re-install, start a new thread, also providing some CPU load information. Sometimes a highly spinning fan does so without cause.

---

