---
title: "Boot failed every two times reboot"
date: 2012-08-02
forum: Server Platforms
---

### Post by yhjhoo on 2012-08-02
I just install the ubuntu server 12.04 64 bit to IBM system x server. and I found a very strange issue.

When I try to reboot, the first time is always failed. I will press ctrl+alt+del to reboot again and it will successfully boot up.


So here is my question, is it able to set it the auto retry if the boot up failed!

---

### Post by Grenage on 2012-08-02
Are your boot drives particularly slow at spinning up?  Can you add a delay one way or another in the BIOS?

---

### Post by yhjhoo on 2012-08-02
> **Grenage said:**
> Are your boot drives particularly slow at spinning up?  Can you add a delay one way or another in the BIOS?



I think this should be done in OS level. For example, windows server will try to reboot if it's failed

---

### Post by WSmart on 2012-08-03
Greetings!

First reboot, so every time you reboot from either OS?   You said winblows so I assume your using that as well as Linux on this machine?   

I wonder if your talking about first boot of the day which is a relatively common issue.   Not sure if English is your first language so I wonder if that's what you mean.

If it's crashing on an actual reboot as you say, is it hanging before, during or after the post screen at start up?

The operating system can't do anything if it's not loaded.   Maybe you could try resetting the bios?

More details would help.  Thanks.

---

### Post by 2F4U on 2012-08-03
Did you ever try to find the reason why it fails to boot, for example, by looking into the log files?

---

### Post by yhjhoo on 2012-08-04
> **2F4U said:**
> Did you ever try to find the reason why it fails to boot, for example, by looking into the log files?

Thanks for your reply, which log file shall I looking for?

After I do a upgrade, it become much better. Failed 1 time after 10 times reboot.

---

