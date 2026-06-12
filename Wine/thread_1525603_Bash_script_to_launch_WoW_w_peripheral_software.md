---
title: "Bash script to launch WoW w/ peripheral software"
date: 2010-07-07
forum: Wine
---

### Post by themonkeymoo on 2010-07-07
I have written a bash script that improves some aspects of WoW performance when running on linux via wine. It does any/all of the following:

*Loads folders containing frequently-written files into a RAMdisk (this improves performance when large numbers of file writes occur; usually during exit/logout). This can vastly reduce the time it takes to switch characters, as well as somewhat improve addon performance overall.
*Launches peripheral software (VOIP, addon updater, etc...)
*Automatically closes peripheral software and cleans RAMdisk when WoW exits.
*Natively supports:
**mangler (free, open-source, linux-native VOIP client that interfaces with ventrilo servers; requires speex codec)
**WUU (WoW UI Updater; free, python-based addon updater; interfaces with most addon hosting sites)
**nostromo_daemon (configuration and keymapping daemon for Nostromo Speedpad series gaming mini keyboards)
*User-configurable for alternatives to above software and nonstandard WoW install path/RAMdisk path
*Automagically configures your WoW folder to make use of a RAMdisk

USES A LOT OF RAM; IF YOU RUN A LARGE NUMBER OF ADDONS, YOUR RAMDISK MAY CONTAIN UPWARDS OF 1.5GB OF DATA!!!!

WHAT IT DOES NOT DO!!!:
*Set up a RAMdisk on your computer
**You must have a user-accessible RAMdisk already set up on your system. If you use a recent version of Ubuntu, this is already available at /dev/shm by default (and the script will use this path). Setting up a user-accessible RAMdisk requires root access and editing of your /etc/fstab file.

IF YOU DO NOT KNOW HOW TO SET UP A RAMDISK OR WHAT A RAMDISK IS, DO NOT USE THIS SCRIPT.

The script is available at sourceforge.net/projects/wowlaunchersh
It consists of two separate files (wowlauncher.sh and wowlauncher.funcs); both are required for the script to function

---

