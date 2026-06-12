---
title: "how to use /etc/pulse/client.conf"
date: 2013-01-22
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-01-22
how do i use this file and have it work, i have the file set properly but the effects are not working, i even put a symlink to it in /etc/skel/.pulse
```
guest-jTtRFm@M4A79XTD-EVO:~$ cat .pulse/client.conf 
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for PulseAudio clients. See pulse-client.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

default-sink = alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1
default-source = alsa_input.pci-0000_00_14.2.analog-stereo
; default-server =
; default-dbus-server =

; autospawn = yes
; daemon-binary = /usr/bin/pulseaudio
; extra-arguments = --log-target=syslog

; cookie-file =

; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; auto-connect-localhost = no
; auto-connect-display = no

```

---

### Post by Yellow Pasque on 2013-01-24
If I had to venture a guess, I would delete the user's pulseaudio configuration files and force them to be regenerated.
```
rm -r ~/.pulse*
```
Then, log out/in to restart pulseaudio and see if your changes took effect. Note that /etc/pulse/default.pa loads module-default-device-restore, which might be interfering too.

---

### Post by zika on 2013-01-24
> **Temüjin said:**
> If I had to venture a guess, I would delete the user's pulseaudio configuration files and force them to be regenerated.
```
rm -r ~/.pulse*
```
Then, **log out/in to restart pulseaudio** and see if your changes took effect. Note that /etc/pulse/default.pa loads module-default-device-restore, which might be interfering too.```
pulseaudio --kill
```is more that enough to restart pulseaudio...

---

### Post by pqwoerituytrueiwoq on 2013-01-24
it is a guest account, it ignores the settings on login
a guest account is deleted on logout

---

