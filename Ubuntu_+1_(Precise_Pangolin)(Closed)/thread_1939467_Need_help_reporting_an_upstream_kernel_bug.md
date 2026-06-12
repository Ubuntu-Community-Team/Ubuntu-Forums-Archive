---
title: "Need help reporting an upstream kernel bug"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tr333 on 2012-03-11
I've got a system running an AMD A8-3850 APU.  I can run it without problem from HDMI, but the VGA port doesn't work.  I can only get VGA working if I run with "nomodeset" on the kernel boot parameters.  I've tested with the latest 3.3-rc7 mainline kernel and it's also failing there (unless I run with "nomodeset"), so I'm guessing it's an upstream kernel bug and not Ubuntu-specific.

Can anyone please advise on how to report this to the upstream Linux kernel?


Launchpad bug report: [http://pad.lv/908659](http://pad.lv/908659)

---

### Post by dcstar on 2012-03-11
> **tr333 said:**
> 
.........
Can anyone please advise on how to report this to the upstream Linux kernel?


[https://wiki.ubuntu.com/Bugs/Upstream/kernel](https://wiki.ubuntu.com/Bugs/Upstream/kernel)

---

### Post by Doug S on 2012-03-11
Hi,
 
Just a week or two ago, I sent a bug upstream to Kernel.org.
I am still hoping the fix will make it into 12.04, but when I looked at 3.3rc7 earlier today, the fix was not included yet.
 
I might be wrong, but I think much of the contents of the link given in the previous post are no longer valid. I don't think they use bugzilla anymore. At least I couldn't find anything current (and now it seems the link doesn't even work). However the step 1 link is still valid, but you will also find those instructions in the source code for 3.3rc7 that I assume you downloaded.
See: linux-3.3-rc7/REPORTING-BUGS and the begining of linux-3.3-rc7/MAINTAINERS
 
References and additional notes:
Please know that I did make mistakes in my upstream escalation, and was told so. (send your e-mail as plain text and do not make any external links (include all info) and figure out some list to C.C. (which I still do not know how to determine the list, it was taken care of for me after my mistake))(Edit: I think it is [EMAIL="linux-kernel@vger.kernel.org"]linux-kernel@vger.kernel.org[/EMAIL] you are supposed to copy)
The [launchpad bu]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811")g for my case (I am not the original poster, but I worked a ton on the issue).
 
Hope this helps.

---

### Post by tr333 on 2012-03-15
Thanks for the info. I'll take a look and see what comes up.

---

