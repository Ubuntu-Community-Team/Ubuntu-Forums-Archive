---
title: "Similar software for Ubuntu"
date: 2009-09-10
forum: Security
---

### Post by newyorkee on 2009-09-10
Hi,
 
A new user of linux system wanting to ask two questions :
 
1) Is there a similar software which support Ubuntu like the [http://www.faronics.com/html/AntiExec.asp](http://www.faronics.com/html/AntiExec.asp)?
 
2) Is possible to create a Ubuntu live cd in a write protect media like sd card? So when the write protect is on, the Ubuntu boot up and run successfully and all software like browser, video player, download files, install software, etc. Yes once reboot all the changes revert. In xp write protect intervene with booting and a alot of softwares is not possible to use. If possible how to go abt doing this?
 
Regards.

---

### Post by phillw on 2009-09-10
I think u need edubuntu for the control you want.

I'm pretty sure that from other forum replies - it is not the putting ubuntu onto the device that is a problem - it's the fact that u cannot set your bios to boot from SD cards !!

Sorry about the 2nd point - You can, however get usb memory sticks that have a 'lock' function on them to make them read only - I've never tried them in Linux, though,

Regards,

Phill.

---

### Post by cdenley on 2009-09-10
1. I don't think there is anything quite like that for Linux. Ubuntu uses apparmor which can restrict applications from runnning, but I don't think it can be configured to disallow all applications until they are allowed. Perhaps SELinux can do this, I never tried. Malware and unlicensed software typically isn't a problem in the Linux world.

2. Ubuntu wouldn't work well with write protect, either. There is a trick used for livecd's, though. The root filesystem can be mounted in a way that any changes will be written to a ramdrive intead and will not be persistent after a reboot. If you're concerned about your users making persistent changes, though, make sure they aren't in the admin group, because then they would be able to remount the root filesystem in a way that they can make permanent changes.

---

### Post by phillw on 2009-09-10
I *think* the OP is after an implementation of LTSP - I read in another posting that a disgruntled student has been asking how get around the security in edbuntu to install & run pidgin, for example.

:lolflag:

Phill.

---

### Post by __p1n__ on 2009-09-10
Using whitelist-based authorization for process execution is a fair stop-gap measure.  Although it formally appears to improve the logical security model given real-world os and MAC implementations it's potential protection is undercut and consequently cannot be relied upon in practical terms.

A few high-level examples illustrate:

A. ubuntu

1. If a segmentation fault can be induced remotely (and there appears to be no end to the trend of vulnerable network services not to mention network stack vulnerabilities) then after some trial and error injected shell code will execute.

2. As of Sep 2009 several local vulnerabilities exist in linux distributions that allow a process to gain uid 0 status.

3. A process that has root permissions can trivially turn off enforcement of SELINUX (this is effectively the same as disabling it but without requiring a reboot.)

4. Game over. MAC is now "switched off" and is providing zero effective security support.  

B. windows

1. If a segmentation fault can be induced remotely (and there appears to be no end to the trend of vulnerable network services not to mention network stack vulnerabilities) then after some trial and error injected shell code will execute.

2. Game over. Modern malware typically contains it's own process loader and is therefore invisible to any "windows security" product that works by hooking pexec calls or scanning the pet.  The payload can also be migrated to any running process owing to a complete lack of windows internal security so the whitelist is bypassed either way.

It's all frankly rather depressing which is why I've personally moved to and adopted a security by isolation approach.  It doesn't mean however that I won't use the maximum number of security measures within a given platform no matter how limited in effectiveness that they may be.

---

### Post by scorp123 on 2009-09-10
> **newyorkee said:**
>  
1) Is there a similar software which support Ubuntu like the [http://www.faronics.com/html/AntiExec.asp](http://www.faronics.com/html/AntiExec.asp)? Normally such stuff shouldn't be needed: The likelihood of catching malware and what not on Linux is rather small if you're a desktop user and don't do stupid things (like surfing the web as "root" ...).

In my opinion the easiest way to block e.g. certain users from accessing certain programs on a Linux system is to use Access Control Lists (ACL's). You could set an ACL and remove e.g. the "execute" bit on certain programs for certain user groups ... The result would be that those users would get a "Access denied" message and similar errors ("cannot execute") and so on while for everbody else not affected by the ACL everything would look and work as it did before.

So let's suppose I have a user group "kids" on my system and I don't want them to use e.g. Firefox because I want them absolutely to use Opera ... So I'd trigger these commands to block the Firefox binary for them:

**[COLOR="Red"]* *  PLEASE BE CAUTIOUS WITH THIS COMMAND!  * * [/COLOR]**
```
sudo setfacl -m g:kids:r- /usr/bin/firefox
```


But for this to work the file system has to be mounted with Access List support which per default it isn't.

Please read here for more examples:
[http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists](http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists)

---

### Post by bodhi.zazen on 2009-09-10
> **__p1n__ said:**
> Using whitelist-based authorization for process execution is a fair stop-gap measure.  Although it formally appears to improve the logical security model given real-world os and MAC implementations it's potential protection is undercut and consequently cannot be relied upon in practical terms.

A few high-level examples illustrate:

A. ubuntu

1. If a segmentation fault can be induced remotely (and there appears to be no end to the trend of vulnerable network services not to mention network stack vulnerabilities) then after some trial and error injected shell code will execute.

2. As of Sep 2009 several local vulnerabilities exist in linux distributions that allow a process to gain uid 0 status.

3. A process that has root permissions can trivially turn off enforcement of SELINUX (this is effectively the same as disabling it but without requiring a reboot.)

4. Game over. MAC is now "switched off" and is providing zero effective security support.  

B. windows

1. If a segmentation fault can be induced remotely (and there appears to be no end to the trend of vulnerable network services not to mention network stack vulnerabilities) then after some trial and error injected shell code will execute.

2. Game over. Modern malware typically contains it's own process loader and is therefore invisible to any "windows security" product that works by hooking pexec calls or scanning the pet.  The payload can also be migrated to any running process owing to a complete lack of windows internal security so the whitelist is bypassed either way.

It's all frankly rather depressing which is why I've personally moved to and adopted a security by isolation approach.  It doesn't mean however that I won't use the maximum number of security measures within a given platform no matter how limited in effectiveness that they may be.

I agree with most of what you said, however you left out Apparmor and I do not completely agree with your conclusion about the futility of selinux.

Both Apparmor and SELinux can restrict even root. With SELinux root can becomes just another user and you can assign supreme admin rights to an alternate user, so even cracking the root account does not get you very far.

With Apparmor you can confine all network aware applications and/or servers such that said injected code can be confined.

On a properly configured system it is not so easy to inject code and simply turn apparmor or selinux off.

With that said, I agree with you, I would not rely on either to be completely effective all the time, but I would not dismiss selinux or apparmor so casually either.

---

### Post by bodhi.zazen on 2009-09-10
> **scorp123 said:**
> But for this to work the file system has to be mounted with Access List support which per default it isn't.

Very nice example of ACL.

My only comment is that it depends on the file system. Not every file system supports ACL (ext2,3, and 4 do). With JFS, unlike ext{2,3,4},  acl is enabled by default.

I found this out by accident, you can not mount jfs with acl :

```
sudo mount -t jfs /dev/sda5 /mnt/point -o acl
``` will fail, but if you simply mount the jfs file system , without the acl option, acl can be set.

---

### Post by __p1n__ on 2009-09-10
> **bodhi.zazen said:**
> I agree with most of what you said, however you left out Apparmor and I do not completely agree with your conclusion about the futility of selinux.

Both Apparmor and SELinux can restrict even root. With SELinux root can becomes just another user and you can assign supreme admin rights to an alternate user, so even cracking the root account does not get you very far.

With Apparmor you can confine all network aware applications and/or servers such that said injected code can be confined.

On a properly configured system it is not so easy to inject code and simply turn apparmor or selinux off.

With that said, I agree with you, I would not rely on either to be completely effective all the time, but I would not dismiss selinux or apparmor so casually either.

Both AppArmor and SELinux leverage LSM kernel hooks so I simply picked SELinux as the examplar.  Inasmuch as my post avoided policy details you can freely interchange both at this high level of discussion.

I used uid=0 to refer to traditional root-level privileges and not specifically root account so I'll apologize for that confusion.  The publicly disclosed local root vulnerability a week or so ago will in fact result in a running process with superuser privileges.  Whatever configuration you may have made with respect to the actual root account with those tools is moot.

I have intentionally kept this at a high level so as not to support the expansion of the exploits referred to however I will state that turning off SELinux enforcement requires only a 1 line echo command.  Code injection is also always possible as long as there is an active network connection and at least one process to read packets from the network stack.  Please note that there is usually at least one other client process reading PRE packets from the network stack in addition to the routing process that implements IPTables so this latter is not always effective.

You are quite correct in stating that configuring these elements will "harden" a system and I fully agree with and personally implement this approach.  It is however not enough in my humble opinion which is why I sandbox the entire o/s as well.

Thank you for your excellent comments.

---

### Post by bodhi.zazen on 2009-09-10
Have you ever run selinux strict (Fedora, Centos, RHEL are targeted by default)? Just curious if you have ever toyed with it. It is not so easy to disable in strict mode. Not saying it can not be done mind you.

With apparmor you can restrict root's shell as well.

Again, not saying they are invulnerable, just saying it is possible to restrict root or UID 0 (that is part of the fun of running selinux / apparmor, restrict access to $HOME and reign in root).

In the case of Apparmor, you are injecting code into something, and that something can (potentially) be confined.

Is it fool proof, no of course not, but IMO they are potentially the best tools out there, if any exist, for such code injections.

I am also curious as to what you are doing to "isolate" your system, what is it you feel is better then selinux / apparmor ?

---

### Post by __p1n__ on 2009-09-10
> **bodhi.zazen said:**
> Have you ever run selinux strict (Fedora, Centos, RHEL are targeted by default)? Just curious if you have ever toyed with it. It is not so easy to disable in strict mode. Not saying it can not be done mind you.

I am also curious as to what you are doing to "isolate" your system, what is it you feel is better then selinux / apparmor ?

I haven't tried that, thanks for the suggestion.

There's nothing wrong with using LSM-based tools to tighten up a system. More can be done however.

My main machine at home runs the Xen hypervisor (3.4.1) and NetBSD (5.0.1) in a VMM as dom0.  The disk is partitioned into 2 areas: a 50 GB partition for NetBSD and the rest is a logical container.  I've carved up the container into a number of 50GB logical volumes.  When I run up an os instance to do something I create a new VMM referencing a specific logical volume.  The domu will boot up inside the VMM - usually kubunutu but I run an xp image from time to time as well.

The real networking happens down at the dom0 (NetBSD;) pf has the real rules and traffic is bridged to the logical network inside the domu.  I do my work inside the guest os which looks just like it would if it was running natively on the machine.  If the domu gets infected or corrupted (you can't make anything absolutely tight) then I just exit the VMM and delete the logical volume from within NetBSD.  A quick block copy from the reference kubuntu volume to the target volume and you're back up and running in 10 minutes.

There are a few exploits that can break out of a VMM but they're mostly targetted at vmware and paravirtualized domu's.  With Xen at this release level and my chipset my VMM's use hardware virtualization so the guest os requires zero modifications and literally sees no difference between running in the VMM and running natively on the box.

That's what I mean by isolation.

---

### Post by bodhi.zazen on 2009-09-11
Thank you.

---

### Post by newyorkee on 2009-09-15
Frankly speaking, don't know there exit a perfectly clean system be xp vista or linux. Even there is most likely the users is really expert in computer. Using xp all along and all along know there is a hacker watching all the work. Whatever want to do, the hacker would try to thwart the attempt. Simple things like searching youtube (the hacker remove all pictures, clicking new new link don't load the page), downloading software (hacker attach their own script even while downloading, remove softwares functions), and delete work in progress files on rebooting. Even when this is wrote the hacker is watching . Simple hate them... a bunch of idiots.
 
Thought if work on files using a no internet connection computer that would get rid of them initially. However files still gets deleted on reboot and softwares gets modified. Anyone knows is possible to browse a computer screen remotely when the computer is not connected to to internet? Not using wifi or wireless just cables. Maybe they are using another computer (with internet) to connect using just electricity. And their modification is realtime like when searching for madonna on youtube a few times the hacker knows your fav is madonna and whatever search you enter abt the celebrity name, the pictures are remove. No this is not browser supporting pictures files format problem. Even system having administer gets hacked too.
 
Wanted to install and use a clean machine. How? Currently all systems in house are all get comprised. Cafes? No ways... Formatting or even low format... yeah tried that but they are still there. Suspect they put there hiddeous files on the monitor hardwares or dvd rw? Use to think format gets rid of everything but not now...
 
Another question: if a dvd-r has burned and there are unused space on the dvd, is possible for hacker to attach or burn new files onto the dvd once the dvd is put into the dvd rw? Or once burn the dvd-r is not possible to write too even there is unuse space?

---

### Post by rookcifer on 2009-09-15
> **__p1n__ said:**
> Both AppArmor and SELinux leverage LSM kernel hooks so I simply picked SELinux as the examplar.  Inasmuch as my post avoided policy details you can freely interchange both at this high level of discussion.

I used uid=0 to refer to traditional root-level privileges and not specifically root account so I'll apologize for that confusion.  The publicly disclosed local root vulnerability a week or so ago will in fact result in a running process with superuser privileges.  Whatever configuration you may have made with respect to the actual root account with those tools is moot.

I have intentionally kept this at a high level so as not to support the expansion of the exploits referred to however I will state that turning off SELinux enforcement requires only a 1 line echo command.  Code injection is also always possible as long as there is an active network connection and at least one process to read packets from the network stack.  Please note that there is usually at least one other client process reading PRE packets from the network stack in addition to the routing process that implements IPTables so this latter is not always effective.

You are quite correct in stating that configuring these elements will "harden" a system and I fully agree with and personally implement this approach.  It is however not enough in my humble opinion which is why I sandbox the entire o/s as well.

Thank you for your excellent comments.


I assume you are talking about the ["NULL pointer"]("http://blog.cr0.org/2009/08/linux-null-pointer-dereference-due-to.html") root exploit demonstrated by Brad Spengler where he demonstrated himself turning off SELinux (Brad has found more than one of these over the years).  And then there was a [similar exploit]("http://kernelbof.blogspot.com/") found back in July where the author showed how he was also able to disable SELinux.  I think he even used the words "Game Over" in his blog post. :)

But none of this is taking into account the protections provided by PaX and Grsecurity (as well as upstream protections like SSP), for instance.  I realize that memory hardening and MAC's wont stop all possible exploits, but they will stop *most* of them.  In fact, the only reason SELinux was disabled with this recent null pointer vuln was because the default Red Hat/Fedora SELinux policy was not adequate enough to handle it.  All it takes is a change of the policy.

And PaX hardened systems were immune to this null pointer vuln, as you can see in the first link I provided.

---

