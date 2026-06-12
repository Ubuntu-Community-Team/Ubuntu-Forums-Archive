---
title: "System won't shutdown after upgrade to 13.04"
date: 2013-03-18
forum: Ubuntu Development Version
---

### Post by Kotrfa on 2013-03-18
Hi,

yesterday I upgraded to 13.04. Everything went fine and the system is OK. But when I try to turn off (using "sudo shutdown now" in tty, terminal or using GUI through gnome) the computer, it hangs at: "The system is going shutdown for maintenance NOW!" and nothing happen. It doesn't react to anything (like changing tty, writing commands). I need to use "hard" shutdown using hardware power button.
Any ideas? Thanks a lot

---

### Post by dino99 on 2013-03-18
the logs might be usefull to find errors and/or warnings.
look at .xsession-errors inside /home and also logs inside /var/log/ & /var/crash/

---

### Post by Kotrfa on 2013-03-18
It occurs very randomly. :confused: I haven't changed anything, I haven't made any updates and it worked for last three reboots/shutdowns works OK. Here are my logs from last time when it occurs. I haven't found anything strange there. The only interesting might be /var/log/Xorg.1.log.

```

[  6558.284] (II) AIGLX: Suspending AIGLX clients for VT switch
[  6560.694] (II) Open ACPI successful (/var/run/acpid.socket)
[  6560.694] (II) AIGLX: Resuming AIGLX clients after VT switch
[  6560.694] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[  6560.800] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  6561.114] (II) XKB: reuse xkmfile /var/lib/xkb/server-A83C9FD1E122A6B4C0EA72280460AC0F580A6A41.xkm
[  6566.209] (II) UnloadModule: "synaptics"
[  6566.209] (II) evdev: AT Translated Set 2 keyboard: Close
[  6566.209] (II) UnloadModule: "evdev"
[  6566.209] (II) evdev: WebCam SC-13HDL11431N: Close
[  6566.209] (II) UnloadModule: "evdev"
[  6566.210] (II) evdev: A4Tech USB Mouse: Close
[  6566.210] (II) UnloadModule: "evdev"
[  6566.210] (II) evdev: Power Button: Close
[  6566.210] (II) UnloadModule: "evdev"
[  6566.210] (II) evdev: Video Bus: Close
[  6566.210] (II) UnloadModule: "evdev"
[  6566.210] (II) evdev: Power Button: Close
[  6566.210] (II) UnloadModule: "evdev"
[  6566.246] Server terminated successfully (0). Closing log file.



```

---

### Post by Shea83 on 2013-03-24
I' ve the same issue... i've an Nvidea (as a video card) and i tried with and without open driver but the problem always remains.

---

### Post by dino99 on 2013-03-24
Got that issue yoo, and the work around is to run these commands into a terminal, one by one:

> compiz --replace cpp &
> unity --replace

if its not enough, then install & use unity-tweak-tool to reset the settings

---

### Post by Shea83 on 2013-03-31
> **dino99 said:**
> Got that issue yoo, and the work around is to run these commands into a terminal, one by one:




if its not enough, then install & use unity-tweak-tool to reset the settings


I have not solved with this solution (i use gnome and not unity as a desktop manager)...

But i have found a workarond with the open source video driver (nouveau)... if i shutdown the pc manually by terminal ("sudo shutdown -h now") it turn off normally.

---

### Post by Kotrfa on 2013-04-03
Yeah, thats the workaround for me also. 
```
sudo shutdown -h now
```

---

### Post by iluvatar0 on 2013-04-05
I got the shutdown problem, too. However shutdown -h now does not solve this - and neither do the two commands suggested above. As I am running kubuntu they aren't even installed. Upgrading to a mainline kernel (I tried v.3.9-rc5) does let me shut down my box but as my sound card did not work using that kernel it's no option on my htpc.

---

### Post by Kotrfa on 2013-04-06
They aren't installed? I've never used Kubuntu but I'm pretty sure that shutdown command isn't locked to DE.
Try type /sbin/shutdown or:
```
dpkg -S /sbin/shutdown
``` 

If it doesn't exist, install upstart package (but I'm very sceptic about that...)

Info about upstart:

```
 ~ $ sudo apt-cache show upstart

Package: upstart
Priority: required
Section: admin
Installed-Size: 1364
Maintainer: James Hunt <james.hunt@ubuntu.com>
Architecture: amd64
Version: 1.8-0ubuntu1
Replaces: startup-tasks, system-services, sysvinit, upstart-compat-sysv, upstart-job
Provides: startup-tasks, system-services, upstart-compat-sysv, upstart-job
Depends: libc6 (>= 2.15), libdbus-1-3 (>= 1.2.16), libjson0 (>= 0.10-1.1ubuntu1), libnih-dbus1 (>= 1.0.0), libnih1 (>= 1.0.0), libudev1 (>= 183), sysvinit-utils, sysv-rc, initscripts, mountall, ifupdown (>= 0.6.10ubuntu5), debianutils (>= 4)
Suggests: python3, graphviz, bash-completion, upstart-monitor
Conflicts: lxcguest, startup-tasks, system-services, sysvinit, upstart-compat-sysv, upstart-job
Breaks: friendly-recovery (<< 0.2.13), libc6 (<< 2.12.1-0ubuntu12)
Filename: pool/main/u/upstart/upstart_1.8-0ubuntu1_amd64.deb
Size: 508422
MD5sum: 70b4c854d197e42dfdaa1d7e637debcb
SHA1: aca5e36777fc8705bd0b79a333bab6324679cd12
SHA256: 74952d602262dc1875efb534cf1efd98398d31640496d4ee3d7c59f87a726fbb
Description-en: event-based init daemon
 upstart is a replacement for the /sbin/init daemon which handles
 starting of tasks and services during boot, stopping them during
 shutdown and supervising them while the system is running.
Multi-Arch: foreign
Homepage: http://upstart.ubuntu.com/
Description-md5: b776ec43b708c13dd0c2ab824471f478
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m
Task: minimal

```

Or you can try kshutdown:

```

Package: kshutdown
Priority: optional
Section: universe/x11
Installed-Size: 793
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Eike Sauer <eike@debian.org>
Architecture: amd64
Version: 3.0~beta5-2
Depends: kde-runtime, libc6 (>= 2.14), libkdecore5 (>= 4:4.4.0), libkdeui5 (>= 4:4.3.4), libkio5 (>= 4:4.3.4), libknotifyconfig4 (>= 4:4.3.4), libkworkspace4abi2 (>= 4:4.8.1), libqt4-dbus (>= 4:4.5.3), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>= 4:4.5.3), libstdc++6 (>= 4.1.1)
Filename: pool/universe/k/kshutdown/kshutdown_3.0~beta5-2_amd64.deb
Size: 145010
MD5sum: 999db49c628b96877c940b08f2968926
SHA1: cb27814a8e950e242f081d1b86b54dc0c73e5c35
SHA256: b05aafcb6d15f6b350d0d1acc951b8be998e72db9e3d73bbe2722ab8cb6e738f
Description-en: advanced shut down utility for KDE
 It has 4 main commands:
 .
  - Shut Down (logout and halt the system),
  - Reboot (logout and reboot the system),
  - Lock Screen (lock the screen using a screen saver),
  - Logout (end the session and logout the user).
 .
 It features time and delay options, command line support, wizard,
 and sounds.
Homepage: http://kshutdown.sourceforge.net/
Description-md5: fc7b6d7fd762ccfdcdbea5b09e94c55b
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu



```

---

### Post by iluvatar0 on 2013-04-06
Kotrfa, you misunderstood me. shutdown surely is installed. But typing shutdown -h now in the shell freezes the box, as does reboot.. Compiz and unity are the two packages that don't come with kubuntu by default. So quite naturally the two commands "[COLOR=#000000]*compiz --replace cpp &" or "*[/COLOR][COLOR=#000000]*unity --replace" don't work here. Using the mainline kernel 3.9 kinda solved the shutdown issue but left me without sound - so it's a nogo. Interestingly Mainline 3.8.6 (which does give me sound) won't shutdown either. So my issues somehow seem to be related to kernel 3.8. Strangely enough I don't see that many complaints as my z68-mainboard isn't that unusual.*[/COLOR]

---

### Post by Kotrfa on 2013-04-07
Sorry - my bad.

By the way - I didn't experience this problem about 4 days.

---

