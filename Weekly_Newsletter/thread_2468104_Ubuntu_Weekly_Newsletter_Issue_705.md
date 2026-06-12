---
title: "Ubuntu Weekly Newsletter Issue 705"
date: 2021-10-18
forum: Weekly Newsletter
---

### Post by Bashing-om on 2021-10-18
[IMG]https://fridge.ubuntu.com/wp-content/uploads/2020/02/c9d7/header.png[/IMG]

Welcome to the Ubuntu Weekly Newsletter, Issue 705 for the week of October 10 - 16, 2021. The wiki page of this issue is available [here]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue705").

**[SIZE="5"]In this Issue[/SIZE]**

[LIST]
[*]Ubuntu 21.10 (Impish Indri) released
[*]Attention: ZFS kernel panic mitigation
[*]Ubuntu Stats
[*]Hot in Support
[*]LoCo Events
[*]Ubuntu Community stand at FOSDEM 2022
[*]Canonical & Ubuntu at Nvidia GTC 2021
[*]Jammy Jellyfish Release Notes
[*]Other Community News
[*]Ubuntu Cloud News
[*]Canonical News
[*]In the Blogosphere
[*]Featured Audio and Video
[*]Meeting Reports
[*]Upcoming Meetings and Events
[*]Updates and Security for 18.04, 20.04, 21.04, and 21.10
[*]And much more!
[/LIST]

**[SIZE="5"]General Community News[/SIZE]**

***[SIZE="4"]Ubuntu 21.10 (Impish Indri) released[/SIZE]***

&#321;ukasz 'si2100' Zemczak on behalf of the Ubuntu Release team announces that Ubuntu 21.10 (Impish Indri) has been released. Outlining some of the newer features found in Ubuntu Desktop 21.10 and Ubuntu Server 21.10, many links are provided. Additional links are provided for more details, including where to download the new release.

[https://lists.ubuntu.com/archives/ubuntu-announce/2021-October/000274.html](https://lists.ubuntu.com/archives/ubuntu-announce/2021-October/000274.html)

This release was widely covered, the following is a collection of articles selected by our editors:
[LIST]
[*]Ubuntu 21.10 has landed - [https://ubuntu.com/blog/ubuntu-21-10-has-landed](https://ubuntu.com/blog/ubuntu-21-10-has-landed)
[*]Ubuntu 21.10: What’s New? - [https://www.omgubuntu.co.uk/2021/10/ubuntu-21-10-whats-new-video](https://www.omgubuntu.co.uk/2021/10/ubuntu-21-10-whats-new-video)
[*]Ubuntu 21.10 Official Flavors Released, Here’s What’s New - [https://9to5linux.com/ubuntu-21-10-official-flavors-released-heres-whats-new](https://9to5linux.com/ubuntu-21-10-official-flavors-released-heres-whats-new)
[*]Ubuntu 21.10 Released With GNOME 40 Desktop, Many Underlying Improvements - [https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-21.10](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-21.10)
[*]Ubuntu 21.10 is Now Available to Download - [https://www.omgubuntu.co.uk/2021/10/ubuntu-21-10-is-now-available-to-download](https://www.omgubuntu.co.uk/2021/10/ubuntu-21-10-is-now-available-to-download)
[*]Canonical Releases Ubuntu Linux 21.10 Impish Indri - [https://linux.slashdot.org/story/21/10/14/2013235/canonical-releases-ubuntu-linux-2110-impish-indri](https://linux.slashdot.org/story/21/10/14/2013235/canonical-releases-ubuntu-linux-2110-impish-indri)
[*]The newest Ubuntu Linux, Impish Indri, arrives - [https://www.zdnet.com/article/the-newest-ubuntu-linux-impish-indri-arrives/#ftag=RSSbaffb68](https://www.zdnet.com/article/the-newest-ubuntu-linux-impish-indri-arrives/#ftag=RSSbaffb68)
[*]Ubuntu 21.10 brings GNOME 40 debut and a focus on devs -https://www.theregister.com/2021/10/14/ubuntu_21_10/
[*]You Can Now Upgrade Ubuntu 21.04 to Ubuntu 21.10, Here’s How -https://9to5linux.com/you-can-now-upgrade-ubuntu-21-04-to-ubuntu-21-10-heres-how
[*]Ubuntu 21.10 “Impish Indri” Is Now Available for Download, This Is What’s New - [https://9to5linux.com/ubuntu-21-10-impish-indri-is-now-available-for-download-this-is-whats-new](https://9to5linux.com/ubuntu-21-10-impish-indri-is-now-available-for-download-this-is-whats-new)
[*]Ubuntu 21.10 is Now Available to Download - [https://www.omgubuntu.co.uk/2021/10/ubuntu-21-10-is-now-available-to-download](https://www.omgubuntu.co.uk/2021/10/ubuntu-21-10-is-now-available-to-download)
[*]Ubuntu 21.10 Released - [https://www.ghacks.net/2021/10/16/ubuntu-21-10-review/](https://www.ghacks.net/2021/10/16/ubuntu-21-10-review/)
[*]Ubuntu 21.10 “Impish Indri” Available To Download - [https://www.linuxandubuntu.com/home/ubuntu-21-10-impish-indri-released](https://www.linuxandubuntu.com/home/ubuntu-21-10-impish-indri-released)
[/LIST]

Interested in the flavors? Release announcements as follows:
[LIST]
[*]Ubuntu MATE 21.10 Release Notes - [https://ubuntu-mate.org/blog/ubuntu-mate-impish-indri-final-release/](https://ubuntu-mate.org/blog/ubuntu-mate-impish-indri-final-release/)
[*]Ubuntu Budgie 21.10 Released! - [https://ubuntubudgie.org/2021/10/ubuntu-budgie-21-10-released/](https://ubuntubudgie.org/2021/10/ubuntu-budgie-21-10-released/)
[*]Lubuntu 21.10 (Impish Indri) Released! - [https://lubuntu.me/impish-released/](https://lubuntu.me/impish-released/)
[*]Xubuntu 21.10 released! - [https://xubuntu.org/news/xubuntu-21-10-released/](https://xubuntu.org/news/xubuntu-21-10-released/)
[*]Kubuntu 21.10 Impish Indri Released - [https://kubuntu.org/news/kubuntu-21-10-impish-indri-released/](https://kubuntu.org/news/kubuntu-21-10-impish-indri-released/)
[*]Ubuntu Studio 21.10 Released - [https://ubuntustudio.org/2021/10/ubuntu-studio-21-10-released/](https://ubuntustudio.org/2021/10/ubuntu-studio-21-10-released/)
[/LIST]

***[SIZE="4"]Attention: ZFS kernel panic mitigation[/SIZE]***

"The version of the ZFS driver included in the 5.13.0-19 kernel contains a bug that can result in filesystem corruption. Users of ZFS are advised to wait until the first Stable Release Update of the kernel in 21.10 before upgrading." Trent Lloyd's long standing bug report of the ZFS kernel panic is mitigated with the 5.13.0-20 impish-proposed kernel.

[https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1906476](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1906476)

**[SIZE="5"]Ubuntu Stats[/SIZE]**

***[SIZE="4"]Bug Stats[/SIZE]***

[LIST]
[*]Open: 137701 (+118)
[*]Critical: 322 (0)
[*]Unconfirmed: 68890 (+71)
[/LIST]

As always, the Bug Squad needs more help. If you want to get started, please see: [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

***[SIZE="4"]Translations[/SIZE]***

[LIST]
[*]Ukrainian: 88.02% (38771/1084)
[*]German: 86.90% (42394/126)
[*]French: 81.44% (60036/7175)
[*]Spanish: 80.79% (62142/4375)
[*]Swedish: 77.37% (73233/969)
[/LIST]

**[SIZE="5"]Hot in Support[/SIZE]**

***[SIZE="4"]Ask Ubuntu Top 5 Questions[/SIZE]***

[LIST]
[*]Can Google Drive desktop be used on Ubuntu? - [https://askubuntu.com/questions/1368874/can-google-drive-desktop-be-used-on-ubuntu](https://askubuntu.com/questions/1368874/can-google-drive-desktop-be-used-on-ubuntu)
[*]How to remove Snap completely without losing Firefox? - [https://askubuntu.com/questions/1369159/how-to-remove-snap-completely-without-losing-firefox](https://askubuntu.com/questions/1369159/how-to-remove-snap-completely-without-losing-firefox)
[*]Error using cURL on the WhatsApp web - [https://askubuntu.com/questions/1368677/error-using-curl-on-the-whatsapp-web](https://askubuntu.com/questions/1368677/error-using-curl-on-the-whatsapp-web)
[*]Installing software to specific locations? - [https://askubuntu.com/questions/1369329/installing-software-to-specific-locations](https://askubuntu.com/questions/1369329/installing-software-to-specific-locations)
[*]I do not know how to install a tar.gz file - [https://askubuntu.com/questions/1369038/i-do-not-know-how-to-install-a-tar-gz-file](https://askubuntu.com/questions/1369038/i-do-not-know-how-to-install-a-tar-gz-file)
[/LIST]

Ask (and answer!) questions at: [https://askubuntu.com/](https://askubuntu.com/)

***[SIZE="4"]Ubuntu Forums Top 5 Threads[/SIZE]***

[LIST]
[*]apache php problem - [https://ubuntuforums.org/showthread.php?t=2467987](https://ubuntuforums.org/showthread.php?t=2467987)
[*]12.04lts upgrade - [https://ubuntuforums.org/showthread.php?t=2467886](https://ubuntuforums.org/showthread.php?t=2467886)
[*]problems with mpv of late ... - [https://ubuntuforums.org/showthread.php?t=2467978](https://ubuntuforums.org/showthread.php?t=2467978)
[*]Stuck in Busybox because sda6 can't mount - [https://ubuntuforums.org/showthread.php?t=2467938](https://ubuntuforums.org/showthread.php?t=2467938)
[*]Permissions for Jellyfin Service account in Ubuntu - [https://ubuntuforums.org/showthread.php?t=2467961](https://ubuntuforums.org/showthread.php?t=2467961)
[/LIST]

Find more support at: [https://ubuntuforums.org/](https://ubuntuforums.org/)

**[SIZE="5"]LoCo Events[/SIZE]**

The following LoCo team events are currently scheduled in the next two weeks:

[LIST]
[*]Encontro Ubuntu-pt @ Sintra // Lançamento Impish Indri, Ubuntu Portugal: [http://loco.ubuntu.com/events/ubuntu-pt/4161-encontro-ubuntu-pt-sintra-lan%C3%A7amento-impish-indri/](http://loco.ubuntu.com/events/ubuntu-pt/4161-encontro-ubuntu-pt-sintra-lan%C3%A7amento-impish-indri/)
[*]Ubuntu Hour - Venezuela, Ubuntu Venezuela Team: [http://loco.ubuntu.com/events/ubuntu-ve/4157-ubuntu-hour-venezuela/](http://loco.ubuntu.com/events/ubuntu-ve/4157-ubuntu-hour-venezuela/)
[*]Virtual Tempe Ubuntu Hour, Arizona LoCo Team: [http://loco.ubuntu.com/events/ubuntu-arizona/4149-virtual-tempe-ubuntu-hour/](http://loco.ubuntu.com/events/ubuntu-arizona/4149-virtual-tempe-ubuntu-hour/)
[/LIST]

Looking beyond the next two weeks? Visit the LoCo Team Portal to browse upcoming events around the world: [http://loco.ubuntu.com/events/](http://loco.ubuntu.com/events/)

**[SIZE="5"]The Hub[/SIZE]**

***[SIZE="4"]Ubuntu Community stand at FOSDEM 2022[/SIZE]***

Diogo Miguel Constantino Dos Santos talks about FOSDEM 2022, and the Ubuntu Community's involvement in prior years, and is proposing a FOSDEM stand/booth for Ubuntu (including Community), Canonical, flavors, and UBports Community. This post is asking for opinions, and a call out for people willing to help.

[https://discourse.ubuntu.com/t/ubuntu-community-stand-at-fosdem-2022/24599](https://discourse.ubuntu.com/t/ubuntu-community-stand-at-fosdem-2022/24599)

***[SIZE="4"]Canonical & Ubuntu at Nvidia GTC 2021[/SIZE]***

Daria Kolarczyk tells us Canonical is a proud sponsor of the Nvidia GTC event which will be held on 8-11 November 2021. We are told Canonical will host two sessions; one co-hosted with Nvidia on "implementing a low-latency streaming solution with Android Cloud" and another on "using open-source tools to build your MLOps infrastructure". Details are provided (including RSVP links).

[https://discourse.ubuntu.com/t/canonical-ubuntu-at-nvidia-gtc-2021/24671](https://discourse.ubuntu.com/t/canonical-ubuntu-at-nvidia-gtc-2021/24671)

***[SIZE="4"]Jammy Jellyfish Release Notes[/SIZE]***

&#321;ukasz 'sil2100' Zemczak of the Ubuntu Release Team has started the release notes for Ubuntu 22.04 LTS (Jammy Jellyfish). This is a live document that will be added to during the development cycle of the next long-term-support release of Ubuntu.

[https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668](https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668)

**[SIZE="5"]Other Community News[/SIZE]**

***[SIZE="4"]git-ubuntu rich history beta[/SIZE]***

Robie Basak informs users & contributors that git-ubuntu can now "accept rich history directly from any uploader". The CLI is in beta thus feedback will be appreciated, and it may change. A brief set of instructions and caveats are provided, if you'd like to use it to make submissions.

[https://lists.ubuntu.com/archives/ubuntu-devel/2021-October/041649.html](https://lists.ubuntu.com/archives/ubuntu-devel/2021-October/041649.html)

**[SIZE="5"]Ubuntu Cloud News[/SIZE]**

[LIST]
[*]SUSE Enterprise Storage: What next? - [https://ubuntu.com/blog/suse-enterprise-storage](https://ubuntu.com/blog/suse-enterprise-storage)
[*]Ubuntu Server 21.10: What’s new? - [https://ubuntu.com/blog/ubuntu-server-21-10](https://ubuntu.com/blog/ubuntu-server-21-10)
[/LIST]

**[SIZE="5"]Canonical News[/SIZE]**

[LIST]
[*]OpenStack Xena for Ubuntu 21.10 and Ubuntu 20.04 LTS - [https://wrestlingpenguins.wordpress.com/2021/10/15/openstack-xena-for-ubuntu-21-10-and-ubuntu-20-04-lts/](https://wrestlingpenguins.wordpress.com/2021/10/15/openstack-xena-for-ubuntu-21-10-and-ubuntu-20-04-lts/)
[*]DISA-STIG on Ubuntu - [https://ubuntu.com/security/disa-stig](https://ubuntu.com/security/disa-stig)
[*]Top 6 projects from our Hackathon - [https://ubuntu.com/blog/top-6-projects-from-our-hackathon](https://ubuntu.com/blog/top-6-projects-from-our-hackathon)
[*]Data centre networking: SDN fundamentals - [https://ubuntu.com/blog/data-centre-networking-sdn-fundamentals](https://ubuntu.com/blog/data-centre-networking-sdn-fundamentals)
[*]Mir 2.5, incorporating new features to improve the development of embedded graphic applications - [https://ubuntu.com/blog/mir-2-5-enhancing-digital-signage-and-smart-screen-development](https://ubuntu.com/blog/mir-2-5-enhancing-digital-signage-and-smart-screen-development)
[*]Driving innovation in autonomous mobile robots – University of Hawaii hits Indy 500 - [https://ubuntu.com/blog/driving-innovation-in-autonomous-mobile-robots-university-of-hawaii-hits-indy-500](https://ubuntu.com/blog/driving-innovation-in-autonomous-mobile-robots-university-of-hawaii-hits-indy-500)
[/LIST]

**[SIZE="5"]In the Blogosphere[/SIZE]**

***[SIZE="4"]KDE Plasma 5.23 Released In Marking 25 Years Of KDE[/SIZE]***

Michael Larabel reports on the KDE Plasma 5.23 release which is also known as the KDE 25th Anniversary Edition. Some of the highlights of the new KDE Plasma stable update are provided, including an embedded youtube video link and KDE.org announcement links.

[https://www.phoronix.com/scan.php?page=news_item&px=KDE-Plasma-5.23-Released](https://www.phoronix.com/scan.php?page=news_item&px=KDE-Plasma-5.23-Released)

***[SIZE="4"]NVIDIA 495 Linux Beta Driver Released With GBM Support[/SIZE]***

Michael Larabel tells us that NVIDIA 495.29.05 is out today and includes GBM (Generic Buffer Manager) API support improving Wayland support and making it more compatible with Wayland software. We are told of various features in this beta, with links for more details.

[https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-495.29.05-Linux](https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-495.29.05-Linux)

***[SIZE="4"]Ubuntu 22.04 LTS Codename is a Jolly Good Choice[/SIZE]***

Joey Sneddon informs us that the codename for Ubuntu 22.04 LTS is 'Jammy Jellyfish'. With some ideas as to what we may find in the release, we are reminded of prior codenames and how it may/may-not fit a pattern. We are assured he'll provide us with more details as they're known.

[https://www.omgubuntu.co.uk/2021/10/ubuntu-22-04-codename-jammy-jellyfish](https://www.omgubuntu.co.uk/2021/10/ubuntu-22-04-codename-jammy-jellyfish)

**[SIZE="5"]Featured Audio and Video[/SIZE]**

***[SIZE="4"]Ubuntu OnAir: Ubuntu Community Chat at Grace Hopper Celebration 2021[/SIZE]***

"In this video, live-streamed and recorded at the virtual Grace Hopper Celebration 2021, Monica from the Community Team chats with two long-standing women in the Ubuntu community, Elizabeth K. Joseph and Valorie Zimmerman. They share their Ubuntu origin stories and how contributing to open source has shaped their lives and careers."

[https://www.youtube.com/watch?v=q7dM1oACJT0](https://www.youtube.com/watch?v=q7dM1oACJT0)

***[SIZE="4"]Ubuntu OnAir: Community Office Hours | Impish Indri Party![/SIZE]***

"It's a celebration for 21.10, Impish Indri! There are chats from team members about the release, special musical guest(s), games, and plenty of chances to hang out with other members of the Ubuntu community and celebrate yet another release!"

[https://www.youtube.com/watch?v=8ZTI7kdPFLc](https://www.youtube.com/watch?v=8ZTI7kdPFLc)

***[SIZE="4"]Ubuntu Security Podcast: Episode 134[/SIZE]***

"It’s release week! As Ubuntu 21.10 Impish Indri is released we take a look at some of the new security features it brings, plus we cover security updates for containerd, MongoDB, Mercurial, docker.io and more."

[https://ubuntusecuritypodcast.org/episode-134/](https://ubuntusecuritypodcast.org/episode-134/)

***[SIZE="4"]Ubuntu Portugal Podcast: 164 Hacktoberfest II – Pedro Silva[/SIZE]***

"No segundo episódio de Outubro, e continuando a nossa série de 4 episódios dedicados a pessoas e projectos ligados ao Hacktoberfest, fiquem com a experiência do Pedro Silva, que nos contou o que já fez em edições anteriores e o que pretende realizar na edição 2021."

[https://podcastubuntuportugal.org/ep-164-hacktoberfest-ii-pedro-silva/](https://podcastubuntuportugal.org/ep-164-hacktoberfest-ii-pedro-silva/)

***[SIZE="4"]Linux Action News 210[/SIZE]***

"Apple M1 Linux development reaches a key milestone and boots a usable desktop; Ubuntu reveals a new product, and the secret SUSE project that leaked this week.
Plus, the essential RISC-V code landing in the Linux kernel."

[https://linuxactionnews.com/210](https://linuxactionnews.com/210)

***[SIZE="4"]Ubuntu 21.10 - Full Review[/SIZE]***

"Ubuntu 21.10 finally features the GNOME 40 desktop, better Wayland support, and more. In this video, I'll give you my thoughts on "Impish Idri" and we'll go over some of the new features. I'll talk about the installation process, Wayland changes, performance, and more!"

[https://www.youtube.com/watch?v=dbVj-xQIJ0I](https://www.youtube.com/watch?v=dbVj-xQIJ0I)

**[SIZE="5"]Meeting Reports[/SIZE]**

[LIST]
[*]Ubuntu +1 Maintenance Reports - [https://lists.ubuntu.com/archives/ubuntu-devel/2021-October/date.html](https://lists.ubuntu.com/archives/ubuntu-devel/2021-October/date.html)
[*]Desktop Team Updates - Monday 18th October 2021 - [https://discourse.ubuntu.com/t/desktop-team-updates-monday-18th-october-2021/24599](https://discourse.ubuntu.com/t/desktop-team-updates-monday-18th-october-2021/24599)
[/LIST]

**[SIZE="5"]Upcoming Meetings and Events[/SIZE]**

[LIST]
[*]Developer Membership Board: Mon, October 18, 3pm – 4pm
[*]Ubuntu Membership Board: Wed, October 20, 12pm – 1pm
[*]Ubuntu Backporters: Wed, October 20, 4pm – 5pm
[*]Community Council: Wed, October 20, 11pm – Thu, October 21, 12am
[/LIST]

Times shown are UTC. For more details and farther dates please visit: [https://fridge.ubuntu.com/calendars/](https://fridge.ubuntu.com/calendars/)

**[SIZE="5"]Updates and Security for 18.04, 20.04, 21.04, and 21.10[/SIZE]**

***[SIZE="4"]Security Updates[/SIZE]***

[LIST]
[*][USN-5078-3] Squashfs-Tools vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2021-October/006235.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2021-October/006235.html)
[*][USN-5091-3] Linux kernel (Azure) regression - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2021-October/006236.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2021-October/006236.html)
[/LIST]

***[SIZE="4"]Ubuntu 18.04 Updates[/SIZE]***

[LIST]
[*]qemu 1:2.11+dfsg-1ubuntu7.38 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035941.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035941.html)
[*]linux-signed-azure-5.4 5.4.0-1061.64~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035942.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035942.html)
[*]linux-restricted-modules-azure-5.4 5.4.0-1061.64~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035943.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035943.html)
[*]linux-restricted-signatures-azure-5.4 5.4.0-1061.64~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035944.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035944.html)
[*]linux-azure-5.4 5.4.0-1061.64~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035945.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035945.html)
[*]linux-meta-azure-5.4 5.4.0.1061.41 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035946.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035946.html)
[*]linux-restricted-modules-aws 4.15.0-1113.120 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035947.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035947.html)
[*]linux-aws 4.15.0-1113.120 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035948.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035948.html)
[*]linux-meta-aws 4.15.0.1113.116 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035949.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035949.html)
[*]linux-restricted-signatures-aws 4.15.0-1113.120 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035950.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035950.html)
[*]linux-azure-5.4 5.4.0-1061.64~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035951.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035951.html)
[*]linux-signed-azure-5.4 5.4.0-1061.64~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035952.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035952.html)
[*]linux-restricted-modules-azure-5.4 5.4.0-1061.64~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035953.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035953.html)
[*]linux-restricted-signatures-azure-5.4 5.4.0-1061.64~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035954.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035954.html)
[*]linux-meta-azure-5.4 5.4.0.1061.41 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035955.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035955.html)
[*]linux-restricted-modules-azure-5.4 5.4.0-1062.65~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035956.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035956.html)
[*]linux-azure-5.4 5.4.0-1062.65~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035957.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035957.html)
[*]linux-meta-azure-5.4 5.4.0.1062.42 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035958.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035958.html)
[*]linux-signed-azure-5.4 5.4.0-1062.65~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035959.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035959.html)
[*]linux-restricted-signatures-azure-5.4 5.4.0-1062.65~18.04.1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035960.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035960.html)
[*]augeas 1.10.1-2ubuntu1 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035961.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035961.html)
[*]nova 2:17.0.13-0ubuntu4 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035962.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035962.html)
[*]dnsmasq 2.79-1ubuntu0.5 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035963.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035963.html)
[*]cloud-init 21.3-1-g6803368d-0ubuntu1~18.04.4 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035964.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035964.html)
[*]debootstrap 1.0.95ubuntu0.10 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035965.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035965.html)
[*]distro-info-data 0.37ubuntu0.13 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035966.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035966.html)
[*]distro-info-data 0.37ubuntu0.13 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035967.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035967.html)
[*]distro-info-data 0.37ubuntu0.13 - [https://lists.ubuntu.com/archives/bionic-changes/2021-October/035968.html](https://lists.ubuntu.com/archives/bionic-changes/2021-October/035968.html)
[/LIST]

End of Standard Support: April 2023

***[SIZE="4"]Ubuntu 20.04 Updates[/SIZE]***

[LIST]
[*]linux-restricted-modules-azure-5.11 5.11.0-1019.20~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028039.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028039.html)
[*]linux-azure-5.11 5.11.0-1019.20~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028038.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028038.html)
[*]virtualbox-hwe 6.1.26-dfsg-3~ubuntu1.20.04.2 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028040.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028040.html)
[*]virtualbox 6.1.26-dfsg-3~ubuntu1.20.04.2 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028041.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028041.html)
[*]qemu 1:4.2-3ubuntu6.18 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028042.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028042.html)
[*]neutron 2:16.4.1-0ubuntu2 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028043.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028043.html)
[*]s390-tools 2.12.0-0ubuntu3.4 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028044.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028044.html)
[*]s390-tools-signed 2.12.0-0ubuntu3.4 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028045.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028045.html)
[*]netplan.io 0.103-0ubuntu5~20.04.2 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028046.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028046.html)
[*]oem-sutton.simon-baird-meta 20.04~ubuntu3 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028047.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028047.html)
[*]oem-sutton.newell-cade-meta 20.04~ubuntu3 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028048.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028048.html)
[*]linux-signed-azure 5.4.0-1061.64 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028050.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028050.html)
[*]linux-restricted-modules-azure 5.4.0-1061.64 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028049.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028049.html)
[*]linux-azure 5.4.0-1061.64 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028051.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028051.html)
[*]linux-restricted-signatures-azure 5.4.0-1061.64 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028052.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028052.html)
[*]linux-meta-azure 5.4.0.1061.59 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028053.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028053.html)
[*]linux-restricted-modules-oem-5.10 5.10.0-1050.52 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028054.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028054.html)
[*]linux-meta-oem-5.10 5.10.0.1050.52 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028055.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028055.html)
[*]linux-oem-5.10 5.10.0-1050.52 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028056.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028056.html)
[*]linux-signed-oem-5.10 5.10.0-1050.52 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028058.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028058.html)
[*]linux-restricted-signatures-oem-5.10 5.10.0-1050.52 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028057.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028057.html)
[*]linux-meta-intel-5.13 5.13.0.1007.8 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028059.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028059.html)
[*]linux-intel-5.13 5.13.0-1007.7 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028060.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028060.html)
[*]linux-signed-intel-5.13 5.13.0-1007.7 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028061.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028061.html)
[*]linux-restricted-modules-azure 5.4.0-1062.65 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028066.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028066.html)
[*]linux-meta-azure 5.4.0.1062.60 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028062.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028062.html)
[*]linux-azure 5.4.0-1062.65 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028063.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028063.html)
[*]linux-signed-azure 5.4.0-1062.65 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028064.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028064.html)
[*]linux-restricted-signatures-azure 5.4.0-1062.65 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028065.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028065.html)
[*]linux-firmware 1.187.19 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028067.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028067.html)
[*]squashfs-tools 1:4.4-1ubuntu0.3 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028068.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028068.html)
[*]mesa 21.0.3-0ubuntu0.3~20.04.3 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028069.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028069.html)
[*]squashfs-tools 1:4.4-1ubuntu0.3 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028070.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028070.html)
[*]xlnx-kria-firmware 0.6~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028071.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028071.html)
[*]linux-azure 5.4.0-1061.64 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028072.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028072.html)
[*]linux-signed-azure 5.4.0-1061.64 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028073.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028073.html)
[*]linux-restricted-modules-azure 5.4.0-1061.64 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028074.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028074.html)
[*]linux-restricted-signatures-azure 5.4.0-1061.64 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028075.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028075.html)
[*]linux-meta-azure 5.4.0.1061.59 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028076.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028076.html)
[*]linux-restricted-modules-oem-5.13 5.13.0-1017.21 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028077.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028077.html)
[*]linux-oem-5.13 5.13.0-1017.21 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028078.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028078.html)
[*]linux-meta-oem-5.13 5.13.0.1017.21 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028079.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028079.html)
[*]linux-signed-oem-5.13 5.13.0-1017.21 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028081.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028081.html)
[*]linux-restricted-signatures-oem-5.13 5.13.0-1017.21 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028080.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028080.html)
[*]linux-restricted-modules-hwe-5.13 5.13.0-19.19~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028082.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028082.html)
[*]linux-signed-hwe-5.13 5.13.0-19.19~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028083.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028083.html)
[*]linux-meta-hwe-5.13 5.13.0.19.19~20.04.7 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028084.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028084.html)
[*]linux-restricted-signatures-hwe-5.13 5.13.0-19.19~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028085.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028085.html)
[*]linux-hwe-5.13 5.13.0-19.19~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028086.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028086.html)
[*]linux-signed-azure-5.11 5.11.0-1019.20~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028087.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028087.html)
[*]linux-restricted-modules-azure-5.11 5.11.0-1019.20~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028088.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028088.html)
[*]linux-restricted-signatures-azure-5.11 5.11.0-1019.20~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028089.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028089.html)
[*]linux-meta-azure-5.11 5.11.0.1019.20~20.04.18 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028090.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028090.html)
[*]linux-azure-5.11 5.11.0-1019.20~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028091.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028091.html)
[*]cloud-init 21.3-1-g6803368d-0ubuntu1~20.04.4 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028092.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028092.html)
[*]debootstrap 1.0.118ubuntu1.5 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028093.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028093.html)
[*]distro-info-data 0.43ubuntu1.9 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028094.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028094.html)
[*]distro-info-data 0.43ubuntu1.9 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028095.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028095.html)
[*]distro-info-data 0.43ubuntu1.9 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028096.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028096.html)
[*]linux-restricted-modules-azure-5.11 5.11.0-1020.21~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028097.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028097.html)
[*]linux-meta-azure-5.11 5.11.0.1020.21~20.04.19 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028098.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028098.html)
[*]linux-azure-5.11 5.11.0-1020.21~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028099.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028099.html)
[*]linux-signed-azure-5.11 5.11.0-1020.21~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028100.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028100.html)
[*]linux-restricted-signatures-azure-5.11 5.11.0-1020.21~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2021-October/028101.html](https://lists.ubuntu.com/archives/focal-changes/2021-October/028101.html)
[/LIST]

End of Standard Support: April 2025

***[SIZE="4"]Ubuntu 21.04 Updates[/SIZE]***

[LIST]
[*]qemu 1:5.2+dfsg-9ubuntu3.2 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014466.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014466.html)
[*]s390-tools 2.16.0-0ubuntu1.1 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014467.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014467.html)
[*]s390-tools-signed 2.16.0-0ubuntu1.1 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014468.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014468.html)
[*]net-snmp 5.9+dfsg-3ubuntu1.21.04.1 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014469.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014469.html)
[*]netplan.io 0.103-0ubuntu5~21.04.2 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014470.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014470.html)
[*]squashfs-tools 1:4.4-2ubuntu0.3 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014471.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014471.html)
[*]squashfs-tools 1:4.4-2ubuntu0.3 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014472.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014472.html)
[*]zfs-linux 2.0.2-1ubuntu5.3 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014473.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014473.html)
[*]cinder 2:18.1.0-0ubuntu1 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014474.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014474.html)
[*]linux-signed-azure 5.11.0-1019.20 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014475.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014475.html)
[*]linux-restricted-signatures-azure 5.11.0-1019.20 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014476.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014476.html)
[*]linux-restricted-modules-azure 5.11.0-1019.20 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014477.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014477.html)
[*]linux-meta-azure 5.11.0.1019.20 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014478.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014478.html)
[*]linux-azure 5.11.0-1019.20 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014479.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014479.html)
[*]cloud-init 21.3-1-g6803368d-0ubuntu1~21.04.4 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014480.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014480.html)
[*]debootstrap 1.0.123ubuntu6.1 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014481.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014481.html)
[*]distro-info-data 0.46ubuntu4.3 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014482.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014482.html)
[*]distro-info-data 0.46ubuntu4.3 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014483.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014483.html)
[*]distro-info-data 0.46ubuntu4.3 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014484.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014484.html)
[*]linux-restricted-modules-azure 5.11.0-1020.21 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014485.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014485.html)
[*]linux-azure 5.11.0-1020.21 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014486.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014486.html)
[*]linux-meta-azure 5.11.0.1020.21 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014487.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014487.html)
[*]linux-signed-azure 5.11.0-1020.21 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014488.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014488.html)
[*]linux-restricted-signatures-azure 5.11.0-1020.21 - [https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014489.html](https://lists.ubuntu.com/archives/hirsute-changes/2021-October/014489.html)
[/LIST]

End of life: January 2022

***[SIZE="4"]Ubuntu 21.10 Updates[/SIZE]***

[LIST]
[*]osinfo-db 0.20211013-1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007588.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007588.html)
[*]cdbs 0.4.163ubuntu2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007589.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007589.html)
[*]checkinstall 1.6.2+git20170426.d24a630-2ubuntu2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007590.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007590.html)
[*]gsmlib 1.10+20120414.gita5e5ae9a-0.5 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007591.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007591.html)
[*]sway 1.5.1-2ubuntu1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007592.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007592.html)
[*]debootstrap 1.0.124ubuntu0.1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007593.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007593.html)
[*]distro-info-data 0.51ubuntu1.1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007594.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007594.html)
[*]distro-info-data 0.51ubuntu1.1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007595.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007595.html)
[*]distro-info-data 0.51ubuntu1.1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007596.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007596.html)
[*]glm 0.9.9.8+ds-1ubuntu1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007597.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007597.html)
[*]util-linux 2.36.1-8ubuntu2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007598.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007598.html)
[*]geonkick 2.8.0-0ubuntu2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007599.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007599.html)
[*]zfs-linux 2.0.6-1ubuntu2.1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007600.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007600.html)
[*]python-esmre 0.5.2-1build3 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007601.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007601.html)
[*]python-dnaio 0.5.0-1build1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007602.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007602.html)
[*]python-dmidecode 3.12.2-11build3 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007603.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007603.html)
[*]python-djvulibre 0.8.4-3build4 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007604.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007604.html)
[*]python-datrie 0.8.2-1build2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007605.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007605.html)
[*]python-cytoolz 0.11.0-1build2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007606.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007606.html)
[*]python-cymem 2.0.2-1build5 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007607.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007607.html)
[*]python-cwcwidth 0.1.4-1build1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007608.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007608.html)
[*]python-cmarkgfm 0.4.2-1build4 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007609.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007609.html)
[*]python-argon2 18.3.0-2build3 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007610.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007610.html)
[*]python-alignlib 0.1.1+dfsg-1.1build3 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007611.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007611.html)
[*]python-admesh 0.98.9-2build4 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007612.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007612.html)
[*]python-acora 2.2-1.3build2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007613.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007613.html)
[*]pytaglib 0.3.6+dfsg-2build13 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007614.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007614.html)
[*]pysvn 1.9.12-2build1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007615.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007615.html)
[*]pystemmer 2.0.1+dfsg-2build1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007616.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007616.html)
[*]pyside2 5.15.2-1build1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007620.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007620.html)
[*]pyode 1.2.0.dev15-3build2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007617.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007617.html)
[*]py-radix 0.10.0-3build4 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007621.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007621.html)
[*]pykafka 2.7.0-1build5 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007618.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007618.html)
[*]pymssql 2.1.4+dfsg-3build5 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007627.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007627.html)
[*]pyliblo 0.10.0-4build4 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007628.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007628.html)
[*]pygccjit 0.4-11build2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007622.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007622.html)
[*]pygobject 3.40.1-1build2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007629.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007629.html)
[*]pygame-sdl2 7.4.2-1build2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007623.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007623.html)
[*]pyfuse3 3.2.0-2build2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007624.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007624.html)
[*]pycson 0.8-1build2 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007625.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007625.html)
[*]pycares 3.1.1-1build4 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007619.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007619.html)
[*]pyclipper 1.2.1-1build1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007626.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007626.html)
[*]pybik 3.0-3.1build1 - [https://lists.ubuntu.com/archives/impish-changes/2021-October/007630.html](https://lists.ubuntu.com/archives/impish-changes/2021-October/007630.html)
[/LIST]

End of life: July 2022

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
[*][https://ubuntu.com/blog/](https://ubuntu.com/blog/)
[*][https://fridge.ubuntu.com/](https://fridge.ubuntu.com/)
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

