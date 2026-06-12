---
title: "Ubuntu Weekly Newsletter Issue 854"
date: 2024-08-26
forum: Weekly Newsletter
---

### Post by Bashing-om on 2024-08-26
[IMG]https://fridge.ubuntu.com/wp-content/uploads/2020/02/c9d7/header.png[/IMG]

Welcome to the Ubuntu Weekly Newsletter, Issue 854 for the week of August 18 - 24, 2024.
The Discourse post of this issue is available [ here]("https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-854/47301").

**[SIZE="5"]In this Issue[/SIZE]**

[LIST]
[*]“Something has gone seriously wrong,” dual-boot systems warn after Microsoft update
[*]SRU announcement
[*]Call for nominations: Ubuntu Community Council
[*]Welcome New Members and Developers
[*]Ubuntu Stats
[*]Hot in Support
[*]Weekly Meeting Reports
[*]Starcraft Clinic 2024-Aug-16
[*]Midwest Superfest and Software Freedom Day 2024
[*]UbuCon Asia 2024
[*]UbuCon Korea 2024 has wrapped up with 151 attendees this year!
[*]LoCo Events
[*]Ubuntu WSL channel on Matrix
[*]The CMA wants your comments on web apps
[*]Other Community News
[*]Canonical News
[*]In the Blogosphere
[*]Featured Audio and Video
[*]Meeting Reports
[*]Upcoming Meetings and Events
[*]Updates and Security for Ubuntu 20.04, 22.04, and 24.04
[*]And much more!
[/LIST]

**[SIZE="5"]General Community News[/SIZE]**

**[SIZE="4"]“Something has gone seriously wrong,” dual-boot systems warn after Microsoft update[/SIZE]**

Dan Goodin reports on a windows fix to a two year old vulnerability that had some unforeseen issues. With details of the problem, and Microsoft's fix; a fix that didn't work for many people & thus left systems that failed to boot. We're walked through this story, and the consequences, before being given steps for a workaround with mention of some of the problems in the secure-boot approach.

[https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/](https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/)
[LIST]
[*]Microsoft’s latest security update has ruined dual-boot Windows and Linux PCs - [https://www.theverge.com/2024/8/21/24225108/microsoft-security-update-windows-linux-dual-boot-errors](https://www.theverge.com/2024/8/21/24225108/microsoft-security-update-windows-linux-dual-boot-errors)
[*]SBAT self-check failed: Mitigating the impact of shim 15.7 revocation on the Ubuntu boot process for devices running Windows - [https://discourse.ubuntu.com/t/sbat-self-check-failed-mitigating-the-impact-of-shim-15-7-revocation-on-the-ubuntu-boot-process-for-devices-running-windows/47378](https://discourse.ubuntu.com/t/sbat-self-check-failed-mitigating-the-impact-of-shim-15-7-revocation-on-the-ubuntu-boot-process-for-devices-running-windows/47378)
[*]Ubuntu SBAT reset media [https://github.com/canonical/sbat-reset-media](https://github.com/canonical/sbat-reset-media)
[/LIST]

**[SIZE="4"]SRU announcement[/SIZE]**

Roxana Nicolescu alerts readers that the SRU (Stable Release Updates) cycle 2024.09.02 will be skipped due to infrastructure change. We're told the next SRU cycle will start when infrastructure is 'back online' which is expected start of October, with known details provided & more to come. We're also told this won't impact critical security fixes during the current cycle.

[https://lists.ubuntu.com/archives/kernel-team/2024-August/152944.html](https://lists.ubuntu.com/archives/kernel-team/2024-August/152944.html)
[LIST]
[*]Ubuntu Will Be Skipping Non-Critical Linux Kernel Updates For September - [https://www.phoronix.com/news/Ubuntu-Skipping-Kernel-SRU-Fix](https://www.phoronix.com/news/Ubuntu-Skipping-Kernel-SRU-Fix)
[/LIST]

**[SIZE="4"]Call for nominations: Ubuntu Community Council[/SIZE]**

Merlijn Sebrechts, in announcing the call open, provides the guidelines for applying and why one should take up the responsibility. The nominations will close on Sunday September 22, 23:59 UTC, with the vote to end on Sunday October 13, 23:59 UTC. Additional informative links and the application link are provided.

[https://discourse.ubuntu.com/t/call-for-nominations-ubuntu-community-council/47458](https://discourse.ubuntu.com/t/call-for-nominations-ubuntu-community-council/47458)

**[SIZE="4"]Welcome New Members and Developers[/SIZE]**

[LIST]
[*]Nathan Teodosio (nteodosio); Ubuntu Membership - [https://lists.ubuntu.com/archives/ubuntu-news-team/2024-August/003082.html](https://lists.ubuntu.com/archives/ubuntu-news-team/2024-August/003082.html)
[/LIST]

Congratulations to this contributor!

**[SIZE="5"]Ubuntu Stats[/SIZE]**

**[SIZE="4"]Bug Stats[/SIZE]**

[LIST]
[*]Open: 144576 (+125)
[*]Critical: 307 (0)
[*]Unconfirmed: 73191 (+108)
[/LIST]

As always, the Bug Squad needs more help. If you want to get started, please see: [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

**[SIZE="4"]Translations[/SIZE]**

[LIST]
[*]German: 86.72% (46620/107)
[*]Ukrainian: 85.97% (49268/1268)
[*]French: 83.79% (56895/7296)
[*]Swedish: 79.16% (73174/1138)
[*]Spanish: 76.80% (81451/4795)
[/LIST]

**[SIZE="5"]Hot in Support[/SIZE]**

**[SIZE="4"]Ask Ubuntu Top 5 Questions[/SIZE]**

[LIST]
[*]google-chrome-stable : Depends: libgcc-s1 (>= 4.2) but it is not installable - [https://askubuntu.com/questions/1524103/google-chrome-stable-depends-libgcc-s1-4-2-but-it-is-not-installable](https://askubuntu.com/questions/1524103/google-chrome-stable-depends-libgcc-s1-4-2-but-it-is-not-installable)
[*]Signal Desktop 7.9.0 shows expired on Ubuntu 24.04? - [https://askubuntu.com/questions/1524141/signal-desktop-7-9-0-shows-expired-on-ubuntu-24-04](https://askubuntu.com/questions/1524141/signal-desktop-7-9-0-shows-expired-on-ubuntu-24-04)
[*]Print tree of uninstalled dependencies and their filesizes for apt packages - [https://askubuntu.com/questions/1524293/print-tree-of-uninstalled-dependencies-and-their-filesizes-for-apt-packages](https://askubuntu.com/questions/1524293/print-tree-of-uninstalled-dependencies-and-their-filesizes-for-apt-packages)
[*]Verifying shim SBAT data failed: Security Policy Violation - Ubuntu 22.04.4 LTS - [https://askubuntu.com/questions/1524048/verifying-shim-sbat-data-failed-security-policy-violation-ubuntu-22-04-4-lts](https://askubuntu.com/questions/1524048/verifying-shim-sbat-data-failed-security-policy-violation-ubuntu-22-04-4-lts)
[*]Video stream very slow in Ubuntu server - [https://askubuntu.com/questions/1524262/video-stream-very-slow-in-ubuntu-server](https://askubuntu.com/questions/1524262/video-stream-very-slow-in-ubuntu-server)
[/LIST]

Ask (and answer!) questions at: [https://askubuntu.com/](https://askubuntu.com/)

**[SIZE="4"]Ubuntu Forums Top 5 Threads[/SIZE]**

[LIST]
[*]is this librewolf messege should worry me? - [https://ubuntuforums.org/showthread.php?t=2500112](https://ubuntuforums.org/showthread.php?t=2500112)
[*]Unable to install GRUB in /dev/nvme0n1 when installing Ubuntu 22.04 Dual Boot HP - [https://ubuntuforums.org/showthread.php?t=2500155](https://ubuntuforums.org/showthread.php?t=2500155)
[*]Second Hard Drive Doesn't Show - [https://ubuntuforums.org/showthread.php?t=2500066](https://ubuntuforums.org/showthread.php?t=2500066)
[*]Grub minimal commandline on startup - [https://ubuntuforums.org/showthread.php?t=2500037](https://ubuntuforums.org/showthread.php?t=2500037)
[*]AppImages Won't Work - [https://ubuntuforums.org/showthread.php?t=2500030](https://ubuntuforums.org/showthread.php?t=2500030)
[/LIST]

Find more support at: [https://ubuntuforums.org/](https://ubuntuforums.org/)

**[SIZE="5"]Weekly Meeting Reports[/SIZE]**

**[SIZE="4"]Starcraft Clinic 2024-Aug-16[/SIZE]**

Meeting summary includes the topics: Remote Build, Mesa, dotnet snap, Snapcraft 7, Riscv64, and more. Thanks are given to all who sponsored and to those who joined.

[https://forum.snapcraft.io/t/starcraft-clinic-2024-aug-16/41427/4?u=soumyadghosh](https://forum.snapcraft.io/t/starcraft-clinic-2024-aug-16/41427/4?u=soumyadghosh)

**[SIZE="5"]LoCo News[/SIZE]**

**[SIZE="4"]Midwest Superfest and Software Freedom Day 2024[/SIZE]**

Zackariah Fosdyck tells us the Midwest Superfest which is hosted by the Peoria-Area Amateur Radio Club has a booth for LibrePlanet Illinois team and Ubuntu Illinois Local Community team on September 21, 2024. This post gives details of that event.

[https://discourse.ubuntu.com/t/midwest-superfest-and-software-freedom-day-2024/47325](https://discourse.ubuntu.com/t/midwest-superfest-and-software-freedom-day-2024/47325)

**[SIZE="4"]UbuCon Asia 2024[/SIZE]**

The UbuCon Asia team, with the collaboration of UbuCon India team, will be organizing the UbuCon Asia 2024 in Jaipur, India, from 31 August to 2 September. So, those who have booked the tickets, pack your bag and lets make this event a great success. Anyone having visa related issues or any other issue, please contact us on:

[LIST]
[*]Telegram: [https://t.me/UbuConAsia](https://t.me/UbuConAsia)
[*]Matrix: [https://matrix.to/#/#ubucon-asia-general:matrix.org](https://matrix.to/#/#ubucon-asia-general:matrix.org)
[*]Website: [https://2024.ubucon.asia/](https://2024.ubucon.asia/)
[/LIST]

[https://events.canonical.com/event/47/program](https://events.canonical.com/event/47/program)
[LIST]
[*][https://discourse.ubuntu.com/t/ubucon-asia-2024-around-the-corner/46825](https://discourse.ubuntu.com/t/ubucon-asia-2024-around-the-corner/46825)
[/LIST]

**[SIZE="4"]UbuCon Korea 2024 has wrapped up with 151 attendees this year![/SIZE]**

Jungmin Yoon (paperbox), in relating the August 9th conclusion, advises of the many participants who produced these workshops and events. The program included 9 talks, 2 workshops, 3 lightning talks, 3 BoFs, and a signing key party. Minseong Cho (mscho7969) renders reporting support with adding additional screen shots and a big thanks to the sponsors of the event: "It would be difficult to make the event happen without any help from our sponsors!"

[https://discourse.ubuntu.com/t/ubucon-korea-2024-has-wrapped-up-with-151-attendees-this-year/47443](https://discourse.ubuntu.com/t/ubucon-korea-2024-has-wrapped-up-with-151-attendees-this-year/47443)

**[SIZE="5"]LoCo Events[/SIZE]**

The following LoCo team events are currently scheduled in the next two weeks:

[LIST]
[*]Atlanta Linux Enthusiasts: Southwest Weekly Help Sessions; 29 August, 6:00 - 8:00 PM EDT; Wings and Things - [https://www.meetup.com/ale-atlanta-linux-enthusiasts/events/302744310/](https://www.meetup.com/ale-atlanta-linux-enthusiasts/events/302744310/)
[*]Arizona LoCo: AZLOCO Team Meeting on IRC.libera.chat; 1 September, 2100-2130 - IRC channel #ubuntu.us.az
[*]Atlanta Linux Enthusiasts: NW Weekly Linux Help Session (online); 1 September, 3:00- 6:00 PM EDT - [https://www.meetup.com/ale-atlanta-linux-enthusiasts/events/302796623/](https://www.meetup.com/ale-atlanta-linux-enthusiasts/events/302796623/)
[*]Arizona LoCo: Virtual Tempe Ubuntu Hour; 5 September, 1900-2000 - BigBlue Button, [https://bbb.azloco.net](https://bbb.azloco.net)
[*]Atlanta Linux Enthusiasts: Southwest Weekly Help Sessions; 5 September 6:00 - 8:00 PM EDT; Wings and Things - [https://www.meetup.com/ale-atlanta-linux-enthusiasts/events/302874983/](https://www.meetup.com/ale-atlanta-linux-enthusiasts/events/302874983/)
[*]Arizona LoCo: Virtual Installfest/Linux Workshop on line; 7 September, 1000-1600 - Big Blue Button, [https://bbb.azloco.net](https://bbb.azloco.net) (co-hosted with the Phoenix Linux User Group)
[*]Atlanta Linux Enthusiasts: NW Weekly Linux Help Session (online); 8 September, 3:00- 6:00 PM EDT - [https://www.meetup.com/ale-atlanta-linux-enthusiasts/events/302927982/](https://www.meetup.com/ale-atlanta-linux-enthusiasts/events/302927982/)
[/LIST]

Looking beyond the next two weeks? Visit the respective LoCo Team calendar to browse upcoming events.

Please see:

[LIST]
[*]Atlanta Linux Enthusiasts: [https://www.meetup.com/ale-atlanta-linux-enthusiasts/](https://www.meetup.com/ale-atlanta-linux-enthusiasts/) and [https://ale.org/](https://ale.org/)
[*]Ubuntu Arizona LoCo: [https://discourse.ubuntu.com/t/upcoming-events-for-azloco/38466](https://discourse.ubuntu.com/t/upcoming-events-for-azloco/38466)
[*]Registered LoCo contacts: [https://discourse.ubuntu.com/c/locos/129](https://discourse.ubuntu.com/c/locos/129)
[/LIST]

**[SIZE="5"]The Hub[/SIZE]**

**[SIZE="4"]Ubuntu WSL channel on Matrix[/SIZE]**

Jean Baptiste Lallement reports a new Matrix channel for the Ubuntu WSL community.

[https://discourse.ubuntu.com/t/ubuntu-wsl-channel-on-matrix/47322](https://discourse.ubuntu.com/t/ubuntu-wsl-channel-on-matrix/47322)

**[SIZE="4"]Ubuntu 24.10 Testing Week[/SIZE]**

Aaron Prisk reminds us October is approaching, as is Ubuntu 24.10. This post highlights Ubuntu Testing Week which runs from August 22-29 where users are encouraged to grab the latest build & run some tests. This detailed post gives some details on what we'll see when testing Ubuntu 24.10, plus details on useful inputs for testing. It includes flavour testing, with links where we can speak with other testers, or gain knowledge on Quality Assurance testing.

[https://discourse.ubuntu.com/t/ubuntu-24-10-testing-week/47330](https://discourse.ubuntu.com/t/ubuntu-24-10-testing-week/47330)

**[SIZE="5"]The Planet[/SIZE]**

**[SIZE="4"]The CMA wants your comments on web apps[/SIZE]**

Stuart Langridge writes that the UK CMA (Competition and Markets Authority) has put out a request for proposals related to anti-competitive behavior by web browsers or platforms and the current (potential) list of remedies. Stuart outlines the 'state of affairs' as he sees it, requesting readers to read the linked document and express their own view. Further Stuart tells us he is speaking in OWA at the State of the Browser on September 14 in London (details provided), and gives links to other related details/opinion.

[https://www.kryogenix.org/days/2024/08/21/the-cma-wants-your-comments-on-web-apps/](https://www.kryogenix.org/days/2024/08/21/the-cma-wants-your-comments-on-web-apps/)

**[SIZE="5"]Other Community News[/SIZE]**

**[SIZE="4"]GNOME 47.beta Released[/SIZE]**

Jordan Petridis announces that the GNOME 47 beta is now available, giving us details and requesting we help test it. Links and a reminder that this is beta software are provided.

[https://discourse.gnome.org/t/gnome-47-beta-released/22919/](https://discourse.gnome.org/t/gnome-47-beta-released/22919/)
[LIST]
[*]GNOME 47 Beta Desktop Released with Many Changes, Here’s What’s New - [https://9to5linux.com/gnome-47-beta-desktop-released-with-many-changes-heres-whats-new](https://9to5linux.com/gnome-47-beta-desktop-released-with-many-changes-heres-whats-new)
[/LIST]

**[SIZE="5"]Canonical News[/SIZE]**

[LIST]
[*]How Ubuntu keeps you secure with KEV prioritisation - [https://ubuntu.com//blog/how-ubuntu-keeps-you-secure-with-kev-prioritisation](https://ubuntu.com//blog/how-ubuntu-keeps-you-secure-with-kev-prioritisation)
[/LIST]

**[SIZE="5"]In the Blogosphere[/SIZE]**

**[SIZE="4"]Ubuntu Fixes Old NVIDIA Wayland Support For GNOME, Hiring More Desktop Engineers[/SIZE]**

Michael Larabel writes that Canonical's Daniel Van Vugt has continued 'hacking on the GNOME Mutter triple buffering support' that has been in Ubuntu/Debian awhile now, though Michael expresses a view that its unlikely to be mainstreamed to GNOME 47. Another merge request that will be in the GNOME 47 release is mentioned, along with details on Canonical hiring new desktop software engineers.

[https://www.phoronix.com/news/Ubuntu-Fixes-EGLDevice-GNOME](https://www.phoronix.com/news/Ubuntu-Fixes-EGLDevice-GNOME)

**[SIZE="4"]Over 9 Years LVFS Has Served Over 110 Million Firmware Files To Linux Systems[/SIZE]**

Michael Larabel writes about Linux Vendor Firmware Services (LVFS) which was started by Richard Hughes of Red Hat nine years ago. This post covers a 'brief retrospective' by Richard on what this code has achieved, with links should you need more.

[https://www.phoronix.com/news/LVFS-9th-Birthday](https://www.phoronix.com/news/LVFS-9th-Birthday)

**[SIZE="4"]NVIDIA 560 Linux Driver Released with Open GPU Kernel Modules by Default[/SIZE]**

Marius Nestor tells us the NVIDIA 560 has been released as stable, with this the first version to use open-source GPU kernels by default. We're given highlights of this release, details of some use-cases that will benefit from its use, as well as links to the release notes and where we can download it.

[https://9to5linux.com/nvidia-560-linux-driver-released-with-open-gpu-kernel-modules-by-default](https://9to5linux.com/nvidia-560-linux-driver-released-with-open-gpu-kernel-modules-by-default)
[LIST]
[*]NVIDIA 560.35.03 Linux Driver Released With More Wayland Fixes -
[/LIST]
[https://www.phoronix.com/news/NVIDIA-560.35.03-Linux-Driver](https://www.phoronix.com/news/NVIDIA-560.35.03-Linux-Driver)

**[SIZE="4"]LibreOffice 24.8 Delivers Many Advancements To This Free Software Office Suite[/SIZE]**

Michael Larabel blogs that LibreOffice 24.8 is now officially out, giving us some details of what is found in this release. We're given a screenshot, and a link to the Document Foundation wiki for more info, or to LibreOffice to download.

[https://www.phoronix.com/news/LibreOffice-24.8-Released](https://www.phoronix.com/news/LibreOffice-24.8-Released)

**[SIZE="5"]Featured Audio and Video[/SIZE]**

**[SIZE="4"]Ubuntu Security Podcast: Episode 235[/SIZE]**

"A recent Microsoft Windows update breaks Linux dual-boot - or does it? This week we look into reports of the recent Windows patch-Tuesday update breaking dual-boot, including a deep-dive into the technical details of Secure Boot, SBAT, grub, shim and more, plus we look at a vulnerability in GNOME Shell and the handling of captive portals as well."

[https://ubuntusecuritypodcast.org/episode-235/](https://ubuntusecuritypodcast.org/episode-235/)

**[SIZE="4"]Ubuntu Portugal Podcast: Episode 312 - Nuno do Carmo[/SIZE]**

"Um Português, um Suíço exilado em Portugal e um Português exilado na Suíça entram num bar: a Microsoft é uma empresa Open Source? Como é que se pronuncia SUSE correctamente? Suza? Suze? Suzy? Suzette? A resposta a esta e muitas outras perguntas serão dadas pelo Nuno do Carmo (a.k.a.: Corsário), um multifacetado Tech Writer (Kubernetes e outras aplicações cloud native) e Microsoft MVP (Profissional Muito Valioso), Embaixador da CNCF (Cloud Native Computing Foundation) e da CIVO. É perito em WSL (Windows Subsystem for Linux) - e trabalha na SUSE, um sistema operativo Gnu-Linux muito popular no sector empresarial.?

[https://podcastubuntuportugal.org/e312/](https://podcastubuntuportugal.org/e312/)

**[SIZE="4"]Ubuntu OnAir: Opportunity Open Source IIT Kanpur, India - Room 1: Plenary - Sat, Aug. 24, Afternoon[/SIZE]**

"Live coverage of the Opportunity Open Source conference in the Indian Institute of Technology Kanpur in India, for attending the conference remotely. This is the stream for the Room 1 (Plenary) on Saturday, Aug. 24 in the afternoon. On this day we will have sessions from 3:00pm - 7:10pm IST or 9:30 - 13:40 UTC (or 4:10 hours of streaming)."

[https://www.youtube.com/watch?v=zb7vGeTwTDs](https://www.youtube.com/watch?v=zb7vGeTwTDs)

**[SIZE="4"]Destination Linux: episode 384 - Ubuntu’s New Kernel Strategy & What It Means for Users[/SIZE]**

"On this episode, we’re going to discuss Ubuntu announcing a major Linux Kernel change that the Linux community will love! ... "

[https://tuxdigital.com/podcasts/destination-linux/dl-384/](https://tuxdigital.com/podcasts/destination-linux/dl-384/)

**[SIZE="5"]Meeting Reports[/SIZE]**

[LIST]
[*]Rocks Public Journal 2024-08-19 - [https://discourse.ubuntu.com/t/rocks-public-journal-2024-08-19/47277](https://discourse.ubuntu.com/t/rocks-public-journal-2024-08-19/47277)
[*]LXD: Weekly news #359 - [https://discourse.ubuntu.com/t/weekly-news-359/47279](https://discourse.ubuntu.com/t/weekly-news-359/47279)
[*]+1 maintenance reports - [https://lists.ubuntu.com/archives/ubuntu-devel/2024-August/date.html](https://lists.ubuntu.com/archives/ubuntu-devel/2024-August/date.html)
[*]+1 Maintenance report - Week 34 - [https://discourse.ubuntu.com/t/1-maintenance-report-week-34/47417](https://discourse.ubuntu.com/t/1-maintenance-report-week-34/47417)
[*]Matrix Council meeting: Aug 22 2024 - [https://discourse.ubuntu.com/t/matrix-council-meeting-aug-22-2024/47387](https://discourse.ubuntu.com/t/matrix-council-meeting-aug-22-2024/47387)
[/LIST]

**[SIZE="5"]Upcoming Meetings and Events[/SIZE]**

[LIST]
[*]Main Inclusion Requests (MIR) Status: Tue, August 27, 3:30pm – 4:00pm
[*]Technical Board: Tue, August 27, 7pm – 8pm
[*]Ubuntu HPC weekly community call: Wed, August 28, 11:30 AM- 12:00 PM - [https://meet.jit.si/Ubuntu-HPC](https://meet.jit.si/Ubuntu-HPC) and [https://matrix.to/#/#hpc:ubuntu.com](https://matrix.to/#/#hpc:ubuntu.com)
[*]Ubuntu Foundations: Thu, August 29, 3pm – 4pm
[*]Mir Office Hours - 2024-08-29 15:00UTC: August 29, 10:00 - 10:45AM - [https://meet.google.com/kty-otcc-ucx](https://meet.google.com/kty-otcc-ucx)
[*]Lubuntu Weekly Standup: Thu, August 29, 4:00 - 5:00 PM - [https://matrix.to/#/#lubuntu-devel:ubuntu.com](https://matrix.to/#/#lubuntu-devel:ubuntu.com)
[*]UbuCon North America committee meeting: August 29, 4:00 - 5:00 PM - [https://matrix.to/#/#ubucon-na:ubuntu.com](https://matrix.to/#/#ubucon-na:ubuntu.com)
[*]Ubuntu Desktop Indaba: Fri, August 30, 4pm – 5pm
[*]UbuCon Latin America 2024: August 30 -31; Barranquilla, Colombia - [https://ubuconla.org/2024/](https://ubuconla.org/2024/)
[*]Starcraft Clinics: Fri, August 30, 9:00 - 10:00 AM - [https://meet.google.com/ixc-nucm-hjn](https://meet.google.com/ixc-nucm-hjn)
[*]Open Documentation Hour: August 30, 10:00 - 11:00 AM - [https://meet.google.com/zcy-onjk-smi](https://meet.google.com/zcy-onjk-smi)
[*]UbuCon Asia 2024: 31 August - 2 September - [https://discourse.ubuntu.com/t/ubucon-asia-2024-around-the-corner/46825](https://discourse.ubuntu.com/t/ubucon-asia-2024-around-the-corner/46825)
[/LIST]

Times shown are UTC unless otherwise specified. For more details and farther dates please visit: [https://fridge.ubuntu.com/calendars/](https://fridge.ubuntu.com/calendars/) | [https://discourse.ubuntu.com/upcoming-events](https://discourse.ubuntu.com/upcoming-events)

**[SIZE="5"]Updates and Security for Ubuntu 20.04, 22.04, and 24.04[/SIZE]**

**[SIZE="4"]Security Updates[/SIZE]**

[LIST]
[*][USN-6837-2] Rack vulnerabilitie - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008554.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008554.html)
[*][USN-6966-1] Firefox vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008555.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008555.html)
[*][USN-6951-3] Linux kernel (Azure) vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008556.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008556.html)
[*][USN-6968-1] PostgreSQL vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008557.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008557.html)
[*][USN-6967-1] Intel Microcode vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008558.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008558.html)
[*][LSN-0106-1] Linux kernel vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008559.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008559.html)
[*][USN-6969-1] Cacti vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008560.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008560.html)
[*][USN-6970-1] exfatprogs vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008561.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008561.html)
[*][USN-6944-2] curl vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008562.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008562.html)
[*][USN-6966-2] Firefox regressions - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008563.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008563.html)
[*][USN-6965-1] Vim vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008564.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008564.html)
[*][USN-6950-4] Linux kernel (HWE) vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008565.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008565.html)
[*][USN-6951-4] Linux kernel (BlueField) vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008566.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008566.html)
[*][USN-6971-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008567.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008567.html)
[*][USN-6972-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008568.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008568.html)
[*][USN-6973-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008569.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008569.html)
[*][USN-6974-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008571.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008571.html)
[*][USN-6975-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008570.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008570.html)
[*][USN-6976-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008572.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008572.html)
[*][USN-6977-1] QEMU vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008573.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008573.html)
[*][USN-6979-1] Linux kernel (Raspberry Pi) vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008574.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008574.html)
[*][USN-6972-2] Linux kernel (AWS) vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008575.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008575.html)
[*][USN-6978-1] XStream vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008576.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008576.html)
[*][USN-6980-1] ImageMagick vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008577.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008577.html)
[*][USN-6972-3] Linux kernel (Azure) vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008578.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008578.html)
[*][USN-6973-2] Linux kernel (Azure) vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008579.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008579.html)
[*][USN-6974-2] Linux kernel (Oracle) vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008580.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2024-August/008580.html)
[/LIST]

**[SIZE="4"]Ubuntu 20.04 Updates[/SIZE]**

[LIST]
[*]firefox 129.0.1+build1-0ubuntu0.20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049272.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049272.html)
[*]intel-microcode 3.20240813.0ubuntu0.20.04.2 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049274.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049274.html)
[*]shim 15.8-0ubuntu1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049276.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049276.html)
[*]shim-signed 1.40.10 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049277.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049277.html)
[*]postgresql-12 12.20-0ubuntu0.20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049278.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049278.html)
[*]linux-aws 5.4.0-1132.142 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049279.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049279.html)
[*]linux-meta-aws 5.4.0.1132.129 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049280.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049280.html)
[*]linux-signed-aws 5.4.0-1132.142 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049282.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049282.html)
[*]linux-restricted-modules-aws 5.4.0-1132.142 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049281.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049281.html)
[*]linux-restricted-signatures-aws 5.4.0-1132.142 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049283.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049283.html)

Due to excessive content these are abridged; The complete list is here: [https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-854/47301](https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-854/47301)


[*]linux-restricted-modules-oracle-5.15 5.15.0-1066.72~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049528.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049528.html)
[*]linux-meta-oracle-5.15 5.15.0.1066.72~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049529.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049529.html)
[*]linux-oracle-5.15 5.15.0-1066.72~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049530.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049530.html)
[*]linux-signed-oracle-5.15 5.15.0-1066.72~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049531.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049531.html)
[*]linux-meta-oracle-5.15 5.15.0.1067.73~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049532.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049532.html)
[*]linux-oracle-5.15 5.15.0-1067.73~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049533.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049533.html)
[*]linux-signed-oracle-5.15 5.15.0-1067.73~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049535.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049535.html)
[*]linux-restricted-modules-oracle-5.15 5.15.0-1067.73~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049534.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049534.html)
[*]linux-restricted-signatures-oracle-5.15 5.15.0-1067.73~20.04.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049536.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049536.html)
[*]rabbitmq-server 3.8.3-0ubuntu0.1 - [https://lists.ubuntu.com/archives/focal-changes/2024-August/049537.html](https://lists.ubuntu.com/archives/focal-changes/2024-August/049537.html)
[/LIST]

End of Standard Support: April 2025

**[SIZE="4"]Ubuntu 22.04 Updates[/SIZE]**

[LIST]
[*]intel-microcode 3.20240813.0ubuntu0.22.04.2 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/032930.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/032930.html)
[*]linux-meta-ibm-6.8 6.8.0-1012.12~22.04.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/032932.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/032932.html)
[*]linux-ibm-6.8 6.8.0-1012.12~22.04.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/032933.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/032933.html)
[*]linux-signed-ibm-6.8 6.8.0-1012.12~22.04.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/032934.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/032934.html)
[*]linux-restricted-modules-ibm-6.8 6.8.0-1012.12~22.04.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/032935.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/032935.html)
[*]linux-restricted-signatures-ibm-6.8 6.8.0-1012.12~22.04.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/032936.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/032936.html)
[*]shim 15.8-0ubuntu1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/032937.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/032937.html)
[*]shim-signed 1.51.4 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/032938.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/032938.html)
[*]linux-ibm 5.15.0-1062.65 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/032939.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/032939.html)
[*]linux-meta-ibm 5.15.0.1062.58 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/032940.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/032940.html)

Due to excessive content these are abridged; The complete list is here: [https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-854/47301](https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-854/47301)


[*]linux-signed-nvidia-6.8 6.8.0-1013.14~22.04.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/033168.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/033168.html)
[*]linux-restricted-signatures-nvidia-6.8 6.8.0-1013.14~22.04.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/033169.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/033169.html)
[*]linux-restricted-modules-nvidia-6.8 6.8.0-1013.14~22.04.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/033170.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/033170.html)
[*]vsftpd 3.0.5-0ubuntu1.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/033171.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/033171.html)
[*]livecd-rootfs 2.765.46 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/033172.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/033172.html)
[*]swtpm 0.6.3-0ubuntu3.3 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/033173.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/033173.html)
[*]python-ovsdbapp 1.15.1-0ubuntu2.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/033174.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/033174.html)
[*]python3-defaults 3.10.6-1~22.04.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/033175.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/033175.html)
[*]dotnet6 6.0.133-0ubuntu1~22.04.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/033176.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/033176.html)
[*]rabbitmq-server 3.9.27-0ubuntu0.1 - [https://lists.ubuntu.com/archives/jammy-changes/2024-August/033177.html](https://lists.ubuntu.com/archives/jammy-changes/2024-August/033177.html)
[/LIST]

End of Standard Support: April 2027

**[SIZE="4"]Ubuntu 24.04 Updates[/SIZE]**

[LIST]
[*]intel-microcode 3.20240813.0ubuntu0.24.04.2 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/040990.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/040990.html)
[*]dpkg 1.22.6ubuntu6.1 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/040992.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/040992.html)
[*]dotnet8 8.0.108-8.0.8-0ubuntu1~24.04.2 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/040993.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/040993.html)
[*]linux-signed 6.8.0-44.44 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/040994.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/040994.html)
[*]linux 6.8.0-44.44 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/040995.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/040995.html)
[*]linux-meta 6.8.0-44.44 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/040996.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/040996.html)
[*]linux-restricted-signatures 6.8.0-44.44 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/040997.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/040997.html)
[*]linux-restricted-modules 6.8.0-44.44 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/040998.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/040998.html)
[*]linux-azure 6.8.0-1014.16 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/040999.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/040999.html)
[*]linux-meta-azure 6.8.0-1014.16 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041000.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041000.html)

Due to excessive content these are abridged; The complete list is here: [https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-854/47301](https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-854/47301)


[*]linux-oem-6.11 6.11.0-1002.2 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041232.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041232.html)
[*]linux-meta-oem-6.11 6.11.0-1002.2 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041233.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041233.html)
[*]linux-signed-oem-6.11 6.11.0-1002.2 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041234.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041234.html)
[*]linux-restricted-modules-oem-6.11 6.11.0-1002.2 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041235.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041235.html)
[*]linux-restricted-signatures-oem-6.11 6.11.0-1002.2 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041236.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041236.html)
[*]python-apt 2.7.7ubuntu3 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041237.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041237.html)
[*]fwupd 1.9.24-1~24.04.1 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041238.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041238.html)
[*]rabbitmq-server 3.12.1-1ubuntu1.1 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041239.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041239.html)
[*]base-files 13ubuntu10.1 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041240.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041240.html)
[*]livecd-rootfs 24.04.77 - [https://lists.ubuntu.com/archives/noble-changes/2024-August/041241.html](https://lists.ubuntu.com/archives/noble-changes/2024-August/041241.html)
[/LIST]

End of standard support: April 2029

**[SIZE="5"]Subscribe[/SIZE]**

Get your copy of the Ubuntu Weekly Newsletter delivered each week to you via email at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-news](https://lists.ubuntu.com/mailman/listinfo/ubuntu-news)

Or follow us via our various social media presences:

[LIST]
[*][https://www.facebook.com/UbuntuWeeklyNewsletter](https://www.facebook.com/UbuntuWeeklyNewsletter)
[*][https://twitter.com/Ubuntu_News](https://twitter.com/Ubuntu_News)
[*][https://ubuntu.social/@ubuntuweeklynews](https://ubuntu.social/@ubuntuweeklynews) (Mastodon)
[*][https://t.me/ubuntunewsletter](https://t.me/ubuntunewsletter) (Telegram)
[/LIST]

**[SIZE="5"]Archive[/SIZE]**

You can always find older Ubuntu Weekly Newsletter issues at: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Archive](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Archive)

**[SIZE="5"]Further News[/SIZE]**

As always you can find more Ubuntu news and announcements at:

[LIST]
[*][https://ubuntu.com/blog/](https://ubuntu.com/blog/)
[*][https://fridge.ubuntu.com/](https://fridge.ubuntu.com/)
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
[*]soumyadghosh
[*]And many others
[/LIST]

**[SIZE="5"]Glossary of Terms[/SIZE]**

Other acronyms can be found at: [https://discourse.ubuntu.com/t/glossary-uwn/42405](https://discourse.ubuntu.com/t/glossary-uwn/42405)

**[SIZE="5"]Get Involved[/SIZE]**

The Ubuntu community consists of individuals and teams, working on different aspects of the distribution, giving advice and technical support, and helping to promote Ubuntu to a wider audience. No contribution is too small, and anyone can help. It's your chance to get in on all the community fun associated with developing and promoting Ubuntu. More on this at: [https://community.ubuntu.com/contribute/](https://community.ubuntu.com/contribute/)

Or get involved with the Ubuntu Weekly Newsletter team! We always need summary writers and editors, if you're interested, learn more at: [https://discourse.ubuntu.com/t/joining-the-ubuntu-weekly-newsletter-team/40929](https://discourse.ubuntu.com/t/joining-the-ubuntu-weekly-newsletter-team/40929)

**[SIZE="5"]Feedback[/SIZE]**

This document is maintained by the Ubuntu Weekly News Team. If you have a story idea or suggestions for the Weekly Newsletter, join the Ubuntu News Team mailing list at [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team) and submit it. Ideas can also be added to the wiki at [https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-ideas/40053/](https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-ideas/40053/). If you'd like to contribute to a future issue of the Ubuntu Weekly Newsletter, please feel free to edit the appropriate wiki page. If you have any technical support questions, please check [https://community.ubuntu.com/help-information/](https://community.ubuntu.com/help-information/) for more information on where to get help.

Except where otherwise noted, this issue of the Ubuntu Weekly Newsletter is licensed under a Creative Commons Attribution ShareAlike 3.0 License.
[IMG]https://fridge.ubuntu.com/wp-content/uploads/2015/05/ab28/CCL.png[/IMG]

---

