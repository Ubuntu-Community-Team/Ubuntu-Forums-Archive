---
title: "ubuntu 16.04 gui in virtualbox"
date: 2018-10-01
forum: Virtualisation
---

### Post by aboud.sawan on 2018-10-01
Hello,

I'm running ubuntu 16.04 (guest machine) in virtual box under windows 10.

my issue; when moving windows (any windows.. terminal for example),they become grayed ( ie loss content while moving). how to solve thisgui  issue.

---

### Post by monkeybrain20122 on 2018-10-01
Ubuntu uses  desktop composting in its default DE. If you run in VB better use a flavour without fancy graphics since the graphic driver in VB is very basic.

---

### Post by deadflowr on 2018-10-01
*Thread moved to **Virtualization***

Typically a greyed out window means the system is very busy.
What are the allocated settings (cpu, ram, disk size) for the guest?

---

### Post by ajgreeny on 2018-10-01
You may also like to see if disabling 3D acceleration in the guest makes any difference.

I used to run Ubuntu 16.04 as a VM in VBox without a problem but I always turned off 3D in the guests as I see no real point in it when running a VM; you may disagree, of course, in which case try some other DE system such as Xubuntu as suggested by monkeybrain20122

---

### Post by aboud.sawan on 2018-10-01
thanks for the replay, my desktop is very basic, not running any fancy graphics

---

### Post by aboud.sawan on 2018-10-01
tried to turn off 3D acceleration, no change

---

### Post by ajgreeny on 2018-10-01
Can you please give us an answer to deadflowr's query about the VM settings; it may help us.

---

### Post by aboud.sawan on 2018-10-01
ubuntu 64 bit
base memory: 1024 MB
HardDisk: 10 GB SATA

---

### Post by deadflowr on 2018-10-01
1gb of RAM is a tad weak. Ubuntu really needs at least 2gb.
Also, do you know what cpu settings are for the guest?
(Like allocated cores, and also what the main cpu on the host is)

---

### Post by aboud.sawan on 2018-10-01
spec of host machine:
Core i7-7700 CPU @ 3.6Ghz
16 GB RAM

I raised memory of guest machine to 4 GB, still the same issue

---

### Post by deadflowr on 2018-10-01
You know alternatively, you might consider ditching Virtualbox and try Windows own vm creator utility:
[https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine]("https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine")
Bonus, here's something Microsoft was working on for better performance with Ubuntu on Hyper-v:
[https://community.ubuntu.com/t/enhanced-ubuntu-vm-in-hyper-v/4363]("https://community.ubuntu.com/t/enhanced-ubuntu-vm-in-hyper-v/4363")

Just a thought.
You're entitled to go which ever way works best for you.

---

