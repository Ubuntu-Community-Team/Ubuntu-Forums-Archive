---
title: "Deleted all my kernels"
date: 2010-02-21
forum: The Cafe
---

### Post by sports fan Matt on 2010-02-21
So yesterday I decided to clean a few kernels when I deleted ALL of them.  I was shocked.  I couldn't think it could be done without a reinstall.  I reinstalled anyway and all is well with Karmic.  What interesting things have ya'll done?

---

### Post by falconindy on 2010-02-21
This one time, I installed Windows. True story.

P.S. I've been w/o a kernel package installed for about 2 days. It's only an issue if you want to reboot. Reinstallation is rarely the only solution.

---

### Post by MaxIBoy on 2010-02-21
> **sox fan Matt said:**
> So yesterday I decided to clean a few kernels when I deleted ALL of them.  I was shocked.  I couldn't think it could be done without a reinstall.  I reinstalled anyway and all is well with Karmic.  What interesting things have ya'll done?Couldn't you just boot off a liveCD, chroot into your installation, and apt-get install or compile a new kernel? That's what I would do.


Um, one time I deleted all my initscripts and had to restore from my backups (thus there was a regression of about a half second in my boot time.) Meant to do ```
sudo rm /etc/rc*.d/*~
``` but left off the "~" from the end of it.

---

### Post by dragos240 on 2010-02-21
I once gave out a username and password to an SSH server. That ended badly.......

---

### Post by sports fan Matt on 2010-02-21
At the time If I had thought about it yes.  I wasn't think about it though :)

---

### Post by user1397 on 2010-02-21
first time i installed linux i wiped my windows drive and used the entire disk, thereby losing some files (i backed up the most important ones, but still lost some files)

once i chmod'ed my entire /home with 777 permissions...

once i installed arch :popcorn:

---

### Post by #11u-max on 2010-02-21
I once accidentially all your base

---

### Post by FuturePilot on 2010-02-21
I accidentally typed "rm" instead of "mv" [s]once[/s] twice #-o
That wasn't cool.

---

### Post by chucky chuckaluck on 2010-02-21
mistake free, here, and lovin' it.

---

### Post by dragos240 on 2010-02-21
> **ubuntuman001 said:**
> first time i installed linux i wiped my windows drive and used the entire disk, thereby losing some files (i backed up the most important ones, but still lost some files)

once i chmod'ed my entire /home with 777 permissions...

once i installed arch :popcorn:
Really? Wow, I did the same thing! But I chmoded root 777. I did this:
chmod -r 777 /

Stupid me.

I've also done rm instead of mv many many times. Every time it was a non-vital conf file. Lucky me. I also accidentally 21mb of rar files.

---

### Post by Jesus_Valdez on 2010-02-22
> **dragos240 said:**
> Really? Wow, I did the same thing! But I chmoded root 777. I did this:
chmod -r 777 /

Stupid me.

I've also done rm instead of mv many many times. Every time it was a non-vital conf file. Lucky me. I also accidentally 21mb of rar files.
It also happened to me once.

But I was kind of bored so I changed the permissions back using GUI (right click, properties, etc.), that was fun.

---

### Post by toupeiro on 2010-02-22
I once applied a RHEL update bundle on a server that was 4 bundles behind, so it updated all the software but *didn't* completely update the kernel to the version in the latest bundle.  It did not generate a initrd file, and because mkinitrd was updated to a version outside of the running kernel, it just locked up when I tried to generate one.  I really thought I was looking at a complete rebuild..

How I ended up fixing the issue is installing just the desired kernel packages on another server with the same hardware, but **not upgrading** to that new kernel, then ran mkinitrd on that server and copied the initrd file for that kernel over.  Amazingly enough, that worked, and saved me hours of rebuilding a server and reloading applications and data from media and backup tape.  This kind of flexibility is much harder to find in windows these days.

---

