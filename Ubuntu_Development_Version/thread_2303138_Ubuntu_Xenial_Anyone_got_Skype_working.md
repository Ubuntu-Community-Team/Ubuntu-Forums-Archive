---
title: "Ubuntu Xenial: Anyone got Skype working?"
date: 2015-11-16
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-11-16
Try it 3 times:
Ubuntu Software Center: Apport error sent
Synaptic: Fix broken package first (message)
Command lines: Skype-bin is missing
So how do I fix broken packages and/or Skype-bin

---

### Post by sammiev on 2015-11-16
Hi Mike,

No troubles with Skype on my end with Xenial.

I downloaded it from [here]("http://www.skype.com/en/download-skype/skype-for-computer/").

---

### Post by MikeMecanic on 2015-11-16
@ sammiev
Thanks for replying!
Already try that link. Which version did you choose? Try the 12.04 one, open it with Ubuntu Software Center but didn't succeed.  Should I give it a second try? 

Smile!

---

### Post by sammiev on 2015-11-16
Hi Mike,

I used 12.04

You may have broken packages.

I would run:

```
sudo apt-get update && sudo apt-get upgrade
```

See what errors it throws back at you.

---

### Post by MikeMecanic on 2015-11-16
Already try that link also that appears to be that one:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

Here's the result, last command line:

```
The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.
```

Its exactly where I'm stuck.  Succeed ounce, shown n the dash board but it won't open?

Should I try via Software Center now?

Edit: [COLOR=#333333][FONT=Ubuntu]Problem in skype-bin [/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The problem cannot be reported: [/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]This is not an official Ubuntu package. Please remove any third party package and try again.[/FONT][/COLOR]

---

### Post by MikeMecanic on 2015-11-16
> **sammiev said:**
> Hi Mike,

I used 12.04

You may have broken packages.

I would run:

```
sudo apt-get update && sudo apt-get upgrade
```

See what errors it throws back at you.

No error there

```
Calculating upgrade... Done
The following packages will be upgraded:
  gedit gedit-common libsigc++-2.0-0v5 ubuntu-desktop ubuntu-minimal
  ubuntu-standard
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 559 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ubuntu.mirror.rafal.ca/ubuntu/ xenial/main ubuntu-minimal amd64 1.342 [3,024 B]
Get:2 http://ubuntu.mirror.rafal.ca/ubuntu/ xenial/main ubuntu-standard amd64 1.342 [3,082 B]
Get:3 http://ubuntu.mirror.rafal.ca/ubuntu/ xenial/main gedit-common all 3.18.2-1ubuntu2 [132 kB]
Get:4 http://ubuntu.mirror.rafal.ca/ubuntu/ xenial/main gedit amd64 3.18.2-1ubuntu2 [406 kB]
Get:5 http://ubuntu.mirror.rafal.ca/ubuntu/ xenial/main libsigc++-2.0-0v5 amd64 2.6.2-1 [11.1 kB]
Get:6 http://ubuntu.mirror.rafal.ca/ubuntu/ xenial/main ubuntu-desktop amd64 1.342 [4,054 B]
Fetched 559 kB in 0s (1,201 kB/s)          
(Reading database ... 210129 files and directories currently installed.)
Preparing to unpack .../ubuntu-minimal_1.342_amd64.deb ...
Unpacking ubuntu-minimal (1.342) over (1.341) ...
Preparing to unpack .../ubuntu-standard_1.342_amd64.deb ...
Unpacking ubuntu-standard (1.342) over (1.341) ...
Preparing to unpack .../gedit-common_3.18.2-1ubuntu2_all.deb ...
Unpacking gedit-common (3.18.2-1ubuntu2) over (3.18.2-1ubuntu1) ...
Preparing to unpack .../gedit_3.18.2-1ubuntu2_amd64.deb ...
Unpacking gedit (3.18.2-1ubuntu2) over (3.18.2-1ubuntu1) ...
Preparing to unpack .../libsigc++-2.0-0v5_2.6.2-1_amd64.deb ...
Unpacking libsigc++-2.0-0v5:amd64 (2.6.2-1) over (2.6.1-3) ...
Preparing to unpack .../ubuntu-desktop_1.342_amd64.deb ...
Unpacking ubuntu-desktop (1.342) over (1.341) ...
Processing triggers for gconf2 (3.2.6-3ubuntu5) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libglib2.0-0:amd64 (2.47.1-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.2~bzr0+16.04.20151104-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Setting up ubuntu-minimal (1.342) ...
Setting up ubuntu-standard (1.342) ...
Setting up gedit-common (3.18.2-1ubuntu2) ...
Setting up gedit (3.18.2-1ubuntu2) ...
Setting up libsigc++-2.0-0v5:amd64 (2.6.2-1) ...
Setting up ubuntu-desktop (1.342) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
xenial@hp:~$
```

Give it a second try in Ubuntu Software Center:  See screenshot

---

### Post by sammiev on 2015-11-16
Hi Mike,

I would use Synaptic Package Manager (available in the Software Center) is a graphical tool for managing packages, and among many features it allows you to filter packages by their state. In few clicks, by selecting the desired category on the left panel, you will be presented with the list of packages that require fixing.

---

### Post by MikeMecanic on 2015-11-16
To quote myself

> **MikeMecanic said:**
> Try it 3 times:
Ubuntu Software Center: Apport error sent
Synaptic: Fix broken package first (message)
Command lines: Skype-bin is missing
So how do I fix broken packages and/or Skype-bin

See screenshot: Stock there since 2 days.  Try it without the green files (discover today that they are part of the patch) on the 14th.  Returns the same message with the green files: Pyton and Skytools. The missing piece is the command lines to reach Skype.  It's up to you!

P.S.:  Take good note that Proposed was turn OFF Saturday night.

---

### Post by MikeMecanic on 2015-11-16
1)  Enable Proposed and discover that 2 Canonical files were not enable: enable them (Out of nowhere)
2)  Switch to main server (pretty slow these days): Reload and run Software Updater
3)  Try X64 version via Software Center: Didn't work
4)  Install the debian version in Ubuntu Software Center: Skype-install.deb (Debian version)
5)  As a gift for my birthday, Irunning the version 4.3.0.37


Thanks for help, smile and take care,

Edit:

The Python files and the Skype tools files are not part of the installation (Synaptic Screenshot Post #8).  The 3 files in the Home folder 32/64 bit Beta, plus the .deb file remain a mystery (they are not related to the download file below nor in post #2). I don't know how they arrived there (Debian Screenshot in Post #9).  Must be in my multiple attempts last Saturday to install Skype.  I do believe that the bug was caused by Software Updater wrong configuration (out of nowhere screenshot Post #9).  I tried today to install it directly from Ubuntu Software Center and it worked.  The only difference is that it contains 2 files (seen from Synaptic): Skype and Skype-bin i386.


**Here's the sequence to properly install Skype in Ubuntu Xenial Xerux:**


[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

i386

```
sudo dpkg --add-architecture i386
```


```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
```


```
sudo apt-get update && sudo apt-get install skype
```

Version 12.04

[http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/)
Open it in Ubuntu Software Center.

---

### Post by sammiev on 2015-11-16
Great to hear and Happy Birthday!!! =d>

---

### Post by MikeMecanic on 2015-11-17
Edit Post #9 for a better understanding.  Thanks ounce again Sammiev.

---

