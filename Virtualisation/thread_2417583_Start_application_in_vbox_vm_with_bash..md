---
title: "Start application in vbox vm with bash."
date: 2019-04-24
forum: Virtualisation
---

### Post by antoniovc on 2019-04-24
Hi eveyone,

I need some help from you guys.
My problem is the following;
I would like to start an application in a virtual-box vm with a bash-script placed on my Ubuntu desktop, and i would like to suspend the continuation of the bash-script till I'm finished with that application .
The bash-script should continue the moment I stop the application in the vm.
Is this possible?

I have the following:

#!/usr/bin/env bash 
VboxName="Windows 10 Enterprise LTSC"
VAppName="C:\\Windows\\System32\\calc.exe"

VBoxManage -nologo startvm "$VboxName"
VBoxManage -nologo guestcontrol "$VboxName" run --exe "$VAppName" --wait-stdout      


Is it possible to start seamlessly?

How can I suspend the continuation of the bash-script till I'm finished with my work?

How can i force the vm going in suspending mode?

I'm new to Linux, and help will be much appreciated.

Rgds.

---

### Post by TheFu on 2019-04-25
[https://www.virtualbox.org/manual/ch08.html#vboxmanage-guestcontrol](https://www.virtualbox.org/manual/ch08.html#vboxmanage-guestcontrol) has examples.  All the examples show specifying a userid and password due to security requirements inside the guest.

There is a timeout option which might be useful.

BTW, Windows supports using / instead of \\ for directory separators.  Cross-platform programmers have been using this fact for 25+ years. On any Windows machine, type 
```
c:<enter>
cd /windows/system32<enter>
```
what directory are you in now?

I haven't used vbox in a long time, so can't test this.  I'm not certain about the suspend or running in seamless mode.  I never used either of those features more than a few times just to see what they did.  I was not impressed that they'd fit anything in my needs.

---

