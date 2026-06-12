---
title: "VirtualBox 2.2 hangs on guest OS startup"
date: 2009-04-27
forum: Virtualisation
---

### Post by RainKap on 2009-04-27
A week or so back I upgraded VirtualBox from 2.1 to 2.2 on my desktop machine (2 x 2GHz dual core Opteron, running Ubuntu Hardy AMD64). Since then, I've had fairly frequent occurrences of VirtualBox hanging when I try to start the guest OS (Win XP Pro, which I need for my scanner and to run an Access database). When this happens:

- The VirtualBox window and the guest OS window are both greyed out; I can force a quit, but...

- If I leave the VirtualBox window and the guest OS window to stew, I can open other applications (e.g. Firefox to post this), but trying to shut down from the big red button on the panel doesn't work; I *can* open a terminal and use sudo shutdown -h now to switch off.

- If I force a quit from the VirtualBox window and the guest OS window the only way out is to open a full screen console with Ctrl-Alt-F1 and use sudo shutdown -h now to switch off.

The immediately obvious symptom of a failed startup is that if I *don't* get the VirtualBox splash screen after I've tried to start the guest OS it is going to hang; if I *do* get the VirtualBox splash screen after I've tried to start the guest OS it works OK.

If you can point me to which logs I need to look at in /var/log then I can provide more specific details.

Thanks in advance for any help.

Ian

---

### Post by RainKap on 2009-05-11
The problem seems to have gone away after I took the update of VirtualBox 2.2 from Update Manager...

Ian

---

