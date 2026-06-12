---
title: "root access with no password in recovery mode"
date: 2011-08-29
forum: Security
---

### Post by 98cwitr on 2011-08-29
So I'm using 11.10 alpha release and just realized I can gain root access to the box without a password. When loading recovery mode in GRUB and selecting the 'down to root shell' option, it does just that, but without a password. Does this happen in the full-release version too?

Any thought?

---

### Post by haqking on 2011-08-29
> **98cwitr said:**
> So I'm using 11.10 alpha release and just realized I can gain root access to the box without a password. When loading recovery mode in GRUB and selecting the 'down to root shell' option, it does just that, but without a password. Does this happen in the full-release version too?

Any thought?

it does it in all versions.

Physical access is root access

---

### Post by 98cwitr on 2011-08-29
man...that sucks. :(

---

### Post by Dangertux on 2011-08-29
Yep -- recovery mode is just that recovery mode.

Heck -- you can even do some fancy stuff with grub cause a few kernel panics and reset a root password. Then again, they kinda frown on that in this forum so I won't go into details :-P

---

### Post by 98cwitr on 2011-08-29
> **Dangertux said:**
> Yep -- recovery mode is just that recovery mode.

Heck -- you can even do some fancy stuff with grub cause a few kernel panics and reset a root password. Then again, they kinda frown on that in this forum so I won't go into details :-P

That blows even harder :/

---

### Post by bodhi.zazen on 2011-08-29
> **98cwitr said:**
> That blows even harder :/

Physical access is root access in any OS.

See : [https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue_Mode](https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue_Mode)

Your best option if you have sensitive data is to use encryption.

---

### Post by snowpine on 2011-08-29
It is a "feature not a bug." Among other uses, Recovery Mode allows you to recover the system if you forget your password. Requiring a password would kind of defeat the purpose. It would also give a false sense of security--it is trivially easy to recover unencrypted data from any Linux/Windows/Mac system if you have physical access.

---

### Post by HarriU11-04 on 2011-08-30
> **snowpine said:**
> It is a "feature not a bug." Among other uses, Recovery Mode allows you to recover the system if you forget your password. Requiring a password would kind of defeat the purpose. It would also give a false sense of security--it is trivially easy to recover unencrypted data from any Linux/Windows/Mac system if you have physical access.
i've just discovered this feature of ubuntu.....so whats the point of a root password? indeed, any user who can physically access the machine can go into the recovery console and voila1 wide-open system

---

### Post by amauk on 2011-08-30
> **HarriU11-04 said:**
> any user who can physically access the machine can go into the recovery console and voila1 wide-open system
Any user with physical access to the machine can just steal it, or hit it with a hammer

Stopping nasty people doing stuff physically to your machine is not a problem software can solve

---

### Post by haqking on 2011-08-30
> **HarriU11-04 said:**
> i've just discovered this feature of ubuntu.....so whats the point of a root password? indeed, any user who can physically access the machine can go into the recovery console and voila1 wide-open system

There is no root password, root is disabled by default.

It doesnt matter what system physical access is root access.  On a windows machine if you have physical access you can boot to various recovery CD and access the system or even change the admin password.

If you are in the habit of leaving your system where others can access it then it is insecure, thats why servers stay locked up in a server room.

---

### Post by snowpine on 2011-08-30
> **HarriU11-04 said:**
> i've just discovered this feature of ubuntu.....so whats the point of a root password? indeed, any user who can physically access the machine can go into the recovery console and voila1 wide-open system

Ubuntu has no root password.

Ubuntu security is a vast topic (for some it is a full-time profession); if you want to learn more, we have an entire sub-forum here. A good place to start is this sticky thread: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bodhi.zazen on 2011-08-30
> **HarriU11-04 said:**
> i've just discovered this feature of ubuntu.....so whats the point of a root password? indeed, any user who can physically access the machine can go into the recovery console and voila1 wide-open system

Physical security is crucial for system security, why do you think they keep servers in locked rooms ? Why do you think rack servers come with physical locks ?

Separating user accounts from root powers is also basic security.

No offense intended, but I suggest you start by reading most any computer security 101 book as by your question you seem to lack the fundamentals of computer security.

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

---

### Post by amauk on 2011-08-30
> **bodhi.zazen said:**
> No offense intended, but I suggest you start by reading most any computer security 101 bookBy "you", I assume you mean the OP, and not me :P

---

### Post by Dangertux on 2011-08-30
I've actually adopted a new philosophy that I am advocating to my clients in terms of physical security.

They're used to things like access rosters, time logs, keys, locks, and identification badges.

I have come to realize that booby trapping production systems and only teaching a select few how to disable the booby traps is the way to go; however let the other personnel know that they may be maimed if they attempt to gain unauthorized access to restricted systems.

This was a joke, just emphasizing the points made about physical security :-)

P.S : these methods may not be accepted during a compliance audit.

---

### Post by haqking on 2011-08-30
> **Dangertux said:**
> 

P.S : these methods may not be accepted during a compliance audit.

Damn and i was hoping for a quick fix for PCI DSS and SOX ;-)

---

### Post by bodhi.zazen on 2011-08-30
> **amauk said:**
> By "you", I assume you mean the OP, and not me :P

Oh sorry, wrong quote button will fix that.

---

### Post by Dangertux on 2011-09-06
> **haqking said:**
> Damn and i was hoping for a quick fix for PCI DSS and SOX ;-)

Just keep telling them how awesome your WAF is and you'll pass a PCI audit. No....don't worry about updated rule sets, just tell the auditor you have mod_security, they will smile and check the box for you =)

I'm kidding (only mostly unfortunately)

---

### Post by jsvidyad on 2011-09-13
Is there a way to prevent the recovery mode option from showing up when you boot the computer? I use kubuntu 10.04 and I believe therefore I use grub2. I have a dual boot system and the recovery mode shows up in the grub boot screen. I want to get rid  of that

---

### Post by BkkBonanza on 2011-09-13
Just to spell it out... there would be no point in having a password on the recovery mode since anyone with physical access could simply take the drive and mount it as non-boot drive in another system. At that point they can access anything as root anyway. Or they could boot on a livecd and get access. It's just not feasible to prevent this.

So, yes, encryption is what you want if you need to better secure the data on a system. Nowadays the overhead is minimal. Full drive encryption is the most secure but more trouble to setup. 

An encrypted home is good for most general uses and can be applied afterwards even on a running system. At least this way if someone outright steals your system then they can't get at the data. And, as I found out a couple weeks back when my Vertex SSD failed - it's sure nice to know when I send the drive in for warranty replacement they won't be browsing about in my data.

---

