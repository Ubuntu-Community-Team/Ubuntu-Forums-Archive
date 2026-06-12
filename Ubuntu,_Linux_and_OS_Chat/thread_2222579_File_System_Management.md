---
title: "File System Management"
date: 2014-05-07
forum: Ubuntu, Linux and OS Chat
---

### Post by pfeiffep on 2014-05-07
I have 2 systems running Ubuntu 14.04 both configured with gnome flashback / metacity. One is an old laptop (32 bit) with somewhat limited storage, the second is a tower (64 bit) with plenty of storage. 
When running 12.?? I noticed the laptop would occasionally boot with an error message about /tmp being unavailable. I installed bleachbit on both machines and run it prior to shut down which seemed to 'fix the /tmp issue. 
I've continued this practice on 13.04 and now on 14.04. I decided to run an experiment on tower while running 13.04 to track how much crud accumulates. 
After a month of running bleachbit, analyze only prior to shutdown the amount had grown to over 1 GB.

I noticed over the past week or so about 50 MB minimum is deleted from the laptop daily.

I'm really happy with my procedure using bleachbit, but I'm also wondering about Linux and how or what should be happening (built in, automated, or manual) to manage the file system.

---

### Post by TheFu on 2014-05-07
Likely, it is log files, but you can watch different directories using **du**.
For most people, [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) is all the system maintenance they require, provided they only install packages through the package manager.  .deb file installs and installations from source seldom clean up after themselves or automatically rotate log files by day or size.

There are many tools to monitor a Linux system. A beginner-level tool is **logwatch**. Install that, set it up to notify you of changes.

Can't say what the /tmp issue is without more details. On my desktop, /tmp is just part of /, so if there is any issue with it, that means disk corruption and I'd ensure my backups are 100% recoverable ASAP, check cables, and be ready to replace some hardware.

---

### Post by pfeiffep on 2014-05-07
@TheFu - thanks for your reply. I wanted to know more about the large number of MB that bleachbit is removing contrasting that with what would happen if I did nothing other than apt-get update/upgrade/autoclean/autoremove?

---

### Post by TheFu on 2014-05-07
a) I've never used bleachbit ... in 20+ yrs of Linux use. Don't know anything about it or what it claims. Perhaps there is a log file?
b) apt-get is NOT the recommended method by the debian team anymore. Hasn't been for years.  **aptitude** is smarter almost always. Use it instead.
c) NOTHING replaces backups. There are thousands of reasons for backups beyond just saving data. With versioned backups, it is possible to reconstruct what happens to a system over time, for example.  Think of how useful that would be to answer THIS question today, but also think of how useful that would be for when the machine gets hacked.

---

### Post by pfeiffep on 2014-05-07
@TheFu, I am unable to find a bleachbit log file, I'll explore the available command line execution and redirect the output to a file.  I did a quick browse of the files the non-admin gui execution deleted and it seemed like the majority of the deletions were related to Chromium and Thunderbird - this morning on my laptop the total was around 60 MB (I shut the laptop down when not in use)

Here's a[ snip]("http://bleachbit.sourceforge.net/") "[COLOR=#444444][FONT=PT Sans]BleachBit quickly frees disk space and tirelessly guards your privacy. Free cache, delete cookies, clear Internet history, shred temporary files, delete logs, and discard junk you didn't know was there."[/FONT][/COLOR]

---

### Post by pfeiffep on 2014-05-08
> **TheFu said:**
> a) I've never used bleachbit ... in 20+ yrs of Linux use. Don't know anything about it or what it claims. Perhaps there is a log file?
**b) apt-get is NOT the recommended method by the debian team anymore. Hasn't been for years.  aptitude is smarter almost always. Use it instead.**
c) NOTHING replaces backups. There are thousands of reasons for backups beyond just saving data. With versioned backups, it is possible to reconstruct what happens to a system over time, for example.  Think of how useful that would be to answer THIS question today, but also think of how useful that would be for when the machine gets hacked.Regarding the bolded point. After reading [online]("http://debian-handbook.info/browse/wheezy/sect.apt-get.html") I'm hard pressed to find much difference between apt and aptitude as they both use the same sources. As I understand aptitude is a 'terminal' front end for apt.

---

### Post by TheFu on 2014-05-08
> **pfeiffep said:**
> Regarding the bolded point. After reading [online]("http://debian-handbook.info/browse/wheezy/sect.apt-get.html") I'm hard pressed to find much difference between apt and aptitude as they both use the same sources. As I understand aptitude is a 'terminal' front end for apt.

apt-get generally works, until it doesn't.  Aptitude will try much, much harder to resolve dependency issues introduces when admins do something outside the normal - like installing mariaDB instead of mysql or installing directly .deb files with locked dependencies.  My information comes directly from a debian developer (though not on APT).  Aptitude is smarter about cleaning up too, IME.

As far as bleachbit - looks like it does things that my pre-backup script handles. I wipe flash objects, remove TMP files, etc... and have the browsers set to remove all cookies at shutdown (i.e. only session cookies are allowed).  They probably do it better.

---

### Post by vasa1 on 2014-05-08
> **TheFu said:**
> apt-get generally works, until it doesn't.  Aptitude will try much, much harder to resolve dependency issues introduces when admins do something outside the normal ...
So a normal, conservative user needn't worry about not using aptitude? I've started using Linux relatively recently (11.04 on) and not had a problem with apt-get. Any idea why Ubuntu provides apt-get by default?

---

### Post by TheFu on 2014-05-08
apt-get has been core to Debian since the 1990s.  Almost every CLI how-to written says "apt-get".  The default becomes the standard, especially when it usually works.
I use apt-get most of the time out of habit too.  I'm trying to convert to aptitude.  Aptitude HAS resolved dependency issues on a few of my systems that apt-get couldn't. It really is amazing.

So - I don't know.  They (Canonical) is also are pushing "software center" - I don't know why. Never used it, but I don't run Unity. I install "server", then add a GUI on GUI platforms. Most of the systems here are servers, however. Mainly managed through Ansible.

I don't know why Firefox v29 removed the status bar either ... idiots.

---

### Post by vasa1 on 2014-05-08
> **TheFu said:**
> ...
So - I don't know.  They (Canonical) is also are pushing "software center" - I don't know why. Never used it, but I don't run Unity. ...
Strangely, that's the most persuasive argument I've encountered. I never thought of it that way.
I will now certainly look at aptitude :)

---

### Post by pfeiffep on 2014-05-08
Thanks,
> **TheFu said:**
> apt-get generally works, until it doesn't.  Aptitude will try much, much harder to resolve dependency issues introduces when admins do something outside the normal - like installing mariaDB instead of mysql or installing directly .deb files with locked dependencies.  My information comes directly from a debian developer (though not on APT).  Aptitude is smarter about cleaning up too, IME.

As far as bleachbit - looks like it does things that my pre-backup script handles. I wipe flash objects, remove TMP files, etc... and have the browsers set to remove all cookies at shutdown (i.e. only session cookies are allowed).  They probably do it better.I discovered an nice aptitude command / feature "aptitude show {package name} ; apt show also works. I'll be exploring aptitude a bit more with the goal of replacing my normal apt-get routine. An aside - I don't like the terminal UI - so if I need a different interface I'll stick with synaptic GUI

---

