---
title: "VMWare Multi Core not functioning Correctly?"
date: 2012-08-10
forum: Virtualisation
---

### Post by jeannief on 2012-08-10
Hi,

I am using Ubuntu 11.10 under VMWare Workstation 8. I have several process running each of which periodically needs to perform system commands such as copying and deleting files (each process uses different directories although the files are identically named). My machine is a Dell XPS quad core. Have tried configuring the processors setting on VMWare various ways to allow Ubuntu to use separate processors / cores for each process. The problem I am seeing is that the system commands are not correctly performed: eg. the file copy creates empty files in the new location and does not delete the originals. but it works sometimes.

When I configured the processors to have 2 processors with 1 core each - top command showed two processors but the unwanted behaviour was still evident.

Any help appreciated. The jobs I am trying to run are very time consuming and it would be great if I could utilise the available processing power.

/proc/cpuinfo shows all available cores
many thanks

---

### Post by papibe on 2012-08-10
Moved to **Virtualization**.

---

### Post by jeannief on 2012-08-11
Hi 

I am new to this forum and having some trouble navigating: can't find this 
under Virtualisation. 

j

---

### Post by dcstar on 2012-08-30
> **jeannief said:**
> Hi,

I am using Ubuntu 11.10 under VMWare Workstation 8. I have several process running each of which periodically needs to perform system commands such as copying and deleting files (each process uses different directories although the files are identically named). My machine is a Dell XPS quad core. Have tried configuring the processors setting on VMWare various ways to allow Ubuntu to use separate processors / cores for each process. The problem I am seeing is that the system commands are not correctly performed: eg. the file copy creates empty files in the new location and does not delete the originals. but it works sometimes.
.........

Processors are not really relevant to problems with copying whether in a VM or not.

Explain what you are trying to do in **some** detail and you might get some assistance.

---

