---
title: "Latest Ubuntu update (kernel) borked Realtek wireless??"
date: 2012-06-13
forum: System76 Support
---

### Post by CaptSaltyJack on 2012-06-13
My System76 laptop was working great with 12.04 on it, and suddenly the wireless is absolutely unusable. It works about 20% of the time. I was thinking what changed, and I did a software update recently where the kernel was updated (so, whatever the latest version is as of this post - I don't recall offhand).

My laptop has the Realtek 8188CE in it. Anyone have any ideas? Is this a known issue? My laptop has been rendered useless as far as wifi use goes.

Thanks.

---

### Post by sk8 on 2012-06-13
i've been having serious issues with wifi aswell. still trying to figure it out.

---

### Post by ctsdownloads on 2012-06-13
A quick Google query led me to the issue.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557)

Two good things about this.

1) It's being taken seriously and a fix should come down in another kernel release.

2) Rolling back to an older kernel would likely solve your problem instantly.

Because this is a kernel issue, I am sure System76 will (wisely) allow this bug to work itself out since it's easy to roll back to a more stable kernel.

This gives you an idea of which kernel to use and which to dump, using Esc during bootup.


[https://help.ubuntu.com/community/Kernel/Upgrade](https://help.ubuntu.com/community/Kernel/Upgrade)

Hope this helps
 Much like any update, it's always good to have a roll back option. Thankfully, Ubuntu allows for this with its installed Linux kernel(s).

---

### Post by CaptSaltyJack on 2012-06-14
Very helpful, thanks! I did search, not sure why I didn't find that bug.

So I held SHIFT while booting, and booted up the previous kernel (3.2.0-24) which works. Will wait for 3.2.0-26 to surface or whatever version number it will be.

Thanks again.

---

### Post by ctsdownloads on 2012-06-15
> **CaptSaltyJack said:**
> Very helpful, thanks! I did search, not sure why I didn't find that bug.

So I held SHIFT while booting, and booted up the previous kernel (3.2.0-24) which works. Will wait for 3.2.0-26 to surface or whatever version number it will be.

Thanks again.

Awesome, glad you found a way around it. :)

---

