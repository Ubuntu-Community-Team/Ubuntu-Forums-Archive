---
title: "no authentication agent was found when installing VBox extension pack"
date: 2011-09-03
forum: Virtualisation
---

### Post by CharlesA on 2011-09-03
Hi,

I'm trying to install the virtualbox extension pack on Lucid x64 and seems to have run into a hitch - I get the error:

```
charles@Atlantis:~$ vboxmanage extpack install Oracle_VM_VirtualBox_Extension_Pack-4.1.2-73507.vbox-extpack 
0%...
Progress state: NS_ERROR_FAILURE
VBoxManage: error: Failed to install "/home/charles/Oracle_VM_VirtualBox_Extension_Pack-4.1.2-73507.vbox-extpack": The installer failed with exit code 127: Error executing command as another user: No authentication agent was found.

```

I've compared this machine witht he machine that works (same version of Ubuntu) and I can't find anything that might be causing the problem.

Here's a diff of the installed packages between the two (< is the working machine, > is the non working one):

```
< ii  hptsvr-https                    1.4-11                                          HighPoint Web RAID Management Service
< ii  lib32gcc1                       1:4.4.3-4ubuntu5                                GCC support library (32 bit Version)
< ii  libc6-i386                      2.11.1-0ubuntu7.8                               GNU C Library: 32-bit shared libraries for A
> ii  libpolkit-dbus2                 0.9-4ubuntu2                                    library for accessing PolicyKit via D-Bus
> ii  libpolkit-grant2                0.9-4ubuntu2                                    library for obtaining privileges via PolicyK
> ii  libpolkit2                      0.9-4ubuntu2                                    library for accessing PolicyKit
< ii  libuptimed0                     1:0.3.16-3                                      Library for uptimed
< ii  linux-image-2.6.32-32-server    2.6.32-32.62                                    Linux kernel image for version 2.6.32 on x86
< ii  sdparm                          1.02-1                                          Output and modify SCSI device parameters
< ii  ssh                             1:5.3p1-3ubuntu7                                secure shell client and server (metapackage)
< ii  uptimed                         1:0.3.16-3                                      Utility to track your highest uptimes
```

Could libpolkit be causing the problem? When I googled the error, I got the most hits from policy kit.

Note: When I installed the extension pack on the working machine (as a normal user) I got a kdesudo prompt that asked for my password, the non working machine never got that far, apparently, and kdesudo is installed.

---

### Post by b0b138 on 2011-09-03
I'm just guessing and throwing out things...

When I installed it, I just double clicked and it ran, instead of cli.

The extpack is 4.1.2-73507.  Does that match the version of vbox installed? I have no idea if it would matter.

Try rebooting to clear out the cobwebs?

---

### Post by CharlesA on 2011-09-03
> **b0b138 said:**
> I'm just guessing and throwing out things...

When I installed it, I just double clicked and it ran, instead of cli.

The extpack is 4.1.2-73507.  Does that match the version of vbox installed? I have no idea if it would matter.

Try rebooting to clear out the cobwebs?

That's the same version of VBox I am running. Guessing you are running a DE since you mentioned double clicking? Were you prompted for your sudo password?

Rebooted to no effect. I'm going to wipe the machine again and try one more time.

---

### Post by b0b138 on 2011-09-04
Yes, standard gnome on lucid.  Maybe try downloading the extpack again? Probably too late for that now ;)

---

### Post by CharlesA on 2011-09-04
> **b0b138 said:**
> Yes, standard gnome on lucid.  Maybe try downloading the extpack again? Probably too late for that now ;)
Done that a few times- it runs fine if I run it with sudo, but the extpack doesn't show up for the user that it needs to run as.

I'm not sure if it's a bug in that extpack or what.

EDIT: Hmm, I shutdown one of the machines that was having the problem and when I started it back up this morning, the extension pack was installed and seen from both root and the user.. Testing it on another box to see what happens.

EDIT2: No go after a reboot. When I tested it with just installing virtualbox, it prompted for the password fine, after installing all the junk, it just errored out again. Guess I know where to look now.

EDIT3: After installing the extpack with sudo and rebooting, it's now showing up for the user. Guess I'll mark this one as solved.

Just for the record - uninstalling behaves the same way, just in case someone else runs into this problem.
[COLOR="Blue"]
Solution in my case: Stop vboxweb-server and wait for these two processes to end (check using ps aux | grep VBox):
```
/usr/lib/virtualbox/VBoxXPCOMIPCD
/usr/lib/virtualbox/VBoxSVC --auto-shutdown
```

After those were stopped I was prompted with the kdesudo box and everything installed fine.[/COLOR]

---

