---
title: "apt-get update not working correctly"
date: 2012-10-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-10-14
Today I just found that synaptic crashes and will not start any longer.
Then, in terminal when I run
```

sudo apt-get update

```
apt stops reading package lists when 45% is done and will not go any further.

I also found out that if I remove the universe part from /etc/apt/sources.lists,
all is well again and synaptic also is OK.

Is there some temporary issue with universe repo now?
Does some one else see this too?

BTW.
I use main repository server.
This might be this bug (#1066445): 
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1066445](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1066445)

---

### Post by Elfy on 2012-10-14
All works ok here - gb archive.

---

### Post by philinux on 2012-10-14
Just done an update via chroot and all ok here ok Main server.

---

### Post by Harry33 on 2012-10-14
I can now confirm this is the bug #1066445.
It seems to affect only amd64 setups.
The bug is considered critical.

---

### Post by philinux on 2012-10-14
> **Harry33 said:**
> I can now confirm this is the bug #1066445.
It seems to affect only amd64 setups.
The bug is considered critical.

I'm using amd 64 bit here.

---

### Post by matt_symes on 2012-10-14
I'm not seeing this issue either with amd64 and gb servers.

I updated not 2 hours ago.

---

### Post by Billxyzzy on 2012-10-14
Are you using a system that has win 7 installed?
sudo apt-get update reports problems when win 7 is also available.  Update suggests running dpkg --configure -a  when this is done it hangs.
using Ctrl c causes it to continue but spits out error messages at the end.
sudo apt-get upgrade freezes at the end and locks up a terminal.
This has been the same for several days now.
I just updated this morning and still have the problems.
Ignoring that terminal and selecting firefox allows the system to run.  I am posting in this condition at this time

---

### Post by funicorn on 2012-10-14
try
sudo apt-cache gencaches && sudo apt-get update

if not work&#65292;

cd /var/lib/apt/lists
sudo rm partial/* && sudo apt-get update

if not work, 

cd /var/lib/apt/lists/
mkdir -p ~/apt_lists && cp * ~/apt_lists/ && sudo rm *
sudo apt-get update

---

### Post by Billxyzzy on 2012-10-14
Still no good 
error reports memtest+86 fails and ubuntu-standard fails.

---

### Post by Harry33 on 2012-10-14
> **Billxyzzy said:**
> Are you using a system that has win 7 installed?
sudo apt-get update reports problems when win 7 is also available.  Update suggests running dpkg --configure -a  when this is done it hangs.
using Ctrl c causes it to continue but spits out error messages at the end.
sudo apt-get upgrade freezes at the end and locks up a terminal.
This has been the same for several days now.
I just updated this morning and still have the problems.
Ignoring that terminal and selecting firefox allows the system to run.  I am posting in this condition at this time

Nope. No windows-fun here. :lolflag:

---

### Post by Harry33 on 2012-10-14
> **philinux said:**
> I'm using amd 64 bit here.

OK.
The, what if you edit your sources.list file in a way that both
quantal main and universe are in the same line.
Like this:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main universeI get the crash even if I comment all other deb lines from sources.list.
If I remove the universe, then no crash any longer.

---

### Post by Harry33 on 2012-10-14
This critical issue is now fixed with the newest apt update (0.9.7.5ubuntu4):

> 
apt (0.9.7.5ubuntu4) quantal-proposed; urgency=low
[ Colin Watson ]
* apt-pkg/pkgcachegen.cc:
- Fix crash if the cache is remapped while writing a Provides version
(LP: #1066445).
Cherry-pick from [http://bzr.debian.org/bzr/apt/apt/debian-sid:](http://bzr.debian.org/bzr/apt/apt/debian-sid:)

[ David Kalnischkies ]
* apt-pkg/pkgcachegen.cc:
- add a missing remap registration causing a segfault in case
we use the not remapped iterators after a move of the mmap again


---

