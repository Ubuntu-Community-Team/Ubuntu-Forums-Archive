---
title: "Can't enable desktop effects in any variation of Ubuntu under virtual box 3.2"
date: 2010-10-16
forum: Virtualisation
---

### Post by charlesC8188 on 2010-10-16
Ok so I have been reading these forums trying to figure out why I can't enable desktop effects in Ubuntu under Virtual Box. My host OS is Windows 7 pro 64bit. I have tried installing Ubuntu 10.10, 10.4, and 9.10 both x86 and x64 editions. I have downloaded and installed Vbox Additions, enabled 3d acceleration in Vbox, and moved the display memory to 128mb. I see so many others being able to enable their desktop effects in virtual box on a Windows 7 host, but like many others I can not. I know my hardware is capable of running compiz.

Hardware: AMD Phenom 2 x4 @ 3.8ghz
GPU- XFX HD 5850 1gb DDR5
Memory - 6gb ddr3 (1600mhz) 
OS- windows 7 x64
Vbox- version 3.2 (newest version)


Any suggestions or ideas would be greatly appreciated.

---

### Post by sikander3786 on 2010-10-16
I fear, Virtualbox can't handle compiz as the 3d effects are choppy under any Virtual Server for the moment.

---

### Post by charlesC8188 on 2010-10-17
I have seen compiz effects working correctly on a few different  occasions. There are tutorials. I have followed them and no compiz  effects. My hardware is superior to the machines that have enabled  desktop effects in Virtual Box through Vbox Additions and 3d  acceleration. For some reason my just doesn't want to work. Any other  VM's I could use?

---

### Post by sikander3786 on 2010-10-17
I have heard that some people got compiz working inside virtualbox and vmware server but I cannot confirm that.

The guest OS only sees a virtual graphics card, not the actual one that you've got on your machine, vmware server has got some settings to achieve that but I don't exactly know if they work or not.

---

### Post by charlesC8188 on 2010-10-17
[http://www.youtube.com/watch?v=wUEkLw7-s7o](http://www.youtube.com/watch?v=wUEkLw7-s7o)

Compiz working in a virtual machine.

---

