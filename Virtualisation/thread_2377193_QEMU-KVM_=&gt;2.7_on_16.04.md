---
title: "QEMU-KVM =&gt;2.7 on 16.04"
date: 2017-11-10
forum: Virtualisation
---

### Post by izznogooood on 2017-11-10
Hi, I'm trying to get QEMU 2.7 (current 2.5) or newer on Ubuntu 16.04. The reason for this is I want Hyper-V to work on Server 2016. (For testing purposes).

I cant find a PPA for QEMU, and i am hesitant to build from source as I have other KVM's running. 

Has anyone done this or have some thoughts around the subject?

---

### Post by KillerKelvUK on 2017-11-10
I've previously used this PPA ([https://launchpad.net/~jacob/+archive/ubuntu/virtualisation](https://launchpad.net/~jacob/+archive/ubuntu/virtualisation)) but I don't think it reaches the version of qemu you want for your distro.  More recently for testing qemu functionality I just build from source and run the binary from the build tree without replacing my distro's package installed default.  Once you have the dependencies nailed building qemu is pretty quick (build spec not withstanding).

---

### Post by izznogooood on 2017-11-10
Thank you, as you say the package for QEMU does not quite reach the version I was hoping for...

I will give the manual intervention a try, but I dont like it ;). Another option is to skip straight to Beta LTS ...

---

