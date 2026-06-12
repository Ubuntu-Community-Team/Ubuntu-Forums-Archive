---
title: "Kubuntu 21.04 BETA install fails"
date: 2021-04-03
forum: Ubuntu Development Version
---

### Post by gh4mint on 2021-04-03
Tried to install Kubuntu 21.04 BETA on two different PCs and it Fails to start Install Tool.
Both PCs run Kubuntu 20.04 OK.

---

### Post by jeremy31 on 2021-04-03
Moved to Ubuntu Dev Version as 21.04 hasn't been released yet

---

### Post by xyz-t on 2021-04-03
April first ISO was ok here. It takes longer to see Try/Install Kubuntu in this cycle, may take up to a minute or more.
Varying from one build with the other. March 25th ISO booted under 30 seconds. 

How did you make the bootable stick? From Ku 20.04? Where the process stalls?

---

### Post by IanW on 2021-04-04
Were you installing on a VM?
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1920665](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1920665)

---

### Post by gh4mint on 2021-04-04
Download 21.04 Beta amd iso file from DistroWatch.com, then burned ISO DVD in the usual manner.
The DVD boots but the usual Live Demo and Install Tool never appear.

---

### Post by CelticWarrior on 2021-04-04
Distrowatch.com doesn't host any ISO. It merely has links for the main download page of each distro. Hopefully the correct one in this case.

---

### Post by xyz-t on 2021-04-05
> **gh4mint said:**
> Download 21.04 Beta amd iso file from DistroWatch.com, then burned ISO DVD in the usual manner.
The DVD boots but the usual Live Demo and Install Tool never appear.

Get it there instead:

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

---

### Post by gh4mint on 2021-04-05
xyz-t Thanks for the link to the cdimage.ubuntu.com.
Downloaded the iSO file and created a DVD in the usual manner.
DVD boots but Ubuntu Live fails to start....last message on screen follows:

"Failed to start Ubuntu Live CD Installer, submit kernel crash signatures."

PC then hangs.

---

### Post by bobbicat on 2021-04-06
There is a bug with Kubuntu Hippo which appears if 'Safe Graphics' mode is selected when booting the iso.
This bug is reported in Launchpad 'Ubiquity KDE crash on try/install and from live session with "malloc(): unaligned tcache chunk detected"' Bug #1920665
It is also mentioned in the release notes with Hippo Beta.

If you go to the Kubuntu website [Kubuntu.org] look in the News section for more info on Kubuntu Hippo2104 testing and also the Beta.

---

