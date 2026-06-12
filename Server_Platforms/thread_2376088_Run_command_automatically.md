---
title: "Run command automatically"
date: 2017-10-30
forum: Server Platforms
---

### Post by dam034 on 2017-10-30
Dear users,

I want to run a command automatically on my VPS, which is running the 16.04 server version.

These are examples:
```
mediatomb
```
```
node index.js
```
```
./my-app
```
Obviously, I can run the commands from my remote terminal, but I don't want to stop them when I exit the terminal.

And if possible, on special events I'll specify, I want to execute commands in the opened programs, e.g.:
```
root@myvps:/#mediatomb
[mediatomb] is running
refresh
```
When "refresh" is my command I write to do some operations.

How can I do?

Thanks

---

### Post by slickymaster on 2017-10-30
Thread moved to **Server Platforms** for a better fit

---

### Post by ian-weisser on 2017-10-30
There are several applications which keep applications alive when you close a terminal window, and permit you to access those applications from a later terminal window: Screen and Tmux are two of the most common.

Some of your jobs (like mediatomb and other servers) should be running as headless *services*, not in a terminal window at all.

---

### Post by LHammonds on 2017-10-30
> **dam034 said:**
> How can I do?
If you want to just fire-and-forget, you can use the following:
```
nohup YourCommand &
```
The "nohup" allows your process to continue even if your shell ends.
The "&" sends the command into the background so you can continue to do other tasks while it runs.

If you need to look at the output, you could also re-direct output to a log file and look at that...or run it inside a "screen" window that you have can running in the background and then bring it back to the foreground whenever you want.

You will need to read the manual on "screen" to get the basics though.  I use "screen" to manage multiple instances of my Minecraft servers and even inject commands to them via crontab such as during a reboot to let users know there is some downtime coming their way and when.

LHammonds

---

### Post by TheFu on 2017-10-30
You can make them into a system-wide daemon and run them as all the other system-wide daemons/services are run.  Just look for examples with your web server - how is that configured, started, stopped?

In the old days, we'd create/copy a script that was in /etc/init.d/.  That script knew how to start, stop, restart, status, and reload the program.  There are certainly examples of this on your server today.

For the last 8 yrs, Ubuntu used "upstart" to perform the same start/stop/restart ... stuff.  Forunately, it was backwards compatible with these "init" scripts that were used the prior 40 yrs.

Then systemd came along to solve all the problems that 1% of server admins had.  In their infinite wisdom, the different distros decided that everyone else needed to be "helped" by systemd too - even if we didn't want it.  Anyway, systemd has config files (which I've never used), but YOU can learn how to do it.  There are examples on your system.  Some examples are here: /etc/systemd/system
[https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers) might be helpful.

I don't want to be too pessimistic about systemd.  It does some things better/easier than what we had before, like restarting processes which have died.  It also helps out computers to appear to startup faster.  

Be aware that regardless of which method you use, that your script will need to correctly setup the environment variables necessary for each of those programs to run.  Programs started by the system don't have a login. They don't get much of an environment.  What does that mean?  Type "env" - see all that stuff? Most of that isn't set for system-wide daemons, so we need to artificially set it.  You can start with the 'env' list and pair it down to the 5 things needed for each program to work.  Usually 2-5 are needed.

Anyway, hopefully this will help you.

---

### Post by dam034 on 2017-10-30
So, I need:

[LIST]
[*]to run a command fire-and-forget
[*]to execute commands in those opened commands, also via HTTP API
[*]to see the output in a log file
[*]to stop and restart the commands
[/LIST]

Please, can you give me some examples (also in services mode)?


Thanks

---

### Post by ian-weisser on 2017-10-30
> **dam034 said:**
> Please, can you give me some examples (also in services mode)?

TheFu already provided you two examples and a reference wiki link.

---

### Post by dam034 on 2017-11-05
Sorry for the delay.

I partially read the guide posted by TheFu, and I'm asking to you: which you advice for me, upstart or systemd?

Thanks

---

### Post by ian-weisser on 2017-11-05
16.04 and newer: systemd
14.04: upstart

---

### Post by dam034 on 2017-11-07
Now I read all the guide.

Since I'm not an upstart user, and that guide is for upstart users whom are switching to systemd, which guide can I read?

I premise I never heard upstart or systemd, then I can't use them, pardon the ignorance.

Thanks

---

### Post by ian-weisser on 2017-11-07
There are many, many, many systemd tutorials just a search-engine away. 
Find one that matches your needs and learning style.

Do be aware that systemd requires a bit of learning and understanding.
Once you do understand it, it's quite easy.

---

### Post by dam034 on 2017-11-08
Yes I understand the basilar commands on ubuntu.

Before continuing, I read on the internet that it's better to use debian instead of ubuntu in production mode, and ubuntu for a personal server.

What I want to know is: systemd is the same on debian and ubuntu?


Thanks

---

### Post by ian-weisser on 2017-11-08
> **dam034 said:**
> I read on the internet that it's better to use debian instead of ubuntu in production mode, and ubuntu for a personal server.

Lots of dodgy advice on the dirty, dirty internet.
Netflix, Walmart, Amazon, Google, and many others use Ubuntu servers in production, so they might disagree with that assessment.
Ubuntu releases are based on Debian, and up-to-date sources are pulled every six months, so the differences are intentionally minor.
Ubuntu's Secret Sauce is a few patches (including branding), a QA and Security process managed by paid engineers, and a large volunteer testing and support community.  
The choice boils down to a matter of preference.

> **dam034 said:**
> What I want to know is: systemd is the same on debian and ubuntu?

Yes, in every important way.

---

### Post by dam034 on 2017-11-08
> **ian-weisser said:**
> Lots of dodgy advice on the dirty, dirty internet.
Netflix, Walmart, Amazon, Google, and many others use Ubuntu servers in production, so they might disagree with that assessment.
Ubuntu releases are based on Debian, and up-to-date sources are pulled every six months, so the differences are intentionally minor.
Ubuntu's Secret Sauce is a few patches (including branding), a QA and Security process managed by paid engineers, and a large volunteer testing and support community.  
The choice boils down to a matter of preference.
Yes, in fact I had doubts regarding the ubuntu support, because I saw the ubuntu and debian communities and I thought ubuntu is better.
Also the wiki, this forum and OS docs are better. It was only to know.

> **ian-weisser said:**
> Yes, in every important way.
Now, if I want to run a command (e.g. "node index.js"), can you please give me an example how to do it, and run sub-commands and quit it by systemd?


Thanks

---

### Post by TheFu on 2017-11-08
> **dam034 said:**
> Yes I understand the basilar commands on ubuntu.

Before continuing, I read on the internet that it's better to use debian instead of ubuntu in production mode, and ubuntu for a personal server.

What I want to know is: systemd is the same on debian and ubuntu?

Everyone on the internet has an opinion.  There are times with debian is better and there are times with Ubuntu is better and there are times with CentOS is better and there are times with tinycore, core, SuSE, Arch, Gentoo ... each are better.

As you might expect, people here will lean towards Ubuntu for servers.  I do, but I also run Debian and CentOS servers. However, most of my servers are Ubuntu and I have a number of reasons for this.

Also, I won't run node or php webapps on the public internet.  I have reasons for that as well.  I do run 2 php webapps that are only available from inside our network or via VPN.  I've seen too many of those webapps get hacked to believe they can be secured.  That is MY opinion.  People who use php likely have a different opinion and they probably have good reasons too.

I would assume that systemd is almost the same between debian and ubuntu and Linux-Mint and all the others using systemd.  I say that because most things across all Linux distros are very similar, when they use the same tools.  The primary differences are with package managers and where config files might be located.  Debian and Ubuntu keep their config files in the same places. RHEL/CentOS go in slightly different, but still similar locations.

systemd is new enough that I haven't needed to learn it yet.  My servers don't use it. They run older distros.  Sorry I'm not more helpful.

---

