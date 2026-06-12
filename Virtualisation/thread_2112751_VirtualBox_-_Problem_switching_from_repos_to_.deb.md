---
title: "VirtualBox - Problem switching from repos to .deb"
date: 2013-02-05
forum: Virtualisation
---

### Post by wilko2205 on 2013-02-05
Hi. First off, I should probably warn you I've only been using linux for 2 weeks, so I'm a bit of a newbie. I'm on Ubuntu 12.10 and I started using VB last night by installing it from the repos. After working out that I needed to get the .deb package from the website to get USB support, I uninstalled VB with:

```
sudo apt-get purge virtualbox
```Then I installed the deb (32-bit) and tried to open the Windows 7 guest I had on the last version, and I got the following error:
> Failed to open a session for the virtual machine Windows 7.

The virtual machine 'Windows 7' has terminated unexpectedly during startup with exit code 1.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {22781af3-1c96-4126-9edf-67a020e0e858}

This was followed with another pop-up error:
> RTR3InitEx failed with rc=-1912 (rc=-1912)

The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing

'/etc/init.d/vboxdrv setup'

may correct this. Make sure that you do not mix the OSE version and the PUEL version of VirtualBox.I tried creating a new machine and got the same error. So I'm guessing something went wrong in the uninstall of the repo version. When installing the .deb version with *dpkg*, I  keep getting this: ```
 * Stopping VirtualBox kernel modules                                           
 * Cannot unload module vboxdrv
```As I said, I'm new to this kind of thing and couldn't even begin to guess what a Kernel Module is. Any ideas on how to fix this?

Thanks

---

### Post by SeijiSensei on 2013-02-05
Let's start with a simpler approach first.  First, did you read the [Linux downloads page]("https://www.virtualbox.org/wiki/Linux_Downloads") at virtualbox.org?  You should use the instructions presented there for "Debian-based distributions."  You need to add a line to /etc/apt/sources.list by opening a terminal and running "sudo nano /etc/apt/sources.list". Copy the line from the downloads page corresponding to your version of Ubuntu, and paste at the end of sources.list.  There doesn't seem to be an entry for 12.10 ("quantal"), so use the one for "precise" instead.  Then follow the rest of the steps.  You should end up with a working installation of VirtualBox 4.2.

Before doing this, run "sudo apt-get purge virtualbox*" to remove any lingering stuff from your previous attempts.

There's a chance this won't work because of the mismatch between Ubuntu versions.  (If you haven't got much invested in this version yet, I strongly recommend you reinstall from a [12.04.1 CD]("http://cdimage.ubuntu.com/releases/12.04.1/release/").  12.04 has "long-term support" through April of 2017; 12.10 will reach its "end-of-life" much sooner than that.  If you are committed to 12.10, there are ways around the problem you encountered, but they require installing additional software like the GCC compiler and the "headers" that match your current Linux kernel.  I'd go the 12.04 route myself unless you like fiddling with your machine.

---

### Post by wilko2205 on 2013-02-08
> **SeijiSensei said:**
> Let's start with a simpler approach first.  First, did you read the [Linux downloads page]("https://www.virtualbox.org/wiki/Linux_Downloads") at virtualbox.org?  You should use the instructions presented there for "Debian-based distributions."  You need to add a line to /etc/apt/sources.list by opening a terminal and running "sudo nano /etc/apt/sources.list". Copy the line from the downloads page corresponding to your version of Ubuntu, and paste at the end of sources.list.  There doesn't seem to be an entry for 12.10 ("quantal"), so use the one for "precise" instead.  Then follow the rest of the steps.  You should end up with a working installation of VirtualBox 4.2.

Before doing this, run "sudo apt-get purge virtualbox*" to remove any lingering stuff from your previous attempts.

There's a chance this won't work because of the mismatch between Ubuntu versions.  (If you haven't got much invested in this version yet, I strongly recommend you reinstall from a [12.04.1 CD]("http://cdimage.ubuntu.com/releases/12.04.1/release/").  12.04 has "long-term support" through April of 2017; 12.10 will reach its "end-of-life" much sooner than that.  If you are committed to 12.10, there are ways around the problem you encountered, but they require installing additional software like the GCC compiler and the "headers" that match your current Linux kernel.  I'd go the 12.04 route myself unless you like fiddling with your machine.

Ahhhhh there we go. I saw the ubuntu packages and assumed that was it. I should have read on, it's working now. Thanks!

I'm running Ubuntu from a partition on a friend's old laptop, I'll be getting my new one in a week or so, so I'll be doing a fresh install. Is 12.04 really better in the long run? As a newcomer I just assumed I'd be better off with the latest version.

---

