---
title: "virtualbox and Ubuntu 10.04 Server"
date: 2010-11-04
forum: Server Platforms
---

### Post by ubudog on 2010-11-04
Hi, yesterday I installed Ubuntu 10.04 Server Edition in a virtual machine on VirtualBox.  I booted up, started Apache, etc.  On my host machine, I went to localhost in Firefox.  It says connection not found.  Shouldn't the virtual machine have the same IP as the host?  What am I doing wrong?  Thanks!

---

### Post by arrrghhh on 2010-11-04
No, the virtual machine has it's own IP.  It would be "localhost" within the VM, but not on your host machine :p

Do an ifconfig on the VM, see what the IP is.  It kinda depends if you use bridged or NAT how to connect to it.

---

### Post by CharlesA on 2010-11-04
Be sure to use bridged networking if you want to access services running on the VM.

---

### Post by ubudog on 2010-11-05
Thanks guys, I will try to setup bridge later. :guitar:

---

