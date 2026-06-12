---
title: "Single Application RDP - What Am I doing Wrong"
date: 2010-02-22
forum: Server Platforms
---

### Post by dr_latino999 on 2010-02-22
I am looking at having available to myself on Linux clients VMware Infrastructure Client, which is a Windows only application. I am using this guide here - [http://vmetc.com/2009/10/23/using-vsphere-client-on-ubuntu-linux-with-single-application-rdp/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+vmetc+(VM+/ETC)](http://vmetc.com/2009/10/23/using-vsphere-client-on-ubuntu-linux-with-single-application-rdp/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+vmetc+(VM+/ETC)) - to setup a single Application RDP to the Infrastructure client.

I have a problem where the desktop of the remote computer loads, but the specific program am I trying to launch doesn't. Any ideas would be more than helpful.

Currently the target computer is running Windows 7 Ultimate x64, while the workstation I am using is Ubuntu 10.04 (Alpha) x32 Server w/minimal gui.

Attached is the RDP file I am using to connect to the Windows installation.

```
alternate full switch:i:0
alternate shell:s:c:\Program Files (x86)\VMware\Infrastructure\Virtual Infrastructure Client\Launcher\VpxClient.exe
attach to console:i:0
audiomode:i:2
auto connect:i:0
diskmapping:i:1
bitmapcachepersistenable:i:1
client hostname:s:
compression:i:0
description:s:
desktop size id:i:1
desktopheight:i:0
desktopwidth:i:0
disable full window drag:i:1
disable menu anims:i:1
disable themes:i:1
disable wallpaper:i:1
displayconnectionbar:i:0
domain:s:
enable alternate shell:i:1
enable wm keys:i:0
full address:s:129.171.37.213
hide wm decorations:i:0
keyboard language:s:
keyboardhook:i:0
no motion events:i:0
password:b:4073758256Cell
password 51:b:progman group:s:
protocol:i:0
protocol file:s:
redirectcomports:i:0
redirectdrives:i:0
redirectprinters:i:0
redirectsmartcards:i:0
screen mode id:i:1
session bpp:i:0
shell working directory:s:
username:s:Edwin
winposstr:s:
```

---

