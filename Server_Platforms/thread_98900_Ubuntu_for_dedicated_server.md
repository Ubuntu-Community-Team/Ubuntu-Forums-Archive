---
title: "Ubuntu for dedicated server"
date: 2005-12-04
forum: Server Platforms
---

### Post by dutchie on 2005-12-04
Are there many people running Ubuntu server on dedicated servers? I ask because I dont see many providers supporting Ubuntu as an install option.

Also is there a HOWTO somewhere on how to install Ubuntu server on a dedicated server if it is running another Linux distro?

I'm about to upgrade to a new server, and Debian has always been my preffered distro, but the providers I've shortlisted all provide only CentOS or Fedora

Cheers,
Dutchie.

---

### Post by atoponce on 2005-12-04
I use Ubuntu as a dedicated server hosting 2 different domains currently, with a possibility of a third.  Traffic right now is light with about 50-75 hits per day.  So far, it runs great.  I am also running an Ubuntu server at work, and it hasn't had any problems.

As far as a HOWTO is concerned, check out [http://www.howtoforge.com/perfect_setup_ubuntu_5.10]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10")

---

### Post by dotmil on 2005-12-04
I've been bugging my provider about supporting Ubuntu as an install option at order time (currently I run Debian on all of mine). For now though, my options are to either attempt to upgrade from a Sarge install (potentially ugly), or rent a KVM over IP and install Ubuntu myself.

I may go with the KVM idea after the holidays. But yes, I do wish some provider would suppport Ubuntu at order time; I know they'd get some business from me right away!

---

### Post by dutchie on 2005-12-04
Yeah, some providers provide a recovery tool, which somehow lets you boot into another linux and access your machine's hard disk. Not exactly sure how this works, but I'm thinking it must be possible to install Ubuntu that way.

Thanks for the pointer to the how-to Atoponce. It mentions using the cd though. Is it easy to to a network install? I've done it for debian before, but couldn't find any info for Ubuntu.

Cheers,
Dutchie

---

### Post by dotmil on 2005-12-04
I actually found someone who offers Ubuntu on a dedicated server! they don't say which release, but it is there as an option for OS at order time.

[http://serverpronto.com/]("http://serverpronto.com/")

I don't know anything about the company, but those prices seem almost too good to be true also. So, who wants to be the guinea pig? ;)

---

### Post by Wide on 2005-12-04
If your looking for a solid production server you may want to go with something thats  rock solid stable thats not running the latest & greatest.

We use Debian stable along with RHEL4

The  Debian systems have been running for  years without any reinstalls, just upgrades.

---

### Post by dotmil on 2005-12-05
[QUOTE=Wide]If your looking for a solid production server you may want to go with something thats  rock solid stable thats not running the latest & greatest.

We use Debian stable along with RHEL4

The  Debian systems have been running for  years without any reinstalls, just upgrades.[/QUOTE]

Well isn't that the goal for Dapper? Rock solid servers? Also, when RHEL 4 was released, it *was* the latest and greatest. Just because something is older doesn't make it more stable.

Anyway, for $30/month how much stability would you expect?

---

### Post by nagilum on 2005-12-05
If you desperately want to install Ubuntu on your server it can be done remotely. There's a good HOWTO for that ([http://www.underhanded.org/papers/debian-conversion/remotedeb.html](http://www.underhanded.org/papers/debian-conversion/remotedeb.html)), it basically uses debootstrap to install a minimal system and makes it bootable. Just make sure you follow the steps precisely to not leave the system in a non-bootable state. Even better if your ISP allows to run some kind of emergency system.

---

### Post by dutchie on 2005-12-05
Thanks for the pointer to the howto Nagilum, will come in handy.

---

### Post by davebgimp on 2007-02-28
> **dotmil said:**
> I actually found someone who offers Ubuntu on a dedicated server! they don't say which release, but it is there as an option for OS at order time.

[http://serverpronto.com/]("http://serverpronto.com/")

I don't know anything about the company, but those prices seem almost too good to be true also. So, who wants to be the guinea pig? ;)

I and my boss have both used this company about a year for our separate servers. During that time, I've not had any real complaints. I think when I signed up, they were installing Breezy. Since then I've manually upgraded to Dapper with everything except the kernel, which is still at 2.6.12 because everything later will not load the network on reboot. They give me  some talk about a bug in the later kernels with their NIC cards and I've more or less given up on trying to force the issue as my server is totally functional.

Mainly it's so cheap because nothing is really supported. You're renting a box in a server farm and once they install your OS, you're on your own. That said, it's been a learning experience for me, enough to justify keeping my account with them.

---

### Post by HumanAnarchist on 2007-02-28
We use [http://budgetdedicated.com/](http://budgetdedicated.com/) at work. They support Ubuntu Dapper. Their located in Amsterdam (nice) and are hella cool. Great IRC support as well.

-ha-

---

