---
title: "Ubuntu hangs -16.04 BETA 2 -acer aspire v15 v3-575T-7008"
date: 2016-04-04
forum: Ubuntu Development Version
---

### Post by vatsaldin on 2016-04-04
Hi,

After 10-15 minutes of inactivity Ubuntu freezes and hangs and then it needs hard shut down or reboot.


Posted here since in "general" section it is not allowing to post new thread.

Thanks in advance.

---

### Post by howefield on 2016-04-04
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by izznogooood on 2016-04-04
[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]Which kernel are you running?

"sudo uname -r"[/COLOR][/FONT]

---

### Post by vatsaldin on 2016-04-05
> **izznogooood said:**
> [FONT=Ubuntu][COLOR=#111111]Which kernel are you running?

"sudo uname -r"[/COLOR][/FONT]


Kernel is as below:-

4.4.0-15-generic

---

### Post by shivam-19mishra on 2016-04-05
I am having same problem with HP 15r250tu notebook. 

This problem was with wily too, it hasn't been resolved since

---

### Post by boozzz on 2016-05-03
I have the exact same issue using ubuntu 16.04 with kernel 4.4.0-21-generic and kodi 16.1 on x86 64-bit. Did you find any workaround?

---

### Post by shivam-19mishra on 2016-05-03
Yeah, I found a workaround, and it's been working perfectly fine since then. I'm not sure if it will work for your system or not. 

Go to Terminal, type gedit /etc/default/grub

In the grub file, find the line GRUB_CMDLINE_LINUX_DEFAULT, to it add : "intel_idle.max_cstate=1" (keep this inside the quotes already present for this line)

Save it and close. In the terminal now : sudo update-grub.

Reboot your system for the changes to take effect. 

Now, remember this is just a workaround until the bug is resolved. The bug is reported here: [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051). 
So, keep checking for any permanent solution; when a solution is out, remove the cstate as it consumes more power.

---

### Post by deadflowr on 2016-05-03
Out of the frying pan and into the fire.
Development of 16.04 is done
Open a thread in non-development support areas for help with 16.04
Thread Closed

---

