---
title: "Question about systemd"
date: 2016-01-13
forum: The Cafe
---

### Post by pqwoerituytrueiwoq on 2016-01-13
based on my googling it seems there are quite a few haters of it, so i am trying to verify if a something i found is true
somewhere i read that cause systemd is using binary blobs and is so integrated it requires a reboot to apply updates, is that true? i don't want to reboot my server to apply some update, id rather just revert to init if that is the case
i read it a long time ago so  i don't recall the exact wording and for all i know it may no longer be true if it ever was in the 1st place

---

### Post by TheFu on 2016-01-13
> systemd is suing binary blobs?
I'm lost.
Good luck "reverting to init."  That won't be with ubuntu, to my knowledge.

---

### Post by vasa1 on 2016-01-13
systemd is _us_ing binary blobs?

---

### Post by buzzingrobot on 2016-01-13
After using systemd since its adoption in Fedora and then in Ubuntu, I can say rebooting after updates depends on what is updated, as always.

Gnome, I believe, can download and apply updates in the background and then prompt the user to reboot. Running Gnome Shell, though, on a server would be inappropriate 

"Binary blobs" only happen when proprietary vendors release a driver, etc., without source.

There's lots of agenda-driven, heated/hysterical venting about systemd that will linger forever on the web. I would go straight to the docs.

---

### Post by TheFu on 2016-01-13
> **buzzingrobot said:**
>  I would go straight to the docs.

One of the complaints about systemd is the lack of clear and accurate documentation. That could be just ranters, I dunno. 

Been putting off anything to do with systemd myself until absolutely necessary.  Did get a Debian-based system forced on me with systemd and wasn't able to figure out the dependency stuff - ended up using a "sleep 30" to avoid knowing it.  Expect I'll have to learn something around June-ish thanks to 16.04.

My LUG has had some heated arguments about systemd. My summary is:
* new doesn't mean better.
* new is scary for some people.
* not using text log files breaks a core tenant of "The Unix Philosophy" - > Write programs to handle text streams, because that is a universal interface.
* systemd was created to solve an issue for 1% of Linux users. The other 99% didn't need/want it.
* the lead developer of systemd also provided that great audio system that didn't work for at least 5 yrs - pulseaudio. Is this a repeat?
* systemd seems to be taking over more and more features that other tools provided. Having those in a single project is scary, but if the other projects hadn't been maintaining those programs, seems that having anyone (except the NSA/GCHQ) interested in maintaining it would be a good thing.
* there are some really cool features in systemd - 
** remote logging is easy, 
** binary log files are much smaller
** binary log files faster to query than text, 
** parallel process startups are nice on multi-core system, 
** better dependency handling for startup processes than the old-way.

A few of the vocal people have left all distros that use systemd.
A few of the old-guys have embraced it, including some highly respected, redhat-centric, folks.

The EFF-track at DragonCon this year had a panel discussion about systemd - I didn't really learn anything new, but Jim K can be funny. Video is on Youtube if you have an hour to waste.

I expect to restart an internet-facing server about 2-times a month for kernel security patches. That's the nature of computing these days.  For non-internet-facing servers, only a few don't get restarted as needed by patching. That reminds me, need to reboot the NAS. Done.

From the examples I've seen, systemd takes more typing to use and requires an extra parameter (4 instead of 3) to the old "service" commands. Perhaps after some time with it, the CLI interface will show genius - I dunno.  I still prefer the /etc/init.d/daemon start/stop/restart/status method, myself. It was clear and easy to understand.  Run levels are understood. Systemd doesn't really have run-levels, as such, so we get to learn new terminology and have more complexity. Not good or bad, just more crap to know in order to have even more flexibility than we had previously.

Learning something different after 30 yrs of doing things a different way isn't always bad.

---

### Post by Morbius1 on 2016-01-13
> One of the complaints about systemd is the lack of clear and accurate documentation. That could be just ranters, I dunno. 
Want to know what the most frustrating thing about systemd has been for me? I'll tell you anyway.

All of the documentation even the man pages were written as more of a wish list of things it will do. I don't know if I've ever come across something like that.

I had been trying to do things I had read on other forums and on the web in general and they never worked. It was driving me insane. Then I happened on a report of the changes made to systemd in their latest release at the time and it was there that they mentioned that they implemented functionX or functionY. Something that had been in the man pages for over a year.

I had to install Manjaro which had the lasted version of systemd before I could accomplish what I was trying to test.

---

### Post by grahammechanical on 2016-01-13
> is so integrated it requires a reboot to apply updates

Now, here is a strange thing. I have heard that with the latest Linux kernels a kernel upgrade can now be installed without requiring a restart but I am not sure if the function has been implemented yet in Ubuntu. So, in theory we should be having less re-starts following updates.

I am running Xenial & I have seen more instructions to re-start after an update than ever before and it has nothing to do with a kernel being upgraded. Is systemd the culprit. I cannot make a positive identification, your honuor, but systemd has the typical look of a "usual suspect." :)

From the little reading I have done on this subject I do not think that the Redhat developers who have produced systemd have ever hidden the fact that they intend it to be more than a simple init system.

A description of systemd in Synaptic

> systemd is a system and service manager for Linux. It provides aggressive parallelization capabilities, uses socket and D-Bus activation for starting services, offers on-demand starting of daemons, keep tracks of processes using Linux control groups, supports snapshotting and restoring of the system state, maintains mount and automount points and implements an elaborate transactional dependency-based service control logic.

I think that you will find that in 16.04 it is systemd that switches on a lot of the services such as sound.

We will soon see arguments about whether the OS should be called Linux or Grub/GNU/Linux/Systemd.

Regards.

---

### Post by QDR06VV9 on 2016-01-13
> **Morbius1 said:**
> Want to know what the most frustrating thing about systemd has been for me? I'll tell you anyway.

All of the documentation even the man pages were written as more of a wish list of things it will do. I don't know if I've ever come across something like that.

I had been trying to do things I had read on other forums and on the web in general and they never worked. It was driving me insane. Then I happened on a report of the changes made to systemd in their latest release at the time and it was there that they mentioned that they implemented functionX or functionY. Something that had been in the man pages for over a year.

I had to install Manjaro which had the lasted version of systemd before I could accomplish what I was trying to test.

+1;)
[Systemd Docs]("https://wiki.archlinux.org/index.php/systemd")
I was seriously considering dropping any debian based distro due to systemd, but those docs in the link provided has eased that urge..:D
Regards

---

### Post by pqwoerituytrueiwoq on 2016-01-13
> **TheFu said:**
> ?
I'm lost.
Good luck "reverting to init."  That won't be with ubuntu, to my knowledge.
Rasbian
> **TheFu said:**
> I expect to restart an internet-facing server about 2-times a month for kernel security patches.

i read a phonorix article some time back that mentioned a new feature that would allow a skilled user to update the kernel without rebooting

---

### Post by TheFu on 2016-01-13
> **pqwoerituytrueiwoq said:**
> Rasbian


i read a phonorix article some time back that mentioned a new feature that would allow a skilled user to update the kernel without rebooting

Patching a running kernel has been possible since the late 1990s for certain distros (thinking redhat-based). Commercial support for this by a 3rd party came before then.
Think wider support for that comes with 4.x kernels - don't know the exact version.

One of my relatives created a system to patch running MVS systems without bringing them down decades ago. I suspect something similar is being used for this.  Remember when he shared a story of IBM claiming his patch system wouldn't work with some of his clients in Japan.  Then he explained it and they said - jeeze - that WILL work.  Made a bunch of money selling that for corporations running Oracle on MVS which basically never, ever, get turned off since their businesses follow the Sun around the globe for decades at a time between reboots.

I will probably wait a few years before using the new-fangled kernel-patch methods.  Don't want clients expecting miracles before enough time proving it works perfectly has happened. ;)

Don't know what Rasbian has to do with this at all.  My Raspberry Pi running Debian had to be rebooted 3 times last week, once with the power plug.

---

### Post by RichardET on 2016-01-17
On my Lenovo B590, systemd has conflicts with the resume/sleep system.  I had to dump Ubuntu 15.10 and go back to the current LTS release, no systemd.  After Ubuntu goes 100% systend, I may have to use a BSD instead.

---

### Post by HermanAB on 2016-01-17
I've been running Fedora with systemd for years and it works.  So some people may have issues, but it is prolly overblown.

---

