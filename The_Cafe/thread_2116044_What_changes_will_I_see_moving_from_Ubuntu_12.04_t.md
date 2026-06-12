---
title: "What changes will I see moving from Ubuntu 12.04 to community ver. of Red Hat?"
date: 2013-02-14
forum: The Cafe
---

### Post by pythonscript on 2013-02-14
I'm considering moving my main laptop from Ubuntu 12.04 to one of the community versions of Red Hat Linux, most likely Scientific Linux 6.3. These are the changes I'm expecting initially:

1. Different user interface. Scientific Linux uses a version of Gnome 2, while Ubuntu uses Unity.

3. .deb/apt vs. .rpm/yum

4. Less package availability in the SL repositories and therefore more compiling from source, e.g. Python 3.

4. Less up-to-date software in SL for stability reasons.

5. Media playback. I've read that SL doesn't really have problems with this, but I know personally that Ubuntu doesn't.

6. GRUB. Ubuntu uses grub2, but I believe SL uses grub legacy.

What else should I consider? My laptop is about two years old, so I presume driver availability won't be a problem.

I'm considering switching so I can use a RH-based distro as a base for a hardened system, so I'm hoping the package availability isn't too limited in SL, because I don't really want to compile many packages from source or add a slew of third-party repositories, e.g. all of the Fedora ones, just to have access to certain pieces of software. 

Any other feedback I should take into account?

---

### Post by mamamia88 on 2013-02-14
Linux is Linux. Besides having older or newer packages and a different way to install them you won't really notice night and day differences between distributions.   Unless you are trying to get a job working on red hat i'd personally stick with Ubuntu or maybe fedora for something similar to red hat.

---

### Post by deadflowr on 2013-02-14
Eventually, it'll upgrade to Gnome3.

---

### Post by snowpine on 2013-02-14
While you are waiting for replies, you can test drive a Live CD of Scientific Linux: [http://ftp.scientificlinux.org/linux/scientific/livecd/63/](http://ftp.scientificlinux.org/linux/scientific/livecd/63/)

I personally used it for about 6 months and found it to be a fantastic OS. In the end I was a little more familiar with "apt" instead of "yum" and switched back to Debian. It was a close call, though. :)

---

### Post by schragge on 2013-02-14
Other administration tools (all the /usr/sbin/system-config-*), sysvinit vs. upstart, many packages (especially libraries, perl and python modules etc.) are named differently (e.g. libc6 on Debian is glibc on Redhat), the directory layout is somewhat different (e.g. /etc/default on Debian is /etc/sysconfig on Redhat).

---

### Post by monkeybrain2012 on 2013-02-14
I can't see the advantage or point of scientific linux. It seems to be just an outdated CENTOS like OS  preinstalled with a bunch of outdated scientific software. You can install updated version of all those software in Ubuntu or any linux distro yourself anyway. If one insists on a red hat like system I would much rather get Fedora and install those scientific software myself.

---

### Post by blackbird34 on 2013-02-15
Outdated for you means tried and tested and stable for them. They're doing real stuff on it, they're not going to spend their time debugging crackpot Gnome 3 extensions...

---

### Post by snowpine on 2013-02-15
We landed men on the moon with slide rules, I'm sure our leading thinkers can invent/discover lots of great things with the "outdated" software in Scientific Linux 6.3! :)

---

### Post by monkeybrain2012 on 2013-02-16
> **snowpine said:**
> We landed men on the moon with slide rules, I'm sure our leading thinkers can invent/discover lots of great things with the "outdated" software in Scientific Linux 6.3! :)

Sure. I am sure that Einstein didn't need no stinking computers at all. :)

---

### Post by PIE09gbLmgG6 on 2013-02-16
How different is red hat from ubuntu...does it install and run similiarly? Newb question sorry...

---

### Post by snowpine on 2013-02-16
> **egosophist said:**
> How different is red hat from ubuntu...does it install and run similiarly? Newb question sorry...

Very different. For starters it costs $299/year and up...
(but you can do a 30 day free trial, if you're curious... or try Scientific Linux or CentOS, which are pretty much the same software, but free-to-use)

---

### Post by monkeybrain2012 on 2013-02-16
> **snowpine said:**
>  if you're curious... or try Scientific Linux or CentOS, which are pretty much the same software, but free-to-use)

I suggest Fedora. Both CentOS are Scientific Linux are old. Fedora is cutting edge, if one doesn't like too cutting edge for stability worries go for Fedora - 1 (so the current newest version is Fedora 18, install Fedora 17 instead)

---

### Post by PIE09gbLmgG6 on 2013-02-16
K...guess I'm not understanding...I thought this was all opensource...Why do those cost money...sorta getting lost...fedora?

I appreciate the patience...My goal was to try everything and see what I like...don't want to just settle...

Is there a good link you all could share with me that breaks all of this down simply?

ego-

---

### Post by snowpine on 2013-02-16
Red Hat software is open source (thus enabling spin-offs like CentOS and Scientific to exist) but what you pay for is the subscription. The subscription gives you access to the repositories to download updates and additional applications, as well as technical support.

As to why this exists, and why Red Hat is so popular despite the fact you can get similar software for free, is the reality of the corporate/institutional world. If an organization depends on their computers for billions of dollars in trade, or the lives of their patients, or the people their missiles are pointed at, they do not want to use free community-backed software. Rather, the "powers that be" demand software that has a corporation behind it, who can be accountable for updates/bug fixes as well as providing support. Also the software must be very stable (older software that is well tested) and supported for a long time (up to 10 years if you are willing to pay a little extra). And they have a hardware certification program so organizations can purchase hardware/software combo that is guaranteed to work flawlessly. Furthermore the popularity of Red Hat creates an "industry standard" platform for third parties to develop compatible software.

Red Hat is used by government/banks/military/hospitals/universities/etc. who must have a solid product backed by a company with a good reputation and an 800 number they can call. These organizations traditionally used Microsoft, Apple, IBM, etc. and now thanks to Red Hat (and a few other similar distros) they can use Linux with confidence too.

Home/student/amateur/hobby users can get benefits of all this testing and R&D by using CentOS or Scientific Linux.

Hope that clears up the confusion.

---

### Post by monkeybrain2012 on 2013-02-16
> **egosophist said:**
> K...guess I'm not understanding...I thought this was all opensource...Why do those cost money...sorta getting lost...fedora?

I appreciate the patience...My goal was to try everything and see what I like...don't want to just settle...

Is there a good link you all could share with me that breaks all of this down simply?

ego-

I suggest Fedora. It is the community version of Redhat and it is up to date unlike CentOS (which is more suited for servers)

[http://fedoraproject.org/en/get-fedora-options](http://fedoraproject.org/en/get-fedora-options)

For Fedora - 1(less cutting edge but more stable)

[http://archive.fedoraproject.org/pub/fedora-secondary/releases/](http://archive.fedoraproject.org/pub/fedora-secondary/releases/)

I dual boot Ubuntu and Fedora, while I prefer Ubuntu because of ease of use, good hardware support and availability of software (without needing to compile them myself) But Fedora is also very good.

---

### Post by PIE09gbLmgG6 on 2013-02-16
Snowpine,

That makes perfect sense! Well said. 

That gives me a good direction to try things out.

Appreciate your time explaining.

ego-

---

### Post by PIE09gbLmgG6 on 2013-02-16
MB,

I'll hit those links right now! Thanks for the help.

ego-

---

### Post by monkeybrain2012 on 2013-02-16
If you want to try Fedora you may want to add some extra repositories (at least rpmfusion for multimedia and codecs)

[https://fedoraproject.org/wiki/Third_party_repositories](https://fedoraproject.org/wiki/Third_party_repositories)

Also I recommend installing Yumex (from Add-Remove or the terminal) to manage software. It is kind of like synaptic in Ubuntu and works better than the default Add-Remove package manager

---

### Post by monkeybrain2012 on 2013-02-16
> **blackbird34 said:**
> Outdated for you means tried and tested and stable for them. They're doing real stuff on it, they're not going to spend their time debugging crackpot Gnome 3 extensions...

Well walking is well tested and stable. Why drive a car or take a bus? I have never spend any time debugging gnome 3 extensions and FYI I also do real stuffs.

---

### Post by PIE09gbLmgG6 on 2013-02-16
MB!

Now I really feel like a newb...repositories...

I feel like there is so much to understand...

Guess I have some more homework tonight.

ego-

---

### Post by snowpine on 2013-02-16
You've been living under a rock if you think the Gnome 3/Unity transition hasn't been disruptive for many users. Multiply that by 1,000 or more employees, calculate the re-training costs, and you'll see why some corporations are happy to pay Red Hat a little extra to keep using the familiar Gnome 2 desktop for years to come. :)

---

### Post by gordintoronto on 2013-02-16
I can't imagine why the OP would want to do this. If Ubuntu doesn't turn your crank, try Xubuntu or Linux Mint. Huge repositories which resolve all dependancy problems: excellent solution.

---

### Post by Peripheral Visionary on 2013-02-17
> **egosophist said:**
> MB!

Now I really feel like a newb...repositories...

I feel like there is so much to understand...

Guess I have some more homework tonight.

ego-

Think of Repositories as libraries for software instead of books.  In Linux you don't have to go to some unfamiliar web site and download some program you think might be good, then install it.  Linux uses repositories and you can simply download and install stuff from there instead of some unknown or untrusted web site.  Ubuntu has made it even easier with their Software Center.

---

### Post by snowpine on 2013-02-17
Here's a great resource about repositories in CentOS:

[http://wiki.centos.org/AdditionalResources/Repositories](http://wiki.centos.org/AdditionalResources/Repositories)

The same concepts apply to Red Hat and Scientific.

---

### Post by snowpine on 2013-02-17
> **gordintoronto said:**
> I can't imagine why the OP would want to do this. If Ubuntu doesn't turn your crank, try Xubuntu or Linux Mint. Huge repositories which resolve all dependancy problems: excellent solution.

I agree that the average home/student/hobby/desktop/laptop/netbook user who simply wants email/facebook/youtube/games/office is probably better served with Ubuntu/Mint/Fuduntu/Fedora/etc. than enterprise-grade Linux.

Nevertheless since this particular thread is specifically about community versions of Red Hat, I have tried to be supportive of this inquiry in my responses.

---

### Post by mips on 2013-02-17
SL is supposedly quite stable but if you like apt and all those things then you could always go with Debian 7 which should be pretty stable seeing it went into freeze mode about 8 months ago.

I've never been a fan of RPM based distros but at the same time I have to admit that I have never actually tried any.

---

### Post by Peripheral Visionary on 2013-02-17
> **mips said:**
> 
I've never been a fan of RPM based distros but at the same time I have to admit that I have never actually tried any.

The only RPM distro I am even a tiny bit familiar with is PCLinuxOS.  Even the Xfce edition was too heavy for this computer, but it had Synaptic Package Manager so it was no different at all from that standpoint.  I know RPM is different from APT, but I never thought one was better than the other.  That's too geeky for me!

---

### Post by buzzingrobot on 2013-02-17
CentOS, Scientific, and Oracle Linux are all recompiled Red Hat Enterprise Linux with the trademarks removed. 

If you need stability more than new-ness, then look at any one of them.

I used CentOS 6.3 as a desktop for some time, and it was fine and very reliable.  Boringly reliable. Given Red Hat's position on open source, it comes with no proprietary drivers, codecs, etc. (Neither does Fedora, for the same reason.) Those, and other packages, are usually available from non-official repos, but you need to be careful how you mix and match them.  Some repos include packages that duplicate those available in the official repos, but which can break a system if inadvertently installed, say, during an update.

RHEL 6.3 (and the current versions of CentOS, Scientific and Linux) is based on Fedora12/13 along with some changes. Red Hat fixes bugs, backports kernel features (it ships with a 2.6 kernel but that is a bit misleading), and tries to avoid forcing users to update to new software versions just to get a bug fix. (They will try to isolate the fix and backport it to the version they ship.)

That accounts for its reputation for stability.  

Fedora is *not* RHEL.  Among other things, it's a place for RH to try out new things that may or may not work and may or may not make it into RHEL. The current Fedora release is at least as distant from RHEL as, say, Debian Sid is from whatever stable release they put out in 2010. A new release of RHEL 7 is expected later this year and it will be a similar amalgam of recent Fedora releases.

RHEL, CentOS, etc., include some core components that are difficult or impossible to upgrade without breaking it.  For example, it's pretty hardwired to use Python 2.6.  You can install 2.7/3.0 in a separate environment. But, if you replace 2.6 with a later version, your system  will break.

---

### Post by fuduntu on 2013-02-17
> **buzzingrobot said:**
> CentOS, Scientific, and Oracle Linux are all recompiled Red Hat Enterprise Linux with the trademarks removed. 

If you need stability more than new-ness, then look at any one of them.

I used CentOS 6.3 as a desktop for some time, and it was fine and very reliable.  Boringly reliable. Given Red Hat's position on open source, it comes with no proprietary drivers, codecs, etc. (Neither does Fedora, for the same reason.) Those, and other packages, are usually available from non-official repos, but you need to be careful how you mix and match them.  Some repos include packages that duplicate those available in the official repos, but which can break a system if inadvertently installed, say, during an update.

RHEL 6.3 (and the current versions of CentOS, Scientific and Linux) is based on Fedora12/13 along with some changes. Red Hat fixes bugs, backports kernel features (it ships with a 2.6 kernel but that is a bit misleading), and tries to avoid forcing users to update to new software versions just to get a bug fix. (They will try to isolate the fix and backport it to the version they ship.)

That accounts for its reputation for stability.  

Fedora is *not* RHEL.  Among other things, it's a place for RH to try out new things that may or may not work and may or may not make it into RHEL. The current Fedora release is at least as distant from RHEL as, say, Debian Sid is from whatever stable release they put out in 2010. A new release of RHEL 7 is expected later this year and it will be a similar amalgam of recent Fedora releases.

RHEL, CentOS, etc., include some core components that are difficult or impossible to upgrade without breaking it.  For example, it's pretty hardwired to use Python 2.6.  You can install 2.7/3.0 in a separate environment. But, if you replace 2.6 with a later version, your system  will break.

RHEL 6.x is fine for a server, or a mission critical workstation - but it makes little sense on a desktop or laptop.  Fuduntu tends to be a good fit there and should be considered before landing on whatever works best for the user. :)

Don't just take it from me though - ask this guy: [http://www.dedoimedo.com/computers/fuduntu-2013-1.html](http://www.dedoimedo.com/computers/fuduntu-2013-1.html)

:guitar:

---

### Post by Kov3nant on 2013-02-19
OP,  if you're looking to distro hop. You can do what I did.  Go to distrowatch and check out the top 10. Do a backup of your stuff and then just install anything that looks interesting. Dual booting is cool too because you can compare and contrast. And don't limit yourself to the top 10,  but it's a good starting point.  Depending on the kind of user you are,  you'll most likely end up using some version of Ubuntu or arch. Or both :)

---

### Post by buzzingrobot on 2013-02-19
> **fuduntu said:**
> RHEL 6.x is fine for a server, or a mission critical workstation - but it makes little sense on a desktop or laptop.  Fuduntu tends to be a good fit there and should be considered before landing on whatever works best for the user. :)

Don't just take it from me though - ask this guy: [http://www.dedoimedo.com/computers/fuduntu-2013-1.html](http://www.dedoimedo.com/computers/fuduntu-2013-1.html)

:guitar:

If you read Dedoimedo, you know that he has a CentOS partition on that laptop he uses for distro reviews. He's a CentOS desktop fan and has posted extensively about it.

I've used both Fuduntu and CentOS, the latter extensively.  They are very, very similar. If one makes sense as a desktop, so does the other.  Here are the basic differences:

1. CentOS 6.3 runs Gnome 2.28.  Fuduntu runs Gnome 2.32.

2. CentOS is recompiled RHEL 6.3, which is based on Fedora 12/13.  Fuduntu is a fork of Fedora 14.

3.  CentOS releases bug fixes released by Red Hat, as well as relaying issues upstream.  Fuduntu also uses Gnome 2 bug fixes released by Red Hat.

4. Fuduntu has more current libraries, etc.  Red Hat tries to avoid introducing new code into RHEL, preferring to backport fixes whenever possible to minimize the impact on customer installations. 

That's about it.  While it's a great server OS, and that is why it exists, fewer services are enabled by default in CentOS than, in my experience, an Ubuntu desktop.

I suspect that more independent repositories are available for CentOS than Fuduntu.  The Red Hat/Fedora community maintain, for example, an extensive site at epel.org specifically to support RHEL.  All those rpm's work on CentOS.

---

