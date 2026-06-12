---
title: "Slow Boot Time and Poor Performance on Ubuntu Server 16.04"
date: 2018-05-02
forum: Server Platforms
---

### Post by elembke on 2018-05-02
[COLOR=#111111][FONT=Ubuntu]I have been trying every trick and tip on this forum and others, with little success. I need help.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I am running two Ubuntu 16.04 servers as NVRs running Zoneminder. Each machine is the exactly the same and is utilizing RAID 0. Ever since I set them up, they have been sluggish and unreliable. I run updates regularly and used several monitoring programs with little luck.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I was rebooting regularly to help with issues, and have now scheduled a nightly boot. The boot time is bad and sometimes it boots with no network. I have tried to restart network services as well as "ifconfig eth0 down && ifconfig eth0 up" without luck. I have written a crobtab job to check for network connection and if there isn't one, it reboots again. Performance is decent after a reboot. Here is the [output of dmesg]("https://drive.google.com/file/d/1nYPKR8OhWxwWvj6m5H_eysv-kmsVL3wL/view?usp=sharing") from one of the machines:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Using htop, load averages range from 3-5 across 4 cores. Memory usage also runs in the 25-35% range. Swap is rarely used.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If anyone has any ideas or thoughts, I am open and willing to try anything.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks![/FONT][/COLOR]

---

