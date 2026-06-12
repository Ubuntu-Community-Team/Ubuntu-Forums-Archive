---
title: "Vivid shutdown failure"
date: 2015-02-01
forum: Ubuntu Development Version
---

### Post by crcarson on 2015-02-01
Was running Vivid for several week successfully but an update in the last 3 days has caused shutdown/restart to fail.  To be certain it, rebuild the system from the 1/31/15 daily image and it still fails.  See this message in syslog:

Feb  1 10:30:18 Desktopps kernel: [  159.926835] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card2/input24
Feb  1 10:30:21 Desktopps kernel: [  162.489914] init: wait-for-state (whoopsienetwork-manager) main process (3251) terminated with status 100
Feb  1 10:30:21 Desktopps kernel: [  162.524157] init: whoopsie main process (6153) terminated with status 1
Feb  1 10:30:21 Desktopps kernel: [  162.524162] init: whoopsie main process ended, respawning
Feb  1 10:30:44 Desktopps gnome-session[2064]: WARNING: Shutdown failed: GDBus.Error:org.freedesktop.DBus.Error.InteractiveAuthorizationRequired: Interactive authentication required.
Feb  1 10:30:51 Desktopps kernel: [  192.560036] init: wait-for-state (whoopsienetwork-manager) main process (6157) terminated with status 100
Feb  1 10:30:51 Desktopps kernel: [  192.594018] init: whoopsie main process (6176) terminated with status 1
Feb  1 10:30:51 Desktopps kernel: [  192.594026] init: whoopsie main process ended, respawning
Feb  1 10:30:01 Desktopps dbus[732]: message repeated 5 times: [ [system] Reloaded configuration]
Feb  1 10:30:58 Desktopps dbus[732]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Feb  1 10:30:58 Desktopps dbus[732]: [system] Successfully activated service 'org.freedesktop.hostname1'

---

### Post by zika on 2015-02-01
> **crcarson said:**
> Was running Vivid for several week successfully but an update in the last 3 days has caused shutdown/restart to fail.  To be certain it, rebuild the system from the 1/31/15 daily image and it still fails.  See this message in syslog:

Feb  1 10:30:18 Desktopps kernel: [  159.926835] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card2/input24
Feb  1 10:30:21 Desktopps kernel: [  162.489914] init: wait-for-state (whoopsienetwork-manager) main process (3251) terminated with status 100
Feb  1 10:30:21 Desktopps kernel: [  162.524157] init: whoopsie main process (6153) terminated with status 1
Feb  1 10:30:21 Desktopps kernel: [  162.524162] init: whoopsie main process ended, respawning
Feb  1 10:30:44 Desktopps gnome-session[2064]: [SIZE=4][COLOR=#0000ff]WARNING: Shutdown failed: GDBus.Error:org.freedesktop.DBus.Error.InteractiveAuthorizationRequired: Interactive authentication required.[/COLOR][/SIZE]
Feb  1 10:30:51 Desktopps kernel: [  192.560036] init: wait-for-state (whoopsienetwork-manager) main process (6157) terminated with status 100
Feb  1 10:30:51 Desktopps kernel: [  192.594018] init: whoopsie main process (6176) terminated with status 1
Feb  1 10:30:51 Desktopps kernel: [  192.594026] init: whoopsie main process ended, respawning
Feb  1 10:30:01 Desktopps dbus[732]: message repeated 5 times: [ [system] Reloaded configuration]
Feb  1 10:30:58 Desktopps dbus[732]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Feb  1 10:30:58 Desktopps dbus[732]: [system] Successfully activated service 'org.freedesktop.hostname1'Does```
sudo shutdown now
```work in CLI?

---

### Post by crcarson on 2015-02-01
Tried "sudo shutdown now" and still didn't complete the shutdown although it appears I got farther in the shutdown process.  Using normal shutdown (via the system ICON) even the destop didn't go away.  Had a functing system.  Using the comand line shutdown ended up hanging on a black screen with couple of process terminated messages (nothing to indicate what was the problem).  Had to hard power off to restart the system.

---

### Post by zika on 2015-02-01
Try now```
sudo shutdown -P now
```...

---

### Post by crcarson on 2015-02-02
> **zika said:**
> Try now```
sudo shutdown -P now
```...

Yes, adding the -P (power down) does power off the system (quite a rapid shutdown).

---

### Post by crcarson on 2015-02-02
Was reading the post on 15.04 USB Permissions on new Install and tried out booting with init=/lib/systemd/systemd.  Both this problem and the "No Audio after Vivid Update" are resolved.  I am able to shutdown with the normal ICON and both expected Audio devices are back.

---

### Post by crcarson on 2015-02-02
Thought the 15.04 system was back but unable to stop/start mysql due to an upstart problem with sockets (could be a permission problem).  Also recently be seeing some upstart.udev.nnn.pid files (could be file per boot of the system) in my home directory.

---

### Post by zika on 2015-02-02
> **crcarson said:**
> Thought the 15.04 system was back but unable to stop/start mysql due to an upstart problem with sockets (could be a permission problem).  Also recently be seeing some upstart.udev.nnn.pid files (could be file per boot of the system) in my home directory.Those file could/should be moved to be written in /tmp... ;)

---

### Post by zika on 2015-02-02
> **crcarson said:**
> Was reading the post on 15.04 USB Permissions on new Install and tried out booting with init=/lib/systemd/systemd.  Both this problem and the "No Audio after Vivid Update" are resolved.  I am able to shutdown with the normal ICON and both expected Audio devices are back.Nice to read that. As You're on Vivid You could choose SystemD option in Grub or cross to the dark side and make SystemD default and UpStart as option... I'm yet undecide as which one is better, SystemD as default or as an option. UpStart is not an option for me anymore... ;) The difference is not just in UReadAhead... ;)

---

### Post by crcarson on 2015-02-02
> **zika said:**
> Nice to read that. As You're on Vivid You could choose SystemD option in Grub or cross to the dark side and make SystemD default and UpStart as option... I'm yet undecide as which one is better, SystemD as default or as an option. UpStart is not an option for me anymore... ;) The difference is not just in UReadAhead... ;)

OK, up and running on 15.04 with systemd (install systemd-sysv).  Reboot got around the need to stop/start mysql.

---

### Post by NunoLava1998 on 2015-02-08
Can you use the Alt+SysRq thing to shutdown your system?

---

### Post by sgage on 2015-02-09
> **zika said:**
> Nice to read that. As You're on Vivid You could choose SystemD option in Grub or cross to the dark side and make SystemD default and UpStart as option... I'm yet undecide as which one is better, SystemD as default or as an option. UpStart is not an option for me anymore... ;) The difference is not just in UReadAhead... ;)

How does one configure these two options?

---

### Post by zika on 2015-02-09
> **sgage said:**
> How does one configure these two options?
[http://ubuntuforums.org/showthread.php?t=2259716](http://ubuntuforums.org/showthread.php?t=2259716)
[http://ubuntuforums.org/showthread.php?t=2249915](http://ubuntuforums.org/showthread.php?t=2249915)

---

### Post by sgage on 2015-02-09
> **zika said:**
> [http://ubuntuforums.org/showthread.php?t=2259716](http://ubuntuforums.org/showthread.php?t=2259716)
[http://ubuntuforums.org/showthread.php?t=2249915](http://ubuntuforums.org/showthread.php?t=2249915)

Thanks, zika.

Systemd working fine here...

---

