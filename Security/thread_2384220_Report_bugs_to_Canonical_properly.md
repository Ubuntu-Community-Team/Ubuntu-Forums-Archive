---
title: "Report bugs to Canonical properly?"
date: 2018-02-03
forum: Security
---

### Post by espectro2 on 2018-02-03
I would like to  know what information is sent when we report a bug via Launchpad  security and privacy send reports will the MAC address of the machine? What information is for canonical?
ubuntu-bug followed by program or package name is sure way to report bugs?
I am suspicious  looking at the logs that someone tried to install minergate on my  computer to mine bitcoins see log photo  2018-01-07 01:01    2018-01-06  16:01 UTC    Crash    minergate[ATTACH=CONFIG]278433[/ATTACH]
What should I do if someone is remotely using my machine to mine bitcoins?
Thanks for listening

---

### Post by QIII on 2018-02-03
Hello!

ubuntu-bug is the appropriate method to report a crash as a possible bug -- for packages installed from Canonical repos.  Have a look [here]("https://help.ubuntu.com/community/ReportingBugs").  I don't think minergate is hosted in the Canonical repos.

If it was installed without your knowledge, that wouldn't be a bug.  If anything, it would be a compromise or attack.  A bug report related to an intrusion would be rejected unless there were some reason to believe it was due to a fault in the security measures baked into the kernel and the OS.

If you did not install minergate, the first thing to consider is whether the machine has been physically available to others.  Is it locked up when you are away?  Do you have room mates?  Family members?

As to what information is available in the crash report? Quite a bit.  Could they discover who installed it?  Perhaps, but it would probably be your user account.  Would they do that for you?  Maybe, if you bought a support subscription.

You could use something like 

```
 less /var/log/dpkg.log
``` to see when it was installed.

You might have to search older, compressed files:

```
ls -l /var/log/dpkg.log*
```

to find out what is there.

You might search through auth.log (and compressed files).

---

### Post by espectro2 on 2018-02-04
I'm going to run  these commands indicated already I warn that only I use the machine  nobody has the password of ubuntu nobody uses machine besides me I do  not even use bitcoin I installed minergate in my machine
Thanks for listening.

result of the command executed first in sudo non-root account
and then the result in the default account that does not belong to sudo just for web browsing
I note that number of programs that appear running dpkg -l command assumes me.
My central ubuntu software program does not open in the administrative sudo user created in the installation of the machine.
Thanks for listening.

commands executed on the sudo user created at the machine installation
```
2018-02-01 14:19:43 startup archives unpack
2018-02-01 14:19:44 upgrade libcurl3-gnutls:amd64 7.47.0-1ubuntu2.5 7.47.0-1ubuntu2.6
2018-02-01 14:19:44 status triggers-pending libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:44 status half-configured libcurl3-gnutls:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:44 status unpacked libcurl3-gnutls:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:44 status half-installed libcurl3-gnutls:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:44 status half-installed libcurl3-gnutls:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:44 status unpacked libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:44 status unpacked libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 upgrade libcurl3:amd64 7.47.0-1ubuntu2.5 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status half-configured libcurl3:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:45 status unpacked libcurl3:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:45 status half-installed libcurl3:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:45 status half-installed libcurl3:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:45 status unpacked libcurl3:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status unpacked libcurl3:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 trigproc libc-bin:amd64 2.23-0ubuntu10 <nenhuma>
2018-02-01 14:19:45 status half-configured libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:45 status installed libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:45 startup packages configure
2018-02-01 14:19:45 configure libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6 <nenhuma>
2018-02-01 14:19:45 status triggers-pending libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:45 status unpacked libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status half-configured libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status installed libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 configure libcurl3:amd64 7.47.0-1ubuntu2.6 <nenhuma>
2018-02-01 14:19:45 status unpacked libcurl3:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status half-configured libcurl3:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status installed libcurl3:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 trigproc libc-bin:amd64 2.23-0ubuntu10 <nenhuma>
2018-02-01 14:19:45 status half-configured libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:45 status installed libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:45 startup packages configure

``````

-rw-r--r-- 1 root root   2381 Fev  1 14:19 /var/log/dpkg.log
-rw-r--r-- 1 root root 261454 Jan 31 21:21 /var/log/dpkg.log.1
-rw-r--r-- 1 root root  11759 Dez 29 21:18 /var/log/dpkg.log.2.gz
-rw-r--r-- 1 root root 128677 Nov 28 19:46 /var/log/dpkg.log.3.gz
```

Note I do not have root user activated by least not by methese second reports of commands were executed in the default user without sudo permission etc. only for web browsingThanks for listening.
I use sudo for everything in the user created in the installation
minirgate worries me a lot since I do not even use bitcoin 2018-01-07 01:01    2018-01-06 16:01 UTC    Crash    minergate
thanks for listening

user padrao
```
2018-02-01 14:19:43 startup archives unpack
2018-02-01 14:19:44 upgrade libcurl3-gnutls:amd64 7.47.0-1ubuntu2.5 7.47.0-1ubuntu2.6
2018-02-01 14:19:44 status triggers-pending libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:44 status half-configured libcurl3-gnutls:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:44 status unpacked libcurl3-gnutls:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:44 status half-installed libcurl3-gnutls:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:44 status half-installed libcurl3-gnutls:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:44 status unpacked libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:44 status unpacked libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 upgrade libcurl3:amd64 7.47.0-1ubuntu2.5 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status half-configured libcurl3:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:45 status unpacked libcurl3:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:45 status half-installed libcurl3:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:45 status half-installed libcurl3:amd64 7.47.0-1ubuntu2.5
2018-02-01 14:19:45 status unpacked libcurl3:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status unpacked libcurl3:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 trigproc libc-bin:amd64 2.23-0ubuntu10 <nenhuma>
2018-02-01 14:19:45 status half-configured libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:45 status installed libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:45 startup packages configure
2018-02-01 14:19:45 configure libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6 <nenhuma>
2018-02-01 14:19:45 status triggers-pending libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:45 status unpacked libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status half-configured libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status installed libcurl3-gnutls:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 configure libcurl3:amd64 7.47.0-1ubuntu2.6 <nenhuma>
2018-02-01 14:19:45 status unpacked libcurl3:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status half-configured libcurl3:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 status installed libcurl3:amd64 7.47.0-1ubuntu2.6
2018-02-01 14:19:45 trigproc libc-bin:amd64 2.23-0ubuntu10 <nenhuma>
2018-02-01 14:19:45 status half-configured libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:45 status installed libc-bin:amd64 2.23-0ubuntu10
2018-02-01 14:19:45 startup packages configure
```
user padrao
```
-rw-r--r-- 1 root root   2381 Fev  1 14:19 /var/log/dpkg.log
-rw-r--r-- 1 root root 261454 Jan 31 21:21 /var/log/dpkg.log.1
-rw-r--r-- 1 root root  11759 Dez 29 21:18 /var/log/dpkg.log.2.gz
-rw-r--r-- 1 root root 128677 Nov 28 19:46 /var/log/dpkg.log.3.gz
```

thanks for listening

---

### Post by vasa1 on 2018-02-04
From your first post:> **espectro2 said:**
> ...
I am suspicious  looking at the logs that someone tried to install minergate on my  computer ...

From a subsequent post by you:> **espectro2 said:**
> ... I installed minergate in my machine
...
So did you or did you not install minergate yourself?

---

### Post by espectro2 on 2018-02-04
I did not  install the minergate nor do I have bitcoin wallet so I would install it  strange in previous reports security and privacy appears attempt to  install this software that I never installed
Thanks for listening.
2018-01-07 01:01    2018-01-06 16:01 UTC    Crash    minergate
and ubuntu  software center does not open more in my user admin than I use sudo not  strange that attempt log of installation of minergate and ubuntu  software center not open in the user created in the installation where  use sudo?
Thanks for listening.

[https://ubuntuforums.org/attachment.php?attachmentid=278433&d=1517711547](https://ubuntuforums.org/attachment.php?attachmentid=278433&d=1517711547)

---

### Post by corradoventu on 2018-02-04
I suspect some strange problem because in activity log manager i see the SAME report as you.
the page says: 'Error reports sent from this system' how is decided 'this system'?
if i look at the page i see: [https://errors.ubuntu.com/user/39229ebea988d6578bed98d7e18bd96fd9cd523cf89495ed70d4ce4c0f8b7937667368f389be8d8b2588bafc31d1935109305b4abf52dbb724a7cf43c3b425b4](https://errors.ubuntu.com/user/39229ebea988d6578bed98d7e18bd96fd9cd523cf89495ed70d4ce4c0f8b7937667368f389be8d8b2588bafc31d1935109305b4abf52dbb724a7cf43c3b425b4)

---

### Post by vasa1 on 2018-02-05
[s]Hmmm... definitely something amiss here!

I'm seeing minergate as well. And other software I don't have on my system which is Kubuntu 16.04.```
Error reports sent from this system
    Occurred                   Received              Problem Type     Program
2018-01-20 02:01          2018-01-22 05:01 UTC          Crash          code
2018-01-07 01:01          2018-01-06 16:01 UTC          Crash          minergate
2018-01-06 18:01          2018-01-06 16:01 UTC          Crash          kodi-bin
2018-01-03 11:01          2018-01-04 01:01 UTC          Crash          samba
2017-11-12 19:11          2017-11-12 10:11 UTC          Crash          darktable
2017-11-04 15:11          2017-11-04 22:11 UTC          Crash          ffdiaporama
2017-10-30 09:10          2017-10-30 09:10 UTC          Crash          filezilla
2017-09-21 18:09          2017-09-21 16:09 UTC          Crash          gvfs-backends
2017-09-18 14:09          2017-09-18 21:09 UTC          Crash          gnome-shell
2017-08-16 12:08          2017-08-16 06:08 UTC          Crash          bamfdaemon
2017-08-15 15:08          2017-08-15 18:08 UTC          Crash          pac
2017-08-03 09:08          2017-08-03 12:08 UTC          Crash          abiword
2017-07-26 16:07          2017-07-26 14:07 UTC          Crash          tuxboot
2017-07-21 20:07          2017-07-21 18:07 UTC          Crash          amule
2017-07-11 06:07          2017-07-11 04:07 UTC          Crash          plymouth
2017-06-14 16:06          2017-06-16 18:06 UTC          Crash          gnome-software
2017-05-29 14:05          2017-05-30 10:05 UTC          Crash          gvfs-fuse
2017-05-26 04:05          2017-05-26 09:05 UTC          Crash          cadence
2017-05-10 12:05          2017-05-10 07:05 UTC          Crash          ibus
2017-04-23 17:04          2017-04-23 09:04 UTC          Crash          evince
2017-04-05 14:04          2017-04-05 12:04 UTC          Crash          libunity9
2017-03-03 19:03          2017-03-04 02:03 UTC          Crash          xserver-xorg-core-lts-xenial
2017-03-01 17:03          2017-03-01 17:03 UTC          Crash          remmina
2017-02-13 23:02          2017-02-14 01:02 UTC          Crash          software-properties-gtk
2017-01-16 16:01          2017-01-16 19:01 UTC          Crash          gnome-software
2016-11-28 07:11          2016-11-28 06:11 UTC          Crash          gnome-software
2016-10-28 21:10          2016-10-28 19:10 UTC          Crash          thunar
2016-10-23 13:10          2016-10-24 02:10 UTC          Crash          url-dispatcher
2016-10-17 15:10          2016-10-17 13:10 UTC          Crash          update-manager
2016-09-13 20:09          2016-09-13 11:09 UTC          Crash          musescore
2016-08-18 07:08          2016-08-18 04:08 UTC          Crash          remmina
2016-07-01 16:07          2016-07-01 15:07 UTC          Crash          unity-services
2016-05-05 09:05          2016-05-05 07:05 UTC          Crash          google-chrome-stable
2016-05-01 23:05          2016-05-01 21:05 UTC          Crash          libunity9
2016-01-16 23:01          2016-01-23 13:01 UTC          KernelOops     linux-image-3.19.0-39-generic
2015-12-16 10:12          2015-12-16 07:12 UTC          Crash          gvfs-backends
2015-12-12 17:12          2015-12-12 16:12 UTC          Crash          acestream-player
2015-11-04 20:11          2015-11-05 08:11 UTC          Crash          lxsession
2015-09-12 15:09          2015-09-12 13:09 UTC          Crash          rhythmbox
2015-08-31 14:08          2015-08-31 11:08 UTC          Crash          pac
2014-12-10 14:12          2014-12-11 07:12 UTC          Crash          software-center
2014-10-21 11:10          2014-10-22 01:10 UTC          Crash          emacs23
2014-02-24 15:02          2014-02-24 14:02 UTC          Crash          /usr/bin/indicator-multiload
2014-02-14 21:02          2014-02-14 23:02 UTC          Crash          firefox
2014-02-01 08:02          2014-02-01 12:02 UTC          Crash          qbittorrent
2013-09-04 23:09          2013-09-04 17:09 UTC          Crash          totem
2013-07-09 10:07          2013-07-09 14:07 UTC          Crash          pidgin
2013-06-08 20:06          2013-06-08 18:06 UTC          Crash          me-tv
2013-05-28 22:05          2013-05-28 20:05 UTC          Crash          rhythmbox
2013-05-01 16:05          2013-05-01 16:05 UTC          Crash          skype

© 2012-2015 Canonical Ltd. Source code for this service (r584) is licensed under the AGPL.
Ubuntu and Canonical are registered trademarks of Canonical Group Ltd.
Contribute to the Ubuntu Error tracker project.

```My link is [https://errors.ubuntu.com/user/39229ebea988d6578bed98d7e18bd96fd9cd523cf89495ed70d4ce4c0f8b7937667368f389be8d8b2588bafc31d1935109305b4abf52dbb724a7cf43c3b425b4](https://errors.ubuntu.com/user/39229ebea988d6578bed98d7e18bd96fd9cd523cf89495ed70d4ce4c0f8b7937667368f389be8d8b2588bafc31d1935109305b4abf52dbb724a7cf43c3b425b4)

[s]And it seems to pick up one's forum login:[/s]

Some links that don't particularly help:
[https://wiki.ubuntu.com/ErrorTracker](https://wiki.ubuntu.com/ErrorTracker)
[http://linux.softpedia.com/blog/Meet-errors-ubuntu-com-a-Poweful-Bug-Tracker-from-Canonical-441966.shtml](http://linux.softpedia.com/blog/Meet-errors-ubuntu-com-a-Poweful-Bug-Tracker-from-Canonical-441966.shtml)[/s]

---

### Post by corradoventu on 2018-02-05
I opened a question about this problem [https://answers.launchpad.net/activity-log-manager/+question/664089](https://answers.launchpad.net/activity-log-manager/+question/664089)
from another PC same user I see a different error report
from a 3rd pc different user I see a different error report
may the problem depend from my hardware? error tracker looks to hardware instead user+hardware?
my hardware is:```
corrado@corrado-p8-bb-1221:~$ inxi -Fx
System:    Host: corrado-p8-bb-1221 Kernel: 4.13.0-32-generic x86_64 bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.26-2ubuntu1) Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop Mobo: ASRock model: H110M-G/M.2 serial: N/A UEFI: American Megatrends v: P1.10 date: 05/11/2017
CPU:       Dual core Intel Core i3-7100 (-MT-MCP-) arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 3900 MHz 2: 3900 MHz 3: 3900 MHz 4: 3900 MHz
Graphics:  Card: Intel HD Graphics 630 bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.5 ) driver: i915 Resolution: 1920x1080@59.96hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version: 4.5 Mesa 17.3.3 Direct Render: Yes
Audio:     Card Intel Sunrise Point-H HD Audio driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.13.0-32-generic
Network:   Card: Intel Ethernet Connection (2) I219-V driver: e1000e v: 3.2.6-k bus-ID: 00:1f.6
           IF: enp0s31f6 state: up speed: 100 Mbps duplex: full mac: 70:85:c2:44:7b:86
Drives:    HDD Total Size: 1000.2GB (1.5% used)
           ID-1: /dev/sda model: TOSHIBA_DT01ACA1 size: 1000.2GB
Partition: ID-1: / size: 32G used: 6.1G (21%) fs: ext4 dev: /dev/sda8
           ID-2: swap-1 size: 8.59GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 230 Uptime: 28 min Memory: 1211.8/7681.0MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.56 
corrado@corrado-p8-bb-1221:~$ 


```

---

### Post by mc4man on 2018-02-05
> **corradoventu said:**
> I opened a question about this problem [https://answers.launchpad.net/activity-log-manager/+question/664089](https://answers.launchpad.net/activity-log-manager/+question/664089)
from another PC same user I see a different error report
from a 3rd pc different user I see a different error report
may the problem depend from my hardware? error tracker looks to hardware instead user+hardware?

The 'identifier' is based on hardware. So here see the same report page in a multi-boot machine (- and the report page is accurate.
Maybe the system is ill-maintained, wouldn't be surprising.. Also note that it seems recent Ubuntu's  (gnome-shell) no longer offers this option to view previous reports in System settings  (- or at least I haven't found.

---

### Post by corradoventu on 2018-02-05
The user espectro2 and vasa1 are not using my PC, (so hardware is not the same) but have the same error report.
I have the same error report also from Ubuntu 16.04 Security & Privacy same hardware different partition
I never used nor installed some of the application listed in the report.

---

### Post by vasa1 on 2018-02-05
> **corradoventu said:**
> The user espectro2 and vasa1 are not using my PC, (so hardware is not the same) but have the same error report.
I have the same error report also from Ubuntu 16.04 Security & Privacy same hardware different partition

Hi, please disregard my post! I think I just pasted in the link OP (or you) provided.

I'm now posting from Ubuntu 16.04. Can you please tell me where I can find the activity log that provides such information?

---

### Post by corradoventu on 2018-02-05
In Ubuntu 16.04 the app is named 'Security & privacy'

---

### Post by corradoventu on 2018-02-05
@espectro2: please may you confirm the report of your 1st post is YOUR report? or you got this report somewhere else? Thanks.

---

### Post by corradoventu on 2018-02-06
@mc4man: the option to view previous reports is in the application in the app Activity log manager to be installed from ubuntu software.

---

### Post by espectro2 on 2018-02-06
yes this report and from my machine that I am using to speak with you in the forum this report I have verified in previous reports security and privacy.
Note I do not have bitcoin wallet I do not know why this app appears in the list of errors.
Thanks for listening

---

### Post by espectro2 on 2018-02-09
QIII I put the topic as resolved I need to learn how to report the bugs as indicated in the documentation only who buys the extra canonical support can report bugs a last doubt?Thanks for listening.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by QIII on 2018-02-09
What makes you think only those who buy paid support can report bugs?  I do it all the time.

You need only sign up for a launchpad account, which costs nothing.

---

### Post by vasa1 on 2018-02-09
> **espectro2 said:**
> ...
Note I do not have bitcoin wallet I do not know why this app appears in the list of errors.
...
Just guessing, but could your P2P client somehow have pulled it in?

---

### Post by #&amp;thj^% on 2018-02-09
> **vasa1 said:**
> Just guessing, but could your P2P client somehow have pulled it in?

+1
Minergate: [https://minergate.com/faq/how-minergate-console](https://minergate.com/faq/how-minergate-console)  (Bitcoin)

---

### Post by corradoventu on 2018-02-10
@mc4man: My activity log manager reports many crash (up to 2013) before September 25th 2017 when I bought this PC, so if the 'identifier' is based on hardware the page I receive from Activity log manager does not belong to this hardware.
and espectro2 does not use my PC. Y see the same report from each partition of my multi-boot machine but espectro2 does not use the same machine.
@espectro2: Please help me to debug this problem because I fear a worse problem, the 1st 2 dates in my report are:
2013-05-28 22:05	2013-05-28 20:05 UTC	Crash	rhythmbox
2013-05-01 16:05	2013-05-01 16:05 UTC	Crash	skype
did you have the same? You was using the same PC at that time?

---

### Post by corradoventu on 2018-02-10
also after a new crash [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1748632](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1748632) i still have the same crash report from activity log managerf

---

### Post by espectro2 on 2018-02-10
About the date of the error on my machine started in
2018-01-07  01:01 2018-01-06 16:01 UTC Crash minergate just like the photo I posted  at the beginning of the topic about the torrent activate the minergate I  think it's strange because I do not use a torrent download program on  this machine I unsealed the transmission via interface through the program center although it still appears in dpkg -l
transmission-common
transmission-gtk

---

### Post by #&amp;thj^% on 2018-02-10
[U]**Hint>>>:** aMule - all-platform eMule P2P Client
[/U]
If you really want to uninstall transmission: (Don't  know why you would though) 	

To remove everything to do with transmission, use:

```
sudo apt-get purge transmission*
```

This will remove every package with the word transmission.
See my dry run :
```
sudo apt purge -s transmission*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'transmission-common' for glob 'transmission*'
Note, selecting 'transmission-remote-cli' for glob 'transmission*'
Note, selecting 'transmission-remote-gtk' for glob 'transmission*'
Note, selecting 'transmission-qt' for glob 'transmission*'
Note, selecting 'transmission' for glob 'transmission*'
Note, selecting 'transmission-daemon' for glob 'transmission*'
Note, selecting 'transmission-cli' for glob 'transmission*'
Note, selecting 'transmission-gtk' for glob 'transmission*'
Package 'transmission' is not installed, so not removed
Package 'transmission-cli' is not installed, so not removed
Package 'transmission-daemon' is not installed, so not removed
Package 'transmission-qt' is not installed, so not removed
Package 'transmission-remote-cli' is not installed, so not removed
Package 'transmission-remote-gtk' is not installed, so not removed
The following packages will be REMOVED:
  transmission-common* transmission-gtk*
0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
Purg transmission-gtk [2.92-3ubuntu2]
Purg transmission-common [2.92-3ubuntu2]
```

---

