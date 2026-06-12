---
title: "Considering Fedora Instead of Ubuntu as a Desktop OS"
date: 2023-01-15
forum: Ubuntu, Linux and OS Chat
---

### Post by sash5 on 2023-01-15
I have been using Ubuntu for a while. If you're using your OS as your desktop environment, it's all about the installed software. But so far I have not always been able to find an easy and safe way to install new software on Ubuntu, and now I am considering Fedora as an alternative.

The easiest and safest way to install some software is to use the standard repositories that are installed with the OS and are considered a trusted source of software packages. During installation from this repository, software authentication and integrity is performed automatically on Ubuntu and Fedora. The advantage of Fedora is that the standard repositories have newer packages and are updated more frequently.

The second option is to install software packages from third-party repositories. The problem here is that you have to trust this repository, and if you want to double-check a software package before installing it, for example with virus total, it's difficult. In this case, Ubuntu and Fedora are identical.

A third possibility, and many programs are distributed this way, is to download an installation package. You must trust the source. But if it is a deb package for Ubuntu, the signature can only be provided as a separate file, and this is not always the case. And rpm for Fedora always contains signatures, the authenticity and integrity of which is checked automatically.

There is definitely a way to build software packages from source, but it can be tricky and is the same for Ubuntu and Fedora.

Correct me if I'm wrong in my consideration.

---

### Post by TheFu on 2023-01-15
Seems correct to me.  Always remember that "new" is the enemy of stable.  If you want the newest, then a rolling release like Arch would be better. Of course, the risk is in being too new, thus unstable.
Fedora isn't considered a stable release and doesn't provide any LTS like Ubuntu.  That could be important. It is for me.

But we are all different with different considerations.  It doesn't hurt to look around, try some other versions, see if you like them better.  If you go with Fedora, is losing support every 6 months acceptable? Do you want to do a fresh install 2x a year?

Rather than dumping Ubuntu with just hope that it is better, perhaps you could run Fedora inside a VM for a few months first.  Then you'll "know" if it will fit your needs and whether the really new stuff will be a problem or not. Same for Arch and any other distro.  There's no commitment besides 40G of storage to have sufficient room to try out everything.

---

### Post by #&amp;thj^% on 2023-01-15
I wish I could add here without a flame bait.
"New" is the gateway to stable, but until it is classified as stable, USER BEWARE.
I agree with TheFu Arch or an Arch based distro would be the best option, for ease of installing software.

---

### Post by QIII on 2023-01-15
I use Fedora every bit as much as I use Ubuntu.  There is absolutely nothing wrong with using another OS, nor is there anything wrong with just going with another OS entirely.  This should never by seen as a marriage or a religion.

My software company (from which I have *mostly* retired and turned over to other members of the family) develops bespoke, one-off Windows software for specific applications in specific industries.  I shrug off the brickbats hurled by true Linux believers.  I don't like Microsoft's business practices and the overly complex and non-open source bits don't please me either.  But Windows definitely serves the needs of my clients.

Use what works for you.  That's the whole point of the freedom of the Linux ecosystem.

---

### Post by sash5 on 2023-01-15
> **TheFu said:**
> Always remember that "new" is the enemy of stable. 
Not always. If the update is an implementation of a new feature, it may be unstable because it has not been well tested. But if it's a bug fix, or even a hot fix that closes a security hole, it's very important to get this update as soon as possible. And I've seen some packages that haven't been updated for a very long time, like wine, docker, rclone etc.

---

### Post by exploder on 2023-01-15
> There is absolutely nothing wrong with using another OS, nor is there anything wrong with just going with another OS entirely. This should never by seen as a marriage or a religion.

Use what works for you. That's the whole point of the freedom of the Linux ecosystem. 

Well said!

---

### Post by sash5 on 2023-01-15
> **QIII said:**
> That's the whole point of the freedom of the Linux ecosystem.
I just consider the time i have to spend to install and configure Fedora, and if this investment make sense :)

---

### Post by #&amp;thj^% on 2023-01-15
And only time will tell. :)

---

### Post by mark-chandler on 2023-01-15
> **QIII said:**
> 
There is absolutely nothing wrong with using another OS, nor is there anything wrong with just going with another OS entirely.  This should never by seen as a marriage or a religion.


Quoted for truth.

---

### Post by grahammechanical on 2023-01-15
I have absolutely no interest in whether someone uses Ubuntu or chooses some other Linux distribution. I do not care if they choose an operating system that is not open source. Life is too short to get worked up over these things.

I am very loyal to Ubuntu since I first installed Ubuntu 07.04. I will admit to being tempted to try Fedora Silverblue. I think an immutable OS is a good idea. If I knew how to put a desktop environment on Ubuntu Core then I would try doing that. 

I tell you this: If I did install Fedora Silverblue and I found that it did not compare well with Ubuntu then I would not go on a Fedora forum and say so. We are not that sort of person on Ubuntu forums. Are we?

Regards

---

### Post by ActionParsnip on 2023-01-16
Try it, see what you reckon

---

### Post by MAFoElffen on 2023-01-17
I remember reading the history of Linux distributions and branches. When it got to Debian, it said that it's Dev's said that Debian "is for people that need something that works." There is something to be said for long support cylces and repo's that are full of testing and patching.

I keep a few Fedora VM's around... As well as others. Explore. Test. Sometimes you can earn an appreciation for things, seeing what else is out there.

---

### Post by SeijiSensei on 2023-01-18
I suggest you add support for virtual machines, either through [VirtualBox]("https://virtualbox.org/") or the kernel VM facility ([KVM]("https://www.tecmint.com/install-kvm-on-ubuntu/")), to your current Ubuntu installation. Then create a VM and install your candidate Fedora distribution for comparison.

---

### Post by slickymaster on 2023-01-18
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

