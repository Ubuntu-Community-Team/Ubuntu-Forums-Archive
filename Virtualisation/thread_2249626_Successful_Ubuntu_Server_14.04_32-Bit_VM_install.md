---
title: "Successful Ubuntu Server 14.04 32-Bit VM install"
date: 2014-10-23
forum: Virtualisation
---

### Post by andrew163 on 2014-10-23
First off, I am by no means a Linux Guru; but, I have recently come across a solution that may be useful to others.

 I set out to create a V-box headless virtualization server on top of Ubuntu Server 14.04 (no GUI), after getting that build up and running I installed Oracle's VirtualBox application, then installed phpVirtualbox and dependacies to manage the system. After the installation was finalized I realized that I could only build VM's for 32-bit guests through phpVirtualbox. This caused a problem...... from my understanding and research Ubuntu Server 14.04 is only distributed as a 64-bit. So, I moved back to the latest 32-bit LTS version which was 12.04.5. After creating the VM I got the standard message screen stating the availability of the New 14.04 LTS..... So naturally I upgraded. Low and Behold, the system was updated with the "non-existant" Ubuntu Server 14.04 LTS 32-bit. Aterward I configured the said VM as my main home file server. This is a VERY time consuming process but as far as I can tell it is the only way to get ahold of the software. If anyone does know of a stable copy of Ubuntu Server 14.04 32-bit, please let me know so I can get it in my tool box.

Happy Days

---

### Post by Doug S on 2014-10-23
Ubuntu server 14.04 32 bit has always been available.
There are a few places to find it.
One is here: [http://releases.ubuntu.com/14.04.1/](http://releases.ubuntu.com/14.04.1/)
On that list, see this one: [http://releases.ubuntu.com/14.04.1/ubuntu-14.04.1-server-i386.iso](http://releases.ubuntu.com/14.04.1/ubuntu-14.04.1-server-i386.iso) , but other download options are available.

---

### Post by andrew163 on 2014-10-24
Thank you very much, I dont know why I couldn't find this before..... must have been an off day lol, now that I have a fews 32 bit copy I can get some more Home servers up and running :D

---

