---
title: "kvm problem"
date: 2012-08-08
forum: Virtualisation
---

### Post by jemadux on 2012-08-08
first of all I installed qemu-kvm 
and then qemu-kvm coomand is not found 

and theese are the commands about kvm 
[IMG]http://i.imgur.com/eVbpM.png[/IMG]

and also 

jemadux-ThinkPad:[jemadux]:~%lsmod | grep kvm 
kvm_intel             137721  0 
kvm                   415549  1 kvm_intel
jemadux-ThinkPad:[jemadux]:~%

---

### Post by slooksterpsv on 2012-08-14
qemu-kvm encompasses a bunch of utilities for kvm to work with qemu. You'll need to setup a virtual machine using qemu and specify the options to use KVM otherwise you can find a GUI in Software Center to help configure qemu's with KVM functionality.

---

### Post by johnathansmith on 2012-08-14
As slooksterpsv mentioned, you need to make a setup first. Here is a [link]("http://wiki.qemu.org/Manual"), that should help you with that. 
Also here is a [guide ]("http://www.ubuntugeek.com/qemu-machine-emulator-and-virtualizer-setup-in-ubuntu.html")from ubuntu geek (little bit outdated).

---

### Post by Metallion on 2012-08-15
The qemu-system* commands or plain kvm should work.

---

### Post by Dedoimedo on 2012-08-16
You can also use the virsh frontend for qemu commands.
Dedoimedo

---

