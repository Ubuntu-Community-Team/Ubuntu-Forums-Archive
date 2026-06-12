---
title: "Travelled both roads, don't know which to take"
date: 2008-04-13
forum: Testimonials &amp; Experiences
---

### Post by Jordanwb on 2008-04-13
I've been having problems getting Ubuntu 8.04 to work on my laptop, Ubuntu 7.10 sort of works, and Windows XP works but it's slow.

Now there are pros and cons for each of the three OSes. I can't say anything good about 8.04 because I couldn't get past the Installer.

**Windows XP**:

Pros:

It boots each time and every time without a hitch
Streets & Trips (which I need ocasionally)
Full Wifi support

Cons:

Microsoft
Horrible tech support
Slow, bloated and takes way to much space

**Ubuntu 7.10**:

Pros:

Looks cool
Almost Complete control over what's installed
Free
Good tech support
Surprisingly good Wifi support

Cons:

Stalls every 1 in 4 boots

**Ubuntu 8.04**:

Pros:

I found out how to burn bootable floppies onto a CD

Cons:

I wasted ~ 12 hours trying to install it.
Couldn't install Grub <- The super Grub Disk was suggested but I don't know what the **** I'm supposed to do with it.
I fully formatted my laptop's hard drive at least 6 times. It's probably gonna board the fail boat soon.

I don't know whether to go with XP or Ubuntu. I could dual boot but that doesn't really solve any problems. It allows me temporarily avoid problems.

---

### Post by armandh on 2008-04-13
try Gparted [my favorite gui partitioner]free to download.
reduce the windows partition enough to install 8.04, leave unpartitioned
select "use unpartitioned space" when installing 8.04.

---

### Post by finferflu on 2008-04-13
I say try to find out what exactly is in the way when you try to install GRUB (for Ubuntu 8.04). I believe that if you wanna keep using Ubuntu, you're better off trying to fix the newest version. So, I would suggest you to start another thread specifically for the GRUB failure. 

Going back to Windows there's too much to lose, at least for me.

---

### Post by mrsudo on 2008-04-13
I dual boot.  i almost never use XP.  but in those rare occurances when ubuntu will just not do or i cannot boot into it, XP is my backup.
Works like a charm

---

### Post by Jordanwb on 2008-04-13
> **armandh said:**
> try Gparted [my favorite gui partitioner]free to download.
reduce the windows partition enough to install 8.04, leave unpartitioned
select "use unpartitioned space" when installing 8.04.

> **finferflu said:**
> I say try to find out what exactly is in the way when you try to install GRUB (for Ubuntu 8.04). I believe that if you wanna keep using Ubuntu, you're better off trying to fix the newest version. So, I would suggest you to start another thread specifically for the GRUB failure. 

Going back to Windows there's too much to lose, at least for me.

[Thread]("http://ubuntuforums.org/showthread.php?t=752649"), GParted was suggested to me. I created an ext3 partition and a Linux swap partiition, when I got to the partiton window in 8.04 Alternate installer I didn't know what to do.

> **mrsudo said:**
> I dual boot.  i almost never use XP.  but in those rare occurances when ubuntu will just not do or i cannot boot into it, XP is my backup.
Works like a charm

I may do that for Microsoft Streets & Trips 2007, but XP still uses way to much space. It's hard for something to impress me. Ubuntu is one of the few programs - or rather OS's - that has been able to impress me.

---

### Post by armandh on 2008-04-13
it didn't know what to do either
do NOT install partitions
leave the space unpartitioned
when installing 8.04 from the live disk select the option
use largest unpartitioned space [which will be available if there is any]
it has always worked well for me

---

### Post by Jordanwb on 2008-04-13
Well I'm using Alternate, so the option would be "Use Largest Contiguous space" or something like that. I decided to dual boot XP and 8.04, I want to see what Grub will do when it's installed by Ubuntu.

---

### Post by 3rdalbum on 2008-04-14
Why not have 7.10 installed, and then dist-upgrade to 8.04 over the Internet?

---

