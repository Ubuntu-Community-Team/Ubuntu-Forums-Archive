---
title: "Missing Plymouth splash screen during bootup after kernel upgrade"
date: 2019-07-12
forum: Virtualisation
---

### Post by faubuntu on 2019-07-12
Hi everybody

Been having the following issue: on a Virtualbox Lubuntu installation my Plymouth splash screen shows at boot time, however if I upgrade the kernel, next time I boot the splash screen is no longer invoked and I get this.
[ATTACH=CONFIG]283609[/ATTACH]

I have performed several selective updates to try and isolate the problem: whenever it comes to upgrading the kernel the above happens, so I am assuming that, somewhere between kernel version 4.15.0-20-generic (the one I had at install time) and the latest I'm presented with (4.15.0-54) the issue occurs.

The splash screen is not missing, it is just not invoked at boot time. This is confirmed at shutdown time when the splash screen is shown as expected:

[ATTACH=CONFIG]283608[/ATTACH]

After kernel upgrade, plymouth-debug.log shows some inconsistencies such as this

```
[main.c:998]                                on_show_splash:no displays available to show splash on, waiting...
```

I have attached both plymouth-debug.log files (before and after kernel upgrade) for comparison.



Has anyone come across this issue before?


**System details:**
VirtualBox 5.2.30
Lubuntu 32-bit 18.04 alternate version (lubuntu-18.04-alternate-i386.iso)
working kernel version: 4.15.0-20-generic


Thanks

---

### Post by faubuntu on 2019-07-15
Update: For comparison, I've installed Lubuntu 32-bit 18.10. After installing all the updates there does not seem to be the same issue with version 18.04.

---

### Post by Claus7 on 2019-07-15
Hello,

I had an issue with plymouth having 18.04. I reinstalled lightdm. If I recall correctly I reinstalled plymouth from synaptic as well. Changing plymouth theme and back again did not solve the issue. I have not experienced such an issue after that. I should mention though that during the reinstallations there were kernel upgrades that were taking place almost the same time. During shut down there was no issue.

Regards!

---

### Post by faubuntu on 2019-07-17
> **Claus7 said:**
> Hello,

I had an issue with plymouth having 18.04. I reinstalled lightdm. If I recall correctly I reinstalled plymouth from synaptic as well. Changing plymouth theme and back again did not solve the issue. I have not experienced such an issue after that. I should mention though that during the reinstallations there were kernel upgrades that were taking place almost the same time. During shut down there was no issue.

Regards!

Hi Claus7, thanks - I've just tried this: either reinstalling lightdm and plymouth as standalone or reinstalling with all their components did not solve the issue.

I want to check: when you say 'During shut down there was no issue.' do you mean that you could see Plymouth splash screen during shutdown but you could not see it during boot time?

---

### Post by Claus7 on 2019-07-17
Hello,

> **faubuntu said:**
> ...
I want to check: when you say 'During shut down there was no issue.' do you mean that you could see Plymouth splash screen during shutdown but you could not see it during boot time?

exactly! Why do you have such a low version kernel for 18.04?

Regards!

---

### Post by faubuntu on 2019-07-17
> **Claus7 said:**
> Hello,



exactly! Why do you have such a low version kernel for 18.04?

Regards!

About the plymouth issue: in your first post you mentioned that after reinstalling plymouth and lightdm you have not experienced such an issue after that.

Yet it seems that you still experienced the issue of not seeing the splash screen at boot time (which is the issue on this thread), am I understanding correctly?



About the kernel version: which version should I see?


Thank you

---

### Post by Claus7 on 2019-07-18
Hello,

the story goes lies this: suddenly I was not able to see plymouth during boot. All the times though I was able to see plymouth during shutdown as you pinpointed correctly. Re-installing plymouth or changing plymouth theme did not change anything. Then, I reinstalled lightdm and things were fixed. The thing is that almost simultaneously ubuntu 18.04 was experiencing updates in its kernel and new version was installed.

In order to check which kernel version you have you can open a terminal and with the command:
uname -a

to check yours. The kernel versions of ubuntu 18.04 are 5.x, so I do not understand why you still have 4.x ones.

Regards!

---

### Post by faubuntu on 2019-07-18
> **Claus7 said:**
> Then, I reinstalled lightdm and things were fixed. The thing is that almost simultaneously ubuntu 18.04 was experiencing updates in its kernel and new version was installed.

In order to check which kernel version you have you can open a terminal and with the command:
uname -a

to check yours. The kernel versions of ubuntu 18.04 are 5.x, so I do not understand why you still have 4.x ones.

Regards!

Ok, thanks for clarifying - about the kernel: the version I currently have is *Linux ubuntu 4.15.0-54-generic. *I don't know why I'm not being offered a newer version. Perhaps it's got something to do with the fact I have chosen Lubuntu over Ubuntu?

---

### Post by faubuntu on 2019-07-18
Update: I have installed images from *lubuntu-18.04-desktop-i386.iso* and *lubuntu-18.04.2-desktop-i386.iso*, with various install options (i.e. minimal/full, download/don't download drivers, etc.) but in all cases I got the missing graphical splash screen right from the start, i.e. with a clean install.


```
$ uname -a
Linux drupalpro-VirtualBox 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:15:38 UTC 2018 i686 i686 i686 GNU/Linux


```

Kernel version appears to be the same as the initial version of the alternate image, where I do not experience the issue.

---

### Post by faubuntu on 2019-07-18
Reattaching both Plymouth logs

**plymouth-debug.log** (after software updates, broken)
[https://paste.ubuntu.com/p/NWdvj7tyvz/](https://paste.ubuntu.com/p/NWdvj7tyvz/)


**plymouth-debug.log** (before software updates, working)
[https://paste.ubuntu.com/p/F5PzthvF2s/](https://paste.ubuntu.com/p/F5PzthvF2s/)

---

### Post by Claus7 on 2019-07-18
Hello,

there are two different things that I was able to notice: i) you are using virtualbox ii) your version is a 32bit one. I do not know if these somehow affect the final behavior. 

You might want to change from lightdm to gdm3 and back again in case this fixes your issue.

Regards!

---

### Post by faubuntu on 2019-07-18
Uncommented the following line in GRUB to see if forcing a resolution would make a difference.

```
GRUB_GFXMODE=640x480
```

to no avail.


By the way, there's no differences in GRUB between the working version and the non-working one.

---

### Post by faubuntu on 2019-07-18
> **Claus7 said:**
> Hello,

there are two different things that I was able to notice: i) you are using virtualbox ii) your version is a 32bit one. I do not know if these somehow affect the final behavior. 

You might want to change from lightdm to gdm3 and back again in case this fixes your issue.

Regards!

Thanks Claus7,

I have just tried installing and switching to gdm3, unfortunately it did not make a difference, and neither does switching back.

Since I'm trying different installs to try and pinpoint where the issue originates from, I'll probably try the 64 bit version as well. I still need to use VirtualBox though.

---

### Post by CatKiller on 2019-07-18
> **Claus7 said:**
> The kernel versions of ubuntu 18.04 are 5.x, so I do not understand why you still have 4.x ones.
The kernel version for 18.04 and 18.04.1 is 4.15. The kernel version for 18.04.2 and 18.04 with the Hardware Enablement Stack is 4.18. 5.0 will come with the next Hardware Enablement Stack update with 18.04.3.

---

### Post by faubuntu on 2019-07-18
> **CatKiller said:**
> The kernel version for 18.04 and 18.04.1 is 4.15. The kernel version for 18.04.2 and 18.04 with the Hardware Enablement Stack is 4.18. 5.0 will come with the next Hardware Enablement Stack update with 18.04.3.

Thanks CatKiller,

this would actually be consistent with what I had read on *It's Foss* in this article [https://itsfoss.com/linux-kernel-5/](https://itsfoss.com/linux-kernel-5/)

> Some rolling release distributions like Arch Linux will start to provide Kernel 5.0 in a few days (or hours perhaps). [Check your Linux kernel version]("https://itsfoss.com/find-which-kernel-version-is-running-in-ubuntu/") and see if it’s already updated to the new kernel with the last system update.


But most other distributions like Ubuntu, Linux Mint, Fedora, Debian etc won’t provide this release anytime soon (or ever).



---

### Post by faubuntu on 2019-07-18
> **faubuntu said:**
> Update: I have installed images from *lubuntu-18.04-desktop-i386.iso* and *lubuntu-18.04.2-desktop-i386.iso*, with various install options (i.e. minimal/full, download/don't download drivers, etc.) but in all cases I got the missing graphical splash screen right from the start, i.e. with a clean install.


```
$ uname -a
Linux drupalpro-VirtualBox 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:15:38 UTC 2018 i686 i686 i686 GNU/Linux


```

Kernel version appears to be the same as the initial version of the alternate image, where I do not experience the issue.

This seemed inconsistent with my initial assumptions that the kernel version might be responsible for the issue. Also, this would have left the 'Alternate' image as the only one not presenting the issue right after a clean install.

I decided to perform another clean install of the 'Alternate' image again. Interestingly enough, the issue was present from the start this time, which I found confusing.

I then realized that I had upgraded Virtualbox version, from VirtualBox-5.2.28-130011-Win to VirtualBox-5.2.30-130521-Win.

So, by downgrading Virtualbox back to version 5.2.28 the issue is no longer there.


This is still somewhat confusing: if I leave the image as a clean install Plymouth will behave as expected during boot-up. But if I perform any software update that involves a kernel upgrade Plymouth will not show the splash screen anymore.

---

### Post by faubuntu on 2019-07-18
Also, I tried a 64-bit install which did not work from the start (graphical issues). Given I did this for troubleshooting purposes, I am going to assume that all the other 64-bit versions present this problem and will no longer pursue this branch.

---

### Post by CatKiller on 2019-07-18
I mean, you can clearly see the difference:

```

[main.c:926]           plymouth_should_show_default_splash:checking if plymouth should show default splash
[main.c:954]           plymouth_should_show_default_splash:using default splash because kernel command line has option "splash"
[ply-device-manager.c:766]                 create_devices_from_terminals:checking for consoles
[ply-device-manager.c:544]                        add_consoles_from_file:opening /sys/class/tty/console/active
[ply-device-manager.c:552]                        add_consoles_from_file:reading file
[ply-device-manager.c:590]                        add_consoles_from_file:console /dev/tty1 found!
[ply-device-manager.c:378]                         watch_for_udev_events:watching for udev graphics device add and remove events
[ply-device-manager.c:282]                  create_devices_for_subsystem:creating objects for drm devices
[ply-device-manager.c:299]                  create_devices_for_subsystem:found device /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[ply-device-manager.c:306]                  create_devices_for_subsystem:device is initialized
[ply-device-manager.c:315]                  create_devices_for_subsystem:found node /dev/dri/card0
[ply-device-manager.c:229]                create_devices_for_udev_device:device subsystem is drm
[ply-device-manager.c:232]                create_devices_for_udev_device:found DRM device /dev/dri/card0
[ply-device-manager.c:679] create_devices_for_terminal_and_renderer_type:creating devices for /dev/dri/card0 (renderer type: 1) (terminal: /dev/tty1)
[ply-renderer.c:236]                      ply_renderer_open_plugin:trying to open renderer plugin /usr/lib/i386-linux-gnu/plymouth/renderers/drm.so
[./plugin.c:609]                                create_backend:creating renderer backend for device /dev/dri/card0
[./plugin.c:701]                                   load_driver:Opening '/dev/dri/card0'
[ply-terminal.c:603]                             ply_terminal_open:trying to open terminal '/dev/tty1'
[ply-terminal.c:396]                 ply_terminal_refresh_geometry:looking up terminal text geometry
[ply-terminal.c:410]                 ply_terminal_refresh_geometry:terminal is now 100x37 text cells
[ply-terminal.c:447]                                 get_active_vt:Remembering that initial vt is 1
```

vs

```

[main.c:926]           plymouth_should_show_default_splash:checking if plymouth should show default splash
[main.c:954]           plymouth_should_show_default_splash:using default splash because kernel command line has option "splash"
[ply-device-manager.c:814]                 create_devices_from_terminals:checking for consoles
[ply-device-manager.c:592]                        add_consoles_from_file:opening /sys/class/tty/console/active
[ply-device-manager.c:600]                        add_consoles_from_file:reading file
[ply-device-manager.c:638]                        add_consoles_from_file:console /dev/tty1 found!
[ply-device-manager.c:414]                         watch_for_udev_events:watching for udev graphics device add and remove events
[ply-device-manager.c:315]                  create_devices_for_subsystem:creating objects for drm devices
[main.c:2400]                                          main:entering event loop
[ply-boot-server.c:388]             print_connection_process_identity:connection is from pid 248 (plymouth --ping) with parent pid 235 (/bin/sh /etc/init.d/apparmor start)
[ply-event-loop.c:1060]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x452b90 for fd 10
[ply-event-loop.c:1064]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x452b90 for fd 10
[ply-event-loop.c:1144]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x452d00, 0x452b90) of fd 10
[ply-event-loop.c:643]             ply_event_loop_remove_source_node:failed to delete fd 10 from epoll watch list: Bad file descriptor
[ply-boot-server.c:388]             print_connection_process_identity:connection is from pid 252 (/bin/plymouth show-splash) with parent pid 1 (/sbin/init splash plymouth:debug)
[ply-boot-server.c:484]                ply_boot_connection_on_request:got show splash request
[main.c:896]      plymouth_should_ignore_show_splash_calls:checking if plymouth should be running
[main.c:998]                                on_show_splash:no displays available to show splash on, waiting...
[ply-event-loop.c:1060]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x452b90 for fd 10
[ply-event-loop.c:1064]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x452b90 for fd 10
[ply-event-loop.c:1144]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x452d00, 0x452b90) of fd 10
[ply-event-loop.c:643]             ply_event_loop_remove_source_node:failed to delete fd 10 from epoll watch list: Bad file descriptor
```

It's just not able to set up the card to draw the splash screen in.

Since one rarely needs to reboot, and it's a VM anyway, I personally wouldn't spend any time on it at all. Maybe it's a Grub configuration glitch, maybe it's an apparmor configuration glitch, maybe it's just changing how it interprets the pretend graphics card for the VM; it's just not that important, I'd say.

---

### Post by faubuntu on 2019-07-19
> **CatKiller said:**
> It's just not able to set up the card to draw the splash screen in.

Since one rarely needs to reboot, and it's a VM anyway, I personally wouldn't spend any time on it at all. Maybe it's a Grub configuration glitch, maybe it's an apparmor configuration glitch, maybe it's just changing how it interprets the pretend graphics card for the VM; it's just not that important, I'd say.

I appreciate that. It's just that I find this specific glitch puzzling and enjoyable to troubleshoot at the same time, although you are right that it's probably just cosmetic, and happens only during boot time.


I'm going to put it on the backburner for now, coming back to it occasionally. Thanks for the contribution.

---

### Post by Claus7 on 2019-07-20
Hello,

> **CatKiller said:**
> The kernel version for 18.04 and 18.04.1 is 4.15. The kernel version for 18.04.2 and 18.04 with the Hardware Enablement Stack is 4.18. 5.0 will come with the next Hardware Enablement Stack update with 18.04.3.

> **faubuntu said:**
> Thanks CatKiller,

this would actually be consistent with what I had read on *It's Foss* in this article [https://itsfoss.com/linux-kernel-5/](https://itsfoss.com/linux-kernel-5/)

mea culpa! You are both correct. Working with 19.04 as well and facing for a brief amount of time the same issue with that version as well caused the confusion.

There can be some issues about virtualbox and booting procedures, in cases when some latest update shows up. A newest version of virtualbox might fix it soon.

Regards!

---

### Post by faubuntu on 2019-07-20
> **Claus7 said:**
> Hello,





mea culpa! You are both correct. Working with 19.04 as well and facing for a brief amount of time the same issue with that version as well caused the confusion.

There can be some issues about virtualbox and booting procedures, in cases when some latest update shows up. A newest version of virtualbox might fix it soon.

Regards!

Hi Claus7, no worries.


Yes, as part of the troubleshooting process I will - at some point - try different Virtualbox versions to further attempt to isolate the problem.


After all, if the culprit is found, a proper bug report can be logged.


Thank you

---

### Post by faubuntu on 2019-08-09
Tried a selective kernel upgrade, from 4.15.0-20-generic to 4.15.0-21-generic.

Plymouth splash screen still shows up as it should after this upgrade.

---

