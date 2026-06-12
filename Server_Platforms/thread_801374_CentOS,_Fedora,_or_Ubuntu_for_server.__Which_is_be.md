---
title: "CentOS, Fedora, or Ubuntu for server.  Which is best?"
date: 2008-05-20
forum: Server Platforms
---

### Post by laptoplinux on 2008-05-20
The title sums it up.  And, posting this on an Ubuntu forum, I know beforehand that the answers might be a little biased.  

But the gist of it is that I may soon need to set up and periodically administer a box that will be used for subversion, among other things.  I've been using Ubuntu since Feisty on might desktop and have loved it overall.  My first instinct is to go ahead and load Hardy LTS on the new server, but then again Fedora seems to be the go-to distro for servers.  

I realize that Canonical is working hard to make Ubuntu a server household name in its own right with some already evident success, but I know Fedora supposedly has a history of being a strong server platform, and nearly every server I've seen in the past is usually running some form of Red Hat-inspired software.  

Come to think of it, I had forgotten about CentOS.  How does that stack up?  

I haven't really administered a server of any kind before, so I'd appreciate honest assessments of each distro's ease of use, reliability, security, availability of convenient admin tools, etc. and any other points that would be relevant.  

Thanks in advance.

---

### Post by geertn on 2008-05-20
CentOS or Ubuntu because of the long support cycles. Ubuntu because it's newer, uses .deb packages and because it shines:)

---

### Post by Caraibes on 2008-05-20
Debian Stable all the way !!!
:)

---

### Post by solcott on 2008-05-20
I would pretty much agree with the CentOS or Ubuntu statement.  Fedora is basically the testing ground for Red Hat Enterprise Linux, the Fedora users who don't pay for Red Hat Enterprise Linux are basically the guinea pigs to find out what works good and what works bad and the result becomes a RHEL release.

CentOS, on the other hand, for the most part *is* RHEL.  RHEL packages are built from source, the ditrobution name is changed and whammo, CentOS Linux.

You say you've used Ubuntu since Feisty, so you've probably gotten familiar with how installing packages works.  Because of Ubuntu using Debians dpkg system I think Debian based OS's really have the superior package management solution.

Security.  The most 'secure' of the three would probably be CentOS, because it uses old packages.  Distrobutions like RHEL and it's clones (eg. White Box, CentOS) as well as Debian don't allow a package into their release until it is practically ancient, with a track record that proves that there is *nothing* wrong with it.  Fedora and Ubuntu release package updates far more often.  If a piece of software is updated by it's creator, and those updates to the software don't cause it to stop working updated packages will generally be released for Ubuntu/Fedora.  For example Ubuntu 8.04 is using xorg 7.3, and I can be pretty certain the majority of users would agree with me on this one, which has **less** functionality than the version included in Ubuntu 7.10 but it didnd't cause anything to stop working so the newer software version was released.

As far as administrating the servers.  For a first timer you'll probably want to get a tool like Webmin, and with tools like that the administration would be the same on all of them.  What you should think about is what distro you will be most comfortable with when things don't work, because seriously when you get new things you play with them and when you play with them too much they break, and then after you fix that you are going to play, and break, with something else and pretty much repeat that until you run out of things to play with.

For me, I usually run out of things to play with just in time for the every six month release, then I get some new toys to break :-)

---

### Post by geertn on 2008-05-20
> **solcott said:**
> 
Security.  The most 'secure' of the three would probably be CentOS, because it uses old packages.


I don't agree with this statement. New versions of software sometimes silently fix bugs which can hide security problems in earlier version. Furthermore, software will get new security features (e.g. ssh privilege separation) which you miss when using old packages.

---

### Post by ginjabunny on 2008-05-20
For my home server/firewall I used to use Fedora then CentOS but SELinux was driving me nuts, SELinux is a good idea as long as you don't want to do anything out of the ordinary and I wanted to experiment, then I tried Debian but I didn't like it not being the latest packages, so I switched to Ubuntu and now I am happy because it is flexible.

So if you want super-secure then maybe something with SELinux is good, I don't think it is implemented on Ubuntu server (I maybe wrong). If you want super-stable try Debian.

That's my 2 pence worth :)

---

### Post by nix4me on 2008-05-20
For a production server I would use Debian Stable or CentOS.  For a home server I would entertain Ubuntu or Fedora.  I like them all.  I have a production server that ran Fedora for a while but i got tired of updating it all the time with package updates.  CentOS and Debian both are rock solid.  CentOS has better documentation out there, Debian has a large community support.  Ubuntu is stable, but there will be updates to it pushed often.

---

### Post by ubudog on 2010-08-24
For my site, I am setting up a Fedora server.  I got the "Security" spin.  Fedora is probably the best for a home server.

---

### Post by CharlesA on 2010-08-24
Two year old thread is old.

Use what works best for you.

---

### Post by Sef on 2010-08-24
Necromancing, so locked.

---

