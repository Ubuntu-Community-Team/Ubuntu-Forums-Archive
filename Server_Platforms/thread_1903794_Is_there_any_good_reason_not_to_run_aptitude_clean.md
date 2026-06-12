---
title: "Is there any good reason not to run aptitude clean (or autoclean) weekly?"
date: 2012-01-03
forum: Server Platforms
---

### Post by saphil on 2012-01-03
I want to make weekly tarballs of /var, /etc, /home and /opt on my machine weekly and then ssh the tarballs to a remote location.  
```
aptitude clean 
```takes a lot out of the /var/cache/apt files and AFAIK removes the binaries from which installed packages are derived.
Is there any reason not to make this a cron job and run it weekly, or whenever ones updates are scheduled?

-Wolf

---

### Post by crazy bird on 2012-01-03
What you can do is using these commands:
 
> **sudo apt-get autoclean**
> **sudo apt-get autoremove**
 
You can also install deborphan and gtkorphan (= GUI for deborphan):
> **sudo apt-get install deborphan gtkorphan**

---

### Post by saphil on 2012-01-03
> **crazy bird said:**
> What you can do is using these commands:
 


 
You can also install deborphan and gtkorphan (= GUI for deborphan):
OK, I guess you don't see it as a bad idea.  
I just don't want to have to ship a lot of unnecessary binaries to backup.  It seems like, if I send the apt database and state, I can rebuild something similar to my machine if it happens to blow up.

---

### Post by ratcheer on 2012-01-03
I run aptitude autoclean regularly, and I have not noticed any problems from it.

Tim

---

### Post by crazy bird on 2012-01-03
> **saphil said:**
> OK, I guess you don't see it as a bad idea.  
I just don't want to have to ship a lot of unnecessary binaries to backup.  It seems like, if I send the apt database and state, I can rebuild something similar to my machine if it happens to blow up.

I don't think you understand what these 2 commands do. They both only clean up unnecessary packages that were installed by other packages which aren't needed any longer. It's like the same as under Synaptic Package Manager > option Status > Not Installed (Residual config). There you see also the packages which aren't needed any more. Those you can clean as well using Synaptic.

[Here some more info]("https://help.ubuntu.com/community/AptGet/Howto#Removal_commands"). [And here too]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html"). [Here also a website containing some info]("http://www.stchman.com/cleanup.html").

---

### Post by OrangeCrate on 2012-01-03
This will help...

**"HOWTO: Cleaning up all those unnecessary junk files..."**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

(Don't let the date of the thread fool you. It's as valid today, as when it was originally posted).

---

### Post by saphil on 2012-01-03
Now I am confused:
```
man aptitude 
 clean  Removes all previously downloaded .deb files from the package cache directory (usually /var/cache/apt/archives).        
 autoclean Removes any cached packages which can no longer be downloaded. This allows you to prevent a cache from growing out of control over time            without completely emptying it.
```So clean removes all the *.deb files in the cache, causing me to have to download them again if I need something different from the package and Autoclean just removes obsolete packages.

```
man apt-get
clean Clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. 
autoclean Like clean, autoclean clears out the local  repository of retrieved package files. The difference is that it only  removes package files that can no longer be downloaded, and are largely useless. This allows a  cache to be maintained over a long period of time without it growing out  of control. The configuration option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.
```This does approximately the same thing and so it would not matter if I use apt-get or aptitude (my choice, usually) in a script to shrink the cache size, would it?

```
man deborphan
deborphan  finds packages that have no packages depending on them. The default operation is to search only within the libs and oldlibs sections to hunt down unused libraries. 
```It looks like this command takes a much smaller selection of files - just lib files.
It looks like I have to see what an uncleaned cache contains, run deborphan on it, then run apt-get clean and see what is left then.

I have several machines to work on and I want to make a "final solution" so I don't have to visit all of them once a week for this kind of maintenance. 

Thanks for your help,

Wolf

---

### Post by saphil on 2012-01-03
> **OrangeCrate said:**
> This will help...

**"HOWTO: Cleaning up all those unnecessary junk files..."**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

(Don't let the date of the thread fool you. It's as valid today, as when it was originally posted).

That is a good how-to - Thanks.

---

### Post by OrangeCrate on 2012-01-03
^,

You're welcome.

:)

---

