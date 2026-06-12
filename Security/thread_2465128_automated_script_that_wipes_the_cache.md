---
title: "automated script that wipes the cache"
date: 2021-07-22
forum: Security
---

### Post by swangnation on 2021-07-22
Hi guys, I've been away from ubuntu for a little while and I ask for patience as i am not sure if i am asking this question correctly.
I currently have an alias which wipes my cache. Its really basic but i would like to improve it.

My intention is simple ( i think ); in case someone is able to latch on to my computer, i do not want them to see what i have been researching or doing or viewing online.

Can anyone give me some ideas as how to create a script that automates the process of wiping the data that's necessary to wipe out. Keep in mind that this alias or script would need to operated from the terminal after internet connections have been stopped.

Thanks to all who read this and help in advance. Almost forgot. I'm using ubuntu 20.04

---

### Post by scorp123 on 2021-07-23
> **swangnation said:**
>  Keep in mind that this alias or script would need to operated from the terminal after internet connections have been stopped.

Why?

You could create a custom shell script that will launch your browser of choice (e.g. Firefox, Chromium, Chrome, ... or whatever it is you use) and then goes and wipes everything by itself once the last browser window closes. Also: all browsers offer a *"Privacy Mode"* or *"Incognito Mode"* these days so they themselves will wipe everything once your session closes. Did you ever consider using that? No need to do this manually or via script in that case.

Also: your provider, or the owner of the WiFi access point you might happen to be using at that moment (e.g. in a restaurant? at work? at school? ... you get the idea) can still easily see what addresses you have been visiting. So if you are concerned about your privacy please consider getting yourself a VPN ...

A VPN is still not 100% "foolproof", depending on various things such as who the VPN provider is and what you (ab)use it for, and what your overall usage patterns are. But it would offer one additional layer of privacy.

---

### Post by swangnation on 2021-07-23
> **scorp123 said:**
> Why?

You could create a custom shell script that will launch your browser of choice (e.g. Firefox, Chromium, Chrome, ... or whatever it is you use) and then goes and wipes everything by itself once the last browser window closes. Also: all browsers offer a *"Privacy Mode"* or *"Incognito Mode"* these days so they themselves will wipe everything once your session closes. Did you ever consider using that? No need to do this manually or via script in that case.

Also: your provider, or the owner of the WiFi access point you might happen to be using at that moment (e.g. in a restaurant? at work? at school? ... you get the idea) can still easily see what addresses you have been visiting. So if you are concerned about your privacy please consider getting yourself a VPN ...

A VPN is still not 100% "foolproof", depending on various things such as who the VPN provider is and what you (ab)use it for, and what your overall usage patterns are. But it would offer one additional layer of privacy.


i have it on good authority that when in "private or incognito' mode, the cache does not always get wiped. I've actually seen this myself a number of times already but on android devices not a computer. And...no I didn't consider creating a custom shell script that will launch my browser of choice. How would i go about doing that?

---

### Post by cmcanulty on 2021-07-23
I would just install bleachbit and you can choose to clean many things including browser caches

---

### Post by scorp123 on 2021-07-23
> **cmcanulty said:**
> I would just install bleachbit and you can choose to clean many things including browser caches

+1

Maybe the easiest approach for OP...

---

### Post by TheFu on 2021-07-23
Which cache do you want to wipe?  The CPU has a cache, a swap file is a kind of "cache", lots of programs have temporary files they call "cache".

If you don't want anything written to disk at all while using a program, why not just prevent that by using a pseudo-container like firejail?

I'm so confused.

For example:
```
/usr/bin/firejail  --private /usr/bin/chromium-browser
/usr/bin/firejail --private /usr/bin/firefox 
```

That would prevent both of those browsers from touching any local storage. I don't know if chromium works on 20.04 inside a firejail. I vaguely remember some conflict, which I assume was done by Google to prevent anti-tracking efforts.  I know that on 18.04 and earlier, it works fine.

To get a better understanding of firejail, open two terminals, in one run **firejail bash**. In the other, run **firejail --private bash**.  In each, look around, see what you can see. Create some temporary files in /tmp/, ~/ and ~/Downloads/ (use different file names for each firejail session), try to sudo.  See what happens.  Then 'exit' out of those programs and take a look for the temporary files.  Which are there?  Which are missing?  What happened with sudo?

Firejail is a handy little tool. Be certain to install both the firejail program AND the firejail profile packages.  May want to use the firejail PPA for the profile stuff, since browsers are updated often and seem to break old firejail profiles a few times a year. Getting the newer profiles automatically is good.

---

### Post by swangnation on 2021-07-23
Sorry for the confusion...you are right to ask which cache indeed. Any cache that gets written to when i am online.

---

### Post by TheFu on 2021-07-23
> **swangnation said:**
> Sorry for the confusion...you are right to ask which cache indeed. Any cache that gets written to when i am online.

That would be all of them. Both in hardware and in software.

---

### Post by swangnation on 2021-07-24
> **TheFu said:**
> That would be all of them. Both in hardware and in software.


I think for me it would be very practical to have a script that i can run from terminal. As i am still a bit of noob with ubuntu i'm asking for help on this. What would a bash script look like if i wanted to wipe all the caches? Can you guys help or would i be better off going to 'ask ubuntu'?

I'll amend this post...this is a learning curve for me anyway so i might as well start at the beginning. what commands do i need to locate the hardware caches? what commands do i need to locate the software caches? I think this is a better way to start because i haven't realised how complex my question may be. Apologies for that guys.

---

### Post by TheFu on 2021-07-24
I don't know of any way to flush the L1 or L2 cache from a CPU. Sorry.

I still think that the best answer was what I suggested in post #6 - prevent **anything** from being written to begin with. If it is never on disk, then you don't have to delete it.

But ... basic bash scripting isn't hard.  There are subtle things that are too hard to explain here, so best to share a screen with some people who know how to do it and talk through decisions.  
Beginning Bash scripting Guide:  [https://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](https://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)
Advanced Bash Scripting Guide: [https://tldp.org/LDP/abs/html/](https://tldp.org/LDP/abs/html/)

Also, your systems have different programs than my systems have, so the caches on my system are different from what are on yours.  There's no way any of us can 100% tell you how to find each program, then find the documentation for those (if there is any) and say that the disk cache for that program is 100% always in /x/y/z directory.  There are many, many, many, things that can change the locations.  Different DEs can use different cache locations - and depending on which release for each program, each DE, each user, the cache directory for each program can be in different places.

With all that said, you can look for directories with "cache" in their name.  There are system caches and per-userid caches.  System caches, say for APT, are under /var/lib ... somewhere.  I honestly don't know where system caches are for snap packages.  For userids, 99.999% of the time, the default locations for those would be under the userid's $HOME directory, which is held in the HOME environment variable, set at login time, based on the command 
getent passwd {userid}

The man page for the passwd file (not the command), explains which field holds the HOME directory setting, but most people would be able to recognize it in the : separated fields.  I could head of on a tangent about the passwd file, LDAP databases, and how /home/ isn't mandatory, just common on home Linux systems.  In a corporate environment with hundreds of users, I'd be surprised if /home/ was used for any Unix workstation.  It just isn't done.

There are probably GUI tools that will get most of the big cache directories for the top 5 popular programs.  But for the 20,000 other programs, who knows where they would put files?  In my code, I would always put cache files under /tmp/{userid}+{PID}/ and clean them up when the program was closed for any reason.  /tmp gets automatically cleaned up at reboot as well, so there is little cause for end-users to deal with it, unless their systems run for a month.  That can happen, here's one of my systems:
```
$ uptime 
 22:24:42 **up 21 days,  9:35**,  2 users,
```
But that box got patched to day and needs to be rebooted. All my systems need to be rebooted after today's patches.  I know this because the file, /var/run/reboot-needed exists.

Anyway, after you find all the cache directories, the script would just be rm commands.
```
#!/bin/bash

/bin/rm /path/to/cache/directory/*
/bin/rm /path/to/cache/directory2/*
/bin/rm  /another/path/to/different/cache/*

```
Is that helpful?  Be certain to make the file you put those commands into have execute permissions.
Another way would be to do this:
```
#!/bin/bash
/bin/rm /path/to/cache/directory/*  /path/to/cache/directory2/*   /another/path/to/different/cache/*

```
And another way that would only delete files over 1 day old is this:
```
#!/bin/bash
/usr/bin/find  /path/to/cache/directory  /path/to/cache/directory2   /another/path/to/different/cache -type f -mtime +1 -delete

```

Be careful with these commands.  Any files that get found either by the globbing or using 'find' will be removed. If stuff you don't want found gets found, it can be removed too.  I didn't show recursive removal in the first 2 example scripts, so and damage done would be limited.  But in the last script that uses the 'find' command, that one can wipe out millions of files if the paths are bad.  Be very careful.  Of course, the find in my example lists 3 directories to search in 1 command, but you could split that up into 3 find commands, each with 1 directory.

My scripting 101 article: [https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

Ok, a quick concrete example.
```
#!/bin/bash
/usr/bin/find     /u/thefu/.cache   -type f     -mtime +1     [COLOR="#FF0000"]-delete[/COLOR]

```

Let's see how much damage I could do with that script .... 
```
$ /usr/bin/find     ~/.cache   -type f     -mtime +1|wc -l
/usr/bin/find: &#8216;~/.cache/dconf&#8217;: Permission denied
13064
```
So, there are 13000 files in my personal "cache" directory that were last modified over 1 day ago.  How bad would it be to delete all those files?  Is it safe to delete those files when they are actively being used?  Obviously, I have a browser open right now, and there are many, many, browser cache files that I see there. Some of them are certainly open.  That's why I want the last modified time to be at least 1 day ago.  'find' has many, many, many, options to hone in on exactly the files or directories that we seek.  This is one of the few commands where seeing a _top 50 find examples_ webpage is extremely helpful.

BTW, in a script, never use ~/ and never use $HOME.  Those aren't normally set when we go to automate running a script via crontab and we really don't want a script to "find" anywhere we didn't intend.   What would happen if / was "found"? and we started deleting all the files not modified in the last day?  There's good news - Unix permissions should prevent any normal userid from deleting any system files, but every file in our HOME directory would likely get deleted.  I'm just trying to convey what could happen.  In 1996, I was a new Unix admin and wrote a little clean-up script.  Because it needed to delete old files from many different users, I ran it as root.  It found ./ which happened to be / at the time and started to delete the entire OS on a relatively new server.  I was fortunate in that the day prior, I'd just made a full system backup to tape, but I didn't know how to restore it yet.  Ended up running to the local Microcenter and buying a book _Essential System Administration_. I gave away that 1996 version long ago, but still have the 3rd edition within arms reach now.

Anyways, be careful deleting files in a script. The first few runs, use a different command, perhaps 'ls' rather than delete. Look carefully at the files.

---

### Post by swangnation on 2021-07-25
Your response is very enlightening and helpful and i almost regret asking about this as I now see the implication of my question/query. I think what i want to do simply isn't done in this way. (forgive my stubbornness) Nevertheless everything mentioned above will be noted and tried but ultimately I can see myself formatting all my drives, discarding this computer and literally starting from scratch as this computer is getting quite old, I've already replaced the motherboard once already anyway ....and THEN, your suggestion in #6 will HAVE to be the most viable solution. I will try all the above and start reading about firejail.

---

