---
title: "Ubuntu Weekly Newsletter Issue 592"
date: 2019-08-19
forum: Weekly Newsletter
---

### Post by Bashing-om on 2019-08-19
[IMG]https://fridge.ubuntu.com/wp-content/uploads/2011/07/newspaper-icon4.jpg[/IMG]

Welcome to the Ubuntu Weekly Newsletter, Issue 592 for the week of August 11 - 17, 2019. The wiki page of this issue is available [here]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue592").

**[SIZE="5"]In this Issue[/SIZE]**

[LIST]
[*]Ubuntu Stats
[*]Hot in Support
[*]LoCo Events
[*]Mir 1.4.0 Release
[*]APT Patterns
[*]Other Community News
[*]Canonical News
[*]In the Blogosphere
[*]Featured Audio and Video
[*]Meeting Reports
[*]Upcoming Meetings and Events
[*]Updates and Security for 16.04, 18.04, and 19.04
[*]And much more!
[/LIST]

**[SIZE="5"]Ubuntu Stats[/SIZE]**

***[SIZE="4"]Bug Stats[/SIZE]***

[LIST]
[*]Open: 135357 (+23)
[*]Critical: 379 (+1)
[*]Unconfirmed: 66584 (+108)
[/LIST]

As always, the Bug Squad needs more help. If you want to get started, please see: [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

***[SIZE="4"]Translations[/SIZE]***

[LIST]
[*]Ukrainian: 87.56% (33979/2676)
[*]German: 85.93% (38441/8)
[*]Spanish: 85.36% (39986/2865)
[*]French: 80.73% (52660/6179)
[*]Bosnian: 79.91% (54876/155)
[/LIST]

**[SIZE="5"]Hot in Support[/SIZE]**

***[SIZE="4"]Ask Ubuntu Top 5 Questions[/SIZE]***

[LIST]
[*]Is there any way to stop a user from creating executables and running them? - [https://askubuntu.com/questions/1165175/is-there-any-way-to-stop-a-user-from-creating-executables-and-running-them](https://askubuntu.com/questions/1165175/is-there-any-way-to-stop-a-user-from-creating-executables-and-running-them)
[*]Installing Windows to flash UEFI/ BIOS, then reinstalling Ubuntu - [https://askubuntu.com/questions/1165520/installing-windows-to-flash-uefi-bios-then-reinstalling-ubuntu](https://askubuntu.com/questions/1165520/installing-windows-to-flash-uefi-bios-then-reinstalling-ubuntu)
[*]Why is Python 2.7 still the default Python version in Ubuntu? - [https://askubuntu.com/questions/1165360/why-is-python-2-7-still-the-default-python-version-in-ubuntu](https://askubuntu.com/questions/1165360/why-is-python-2-7-still-the-default-python-version-in-ubuntu)
[*]Is there a command to install basic applications on Ubuntu 16.04? - [https://askubuntu.com/questions/1165171/is-there-a-command-to-install-basic-applications-on-ubuntu-16-04](https://askubuntu.com/questions/1165171/is-there-a-command-to-install-basic-applications-on-ubuntu-16-04)
[*]Swap (and hibernation) on SSD in 2019? - [https://askubuntu.com/questions/1165507/swap-and-hibernation-on-ssd-in-2019](https://askubuntu.com/questions/1165507/swap-and-hibernation-on-ssd-in-2019)
[/LIST]

Ask (and answer!) questions at: [https://askubuntu.com/](https://askubuntu.com/)

***[SIZE="4"]Ubuntu Forums Top 5 Threads[/SIZE]***

[LIST]
[*]I am compiling a new coin for fun - [https://ubuntuforums.org/showthread.php?t=2424809](https://ubuntuforums.org/showthread.php?t=2424809)
[*]Ubuntu 18.04 (and also Kubuntu 19.04) won't boot/install from USB - [https://ubuntuforums.org/showthread.php?t=2424658](https://ubuntuforums.org/showthread.php?t=2424658)
[*]Ubuntu 18.04 no longer booting - [https://ubuntuforums.org/showthread.php?t=2424778](https://ubuntuforums.org/showthread.php?t=2424778)
[*]NFS copy performance question - [https://ubuntuforums.org/showthread.php?t=2424846](https://ubuntuforums.org/showthread.php?t=2424846)
[*]Backup Issues and Restoration Attempts - [https://ubuntuforums.org/showthread.php?t=2424669](https://ubuntuforums.org/showthread.php?t=2424669)
[/LIST]

Find more support at: [https://ubuntuforums.org/](https://ubuntuforums.org/)

**[SIZE="5"]LoCo Events[/SIZE]**

The following LoCo team events are currently scheduled in the next two weeks:
[LIST]
[*]UbuConLa 2019, Ubuntu Chile: [http://loco.ubuntu.com/events/ubuntu-cl/3855-ubuconla-2019/](http://loco.ubuntu.com/events/ubuntu-cl/3855-ubuconla-2019/)
[*]Tempe Ubuntu Hour, Arizona LoCo Team: [http://loco.ubuntu.com/events/ubuntu-arizona/3879-tempe-ubuntu-hour/](http://loco.ubuntu.com/events/ubuntu-arizona/3879-tempe-ubuntu-hour/)
[*]Encontro Ubuntu-pt @ Sintra, Ubuntu Portugal: [http://loco.ubuntu.com/events/ubuntu-pt/3935-encontro-ubuntu-pt-sintra/](http://loco.ubuntu.com/events/ubuntu-pt/3935-encontro-ubuntu-pt-sintra/)
[*]Introduction to Linux, Arizona LoCo Team: [http://loco.ubuntu.com/events/ubuntu-arizona/3933-introduction-to-linux/](http://loco.ubuntu.com/events/ubuntu-arizona/3933-introduction-to-linux/)
[/LIST]

Looking beyond the next two weeks? Visit the LoCo Team Portal to browse upcoming events around the world: [http://loco.ubuntu.com/events/](http://loco.ubuntu.com/events/)

**[SIZE="5"]The Hub[/SIZE]**

***[SIZE="4"]Mir 1.4.0 Release[/SIZE]***

Alan Griffiths (alan_g) announces the release of Mir 1.4.0. Alan advises "This release is mostly about supporting Mir based shells using Sway’s layer-shell extension protocol". The first steps are in progress to remove support for the mirclient API in favour of Wayland; but the ability to enable still exist. Alan gives a ABI summary and a Bugs fixed list.

[https://discourse.ubuntu.com/t/mir-1-4-0-release/12198](https://discourse.ubuntu.com/t/mir-1-4-0-release/12198)

**[SIZE="5"]The Planet[/SIZE]**

***[SIZE="4"]APT Patterns[/SIZE]***

Julian Andres Klode makes an implementation of APT patterns so it simplifies the way of finding automatically installed packages, garbage packages (Installed but not required anymore), etc. He makes a few patterns this week, and will be making more in the future. He also submits a pull request to Debian's APT package manager and provides means for user feedback.

[https://blog.jak-linux.org/2019/08/15/apt-patterns/](https://blog.jak-linux.org/2019/08/15/apt-patterns/)

**[SIZE="5"]Other Community News[/SIZE]**

***[SIZE="4"]Xfce 4.14 released[/SIZE]***

The Xfce development team announces the long awaited release of the Xfce desktop 4.14. This cycle sees all core component ports to GTK3 and GDBus, as well most components also have GObject Introspection support. The user experience got some polish, with several new features and numerous bug fixes. Highlights, the changelog, and many links for additional information of the release are provided.

[https://www.xfce.org/about/news/?post=1565568000](https://www.xfce.org/about/news/?post=1565568000)

This story was also covered by a number of news sites. The following is a collection of articles selected by our editors:

[LIST]
[*]Xfce 4.14 officially released, here is what’s new - [https://www.fosslinux.com/18388/xfce-4-14-officially-released-here-is-whats-new.htm](https://www.fosslinux.com/18388/xfce-4-14-officially-released-here-is-whats-new.htm)
[*]XFCE 4.14 Released. Here’s What’s New. - [https://www.debugpoint.com/2019/08/xfce-4-14-released-download/](https://www.debugpoint.com/2019/08/xfce-4-14-released-download/)
[*]Xfce 4.14 Desktop Officially Released - [https://www.phoronix.com/scan.php?page=news_item&px=Xfce-4.14-Released](https://www.phoronix.com/scan.php?page=news_item&px=Xfce-4.14-Released)
[*]Xfce 4.14 Desktop Officially Released, This is What’s New - [https://www.omgubuntu.co.uk/2019/08/xfce-4-14](https://www.omgubuntu.co.uk/2019/08/xfce-4-14)
[/LIST]

**[SIZE="5"]Canonical News[/SIZE]**

[LIST]
[*]Issue #2019.08.12 – The Kubeflow Machine Learning Toolkit - [https://admin.insights.ubuntu.com/2019/08/12/issue-2019-08-12-the-kubeflow-machine-learning-toolkit/](https://admin.insights.ubuntu.com/2019/08/12/issue-2019-08-12-the-kubeflow-machine-learning-toolkit/)
[*]Provisioning ESXi with MAAS: An overview - [https://ubuntu.com/blog/2019/08/12/provisioning-esxi-with-maas/](https://ubuntu.com/blog/2019/08/12/provisioning-esxi-with-maas/)
[*]OpenStack Charms 19.07 – Percona Cluster Cold Start, DVR SNAT and more - [https://ubuntu.com/blog/2019/08/14/openstack-charms-19-07-percona-cluster-cold-start-dvr-snat-and-more/](https://ubuntu.com/blog/2019/08/14/openstack-charms-19-07-percona-cluster-cold-start-dvr-snat-and-more/)
[*]8 Ways Snaps are Different - [https://ubuntu.com/blog/2019/08/15/8-ways-snaps-are-different/](https://ubuntu.com/blog/2019/08/15/8-ways-snaps-are-different/)
[*]Why multi-cloud has become a must-have for enterprises: six experts weigh in -
[/LIST]
 [https://ubuntu.com/blog/2019/08/15/why-multi-cloud-has-become-a-must-have-for-enterprises-six-experts-weigh-in/](https://ubuntu.com/blog/2019/08/15/why-multi-cloud-has-become-a-must-have-for-enterprises-six-experts-weigh-in/)

**[SIZE="5"]In the Blogosphere[/SIZE]**

***[SIZE="4"]AMD Ryzen 3000 Series Playing Nicely With Latest Linux Distros Following BIOS Updates[/SIZE]***

Michael Larabel reports that vendors are pushing out the bios updates affecting the AMD Ryzen 3000 Series motherboards ability to boot. Michael affirms that the update "allows Ubuntu 19.04 and other newer Linux distributions to now boot gracefully on the new AMD Zen 2 desktops”.

[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)

***[SIZE="4"]Intel's Linux Graphics Driver Developers Discover 3~20% Boost For Current-Gen Hardware[/SIZE]***

Michael Larabel reports on this latest driver optimizations for Intel Gallium drivers that applies to the "Gen 9" graphics hardware. Credit is given to Francisco Jerez for the patches and testing that yield significant boosts in performance. The metrics for various chip sets are provided and Francisco is open to feedback from performance testing. These patches will make it into the Mesa 19.2 release (Ubuntu 19.10).

[https://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Graphics-Gen9-Boost](https://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Graphics-Gen9-Boost)

***[SIZE="4"]Linux Finally Has A Fix For Crackling Audio Input On Recent AMD Systems[/SIZE]***

After two years, Michael Larabel finally reports that Linux 5.3 has a fix for crackling sound input, and will be backported to older Linux versions. The fix is made from Takashi Iwai's workaround. It affects motherboards that contain the recent AMD chipsets (e.g. X370/X470) and Realtek sound chipsets.

[https://www.phoronix.com/scan.php?page=news_item&px=Linux-AMD-Analog-Input-Audio-WA](https://www.phoronix.com/scan.php?page=news_item&px=Linux-AMD-Analog-Input-Audio-WA)

***[SIZE="4"]NVIDIA 435.17 Linux Beta Driver Adds Vulkan + OpenGL PRIME Render Offload[/SIZE]***

Michael Larabel reports of the 435 Linux driver, noting improved PRIME/multi-GPU support slated for the xorg-server 1.21 release. However, "NVIDIA is providing an Ubuntu PPA with a patched X.Org Server build" that requires some tweaking to fit. Additionally is support for Turing notebook GPUs with a variety of bug fixes. A link is provided to NVIDIA DevTalk for more details.

[https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-435.17-Linux-Driver](https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-435.17-Linux-Driver)

***[SIZE="4"]Canonical Outs Major Linux Kernel Updates for All Supported Ubuntu Releases[/SIZE]***

Marius Nestor writes that Canonical have released major linux kernel updates for all supported architectures of Ubuntu. Users of Ubuntu 19.04, Ubuntu 18.04 LTS, Ubuntu 16.04 LTS and Ubuntu 14.04 ESM should upgrade to receive fixes for more than thirty security vulnerabilities. Marius provides specifics of selected patch fixes, all users of supported Ubuntu are encouraged to update.

[https://news.softpedia.com/news/canonical-outs-major-linux-kernel-updates-for-all-supported-ubuntu-releases-527037.shtml](https://news.softpedia.com/news/canonical-outs-major-linux-kernel-updates-for-all-supported-ubuntu-releases-527037.shtml)

***[SIZE="4"]LibreOffice 6.2 Open-Source Office Suite Is Now Ready for Enterprise Deployments[/SIZE]***

Marius Nestor reports on this the sixth maintenance update to LibreOffice 6.2. With the latest security patches and back-ported fixes, the release is recommended for users in production environments. All users are urged to update immediately. A link to the software portal is provided that also contains the 6.3 suite series that is not recommended for deployment.

[https://news.softpedia.com/news/libreoffice-6-2-open-source-office-suite-is-now-ready-for-enterprise-deployments-527043.shtml](https://news.softpedia.com/news/libreoffice-6-2-open-source-office-suite-is-now-ready-for-enterprise-deployments-527043.shtml)

**[SIZE="5"]Featured Audio and Video[/SIZE]**

***[SIZE="4"]Ubuntu Security Podcast: Episode 42[/SIZE]***

"This week we have a special interview with Ubuntu Security Team member Jamie Strandboge, talking about security aspects of the Snap packaging system, as well as the usual roundup of security fixes from the past week."

[https://ubuntusecuritypodcast.org/episode-42/](https://ubuntusecuritypodcast.org/episode-42/)

***[SIZE="4"]Ubuntu Podcast from the UK LoCo: S12E19 – Starglider[/SIZE]***

"This week we’ve been fixing floors and playing with the new portal HTML element. We round up the Ubuntu community news including the release of 18.04.3 with a new hardware enablement stack, better desktop integration for Livepatch and improvements in accessing the latest Nvidia drivers. We also have our favourite picks from the general tech news."

[http://ubuntupodcast.org/2019/08/15/s12e19-starglider/](http://ubuntupodcast.org/2019/08/15/s12e19-starglider/)

**[SIZE="5"]Meeting Reports[/SIZE]**

[LIST]
[*]Desktop Team - Monday 19th August 2019 - [https://discourse.ubuntu.com/t/desktop-team-update-monday-19th-august-2019/12223](https://discourse.ubuntu.com/t/desktop-team-update-monday-19th-august-2019/12223)
[*]Server Team - 12 August 2019 - [https://discourse.ubuntu.com/t/ubuntu-server-team-update-12-august-2019/12201](https://discourse.ubuntu.com/t/ubuntu-server-team-update-12-august-2019/12201)
[/LIST]

**[SIZE="5"]Upcoming Meetings and Events[/SIZE]**

[LIST]
[*]Kernel Team: Tue, August 20, 5pm – 6pm
[*]Desktop Team: Tue, August 20, 6:30pm – 7:30pm
[*]Ubuntu Membership Board: Wed, August 21, 12pm – 1pm
[*]Ubuntu Foundations: Thu, August 22, 3pm – 4pm
[/LIST]

For more details and farther dates please visit: [http://fridge.ubuntu.com/calendars/](http://fridge.ubuntu.com/calendars/)

**[SIZE="5"]Updates and Security for 16.04, 18.04, and 19.04[/SIZE]**

***[SIZE="4"]Security Updates[/SIZE]***

[LIST]
[*][USN-4091-1] poppler vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005058.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005058.html)
[*][USN-4092-1] Ghostscript vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005059.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005059.html)
[*][USN-4070-2] MariaDB vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005060.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005060.html)
[*][USN-4070-3] MariaDB vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005061.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005061.html)
[*][USN-4093-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005062.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005062.html)
[*][USN-4094-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005063.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005063.html)
[*][USN-4095-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005064.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005064.html)
[*][USN-4096-1] Linux kernel (AWS) vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005066.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005066.html)
[*][USN-4095-2] Linux kernel (Xenial HWE) vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005065.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005065.html)
[*][USN-4097-1] PHP vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005067.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005067.html)
[*][USN-4097-2] PHP vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005068.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005068.html)
[*][USN-4098-1] wpa_supplicant and hostapd vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005069.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005069.html)
[*][USN-4099-1] nginx vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005070.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005070.html)
[*][USN-4101-1] Firefox vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005071.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-August/005071.html)
[/LIST]

***[SIZE="4"]Ubuntu 16.04 Updates[/SIZE]***

[LIST]
[*]kconfig 5.18.0-0ubuntu1.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025223.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025223.html)
[*]ghostscript 9.26~dfsg+0-0ubuntu0.16.04.10 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025224.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025224.html)
[*]kconfig 5.18.0-0ubuntu1.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025225.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025225.html)
[*]ghostscript 9.26~dfsg+0-0ubuntu0.16.04.10 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025226.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025226.html)
[*]linux-aws-hwe 4.15.0-1045.47~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025227.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025227.html)
[*]linux-meta-aws-hwe 4.15.0.1045.45 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025228.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025228.html)
[*]linux-signed-gcp 4.15.0-1040.42~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025229.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025229.html)
[*]linux-meta-gcp 4.15.0.1040.54 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025230.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025230.html)
[*]linux-gcp 4.15.0-1040.42~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025231.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025231.html)
[*]linux-signed-oracle 4.15.0-1021.23~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025232.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025232.html)
[*]linux-meta-oracle 4.15.0.1021.15 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025233.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025233.html)
[*]linux-oracle 4.15.0-1021.23~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025234.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025234.html)
[*]linux-signed-hwe 4.15.0-58.64~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025235.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025235.html)
[*]linux-meta-hwe 4.15.0.58.79 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025236.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025236.html)
[*]linux-meta-hwe-edge 4.15.0.58.77 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025237.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025237.html)
[*]linux-hwe 4.15.0-58.64~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025238.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025238.html)
[*]linux-signed 4.4.0-159.187 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025239.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025239.html)
[*]linux-meta 4.4.0.159.167 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025240.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025240.html)
[*]linux 4.4.0-159.187 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025241.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025241.html)
[*]linux-meta-aws 4.4.0.1090.94 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025242.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025242.html)
[*]linux-aws 4.4.0-1090.101 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025243.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025243.html)
[*]linux-meta-kvm 4.4.0.1054.54 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025244.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025244.html)
[*]linux-kvm 4.4.0-1054.61 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025245.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025245.html)
[*]linux-meta-raspi2 4.4.0.1118.118 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025246.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025246.html)
[*]linux-raspi2 4.4.0-1118.127 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025247.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025247.html)
[*]linux-snapdragon 4.4.0-1122.128 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025248.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025248.html)
[*]linux-meta-snapdragon 4.4.0.1122.114 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025249.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025249.html)
[*]adobe-flashplugin 1:20190813.1-0ubuntu0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025250.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025250.html)
[*]linux-signed-azure 4.15.0-1055.60 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025251.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025251.html)
[*]linux-meta-azure 4.15.0.1055.58 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025252.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025252.html)
[*]linux-meta-azure-edge 4.15.0.1055.37 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025253.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025253.html)
[*]linux-azure 4.15.0-1055.60 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025254.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025254.html)
[*]software-properties 0.96.20.9 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025255.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025255.html)
[*]dpkg 1.18.4ubuntu1.6 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025256.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025256.html)
[*]php7.0 7.0.33-0ubuntu0.16.04.6 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025257.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025257.html)
[*]bind9 1:9.10.3.dfsg.P4-8ubuntu1.15 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025258.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025258.html)
[*]php7.0 7.0.33-0ubuntu0.16.04.6 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025259.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025259.html)
[*]flashplugin-nonfree 32.0.0.238ubuntu0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025260.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025260.html)
[*]flashplugin-nonfree 32.0.0.238ubuntu0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025261.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025261.html)
[*]btrfs-tools 4.4-1ubuntu1.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025262.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025262.html)
[*]zfs-linux 0.6.5.6-0ubuntu28 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025263.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025263.html)
[*]landscape-client 16.03-0ubuntu2.16.04.7 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025264.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025264.html)
[*]adobe-flashplugin 1:20190813.1-0ubuntu0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025265.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025265.html)
[*]linux-azure_4.15.0-1055.60_amd64.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025266.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025266.html)
[*]linux_4.4.0-159.187_amd64.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025267.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025267.html)
[*]linux-hwe_4.15.0-58.64~16.04.1_ppc64el.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025268.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025268.html)
[*]linux-hwe_4.15.0-58.64~16.04.1_amd64.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025269.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025269.html)
[*]linux-oracle_4.15.0-1021.23~16.04.1_amd64.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025270.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025270.html)
[*]linux-gcp_4.15.0-1040.42~16.04.1_amd64.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025271.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025271.html)
[*]linux-signed 4.4.0-159.187 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025272.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025272.html)
[*]linux 4.4.0-159.187 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025273.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025273.html)
[*]linux-meta 4.4.0.159.167 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025274.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025274.html)
[*]linux-raspi2 4.4.0-1118.127 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025275.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025275.html)
[*]linux-meta-raspi2 4.4.0.1118.118 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025276.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025276.html)
[*]linux-snapdragon 4.4.0-1122.128 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025277.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025277.html)
[*]linux-meta-snapdragon 4.4.0.1122.114 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025278.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025278.html)
[*]linux-meta-aws 4.4.0.1090.94 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025279.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025279.html)
[*]linux-aws 4.4.0-1090.101 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025280.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025280.html)
[*]linux-meta-kvm 4.4.0.1054.54 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025281.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025281.html)
[*]linux-kvm 4.4.0-1054.61 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025282.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025282.html)
[*]linux-aws-hwe 4.15.0-1045.47~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025283.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025283.html)
[*]linux-meta-aws-hwe 4.15.0.1045.45 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025284.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025284.html)
[*]linux-signed-gcp 4.15.0-1040.42~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025285.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025285.html)
[*]linux-meta-gcp 4.15.0.1040.54 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025286.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025286.html)
[*]linux-gcp 4.15.0-1040.42~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025287.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025287.html)
[*]linux-signed-oracle 4.15.0-1021.23~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025288.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025288.html)
[*]linux-meta-oracle 4.15.0.1021.15 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025289.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025289.html)
[*]linux-oracle 4.15.0-1021.23~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025290.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025290.html)
[*]linux-meta-hwe-edge 4.15.0.58.77 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025291.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025291.html)
[*]linux-signed-hwe 4.15.0-58.64~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025292.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025292.html)
[*]linux-meta-hwe 4.15.0.58.79 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025293.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025293.html)
[*]linux-hwe 4.15.0-58.64~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025294.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025294.html)
[*]linux-signed-azure 4.15.0-1055.60 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025295.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025295.html)
[*]linux-meta-azure 4.15.0.1055.58 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025296.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025296.html)
[*]linux-azure 4.15.0-1055.60 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025297.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025297.html)
[*]linux-meta-azure-edge 4.15.0.1055.37 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025298.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025298.html)
[*]chromium-browser 76.0.3809.100-0ubuntu0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025299.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025299.html)
[*]linux-signed 4.4.0-160.188 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025300.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025300.html)
[*]linux 4.4.0-160.188 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025301.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025301.html)
[*]linux-meta 4.4.0.160.168 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025302.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025302.html)
[*]firefox 68.0.2+build1-0ubuntu0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025303.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025303.html)
[*]linux-aws 4.4.0-1091.102 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025304.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025304.html)
[*]linux-meta-aws 4.4.0.1091.95 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025305.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025305.html)
[*]linux_4.4.0-160.188_amd64.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025306.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025306.html)
[*]linux-kvm 4.4.0-1055.62 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025307.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025307.html)
[*]linux-meta-kvm 4.4.0.1055.55 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025308.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025308.html)
[*]linux-raspi2 4.4.0-1119.128 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025309.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025309.html)
[*]linux-meta-raspi2 4.4.0.1119.119 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025310.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025310.html)
[*]nginx 1.10.3-0ubuntu0.16.04.4 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025311.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025311.html)
[*]linux-snapdragon 4.4.0-1123.129 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025312.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025312.html)
[*]linux-meta-snapdragon 4.4.0.1123.115 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025313.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025313.html)
[*]chromium-browser 76.0.3809.100-0ubuntu0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025314.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025314.html)
[*]firefox 68.0.2+build1-0ubuntu0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025315.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025315.html)
[*]nginx 1.10.3-0ubuntu0.16.04.4 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025316.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025316.html)
[*]linux-signed-hwe 4.15.0-59.66~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025317.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025317.html)
[*]linux-hwe 4.15.0-59.66~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025318.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025318.html)
[*]linux-meta-hwe 4.15.0.59.80 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025319.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025319.html)
[*]kde4libs 4:4.14.16-0ubuntu3.3 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025320.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025320.html)
[*]kde4libs 4:4.14.16-0ubuntu3.3 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025321.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025321.html)
[*]dh-python 2.20151103ubuntu1.2 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025322.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025322.html)
[*]dh-python 2.20151103ubuntu1.2 - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025323.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025323.html)
[*]linux-hwe_4.15.0-59.66~16.04.1_ppc64el.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025324.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025324.html)
[*]linux-hwe_4.15.0-59.66~16.04.1_amd64.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2019-August/025325.html](https://lists.ubuntu.com/archives/xenial-changes/2019-August/025325.html)
[/LIST]

End of Life: April 2021

***[SIZE="4"]Ubuntu 18.04 Updates[/SIZE]***

[LIST]
[*]rtl8812au 4.3.8.12175.20140902+dfsg-0ubuntu8.1 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021550.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021550.html)
[*]nvidia-graphics-drivers-430 430.26-0ubuntu0.18.04.2 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021551.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021551.html)
[*]dpdk 17.11.6-0~ubuntu18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021552.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021552.html)
[*]nvidia-graphics-drivers-340 340.107-0ubuntu0.18.04.3 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021553.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021553.html)
[*]dahdi-linux 1:2.11.1~dfsg-1ubuntu4.1 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021554.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021554.html)
[*]xtables-addons 3.0-0.1ubuntu2 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021555.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021555.html)
[*]kpatch 0.5.0-0ubuntu1.1 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021556.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021556.html)
[*]dm-writeboost 2.2.8-1ubuntu3~18.04.2 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021557.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021557.html)
[*]chromium-browser 76.0.3809.87-0ubuntu0.18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021558.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021558.html)
[*]linux-azure 5.0.0-1013.13~18.04.2 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021559.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021559.html)

Due to excessive content these are abridged; The complete list is here: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue592#Ubuntu_18.04_Updates](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue592#Ubuntu_18.04_Updates)


[*]kde4libs 4:4.14.38-0ubuntu3.1 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021832.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021832.html)
[*]nginx 1.14.0-0ubuntu1.5 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021833.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021833.html)
[*]nginx 1.14.0-0ubuntu1.5 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021834.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021834.html)
[*]linux-oem-osp1 5.0.0-1019.21 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021835.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021835.html)
[*]linux-signed-oem-osp1 5.0.0-1019.21 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021836.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021836.html)
[*]linux-restricted-modules-oem-osp1 5.0.0-1019.21 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021837.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021837.html)
[*]linux-meta-oem-osp1 5.0.0.1019.20 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021838.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021838.html)
[*]linux-raspi2 4.15.0-1044.47 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021839.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021839.html)
[*]linux-meta-raspi2 4.15.0.1044.42 - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021840.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021840.html)
[*]linux-oem-osp1_5.0.0-1019.21_amd64.tar.gz - [https://lists.ubuntu.com/archives/bionic-changes/2019-August/021841.html](https://lists.ubuntu.com/archives/bionic-changes/2019-August/021841.html)
[/LIST]

End of Life: April 2023

***[SIZE="4"]Ubuntu 19.04 Updates[/SIZE]***

[LIST]
[*]linux-meta-oem 4.15.0.1050.54 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011788.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011788.html)
[*]linux-oem 4.15.0-1050.57 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011789.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011789.html)
[*]linux-signed-oem 4.15.0-1050.57 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011790.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011790.html)
[*]linux-oem-osp1 5.0.0-1018.20 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011791.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011791.html)
[*]linux-meta-oem-osp1 5.0.0.1018.19 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011792.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011792.html)
[*]linux-signed-oem-osp1 5.0.0-1018.20 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011793.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011793.html)
[*]linux-oracle 4.15.0-1021.23 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011794.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011794.html)
[*]linux-meta-oracle 4.15.0.1021.24 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011795.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011795.html)
[*]linux-signed-oracle 4.15.0-1021.23 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011796.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011796.html)
[*]linux-oem-osp1_5.0.0-1018.20_amd64.tar.gz - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011797.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011797.html)

Due to excessive content these are abridged; The complete list is here: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue592#Ubuntu_19.04_Updates](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue592#Ubuntu_19.04_Updates)


[*]chromium-browser 76.0.3809.100-0ubuntu0.19.04.1 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011897.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011897.html)
[*]firefox 68.0.2+build1-0ubuntu0.19.04.1 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011898.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011898.html)
[*]nginx 1.15.9-0ubuntu1.1 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011899.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011899.html)
[*]linux-azure 5.0.0-1016.17 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011900.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011900.html)
[*]linux-signed-azure 5.0.0-1016.17 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011901.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011901.html)
[*]linux-meta-azure 5.0.0.1016.15 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011902.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011902.html)
[*]linux-azure_5.0.0-1016.17_amd64.tar.gz - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011903.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011903.html)
[*]kde4libs 4:4.14.38-0ubuntu6.1 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011904.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011904.html)
[*]kde4libs 4:4.14.38-0ubuntu6.1 - [https://lists.ubuntu.com/archives/disco-changes/2019-August/011905.html](https://lists.ubuntu.com/archives/disco-changes/2019-August/011905.html)
[/LIST]

End of Life: January 2020

**[SIZE="5"]Subscribe[/SIZE]**

Get your copy of the Ubuntu Weekly Newsletter delivered each week to you via email at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-news](https://lists.ubuntu.com/mailman/listinfo/ubuntu-news)

Or follow us via our various social media presences:

[LIST]
[*][https://www.facebook.com/UbuntuWeeklyNewsletter](https://www.facebook.com/UbuntuWeeklyNewsletter)
[*][https://twitter.com/Ubuntu_News](https://twitter.com/Ubuntu_News)
[*][https://www.reddit.com/r/Ubuntu/](https://www.reddit.com/r/Ubuntu/)
[/LIST]

**[SIZE="5"]Archive[/SIZE]**

You can always find older Ubuntu Weekly Newsletter issues at: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Archive](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Archive)

**[SIZE="5"]Further News[/SIZE]**

As always you can find more Ubuntu news and announcements at:

[LIST]
[*][https://blog.ubuntu.com/](https://blog.ubuntu.com/)
[*][http://fridge.ubuntu.com/](http://fridge.ubuntu.com/)
[/LIST]

**[SIZE="5"]Conclusion[/SIZE]**

Thank you for reading the Ubuntu Weekly Newsletter.

See you next week!

**[SIZE="5"]Credits[/SIZE]**

The Ubuntu Weekly Newsletter is brought to you by:

[LIST]
[*]Krytarik Raido
[*]Bashing-om
[*]Chris Guiver
[*]Wild Man
[*]EoflaOE
[*]And many others
[/LIST]

**[SIZE="5"]Glossary of Terms[/SIZE]**

Other acronyms can be found at: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/glossary](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/glossary)

**[SIZE="5"]Get Involved[/SIZE]**

The Ubuntu community consists of individuals and teams, working on different aspects of the distribution, giving advice and technical support, and helping to promote Ubuntu to a wider audience. No contribution is too small, and anyone can help. It's your chance to get in on all the community fun associated with developing and promoting Ubuntu. More on this at: [https://community.ubuntu.com/contribute/](https://community.ubuntu.com/contribute/)

Or get involved with the Ubuntu Weekly Newsletter team! We always need summary writers and editors, if you're interested, learn more at: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Join](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Join)

**[SIZE="5"]Feedback[/SIZE]**

This document is maintained by the Ubuntu Weekly News Team. If you have a story idea or suggestions for the Weekly Newsletter, join the Ubuntu News Team mailing list at [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team) and submit it. Ideas can also be added to the wiki at [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas). If you'd like to contribute to a future issue of the Ubuntu Weekly Newsletter, please feel free to edit the appropriate wiki page. If you have any technical support questions, please check [https://community.ubuntu.com/help-information/](https://community.ubuntu.com/help-information/) for more information on where to get help.

[IMG]https://fridge.ubuntu.com/wp-content/uploads/2011/07/CCL.png[/IMG] Except where otherwise noted, this issue of the Ubuntu Weekly Newsletter is licensed under a [Creative Commons Attribution ShareAlike 3.0 License]("https://creativecommons.org/licenses/by-sa/3.0/")

---

