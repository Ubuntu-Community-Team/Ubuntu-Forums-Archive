---
title: "Can't get Hyper-V with Enhanced Session Mode working"
date: 2018-11-28
forum: Server Platforms
---

### Post by qai on 2018-11-28
- Ubuntu Server 18.10 + Xubuntu-Core
- Windows 10 Pro
- VM Tools for Ubuntu 18.04 ([https://github.com/Microsoft/linux-vm-tools](https://github.com/Microsoft/linux-vm-tools))

Followed the instructions as indicated [here]("https://blogs.technet.microsoft.com/virtualization/2018/02/28/sneak-peek-taking-a-spin-with-enhanced-linux-vms/"). Cannot graphically connect to VM remotely (XRDP). The server itself works perfectly fine.

Anyone been able to use XRDP to an Ubuntu server running in Hyper-V's Enhanced Session mode? If so, what would need to be done differently than the above to get things working?

Using a standard Ubuntu install and converting that to a server is way too bloated and troublesome. Xubuntu Core is within acceptable tolerance threshold for adding a GUI to a server.

---

### Post by TheFu on 2018-11-29
Uh ... ubuntu server doesn't have any GUI.  To manage servers, we use ssh.

Also, I wouldn't expect tools compiled for 18.04 to work under 18.10.  Certainly libc has changed and definitely all the other libraries have too.

---

### Post by qai on 2018-11-29
> **TheFu said:**
> Uh ... ubuntu server doesn't have any GUI.  To manage servers, we use ssh.

As I wrote in the OP: - Ubuntu Server 18.10 + Xubuntu-Core

Xubuntu core installs the bare minimum GUI of a Xubuntu install. Basically just Xfce without any apps. Integrates perfectly well with Ubuntu Server (sudo apt install xubuntu-core).

> **TheFu said:**
> Also, I wouldn't expect tools compiled for 18.04 to work under 18.10.   Certainly libc has changed and definitely all the other libraries have  too.

The VM tools is just a single script that calls apt install and some minor configs.

---

### Post by TheFu on 2018-11-29
I must be losing it.  Didn't see the "X".  Clearly I need a rest.  Sorry for wasting your time.

---

