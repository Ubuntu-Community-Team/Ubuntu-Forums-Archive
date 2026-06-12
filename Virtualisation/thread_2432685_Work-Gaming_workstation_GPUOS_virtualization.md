---
title: "Work-Gaming workstation GPU/OS virtualization"
date: 2019-12-06
forum: Virtualisation
---

### Post by Pushkar_Naik on 2019-12-06
I've just finished my high-end home workstation hardware build, and now its time to install the SSD with software.
My use-case of this workstation is two fold. Use linux server for my small team (max 4 users) development work in machine 
learning and parallel algorithms, remotely, as well as let my kids play their high-end graphics games. 
This means, apart from OS level virtualization, I'll be needing GPU virtualization as well. 

Here are my build details:
a) CPU: Ryzen 3900x (12 Core)
b) GPU1: [LEFT]NVidia RTX 2080 Ti
c) GPU2: NVidia GTX 1050 Ti[/LEFT]
d) [LEFT]Motherboard: [/LEFT]
x570 (Asus Crosshair VIII Hero Wifi) 
e) RAM: 32GB G.Skill (3600 MHz) DDR4, 
f) SSD: Sabrient Rocket 1 TB NVME

I have the following requirements, but I'm no expert in this area, so I seek your help:

1] Use a Ubuntu linux host
2] One VM (VM1) running Ubuntu server, for my team to remotely connect to, where most of development work can be done
3] One VM (VM2) where Windows 10 Pro Workstation edition will serve as gaming system
4] GPU sharing/switching between VM's using containers concept i believe, without any restarts, to achieve:
    a) Script based switching of full GPU1 to either VM1 or VM2 when full performance of GPU is desired by either
    b) [LEFT]Script based sharing of GPU1 between VM1/VM2 when full performance of GPU1 is not really desired by either[/LEFT]
    c) GPU2 to be used by host Ubuntu primarily, and which can be shared with VM1 when much performance is not required

Please provide suggestions in terms of host OS, VMs and GPU virtualization, that can provide maximum performance with least latency possible

---

### Post by kevdog on 2019-12-06
Honestly I have no idea why you would want to combine a work machine with a gaming system.  I personally would rethink that strategy.

---

