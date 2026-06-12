---
title: "What distro uses the latest kernel 2.6.34-xx?"
date: 2010-05-24
forum: The Cafe
---

### Post by shuttleworthwannabe on 2010-05-24
I am using x200 Thinkpad and the current kernel of 2.6.32 has a acpi bug that does not allow the fan to throttle down so it keeps blowing forever. Apparently the 2.6.34 lernel has fix for this. Could anyone suggest a distro that is currently using this new kernel--the distro should be at least a beta or RC release, so I could use it in peace.

Thanks
S

---

### Post by Frogs Hair on 2010-05-24
Red Hat Enterprise Linux 6  will have it when released .

---

### Post by ssam on 2010-05-24
[http://distrowatch.com/](http://distrowatch.com/) will tell which versions a distro has.
fedora 13 may be a good option.

another option would to use ubuntu will a mainline kernel. you can download them from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by cariboo on 2010-05-24
Maverick Meerkat:

```
uname -a
Linux maverick 2.6.34-3-generic #10-Ubuntu SMP Wed May 19 03:08:32 UTC 2010 x86_64 GNU/Linux
```

---

### Post by Simian Man on 2010-05-24
> **ssam said:**
> 
fedora 13 may be a good option.

Yep it will be released tomorrow, so good timing :).

> **cariboo907 said:**
> Maverick Meerkat:

```
uname -a
Linux maverick 2.6.34-3-generic #10-Ubuntu SMP Wed May 19 03:08:32 UTC 2010 x86_64 GNU/Linux
```

He said beta software at least.

---

### Post by Twitch6000 on 2010-05-24
^he said beta or rc no pre pre alpha... lol.

Anyways slackware has it in its unstable tree.(or whatever they call it)

I am sure arch has it aswell.

If anything just compile the kernal yourself. Or find a repo that has it compiled. just make sure the repo is trusted.

---

### Post by cascade9 on 2010-05-24
> **ssam said:**
> [http://distrowatch.com/](http://distrowatch.com/) will tell which versions a distro has.
fedora 13 may be a good option.

another option would to use ubuntu will a mainline kernel. you can download them from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Dont rust distrowatch on what kernel (or other components) a distro has. Normally, it is right, but sometimes its wrong (distrowatch has 'linux 2.6.32' for sidux when I know its at 2.6.34 now).

---

### Post by 98cwitr on 2010-05-24
from distrowatch

• Ark Linux 
• Fedora: rawhide 
• Frugalware Linux: current 
• Gentoo Linux: unstable 
• Linux From Scratch: unstable 
• openSUSE: factory 
• Ubuntu: snapshot 
• Vine Linux: VineSeed

---

### Post by castrojo on 2010-05-24
> **shuttleworthwannabe said:**
> I am using x200 Thinkpad and the current kernel of 2.6.32 has a acpi bug that does not allow the fan to throttle down so it keeps blowing forever. Apparently the 2.6.34 lernel has fix for this. Could anyone suggest a distro that is currently using this new kernel--the distro should be at least a beta or RC release, so I could use it in peace.

Do you have a link to this bug report or something and/or the changelog in 2.6.34 that refers to this? I've been struggling with this too. :(

2.6.34 is available here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

I'll give that a shot and report back.

---

### Post by shuttleworthwannabe on 2010-05-24
> **whiprush said:**
> Do you have a link to this bug report or something and/or the changelog in 2.6.34 that refers to this? I've been struggling with this too. :(

2.6.34 is available here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/")

I'll give that a shot and report back.

check [here]("http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2010-03/34348/%28Bug-380303%29-Re-thinkpad-acpi-X200-Thinkpad-fan-fails-to-spin-down-.html")

---

### Post by shuttleworthwannabe on 2010-05-25
I installed the new kernel on Lucid from the link you guys provided here--I must say I do not see a difference in the fan noise and fan speed--still blowing. System seems a bit faster though. I will wait for *_[U][I]**whiprush ***_[/U][/I]to feedback.

---

### Post by doorknob60 on 2010-05-25
Arch (with testing repo enabled, very easy to do). I'm using that and it's very very stable, no problems. I'm sure it will hit [core] soon too (I'm guessing within a couple weeks).

---

### Post by andrew.46 on 2010-05-25
Hi Twitch,

> **Twitch6000 said:**
> Anyways slackware has it in its unstable tree.(or whatever they call it)

Slackware -current has just become 13.1 so features the 2.6.33.4 Linux kernel....

Andrew

---

### Post by handy on 2010-05-25
On Arch64, I used the kernel .34-git since the first version up until very recently, it never gave me any problems at all.

---

### Post by snowpine on 2010-05-25
You can use .34 in any distro (including Ubuntu), no need to switch.

---

### Post by castrojo on 2010-05-25
> **shuttleworthwannabe said:**
> I installed the new kernel on Lucid from the link you guys provided here--I must say I do not see a difference in the fan noise and fan speed--still blowing. System seems a bit faster though. I will wait for *_[U][I]**whiprush ***_[/U][/I]to feedback.

No change in fan speed here either.

---

### Post by handy on 2010-05-25
For Ubuntu:-

1. Go to:

**[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)**

pick the version of the kernel you want to use.

2. Download and execute the following (in this order, switch to 64 if need be)
- linux-headers...all.deb
- linux-headers..generic..i386.deb
- linux-image....i386.deb

3. Restart

---

### Post by shuttleworthwannabe on 2010-05-25
well, then I will have to just live with the fan noise for another kernel release or the bug gets squashed sooner--the status of bug has not escalated though. Does not look good either way.

---

