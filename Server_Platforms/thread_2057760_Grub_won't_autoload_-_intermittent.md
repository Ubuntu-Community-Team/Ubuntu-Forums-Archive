---
title: "Grub won't autoload - intermittent"
date: 2012-09-14
forum: Server Platforms
---

### Post by toshko3 on 2012-09-14
Hi :)
I have installed two or three ubunut-server 12.04 64bit and 32bit until now. There are problems with the autoloading of GRUB. Sometimes it doesn't autoload, just stays at the menu screen. You have to press Enter and it's all OK.
I am installing a router now, which will be restarted from the outlet. Whenever I restart it from the power it doesn't want to autoload.
Is this a known bug or what?

---

### Post by darkod on 2012-09-14
Do you have a monitor connected, does it give some message?

---

### Post by toshko3 on 2012-09-14
Yes, it sits at the menu with kernels and waits for you to press Enter.

---

### Post by darkod on 2012-09-14
Nothing else? No message, no count down for booting the default selection?

---

### Post by toshko3 on 2012-09-14
By default it doesn't count down (visibly). Now, neither.

---

### Post by toshko3 on 2012-09-14
Now I set the "GRUB_HIDDEN_TIMEOUT_QUIET " option to false so the timer can show.
The result:
- when I do a manual reboot - the timer shows and the countdown works, the system loads automaticaly
- when I do a power cutout (physically from the outlet) - the timer doesn't show at all and the system doesn't boot automatically, you have to press Enter and then it boots.
:confused:

---

### Post by darkod on 2012-09-14
That would have been my next question. So, it happens only in a power cut.

Have you looked into BIOS to find the option what to do after power cut? You should use something like Always On. Not sure if it makes a difference or not.

Also, not sure if this is a bug or it happens because the file system was never closed in a clean way.

---

### Post by toshko3 on 2012-09-14
@darkod Thanks for helping out!
The problem seems to be not a bug, but by design (stupid design). When a machine is not cleanly shutdown a "recordfail" state sits in and tells GRUB that it was not shutdown properly. It is by design then to cancel the autoload timer and wait for user input (safety reasons I suppose).
Well, it's OK, but NOT for servers.
The quick workaround is this:
in /etc/grub.d/00_header line 242 change the timeout from -1 to any positive integer

as stated in this bug:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/669481](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/669481)

As they told on 09.12.12, the fix should be released and backported to 12.04 shortly.
:popcorn:

---

