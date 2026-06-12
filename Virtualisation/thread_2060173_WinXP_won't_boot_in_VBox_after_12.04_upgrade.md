---
title: "WinXP won't boot in VBox after 12.04 upgrade"
date: 2012-09-19
forum: Virtualisation
---

### Post by quinne on 2012-09-19
Hello All -- My apologies is this issue has already been addressed in another thread; I did a search but couldn't find anything.

My problem:  I recently ran the 12.04 upgrade via the update manager.  All seemed to go fine, and booted up successfully to the updated OS.  However, when I went to open my previously installed WinXP in VirtualBox, I get the following pop-up error screen:

Failed to open a session for the virtual machine XP_Pro.

Failed to load VMMR0.r0 (VERR_SUPLIB_WRITE_NON_SYS_GROUP).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

This does not bode well, and I have no clue if there is anything to be done or not.  I'm hoping one of you knowledgeable people would know a solution.  Is there anyone that can help?  Thank you!

---

### Post by CharlesA on 2012-09-19
See here:
[https://forums.virtualbox.org/viewtopic.php?f=11&t=43487](https://forums.virtualbox.org/viewtopic.php?f=11&t=43487)

The permissions for /opt for me are as follows:

```
drwxr-xr-x 3 root root 4096 May  1 13:34 /opt

```

---

### Post by afz12 on 2012-09-19
Quinne, hopefully CharlesA' suggestion will work, but if not it may be useful to install Ubuntu 12.04 as a fresh install rather than an upgrade. I have tried upgrades before and none have ever been successful - there has always been one or another item that stops working. However installing from a CD (or DVD) has always worked. Also, XP VM's made in Ubuntu 12.04 seem to run fine even on different OS such as Mint Cinnamon (with the exception of Internet access so far!). I have Ubuntu 12.04 running on this notebook with Virtualbox and 2 XP VMs - both work perfectly fine. I used a fresh install some time ago, rather than an "upgrade". Another advantage for this is that you can change the amount of swap space allocated or set up extra partitions during the install.

---

### Post by quinne on 2012-09-20
Hi folks, thanks for the replies.

CharlesA, I'll read through the thread you linked.  I don't really know what I'm doing when it comes to linux code, so feel a bit like a trained monkey when people say 'open terminal and do blah blah'.  Often it works, but I remain clueless as to why.  I love linux and wish I had time to devote to learn it's inner workings, but life's responsibilities make it otherwiase.

afz12, the 'fresh install' idea occurred to me, but that would mean redoing soooo many things (all my personal app faves need to be reinstalled, back up a ton of stuff -- yes, I know, I should anyway.)   I realize it may come to that, but it's truly a last resort in my mind.    

And please note, it's not VBox that won't boot, it's the WinXP Pro install within VBox that's popping up the error message.  I suppose my next try would be to simply reinstall XP and go from there.  I have some books and music (kindle and itunes, what else?) but those should be redownloadable easily enough....

Thanks for your time, guys!

---

### Post by CharlesA on 2012-09-20
A reinstall of the VM isn't going to fix the problem.

Check the permissions on /opt:

```
ls -ld /opt
```

---

### Post by quinne on 2012-09-21
Reinstall wouldn't fix it?  Hmmmm.... interesting.

Here's the output from the terminal after this monkey typed in what you asked!  (heh...)

me@me-laptop:~$ ls -ld /opt
drwxr-xr-x 3 root root 4096 Sep 20 00:22 /opt

I've got to go to work, but will look for a reply this eve.  Thanks, CharlesA!

---

### Post by CharlesA on 2012-09-21
Check the [log file]("https://blogs.oracle.com/fatbloke/entry/virtualbox_log_files"), it should be in ~/.VirtualBox/VMNAME/Logs

That should give you a more specific error.

---

### Post by quinne on 2012-09-23
Here is the log in the Vbox WinXP file:

00:00:00.341 Log opened 2012-09-18T20:21:44.926901000Z
00:00:00.341 OS Product: Linux
00:00:00.341 OS Release: 3.2.0-30-generic
00:00:00.341 OS Version: #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012
00:00:00.341 DMI Product Name: HP Pavilion dv7 Notebook PC
00:00:00.341 DMI Product Version: 049A210002241220000020000
00:00:00.342 Host RAM: 3700MB RAM, available: 2336MB
00:00:00.342 Executable: /usr/lib/virtualbox/VirtualBox
00:00:00.342 Process ID: 17324
00:00:00.342 Package type: LINUX_64BITS_GENERIC (OSE)
00:00:00.414 Installed Extension Packs:
00:00:00.414   None installed!
00:00:00.416 VRDE: VirtualBox Remote Desktop Extension is not available.
00:00:00.416 pdmR3LoadR0U: pszName="VMMR0.r0" rc=VERR_SUPLIB_WRITE_NON_SYS_GROUP szErr="The group is not a system group and it has write access to '/usr'"
00:00:00.416 VMSetError: /build/buildd/virtualbox-4.1.12-dfsg/src/VBox/VMM/VMMR3/VM.cpp(587) int vmR3CreateU(PUVM, uint32_t, PFNCFGMCONSTRUCTOR, void*); rc=VERR_SUPLIB_WRITE_NON_SYS_GROUP
00:00:00.416 VMSetError: Failed to load VMMR0.r0
00:00:00.416 ERROR [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={1968b7d3-e3bf-4ceb-99e0-cb7c913317bb} aComponent={Console} aText={Failed to load VMMR0.r0 (VERR_SUPLIB_WRITE_NON_SYS_GROUP)}, preserve=false
00:00:00.425 Using XKB for keycode to scan code conversion
00:00:00.483 Power up failed (vrc=VERR_SUPLIB_WRITE_NON_SYS_GROUP, rc=NS_ERROR_FAILURE (0X80004005))

Thanks for your time!

---

### Post by CharlesA on 2012-09-23
Check the permissions of /usr:

```
ls -ld /usr
```

---

