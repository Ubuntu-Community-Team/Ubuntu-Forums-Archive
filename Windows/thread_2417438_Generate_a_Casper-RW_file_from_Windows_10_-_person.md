---
title: "Generate a Casper-RW file from Windows 10 - personal research notes"
date: 2019-04-23
forum: Windows
---

### Post by boqsc on 2019-04-23
Why I created this thread instead of using Github, Gitlab or a simple note applicatoin?
[LIST]
[*]**I will probably Google for this thread myself**
[*]The **GitHub **of mine is very very disorganized, filled with random projects, **It is hard to organise anything at all there**.
[*]**Gitlab**, I do not want to deal with cross-hosted authentication. 
*Example:*
[LIST]
[*]**Gnome **have their **Gitlab** [https://gitlab.gnome.org/users/sign_in]("https://gitlab.gnome.org/users/sign_in?redirect_to_referer=yes") ,
[*]**freedesktop **have theirs [https://gitlab.freedesktop.org/]("https://gitlab.freedesktop.org/freedesktop/freedesktop")[users/sign_in]("https://gitlab.gnome.org/users/sign_in?redirect_to_referer=yes"),
[*]**Gitlab **himself have his [https://gitlab.com/users/sign_in](https://gitlab.com/users/sign_in)

That's a lot to deal with, and a lot of signups to deal with, easy to not remember in which one you created your repository or snippets.
[/LIST]
[/LIST]
[HR][/HR]

**[SIZE=4]Research on creating casper-rw file [Linux][/SIZE]**

**casper-rw** is a simple ANSI text file filled with **NUL** special symbol **and later formatted as a partition** with a file system **Ext2**, Ext3 or even Ext4.

To create **casper-rw** In Linux:
 
[LIST]
[*]we use **GNU Core Utils **tool: **[dd]("https://en.wikipedia.org/wiki/Dd_(Unix)")**
[LIST]
[*]A tool** &#8203;**copies and converts a file
[/LIST]

[*]and we use **Util-linux **tool: **[mkfs]("https://en.wikipedia.org/wiki/Mkfs") (also known as mke2fs)**
[LIST]
[*]A tool create an ext2/ext3/ext4 filesystem
[/LIST]
[/LIST]
[U]Generaly this is how the Linux bash script would look like: 

[/U]After executing this **create-casper-rw.sh **script, you will have a **completely working casper-rw image file -** ready to be dropped into your livecd.

Simple  **create-casper-rw.sh **script with minimal comments 

```

**#!/usr/bin/env bash**

**# Writes 1M-egabyte of ****NUL characters**** for 512 times, to a file named "casper-rw" - Creates 512 megabytes file.     **
[FONT=Verdana]dd if=/dev/zero of=casper-rw bs=1M count=512

[/FONT]**# Using mke2fs binary to format casper-rw file to ext3 file system**
mkfs.ext3 -L casper-rw -F casper-rw[FONT=Verdana]

[/FONT]
```
The same **create-casper-rw.sh **with more advanced commenting.
```

[B]#!/usr/bin/env bash
[/B]
**# Writes 1M-egabyte of ****NUL characters**** for 512 times, to a file named "casper-rw" - Creates 512 megabytes file.     **
dd if=/dev/zero of=casper-rw bs=1M count=512

**      # if=FILE**
      #       read from FILE instead of stdin

**          # if=/dev/zero**
          #      read from device file "/dev/zero" instead of stdin

             [B]# Device FILE "/dev/zero", is a device that prints a NUL character.

[/B]**      # of=FILE**
      #       write to FILE instead of stdout

**        # of=casper-rw**
        #      write to FILE "casper-rw" instead of stdout    





**# Using mke2fs binary to format casper-rw file to ext3 file system**
mkfs.ext3 -L casper-rw -F casper-rw

[B]  # -L new-volume-label
  [/B]# Set the volume label for the filesystem to new-volume-label. The maximum length of the volume label is 16 bytes.[B]

  # -F
  [/B]# Force mke2fs to create a filesystem, even if the specified device is not a partition on a block special device, or if other parameters do not make sense. In order to force mke2fs to create a filesystem even if the filesystem appears to be in use or is mounted (a truly dangerous thing to do), this option must be specified twice.

  [B]# device 
[/B]  # A path to a device (example: /home/myusername/desktop/casper-rw)





```



[HR][/HR]
On Windows operating systems, however, we do not have such dedicated tools, that's why I'm here to help.

**[SIZE=5]Mimicking the functionality in Windows 10 Environment[/SIZE]**

To create **casper-rw** In Windows:


[LIST]
[*]From the **chrysocome.net project**, we will borrow a port of** dd**, that has ability to emulate **Device FILE "/dev/zero" **
[LIST]
[*]**&#8203;**(This project contains required **ddrelease64.exe binary**)
[/LIST]

[*]**[SIZE=4][SIZE=2]We will also use [Ext2Fsd Project]("https://www.ext2fsd.com/") [/SIZE][/SIZE]**
[LIST]
[*][SIZE=4][SIZE=2]Open source ext3/4 file system driver for Windows (2K/XP/WIN7/WIN8)[/SIZE][/SIZE]
[*]**[SIZE=4][SIZE=2]([/SIZE][/SIZE]**[SIZE=4][SIZE=2]this project contains required  fully functional portable [/SIZE][/SIZE]**[SIZE=4][SIZE=2]mke2fs.exe[/SIZE][/SIZE]**[SIZE=4][SIZE=2] binary)[/SIZE][/SIZE]
[/LIST]
[/LIST]
[SIZE=5]
[/SIZE]Simple **create-casper-rw.cmd **with minimal commenting```
@echo off
[SIZE=5]
[/SIZE]**:: Writes 1M-egabyte of ****NUL characters**** for 512 times, to a file named "casper-rw" - Creates 512 megabytes file.     **
dd\ddrelease64.exe if=/dev/zero of=casper-rw bs=1M count=512[SIZE=5]

[/SIZE]**:: Using Ext2Fsd binary to format casper-rw file to ext3 file system on Windows 10**
Ext2Fsd\Setup\mke2fs.exe -t ext3 C:\Users\boqsc\Desktop\Ext2Fsd\Setup\casper-rw


[SIZE=5]
[/SIZE]
```[SIZE=5]

New found - latest discoveries:
[/SIZE]
[LIST]
[*][SIZE=5][SIZE=2]Windows operating systems have built-in [/SIZE][/SIZE]**fsutil utility **for generation of the same Nul files** that dd generates.**[SIZE=5]
[/SIZE]
[LIST]
[*][SIZE=5][SIZE=2]Nul dummy files can also be generated using[/SIZE] [/SIZE]```
**fsutil **file createnew **casper-rw** 10737418240
```, this will generate 10gb file **filled with Nul characters**.[SIZE=5]
[/SIZE]
[/LIST]
[/LIST]
[SIZE=5]
[/SIZE]
[LIST]
[*]There is a new untested version of Ext2Fsd, called [Ext3Fsd]("https://github.com/matt-wu/Ext3Fsd"), [https://github.com/matt-wu/Ext3Fsd](https://github.com/matt-wu/Ext3Fsd)
[/LIST]

More about Casper:[URL="http://manpages.ubuntu.com/manpages/bionic/man7/casper.7.html"]
http://manpages.ubuntu.com/manpages/bionic/man7/casper.7.html[/URL]

---

### Post by boqsc on 2019-05-03
[SIZE=4]Windows [/SIZE]**[SIZE=4]makePersistent.cmd [/SIZE]**[SIZE=4]- Linux tools version

[SIZE=2]**To use this script, you will need dependecies** (If you won't have those, the script is useless)
[/SIZE][/SIZE]
[LIST]
[*]From the [**chrysocome.net Project**]("http://www.chrysocome.net/"), we will borrow a port of** dd**, that has ability to emulate **Device FILE "/dev/zero"**
[LIST]
[*]**&#8203;**(This project contains required **ddrelease64.exe binary**)
[*]Download: [http://www.chrysocome.net/download](http://www.chrysocome.net/download)
[/LIST]

[*]**[SIZE=4][SIZE=2]We will also use [Ext2Fsd Project]("https://www.ext2fsd.com/")[/SIZE][/SIZE]**
[LIST]
[*][SIZE=4][SIZE=2]Open source ext3/4 file system driver for Windows (2K/XP/WIN7/WIN8)[/SIZE][/SIZE]
[*]**[SIZE=4][SIZE=2]([/SIZE][/SIZE]**[SIZE=4][SIZE=2]this project contains required fully functional portable [/SIZE][/SIZE]**[SIZE=4][SIZE=2]mke2fs.exe[/SIZE][/SIZE]**[SIZE=4][SIZE=2] binary)
[/SIZE][/SIZE]
[*][SIZE=4][SIZE=2]Download: [/SIZE][/SIZE][https://sourceforge.net/projects/ext2fsd/](https://sourceforge.net/projects/ext2fsd/)
[/LIST]
[/LIST]
[SIZE=4][SIZE=2]
 [/SIZE]
[/SIZE]


Copy and paste this script into a text file named **[SIZE=2]makePersistent.cmd[/SIZE]**[SIZE=2], remember to download and place dependencies (mentioned above) next to this file.

The file [/SIZE]hierarchy[SIZE=2] you should have:
[LIST]
[*]**dd/[B]ddrelease64.exe** [/B]sub-folder and file
[*]**Ext2Fsd/Setup/mke2fs.exe **sub-folder and file
[*]**[SIZE=2]makePersistent.cmd [/SIZE]**[SIZE=2]file[/SIZE]
[/LIST]


[/SIZE]
```
@echo off && TITLE Generate casper-rw of Ubuntu ( also known as live-rw of Debian)


:: BUGFIX FOR WINDOWS SYSTEMS
:: Running this batch script as Administrator changes current working 
:: directory's path to "C:\Windows\system32", that's bad, huh.


:: Enhanced %~dp0 variable
:: is the path to the current makePersistent.cmd directory


:: Explanation
:: %0 argument variable is simply expanded by ~dp variable modifiers
:: to extract the current makePersistent.cmd directory


:: Reason
:: Launching Batch file with Administrator privilegies, the path of this batch program 
:: is always set to "C:\Windows\system32>". 


:: After applying this fix, this Batch file 
:: now will always point to its current directory instead of "C:\Windows\system32>".
set "dp0=%~dp0"
set "dp0WithoutBackslash=%dp0:~0,-1%" 
PUSHD "%dp0WithoutBackslash%"






:: Main parts of this script


:: The name of the output file
set "nameOfTheOutputFile=casper-rw"


:: Delete Previously generated casper-rw file (If it was generated before)
IF Exist "%nameOfTheOutputFile%" ( Del "%nameOfTheOutputFile%" )


:: Generate a new dummy file
"dd\ddrelease64.exe" if=/dev/zero of=%nameOfTheOutputFile% bs=1M count=2


:: Convert this dummy file to Linux Ext2 or Ext3 filesystem 
echo "Simulate Press Enter" | "Ext2Fsd\Setup\mke2fs.exe" -t "ext3" "%cd%\%nameOfTheOutputFile%"


:: Simply, a reminder that All the steps required to create Casper-rw were completed.
echo "Casper-rw file is ready."


:: Additional steps can be added to copy/move Casper-rw file into USB containing Livecd of Ubuntu. 
  
  ::move /Y "casper-rw" "path/to/usb-device" 


pause

```

---

