---
title: "Mapping Ubuntu kernel version to upstream"
date: 2014-08-19
forum: Ubuntu Development Version
---

### Post by rikki2 on 2014-08-19
I'm trying to reverse bisect commit the kernel, following the instructions [here]("https://wiki.ubuntu.com/Kernel/KernelBisection#How_do_I_bisect_the_upstream_kernel.3F"), but I can't find a way to map the Ubuntu kernel versions to upstream. The versions I'm looking for are v3.14.17-utopic and v3.15-rc1-trusty.

I've tried:

[LIST]
[*][The Ubuntu to Mainline kernel map site]("http://people.canonical.com/~kernel/info/kernel-version-map.html") which doesn't list either of the above versions
[*]cat /proc/version
[*]Google
[/LIST]

Am I doing something wrong or is there another resource I'm not aware of to allow me to map to upstream?

---

### Post by grahammechanical on 2014-08-19
I am not speaking with authority but I do not think that there was a Ubuntu kernel based on Linux kernel 3.14 series. I been reviewing the kernel team minutes.

> 
[LIST]
[*]The 3.13.0-24.46 Ubuntu kernel in the Trusty archive is currently based on the v3.13.9 upstream stable kernel. The kernel is currently frozen in preparation for our final 14.04 release this Thurs Apr 17. kernel. We do not anticipate any uploads between now and Thurs. All patches from here on out are subject to our Ubuntu SRU policy.
[/LIST]


[https://wiki.ubuntu.com/KernelTeam/Meeting/2014-04-15](https://wiki.ubuntu.com/KernelTeam/Meeting/2014-04-15)

> 
[LIST]
[*]Our Trusty kernel has been pocket copied to seed Utopic. We have opened the ubuntu-utopic kernel tree. The master-next branch is currentlytracking the v3.15-rc3 kernel. We likely won't upload a v3.15 based kernel until a few more -rc releases come out.
[/LIST]


[https://wiki.ubuntu.com/KernelTeam/Meeting/2014-04-29](https://wiki.ubuntu.com/KernelTeam/Meeting/2014-04-29)

> 
[LIST]
[*]We are preparing to upload our first v3.15 based kernel to the Utopic archive. We're awaiting some DKMS package fixes before doing so. We'vecurrently rebased to the latest v3.15-rc5 upstream kernel. Additionally, at a minimum, we will converge on the v3.16 kernel for the Utopic 14.10 release.
[/LIST]


It seems to me that Ubuntu kernels went from Linux 3.13 series to Linux 3.15 series and by-passed and Linux 3.14 series kernels. Also the kernel series change in Utopic was based upon Linux kernel 3.15-rc5 not rc1.

> [COLOR=#33290A][FONT=oxygen]There are usually several "longterm maintenance" kernel releases provided for the purposes of backporting bugfixes for older kernel trees. Only important bugfixes are applied to such kernels and they don't usually see very frequent releases, especially for older trees.[/FONT][/COLOR] 

[https://www.kernel.org/category/releases.html](https://www.kernel.org/category/releases.html)

The Linux kernel 3.14 series is a LongTerm Maintenance kernel. I do not think that is used as basis for kernels in Ubuntu. The minutes of the kernel team meetings support  the accuracy of the Ubuntu to Mainline chart.

Regards.
[https://wiki.ubuntu.com/KernelTeam/Meeting/2014-05-13](https://wiki.ubuntu.com/KernelTeam/Meeting/2014-05-13)

---

### Post by rikki2 on 2014-08-20
Thanks for your reply Graham.

This confuses me more though, since the [list of mainline kernel builds]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") (from which I have been told to work) contains v3.14.x upstream kernels, the most recent update to which was around 6 days ago. It seems to me that this codebase is still being worked on.

All I am trying to ascertain is what commit fixed [this bug ]("https://bugs.launchpad.net/bugs/1354410")between the kernel versions above. If I understand you correctly, then I should ignore the v.3.14.x series completely and use the latest v3.13.x and the oldest v3.15.x kernel? I.e. the ones that have maps defined in the Ubuntu to Mainline list? These would be 3.13.0-29.52 and 3.15.0-1.5 respectively.

Wouldn't there be a substantial number of code changes between v3.13.x and v3.15.x which would make identifying the fix commit more difficult?

Thanks

---

