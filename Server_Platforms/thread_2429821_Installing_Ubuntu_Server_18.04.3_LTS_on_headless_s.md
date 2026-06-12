---
title: "Installing Ubuntu Server 18.04.3 LTS on headless server"
date: 2019-10-23
forum: Server Platforms
---

### Post by weedware on 2019-10-23
Greetings All,

I have recently taken possession of some new headless, embedded server processors. It was my intention to install Ubuntu Server 18.04.3 LTS on these boards following the  steps outlined in a Github post located at [https://github.com/ynkjm/ubuntu-serial-install](https://github.com/ynkjm/ubuntu-serial-install). The post was targeted for 16.04, but I had my hopes up. Apparently the process for installing Ubuntu 18.04 differs from the earlier versions? Specifically, the procedure was unable to find menu.c32. All that said, and at the risk of repeating any previous posts/questions, is there a well-groomed, tested procedure for installing Ubuntu 18.04.3 Server LTS on system without graphics capability--with only redirected serial console access? As a side note, the embedded server is running a [COLOR=#000000][FONT=Arial]Intel C3958, 16-core processor.

Please advise[/FONT][/COLOR]

---

### Post by darkod on 2019-10-24
Which iso did you get/use for 18.04 LTS? The exact, full filename?

---

### Post by weedware on 2019-10-24
ubuntu-18.04.3-desktop-amd64.iso

---

### Post by darkod on 2019-10-25
Your thread title says you intend to install Ubuntu Server but you have downloaded the desktop version iso.

What are you trying to install, desktop or server? Because this is the server subforum.

---

### Post by Skaperen on 2019-10-25
aside from the issue of downloading the wrong ISO, does your headless server have a genuine physical serial port you can connect a PC serial port to?  perhaps the easiest way to do this is to attach the storage device from the headless server to a PC that has at least a VGA display.  that's how i installed most evaluation boards (most ARM or MIPS) when i worked for an embedded software company.  how do you access BIOS on your headless servers (e.g. "Hardware Configuration" steps in the linked post)?

---

### Post by weedware on 2019-10-25
> **Skaperen said:**
> aside from the issue of downloading the wrong ISO, does your headless server have a genuine physical serial port you can connect a PC serial port to?  perhaps the easiest way to do this is to attach the storage device from the headless server to a PC that has at least a VGA display.  that's how i installed most evaluation boards (most ARM or MIPS) when i worked for an embedded software company.  how do you access BIOS on your headless servers (e.g. "Hardware Configuration" steps in the linked post)?

How embarassing... I actually downloaded the ubuntu server 18.04.3 LTS. Sorry for the confusion.

---

### Post by darkod on 2019-10-25
Again I ask, what is the exact filename please? Because since 18.04 ubuntu started to release two different server installlation ISOs. And to that tutorial it might make a difference which one you downloaded.

---

