---
title: "Azureus crashes often when having much files"
date: 2006-10-28
forum: Repositories &amp; Backports
---

### Post by Pixman on 2006-10-28
Hi guys,

the title says it mostly. When I'm handling a bunch of files, azureus crashes, both versions (GCJ & java-native). In the repository is 2.5.0 as far as I can see. I'm using Ubuntu Edgy.

I get this crash message after the main window opened:
> 
pixman@fuckup:~$ azureus 
changeLocale: *Default Language* != German (Switzerland). Searching without country..
changeLocale: Searching for language German in *any* country..
changeLocale: no message properties for Locale 'German (Switzerland)' (de_CH), using 'German (Germany)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x00000000, pid=10707, tid=3086137008
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  0x00000000
#
# An error report file with more information is saved as hs_err_pid10707.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


Then I downloaded the version from the source forge page, same version as said in the repository.
It uses the same configuration (from /home/username/.azureus ) and works perfectly.

Anyone experiencing the same issues, crashes etc.?

I think there's something wrong with the package.

Atleast I can use it atm with the SF.net version and so can you... but it isn't quite satisfying I guess. ;)

Greetings,
Michael

---

### Post by dyntryx on 2006-11-06
Yes, I had the same problem.  I also noticed that the icon in the system tray was constantly white, instead of showing the blue frog.  I just downloaded the archive from sourceforge, and it seems to be working fine.  I don't have any other solution to offer, but I can at least confirm that you're not the only one who experienced problems.

I'm also running Ubuntu Edgy, so the package in the Edgy repositories is probably borked or otherwise foobared. :???:

EDIT:

Something else I just noticed: when running the Azureus downloaded from the website, a download column called "rating" is shown by default.  This wasn't so with the package from the repositories.  Yet, both versions were listed as 2.5.0.0 when selecting Help -> About Azureus.  Not sure why, but maybe the packaged version installs some default settings? :???:

Not really that important, but that should be enough to conclude that the package version isn't configured correctly.

---

### Post by pirolla on 2006-11-22
The lusitan way to fix this is to remove your ~/.azureus directory...
But it seems not to work all the time... :-k 

Pirolla.

---

### Post by 8086 on 2007-05-24
I have resorted just to using commandline btlaunchmanycurses for the last 6 months... This truly blows. It normally only happens when seeding/leeching a lot of files (20+ perhaps). The reason it works to remove your .azureus-directory is that Azureus then forgets the 20 torrents. If you add them again, it will crash!

---

### Post by zilebune on 2007-09-19
Please check this link -> [https://launchpad.net/ubuntu/+source/azureus/+bug/95183](https://launchpad.net/ubuntu/+source/azureus/+bug/95183)

I had the same problem and followed the hint. Now Azureus is OK.
It seems there _is_ something wrong with the Ubuntu official package.

---

