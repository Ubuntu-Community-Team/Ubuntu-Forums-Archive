---
title: "VirtualBox 4.1 causes hang on suspend"
date: 2011-07-21
forum: Virtualisation
---

### Post by Dave_L on 2011-07-21
[Ubuntu 10.04 Netbook]
[System76 Starling model star3]

I installed virtualbox-4.1 (version 4.1.0-73009~Ubuntu~lucid) today using synaptic.  That automatically removed virtualbox-4.0 (4.0.12-72916~Ubuntu~lucid).

Virtualbox seemed to work fine.  But when I attempted to suspend the netbook, either by closing the lid or selecting Suspend from the shutdown menu, the computer hung (with a blue screen); the fan was running at a high speed; the indicator light was solid green (flashing green indicates suspend); I had no way of viewing the processes to see what was going on. I had to do a hard power off.

Reverting virtualbox to 4.0 fixed the suspend-issue.

Maybe it's something to do with the virtualbox kernel modules?

---

### Post by nikolam on 2011-07-22
Just to mention that this happens also in Ubuntu 11.04, both 2.6.39.0 and 2.6.38.8 kernels. Closing the lid (suspend) locks the laptop and only hard reset can bring it back up.
I'd agree it has something to do with VirtualBox kernel module as VBox 4.0.12 module worked fine with both kernels.

Also, there is a ticket at VBox site here:

[http://www.virtualbox.org/ticket/9260](http://www.virtualbox.org/ticket/9260)

Similarly, reverting to v4.0.12 resolved the issue.

---

### Post by lotharmat on 2011-07-26
Ditto for me - reverting back to 4.0.xxx worked a treat!

It was only today when I got the 'lightbulb moment'

Vbox 4.1 was the only think I had installed and suddenly it all clicked!

---

### Post by TechBeastie on 2011-07-31
Sorry for cross-posting (to those of you who notice), but I found the 
following two pages while I was investigating this problem on one of my family's machines, and thought they might be helpful to somebody:

[ This one ]("http://www.virtualbox.org/ticket/9260") is a VirtualBox problem ticket discussion, in which some enterprising soul offers the following workaround:
"Adding the following line in /etc/pm/config.d/unload_modules fixes the problem for me:
```

SUSPEND_MODULES="$SUSPEND_MODULES vboxdrv vboxnetflt vboxnetadp vboxpci

```
"
I haven't tried the fix yet, but it looks right on-target.  

And [these folks]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/814323") just released a patch for this very problem.  I haven't tried it yet either, but when/if I do I'll report back.

---

### Post by orsula on 2011-07-31
Hi All,
Thank you for all the info above. However, despite the fact I am running 4.0.12, I am still seeing all the hangs with suspend/hibernate that were previously reported. I am running 11.04 with kernel 2.6.38-10 on a Latitude D630. 
Everything was working perfectly before the 4.1 version. I actually tried to upgrade to 4.1 and got the error I needed to first uninstall 4.0. So I decided at that time NOT TO UPGRADE (!) and stay with 4.0 to save the trouble. I only upgraded from 4.0.11 to 4.0.12. But as you already guessed, I am experiencing all the bad stuff of 4.1. How do I make sure I am all clean of 4.1? Is there a way to completely uninstall VB but retain my VM's somehow so I can re-install 4.0.12 fresh and pick-up exactly where I left?

Can anyone point to something else I might try?
 
Thank you very much!

---

