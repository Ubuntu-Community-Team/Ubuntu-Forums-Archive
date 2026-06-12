---
title: "Ubuntu and Nvidia Graphics Problems"
date: 2010-09-14
forum: Testimonials &amp; Experiences
---

### Post by bsalem on 2010-09-14
A week ago I suddenly lost the high resolution screens from my Gnome desktop. Try as I might I cannot get the X server to restore them. Please see the comment by bsalem added to bug 226983. The system is an Ubuntu 8.10 install, and before you say 'not supported', I had the same failure on Ubuntu 9.10.

From the note I appended to that bug let me point out that the general trouble shooting is as follows.

The high resolution  works in Windows Vista and from Knoppix 5.1.1 Live distro and my problem occured after some event altered the driver or its interaction with the kernel. I have not been able to find out what happened.

This issue is not with the window manager, it is with the X server and its drivers and the kernel.

My real reason to post here, besides the support issue, is to raise a red flag about how issues are being handled WRT Nvidia drivers and how I am on the verge of scrubbing my Ubuntu install and not trying this distro ever again and going to another Linux.

First, I had done technical support for Operating Systems at Sun Microsystems from 1997-2004 and know how bugs are managed and escalated. The problems with Nvidia Video Cards are obviously complex, but IMHO the complexity associated with the drivers and the kernel is an absolute mess and needs to be addressed by Cononical ASAP. This should even include the decision to not support the cards. In the Community Fourms there are at least 2500 issues open relating to Nvidia Drivers and Ubuntu.

Second,There should be a support matrix documented with which packages support which cards. Now I know there are 100 or more different Nvidia configurations, but the confusion about which packages go with which cards or groups of cards needs to be resolved ASAP.

I know how engineers like to say "stupid user" and close bugs, even if the issue is really between current and down-rev releases, just because someone is not using the "latest and greatest" or most alpha, release does not mean that a legacy issue has really been resolved.

Nvidia cards are very common, and to have packages in the repository that break the drivers or kernel or both is going to make people find an alternative distro. I am but days away from that decision and if I make it against Ubuntu, I will not look back, ever.

---

### Post by Perfect Storm on 2010-09-14
Moved to Ubuntu Testimonials & Experiences.

---

### Post by Jazzy_Jeff on 2010-09-14
> **Artificial Intelligence said:**
> Moved to Ubuntu Testimonials & Experiences.

Looks like this is a support thread as well.

---

### Post by realzippy on 2010-09-14
*My real reason to post here, besides the support issue, is to raise a red flag.*
[support]("http://ubuntuforums.org/showthread.php?p=9846187#post9846187")
red flag after support...


...what does red flag mean?

---

### Post by Tamlynmac on 2010-09-15
> realzippy

Might I suggest you pick one. Either raise a red flag or ask for support. Since the T&E is not a support [section]("http://ubuntuforums.org/showthread.php?t=1343965") of the forums. You may wish to post a separate thread requesting support and place it in the appropriate help section, without a red flag comment.

Just a suggestion.
Good Luck

---

### Post by bsalem on 2010-09-15
Thank You, I did just that and I got a resolution, but I noticed that
 'sudo apt-get install linux-headers$(uname -r)'

installed what was evidently the wrong version of the Nvidia Driver. It did detect that it needed to install
a driver but installed the wrong driver:

 * Running DKMS auto installation service for kernel 2.6.27-17-server        
 *  nvidia (173.14.12)...     nvidia (173.14.12): Installing module.

After fixing the Xserver from the recovery boot, it had no change.

From the enable drivers GUI I chose nvidia version 180, rebooted,  and when I came back up
I had the high resolution screens.

Xorg.0.log says:

(--) PCI:*(0@0:13:0) nVidia Corporation GeForce 6150SE nForce 430 rev 162, Mem @
 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x??????
??/131072

(II) NVIDIA GLX Module  180.11  Wed Nov 26 11:17:21 PST 2008
(II) Loading extension GLX

(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.11  Wed Nov 26 10:59:18 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs

There is still some oddness about what it did, but it did work, that is I got my screens back.

If linux-modules gets confused about which driver works with which card, I'd still argue that there is a
support problem. Additionally working to find a match on Launchpad with over 2500 issues open is
futile and a support issue. Anyway, I am sharing this with you as a "red flag" and am not going to file
a bug because of the huge effort required to document it amid all the confusion on Launchpad. I
would still suggest that at least internally there ought to be a support matrix, that is, a list of which
modules and drivers work with which cards and additionally to fix the software and configuration
files so that they provide the correct drivers to the correct card for the given kernel. Judging by the mess
on LaunchPad it seems that people are getting the wrong combinations and that is creating more
work for everybody. I came within a hair of dumping Ubuntu because of this. I was a few minutes away
from scrubbing my disk and installing another distro because I knew that both Windows Vista and
Knoppix 5.1.1 Live Distro had correctly configured my card.

If you want all the debugging info on my system remind me of the name of the bug-report script and I
will run it and send you the gzipped output.

---

### Post by Tamlynmac on 2010-09-16
> bsalem
Thank You, I did just that and I got a resolution

It's amazing how helpful and supportive the forums free help sections  are. I believe it's one of the true examples of the community. Members  helping each other for free and expecting nothing in return (except  maybe a thank you). It's a true reflection of the spirit of the community  and the forums.

Good Luck

---

