---
title: "Libeoffice Offline Help"
date: 2021-03-27
forum: Ubuntu/Debian BASED
---

### Post by artist-wavenet on 2021-03-27
I installed LibreOffice using the Ubuntu's Software application. When I open Libreoffice Writer and navigate to: "Help => LibreOffice Help" I get a message box that says:
> The LibreOffice built-in help for current UI language (English (USA)) is not installed on your computer

How does one install this built-in help for LibreOffice installations done with the Ubuntu's Software application? I need to access this help while offline.

My OS is Ubuntu 18.04

---

### Post by ActionParsnip on 2021-03-27
[https://comeandtechit.wordpress.com/2020/04/28/the-libreoffice-built-in-help-for-current-ui-language-english-usa-is-not-installed-on-your-computer/](https://comeandtechit.wordpress.com/2020/04/28/the-libreoffice-built-in-help-for-current-ui-language-english-usa-is-not-installed-on-your-computer/)

---

### Post by artist-wavenet on 2021-03-27
I did as the webpage at the link you provided recommends and used the command:
> sudo apt-get install libreoffice-help-en-us

This had no effect. The message box still shows no built-in help is installed.

In the output of that apt-get command I see these lines:
> 
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'

I do not know it this has anything to do with LibreOffice being unable to find this help installation.

There were no other error messages, or warnings.

---

### Post by mikewhatever on 2021-03-27
What was the full output of the installation command?
Also, probably obvious,but you need to relaunch LO.

---

### Post by CelticWarrior on 2021-03-27
> [COLOR=#000000]My OS is Ubuntu 18.04[/COLOR]
... So you should have Libreoffice installed by default, the standard minimal office trio: Writer, Calc, Impress. Other elements can and often need to be installed later.
And it seems you *just* installed Ubuntu... If so, why 18.04? The current LTS release is 20.04. 

> [COLOR=#000000]I installed LibreOffice using the Ubuntu's Software application[/COLOR]
What exactly have you installed?
FYI, at Ubuntu Software you can find software that is in the Ubuntu repository and is installed with the "traditional" way (apt) or software that is a snap. Some programs only exist in one version but many have both. If you installed the snap version then the instructions above aren't applicable.

---

### Post by artist-wavenet on 2021-03-27
When I upgraded my laptop from Pop!_OS 18.04, to Pop!_OS 20.04, I lost all content on my laptop's drives. That loss is easily recoverable from. But this would not be so on my desktop where I do my work. Too much time has been invested in software installations. There are a lot of files I cannot afford to risk losing, so a lot of backing up would have to be done. I do not have time for it.

LibreOffice was installed by an Ubuntu system application named simply "Software" which is a core part of the Ubuntu OS.

Here is the entire apt-get output you requested:

```

$ sudo apt-get install libreoffice-help-en-us

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libreoffice-base-core libreoffice-common libreoffice-core libreoffice-math
  libreoffice-style-galaxy libreoffice-style-tango libreoffice-writer
  python3-uno
Suggested packages:
  libreoffice-base fonts-crosextra-caladea fonts-crosextra-carlito
  libreoffice-java-common
The following NEW packages will be installed:
  libreoffice-base-core libreoffice-common libreoffice-core
  libreoffice-help-en-us libreoffice-math libreoffice-style-galaxy
  libreoffice-style-tango libreoffice-writer python3-uno
0 upgraded, 9 newly installed, 0 to remove and 1 not upgraded.
Need to get 71.4 MB of archives.
After this operation, 288 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libreoffice-style-galaxy all 1:6.0.7-0ubuntu0.18.04.10 [1540 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libreoffice-style-tango all 1:6.0.7-0ubuntu0.18.04.10 [1308 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libreoffice-common all 1:6.0.7-0ubuntu0.18.04.10 [24.7 MB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libreoffice-core amd64 1:6.0.7-0ubuntu0.18.04.10 [31.9 MB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libreoffice-base-core amd64 1:6.0.7-0ubuntu0.18.04.10 [704 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libreoffice-writer amd64 1:6.0.7-0ubuntu0.18.04.10 [8318 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libreoffice-help-en-us all 1:6.0.7-0ubuntu0.18.04.10 [2449 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libreoffice-math amd64 1:6.0.7-0ubuntu0.18.04.10 [395 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 python3-uno amd64 1:6.0.7-0ubuntu0.18.04.10 [123 kB]
Fetched 71.4 MB in 4s (16.9 MB/s)     
Selecting previously unselected package libreoffice-style-galaxy.
(Reading database ... 390406 files and directories currently installed.)
Preparing to unpack .../0-libreoffice-style-galaxy_1%3a6.0.7-0ubuntu0.18.04.10_all.deb ...
Unpacking libreoffice-style-galaxy (1:6.0.7-0ubuntu0.18.04.10) ...
Selecting previously unselected package libreoffice-style-tango.
Preparing to unpack .../1-libreoffice-style-tango_1%3a6.0.7-0ubuntu0.18.04.10_all.deb ...
Unpacking libreoffice-style-tango (1:6.0.7-0ubuntu0.18.04.10) ...
Selecting previously unselected package libreoffice-common.
Preparing to unpack .../2-libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb ...
Unpacking libreoffice-common (1:6.0.7-0ubuntu0.18.04.10) ...
Selecting previously unselected package libreoffice-core.
Preparing to unpack .../3-libreoffice-core_1%3a6.0.7-0ubuntu0.18.04.10_amd64.deb ...
Unpacking libreoffice-core (1:6.0.7-0ubuntu0.18.04.10) ...
Selecting previously unselected package libreoffice-base-core.
Preparing to unpack .../4-libreoffice-base-core_1%3a6.0.7-0ubuntu0.18.04.10_amd64.deb ...
Unpacking libreoffice-base-core (1:6.0.7-0ubuntu0.18.04.10) ...
Selecting previously unselected package libreoffice-writer.
Preparing to unpack .../5-libreoffice-writer_1%3a6.0.7-0ubuntu0.18.04.10_amd64.deb ...
Unpacking libreoffice-writer (1:6.0.7-0ubuntu0.18.04.10) ...
Selecting previously unselected package libreoffice-help-en-us.
Preparing to unpack .../6-libreoffice-help-en-us_1%3a6.0.7-0ubuntu0.18.04.10_all.deb ...
Unpacking libreoffice-help-en-us (1:6.0.7-0ubuntu0.18.04.10) ...
Selecting previously unselected package libreoffice-math.
Preparing to unpack .../7-libreoffice-math_1%3a6.0.7-0ubuntu0.18.04.10_amd64.deb ...
Unpacking libreoffice-math (1:6.0.7-0ubuntu0.18.04.10) ...
Selecting previously unselected package python3-uno.
Preparing to unpack .../8-python3-uno_1%3a6.0.7-0ubuntu0.18.04.10_amd64.deb ...
Unpacking python3-uno (1:6.0.7-0ubuntu0.18.04.10) ...
Setting up libreoffice-style-galaxy (1:6.0.7-0ubuntu0.18.04.10) ...
Setting up libreoffice-style-tango (1:6.0.7-0ubuntu0.18.04.10) ...
Setting up libreoffice-common (1:6.0.7-0ubuntu0.18.04.10) ...
Setting up libreoffice-core (1:6.0.7-0ubuntu0.18.04.10) ...
Setting up python3-uno (1:6.0.7-0ubuntu0.18.04.10) ...
Setting up libreoffice-math (1:6.0.7-0ubuntu0.18.04.10) ...
Setting up libreoffice-base-core (1:6.0.7-0ubuntu0.18.04.10) ...
Setting up libreoffice-writer (1:6.0.7-0ubuntu0.18.04.10) ...
Setting up libreoffice-help-en-us (1:6.0.7-0ubuntu0.18.04.10) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for gnome-icon-theme (3.12.0-3) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for shared-mime-info (1.9-2) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
@ubuntu:~$ 

```

---

### Post by CelticWarrior on 2021-03-28
> [COLOR=#000000]When I upgraded my laptop from Pop!_OS 18.04, to Pop!_OS 20.04, I lost all content on my laptop's drives.[/COLOR]
That happens when users don't know what they're doing and even when they do, drives can fail anytime. Backups are a MUST. 

> [COLOR=#000000]There are a lot of files I cannot afford to risk losing, so a lot of backing up would have to be done.[/COLOR]
Yes, please, ASAP.

> [COLOR=#000000]I do not have time for it.[/COLOR]
So, contrary to the previous sentence, you can afford losing your personal data, after all? 

> [COLOR=#000000]LibreOffice was installed by an Ubuntu system application named simply "Software" which is a core part of the Ubuntu OS.[/COLOR]
You already post that at the beginning. Unlike what you might think I'm generally pretty good at reading and understanding. It's pretty clear that you installed Libreoffice and how but the questions above remains, WHY and WHAT?

Re: WHY?
Libreoffice IS installed by default in standard Ubuntu and most of the flavors. Have you uninstalled Libreoffice, purposefully select some sort of minimal installation or what? And, again, it seems you just installed. Why choose 18.04 and not 20.04? Or is it the case that you have some other Ubuntu based distro like Pop_OS (although AFAIK Pop also installs Libreoffice by default), or what?

Re: WHAT?
Looking at was installed along (dependencies) the help file it seems that what you installed was the SNAP version. That would having been good to know as a proper answer to a pertinent question instead of ignoring what was told and paraphrasing. This is actually the most crucial detail to understand your problem.

Possible results: By now you probably have two offices or at least Libreoffice Writer installed from two different and independent sources. The help file you were suggested to install only applies to ONE of them, the one from the Ubuntu repository (the traditional way) that was installed now...

```
[COLOR=#000000][FONT=&quot]The following NEW packages will be installed:[/FONT][/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000]  libreoffice-base-core libreoffice-common libreoffice-core
  libreoffice-help-en-us libreoffice-math libreoffice-style-galaxy libreoffice-style-tango [/COLOR][/FONT]**libreoffice-writer**[FONT=Ubuntu Mono, monospace][COLOR=#000000] python3-uno[/COLOR][/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]
```

[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]So, the recently installed Writer should now work with the offline help but the previously installed snap won't.


[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Please understand that pilling up mistakes and bad practices on top of other mistakes and bad practices all mixed with willful ignorance can only lead to bad results.[/FONT]

---

### Post by The Cog on 2021-03-28
> There are a lot of files I cannot afford to risk losing, so a lot of backing up would have to be done. I do not have time for it.
What would the cost be in time and money to make a backup?
What would the cost be in time and money to recover from total loss of those files (hardware failure, power cut, software crash perhaps)?
Without a backup, you are really playing Russian Roulette every day. Do you feel lucky?

---

### Post by howefield on 2021-03-28
Thread moved to the "*Ubuntu/Debian BASED*" forum in the meantime.

---

### Post by kurt18947 on 2021-03-29
Is this helpful? PDF downloads 

[https://documentation.libreoffice.org/en/english-documentation/](https://documentation.libreoffice.org/en/english-documentation/)

---

### Post by ajgreeny on 2021-03-29
What does command ***snap list*** show as output?

I suspect t it will show us that you have the snap version of LO, but as has already been asked, the question is "why?" You should already have had LO installed by default.

---

### Post by artist-wavenet on 2021-03-31
I know now what that help installation command did. There were two installations of LibreOffice. One was done with apt-get and this was version 6. The other was done with the Software Center and is version 7. That help installation command installed offline help for version 6 only. The need is to have it for the Software Center installed version 7.

LibreOffice 6 is now removed.

The Pop!_OS upgrade on my latpot was installed by means of the upgrade prompt I was getting whenever I booted. Everything was done exactly as instructed in that procedure. The result was just as if there was a completely new installation of the OS. Something went wrong in the upgrade. My laptop's drives are working fine.

My desktop computer is custom built, with two identical disk drives that reviews said were the most reliable on the market. The two drives are RAID 1 mirrored, so I already have a back up of sorts. I do not have time to do better. Upgrading my desktop without off computer backup is something I do not have time for now. I cannot risk doing it without such a back up. And even with off computer backup if something goes wrong I do not have time to reinstall all the software. Ubuntu 18.04 meets the need for now.

---

### Post by artist-wavenet on 2021-03-31
x

---

