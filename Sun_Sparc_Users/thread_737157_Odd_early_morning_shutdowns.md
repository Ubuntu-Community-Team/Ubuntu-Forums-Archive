---
title: "Odd early morning shutdowns"
date: 2008-03-27
forum: Sun Sparc Users
---

### Post by linuxwarz on 2008-03-27
I am new to the Sun Sparc devices and have tried to convert one into a router running Ubuntu 7.10.

What's happening is every morning around 12:00am-12:06am the server dies and goes to the openboot "ok" prompt on the serial. When I boot ubuntu back up, /var/log/messages shows something seen below every time.

> 
Mar 27 00:06:26 nzrouter kernel: [  642.663992] eth5: switching to forced 10bt
Mar 27 09:48:39 nzrouter syslogd 1.4.1#21ubuntu3: restart.
Mar 27 09:48:39 nzrouter kernel: Inspecting /boot/System.map-2.6.22-14-sparc64


Is there something the Sun is doing on its own to force ubuntu offline? I cant seem to find logs as to why.

---

### Post by netztier on 2008-03-28
> **linuxwarz said:**
> 
Is there something the Sun is doing on its own to force ubuntu offline? I cant seem to find logs as to why.

I vaguely remember some standby/powerdown options being available - but for the sake of it, I don't know anymore if these were controlled by OBP or by Solaris...

What output do you get from a **printenv** at the OBP prompt? 

regards

Marc

---

### Post by linuxwarz on 2008-03-28
printenv

> 
Variable Name         Value                          Default Value

ras-shutdown-enabled?  false                         false
shutdown-temp         75                             75
warning-temp          70                             70
env-monitor           disabled                       disabled
diag-passes           1                              1
diag-continue?        0                              0
diag-targets          0                              0
diag-verbosity        0                              0
keyboard-click?       false                          false
keymap
scsi-initiator-id     7                              7
#power-cycles         0                              No default
system-board-serial#                                 No default
system-board-date                                    No default
ttyb-rts-dtr-off      false                          false
ttyb-ignore-cd        true                           true
ttya-rts-dtr-off      false                          false
ttya-ignore-cd        true                           true
ttyb-mode             9600,8,n,1,-                   9600,8,n,1,-
ttya-mode             9600,8,n,1,-                   9600,8,n,1,-
pcia-probe-list       8,5,6,7                        8,5,6,7
pcib-probe-list       7,c,3,d,5                      7,c,3,d,5
mfg-mode              off                            off
diag-level            max                            max
fcode-debug?          false                          false
output-device         ttya                           ttya
input-device          ttya                           ttya
load-base             16384                          16384
auto-boot-retry?      false                          false
boot-command          boot                           boot
auto-boot?            true                           true
watchdog-reboot?      false                          false
diag-file
diag-device           net                            net
boot-file
boot-device           disk disk0                     disk net
local-mac-address?    false                          false
net-timeout           0                              0
ansi-terminal?        true                           true
screen-#columns       80                             80
screen-#rows          34                             34
silent-mode?          false                          false
use-nvramrc?          false                          false
nvramrc
security-mode         none                           No default
security-password                                    No default
security-#badlogins   0                              No default
oem-logo                                             No default
oem-logo?             false                          false
oem-banner                                           No default
oem-banner?           false                          false
hardware-revision                                    No default
last-hardware-update                                 No default
diag-switch?          false                          false


---

