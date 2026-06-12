---
title: "Migration from 32 bit to 64 bit?"
date: 2021-04-02
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2021-04-02
I have one server which is still 32 bit. I've been procrastinating about converting it to 64 bit. It wasn't causing any pain so I let it slide. I can't put it off any longer.

If I Recall Correctly it started out at 6.04 (Possibly even earlier since its first iteration was first installed in very late 2005 and early 2006). Since then it has had at least 2 cases, 4 motherboards and several upgrades of hard drives.

In any event I need to transfer everything on it to a 64 bit version of Ubuntu so I can continue to maintain everything going forward. The current hardware is 64 bit capable.  

I do have other computers I could use but they may need to have additional storage to hold everything. I could also clone the whole thing and go from there.

While the home directories and samba shares could easily be archived and restored as they are separate file systems, I also have backups. What really worries me is the configuration of other services since it also serves as a Samba Domain Controller and runs a few internal web applications using Apache2, php and mySQL. 

Has any one mapped out a process for doing such a transfer? I attempted to do the multi-arch thing a couple of times and failed miserably. I really dread what I'm about to do. Any help or pointers would be appreciated.

---

### Post by TheFu on 2021-04-02
I did this with a 16.04 desktop last June.

It is a full reinstall process, then recover whatever data and settings.  Depending on your backups, this can be a non-event or terrible.  My backups capture data and configurations.

It went like this:
[LIST=1]
[*]Fully patched 32-bit 16.04 
[*]Create a new backup
[*]Do a base install of 64-bit 16.04; patch it fully.
[*]Restore data and configuration files ... the system ones need to be restored only if I'd touched them.  I put comment-tags inside system files that I've touched so grep finds them at restore time.
[*]In my backups, I capture manually installed packages. Install those and only those. Let dependencies get pulled in by APT.
[*]Spend a few hours testing the most important things on a server and fixing those. Stuff that is broken at this point won't get better.
[*]Migrate to 64-bit 18.04. Test. Fix issues.
[/LIST]

I haven't taken any complex servers to 20.04 yet due to incompatible backup tools.  When I took the first desktop system to 20.04, I had to forward-port rdiff-backup to work due to the python3 change.  Fortunately, it was only a few libraries that weren't dependent on anything else that needed recompiling.  The way backup data is stored on disk didn't change, just the way it was transferred between the client and server had between python2 and python3. This took a day to solve, but it is 5 minutes now that I know how.  

For a long time, programs haven't cared about 32-bit/64-bit for storing data - at least not that I've seen in 15+ yrs.  I worked as a cross-platform C++ developer for about a decade. Started porting 32-bit software to 64-bit architectures in 1994. Back then, we had all sorts of issues due to compiler optimizations with the stack and passing values between functions/methods.  For a very long time, that hasn't been any issue.

Have you considered moving the 32-bit version into a VM? Really the DC and website shouldn't run in the same OS instance.  I wouldn't put  file sharing on a DC either.  A DC is a lite process, perfect for a VM, but file sharing needs direct access to storage. Two very different requirements and the DC needs much better security than almost anything else on a LAN.

IMHO.

---

### Post by ubfan1 on 2021-04-02
The process is driven by the cost of downtime.  Performance guarantee penalties may kick in at a certain point.  Set up a parallel 64 installation, and test the h*** out of it, run in parallel, use as backup domain controller, etc. Then switch primary/secondary, when the 64 bit is passing every test, and the 32 bit installation is acting as just a backup, then you can think of removing it.

---

### Post by rsteinmetz70112 on 2021-04-02
> **TheFu said:**
> I did this with a 16.04 desktop last June.

Have you considered moving the 32-bit version into a VM? Really the DC and website shouldn't run in the same OS instance.  I wouldn't put  file sharing on a DC either.  A DC is a lite process, perfect for a VM, but file sharing needs direct access to storage. Two very different requirements and the DC needs much better security than almost anything else on a LAN.

IMHO.

The current DC is using the old NT style Samba, again due to my procrastination.  I intend to migrate that to a AD-DC at some point so it won't be an issue. I already have an AD-DC running but it's not live since I need to learn more about how it works first.

---

### Post by rsteinmetz70112 on 2021-04-02
> **ubfan1 said:**
> The process is driven by the cost of downtime.  Performance guarantee penalties may kick in at a certain point.  Set up a parallel 64 installation, and test the h*** out of it, run in parallel, use as backup domain controller, etc. Then switch primary/secondary, when the 64 bit is passing every test, and the 32 bit installation is acting as just a backup, then you can think of removing it.

SInce these are servers for my own company no performance guarantees just additional cost due to unavailability plus the paid of it all.

---

### Post by ajgreeny on 2021-04-02
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit for this thread.

---

