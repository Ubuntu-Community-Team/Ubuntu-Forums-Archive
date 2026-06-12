---
title: "Considering using Ubuntu for Commercial Production Servers"
date: 2005-11-03
forum: Server Platforms
---

### Post by JTorres176 on 2005-11-03
I'm new to Ubuntu, but have been around other Linux and Unix distros for some time.  On my servers at work, I currently run FreeBSD, but FreeBSD's last legacy release for 4.x is finally coming to pass, and not wanting to continue on to the 5.x series, I'm considering changing OS's to Ubuntu.  I'll be using this on a series of commercial servers using apps such as Apache 1.x, Jakarta-Tomcat5.0, PostgreSQL 7.x, as well as hosting a variety of general support services such as bind, imapd, asterisk, etc.  With the exception of "Th1s 1z teh best d1str0 EVAR!" can anyone enlighten me to specific reasons why I should or shouldn't consider Ubuntu for this task?

My pros and cons so far (after a lot of discussions with a few people) has brought me to considering Ubuntu or Debian.  Although Debian has a long history, their development cycle and security patch implementation has been, shall we say... less than stellar.  Offset in this argument is that Ubuntu, although new to the community and as of late, the hottest thing since sliced bread, is still relatively new, although seemingly stable.  Also, when 6.x series is released and we decide to upgrade, will I have to fly to the datacenter to physically reinstall OS's, or will a simple "sudo apt-get dist-upgrade" over ssh (probably) do it?

---

### Post by JTorres176 on 2005-11-03
[QUOTE=JTorres176] With the exception of "Th1s 1z teh best d1str0 EVAR!" ?[/QUOTE]

My apologies in advance if this came off the wrong way, it would probably be better to put it as "Advocacy aside.."  While beginning research for a previous project, I was looking into another distro, and while posing the same type of question in a different forum, I received approximately nine or so of these types of responses with no valid arguments or substance to them.

---

### Post by bjweeks on 2005-11-03
[QUOTE=JTorres176] "Th1s 1z teh best d1str0 EVAR!"[/QUOTE]

More like "th15 1z t3h b35t d15tr0 3VAR!1!!11!one"

Pros: After daper 5 year server surport. Most server packages are in the repos.

Cons: Some server apps are not in main.

---

### Post by mlomker on 2005-11-03
> Also, when 6.x series is released and we decide to upgrade, will I have to fly to the datacenter to physically reinstall OS's, or will a simple "sudo apt-get dist-upgrade" over ssh (probably) do it?

In theory that should work, but in practice it didn't for me going from Hoary to Breezy (on multiple machines).  

My team runs debian sarge on all of our production servers (other than a few RHE).  You sacrifice being the latest-and-greatest but debian is all about being solid.  Ubuntu is a great desktop OS, but it is snapshots of the unstable version of debian (and everything that it implies).

---

### Post by JTorres176 on 2005-11-03
[QUOTE=mlomker]
My team runs debian sarge on all of our production servers (other than a few RHE).  You sacrifice being the latest-and-greatest but debian is all about being solid.  Ubuntu is a great desktop OS, but it is snapshots of the unstable version of debian (and everything that it implies).[/QUOTE]

This was our primary interest in staying with FreeBSD for so long, the stability is key.  Of course, using PG 7.4x, Tomcat 5.0, Apache 1.3x, we're not exactly going for "latest and greatest" on our own.  The plus side of FreeBSD was the near immediate corrections for security and flaws by the community.  It seemed as though Deb had quite a few problems with that in the past, which is where I'm basing most of my pre-judgement.

I'd rather have a mostly secure mostly stable server, than going to the extreme in either direction.  We never need the latest and greatest, but on the other hand, security fixes sometimes weeks and weeks after they're discovered and released doesn't do us much good either.

---

### Post by mlomker on 2005-11-03
> security fixes sometimes weeks and weeks after they're discovered and released doesn't do us much good either.

One point of irony, that has been raised a couple times, is the fact that ubuntuforums itself runs on BSD.

---

### Post by hostile on 2005-11-03
If I could run some of my stuff on Free/OpenBSD, I'd do it in a second. Alas, I can not.

Choosing b/t distros lately for a server, I came down to Ubuntu/Debian and CentOS (built from the RHEL source). I chose Ubuntu b/c I'm tired of dealing with RPM. I know apt-get/dpkg have their own issues, but I chose the devil I don't know due to the fact that security update servers aren't up and down like a bus station toilet seat.

I'm not quite sure why you'd want to leave such a stable, secure, and moreover, proven environment. Do you have issues w/ FreeBSD 5.4?

---

### Post by JTorres176 on 2005-11-03
[QUOTE=hostile]
I'm not quite sure why you'd want to leave such a stable, secure, and moreover, proven environment. Do you have issues w/ FreeBSD 5.4?[/QUOTE]

Primarily, most of our software is java based, and BSD's near complete lack of java support has been a hindrance in the past.  Most linux distro's are simply "plug and play" when it comes to java, no flaming hoops to jump backwards through while singing the national anthem, even if java's not natively supported, it's as simple as reconstructing the java binaries for the specific system and inserting them.

BSD 4.x wasn't so bad, but 5.x is even worse.  I'd hoped, as well as my fellow administrator, that DragonflyBSD would have matured quickly enough to compensate for the dwindling BSD 4.x, but it's not showing the promise and stability we'd hoped for in this short period of time that they've had.

---

### Post by hostile on 2005-11-03
I know this is a little off-topic, but since you mentioned Dragonfly...

I'm actually quite interested in, and am keeping an eye on PC-BSD.

I installed it once, just to give it a test drive, and quite liked it, however, it wasn't what i was looking for at the time.

---

### Post by blu.gecko on 2005-11-04
not to dis on ubuntu but why on earth would you want to have to up and change everything 18 months from the original release date? I mean they make some small exceptions to release more security updates and what not, but for a server, you might want to consider something more stable like freeBSD, SLACK, Debian, ubuntu is a great distro,the only issue I have is the fact that less than 18 months from today you will have to start all over again.:rolleyes: 

just my opinion

---

### Post by JTorres176 on 2005-11-04
[QUOTE=blu.gecko]not to dis on ubuntu but why on earth would you want to have to up and change everything 18 months from the original release date? I mean they make some small exceptions to release more security updates and what not, but for a server, you might want to consider something more stable like freeBSD, SLACK, Debian, ubuntu is a great distro,the only issue I have is the fact that less than 18 months from today you will have to start all over again.:rolleyes: 

just my opinion[/QUOTE]

Oh, how I long to use Slack.  I use slack on all of my home pc's, but it has a horrible readline support.  The included packages are never useful when compiling software, and PostgreSQL uses readline as a dependency.  I had readline working correctly one time on one server where I could install PG, but I broke it a very short time later.  After taking nearly 6 hours total time to get it properly configured, built from source, and installed so PG would use it, and another couple of hours trying to figure out how I broke it, I gave up on the hopes of using Slack in my particular production setup.

FreeBSD, still out due to it's java problems.  Debian is however, beginning to look like a distro more suited to my particular needs judging from the community's feedback however.

---

### Post by hostile on 2005-11-04
> Debian is however, beginning to look like a distro more suited to my particular needs judging from the community's feedback however.

I chose Ubuntu over Debian b/c the servers I run do not have anything extraordinary about them: Samba, FTP, WWW (w/ PHP+mysql) all fairly plain configs, and thats about it. So, with Ubuntu being "Unstable Debian", I'm not too concerned about having bleeding edge packages, you may be however with your Java deployment.

You may want to consider CentOS too.

---

### Post by dvejnovic on 2005-11-04
[QUOTE=JTorres176]FreeBSD, still out due to it's java problems....[/QUOTE]

What java problem?

---

