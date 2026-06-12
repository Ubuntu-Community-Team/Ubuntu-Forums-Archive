---
title: "Thunderbird on Ubuntu 20.04 /rant"
date: 2020-10-29
forum: Ubuntu, Linux and OS Chat
---

### Post by LVDave on 2020-10-29
I just installed Ubuntu 20.04, and the Thunderbird email package was installed with the OS. Since I use Thunderbird on both my laptop and my desktop, I copied over from my desktop my Thunderbird profile. When I tried starting Thunderbird, I was informed that I was trying to open the profile with an old version of Thunderbird. I was given a choice of exiting or creating a new profile. Since I have a LOT of email accounts in the profile a new profile was NOT happening. After some screwing around I found that the version INSTALLED BY THE UBUNTU INSTALLER was version 68.10.0. This is the version offered by Synaptic. A check of the version installed on my workstation (KUbuntu 18.04) was 78.4.0. Apparently there was a major change in profile configuration/contents between the TEN versions. 

To fix, I removed the version that came with 20.04 and installed the latest version from the Thunderbird website. All's good now..

Since this is a rant, all I can say is WHAT THE HECK??????????? Somebody is not paying attention...

---

### Post by howefield on 2020-10-29
Not a support request, so moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

### Post by rbmorse on 2020-10-29
That somebody might be you.  

20.04 is distributed as a long term support release (LTS) which provides a stable platform for both the kernel and installed applications.  It does not track routine application updates.

---

### Post by walts48 on 2020-10-30
> **rbmorse said:**
> That somebody might be you.  

20.04 is distributed as a long term support release (LTS) which provides a stable platform for both the kernel and installed applications.  It does not track routine application updates.

Then why do I get regular updates to other applications to my 18.04 LTS like Firefox, and other distros have updated their users to Thunderbird 78.4.0?

[https://lwn.net/Articles/835637/](https://lwn.net/Articles/835637/)

[https://lwn.net/Alerts/](https://lwn.net/Alerts/)

I've already been through the add other ppas and use the snap or flatpack discussion here.

[https://ubuntuforums.org/showthread.php?t=2450612](https://ubuntuforums.org/showthread.php?t=2450612)

What happened to the package maintainer?

---

### Post by walts48 on 2020-10-30
> **LVDave said:**
> I just installed Ubuntu 20.04, and the Thunderbird email package was installed with the OS. Since I use Thunderbird on both my laptop and my desktop, I copied over from my desktop my Thunderbird profile. When I tried starting Thunderbird, I was informed that I was trying to open the profile with an old version of Thunderbird. I was given a choice of exiting or creating a new profile. Since I have a LOT of email accounts in the profile a new profile was NOT happening. After some screwing around I found that the version INSTALLED BY THE UBUNTU INSTALLER was version 68.10.0. This is the version offered by Synaptic. A check of the version installed on my workstation (KUbuntu 18.04) was 78.4.0. Apparently there was a major change in profile configuration/contents between the TEN versions. 

To fix, I removed the version that came with 20.04 and installed the latest version from the Thunderbird website. All's good now..

Since this is a rant, all I can say is WHAT THE HECK??????????? Somebody is not paying attention...

Sorry for your difficulty created by the lack of an updated Thunderbird for Ubuntu.

For anyone else coming across this post you could have started Thunderbird from the command line using the --allow-downgrade switch.

[https://support.mozilla.org/en-US/kb/dedicated-profile-thunderbird-installation#w_what-happens-to-my-profile-if-i-downgrade-to-a-previous-version-of-thunderbird](https://support.mozilla.org/en-US/kb/dedicated-profile-thunderbird-installation#w_what-happens-to-my-profile-if-i-downgrade-to-a-previous-version-of-thunderbird)

---

