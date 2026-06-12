---
title: "Blank screen after changing resolution w/Gallium on llvmpipe"
date: 2014-03-12
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-03-12
I maintain some nasty oldish hardware:

> VIA C7 CPU @ 1500MHz
VIA CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)
VIA VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
1GB DDR2 RAM

The P4M800 graphics chip was unusable in Saucy:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643)

But it's fixed in Trusty which now shows it's using Gallium on llvmpipe:

[http://ubuntuforums.org/attachment.php?attachmentid=251011&d=1394427642](http://ubuntuforums.org/attachment.php?attachmentid=251011&d=1394427642)

The general performance is really good in both Ubuntu flashback/w metacity and Lubuntu but if I change the resolution from the default 1366x768 on my 18.5 LCD display to my desired 1280x720 I then just get a blank screen, and that persists on reboot :(

There is no xorg.conf and trying to reset X through the recovery mode doesn't work so I'm clueless where to start :redface:

I'm a total dummy when it comes to filing bugs against X also ;)

---

### Post by cariboo on 2014-03-12
This bit from the bug reporting wiki page may help:

> Filing bugs when off-line
In the event that you have an issue with your Internet connection or want to file a bug for another system you can still do this using apport. 

First, on the target system, gather the information in a file:

For a bug report about a system crash:
apport-cli -p <package name> --save bug.crash

For a bug report about any other issue:
apport-cli -f -p <package name> --save bug.apport

You will need to answer a few questions, which will vary depending on which package the bug report is about. Relevant system information, including the package name, is then saved on the target system, in the current directory. The extension indicates if it is a crash report or another kind of report. If you decide to rename the report file, please keep the .apport or .crash extension.

When the file is ready, copy it to the system you intend to use for filing the report. There you can then file the report:

ubuntu-bug -c <apport_file.extension> 

Warning /!\ 'ubuntu-bug -c x.crash' does not work for crash reports from stable Ubuntu releases (see note about stable releases above).

If this is to be added to an existing bug report, also use the -u option:

ubuntu-bug -c <apport_file.extension> -u <bug number>

You will need to answer a few questions, and a web browser will be launched to complete the bug report. Please do not attach the .apport or .crash file to the report, as this is not the same as performing the above mentioned steps.

THe wiki page is located [here]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by kansasnoob on 2014-03-12
I did manage to get booted by deleting "~/.config/monitors.xml". Now to play :guitar:

---

