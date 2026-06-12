---
title: "Share with us your Groovy Gorilla installation/Upgrade Experience"
date: 2020-10-26
forum: Ubuntu, Linux and OS Chat
---

### Post by wildmanne39 on 2020-10-26
Groovy Gorilla was released October 22, 2020, so it's time for a new poll. Please tell us about your experience upgrading, or doing a fresh install of Groovy Gorilla.

This thread is only for your experience, if you are having problems, please create a thread in the support forums.

The previous poll can be found here:

[https://ubuntuforums.org/showthread.php?t=2441657](https://ubuntuforums.org/showthread.php?t=2441657)

---

### Post by Dennis N on 2020-10-29
I did two upgrades from Ubuntu 20.04 to 20.10 - both were uneventful and quick. I used the Software Updater tool which informed me of the upgrade. I have been operating Ubuntu in a VM starting with Ubuntu 19.04, and this is now the third upgrade: 19.04 > 19.10 > 20.04 > 20.10. So far, all the VM upgrades have gone well. 

My procedure has been to clone the current OS version, then upgrade the clone to the next version. This way, should something go amiss with the upgrade to the new version, the previous version is still intact and working. 

There was only one minor issue this time: One gnome-shell extension (Panel OSD) proved incompatible and will need an upgrade for gnome-shell 3.38 from the maintainer.
I corrected this with the fix found in the user reviews at:
[https://extensions.gnome.org/extension/708/panel-osd/](https://extensions.gnome.org/extension/708/panel-osd/)

Attached: memory usage of Ubuntu 20.10 after startup.

---

### Post by Ars_Ivci on 2020-10-31
I have been using the same setup for the last 5-6 years: mbr with /, swap and /home partitions. 4-5 weeks ago I backed up my files and did a clean install of Xubuntu 20.04, letting iinstaller do its magic for the first time. Interestingly It created a boot/efi partition and an extended partition like this: sda1: boot/efi, sda5: /; system running perfectly. Last week I added Kubuntu 20.10 to the mix, ending with 2 boot/efi partitions (am not sure, though. First one could be a grup partition), two /; both systems perfect. I have a 9 year old laptop which heats easily. Kubuntu almost outperformed Xubuntu so I decided to wipe out everything and install Kubuntu 20.10 only. I chose automatic full disk option again and ended up sda1: unknown, sda2:/bootefi, sda3:/ (no extended partition this time); everying running peachy again. Kubuntu uses sda2. Is it a feature or a bug?
The partition table is as follows:
/dev/sda1    unknown              1.00 Mib
/dev/sda2    fat32   /boot/efi    513 MiB
/dev/sda3    ext4    /

Installer changed partition table from mbr to gpt on its own.

Just to let you know because not many people left using mbr.

---

### Post by RalphPS on 2021-02-02
I ran a clean new install of 20.10 about 60 days ago.  The only issue was a fairly frequent reboot and or Google Chrome lock up and sometimes frozen green screen.  It always occurred when I was watching YouTube videos and rarely when watching videos on other sites. I tried all the suggested fixes but to no avail.  Two weeks age I installed the Chromium browser.  I works with Google as well as Chrome does but it has run flawlessly even after a continuous 4 hour run on connected videos on YouTube.  I'm running an AMD Ryzen 5 3400 with Raedon Vega graphics.

---

### Post by mlocik97 on 2021-04-22
Installed to KVM and had same problems as after installing 20.10. or 20.04 or 19.10 or 19.04 or 18.10 or 18.04 or 16.04 (GNOME) (doesn't matter if in KVM or on baremetal)... Always same little problems.

Login screen is on incorrect display. As main display is default set external monitor instead laptop display. When I set in settings main display, it doesn't set for login screen, what help is simple command:

```

[FONT=SFMono-Regular]sudo cp ~/.config/monitors.xml ~gdm/.config/monitors.xml
sudo chown gdm:gdm ~gdm/.config/monitors.xml[/FONT][COLOR=#ffffff][FONT=SFMono-Regular]
[/FONT][/COLOR]
```[COLOR=#C9D1D9][FONT=SFMono-Regular]

[/FONT][/COLOR]after this it's work as expected.

But well instalation itself was fine.

---

