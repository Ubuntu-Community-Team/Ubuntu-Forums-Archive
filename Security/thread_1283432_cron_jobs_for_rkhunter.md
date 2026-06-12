---
title: "cron jobs for rkhunter"
date: 2009-05-26
forum: Security
---

### Post by Ichindar on 2009-05-26
im new to ubuntu, enjoying it alot, but a friend today mentioned hackers being able to access your root using rootkit viruses or some such? is this true and how can it be avoided, she recommened a rootkit scan program to avoid it?

anyone know anything about this?

---

### Post by Boondoklife on 2009-05-26
> **Ichindar said:**
> im new to ubuntu, enjoying it alot, but a friend today mentioned hackers being able to access your root using rootkit viruses or some such? is this true and how can it be avoided, she recommened a rootkit scan program to avoid it?

anyone know anything about this?


Well this is true with any operating system, but really the best way to make sure it does not happen is to only download and run things from trusted sources. If you follow this simple rule then you are pretty much safe.

Well unless the place you are getting the files from has been rooted, but then again if they are that good then hey the normal user prolly didnt stand a chance againt them anyway. ;)

---

### Post by Ichindar on 2009-05-26
so is there a rootkit detector or some such thing that i could look into?

---

### Post by cdenley on 2009-05-26
```

apt-cache show rkhunter chkrootkit|less

```

---

### Post by HermanAB on 2009-05-26
Don't worry about it.  The only rootkits I ever encountered were ones I installed myself.  So relax and enjoy your nice and secure system.

---

### Post by rookcifer on 2009-05-27
Unless someone has already gotten into your system (through some other means) then a rootkit does them no good whatsoever.  Rootkits are mainly used as backdoors once the system has *already* been compromised.  They are also used to cover the evidence of a breach.

So, as long as you don't have any exposed daemons/services to the Internet, the chances of someone cracking your system are slim.  Just be sure to install all your packages from the Ubuntu repos and you'll be fine.

---

### Post by gorg0th on 2009-10-05
I've been working with Rkhunter for a little while now, and I noticed that it has scheduled jobs through cron for daily and weekly...I didn't set this up, is this part of the normal default setup for rkhunter??

---

### Post by gorg0th on 2009-10-05
Hello folks,

I've been working with jaunty 64 on my hp tx2, and things are quite good in general, but I have a question in regards to rkhunter.  I've been running rkhunter from time to time to check if anything is amiss on my system, (sometimes I play with unverified software), but  I noticed one day a lot of un-invited activity when I wasn't doing much on my machine, (high cpu load when I wasn't doing anything), and I checked my processes and noticed that rkhunter was running, (or something named rkhunter), and then I checked my cron to see if it was a regularly scheduled thing, and sure enough, it is, for both my daily and weekly cron jobs, the only thing is, I didn't set this up...

Does rkhunter default to scheduled executions through cron as far as it's default install settings are concerned?  

I have seen postings with people asking how to set up cron scheduling for rkhunter and chkrootkit, which caused me to assume that this wasn't a default option, but any thoughts or advice would be much appreciated.

~G

---

### Post by cdenley on 2009-10-05
That appears to be the default.
```

cdenley@ubuntu:/var/cache/apt/archives$ dpkg -c rkhunter_1.3.2-6ubuntu1_all.deb|grep cron
drwxr-xr-x root/root         0 2008-10-01 06:41 ./etc/cron.daily/
-rwxr-xr-x root/root       651 2008-10-01 06:41 ./etc/cron.daily/rkhunter
drwxr-xr-x root/root         0 2008-10-01 06:41 ./etc/cron.weekly/
-rwxr-xr-x root/root      1785 2008-10-01 06:41 ./etc/cron.weekly/rkhunter

```

---

### Post by djchandler on 2009-10-05
I've been having something really strange happening in the past several days since the last round of updates a last week. The server from which the updates came is in the United States.

First, it took forever to download all the updates. I have Jaunty 64-bit running on two machines, a laptop and my desktop. The laptop dual boots Vista (for now) and other than Ubuntu being installed, is a stock Toshiba L305D-S5959. The desktop is home built, has Windows 7 RTM (barely been run yet) as well as Ubuntu 9.04 AMD64. The hardware includes a Gigabyte MA780G-US2H, AMD 7750 X2 BE (running stock speed), 4GB OCZ Gold DDR2-1066 and a 1TB WD Caviar Black Hard Drive.

Most noticeable is that SMP Folding@Home workunits using the same processing software core were suddenly, I believe mid-workunit, taking twice as long as before. What used to take 10-15 minutes per 1% is now taking over 30 minutes for each 1%.

I don't run F@H on the laptop--it really heats up. I don't know if there's a problem there or not yet, so I'm only talking about the desktop for now.

So I checked running processes with system monitor and I'm finding one ore more process running that do not have a name, it's just blank or invisible where the name should be,  no nice rating, says they're always sleeping, shows N/A for waiting channel and memory, while the ID number bounces all over the place from a value of about 16000 and up, changing constantly. It seems that either starting the Gnome terminal (bash) or beginning the GROMACS run is what instigates this behavior.

It was common before this to show 20 -24 percent CPU usage for each of the 4 threads, but now they're in the single digits a lot, and I seldom see 20% for any one thread. FahCore_a2 (V. 2.10) executable has a nice rating of 13 per thread. I'm checking this with system monitor with no other foreground applications running, and I have not made any changes other than those included in the update last week.

I'm posting this on the Folding@Home Forum as well, but it seemed like a good idea to get this in on the root kit discussion here.

I just installed rkhunter and chkrootkit but haven't run them yet. When I know what I'm doing with them and get a consistent result, I'll repost.

Any ideas?

---

### Post by gorg0th on 2009-10-05
> **cdenley said:**
> That appears to be the default.
```

cdenley@ubuntu:/var/cache/apt/archives$ dpkg -c rkhunter_1.3.2-6ubuntu1_all.deb|grep cron
drwxr-xr-x root/root         0 2008-10-01 06:41 ./etc/cron.daily/
-rwxr-xr-x root/root       651 2008-10-01 06:41 ./etc/cron.daily/rkhunter
drwxr-xr-x root/root         0 2008-10-01 06:41 ./etc/cron.weekly/
-rwxr-xr-x root/root      1785 2008-10-01 06:41 ./etc/cron.weekly/rkhunter

```
Thanks kindly for the feedback!

---

### Post by djchandler on 2009-10-07
:confused:

Finally ran rkhunter. and only found the usual suspects; wish the developers could keep up with Ubuntu's release schedule.

It seems the actual problem I was having is being caused by Folding@Home releasing bad work units.

I still had Firestarter block ports I never use though, IRC for instance. I can't type well enough or fast enough for that. Already had remote login, xserver, ssh and telnet blocked.

---

### Post by cariboo on 2009-10-07
The problem with rootkit checkers, is that they only catch the problem after the fact, they do nothing to stop someone from cracking you computer and installing a rootkit.

Personally I think it is better to prevent a break-in from happening, than it is to constantly check to see if it has already happened.

---

### Post by djchandler on 2009-10-07
Could not agree with you  more cariboo907. I suppose you could say that using rkhunter is the equivalent of grasping at straws when it comes to computer security.

One of the problems rkhunter flagged was wget. Just got that security update in the past couple of hours. Apparently this bug was giving me fits along with the bad F@H work units.

I wonder if that has anything directly to do with the corrupted work units.

---

