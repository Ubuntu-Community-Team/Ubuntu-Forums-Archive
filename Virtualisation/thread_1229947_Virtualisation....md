---
title: "Virtualisation..."
date: 2009-08-02
forum: Virtualisation
---

### Post by my.self on 2009-08-02
Hi,

I'm using Ubuntu 9.04 and I really need virtualisation for my development environment (Visual Studio, Blend usw.)

First i tried VirtualBox but i wasn't able to set the screen resolution to 1920x1200.

So i tried VmWare Server...
1.) I guess my virtual machine (Win Xp) wasn't as fast as on Windows host. I haven't made any tests but subjective it felt slower...
2.) When i let my virtual machine running a while it crashed. I just saw the last screen but my XP-VM did not response anymore ;-(

Then i tried VmWare Player
1.) When i start my Win Xp in VmWare Player my whole Ubuntu is extremely lagging for about 5 minutes.
I wasn't able to switch to console to kill VM processes,
VLC stopped playing music and so on...
This can't be normal to go thru this everytime i start my VM ;-(


Any Suggestions?

LG Stefan

---

### Post by jocampo on 2009-08-02
> **my.self said:**
> Hi,

I'm using Ubuntu 9.04 and I really need virtualisation for my development environment (Visual Studio, Blend usw.)

First i tried VirtualBox but i wasn't able to set the screen resolution to 1920x1200.

So i tried VmWare Server...
1.) I guess my virtual machine (Win Xp) wasn't as fast as on Windows host. I haven't made any tests but subjective it felt slower...
2.) When i let my virtual machine running a while it crashed. I just saw the last screen but my XP-VM did not response anymore ;-(

Then i tried VmWare Player
1.) When i start my Win Xp in VmWare Player my whole Ubuntu is extremely lagging for about 5 minutes.
I wasn't able to switch to console to kill VM processes,
VLC stopped playing music and so on...
This can't be normal to go thru this everytime i start my VM ;-(


Any Suggestions?

LG Stefan

What's the host hardware (CPU, RAM, disk's rpms) ... that's the 1st step if you want to install any Virtual Machine. For Windows and if you want acceptable performance, you must assign between 512 and 1gb RAM for just that virtual machine. Of course, we're assuming your host runs with 2gb RAM at least. 7200rpm or more for hard disk is recommended if you are going to "push" your VMs a bit.

Regarding VirtualBox, did you install the VirtualBox additions? usually you do not have any screen resolution or mouse problem after you do that.

BTW, Virtualization is with "z" ... ;-)

---

### Post by my.self on 2009-08-02
Yes,
I installed additions and tools...

I'm working on a Dell Vostro 1710 Notebook with 2x2.4ghz, 4gb ram(but only 3 available on my 32bit ubuntu), 2x160gb HDD 7200rpm, Nvidie 8600m ...

I already worked on a XP Host with a Windows 2008 server VM on this notebook for some time and I think this was much faster...


OMG,
it's really written with "z" *gg*
In Austria it's 3am and I'm on my 6th beer so you have to excuse this ;-)

---

### Post by jocampo on 2009-08-03
Something is wrong...it looks like you have decent hardware. Post result(s) of this command, please, when running the VirtualMachine on top of UBuntu

```
free -m
``` 


Also, are you using a recent version of VirtualBox? there are some annoying bugs and issues on old versions.

---

### Post by my.self on 2009-08-03
I definitely know that my notebook isn't the problem.
I also have a Windows XP installed and there my Windows Server 2008 VM runs without any troubles...

I don't know the exact version of VirtualBox is used...
I just installed it via app-get about one month ago.

---

### Post by my.self on 2009-08-04
Ok,
now I installed VirtualBox 3 and it runs perfect!

---

### Post by jocampo on 2009-08-04
> **my.self said:**
> Ok,
now I installed VirtualBox 3 and it runs perfect!

Did you download and installed the virtualbox additions? please do that, in order to improve mouse and video driver behavior ... ;-)

---

