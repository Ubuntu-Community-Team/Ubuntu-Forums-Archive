---
title: "gnome-terminal 3.28 still in cosmic"
date: 2018-09-04
forum: Ubuntu Development Version
---

### Post by sacridex on 2018-09-04
Hi,

there is still gnome-terminal 3.28 in cosmic and not 3.29/3.30. Is this on purpose?

Greetings

---

### Post by jbicha on 2018-09-08
It's a lot of work to update all the GNOME pieces. The [terminal update]("https://launchpad.net/bugs/1791373") is being worked on though.

---

### Post by corradoventu on 2018-09-19
corrado@corrado-HP-p4-cc-0913:~$ apt policy gnome-terminal
gnome-terminal:
  Installed: 3.30.0-1ubuntu1
  Candidate: 3.30.0-1ubuntu1
  Version table:
 *** 3.30.0-1ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-HP-p4-cc-0913:~$ inxi
CPU: Dual Core Intel Core i5-4210U (-MT MCP-) 
speed/min/max: 798/800/2700 MHz Kernel: 4.18.0-7-generic x86_64 Up: 7m 
Mem: 1264.8/3876.4 MiB (32.6%) Storage: 465.76 GiB (1.2% used) Procs: 202 
Shell: bash 4.4.19 inxi: 3.0.22 
corrado@corrado-HP-p4-cc-0913:~$ date
mer 19 set 2018, 18.54.14, CEST
corrado@corrado-HP-p4-cc-0913:~$

---

