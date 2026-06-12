---
title: "Having issue installing vscode on xububtu"
date: 2019-03-07
forum: Virtualisation
---

### Post by colino371 on 2019-03-07
Hi everyone,

Pls I am having an error trying to install vscode on a VM Terminal. See error below:

inyang@inyang-VirtualBox:~$ sudo apt install ./code_1.31.1-1549938243_amd64.deb
Reading package lists... Done
E: Unsupported file ./code_1.31.1-1549938243_amd64.deb given on commandline
inyang@inyang-VirtualBox:~$ 

PLS KINDLY HELP ON HW TO RESOLVE THIS

THanks!

---

### Post by jeremy31 on 2019-03-07
```
sudo dpkg -i code_1.31.1-1549938243_amd64.deb
```
Does that work?

---

### Post by coffeecat on 2019-03-07
Forum Feedback & Help is not for technical support.

*Thread moved to **Virtualisation** sub-forum.*

---

