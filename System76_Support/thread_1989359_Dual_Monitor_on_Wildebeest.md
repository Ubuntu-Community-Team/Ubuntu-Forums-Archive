---
title: "Dual Monitor on Wildebeest"
date: 2012-05-28
forum: System76 Support
---

### Post by eadwacer on 2012-05-28
I am having trouble getting dual monitors to work on my wife's new (shipped 15 May) Ubuntu 12.04 Wildebeest (Wldb2), with the recommended Nvidia drivers.

It appears that the Nvidia card (GE Force GE 210) will support a DVI monitor _or_ a VGA monitor, but not both. Plugging both in gives me a 'no signal' on the VGA. I tried plugging in the DVI to the DVI socket on the PC, but then only the VGA worked.

System Settings / Monitors only shows one monitor (and it thinks my Samsung is a laptop), and System Settings / Details says it doesn't know what kind of video card I have.

Do I need to get some HDMI cables?

---

### Post by eadwacer on 2012-05-29
SOLVED: Had to open a terminal and sudo nvidia-settings. It doesn't seem to be available any other way (like through System Settings). That seems to have done the job.

---

### Post by isantop on 2012-05-30
> **eadwacer said:**
> SOLVED: Had to open a terminal and sudo nvidia-settings. It doesn't seem to be available any other way (like through System Settings). That seems to have done the job.

It's a bit of a caveat to the Nvidia drivers: their configuration utility isn't the most user friendly, and the drivers themselves lack support for the protocol that allows Ubuntu's built-in configuration tool to work. 

Nvidia have recently released a new version of their drive that does include support for this protocol. It should be packaged and available in Ubuntu soon. This should solve any remaining problems you have.

---

### Post by eadwacer on 2012-05-30
Thanks. I eagerly await. Other than that, the new PC is doing well.

---

