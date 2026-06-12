---
title: "Ubuntu Weekly Newsletter Issue 654"
date: 2020-10-26
forum: Weekly Newsletter
---

### Post by Bashing-om on 2020-10-26
Subforum: [https://ubuntuforums.org/forumdisplay.php?f=243](https://ubuntuforums.org/forumdisplay.php?f=243)
Title: Ubuntu Weekly Newsletter Issue 654

[IMG]https://fridge.ubuntu.com/wp-content/uploads/2020/02/c9d7/header.png[/IMG]

Welcome to the Ubuntu Weekly Newsletter, Issue 654 for the week of October 18 - 24, 2020. The wiki page of this issue is available [here]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue654").

**[SIZE="5"]In this Issue[/SIZE]**

[LIST]
[*]Ubuntu 20.10 (Groovy Gorilla) released
[*]Corrections to point release publications of current LTSes
[*]Ubuntu Glibc News
[*]Welcome New Members and Developers
[*]Ubuntu Stats
[*]Hot in Support
[*]LoCo Events
[*]OpenStack Victoria for Ubuntu 20.10 and Ubuntu 20.04 LTS
[*]Ubuntu Cloud News
[*]Canonical News
[*]In the Press
[*]In the Blogosphere
[*]Featured Audio and Video
[*]Meeting Reports
[*]Upcoming Meetings and Events
[*]Updates and Security for 16.04, 18.04, 20.04, and 20.10
[*]And much more!
[/LIST]

**[SIZE="5"]General Community News[/SIZE]**

***[SIZE="4"]Ubuntu 20.10 (Groovy Gorilla) released[/SIZE]***

Brian Murray, on behalf of the Ubuntu Release Team, announces the release of Ubuntu 20.10 (Groovy Gorilla). Its new features and bug fixes are discussed: notably is the update to the 5.8 Linux kernel, the move to glibc 2.32, the addition of the Raspberry Pi image variant, introduction of GNOME 3.38, and many server innovations. Links are provided for supports, the
Official Flavours, and more information.

[https://lists.ubuntu.com/archives/ubuntu-announce/2020-October/000263.html](https://lists.ubuntu.com/archives/ubuntu-announce/2020-October/000263.html)

This release was widely covered, the following is a collection of articles selected by our editors:
[LIST]
[*]Ubuntu 20.10 Released With GNOME 3.38, Active Directory Installer Integration - [https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-20.10-Released](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-20.10-Released)
[*]Canonical Officially Launches Ubuntu 20.10 - [https://news.softpedia.com/news/canonical-officially-launches-ubuntu-20-10-531398.shtml](https://news.softpedia.com/news/canonical-officially-launches-ubuntu-20-10-531398.shtml)
[*]Ubuntu 20.10 Official Flavors Released, Here’s What’s New - [https://9to5linux.com/ubuntu-20-10-official-flavors-released-heres-whats-new](https://9to5linux.com/ubuntu-20-10-official-flavors-released-heres-whats-new)
[*]Ubuntu 20.10 Released, Now Available to Download - [https://www.omgubuntu.co.uk/2020/10/download-ubuntu-20-10](https://www.omgubuntu.co.uk/2020/10/download-ubuntu-20-10)
[*]What’s New in Ubuntu 20.10 ‘Groovy Gorilla’ - https://www.howtogeek.com/694016/what's-new-in-ubuntu-20.10-"groovy-gorilla"/
[/LIST]

Interested in the flavors? Release announcements as follows:
[LIST]
[*]Ubuntu MATE 20.10 Release Notes - [https://ubuntu-mate.org/blog/ubuntu-mate-groovy-gorilla-release-notes/](https://ubuntu-mate.org/blog/ubuntu-mate-groovy-gorilla-release-notes/)
[*]Lubuntu 20.10 (Groovy Gorilla) Released! - [https://lubuntu.me/groovy-released/](https://lubuntu.me/groovy-released/)
[*]Ubuntu Studio 20.10 Released - [https://ubuntustudio.org/2020/10/ubuntu-studio-20-10-released/](https://ubuntustudio.org/2020/10/ubuntu-studio-20-10-released/)
[*]Kubuntu 20.10 Groovy Gorilla released - [https://kubuntu.org/news/kubuntu-20-10-groovy-gorilla-released/](https://kubuntu.org/news/kubuntu-20-10-groovy-gorilla-released/)
[/LIST]

***[SIZE="4"]Corrections to point release publications of current LTSes[/SIZE]***

Steve Langasek reminds us of the dropping of MD5 & SHA1 checksums for Ubuntu and flavor ISOs, in favor of sha256sums only. In the clean up, the md5sum and sha1sum files have now been removed for all currently-published releases. Among the clean up items all stale point release images have been taken down.

[https://lists.ubuntu.com/archives/ubuntu-release/2020-October/005113.html](https://lists.ubuntu.com/archives/ubuntu-release/2020-October/005113.html)

***[SIZE="4"]Ubuntu Glibc News[/SIZE]***

Balint Reczey writes about glibc 2.32 as found in Ubuntu 20.10 that includes many new features, plus some deprecations, which have mitigations. In respect to these, because a number of the mitigations will be dropped in due course, a warning is given. If your current application/package builds using one of these mitigations you need to update your programs before the mitigations are dropped. Updates to glibc used in Ubuntu 20.04 LTS are also noted, likewise with Ubuntu 18.04 LTS; which will soon receive it's update of glibc 2.27. A note is given on how to file merge proposals for Ubuntu specific patches.

[https://lists.ubuntu.com/archives/ubuntu-devel/2020-October/041241.html](https://lists.ubuntu.com/archives/ubuntu-devel/2020-October/041241.html)

***[SIZE="4"]Welcome New Members and Developers[/SIZE]***

 *Ubuntu Member; Bill Iddings (franksmcb) - [https://lists.ubuntu.com/archives/ubuntu-news-team/2020-October/002935.html](https://lists.ubuntu.com/archives/ubuntu-news-team/2020-October/002935.html)
 *Ubuntu Community Council re-election:
[LIST]
[*]Walter Lapchynski
[*]Lina Elizabeth Porras Santana
[*]Thomas Ward
[*]José Antonio Rey
[*]Nathan Haines
[*]Torsten Franz
[*]Erich Eichmeyer
[/LIST]

        [http://fridge.ubuntu.com/2020/10/24/announcing-the-new-ubuntu-community-council-2/](http://fridge.ubuntu.com/2020/10/24/announcing-the-new-ubuntu-community-council-2/)

Congratulations to these contributors!

**[SIZE="5"]Ubuntu Stats[/SIZE]**

***[SIZE="4"]Bug Stats[/SIZE]***

[LIST]
[*]Open: 134783 (+107)
[*]Critical: 343 (-3)
[*]Unconfirmed: 66620 (+111)
[/LIST]

As always, the Bug Squad needs more help. If you want to get started, please see: [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

***[SIZE="4"]Translations[/SIZE]***

[LIST]
[*]Ukrainian: 88.49% (36755/79)
[*]German: 87.06% (41319/1)
[*]Spanish: 82.07% (57264/3565)
[*]French: 81.59% (58797/6956)
[*]Swedish: 75.07% (79610/932)
[/LIST]

**[SIZE="5"]Hot in Support[/SIZE]**

***[SIZE="4"]Ask Ubuntu Top 5 Questions[/SIZE]***

[LIST]
[*]How can I solve “Be aware that removing the lock file is not a solution and may break your system”? - [https://askubuntu.com/questions/1286005/how-can-i-solve-be-aware-that-removing-the-lock-file-is-not-a-solution-and-may](https://askubuntu.com/questions/1286005/how-can-i-solve-be-aware-that-removing-the-lock-file-is-not-a-solution-and-may)
[*]Firefox 82: tab bar merged into window title bar - [https://askubuntu.com/questions/1286491/firefox-82-tab-bar-merged-into-window-title-bar](https://askubuntu.com/questions/1286491/firefox-82-tab-bar-merged-into-window-title-bar)
[*]How do I recursively list dependencies of a package that need to be installed? - [https://askubuntu.com/questions/1286433/how-do-i-recursively-list-dependencies-of-a-package-that-need-to-be-installed](https://askubuntu.com/questions/1286433/how-do-i-recursively-list-dependencies-of-a-package-that-need-to-be-installed)
[*]Uninstall extra Zoom Meeting application? - [https://askubuntu.com/questions/1285389/uninstall-extra-zoom-meeting-application](https://askubuntu.com/questions/1285389/uninstall-extra-zoom-meeting-application)
[*]Ubuntu 18.04 broken install problem with libnvidia-common-450 package - [https://askubuntu.com/questions/1285472/ubuntu-18-04-broken-install-problem-with-libnvidia-common-450-package](https://askubuntu.com/questions/1285472/ubuntu-18-04-broken-install-problem-with-libnvidia-common-450-package)
[/LIST]
Ask (and answer!) questions at: [https://askubuntu.com/](https://askubuntu.com/)

***[SIZE="4"]Ubuntu Forums Top 5 Threads[/SIZE]***

[LIST]
[*]How do grub/ Ubuntu/ grub.cfg interact during boot ? - [https://ubuntuforums.org/showthread.php?t=2452509](https://ubuntuforums.org/showthread.php?t=2452509)
[*]hp printer connection problems - [https://ubuntuforums.org/showthread.php?t=2452452](https://ubuntuforums.org/showthread.php?t=2452452)
[*]20.04.1 is the HARDEST Ubuntu install ever - [https://ubuntuforums.org/showthread.php?t=2452426](https://ubuntuforums.org/showthread.php?t=2452426)
[*]Where can I learn most used Ubuntu Commands? - [https://ubuntuforums.org/showthread.php?t=2452296](https://ubuntuforums.org/showthread.php?t=2452296)
[*]How do I get Ubuntu installed on its own partition - [https://ubuntuforums.org/showthread.php?t=2452415](https://ubuntuforums.org/showthread.php?t=2452415)
[/LIST]

Find more support at: [https://ubuntuforums.org/](https://ubuntuforums.org/)

**[SIZE="5"]LoCo Events[/SIZE]**

The following LoCo team events are currently scheduled in the next two weeks:

[LIST]
[*]Virtual Tempe Ubuntu Hour, Arizona LoCo Team: [http://loco.ubuntu.com/events/ubuntu-arizona/4056-virtual-tempe-ubuntu-hour/](http://loco.ubuntu.com/events/ubuntu-arizona/4056-virtual-tempe-ubuntu-hour/)
[*]Virtual AZLOCO/PLUG Install-fest/Linux Workshop, Arizona LoCo Team: [http://loco.ubuntu.com/events/ubuntu-arizona/4057-virtual-azlocoplug-install-festlinux-workshop/](http://loco.ubuntu.com/events/ubuntu-arizona/4057-virtual-azlocoplug-install-festlinux-workshop/)
[/LIST]

Looking beyond the next two weeks? Visit the LoCo Team Portal to browse upcoming events around the world: [http://loco.ubuntu.com/events/](http://loco.ubuntu.com/events/)

**[SIZE="5"]The Planet[/SIZE]**

***[SIZE="4"]OpenStack Victoria for Ubuntu 20.10 and Ubuntu 20.04 LTS[/SIZE]***

Corey Bryant reports that the Ubuntu OpenStack team at Canonical have announced the general availability of OpenStack Victoria. Packages are in standard repositories for Ubuntu 20.10, and available via Ubuntu Cloud Archive (PPA) for Ubuntu 20.04 LTS. A list of updated packages found in the Ubuntu Cloud Archive is also provided, along with links, and a note on filing bugs, should any be found.

[https://wrestlingpenguins.wordpress.com/2020/10/22/openstack-victoria-for-ubuntu-20-10-and-ubuntu-20-04-lts/](https://wrestlingpenguins.wordpress.com/2020/10/22/openstack-victoria-for-ubuntu-20-10-and-ubuntu-20-04-lts/)

**[SIZE="5"]Ubuntu Cloud News[/SIZE]**

[LIST]
[*]Telco cloud: what is that? - [https://ubuntu.com/blog/telco-cloud-what-is-that](https://ubuntu.com/blog/telco-cloud-what-is-that)
[*]Ubuntu 20.10 on Raspberry Pi delivers the full Linux desktop and micro clouds - [https://ubuntu.com//blog/ubuntu-20-10-on-raspberry-pi-delivers-the-full-linux-desktop-and-micro-clouds](https://ubuntu.com//blog/ubuntu-20-10-on-raspberry-pi-delivers-the-full-linux-desktop-and-micro-clouds)
[/LIST]

**[SIZE="5"]Canonical News[/SIZE]**

[LIST]
[*]Build a Raspberry Pi Desktop with an Ubuntu heart - [https://ubuntu.com//blog/build-a-raspberry-pi-desktop-with-an-ubuntu-heart](https://ubuntu.com//blog/build-a-raspberry-pi-desktop-with-an-ubuntu-heart)
[*]Canonical & Ubuntu Join AfricaCom Virtual 2020 - [https://ubuntu.com/blog/canonical-ubuntu-join-africacom-virtual-2020](https://ubuntu.com/blog/canonical-ubuntu-join-africacom-virtual-2020)
[*]Automating Server Provisioning in phoenixNap’s Bare Metal Cloud with MAAS (Metal-as-a-Service) - [https://ubuntu.com/blog/automating-server-provisioning-in-phoenixnaps-bare-metal-cloud-with-maas-metal-as-a-service](https://ubuntu.com/blog/automating-server-provisioning-in-phoenixnaps-bare-metal-cloud-with-maas-metal-as-a-service)
[*]Canonical & Ubuntu at KubeCon NA Virtual 2020 - [https://ubuntu.com/blog/canonical-ubuntu-at-kubecon-na-virtual-2020](https://ubuntu.com/blog/canonical-ubuntu-at-kubecon-na-virtual-2020)
[*]Ubuntu for Raspberry Pi - [https://ubuntu.com/raspberry-pi](https://ubuntu.com/raspberry-pi)
[/LIST]

**[SIZE="5"]In the Press[/SIZE]**

***[SIZE="4"]Ubuntu clouds on the Raspberry Pi[/SIZE]***

Steven J. Vaughan-Nichols mentions the Ubuntu 20.10 release, noting especially that it provides "optimized Raspberry Pi images for the desktop, server and the cloud". Steven lists some of the features found in Ubuntu 20.10, before quoting Mark Shuttleworth's statement on the Raspberry Pi Foundation's commitment to open computing. The reasons why Ubuntu 20.10 is worth using on the Raspberry Pi 4 (esp. with 8GB RAM) are given, along with numerous links.

[https://www.zdnet.com/article/ubuntu-clouds-on-the-raspberry-pi/](https://www.zdnet.com/article/ubuntu-clouds-on-the-raspberry-pi/)

This support is widely covered in the medias, the following is a collection of articles selected by our editors:
[LIST]
[*]Ubuntu Linux 20.10 'Groovy Gorilla' is here with renewed Raspberry Pi focus - [https://betanews.com/2020/10/22/ubuntu-linux-2010-groovy-gorilla-2/](https://betanews.com/2020/10/22/ubuntu-linux-2010-groovy-gorilla-2/)
[*]Ubuntu 20.10 'Groovy Gorilla' Swings Onto Raspberry Pi - [https://www.tomshardware.com/news/ubuntu-2010-for-raspberry-pi](https://www.tomshardware.com/news/ubuntu-2010-for-raspberry-pi)
[*]Ubuntu 20.10 'Groovy Gorilla' Swings Onto Raspberry Pi - [https://www.tomshardware.com/news/ubuntu-2010-for-raspberry-pi](https://www.tomshardware.com/news/ubuntu-2010-for-raspberry-pi)
[*]Ubuntu 20.10 “Groovy Gorilla” Arrives With Linux 5.8, GNOME 3.38, Raspberry Pi 4 Support - [https://www.linuxjournal.com/content/ubuntu-2010-groovy-gorilla-arrives-linux-58-gnome-338-raspberry-pi-4-support](https://www.linuxjournal.com/content/ubuntu-2010-groovy-gorilla-arrives-linux-58-gnome-338-raspberry-pi-4-support)
[/LIST]

**[SIZE="5"]In the Blogosphere[/SIZE]**

***[SIZE="4"]Ubuntu and Debian Get Patches for Bluetooth Remote Code Execution Flaws, Update Now[/SIZE]***

Marius Nestor tells us that the Debian Project and Canonical have released Linux kernel updates addressing remote code execution vulnerabilities discovered in Bluetooth protocol implementations. The CVEs and releases impacted are listed, which include Ubuntu 20.04 LTS, Ubuntu 18.04 LTS, and Ubuntu 16.04 LTS. Links and kernel versions, including required fixes, are provided.

[https://9to5linux.com/ubuntu-and-debian-get-patches-for-bluetooth-remote-code-execution-flaws-update-now](https://9to5linux.com/ubuntu-and-debian-get-patches-for-bluetooth-remote-code-execution-flaws-update-now)

**[SIZE="5"]Featured Audio and Video[/SIZE]**

***[SIZE="4"]Ubuntu Security Podcast: Episode 93[/SIZE]***

"This week we cover security updates for NTP, Brotli, Spice, the Linux kernel (including BleedingTooth) and a FreeType vulnerability which is being exploited in-the-wild, plus we talk about the NSAs report into the most exploited vulnerabilities as well as the release of Ubuntu 20.10 Groovy Gorilla."

[https://ubuntusecuritypodcast.org/episode-93/](https://ubuntusecuritypodcast.org/episode-93/)

***[SIZE="4"]Ubuntu Podcast from the UK LoCo: S13E31 – Cheers with water[/SIZE]***

"This week we’ve been upgrading computers and Ebaying stuff. We discuss the Windows Calculator coming to Linux, Microsoft Edge browser coming to Linux, Ubuntu Community Council elections and LibreOffice office getting Yaru icons. We also round up our picks from the general tech news."

[https://ubuntupodcast.org/2020/10/22/s13e31-cheers-with-water/](https://ubuntupodcast.org/2020/10/22/s13e31-cheers-with-water/)

***[SIZE="4"]Ubuntu Desktop on Raspberry Pi[/SIZE]***

"Ubuntu Desktop 20.10 sees much-anticipated support for the Raspberry Pi. Download an optimised image that transforms a Raspberry Pi 4 (with 4GB or 8GB of RAM) into a complete Ubuntu workstation. This wouldn’t have been possible without the Ubuntu community, the Raspberry Pi Foundations support and their incredible hardware, and you, the users."

[https://www.youtube.com/watch?v=0pT4-RcTERU](https://www.youtube.com/watch?v=0pT4-RcTERU)

***[SIZE="4"]Ubuntu Portugal Podcast: S01E113 - Cirurgia[/SIZE]***

"Já votaram no Podcast Ubuntu Portugal em podes.pt? Não? Então não leias mais e vai até [https://podes.pt/votar/](https://podes.pt/votar/) escreve Podcast Ubuntu Portugal e clica em VOTAR. Não falhes a aritmética e repete as vezes que conseguires."

[https://podcastubuntuportugal.org/e113/](https://podcastubuntuportugal.org/e113/)

**[SIZE="5"]Meeting Reports[/SIZE]**

[LIST]
[*]Desktop Team Updates - Monday 26th October 2020 - [https://discourse.ubuntu.com/t/desktop-team-updates-monday-26th-october-2020/18900](https://discourse.ubuntu.com/t/desktop-team-updates-monday-26th-october-2020/18900)
[/LIST]

**[SIZE="5"]Upcoming Meetings and Events[/SIZE]**

[LIST]
[*]Kernel Team: Tue, October 27, 5pm – 6pm
[*]Desktop Team: Tue, October 27, 1:30pm – 2:30pm (per IRC topic advisory)
[*]Ubuntu Foundations: Thu, October 29, 3pm – 4pm
[/LIST]

Times shown are UTC. For more details and farther dates please visit: [http://fridge.ubuntu.com/calendars/](http://fridge.ubuntu.com/calendars/)

**[SIZE="5"]Updates and Security for 16.04, 18.04, 20.04, and 20.10[/SIZE]**

***[SIZE="4"]Security Updates[/SIZE]***

[LIST]
[*][USN-4590-1] Collabtive vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005701.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005701.html)
[*][USN-4591-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005702.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005702.html)
[*][USN-4592-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005703.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005703.html)
[*][USN-4593-1] FreeType vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005704.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005704.html)
[*][USN-4586-1] PHP ImageMagick vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005709.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005709.html)
[*][USN-4594-1] Quassel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005705.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005705.html)
[*][USN-4595-1] Grunt vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005706.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005706.html)
[*][USN-4596-1] Tomcat vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005707.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005707.html)
[*][USN-4587-1] iTALC vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005710.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005710.html)
[*][USN-4588-1] FlightGear vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005708.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005708.html)
[*][USN-4597-1] mod_auth_mellon vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005711.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005711.html)
[*][USN-4598-1] LibEtPan vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005712.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005712.html)
[*][USN-4600-1] Netty vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005713.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005713.html)
[*][USN-4601-1] pip vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005714.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005714.html)
[*][USN-4599-1] Firefox vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005715.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005715.html)
[*][USN-4593-2] FreeType vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005716.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-October/005716.html)
[/LIST]

***[SIZE="4"]Ubuntu 16.04 Updates[/SIZE]***

[LIST]
[*]collabtive 2.0+dfsg-6ubuntu1.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028598.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028598.html)
[*]collabtive 2.0+dfsg-6ubuntu1.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028599.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028599.html)
[*]linux-signed-hwe 4.15.0-122.124~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028600.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028600.html)
[*]linux-meta-hwe 4.15.0.122.122 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028601.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028601.html)
[*]linux-hwe 4.15.0-122.124~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028602.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028602.html)
[*]linux-hwe_4.15.0-122.124~16.04.1_ppc64el.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028603.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028603.html)
[*]linux-hwe_4.15.0-122.124~16.04.1_amd64.tar.gz - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028604.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028604.html)
[*]linux-signed-hwe 4.15.0-122.124~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028605.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028605.html)
[*]linux-hwe 4.15.0-122.124~16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028606.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028606.html)
[*]linux-meta-hwe 4.15.0.122.122 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028607.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028607.html)
[*]freetype 2.6.1-0.1ubuntu2.5 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028608.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028608.html)
[*]freetype 2.6.1-0.1ubuntu2.5 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028609.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028609.html)
[*]flightgear 3.4.0-3ubuntu1.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028610.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028610.html)
[*]flightgear 3.4.0-3ubuntu1.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028611.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028611.html)
[*]pam-python 1.0.4-1.1+deb8u1build0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028612.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028612.html)
[*]pam-python 1.0.4-1.1+deb8u1build0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028613.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028613.html)
[*]libapache2-mod-auth-mellon 0.12.0-2+deb9u1build0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028614.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028614.html)
[*]libetpan 1.6-1ubuntu0.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028615.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028615.html)
[*]libapache2-mod-auth-mellon 0.12.0-2+deb9u1build0.16.04.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028616.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028616.html)
[*]libetpan 1.6-1ubuntu0.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028617.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028617.html)
[*]netty-3.9 3.9.0.Final-1ubuntu0.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028618.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028618.html)
[*]netty-3.9 3.9.0.Final-1ubuntu0.1 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028619.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028619.html)
[*]debootstrap 1.0.78+nmu1ubuntu1.12 - [https://lists.ubuntu.com/archives/xenial-changes/2020-October/028620.html](https://lists.ubuntu.com/archives/xenial-changes/2020-October/028620.html)
[/LIST]

End of Standard Support: April 2021

***[SIZE="4"]Ubuntu 18.04 Updates[/SIZE]***

[LIST]
[*]torbrowser-launcher 0.2.9-2ubuntu1 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030016.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030016.html)
[*]linux-signed 4.15.0-122.124 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030017.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030017.html)
[*]linux-restricted-modules 4.15.0-122.124 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030018.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030018.html)
[*]linux 4.15.0-122.124 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030019.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030019.html)
[*]linux-meta 4.15.0.122.109 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030020.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030020.html)
[*]linux-oem 4.15.0-1100.110 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030021.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030021.html)
[*]linux-signed-oem 4.15.0-1100.110 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030022.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030022.html)
[*]linux-restricted-modules-oem 4.15.0-1100.110 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030023.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030023.html)
[*]linux-meta-oem 4.15.0.1100.104 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030024.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030024.html)
[*]linux-signed-oem-osp1 5.0.0-1070.76 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030025.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030025.html)

Due to excessive content these are abridged; The complete list is here: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue654#Ubuntu_18.04_Updates](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue654#Ubuntu_18.04_Updates)


[*]clevis 8-1ubuntu0.2 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030078.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030078.html)
[*]linux-aws 4.15.0-1087.92 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030079.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030079.html)
[*]linux-restricted-modules-aws 4.15.0-1087.92 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030080.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030080.html)
[*]linux-meta-aws 4.15.0.1087.89 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030081.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030081.html)
[*]cryptsetup 2:2.0.2-1ubuntu1.2 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030082.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030082.html)
[*]firefox 82.0+build2-0ubuntu0.18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030083.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030083.html)
[*]firefox 82.0+build2-0ubuntu0.18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030084.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030084.html)
[*]python-pip 9.0.1-2.3~ubuntu1.18.04.4 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030085.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030085.html)
[*]python-pip 9.0.1-2.3~ubuntu1.18.04.4 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030086.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030086.html)
[*]debootstrap 1.0.95ubuntu0.8 - [https://lists.ubuntu.com/archives/bionic-changes/2020-October/030087.html](https://lists.ubuntu.com/archives/bionic-changes/2020-October/030087.html)
[/LIST]

End of Standard Support: April 2023

***[SIZE="4"]Ubuntu 20.04 Updates[/SIZE]***

[LIST]
[*]linux-signed 5.4.0-52.57 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020876.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020876.html)
[*]linux-restricted-modules 5.4.0-52.57 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020877.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020877.html)
[*]linux 5.4.0-52.57 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020878.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020878.html)
[*]linux-meta 5.4.0.52.55 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020879.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020879.html)
[*]linux-meta-raspi 5.4.0.1022.57 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020880.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020880.html)
[*]linux-raspi 5.4.0-1022.25 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020881.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020881.html)
[*]linux_5.4.0-52.57_s390x.tar.gz - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020882.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020882.html)
[*]linux_5.4.0-52.57_amd64.tar.gz - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020883.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020883.html)
[*]linux_5.4.0-52.57_arm64.tar.gz - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020884.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020884.html)
[*]linux_5.4.0-52.57_ppc64el.tar.gz - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020885.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020885.html)

Due to excessive content these are abridged; The complete list is here: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue654#Ubuntu_20.04_Updates](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue654#Ubuntu_20.04_Updates)


[*]tomcat9 9.0.31-1ubuntu0.1 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020919.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020919.html)
[*]linux-signed-oem-5.6 5.6.0-1032.33 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020920.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020920.html)
[*]linux-restricted-modules-oem-5.6 5.6.0-1032.33 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020921.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020921.html)
[*]linux-meta-oem-5.6 5.6.0.1032.28 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020922.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020922.html)
[*]linux-oem-5.6 5.6.0-1032.33 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020923.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020923.html)
[*]firefox 82.0+build2-0ubuntu0.20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020924.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020924.html)
[*]firefox 82.0+build2-0ubuntu0.20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020925.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020925.html)
[*]livecd-rootfs 2.664.8 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020926.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020926.html)
[*]linux-oem-5.6_5.6.0-1032.33_amd64.tar.gz - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020927.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020927.html)
[*]debootstrap 1.0.118ubuntu1.3 - [https://lists.ubuntu.com/archives/focal-changes/2020-October/020928.html](https://lists.ubuntu.com/archives/focal-changes/2020-October/020928.html)
[/LIST]

End of Standard Support: April 2025

***[SIZE="4"]Ubuntu 20.10 Updates[/SIZE]***

[LIST]
[*]freetype 2.10.2+dfsg-3ubuntu1 - [https://lists.ubuntu.com/archives/groovy-changes/2020-October/012283.html](https://lists.ubuntu.com/archives/groovy-changes/2020-October/012283.html)
[*]firefox 82.0+build2-0ubuntu0.20.10.1 - [https://lists.ubuntu.com/archives/groovy-changes/2020-October/012284.html](https://lists.ubuntu.com/archives/groovy-changes/2020-October/012284.html)
[*]firefox 82.0+build2-0ubuntu0.20.10.1 - [https://lists.ubuntu.com/archives/groovy-changes/2020-October/012285.html](https://lists.ubuntu.com/archives/groovy-changes/2020-October/012285.html)
[*]tzdata 2020d-1ubuntu1 - [https://lists.ubuntu.com/archives/groovy-changes/2020-October/012286.html](https://lists.ubuntu.com/archives/groovy-changes/2020-October/012286.html)
[*]pulseaudio 1:13.99.2-1ubuntu2 - [https://lists.ubuntu.com/archives/groovy-changes/2020-October/012287.html](https://lists.ubuntu.com/archives/groovy-changes/2020-October/012287.html)
[*]apt 2.1.11 - [https://lists.ubuntu.com/archives/groovy-changes/2020-October/012288.html](https://lists.ubuntu.com/archives/groovy-changes/2020-October/012288.html)
[*]google-guest-agent 20200617.00-0ubuntu6 - [https://lists.ubuntu.com/archives/groovy-changes/2020-October/012289.html](https://lists.ubuntu.com/archives/groovy-changes/2020-October/012289.html)
[*]debootstrap 1.0.123ubuntu1.1 - [https://lists.ubuntu.com/archives/groovy-changes/2020-October/012290.html](https://lists.ubuntu.com/archives/groovy-changes/2020-October/012290.html)
[/LIST]

End Of Lie: July 2021

**[SIZE="5"]Subscribe[/SIZE]**

Get your copy of the Ubuntu Weekly Newsletter delivered each week to you via email at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-news](https://lists.ubuntu.com/mailman/listinfo/ubuntu-news)

Or follow us via our various social media presences:

[LIST]
[*][https://www.facebook.com/UbuntuWeeklyNewsletter](https://www.facebook.com/UbuntuWeeklyNewsletter)
[*][https://twitter.com/Ubuntu_News](https://twitter.com/Ubuntu_News)
[/LIST]

**[SIZE="5"]Archive[/SIZE]**

You can always find older Ubuntu Weekly Newsletter issues at: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Archive](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Archive)

**[SIZE="5"]Further News[/SIZE]**

As always you can find more Ubuntu news and announcements at:

[LIST]
[*][https://blog.ubuntu.com/](https://blog.ubuntu.com/)
[*][http://fridge.ubuntu.com/](http://fridge.ubuntu.com/)
[*][https://www.reddit.com/r/Ubuntu/](https://www.reddit.com/r/Ubuntu/)
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
[*]And many others
[/LIST]

**[SIZE="5"]Glossary of Terms[/SIZE]**

Other acronyms can be found at: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/glossary](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/glossary)

**[SIZE="5"]Get Involved[/SIZE]**

The Ubuntu community consists of individuals and teams, working on different aspects of the distribution, giving advice and technical support, and helping to promote Ubuntu to a wider audience. No contribution is too small, and anyone can help. It's your chance to get in on all the community fun associated with developing and promoting Ubuntu. More on this at: [https://community.ubuntu.com/contribute/](https://community.ubuntu.com/contribute/)

Or get involved with the Ubuntu Weekly Newsletter team! We always need summary writers and editors, if you're interested, learn more at: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Join](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Join)

**[SIZE="5"]Feedback[/SIZE]**

This document is maintained by the Ubuntu Weekly News Team. If you have a story idea or suggestions for the Weekly Newsletter, join the Ubuntu News Team mailing list at [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team) and submit it. Ideas can also be added to the wiki at [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas). If you'd like to contribute to a future issue of the Ubuntu Weekly Newsletter, please feel free to edit the appropriate wiki page. If you have any technical support questions, please check [https://community.ubuntu.com/help-information/](https://community.ubuntu.com/help-information/) for more information on where to get help.

[IMG]https://fridge.ubuntu.com/wp-content/uploads/2015/05/ab28/CCL.png[/IMG] Except where otherwise noted, this issue of the Ubuntu Weekly Newsletter is licensed under a [Creative Commons Attribution ShareAlike 3.0 License]("https://creativecommons.org/licenses/by-sa/3.0/")

---

