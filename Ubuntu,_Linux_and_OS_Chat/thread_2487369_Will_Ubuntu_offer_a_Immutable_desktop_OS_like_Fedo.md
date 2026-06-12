---
title: "Will Ubuntu offer a Immutable desktop OS like Fedora &amp; some others"
date: 2023-06-01
forum: Ubuntu, Linux and OS Chat
---

### Post by grahammechanical on 2023-06-01
It is a long read. You may find it interesting. Ubuntu immutable Desktop OS could be the offered future of Ubuntu. Testing it will be interesting. Some forum members may also see some benefit from Snap packaging. :) Those forum members can be reassured by this statment:

> For tinkerers, the classic Ubuntu images would remain their preferred  route to enable full control of (and responsibility for) their system.

[https://ubuntu.com/blog/ubuntu-core-an-immutable-linux-desktop](https://ubuntu.com/blog/ubuntu-core-an-immutable-linux-desktop)

I am hoping that discussion will revolve around the benefits or otherwise of an immutable desktop OS.

Regards

---

### Post by Bashing-om on 2023-06-01
Well ---

Will be an interesting experiment, but,
speaking for myself I am fine with the traditional xubuntu desk top :D

[INDENT]it it ain't broke do not fix it !
[/INDENT]

---

### Post by TheFu on 2023-06-01
I'm good with more choice, but Unix systems have supported read-only / and /usr areas for 40+ yrs.
/etc and /var and HOME directories need to be read-write, but pretty much everything else can be read-only.

It does mean updating the OS a little different, but these days, wasting storage and RAM seems to be fine.  Users are expected to just buy more.

People have been running ISO-based versions of Linux for over a decade.  Those are definitely "immutable" if the temporary CoW aspects are carefully handled.

More choice, nothing forced, is good.

---

### Post by ajgreeny on 2023-06-02
Have you seen the info about Ubuntu-Core at [https://ubuntu.com/core](https://ubuntu.com/core) which may or may not be quite what you're asking but is perhaps the nearest that you will find.

Not certain it is immutable and it's  not something I've investigated any further as I have no use for it.

**EDIT:**

Whoops!
I didn't read your OP properly and UC was already mentioned there.

---

### Post by enricobe on 2023-06-02
I really like the idea and I'll try it for sure.

I don't think that Snaps can satisfy all the desktop-users needs at the moment so I expect a very low adoption of this kind of Ubuntu Desktop. I really hope Snaps can grow in quantity and quality and be a serious alternative to the traditional package management

---

### Post by Bashing-om on 2023-06-02
A more reasoned take on what might be:
[https://www.zdnet.com/article/theres-a-new-ubuntu-linux-desktop-on-its-way/#ftag=RSSbaffb68](https://www.zdnet.com/article/theres-a-new-ubuntu-linux-desktop-on-its-way/#ftag=RSSbaffb68)

---

### Post by kurt18947 on 2023-06-03
I wonder if this is an effort to make Ubuntu more acceptable in the enterprise. Home users/hobbyists want access to most parts of their operating system. Enterprise sysadmins certainly DO NOT want their users making changes to most parts of their operating system. Immutable should also make the black hats 'job' more difficult.

---

### Post by #&amp;thj^% on 2023-06-03
> **Bashing-om said:**
> 
speaking for myself I am fine with the traditional xubuntu desk top :D

[INDENT]it it ain't broke do not fix it !
[/INDENT]

Buy this man a big Beer, I was glad to hear the traditional Desktop will still be the same, but Severs and Admins might rejoice with the Immutable Core install.
BTW Immutable desktop??? Why? I'm only guessing but I assume this to mean "immutable operating system".
Thanks for the link grahammechanical. ;)

---

### Post by lammert-nijhof on 2023-06-03
Now hackers get better tools available like e.g AI, anything increasing security is welcome. I will surely test it with 24.04 and I might switch to it after it matured say for say two more years. 

For safety and security I have moved all my Apps to 6 VMs, to reduce the impact of malware. All data and all VMs are running from OpenZFS, so I can roll back to undo a hack. In the last 10 years I have been hacked twice both in 2022. The malware had been introduced by email and the other by the browser, rolling back the VM solved the Issue.  Another advantage from OpenZFS is, that VMs fun from memory cache (L1ARC), so it is like running the system from a RAM disk.

Currently I start working with encryption, my banking VM has been encrypted by Virtualbox since early 2022.  In 23.10 I'm trying out encryption by the Ubuntu installer/OS itself, but currently boot times are 42 seconds instead of 15 seconds.  I'm interested in using it for the Host OS a minimal install of Ubuntu, that I boot say once per day.   VM encryption by Virtualbox only adds ~10% to the boot time and is thus preferable for VMs and that 10% is not noticeable during normal operation.  

That immutable OS I will surely consider for the Host OS, but maybe also for one or two VMs, the banking one and the one for communication, which has a few open ports.

---

### Post by philhughes on 2023-06-25
If anyone wants to take a very early look at this, you can get development releases. You'll need a Github account.

[https://www.omgubuntu.co.uk/2023/06/try-ubuntu-snap-desktop](https://www.omgubuntu.co.uk/2023/06/try-ubuntu-snap-desktop)

---

### Post by TheFu on 2023-06-25
"Ubuntu Core" should be renamed to "Ubuntu-Snaps" to more clearly reflect the true nature of that release.

---

### Post by lammert-nijhof on 2023-06-25
I did  get Ubuntu Core running using virt-manager, after I selected UEFI install.  It is  really a core installation, with only an absolute minimal set of  applications. I have no clue yet about performance, because I use  Virtualbox and I don't like to contaminate my desktop PC for one  try-out. 

But I always keep an eye on virt-manager/KVM, so I have a  Virtualbox VM with the Ubuntu 23.10 Development Branch, that supports  nested virtualization with virt-manager/KVM and I run two KVM-VMs in it;  Ubuntu 14.04 LTS and Peppermint 10 and just now I've added Ubuntu Core  22 to it.
So performance seems fine taking into account that I run the Ubuntu Core 22 Desktop
- on top of KVM in Ubuntu 23.10 
- on top of Virtualbox 7.08 in Ubuntu 22.04 LTS 
- on top of a Ryzen 3 2200G, the 2nd slowest Ryzen CPU ever :sad:

The boot time seems equal to the encrypted Ubuntu 23.10 on UEFI and both are ~2x the boot time of Ubuntu 22.04 LTS or Ubuntu 23.10 on MBR. 
 Tomorrow  I will try to install some programs, that I normally use and  one of the most important programs will be Conky for comparing  performances.
It did play music using Firefox, but it stutters a little but :(     I have a look at that too :)

---

### Post by lammert-nijhof on 2023-06-25
TheFu: You like to kill the project before it even started?  By the way the Ubuntu Core Desktop runs in an lxc container, so the name is perfect :)

---

### Post by TheFu on 2023-06-26
> **lammert-nijhof said:**
> TheFu: You like to kill the project before it even started?  By the way the Ubuntu Core Desktop runs in an lxc container, so the name is perfect :)

Some people actually seek out snap packages, for specialized needs.  Even me. Occasionally.  For example:
```
$ snap list
Name       Version      Rev    Tracking       Publisher   Notes
core18     20230530     2785   latest/stable  canonical&#10003;  base
nextcloud  25.0.7snap1  35562  latest/stable  nextcloud&#10003;  -
snapd      2.59.5       19457  latest/stable  canonical&#10003;  snapd

```
I have to say, running nextcloud as a snap package has been easier than do a manual install and maintaining nextcloud.  I did have a hiccup when the snap moved from 24.x --> 25.x and broke some important addons.  I forced a downgrade and told snap to remain on 24/stable.  In theory, it should still be running 24/stable, not 25.x now - so there's definitely a huge, huge, huge, bug in the snap management software, but since I didn't notice when the 2nd attempted upgrade happened, all the addons are working, I'm not going to complain.  I really should. If you tell a snap to stay on a specific release track, it shouldn't change. Period.

Snaps need some things fixed to be ready for production use and there are many things I really dislike about them, but the design has some good ideas as well, with some important caveats.  I don't think Canonical should inflict snaps onto users without their explicit desire, but that's a management choice by Canonical.  My LUG stopped telling people to use Ubuntu as a learning platform for Linux for noobs, mainly due to massive confusion over snap packages. 

But that as little to do with Ubuntu-Snaps distro.  People choosing that would want snap packages.

---

