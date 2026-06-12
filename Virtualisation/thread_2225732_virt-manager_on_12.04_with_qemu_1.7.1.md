---
title: "virt-manager on 12.04 with qemu 1.7.1"
date: 2014-05-22
forum: Virtualisation
---

### Post by Ramanpreet_Singh on 2014-05-22
Hi,

On Ubuntu 12.04 , i directly installed qemu 1.7.1 . I tarred the images in /usr/local/kvm/bin  and then did a make install , under./configure  in /usr/local/kvm. Initially I was not able to use qemu with my virt-manager since it was pointing to a /usr/sbin . I created soft links with kvm to /usr/local/kvm/bin and also copied qemu files to /usr/local/bin.

I am able to connect to new qemu in virt-manager but when I am trying to create a VM from qcow2 image , i am getting error "unable to complete install, internal error child process".

I'll appreciate  your help.

THanks,
Raman

---

