---
title: "GRUB Error?"
date: 2023-01-25
forum: Server Platforms
---

### Post by themaninblack2 on 2023-01-25
When I try to install ANYTHING on my Ubuntu Server I keep getting this error : How can I fix this without reinstalling the whole server OS.
This ALSO happens when trying to do Upgrade

```
sudo apt-get install zip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zip is already the newest version (3.0-11build1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up grub-common (2.04-1ubuntu26.16) ...
Job for grub-initrd-fallback.service failed because the control process exited with error code.
See "systemctl status grub-initrd-fallback.service" and "journalctl -xe" for details.
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Job for grub-common.service failed because the control process exited with error code.
See "systemctl status grub-common.service" and "journalctl -xe" for details.
invoke-rc.d: initscript grub-common, action "restart" failed.
&#9679; grub-common.service - Record successful boot for GRUB
     Loaded: loaded (/lib/systemd/system/grub-common.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Thu 2023-01-26 01:20:04 UTC; 8ms ago
    Process: 16294 ExecStartPre=/bin/sh -c [ -s /boot/grub/grubenv ] || rm -f /boot/grub/grubenv; mkdir -p /boot/grub (code=exited, status=0/SUCCESS)
    Process: 16296 ExecStart=/usr/bin/grub-editenv /boot/grub/grubenv unset recordfail (code=exited, status=1/FAILURE)
   Main PID: 16296 (code=exited, status=1/FAILURE)

Jan 26 01:20:04  systemd[1]: Starting Record successful boot for GRUB...
Jan 26 01:20:04  grub-editenv[16296]: /usr/bin/grub-editenv: error: invalid environment block.
Jan 26 01:20:04  systemd[1]: grub-common.service: Main process exited, code=exited, status=1/FAILURE
Jan 26 01:20:04  systemd[1]: grub-common.service: Failed with result 'exit-code'.
Jan 26 01:20:04  systemd[1]: Failed to start Record successful boot for GRUB.
dpkg: error processing package grub-common (--configure):
 installed grub-common package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.04-1ubuntu26.16); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.04-1ubuntu26.16); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 2.04-1ubuntu26.16); however:
  Package grub-common is not configured yet.
 grub-pc depends on grub2-common (= 2.04-1ubuntu26.16); however:
  Package grub2-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 2.04-1ubuntu26.16); however:
  Package grub-pc-bin is not configured yet.

dpkg: error processing package grub-pc (--configureNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                             No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                              No apport report written because MaxReports is reached already
                                                                                                                                                            ):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-common
 grub2-common
 grub-pc-bin
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Frogs Hair on 2023-01-26
Moved to server platforms,Ubuntu is already installed.

---

