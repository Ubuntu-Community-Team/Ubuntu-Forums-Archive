---
title: "Ubuntu 18.04.2 is not released yet But My version is Showing as 18.04.2"
date: 2019-02-14
forum: Ubuntu, Linux and OS Chat
---

### Post by sparks79 on 2019-02-14
Like Many Others I am Anxiously Waiting for 18.04.2.
And as of right now 3.30am 15/02/18 Australian Time, it is still not showing in Ubuntu's d/l directory ( only 18.04.1 ).
So last night I did a Clean install of 18.04.1 and let it do it's Initial Update.
I left that running and went to bed.
Now this morning ( up early, middle of the night ), the update has finished.
When I check in Settings About, it Shows it as 18.04.2.?????????????????.
So in the Absence of 18.04.2 not yet available to d/l from Ubuntu, I have a Question.
Is it Possible to make an ISO of The Currently Installed Version, so that one could then Create a Bootable Installable Version of 18.04.2.

---

### Post by oldfred on 2019-02-14
Why?

And if your 18.04.1 is now showing 18.04.2 that is normal, but you still have the original 18.04 kernel.
If you install 18.04.2 you get a newer kernel which may  be required for newer hardware, so that is why the enablement stacks are released. If your system works fine with original kernel no need to use newer install. If you install the enablement stack you then must update regular for each new enablement stack until final version released.
[URL="https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack"]
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)
[/URL]> The purpose of the HWE kernels has always intended to  be used as a mechanism to deliver support for newer platforms and  hardware components requiring functionality provided in a newer kernel.   This has allowed Ubuntu to support customers/users with newer hardware  but still under the umbrella of an LTS release.  Moving to a rolling HWE  stack model has no impact on delivering this newer hardware support to  users in an LTS. 

 [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

