---
title: "Script to auto-update manually installed NVIDIA drivers"
date: 2013-05-11
forum: Tutorials
---

### Post by terminator14 on 2013-05-11
**What it is:**

This is a script that will, as the title says, automatically update drivers that were downloaded from the NVIDIA website every time your kernel updates. Without this script, it is very likely that after a kernel update occurs, you will be dropped down to a terminal at next reboot and will be forced to reinstall the driver without a GUI. It's not really a big deal, but it can get annoying to do that every time, so this script does it for you.

The idea is similar to the one found here: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573), but has the following advantages:

[list]
[*]Updates the entire driver (including NVIDIA X Server Settings application)
[*]Downloads and installs the latest driver from NVIDIA[/list]
**What it does:**

The script contains 2 other scripts:

/etc/kernel/postinst.d/nvidia:
[list]
[*]Runs when a kernel update has been installed
[*]Adds a line to /etc/rc.local which will change the active tty to tty2 at next boot
[*]Modifies /etc/init/tty2.conf to make tty2 load the nvidia_updater script instead of asking for login credentials[/list]

/usr/src/nvidia/nvidia_update.sh:
[list]
[*]Runs at boot after a kernel update
[*]Launches the nvidia driver install package with the --update option to tell it to download the latest version of the driver before installing it.
[*]Removes the changes to rc.local so that next reboot, the system boots normally[/list]

**How to use:**

Running the script for the first time will create a folder called /usr/src/nvidia/ and tell you to download the proper driver from NVIDIA's website and rename it to /usr/src/nvidia/nvidia-driver. Do that, and run the script again. Since all it does is change a few text based config files, it "installs" almost instantly.

**Uninstall:**

Run "./script.sh --uninstall" to undo all changes the script makes to your system.

**Warning:**

While individual parts of the script have been tested multiple times, the fact that it deals with a video driver that can't be installed into a virtual machine makes it more difficult to test. I wrote the script to be as safe as possible, but for now, consider the script experimental. Do not run it on production machines without testing it first.

**Where to get it:**

In order to get the latest version of the script, first install git:

```
sudo apt-get install git
```

Once that's done, run:

```
git clone git://github.com/terminator14/nvidia_updater.git
```

This will create an nvidia_updater folder in your current working directory with the script in it. Keep in mind that there may be different versions of the script in the folder that is created - each file is labelled for the OS it will work for. You only need to run the one that corresponds to your OS.

**Special Mentions:**

Thanks to matt_symes for his contributions

---

### Post by terminator14 on 2013-05-14
Feedback anyone? Does it work for you? Are there problems?

---

