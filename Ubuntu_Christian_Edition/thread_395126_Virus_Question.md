---
title: "Virus Question"
date: 2007-03-27
forum: Ubuntu Christian Edition
---

### Post by runkidrun on 2007-03-27
I have a quick question regarding linux and viruses. I had downloaded some files for a buddy of mine via my +christian+ ubuntu box. These files were for windows (.exe). After downloading all of them for him, I scanned them w/ Clam Anti-Virus. (I ran an update first!) After scanning w/ Clam AV it found 2 infected files. I removed the files and moved on. This arose the question: **Do Windows viruses affect the Linux OS structure?**

P.S. I have the updates but it tells me to upgrade to the new version of Clam AV ... How do I update the whole program?

Thank You In Advance,

RunKidRun :guitar:

---

### Post by WiseElben on 2007-03-27
No, Windows viruses cannot affect your Linux system. Scanning for viruses on Linux doesn't really help you, but others that you might pass the virus to.

---

### Post by az on 2007-03-27
> **runkidrun said:**
>  **Do Windows viruses affect the Linux OS structure?**


Windows viruses and other kinds of malware are built for and only affect windows.  Malware is relatively easy to deploy on a closed-source OS where you install packages from many different sources.  It is a lot harder to get malware onto an OS that is open source and distributed from centralised repositories.

No OS is free of vulnerabilities, though.  The only thing you need to do when running Ubuntu (or any other GNU/Linux) is to keep up-to-date with your updates.

That's it.

---

### Post by Daveski on 2007-03-27
> **runkidrun said:**
> 
P.S. I have the updates but it tells me to upgrade to the new version of Clam AV ... How do I update the whole program?


I have a friend who has ClamAV and KlamAV front-ends installed via the repositories. The only way we could update was either was by running the download/compile/install wizard and then routing around for dependent packages each time it failed, and trying again (and again etc.).

KlamAV required us to download the installer from the website and manually kicking off the compile/install script - which involved hunting for more packages each time it failed. Eventually we got all the headers and libraries required and installed to the newest version.

The packages were often not named the same as in the error messages and so required quite a bit of hunting. It is a shame that the version in the repositories are out of date and do not update easily.

---

### Post by kc1di on 2007-03-30
> **Daveski said:**
> I have a friend who has ClamAV and KlamAV front-ends installed via the repositories. The only way we could update was either was by running the download/compile/install wizard and then routing around for dependent packages each time it failed, and trying again (and again etc.).

KlamAV required us to download the installer from the website and manually kicking off the compile/install script - which involved hunting for more packages each time it failed. Eventually we got all the headers and libraries required and installed to the newest version.

The packages were often not named the same as in the error messages and so required quite a bit of hunting. It is a shame that the version in the repositories are out of date and do not update easily.

Congratulations on sticking with it I got frustrated with trying to upgrade ClamAV and downloaded Avast.  It works great and have never had a problem with upgrading it.  I would recommend it.  How ever I will get flamed for not using and Open sourced package.  But at some point we have to have something that will work also.  As others have said I'm not terribly concerned about viruses that will affect my Linux machines.. but I must inter act with many windows users each day and no sense in passing the ugly critters along to them.
Blessings,
David

---

### Post by justin whitaker on 2007-03-30
> **WiseElben said:**
> No, Windows viruses cannot affect your Linux system. Scanning for viruses on Linux doesn't really help you, but others that you might pass the virus to.

Actually, you can royally mess up an unprotected Linux system if you execute a Windows virus via WINE. Not enough to take the system down, but certainly enough to create some work for you to get it straightened out. There was a thread on this a while back...

[http://www.ubuntuforums.org/showthread.php?t=72598&highlight=virus+wine](http://www.ubuntuforums.org/showthread.php?t=72598&highlight=virus+wine)

But so long as you aren't executing anything with WINE, you are right.

---

### Post by aysiu on 2007-03-30
I think you should read this:
[http://psychocats.net/ubuntu/security#firewallantivirus](http://psychocats.net/ubuntu/security#firewallantivirus)

---

### Post by Wiebelhaus on 2007-03-31
I'm a linux noob , by reading this I'm getting the impression that you just need to keep your ubuntu installation up to date and not to worry about installing anti-virus?

---

### Post by aysiu on 2007-03-31
> **sx66gns said:**
> I'm a linux noob , by reading this I'm getting the impression that you just need to keep your ubuntu installation up to date and not to worry about installing anti-virus?
Yes, and... don't do anything stupid, and use strong passwords (not weak ones).

---

### Post by Wiebelhaus on 2007-04-01
> **aysiu said:**
> Yes, and... don't do anything stupid, and use strong passwords (not weak ones).


thanks for the response.

---

### Post by Hendrixski on 2007-04-01
> **sx66gns said:**
> I'm a linux noob , by reading this I'm getting the impression that you just need to keep your ubuntu installation up to date and not to worry about installing anti-virus?

Yes.  I think I should explain why that is.  It's more a society issue than it is a technical issue.

If you're going to do something bad, like spy on somebody, or stab somebody, you will do it out of sight of everyone else.  If you're going to do something bad on a computer you will also do it where nobody can see it.  Thus unethical programs like Viruses, spyware, adware, etc. can only exist if they have a place to hide.

Theoretically,in a system where everything is transparent, where anyone can inspect what the code does, then viruses and spyware have NO PLACE TO HIDE.

---

### Post by shane2peru on 2007-04-02
I will sum [this thread]("http://www.ubuntuforums.org/showthread.php?t=72598") up for you.  I ran a virus (by accident) with wine.  It copied itself on 2 partitions of my hdd about 2000 times or somewhere in there in about 5 minutes.  Did it mess my system up?  No, however it was a real pain getting rid of it.  I ended up learning better how to use ClamAv and had it scan the entire computer and anything that was virus infected went to a folder for my examining, and then I deleted them.  It is potentially dangerous in that it can embed itself into other windows .exe files.  If you have or use win that could be problematic.  The only other potential danger is as stated passing them on to other windows users.  For that reason I run a virus scan regularly.  

As far as updating ClamAv, you can build it from source, it really isn't that hard.  I have done it a few times.

Shane

---

