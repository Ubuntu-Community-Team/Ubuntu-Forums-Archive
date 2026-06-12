---
title: "Boot Ubuntu with monitor or headless"
date: 2019-11-09
forum: Server Platforms
---

### Post by veikley on 2019-11-09
I have a headless setup using xerver-xorg-video-dummy and an xorg.conf file.  But is there a way to make ubuntu recognize a monitor if needed so you can boot to the monitor or headless?

---

### Post by darkod on 2019-11-10
I don't understand the question. Even a CLI only server installation (without any X server packages) will show you image on monitor when connected. It will be CLI only (no GUI) but it does show on monitor.

Have you tried plugging in a monitor to the server?

The OS shouldn't care whether you have monitor plugged in or not.

---

### Post by veikley on 2019-11-13
Once I set up the headless setup you cannot plug a monitor in and get a response.  Its 100% headless.

---

### Post by veikley on 2019-11-13
This is a remote unit for network packet capture.  Ubuntu would not boot unless a monitor was connected so I went the headless route.  But now it would be nice to hook up a monitor occasionally for local access.

---

### Post by LHammonds on 2019-11-14
> **veikley said:**
> Once I set up the headless setup you cannot plug a monitor in and get a response.  Its 100% headless.

> **veikley said:**
> Ubuntu would not boot unless a monitor was connected

Maybe you should clarify exactly what you mean by "ubuntu" because that is NOT how Ubuntu server works.

I have not installed Ubuntu Desktop (ubuntu-18.04.3-desktop-amd64.iso) but one time on a laptop so I don't know if it would have issue booting if the monitor lid was ripped off but since the purpose of a "Desktop" image is a Graphical User Interface, I would assume it requires a GUI-capable output device.

As for Ubuntu Server (ubuntu-18.04.3-server-amd64.iso), I have installed it many times on devices that only temporarily have input/output devices plugged in such as keyboard, video, mouse...usually only during setup and then it sits in a corner never to be touched again by anything but a power cord and network cable.  However, I only install openssh and use PuTTY or WinSCP to connect to it and manage it.  I do not try to install any type of GUI system on it.

LHammonds

---

### Post by Doug S on 2019-11-14
> **LHammonds said:**
> As for Ubuntu Server (ubuntu-18.04.3-server-amd64.iso), I have installed it many times on devices that only temporarily have input/output devices plugged in such as keyboard, video, mouse...usually only during setup and then it sits in a corner never to be touched again by anything but a power cord and network cable.  However, I only install openssh and use PuTTY or WinSCP to connect to it and manage it.  I do not try to install any type of GUI system on it.Exactly the same here.

---

### Post by veikley on 2019-11-14
Ubuntu Desktop 18.04 LTS is what is installed.

---

