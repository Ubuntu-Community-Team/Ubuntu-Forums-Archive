---
title: "Firewire Card displays in FFADO and Pulse Audio but not Jack"
date: 2016-12-08
forum: Ubuntu Studio
---

### Post by j0330h on 2016-12-08
Hey guys, I've been trying to get my firewire audio interface (Focusrite Saffire Pro 14) to work with Bitwig for years now and I feel like I'm pretty close to getting it to be stable. I finally got around to swapping out my garbage VIA firewire PCI card for one with a Texas Instruments chip and am now able to successfully use my interface with Bitwig without crashing. However, the issue currently is that I get frequent XRUNS and I can only use the interface with JACK using only the ALSA driver selection in Cadence/qJackctl. When I select firewire or freebob I only see a default hw:0 selection. Ffado-mixer finds my interface just fine and I can also select the interface and use it in Ubuntu's Sound settings. I have gone over [this guide]("https://help.ubuntu.com/community/UbuntuStudioPreparation") many times but no avail. Please let me know what commands/logs you need me to generate and thank you ahead of time for your efforts. My specs are listed below:

[LIST]
[*]Ubuntu 16.04 w/ low-latency kernel OS
[*]Focusrite Saffire Pro 14 interface
[*]Intel i5 3570K CPU
[*]Gigabyte Z77X-UP5-TH Motherboard
[*]Bitwig 1.3.14 DAW
[/LIST]

---

