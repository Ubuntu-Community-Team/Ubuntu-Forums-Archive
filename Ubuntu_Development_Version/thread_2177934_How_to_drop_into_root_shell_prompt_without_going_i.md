---
title: "How to drop into root shell prompt without going into recovery?"
date: 2013-10-01
forum: Ubuntu Development Version
---

### Post by HuaiDan on 2013-10-01
Hello,
I completely hosed my system by installing nvidia-current on 13.10.
I need to remove it so my system can boot properly. 
sudo apt-get remove nvidia_current would do nicely.
However, 'm at a los as to how to do this, because the boot freezes on recovery, 6 seconds in, with the message
 "nvidia: module license 'NVIDIA" taints kernel."

I need to remove nvidia so my system can boot, but my system can't boot until I remove nvidia.

What Ubuntu sorely needs (if it has, forgive me, I haven't found it) is a failsafe way to boot into shell should the need arise.

---

### Post by su:bhatta on 2013-10-01
well I am no expert here( but this has helped me twice), but have you tried hitting Ctrl+Alt+F1 once the boot freezes? 

Try it and see if it give you tty1 or if Ctrl+Alt+F2 gives you tty2...(these will be text based terminals)
Then you can login with your usual user name & password and try using 
```

sudo apt-get remove nvidia-current
```

I maybe wrong but it is not nvidia_current.

Read up before hand how to reinstall open source drivers, just in case that is not reverted back to.

Also, when the computer boots up there should be an 'Advanced' menu in grub that lets you boot to a failsafe option or maybe that is the recovery mode, i am confused now.

---

### Post by coffeecat on 2013-10-01
Since this is about Ubuntu 13.10, *thread moved to **Ubuntu +1**.*

@HuaiDan, since the boot process freezes when you boot into the current kernel, have you tried booting into a previous kernel, either in normal or recovery mode?

---

### Post by HuaiDan on 2013-10-01
Since I did a complete wipe/install in hopes of fixing an earlier problem, there are no other kernels to boot into.
Which is what I just did, again. I'll try installing a different nvidia, and see if the ctl-alt f2 helps if it freezes, but I think II tried that already.

---

### Post by coffeecat on 2013-10-01
If it's the boot process that is freezing, ctr-alt-F* into a virtual console is extremely unlikely to work. 

A bit late now, but another thing that is worth considering when confronted by a situation like this is to chroot into the problem system from a live CD/USB, or from a Linux OS on another partition if you are multi-booting.

---

### Post by HuaiDan on 2013-10-01
Mods, please close this thread. Dropping to a root shell won't fix the bigger problem I'm having. Opening a new thread.

---

### Post by coffeecat on 2013-10-02
Closed at request of OP.

@HuaiDan, if you would like a thread closed it's best to use the Report Post button to send a message to the staff area. It's fine to use the report button for this purpose. I only saw your request because I was subscribed to the thread. Good luck with the new thread.

---

