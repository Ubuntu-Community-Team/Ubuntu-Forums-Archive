---
title: "Ubuntu keeps loading the 1.6.0 vboxdrv kernel module, although I downgraded to 1.5.6."
date: 2008-07-07
forum: Virtualisation
---

### Post by plamen_todoroff on 2008-07-07
I installed Virtualbox 1.6.0 Non-OSE from the Sun's site a month ago, everything was ok except that I couldn't get my USB mouse working. After a month of searching for a solution I decided to try the OSE version from the Ubuntu repos (version 1.5.6).

I uninstalled 1.6.0 from the Synaptic package manager, "completely uninstall" option I used. And then installed the OSE 1.5.6 from the repos.

And now when I try to start a virtual machine I get a message about driver mismatch and the virtual machine won't start.

*modinfo vboxdrv* says it is version 1.6.0. I ran *locate vboxdrv* and a file called *vboxdrv.ko* was laying all around in different directories (microsoft's style), and it's date of modification was the one I installed 1.6.0 in.

What's happening? Shouldn't the complete uninstall of 1.6.0 got rid of everything 1.6.0-connected?

How do I clean everything left from 1.6.0 and load vboxdrv kernel module version 1.5.6?

Please somebody help, I'm really stuck.

I'll provide all the info you need, just say what you need, for at least to clean my system from everything virtualbox connected.

Thanks.

---

### Post by plamen_todoroff on 2008-07-10
Anybody?

I'm very frustrated about the state of my Ubuntu right now, it feels "dirty" and the "windows-alike" feeling isn't going away.

I just want my system cleaned from everything virtualbox connected, how do I do that?

And, in what way is dkms connected to virtualbox? I see that the vboxdrv.ko is located in /lib/modules/2.6.24-19-generic/updates/dkms. Is it just enough to delete this folder to get rid of this module? Should I uninstall dkms too? Is it dkms's fault that the complete removal of virtualbox didn't remove completely all of virtualbox's components.

Ubuntu was such a nice expirience before all this happened. Help me clean my system, please.

---

### Post by plamen_todoroff on 2008-07-18
Bump

---

### Post by HotShotDJ on 2008-07-19
> **plamen_todoroff said:**
> I installed Virtualbox 1.6.0 Non-OSE from the Sun's site a month ago, everything was ok except that I couldn't get my USB mouse working. After a month of searching for a solution I decided to try the OSE version from the Ubuntu repos (version 1.5.6).Installing the OSE version will not fix your USB problems.  The OSE version does NOT support USB at all.  The best way to completely remove software is to use the command-line... for example:```
sudo apt-get autoremove virtualbox --purge
```This gets rid of everything that got installed, including dependencies that are no longer needed. You can manually remove the incorrect module (just the module, not the directory).  Be sure, however, to install the virtualbox-ose-modules-generic (or whichever one is appropriate for your kernel... run "uname -a" in a terminal if you don't know which one.)

---

