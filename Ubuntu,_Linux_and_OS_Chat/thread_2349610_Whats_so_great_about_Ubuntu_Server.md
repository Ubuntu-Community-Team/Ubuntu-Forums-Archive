---
title: "Whats so great about Ubuntu Server?"
date: 2017-01-16
forum: Ubuntu, Linux and OS Chat
---

### Post by pixel2 on 2017-01-16
Im owner & admin of one of the HP servers (1TB HDD, 8GB RAM), out-of-the-box, sitted in 1U, all connected but without OS. Ive read alot on how Ubuntu Server is great, how it work flawlessly etc.

But - whats reality? Are here some server admins running Ubuntu Server? Id love to hear from them. Many thanks.

---

### Post by SeijiSensei on 2017-01-16
I run Ubuntu on the desktop, but CentOS on servers.  Server manufacturers have a stronger incentive to make sure their hardware works with RedHat Enterprise Linux.

That said, unless you have uncommon hardware like RAID cards, etc., I doubt there's much difference among server distributions other than usual things like where certain files are stored.  I think the bigger distinction is between distros using systemd (RHEL/CentOS 7, Ubuntu 16.04) and those that don't (RHEL/CentOS 6, Ubuntu 14.04).  Most of my servers (all virtual these days) run some flavor of CentOS 6 for that reason.

---

### Post by Habitual on 2017-01-16
After 22 years, the server OS doesn't matter, to me, any more.
I have a personal preference and a very short list.

---

### Post by The Cog on 2017-01-16
Not totally flawless (nothing is flawless), but pretty-much bomb-proof, flexible and extremely reliable.

If you are having to ask, I would suggest you go for a version of Ubuntu with a GUI instead. The big distinction between Ubuntu server and Ubuntu desktop is that the server is comand-line only: no GUI because it is going to be managed remotely. I suspect that if you're just trying Ubuntu out, you will probably feel that you want a GUI, just to help you explore the OS. You are straight in at the command-line deep end if you opt to install Ubuntu server (which would help you learn the CLI faster, I guess).

---

### Post by mastablasta on 2017-01-17
ot's ok, easy to setup and administer and has good support ffrom manufacturers (HP) as well as very good software and documentation support. LTS edition is suported for 5 years. centos lasts even longer if long term stability is what you are after.

---

### Post by 1clue on 2017-01-17
I have dozens of ubuntu server images, I prefer a long-term support (LTS) release for server images. I also use gentoo if I need something very specific, and a half dozen other distros if required by circumstances.

It all depends on your requirements for the system. I pick the best distro for the job, and Ubuntu Server is, for me, probably "it" more often than any other distro.

---

### Post by kevdog on 2017-01-18
@SeijiSensei -- I get the debate over systemd vs systemv, however honestly how does that make a server "more stable".  I get CentOS is used for a lot of servers, however packages are very very old usually.  I guess this isn't as important on servers, however aren't the kernel versions old?  Because most server versions of linux have limited packages, I don't find a lot of difference between them.  Heck would a bsd variant be considered stable as well??? Nothing seems easier than modifying one rc.conf file in the bsd versions.

---

### Post by mastablasta on 2017-01-19
> **kevdog said:**
> @SeijiSensei -- I get the debate over systemd vs systemv, however honestly how does that make a server "more stable". 

no one said it is more stable. just that there is a difference in server OS if you run systemd or not.

---

### Post by 1clue on 2017-01-19
Stability is gained by using older software and only applying security and stability updates for a long period of time.

This supposedly makes the code more stable than new code, because the only accepted changes are those required to make it more secure and more stable. Statistically speaking some of those fixes will have bugs and could cause a decrease in stability but there's no way to know that when you apply the fix.

RHEL and other "enterprise-grade" distros take it to what I think is an extreme level of so-called stability. Every now and then you need to get new features.

---

### Post by SeijiSensei on 2017-01-19
> **kevdog said:**
> @SeijiSensei -- I get the debate over systemd vs systemv, however honestly how does that make a server "more stable".  I get CentOS is used for a lot of servers, however packages are very very old usually.  I guess this isn't as important on servers, however aren't the kernel versions old?  Because most server versions of linux have limited packages, I don't find a lot of difference between them.  Heck would a bsd variant be considered stable as well??? Nothing seems easier than modifying one rc.conf file in the bsd versions.

I never said anything about stability.  Systemd seems to me to violate the basic Unix principle of one task, one program.  Systemd seems to run everything which seems more fragile to me.  Also I've been using the traditional commands like "service" for years and didn't see a reason to switch.

Many programs running on servers have long histories.  I use sendmail, for instance, which dates back at least thirty years now to [4.2BSD]("https://en.wikipedia.org/wiki/Berkeley_Software_Distribution#4.2BSD") (1983).  It still does what I need it to do so its age is irrelevant. Apache's roots lay in [NCSA httpd]("https://httpd.apache.org/ABOUT_APACHE.html") which appeared around 1995.  It's still the dominant web server on the Internet.  

You ask about the age of kernels, but again, what matters is how well they work.  There are still lots of servers on the Internet running Linux 2.x because they have the needed drivers and are quite stable.  Also don't be confused by the version numbers on a lot of system software.  Both Redhat and Ubuntu "backport" security updates into existing programs without updating their version numbers.  Server administrators value security and stability far more than keeping up with new things.  I want servers I can start up and then largely ignore.

Here is the list of programs that run on most of my servers:
sendmail
Apache httpd
BIND named
PostgreSQL
MySQL (sometimes)
OpenVPN
Sphinx search
Samba (on local networks)
NFS (local networks; between Internet hosts I use SSHFS)
OpenSSH

The youngest of those is probably Sphinx which appeared around 2001.

---

### Post by 1clue on 2017-01-19
> **SeijiSensei said:**
> I never said anything about stability.  Systemd seems to me to violate the basic Unix principle of one task, one program.  Systemd seems to run everything which seems more fragile to me.  Also I've been using the traditional commands like "service" for years and didn't see a reason to switch....

I very definitely hear you there. Systemd is a seriously bad piece of code, and only RedHat's commercial muscle could make it be so widely adopted in the Linux community. Hardcoding a specific init system into the dependency tree of end-user software is extremely wrong on many levels.

Gentoo tried to backport gnome desktop for awhile, they gave up. If you want gnome you need systemd. Most distros seem to have rolled over on this one, either not understanding or not caring about the complexity of the init system as a problem.

---

### Post by Wadim_Korneev on 2017-01-23
[COLOR=#333333][FONT=q_serif]The two most common reasons I've seen are:[/FONT][/COLOR]

[LIST=1]
[*]Having **more recent packages**.  Debian and especially RHEL tend to be too far behind.  There's a middle ground between the bleeding edge and being super conservative, and Ubuntu sits right there in the middle.
[*]Being in an environment where people are **more familiar with the Debian-way** of doing things versus the RedHat-way.  This is surprisingly common, despite RHEL / CentOS being widespread.  It seems like a significant fraction of engineers first learned Linux by using Debian, or have used Debian for several years.
[/LIST]

---

### Post by Tadaen_Sylvermane on 2017-01-23
For me I ended up using Ubuntu for a single reason. For some reason, maybe because I've used Ubuntu so long I prefer and trust ppa's more than adding a repo. In the case of my preferred choice Debian, I would need deb-multimedia. Heard plenty bad about that. Haven't had a problem with a ppa yet. My htpc / server is rock solid stable. 95% of it's use is file server type of stuff. Ubuntu server worked with my hardware 100% from the start, no troubles of any kind. I also prefer apt / apt-get over yum and rpms. I have zero complaints. The only place I may switch is to Arch for my server in the future, only if I upgrade or do a total rebuild. And only then because I've heard (no experience yet) that upgrading Ubuntu from release to release isn't always the smoothest of events. Will find out in a few years, I don't plan on upgrading my server from 16.04 to 18.04 until 20.04 is out and available. I like to stay 1 lts behind for stability and don't need the absolute latest packages for what I do.

*EDIT* An update on using non stock repos on Debian. I was thinking I should try to stick with a Debian on the server, set up a virtualbox vm with it and got all my software including kodi from deb-multimedia. Segfaulted and core dumped the vm. I'll stick with Ubuntu.

---

