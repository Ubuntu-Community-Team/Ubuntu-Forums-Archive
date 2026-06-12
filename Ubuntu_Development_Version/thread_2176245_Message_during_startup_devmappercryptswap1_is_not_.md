---
title: "Message during startup: /dev/mapper/cryptswap1 is not available or ready yet"
date: 2013-09-23
forum: Ubuntu Development Version
---

### Post by santosh83 on 2013-09-23
In Lubuntu 13.10 beta1 (always updated) I get roughly the following message printed to my console during every startup:

```
The device /dev/mapper/cryptswap1 is not available or ready yet
Press any key to Continue or S to Skip or M to mount manually
```

I just ignore this message and startup proceeds normally (as far as I can tell) and once system is running, [FONT=lucida console]swapon -s[/FONT] indicates that [FONT=lucida console]/dev/mapper/cryptswap1[/FONT] is indeed mounted as swap.

I suppose this is just a beta rough edge that'll be smoothed over before release or is something I should investigate further or file a bug report?

---

### Post by rrnbtter on 2013-09-23
Greetings,
I have taken this to be an actually truthful message. An encrypted partitition doesn't exist to an OS absent the crypt support and keys. Hence until the system is booted the encrypted swap file cannot  be neither seen or accessed. When the system boots and encryption is started the swap is on. Thats normal operation.

---

### Post by santosh83 on 2013-09-23
> **rrnbtter said:**
> Greetings,
I have taken this to be an actually truthful message. An encrypted partitition doesn't exist to an OS absent the crypt support and keys. Hence until the system is booted the encrypted swap file cannot  be neither seen or accessed. When the system boots and encryption is started the swap is on. Thats normal operation.

Err... of course it is truthful.

If this is the case then I wonder why the system tries to mount it before the crypt support becomes available, and why a spurious message about it is printed? Searching on Google it seems I'm far from the only one who's got confused about this and asked for help on forums and even bug reports on Launchpad it seems.

---

### Post by rrnbtter on 2013-09-23
Greetings,
Try this command in a terminal "sudo /sbin/mkswap /dev/sdax", replace sdax with your swap file designation (sda1,sda2,sda3, etc). That is what works for me. You just need to let the system know where the swap file is at boot time. The system knows it is coming because there is an encrypted partition which leads to an encrypted swap for security purposes. However it can't find the swap file that it knows exists until it boots. Solution, let it know where it is.

---

### Post by Sworddragon on 2013-09-24
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1153661](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1153661)

---

### Post by enaction on 2013-10-13
I replaced /dev/mapper/cryptswap1 with /dev/sda5* in /ect/sftab from info I found at [http://www.logilab.org/29155](http://www.logilab.org/29155).  And the error message "The device /dev/mapper/cryptswap1 is not available or ready yet.  Press any key to Continue or S to Skip or M to mount manuallyat boot." now has disappeared for me during the boot sequence.   Using "sudo blkid | grep swap" indicated that my encrypted swap was successfully loaded after boot.  *fdisk - told me which swap partition is being used and it is also shown in /etc/crypttab.

This worked for awhile in terms of getting rid of the message but I now every once-in-a-while get a "pipes broken" message during the boot sequence.  So I've revered back to using "/dev/mapper/cryptswap1" in fstab to see if "/dev/sda5" was causing the error message. Yep, I'm a newbie.

---

